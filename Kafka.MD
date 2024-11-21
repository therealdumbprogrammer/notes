## Unit 1: Introduction to Apache Kafka

### Overview

- **Apache Kafka** is a distributed streaming platform used for building real-time data pipelines and streaming applications.
- **Core Concepts**:
  - **Topics**: Categories or feed names to which records are published.
  - **Partitions**: Topics are split into partitions for scalability and parallelism.
  - **Brokers**: Servers that make up the Kafka cluster.
  - **Producers**: Clients that publish data to topics.
  - **Consumers**: Clients that subscribe to topics and process the feed of published messages.
  - **Clusters**: Kafka runs as a cluster on one or more servers.
- **Use Cases**:
  - Real-time data pipelines
  - Stream processing
  - Messaging system replacement

---

## Unit 2: Basic Kafka Operations

### Command-Line Tools

- **Topic Management**:
  - **Create a Topic**:
    ```bash
    bin/kafka-topics.sh --create --topic my-topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
    ```
  - **List Topics**:
    ```bash
    bin/kafka-topics.sh --list --bootstrap-server localhost:9092
    ```
  - **Describe a Topic**:
    ```bash
    bin/kafka-topics.sh --describe --topic my-topic --bootstrap-server localhost:9092
    ```

- **Producing Messages**:
  - Use the console producer to send messages to a topic:
    ```bash
    bin/kafka-console-producer.sh --topic my-topic --bootstrap-server localhost:9092
    ```
    - Type your messages and press Enter to send.

- **Consuming Messages**:
  - Use the console consumer to read messages from a topic:
    ```bash
    bin/kafka-console-consumer.sh --topic my-topic --from-beginning --bootstrap-server localhost:9092
    ```

### Message Formats

- **Default Serialization**: Strings are serialized using UTF-8 encoding.
- **Custom Serialization**: For complex data types, custom serializers and deserializers are needed (covered in Unit 4).

---

## Unit 3: Kafka Producers and Consumers in Java

In this unit, we focus on interacting with Apache Kafka using Java. You'll learn how to write Java applications that produce and consume messages to and from Kafka topics, understand the key components of the Kafka Producer and Consumer APIs, and explore serialization and deserialization techniques, including custom serializers and deserializers. Additionally, we delve into multi-threaded consumers, handling message ordering, and advanced consumer features like `consumer.pause()` and `consumer.resume()`.

### 4.1 Setting Up a Java Project with Kafka Dependencies

- **Build Tools**: Use **Maven** or **Gradle** for dependency management.
- **Kafka Dependencies**:
  - Add the `kafka-clients` library to your project dependencies.
  - **Maven Example** (`pom.xml`):
    ```xml
    <dependencies>
      <dependency>
        <groupId>org.apache.kafka</groupId>
        <artifactId>kafka-clients</artifactId>
        <version>3.5.1</version>
      </dependency>
    </dependencies>
    ```
  - **Gradle Example** (`build.gradle`):
    ```groovy
    dependencies {
      implementation 'org.apache.kafka:kafka-clients:3.5.1'
    }
    ```

### 4.2 Writing a Simple Producer

- **Producer Configuration**:
  ```java
  Properties props = new Properties();
  props.put("bootstrap.servers", "localhost:9092");
  props.put("acks", "all");
  props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
  props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
  ```
- **Creating a Kafka Producer**:
  ```java
  KafkaProducer<String, String> producer = new KafkaProducer<>(props);
  ```
- **Sending Messages**:
  ```java
  ProducerRecord<String, String> record = new ProducerRecord<>("my-topic", "key", "Hello, Kafka!");
  producer.send(record, (metadata, exception) -> {
      if (exception == null) {
          System.out.printf("Sent record to partition %d with offset %d%n", metadata.partition(), metadata.offset());
      } else {
          exception.printStackTrace();
      }
  });
  ```
- **Closing the Producer**:
  ```java
  producer.flush();
  producer.close();
  ```

### 4.3 Writing a Simple Consumer

- **Consumer Configuration**:
  ```java
  Properties props = new Properties();
  props.put("bootstrap.servers", "localhost:9092");
  props.put("group.id", "my-group");
  props.put("enable.auto.commit", "true");
  props.put("auto.commit.interval.ms", "1000");
  props.put("key.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
  props.put("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
  ```
- **Creating a Kafka Consumer**:
  ```java
  KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
  ```
- **Subscribing to Topics**:
  ```java
  consumer.subscribe(Collections.singletonList("my-topic"));
  ```
- **Polling for Messages**:
  ```java
  try {
      while (true) {
          ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
          for (ConsumerRecord<String, String> record : records) {
              System.out.printf("offset = %d, key = %s, value = %s%n",
                  record.offset(), record.key(), record.value());
          }
      }
  } finally {
      consumer.close();
  }
  ```

### 4.4 Serialization and Deserialization

#### Built-in Serializers/Deserializers

- `StringSerializer` and `StringDeserializer` for simple string messages.

#### Custom Serializers and Deserializers

For complex data types, you need to implement custom serializers and deserializers.

##### Example Custom Serializer

```java
import org.apache.kafka.common.serialization.Serializer;
import com.fasterxml.jackson.databind.ObjectMapper;

public class UserSerializer implements Serializer<User> {
    private ObjectMapper objectMapper = new ObjectMapper();

    @Override
    public byte[] serialize(String topic, User user) {
        try {
            return objectMapper.writeValueAsBytes(user);
        } catch (Exception e) {
            throw new RuntimeException("Error serializing User", e);
        }
    }
}
```

##### Example Custom Deserializer

```java
import org.apache.kafka.common.serialization.Deserializer;
import com.fasterxml.jackson.databind.ObjectMapper;

public class UserDeserializer implements Deserializer<User> {
    private ObjectMapper objectMapper = new ObjectMapper();

    @Override
    public User deserialize(String topic, byte[] data) {
        try {
            return objectMapper.readValue(data, User.class);
        } catch (Exception e) {
            throw new RuntimeException("Error deserializing User", e);
        }
    }
}
```

##### Usage in Producer and Consumer Configuration

- **Producer Configuration**:
  ```java
  props.put("value.serializer", "com.example.UserSerializer");
  ```
- **Consumer Configuration**:
  ```java
  props.put("value.deserializer", "com.example.UserDeserializer");
  ```

### 4.5 Multi-Threaded Consumers

When dealing with high message volumes or time-consuming processing, you might need to process messages in parallel to increase throughput.

#### Processing Messages in Parallel Can Lead to Out-of-Order Handling

- **Kafka Guarantees Order Within Partitions**: Messages in a partition are delivered in the order they were produced.
- **Parallel Processing**: If you process messages in parallel (e.g., using multiple threads), the order in which the messages are processed may not match the order in which they were received.
- **Implications**:
  - If your application logic depends on message order, out-of-order processing can cause issues.
  - For idempotent or order-independent processing, this may not be a concern.

#### Approaches to Multi-Threaded Consumption

##### Approach 1: One Consumer Instance Per Thread

- **Concept**:
  - Each thread runs its own `KafkaConsumer` instance.
  - All consumers belong to the same consumer group.
  - Kafka distributes partitions among consumers in the group.
- **Implementation Example**:

```java
public class ConsumerThread implements Runnable {
    private KafkaConsumer<String, String> consumer;

    public ConsumerThread(String groupId, List<String> topics) {
        Properties props = new Properties();
        props.put("bootstrap.servers", "localhost:9092");
        props.put("group.id", groupId);
        props.put("key.deserializer", 
            "org.apache.kafka.common.serialization.StringDeserializer");
        props.put("value.deserializer", 
            "org.apache.kafka.common.serialization.StringDeserializer");
        consumer = new KafkaConsumer<>(props);
        consumer.subscribe(topics);
    }

    @Override
    public void run() {
        try {
            while (true) {
                ConsumerRecords<String, String> records = 
                    consumer.poll(Duration.ofMillis(100));
                for (ConsumerRecord<String, String> record : records) {
                    // Process the record
                    System.out.printf("Thread: %s, Partition: %d, Offset: %d, Key: %s, Value: %s%n",
                        Thread.currentThread().getName(), record.partition(), 
                        record.offset(), record.key(), record.value());
                }
                consumer.commitSync();
            }
        } catch (Exception e) {
            System.out.println("Error in consumer thread: " + e.getMessage());
        } finally {
            consumer.close();
        }
    }
}
```

**Starting Multiple Consumer Threads**:

```java
public class MultiThreadedConsumer {
    public static void main(String[] args) {
        String groupId = "multi-thread-consumer-group";
        List<String> topics = Arrays.asList("my-topic");
        int numThreads = 3;

        ExecutorService executor = Executors.newFixedThreadPool(numThreads);

        for (int i = 0; i < numThreads; i++) {
            ConsumerThread consumerThread = new ConsumerThread(groupId, topics);
            executor.submit(consumerThread);
        }

        // Add shutdown hook
        Runtime.getRuntime().addShutdownHook(new Thread(() -> {
            System.out.println("Shutting down executor...");
            executor.shutdown();
        }));
    }
}
```

**Considerations**:

- Each `KafkaConsumer` instance is confined to its own thread.
- The number of consumer instances should not exceed the number of partitions.

##### Approach 2: Single Consumer Instance with Worker Threads

- **Concept**:
  - A single `KafkaConsumer` runs in its own thread.
  - Messages are dispatched to a pool of worker threads for processing.
- **Handling Offsets and Message Order**:
  - Careful management is needed to ensure offsets are committed only after processing is complete.
  - Processing messages in parallel can lead to out-of-order handling.

##### Example: Commit After Processing All Records

To ensure that offsets are committed only after messages have been processed, you can collect `Future` objects from the executor service and wait for all tasks to complete before committing.

```java
public class SingleConsumerWithWorkers {
    public static void main(String[] args) {
        // Consumer configuration
        // ... (set up properties)

        KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
        consumer.subscribe(Arrays.asList("my-topic"));

        ExecutorService executor = Executors.newFixedThreadPool(10);

        try {
            while (true) {
                ConsumerRecords<String, String> records = 
                    consumer.poll(Duration.ofMillis(100));
                
                List<Future<?>> futures = new ArrayList<>();
                
                for (ConsumerRecord<String, String> record : records) {
                    futures.add(executor.submit(() -> {
                        // Process the record
                        System.out.printf("Processing record with offset %d%n", record.offset());
                    }));
                }

                // Wait for all tasks to complete
                for (Future<?> future : futures) {
                    future.get(); // Blocks until the task is complete
                }

                // Commit offsets after processing
                consumer.commitSync();
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            consumer.close();
            executor.shutdown();
        }
    }
}
```

**Considerations**:

- **Blocking on `future.get()`** ensures that all messages are processed before committing offsets.
- **Potential Performance Impact**: Waiting for all tasks can reduce throughput.

### 4.6 Handling Message Ordering

As discussed, processing messages in parallel can lead to out-of-order handling. If your application requires strict ordering:

- **Process Messages Sequentially**: Process messages in the order they are received.
- **Dedicated Thread per Partition**: Since Kafka maintains order within partitions, assigning one thread per partition can preserve order.
- **Idempotent Processing**: Design your processing logic to be idempotent or order-independent.

### 4.7 Pausing and Resuming Consumption

The Kafka consumer API provides methods to pause and resume consumption, which can be useful for implementing backpressure.

#### Using `consumer.pause()` and `consumer.resume()`

**Example Scenario**:

- **Goal**: Pause consumption when the processing queue is full or downstream systems are slow, and resume when ready.

**Implementation Example**:

```java
public class BackpressureConsumer {
    private static final int MAX_QUEUE_SIZE = 1000;
    private static BlockingQueue<ConsumerRecord<String, String>> processingQueue = new LinkedBlockingQueue<>();
    private static Set<TopicPartition> pausedPartitions = new HashSet<>();

    public static void main(String[] args) {
        // Consumer configuration
        // ... (set up properties)

        KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
        consumer.subscribe(Arrays.asList("my-topic"));

        // Start a worker thread to process messages
        ExecutorService executor = Executors.newSingleThreadExecutor();
        executor.submit(() -> processMessages());

        try {
            while (true) {
                // Check if we need to pause consumption
                if (processingQueue.size() >= MAX_QUEUE_SIZE && pausedPartitions.isEmpty()) {
                    Set<TopicPartition> partitions = consumer.assignment();
                    consumer.pause(partitions);
                    pausedPartitions.addAll(partitions);
                    System.out.println("Consumer paused due to backpressure.");
                }

                // Check if we can resume consumption
                if (processingQueue.size() < MAX_QUEUE_SIZE / 2 && !pausedPartitions.isEmpty()) {
                    consumer.resume(pausedPartitions);
                    pausedPartitions.clear();
                    System.out.println("Consumer resumed.");
                }

                ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
                for (ConsumerRecord<String, String> record : records) {
                    // Add records to processing queue
                    processingQueue.put(record);
                }

                // Commit offsets if not paused
                if (pausedPartitions.isEmpty()) {
                    consumer.commitSync();
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            consumer.close();
            executor.shutdown();
        }
    }

    private static void processMessages() {
        try {
            while (true) {
                ConsumerRecord<String, String> record = processingQueue.take();
                // Process the record
                System.out.printf("Processing record with offset %d%n", record.offset());
                // Simulate processing time
                Thread.sleep(50);
            }
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

**Explanation**:

- **Backpressure Logic**:
  - When the `processingQueue` reaches a certain size, the consumer pauses consumption.
  - Consumption resumes when the queue size decreases.
- **Resource Management**:
  - The consumer and executor service are properly closed in a `finally` block.

### 4.8 File-Based Producer

#### Overview

- **Purpose**: Read data from a file and produce messages to a Kafka topic.
- **Use Cases**: Ingest data from logs, CSV files, or any file-based data source.

#### Implementation Steps

1. **Read Data from File**:
   - Use Java I/O classes like `BufferedReader` to read the file line by line.

2. **Create a Kafka Producer**:
   - Configure producer properties.
   - Use appropriate serializers (e.g., `StringSerializer`).

3. **Send Messages to Kafka**:
   - For each line read from the file, create a `ProducerRecord` and send it.

#### Sample Code

```java
public class FileBasedProducer {
    public static void main(String[] args) {
        String topicName = "file-topic";
        String filePath = "input.txt"; // Path to your input file

        Properties props = new Properties();
        props.put("bootstrap.servers", "localhost:9092");
        props.put("acks", "all");
        props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
        props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

        try (BufferedReader br = new BufferedReader(new FileReader(filePath));
             KafkaProducer<String, String> producer = new KafkaProducer<>(props)) {

            String line;
            while ((line = br.readLine()) != null) {
                ProducerRecord<String, String> record = new ProducerRecord<>(topicName, line);
                producer.send(record, (metadata, exception) -> {
                    if (exception != null) {
                        System.err.printf("Error sending record: %s%n", exception.getMessage());
                    } else {
                        System.out.printf("Record sent to partition %d with offset %d%n",
                            metadata.partition(), metadata.offset());
                    }
                });
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```