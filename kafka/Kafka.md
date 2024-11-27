# Table of Contents

- [Unit 1: Introduction to Apache Kafka](#unit-1-introduction-to-apache-kafka)
  - [1.1 Overview](#11-overview)

- [Unit 2: Basic Kafka Operations](#unit-2-basic-kafka-operations)
  - [2.1 Command-Line Tools](#21-command-line-tools)
  - [2.2 Message Formats](#22-message-formats)

- [Unit 3: Kafka Producers and Consumers in Java](#unit-3-kafka-producers-and-consumers-in-java)
  - [3.1 Setting Up a Java Project with Kafka Dependencies](#31-setting-up-a-java-project-with-kafka-dependencies)
  - [3.2 Writing a Simple Producer](#32-writing-a-simple-producer)
  - [3.3 Writing a Simple Consumer](#33-writing-a-simple-consumer)
  - [3.4 Serialization and Deserialization](#34-serialization-and-deserialization)
  - [3.5 Multi-Threaded Consumers](#35-multi-threaded-consumers)
  - [3.6 Handling Message Ordering](#36-handling-message-ordering)
  - [3.7 Pausing and Resuming Consumption](#37-pausing-and-resuming-consumption)
  - [3.8 File-Based Producer](#38-file-based-producer)

- [Unit 4: Topics and Partitions](#unit-4-topics-and-partitions)
  - [4.1 Topics](#41-topics)
  - [4.2 Partitions](#42-partitions)
  - [4.3 Why Partitions Matter](#43-why-partitions-matter)

- [Unit 5: Kafka Architecture and Internals](#unit-5-kafka-architecture-and-internals)
  - [5.1 Replication and Fault Tolerance](#51-replication-and-fault-tolerance)
    - [5.1.1 Replication Factors](#511-replication-factors)
    - [5.1.2 Leader and Follower Replicas](#512-leader-and-follower-replicas)
    - [5.1.3 In-Sync Replicas (ISR)](#513-in-sync-replicas-isr)
  - [5.2 Understanding the Commit Log](#52-understanding-the-commit-log)
    - [5.2.1 Commit Log Concept](#521-commit-log-concept)
    - [5.2.2 Data Retention](#522-data-retention)
    - [5.2.3 Benefits](#523-benefits)
  - [5.3 Consumer Groups and Load Balancing](#53-consumer-groups-and-load-balancing)
    - [5.3.1 Consumer Groups](#531-consumer-groups)
    - [5.3.2 Load Balancing](#532-load-balancing)
  - [5.4 Offset Management](#54-offset-management)
    - [5.4.1 Committing Offsets](#541-committing-offsets)
    - [5.4.2 Delivery Semantics](#542-delivery-semantics)
    - [5.4.3 Offset Storage](#543-offset-storage)
    - [5.4.4 Offset Management Strategies](#544-offset-management-strategies)
  - [5.5 Exactly-Once Semantics in Kafka](#55-exactly-once-semantics-in-kafka)
    - [5.5.1 Idempotent Producers](#551-idempotent-producers)
    - [5.5.2 Transactions](#552-transactions)
    - [5.5.3 Transactional Consumers](#553-transactional-consumers)
  - [5.6 Kafka's High-Level Architecture](#56-kafkas-high-level-architecture)
    - [5.6.1 Components](#561-components)
    - [5.6.2 Data Flow](#562-data-flow)
    - [5.6.3 Cluster Anatomy](#563-cluster-anatomy)
  - [5.7 Client Request Routing](#57-client-request-routing)
    - [5.7.1 Metadata Fetching](#571-metadata-fetching)
    - [5.7.2 Direct Communication](#572-direct-communication)
    - [5.7.3 Handling Leader Changes](#573-handling-leader-changes)
    - [5.7.4 Benefits](#574-benefits)
  - [5.8 ISR Maintenance and Scenarios](#58-isr-maintenance-and-scenarios)
    - [5.8.1 Maintaining ISR (In-Sync Replicas)](#581-maintaining-isr-in-sync-replicas)
    - [5.8.2 Health Checks and Lag Monitoring](#582-health-checks-and-lag-monitoring)
    - [5.8.3 What Happens When ISR Has Only the Leader](#583-what-happens-when-isr-has-only-the-leader)
    - [5.8.4 Is It Possible for ISR to Be Empty?](#584-is-it-possible-for-isr-to-be-empty)
    - [5.8.5 Recovery and Reassignment](#585-recovery-and-reassignment)
    - [5.8.6 Configuration Parameters](#586-configuration-parameters)
    - [5.8.7 Ensuring High Availability](#587-ensuring-high-availability)

- [Unit 6: Advanced Producer Concepts](#unit-6-advanced-producer-concepts)
  - [6.1 Producer Acknowledgments and Retries](#61-producer-acknowledgments-and-retries)
  - [6.2 Batching and Compression](#62-batching-and-compression)
  - [6.3 Custom Partitioning Strategies](#63-custom-partitioning-strategies)
  - [6.4 Idempotent Producers and Transactions](#64-idempotent-producers-and-transactions)
  - [6.5 Advanced Configuration Settings](#65-advanced-configuration-settings)
  - [6.6 Monitoring and Metrics](#66-monitoring-and-metrics)

- [Unit 7: Advanced Consumer Concepts](#unit-7-advanced-consumer-concepts)
  - [7.1 Consumer Rebalancing and Partition Assignment Strategies](#71-consumer-rebalancing-and-partition-assignment-strategies)
  - [7.2 Manual Partition Assignment](#72-manual-partition-assignment)
  - [7.3 Rebalancing Listeners](#73-rebalancing-listeners)
  - [7.4 Offset Management in Depth](#74-offset-management-in-depth)
  - [7.5 Consuming Records with Timestamps](#75-consuming-records-with-timestamps)
  - [7.6 Best Practices for Consumer Configuration](#76-best-practices-for-consumer-configuration)

- [Unit 8: Kafka Connect](#unit-8-kafka-connect)
  - [8.1 Introduction to Kafka Connect](#81-introduction-to-kafka-connect)
  - [8.2 Kafka Connect Architecture](#82-kafka-connect-architecture)
  - [8.3 Source and Sink Connectors](#83-source-and-sink-connectors)
  - [8.4 Configuring Connectors](#84-configuring-connectors)
  - [8.5 Distributed Mode vs. Standalone Mode](#85-distributed-mode-vs-standalone-mode)
  - [8.6 Developing Custom Connectors](#86-developing-custom-connectors)
  - [8.7 Single Message Transforms (SMTs)](#87-single-message-transforms-smts)
  - [8.8 Data Format and Schema Management](#88-data-format-and-schema-management)
  - [8.9 Best Practices and Troubleshooting](#89-best-practices-and-troubleshooting)
  - [8.10 Practical Example: Setting Up a JDBC Sink Connector](#810-practical-example-setting-up-a-jdbc-sink-connector)
  - [8.11 Deep Dive into Kafka Connect: Workers, Tasks, and Parallelism](#811-deep-dive-into-kafka-connect-workers-tasks-and-parallelism)

- [Unit 9: Kafka Streams API](#unit-9-kafka-streams-api)
  - [9.1 Introduction to Kafka Streams](#91-introduction-to-kafka-streams)
  - [9.2 Stream Processing Concepts](#92-stream-processing-concepts)
  - [9.3 Kafka Streams Architecture](#93-kafka-streams-architecture)
  - [9.4 Writing a Simple Kafka Streams Application](#94-writing-a-simple-kafka-streams-application)
  - [9.5 Stateful Streams](#95-stateful-streams)
    - [5.1 State Storage in Kafka Streams](#51-state-storage-in-kafka-streams)
    - [5.2 Handling Service Instance Failures and Cluster Changes](#52-handling-service-instance-failures-and-cluster-changes)
    - [5.3 Impact on Windowing](#53-impact-on-windowing)
    - [5.4 Use Cases for Stateful Streams](#54-use-cases-for-stateful-streams)
  - [9.6 Integrating Kafka Streams with Spring Boot](#96-integrating-kafka-streams-with-spring-boot)
    - [6.1 Code Organization](#61-code-organization)
    - [6.2 Application ID and Consumer Groups](#62-application-id-and-consumer-groups)

---


## Introduction to Apache Kafka

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

## Basic Kafka Operations

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

## Kafka Producers and Consumers in Java

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
        <version>${use-latest-version}</version>
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

---

## Topics and Partitions

### Topics

- **Definition**: Categories or feed names to which records are published.
- **Characteristics**:
  - Multi-subscriber support.
  - Immutable data.

### Partitions

- **Definition**: A single topic is divided into multiple partitions.
- **Characteristics**:
  - Ordered, immutable sequences of records.
  - Each record has a unique **offset**.
  - Fundamental unit of parallelism and scalability.

### Why Partitions Matter

- **Scalability**: Distributes data across brokers.
- **Parallelism**: Enables multiple consumers to read data in parallel.
- **Ordering Guarantees**: Order is guaranteed within a partition, not across partitions.

**Example**:

```plaintext
Topic: orders
+-----------------+
| Partition 0     |
| Offset: 0, 1, 2 |
+-----------------+
| Partition 1     |
| Offset: 0, 1, 2 |
+-----------------+
| Partition 2     |
| Offset: 0, 1, 2 |
+-----------------+
```

---

## 5.2 Replication and Fault Tolerance

### Replication Factors

- **Definition**: Number of copies of each partition across brokers.
- **Common Practice**: Use a replication factor of **3** in production.

### Leader and Follower Replicas

- **Leader Replica**:
  - Handles all read and write requests.
- **Follower Replicas**:
  - Replicate data from the leader.
  - Take over if the leader fails.

### In-Sync Replicas (ISR)

- **Definition**: Set of replicas fully caught up with the leader.
- **Role**:
  - Only ISR members are eligible for leader election.
  - Ensure data durability and availability.

**Example**:

```plaintext
Partition 0 Replicas:
- Leader: Broker 1
- Follower: Broker 2
- Follower: Broker 3

If Broker 1 fails, Broker 2 or Broker 3 becomes the new leader.
```

---

## 5.3 Understanding the Commit Log

### Commit Log Concept

- **Definition**: An append-only data structure recording every change.
- **Kafka's Use**:
  - Each partition is a commit log.
  - Enables sequential reads and writes.

### Data Retention

- **Configurable Retention**:
  - Time-based (e.g., 7 days).
  - Size-based limits.
- **Log Compaction**:
  - Removes obsolete records with the same key.
  - Retains the latest value per key.

### Benefits

- **Performance**: Efficient disk usage.
- **Reliability**: Immutable logs prevent corruption.
- **Replayability**: Consumers can reprocess data from any point.

---

## 5.4 Consumer Groups and Load Balancing

### Consumer Groups

- **Definition**: A group of consumers sharing the workload.
- **Characteristics**:
  - Each partition is consumed by only one consumer in the group.
  - Consumers can be in different processes or machines.

### Load Balancing

- **Partition Assignment**:
  - Kafka distributes partitions among consumers.
  - Automatic rebalancing upon consumer changes.
- **Benefits**:
  - **Scalability**: Add consumers to increase capacity.
  - **Fault Tolerance**: Redistributes partitions if a consumer fails.

**Example**:

```plaintext
Topic: orders (6 partitions)
Consumer Group: order-processors
Consumers: C1, C2, C3

Partition Assignment:
- C1: Partitions 0, 1
- C2: Partitions 2, 3
- C3: Partitions 4, 5

If C2 fails, partitions 2 and 3 are reassigned to C1 and C3.
```

---

## 5.5 Offset Management

### Committing Offsets

- **Automatic Offset Commit**:
  - Controlled by `enable.auto.commit` (default is `true`).
  - Commits offsets at regular intervals.
- **Manual Offset Commit**:
  - Use `commitSync()` or `commitAsync()`.
  - Provides control over when offsets are committed.

### Delivery Semantics

- **At-Least-Once Delivery**:
  - Default behavior.
  - Possible duplicate processing.
- **Exactly-Once Delivery**:
  - Requires idempotent producers and transactional APIs.
  - Ensures each message is processed exactly once.

### Offset Storage

- **Default**: Stored in Kafka's internal `__consumer_offsets` topic.
- **Custom**: Can be stored externally if needed.

### Offset Management Strategies

#### Automatic Commit

- **Pros**: Simplicity.
- **Cons**: Less control, risk of message loss or duplication.

#### Manual Commit

- **Synchronous Commit (`commitSync()`)**:
  - Blocks until the commit is acknowledged.
- **Asynchronous Commit (`commitAsync()`)**:
  - Non-blocking, but requires error handling.

**Example**:

```java
consumer.commitSync(); // Manual synchronous commit after processing records
```

---

## 5.6 Exactly-Once Semantics in Kafka

### Idempotent Producers

- **Purpose**: Prevent duplicate messages during retries.
- **Configuration**:
  - Set `enable.idempotence` to `true`.

### Transactions

- **Purpose**: Atomic writes across multiple partitions and topics.
- **Usage**:
  - Begin a transaction.
  - Send messages.
  - Commit or abort the transaction.

**Producer Example with Transactions**:

```java
Properties props = new Properties();
props.put("transactional.id", "my-transactional-id");
KafkaProducer<String, String> producer = new KafkaProducer<>(props);

producer.initTransactions();
producer.beginTransaction();
// Send messages
producer.commitTransaction();
```

### Transactional Consumers

- **Configuration**:
  - Set `isolation.level` to `read_committed`.
- **Behavior**:
  - Consumers only read messages from committed transactions.

---

## 5.7 Kafka's High-Level Architecture

### Components

1. **Producers**: Publish data to topics.
2. **Consumers**: Subscribe to topics and process data.
3. **Brokers**: Servers that store and serve data.
4. **ZooKeeper**: Coordinates brokers (being phased out in newer Kafka versions).

### Data Flow

1. **Producers** send messages to the leader broker of a partition.
2. **Brokers** replicate data to followers.
3. **Consumers** read messages from leader brokers.

### Cluster Anatomy

- **Controller Broker**:
  - Manages partition leadership and broker failures.
- **Replication**:
  - Provides fault tolerance.
- **Rebalancing**:
  - Redistributes partitions when brokers join or leave.

---

## 5.8 Client Request Routing

### Metadata Fetching

- **Bootstrap Servers**:
  - Clients connect to one or more brokers specified in `bootstrap.servers` to fetch metadata.
- **Metadata Includes**:
  - List of brokers in the cluster.
  - Topics and their partitions.
  - The leader broker for each partition.
  - Replica assignments.

**Process**:

1. **Initial Connection**:
   - Client connects to any broker in the cluster (bootstrap server).
2. **Metadata Request**:
   - Client requests metadata about the cluster.
3. **Metadata Response**:
   - Broker responds with the current cluster metadata.

### Direct Communication

- **Leader-Based Communication**:
  - Clients communicate directly with the leader broker of the partition they need to interact with.
- **No Multiple Hops**:
  - There are no intermediary brokers; communication is point-to-point between the client and the leader broker.

**Example**:

- **Producer Workflow**:
  1. Fetch metadata to determine the leader for the target partition.
  2. Send produce requests directly to the leader broker.

- **Consumer Workflow**:
  1. Fetch metadata to identify partition leaders.
  2. Send fetch requests directly to the appropriate leader brokers.

### Handling Leader Changes

- **Leader Failure Detection**:
  - If a leader broker becomes unavailable, clients receive errors like `NotLeaderForPartitionException`.
- **Metadata Refresh**:
  - Upon encountering such errors, clients request updated metadata.
- **Automatic Redirection**:
  - Clients update their internal metadata cache and redirect requests to the new leader broker.

**Illustration**:

```plaintext
Client (Producer/Consumer)
     |
     |-- Initial Metadata Request --> Broker A
     |<-- Metadata Response ---------|
     |
     |-- Direct Request to Leader Broker (e.g., Broker B)
```

- **Leader Change Scenario**:
  - If Broker B fails, the client encounters an error.
  - The client refreshes metadata and learns that Broker C is the new leader.
  - Subsequent requests are sent directly to Broker C.

### Benefits

- **Efficiency**:
  - Direct communication reduces latency.
- **Scalability**:
  - Clients distribute load across brokers by connecting directly to partition leaders.
- **Resilience**:
  - Clients adapt to changes in the cluster automatically.

---

## 5.9 ISR Maintenance and Scenarios

### Maintaining ISR (In-Sync Replicas)

- **Leader Role**:
  - The leader broker is responsible for tracking and managing the ISR for each partition it leads.
- **Follower Synchronization**:
  - Followers replicate data from the leader asynchronously.
  - They send fetch requests to the leader to get new messages.

### Health Checks and Lag Monitoring

- **Heartbeat Mechanism**:
  - Followers regularly send heartbeats to the leader to indicate they are alive.
- **Lag Detection**:
  - The leader monitors the lag of followers using metrics like `replica.lag.max.messages` and `replica.lag.time.max.ms`.
- **ISR Updates**:
  - If a follower falls behind beyond configured thresholds, the leader removes it from the ISR.
  - When the follower catches up, it is added back to the ISR.

### What Happens When ISR Has Only the Leader

- **Possible Scenario**:
  - All followers are removed from the ISR due to lag or failures, leaving only the leader.
- **Implications**:
  - **Reduced Fault Tolerance**:
    - If the leader fails, there are no in-sync replicas to take over.
    - This can lead to data loss or unavailability.
  - **Data Durability Risk**:
    - Without replication, messages acknowledged by the leader but not replicated to followers may be lost.

### Is It Possible for ISR to Be Empty?

- **No**:
  - The ISR always contains at least the leader broker.
  - An empty ISR would imply no leader, which is not possible in Kafka's design.

### Recovery and Reassignment

- **Leader Failure with ISR Containing Only Leader**:
  - Kafka cannot elect a new leader from out-of-sync followers.
  - The partition remains unavailable until:
    - The original leader recovers.
    - A follower catches up and joins the ISR.

### Configuration Parameters

- **`replica.lag.time.max.ms`**:
  - Maximum time a follower can lag before being removed from the ISR.
- **`min.insync.replicas`**:
  - Minimum number of replicas that must acknowledge a write for the leader to consider the write successful.
  - Used in conjunction with producer `acks` setting.

### Ensuring High Availability

- **Best Practices**:
  - **Set Appropriate Replication Factor**:
    - Use a replication factor of at least 3.
  - **Monitor ISR Size**:
    - Use monitoring tools to alert when ISR size drops.
  - **Adjust Producer `acks` Setting**:
    - Use `acks=all` to ensure messages are replicated to all ISR members.
  - **Configure `min.insync.replicas`**:
    - Set to a value greater than 1 to prevent writes when insufficient replicas are in sync.

**Example**:

```plaintext
Partition 0 Replicas:
- Leader: Broker 1 (in ISR)
- Follower: Broker 2 (out of ISR)
- Follower: Broker 3 (out of ISR)

ISR = {Broker 1}

If Broker 1 fails:
- No in-sync replicas are available.
- Partition 0 becomes unavailable until Broker 1 recovers or followers catch up.
```

---

# Unit 6: Advanced Producer Concepts

## 6.1 Producer Acknowledgments and Retries

### Acknowledgment Configuration (`acks`)

The `acks` setting determines the level of acknowledgment the producer requires the leader broker to have received before considering a request complete.

- **`acks=0`**:
  - The producer does not wait for any acknowledgment.
  - **Pros**: Maximum throughput, low latency.
  - **Cons**: Messages may be lost; no delivery guarantee.

- **`acks=1`**:
  - Waits for the leader broker's acknowledgment.
  - **Pros**: Balanced reliability and performance.
  - **Cons**: Messages may be lost if the leader fails after acknowledging.

- **`acks=all`** (or **`acks=-1`**):
  - Waits for acknowledgment from all in-sync replicas (ISRs).
  - **Pros**: Highest data durability.
  - **Cons**: Higher latency, lower throughput.

**Configuration Example**:

```java
Properties props = new Properties();
props.put("acks", "all"); // Ensures the highest level of durability
```

### Retries and Retry Backoff

- **`retries`**:
  - Number of times the producer will retry sending a failed message.
  - **Recommendation**: Set a high value to handle transient failures.

- **`retry.backoff.ms`**:
  - Time to wait before attempting a retry.
  - **Default**: `100` milliseconds.

**Configuration Example**:

```java
props.put("retries", 5);            // Number of retries
props.put("retry.backoff.ms", 200); // Backoff time between retries in milliseconds
```

---

## 6.2 Batching and Compression

### Batching

- **Purpose**: Improve throughput by sending multiple records in a single request.

**Key Settings**:

- **`batch.size`**:
  - Maximum bytes per batch for a single partition.
  - **Default**: `16384` bytes (16 KB).

- **`linger.ms`**:
  - Time to wait for additional messages before sending the batch.
  - **Default**: `0` milliseconds.

**Configuration Example**:

```java
props.put("batch.size", 32768); // 32 KB batch size
props.put("linger.ms", 5);      // Wait up to 5 ms
```

### Compression

- **Purpose**: Reduce network bandwidth usage and improve throughput.

**Compression Types**:

- `none` (default), `gzip`, `snappy`, `lz4`, `zstd`.

**Configuration Example**:

```java
props.put("compression.type", "snappy"); // Use Snappy compression
```

---

## 6.3 Custom Partitioning Strategies

### Default Partitioning Behavior

- **Without a Key**: Round-robin distribution among partitions.
- **With a Key**: Partition determined by the hash of the key.

### Implementing a Custom Partitioner

**Purpose**: Control message distribution to partitions based on custom logic.

**Steps**:

1. **Implement the `Partitioner` Interface**:

   ```java
   import org.apache.kafka.clients.producer.Partitioner;
   import org.apache.kafka.common.Cluster;
   import org.apache.kafka.common.utils.Utils;
   import java.util.Map;

   public class CustomPartitioner implements Partitioner {
       @Override
       public void configure(Map<String, ?> configs) {
           // Configuration if needed
       }

       @Override
       public int partition(String topic, Object key, byte[] keyBytes,
                            Object value, byte[] valueBytes, Cluster cluster) {
           // Custom partitioning logic
           int numPartitions = cluster.partitionCountForTopic(topic);
           if (keyBytes == null) {
               // Default to partition 0 if no key
               return 0;
           } else {
               // Example: Send messages with key starting with 'A' to partition 0
               if (((String) key).startsWith("A")) {
                   return 0;
               } else {
                   // Use default hash partitioning
                   return (Utils.toPositive(Utils.murmur2(keyBytes)) % numPartitions);
               }
           }
       }

       @Override
       public void close() {
           // Cleanup if needed
       }
   }
   ```

2. **Configure the Producer**:

   ```java
   props.put("partitioner.class", "com.example.CustomPartitioner");
   ```

3. **Use the Producer as Usual**:

   ```java
   ProducerRecord<String, String> record = new ProducerRecord<>("my-topic", "Key1", "Value1");
   producer.send(record);
   ```

---

## 6.4 Idempotent Producers and Transactions

### Idempotent Producers

- **Purpose**: Prevent duplicate messages during retries.
- **Enabling Idempotence**:

  ```java
  props.put("enable.idempotence", "true");
  ```

- **Constraints**:
  - `acks=all`
  - `retries` > 0
  - `max.in.flight.requests.per.connection` ≤ 5

### Transactions

- **Purpose**: Atomic writes across multiple partitions and topics.
- **Using Transactions**:

  ```java
  props.put("transactional.id", "my-transactional-id"); // Assign a transactional ID
  KafkaProducer<String, String> producer = new KafkaProducer<>(props);

  producer.initTransactions();

  try {
      producer.beginTransaction();
      // Send messages
      producer.send(new ProducerRecord<>("topic1", "key1", "value1"));
      producer.send(new ProducerRecord<>("topic2", "key2", "value2"));
      producer.commitTransaction();
  } catch (Exception e) {
      producer.abortTransaction();
      e.printStackTrace();
  } finally {
      producer.close();
  }
  ```

- **Consumer Configuration**:

  ```java
  props.put("isolation.level", "read_committed");
  ```

---

## 6.5 Advanced Configuration Settings

### `max.in.flight.requests.per.connection`

#### Definition

- **Purpose**: Controls the maximum number of unacknowledged requests the producer will send on a single connection.
- **Default**: `5`

#### Behavior

- **Ordering Guarantee**:
  - **Setting to `1`** ensures messages are written in order.
  - **Higher values** can lead to out-of-order messages during retries.

#### Relationship with Idempotence and Transactions

- **Idempotent Producers**:
  - Must set `max.in.flight.requests.per.connection` to `5` or less.
- **Transactional Producers**:
  - **Required** to set `max.in.flight.requests.per.connection` to `5` or less to maintain ordering guarantees.

**Configuration Example**:

```java
props.put("max.in.flight.requests.per.connection", 5);
```

### Relationship and Impact Among `buffer.memory`, `max.request.size`, `batch.size`, and `linger.ms`

These parameters collectively influence producer performance, memory usage, and batching behavior.

#### 1. `batch.size`

- **Purpose**: Maximum bytes per batch for a single partition.

#### 2. `linger.ms`

- **Purpose**: Time to wait for more records before sending a batch.

#### 3. `max.request.size`

- **Purpose**: Maximum size of a request sent to the broker.

#### 4. `buffer.memory`

- **Purpose**: Total memory available to buffer records waiting to be sent.

#### How They Interact

- **Batch Formation**:
  - A batch is sent when `batch.size` is reached or `linger.ms` expires.
- **Constraints**:
  - `batch.size` must be ≤ `max.request.size`.
  - `buffer.memory` must be sufficient to hold all accumulated batches.
- **Impact on Performance**:
  - Larger `batch.size` and `linger.ms` improve throughput but may increase latency and memory usage.
  - Insufficient `buffer.memory` can lead to blocking or `TimeoutException`.

#### Practical Configuration Example

```java
props.put("batch.size", 65536);          // 64 KB batch size
props.put("linger.ms", 10);              // Wait up to 10 ms
props.put("max.request.size", 1048576);  // 1 MB max request size
props.put("buffer.memory", 67108864);    // 64 MB buffer memory
```

---

## 6.6 Monitoring and Metrics

### Importance of Monitoring

- **Performance Tracking**: Identify bottlenecks.
- **Error Detection**: Quickly address issues.
- **Capacity Planning**: Understand resource utilization.

### Common Metrics

- `record-send-rate`
- `request-latency-avg`
- `batch-size-avg`
- `compression-rate-avg`
- `record-error-rate`

### Accessing Metrics

- **JMX (Java Management Extensions)**
- **Monitoring Tools**: Kafka Manager, Prometheus, Grafana, etc.

---

# Advanced Consumer Concepts

## 7.1 Consumer Rebalancing and Partition Assignment Strategies

### Consumer Rebalancing

- **Definition**: The process by which Kafka reassigns partitions to consumers within a consumer group.
- **Triggers**:
  - A new consumer joins the group.
  - An existing consumer leaves the group.
  - Topic metadata changes (e.g., partitions added).

### Partition Assignment Strategies

Kafka provides several strategies for partition assignment:

1. **Range Assignor** (Default)
   - Assigns partitions in contiguous ranges.
   - May lead to uneven distribution if partitions are not divisible by the number of consumers.

2. **RoundRobin Assignor**
   - Distributes partitions evenly in a round-robin fashion.
   - Provides a more balanced assignment.

3. **Sticky Assignor**
   - Attempts to minimize partition movement during rebalances.
   - Keeps the same partitions assigned to consumers as much as possible.

4. **Cooperative Sticky Assignor** (Kafka 2.4 and Later)
   - Introduces incremental cooperative rebalancing.
   - Minimizes downtime and avoids stopping the entire consumer group during rebalances.

**Configuring Assignment Strategy**:

```java
Properties props = new Properties();
props.put("partition.assignment.strategy", "org.apache.kafka.clients.consumer.StickyAssignor");
```

---

## 7.2 Manual Partition Assignment

### When to Use Manual Assignment

- **Use Cases**:
  - Consuming specific partitions.
  - Testing and debugging.
  - Custom load balancing.

### Assigning Partitions Manually

- **Using `assign()` Method**:

  ```java
  List<TopicPartition> partitions = Arrays.asList(
      new TopicPartition("my-topic", 0),
      new TopicPartition("my-topic", 1)
  );
  consumer.assign(partitions);
  ```

### Considerations

- **No Rebalancing**: Consumers with manual assignment do not participate in group rebalancing.
- **Offset Management**: You may need to manage offsets manually.
- **Fault Tolerance**: Partitions are not reassigned if a consumer fails.

---

## 7.3 Rebalancing Listeners

### Purpose

- **Monitor Rebalance Events**: React to partition assignment changes.
- **Use Cases**:
  - Commit offsets before partitions are revoked.
  - Initialize resources after partitions are assigned.

### Implementing a Rebalance Listener

- **Implement `ConsumerRebalanceListener` Interface**:

  ```java
  public class RebalanceListener implements ConsumerRebalanceListener {
      private final KafkaConsumer<String, String> consumer;

      public RebalanceListener(KafkaConsumer<String, String> consumer) {
          this.consumer = consumer;
      }

      @Override
      public void onPartitionsRevoked(Collection<TopicPartition> partitions) {
          // Commit offsets before partition revocation
          consumer.commitSync();
          System.out.println("Partitions revoked: " + partitions);
      }

      @Override
      public void onPartitionsAssigned(Collection<TopicPartition> partitions) {
          // Reset state or initialize resources
          System.out.println("Partitions assigned: " + partitions);
      }
  }
  ```

- **Registering the Listener**:

  ```java
  consumer.subscribe(Arrays.asList("my-topic"), new RebalanceListener(consumer));
  ```

### Best Practices

- **Commit Offsets in `onPartitionsRevoked()`**: Ensures processed messages are not reprocessed.
- **Avoid Lengthy Operations**: Keep listener methods efficient to avoid delaying rebalances.

---

## 7.4 Offset Management in Depth

### Understanding Consumer Offsets

- **Offset**: The position of a consumer in a partition.
- **Importance**: Determines where the consumer resumes after a restart.

### Offset Reset Policies

- **Configuration**: `auto.offset.reset`
- **Options**:
  - **`earliest`**: Start from the earliest available offset.
  - **`latest`** (default): Start from the latest offset.
  - **`none`**: Throw an exception if no previous offset is found.

### Manual Offset Control

#### Seeking to Specific Offsets

- **Example**:

  ```java
  TopicPartition partition = new TopicPartition("my-topic", 0);
  consumer.assign(Arrays.asList(partition));
  consumer.seek(partition, 100); // Start from offset 100
  ```

#### Seeking to Beginning or End

- **Seek to Beginning**:

  ```java
  consumer.seekToBeginning(consumer.assignment());
  ```

- **Seek to End**:

  ```java
  consumer.seekToEnd(consumer.assignment());
  ```

### Committing Offsets

- **Synchronous Commit**:

  ```java
  consumer.commitSync(); // Blocks until the commit is acknowledged
  ```

- **Asynchronous Commit with Callback**:

  ```java
  consumer.commitAsync((offsets, exception) -> {
      if (exception != null) {
          System.err.printf("Commit failed for offsets %s%n", offsets, exception);
      }
  });
  ```

### Handling Rebalance and Offset Commit

- **Potential Issue**: Uncommitted offsets may lead to message duplication during rebalances.
- **Solution**: Use `ConsumerRebalanceListener` to commit offsets before partitions are revoked.

---

## 7.5 Consuming Records with Timestamps

### Accessing Timestamps

- **Retrieve Record Timestamp**:

  ```java
  long timestamp = record.timestamp();
  ```

### Seeking to a Specific Timestamp

#### Use Case

- **Start Consumption from a Specific Time**: Useful for time-based processing.

#### Implementation Steps

1. **Assign Partitions**:

   ```java
   List<TopicPartition> partitions = new ArrayList<>();
   for (PartitionInfo partitionInfo : consumer.partitionsFor("my-topic")) {
       partitions.add(new TopicPartition(partitionInfo.topic(), partitionInfo.partition()));
   }
   consumer.assign(partitions);
   ```

2. **Define Timestamp to Seek To**:

   ```java
   long timestampToSearch = System.currentTimeMillis() - 24 * 60 * 60 * 1000; // 24 hours ago
   ```

3. **Fetch Offsets for Timestamps**:

   ```java
   Map<TopicPartition, Long> timestampsToSearch = new HashMap<>();
   for (TopicPartition partition : partitions) {
       timestampsToSearch.put(partition, timestampToSearch);
   }
   Map<TopicPartition, OffsetAndTimestamp> offsetsForTimes = consumer.offsetsForTimes(timestampsToSearch);
   ```

4. **Seek to Retrieved Offsets**:

   ```java
   for (TopicPartition partition : partitions) {
       OffsetAndTimestamp offsetAndTimestamp = offsetsForTimes.get(partition);
       if (offsetAndTimestamp != null) {
           consumer.seek(partition, offsetAndTimestamp.offset());
       } else {
           // If no offset is found, seek to beginning
           consumer.seekToBeginning(Arrays.asList(partition));
       }
   }
   ```

---

## 7.6 Best Practices for Consumer Configuration

### Configuring Fetch Size

- **`fetch.min.bytes`**: Minimum amount of data the broker should return for a fetch request.

  ```java
  props.put("fetch.min.bytes", 50000); // Wait for at least 50 KB of data
  ```

- **`fetch.max.wait.ms`**: Maximum time the broker will wait before returning data.

  ```java
  props.put("fetch.max.wait.ms", 500); // Wait up to 500 ms
  ```

### Controlling Session Timeouts

- **`session.timeout.ms`**: Time the consumer can be inactive before it's considered dead.

  ```java
  props.put("session.timeout.ms", 10000); // 10 seconds
  ```

- **`heartbeat.interval.ms`**: Frequency at which the consumer sends heartbeats to the broker.

  ```java
  props.put("heartbeat.interval.ms", 3000); // 3 seconds
  ```

### Maximizing Consumer Throughput

- **Increase `max.poll.records`**: Number of records returned in a single `poll()` call.

  ```java
  props.put("max.poll.records", 1000);
  ```

- **Adjust `max.partition.fetch.bytes`**: Maximum data per partition per fetch request.

  ```java
  props.put("max.partition.fetch.bytes", 1048576); // 1 MB
  ```

### Avoiding Rebalance Issues

- **Manage `max.poll.interval.ms`**: Maximum delay between `poll()` calls.

  ```java
  props.put("max.poll.interval.ms", 300000); // 5 minutes
  ```

- **Best Practice**: Ensure processing time is less than `max.poll.interval.ms` or call `poll()` more frequently.

### Error Handling

- **Handle Exceptions in Poll Loop**:

  ```java
  try {
      while (true) {
          ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
          // Process records
      }
  } catch (Exception e) {
      // Handle exception
      e.printStackTrace();
  } finally {
      consumer.close();
  }
  ```

- **Use `commitSync()` with Retry Logic**:

  ```java
  boolean success = false;
  int retries = 0;
  while (!success && retries < 3) {
      try {
          consumer.commitSync();
          success = true;
      } catch (CommitFailedException e) {
          retries++;
          // Log and handle retry
      }
  }
  ```

### Monitoring and Metrics

- **Consumer Metrics**:
  - `records-consumed-rate`
  - `bytes-consumed-rate`
  - `fetch-latency-avg`
  - `records-lag-max`

- **Accessing Metrics**:

  ```java
  Map<MetricName, ? extends Metric> metrics = consumer.metrics();
  for (Map.Entry<MetricName, ? extends Metric> entry : metrics.entrySet()) {
      System.out.printf("%s: %f%n", entry.getKey().name(), entry.getValue().metricValue());
  }
  ```

---

# Kafka Connect

## 8.1 Introduction to Kafka Connect

### What is Kafka Connect?

- **Kafka Connect** is a framework for connecting Kafka with external systems, such as databases, key-value stores, search indexes, and file systems.
- **Purpose**: Simplifies the integration of Kafka with other systems by providing ready-to-use connectors.

### Why Use Kafka Connect?

- **Simplifies Data Integration**: Reduces the effort required to build custom data pipelines.
- **Scalable and Reliable**: Designed to handle large data volumes efficiently.
- **Pluggable Connectors**: Offers a wide range of pre-built connectors for various systems.
- **Fault Tolerance**: Automatically recovers from failures and provides exactly-once delivery semantics.

### Use Cases

- **Database Streaming**: Ingest data changes from databases into Kafka.
- **Log Aggregation**: Collect logs from various sources and stream them to Kafka.
- **Indexing**: Stream data from Kafka to search indexes like Elasticsearch.
- **Data Warehouse Integration**: Export data from Kafka to data warehouses for analytics.

---

## 8.2 Kafka Connect Architecture

### High-Level Components

- **Connectors**: Define where data comes from (Source) and where it goes (Sink).
- **Workers**: Processes that execute connectors and tasks.
- **Tasks**: Units of work that move data to or from Kafka.
- **Configurations**: Define the behavior of connectors and workers.

### How Kafka Connect Works

1. **Deployment Modes**:
   - **Standalone Mode**: Runs on a single process; suitable for development and testing.
   - **Distributed Mode**: Runs across multiple processes; offers scalability and fault tolerance.

2. **Data Flow**:
   - **Source Connector**:
     - Reads data from an external system.
     - Converts it into **SourceRecords**.
     - Writes to Kafka topics.
   - **Sink Connector**:
     - Reads data from Kafka topics.
     - Converts **SinkRecords** into the required format.
     - Writes data to the external system.

### Key Concepts

- **Offset Management**: Tracks the progress of data transfer to prevent duplication or loss.
- **Serialization and Deserialization**: Uses **Converters** to handle data formats (e.g., JSON, Avro).
- **Single Message Transforms (SMTs)**: Lightweight transformations applied to individual messages.

---

## 8.3 Source and Sink Connectors

### Understanding Connectors

- **Source Connectors**: Import data from external systems into Kafka.
- **Sink Connectors**: Export data from Kafka to external systems.

### Commonly Used Connectors

- **Source Connectors**:
  - **JDBC Source Connector**: Reads data from relational databases.
  - **Debezium Connectors**: Capture Change Data Capture (CDC) events from databases like MySQL, PostgreSQL.
  - **File Source Connector**: Reads data from files.

- **Sink Connectors**:
  - **Elasticsearch Sink Connector**: Writes data to Elasticsearch.
  - **HDFS Sink Connector**: Writes data to Hadoop HDFS.
  - **JDBC Sink Connector**: Writes data to relational databases.
  - **S3 Sink Connector**: Writes data to Amazon S3.

### Finding Connectors

- **Confluent Hub**: Repository of connectors available for download.
- **Community Connectors**: Open-source connectors maintained by the community.

---

## 8.4 Configuring Connectors

### Connector Configuration Basics

- **Connector Class**: The fully qualified class name of the connector.
- **Tasks Max**: Maximum number of tasks the connector can use.
- **Connector-Specific Settings**: Properties unique to each connector (e.g., connection URLs, topics).

### Example Configuration: JDBC Source Connector

```json
{
  "name": "jdbc-source-connector",
  "config": {
    "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
    "tasks.max": "1",
    "connection.url": "jdbc:mysql://localhost:3306/mydb",
    "connection.user": "user",
    "connection.password": "password",
    "table.whitelist": "users",
    "mode": "incrementing",
    "incrementing.column.name": "id",
    "topic.prefix": "jdbc-"
  }
}
```

### Running Connectors

- **REST API**: Submit connector configurations via HTTP POST requests to the Kafka Connect REST API.
- **CLI Tools**: Use command-line utilities to manage connectors (in standalone mode).

### Steps to Deploy a Connector

1. **Set Up Kafka Connect**: Start in standalone or distributed mode.
2. **Prepare Configuration**: Create a JSON or properties file.
3. **Deploy Connector**:
   - **Standalone Mode**: Specify the connector configuration file when starting the worker.
   - **Distributed Mode**: Use the REST API to submit the configuration.
4. **Monitor Connector**: Check logs and status via REST API or monitoring tools.

### Monitoring Connectors

- **Connector Status API**: Retrieve the status of connectors and tasks.
- **Metrics**: Exposed via JMX, collectable by monitoring systems.

---

## 8.5 Distributed Mode vs. Standalone Mode

### Standalone Mode

- **Characteristics**:
  - Runs in a single process.
  - Configuration is stored locally.
- **Use Cases**:
  - Development and testing.
  - Simple deployments without high availability requirements.

### Distributed Mode

- **Characteristics**:
  - Runs across multiple worker processes.
  - Workers coordinate via Kafka topics.
  - Provides scalability and fault tolerance.
- **Use Cases**:
  - Production environments.
  - High availability and scalability requirements.

### Comparison

| Aspect                | Standalone Mode      | Distributed Mode    |
|-----------------------|----------------------|---------------------|
| Deployment Complexity | Simple               | More Complex        |
| Scalability           | Limited              | Horizontally Scalable |
| Fault Tolerance       | Limited              | High                |
| Configuration Storage | Local Filesystem     | Internal Kafka Topics |
| Management            | Local Configuration  | REST API            |

---

## 8.6 Developing Custom Connectors

### When to Develop Custom Connectors

- No existing connector meets your requirements.
- Need to integrate with proprietary or specialized systems.
- Require custom logic during data ingestion or egress.

### Components of a Connector

- **Connector Class**: Manages configuration and creates tasks.
- **Task Class**: Performs the data copying work.
- **Configuration Definitions**: Specify configuration parameters.
- **Transformation Logic**: Optional custom transformations.

### Steps to Create a Custom Connector

1. **Set Up a Project**: Use Maven or Gradle; include Kafka Connect API dependency.
2. **Implement the Connector Class**: Define start, stop, taskConfigs, and other methods.
3. **Implement the Task Class**: Define how data is fetched or written.
4. **Package and Deploy**: Build a JAR file and place it in the `plugins` directory.
5. **Restart Kafka Connect Worker**: Load the new connector.

### Best Practices

- **Error Handling**: Ensure the connector can handle failures gracefully.
- **Offset Management**: Use Kafka Connect's offset storage.
- **Parallelism**: Design tasks to allow parallel execution if possible.
- **Documentation**: Provide clear configuration documentation.

---

## 8.7 Single Message Transforms (SMTs)

### What are SMTs?

- **Single Message Transforms** are simple transformations applied to individual messages as they pass through the connector.

### Common SMTs

- **MaskField**: Masks sensitive fields in the data.
- **RegexRouter**: Modifies topic names using regular expressions.
- **TimestampRouter**: Routes messages to different topics based on timestamps.
- **FilterFields**: Removes or includes specific fields from the data.

### Applying SMTs in Configuration

```json
{
  "transforms": "MaskField",
  "transforms.MaskField.type": "org.apache.kafka.connect.transforms.MaskField$Value",
  "transforms.MaskField.fields": "password,ssn"
}
```

---

## 8.8 Data Format and Schema Management

### Converters

- **Purpose**: Serialize and deserialize data between Kafka Connect and Kafka topics.
- **Common Converters**:
  - **JSON Converter**: For JSON data.
  - **Avro Converter**: Uses Avro serialization with Schema Registry.
  - **String Converter**: Treats data as plain strings.

### Using Schema Registry

- **Benefits**:
  - Manages schemas for Avro, JSON Schema, or Protobuf data.
  - Ensures producers and consumers agree on data structure.
  - Supports schema evolution with compatibility checks.

### Configuring Converters with Schema Registry

```json
{
  "key.converter": "io.confluent.connect.avro.AvroConverter",
  "key.converter.schema.registry.url": "http://localhost:8081",
  "value.converter": "io.confluent.connect.avro.AvroConverter",
  "value.converter.schema.registry.url": "http://localhost:8081"
}
```

---

## 8.9 Best Practices and Troubleshooting

### Managing Offsets and Data Consistency

- **Ensure Idempotency**: Design connectors to handle retries without duplicating data.
- **Use Transactions if Supported**: Some systems support transactional writes.
- **Monitor Offsets**: Regularly check that offsets are advancing.

### Scaling Connectors

- **Increase Tasks**: Adjust `tasks.max` to utilize more parallelism.
- **Monitor Resources**: Ensure workers have sufficient CPU and memory.
- **Load Balancing**: Distribute tasks evenly across workers.

### Error Handling and Retries

- **Configure Retry Policies**: Use `errors.retry.timeout` and `errors.retry.delay.max.ms`.
- **Dead Letter Queues (DLQs)**: Capture problematic records for later analysis.

```json
{
  "errors.tolerance": "all",
  "errors.deadletterqueue.topic.name": "dlq-topic",
  "errors.deadletterqueue.context.headers.enable": "true"
}
```

### Monitoring and Logging

- **Metrics**: Collect metrics exposed by Kafka Connect for performance monitoring.
- **Logging**: Configure appropriate log levels for debugging.
- **Alerting**: Set up alerts for connector failures or performance issues.

---

## 8.10 Practical Example: Setting Up a JDBC Sink Connector

### Scenario

- **Objective**: Export data from a Kafka topic to a relational database (e.g., PostgreSQL) using the JDBC Sink Connector.

### Steps

1. **Prerequisites**:
   - Kafka cluster and Kafka Connect running.
   - Target database accessible.

2. **Install the JDBC Sink Connector**:
   - Download and place the connector JAR in the `plugins` directory.
   - Restart Kafka Connect workers.

3. **Create Connector Configuration** (`jdbc-sink-connector.json`):

```json
{
  "name": "jdbc-sink-connector",
  "config": {
    "connector.class": "io.confluent.connect.jdbc.JdbcSinkConnector",
    "tasks.max": "1",
    "topics": "orders",
    "connection.url": "jdbc:postgresql://localhost:5432/mydb",
    "connection.user": "dbuser",
    "connection.password": "dbpassword",
    "auto.create": "true",
    "insert.mode": "upsert",
    "pk.mode": "record_key",
    "pk.fields": "order_id",
    "table.name.format": "orders_table"
  }
}
```

4. **Deploy the Connector**:

```bash
curl -X POST -H "Content-Type: application/json" --data @jdbc-sink-connector.json http://localhost:8083/connectors
```

5. **Verify the Connector Status**:

```bash
curl http://localhost:8083/connectors/jdbc-sink-connector/status
```

6. **Monitor Data Flow**:
   - Produce messages to the `orders` topic.
   - Verify data insertion into the database.

---

## 8.11 Deep Dive into Kafka Connect: Workers, Tasks, and Parallelism

### Scenario Overview

- **Objective**: Move data from **MySQL** to **Cassandra** using Kafka Connect in **distributed mode** with **4 workers**.
- **Connectors Involved**:
  - **Source Connector**: Reads data from MySQL.
  - **Sink Connector**: Writes data to Cassandra.

### Understanding How Kafka Connect Operates in This Scenario

1. **Connector Trigger Mechanism**:

   - **JDBC Source Connector**:
     - **Polling-based**: Periodically polls MySQL for new data.
     - Uses `poll.interval.ms` and `batch.max.rows` for configuration.
   - **Debezium MySQL Connector**:
     - **Event-driven**: Listens to MySQL binlog for real-time changes.

2. **Batch Size and Data Movement**:

   - **Determined by**:
     - **JDBC Connector**: `batch.max.rows`.
     - **Debezium Connector**: Internally managed.
   - **Impact**:
     - Larger batches increase throughput but require more memory.

3. **Role of Workers and Tasks**:

   - **Workers**:
     - Execute tasks and provide scalability.
     - Coordinate via Kafka's group management protocol.
   - **Tasks**:
     - Units of work that perform data transfer.
     - Configurable via `tasks.max`.

4. **Task Distribution Among Workers**:

   - **Parallelism**:
     - **Source Connector**: Can be increased by raising `tasks.max` and properly partitioning data.
     - **Sink Connector**: Consumes from multiple Kafka partitions in parallel.
   - **Assignment**:
     - Tasks are distributed across workers for load balancing.

### Data Flow Overview

1. **Source Connector (MySQL to Kafka)**:

   - **Connector**: JDBC Source or Debezium Connector.
   - **Tasks**: Configurable number for parallelism.
   - **Workers**: Distribute tasks among themselves.

2. **Kafka Cluster**:

   - **Data Storage**: Kafka topics hold data from MySQL.
   - **Partitioning**: Enables parallel consumption by the sink connector.

3. **Sink Connector (Kafka to Cassandra)**:

   - **Connector**: Cassandra Sink Connector.
   - **Tasks**: Configurable number to parallelize writes.
   - **Workers**: Tasks are assigned to workers for execution.

### Configuration Examples

#### JDBC Source Connector Configuration

```json
{
  "name": "jdbc-source-connector",
  "config": {
    "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
    "tasks.max": "4",
    "connection.url": "jdbc:mysql://localhost:3306/mydb",
    "connection.user": "user",
    "connection.password": "password",
    "mode": "incrementing",
    "incrementing.column.name": "id",
    "table.whitelist": "users,orders,products,inventory",
    "poll.interval.ms": "5000"
  }
}
```

#### Cassandra Sink Connector Configuration

```json
{
  "name": "cassandra-sink-connector",
  "config": {
    "connector.class": "com.datamountaineer.streamreactor.connect.cassandra.CassandraSinkConnector",
    "tasks.max": "4",
    "topics": "users,orders,products,inventory",
    "connect.cassandra.key.space": "mykeyspace",
    "connect.cassandra.contact.points": "cassandra-host",
    "connect.cassandra.port": "9042",
    "connect.cassandra.username": "cassandra",
    "connect.cassandra.password": "cassandra"
  }
}
```

### Additional Considerations

- **Ensuring Effective Parallelism**:
  - **Kafka Topics** should have multiple partitions.
  - Adjust `tasks.max` to utilize available workers.
- **Connector Limitations**:
  - **Debezium Connector**: Typically runs a single task per connector to maintain order.
- **Monitoring and Tuning**:
  - Monitor resource usage (CPU, memory, network).
  - Adjust configurations based on performance metrics.

### Summary

- **Workers** execute tasks and provide fault tolerance.
- **Tasks** determine the level of parallelism.
- **Parallel Data Movement** is achieved through proper configuration.
- **Configuration is Key**:
  - Set `tasks.max` appropriately.
  - Ensure Kafka topics are properly partitioned.
  - Adjust batch sizes and polling intervals for optimal performance.

---

## Unit 9: Kafka Streams API

### 9.1 Introduction to Kafka Streams

**Kafka Streams** is a **Java library** designed for **stream processing** that allows you to consume, process, and produce data from Kafka topics seamlessly.

**Key Features:**
- **Distributed and Scalable:** Automatically handles load balancing across multiple instances.
- **Fault-Tolerant:** Provides mechanisms for stateful processing with built-in fault tolerance.
- **Exactly-Once Semantics:** Ensures data is processed exactly once to prevent duplication or loss.
- **No Separate Cluster Needed:** Runs within your application without requiring a dedicated processing cluster.

**Use Cases:**
- **Real-Time Data Processing:** Enriching, filtering, or aggregating data in real-time.
- **Event-Driven Microservices:** Building services that react to streaming data.
- **Continuous ETL:** Transforming data as it moves from one system to another.
- **Anomaly Detection:** Identifying patterns or anomalies in streaming data.

### 9.2 Stream Processing Concepts

**Streams and Tables:**
- **Stream:** An unbounded, continuously updating sequence of records representing data in motion.
- **Table:** A snapshot of data at a given point in time representing data at rest.

**Records:**
- **Key-Value Pair:** Represents individual pieces of data within streams or tables.
- **Timestamp:** Indicates when the record was created or received.

**Processing Topology:**
- **Definition:** The blueprint of data flow and processing logic consisting of sources, processors, and sinks.

**Stateless vs. Stateful Processing:**
- **Stateless:** Each record is processed independently (e.g., `map`, `filter`, `flatMap`).
- **Stateful:** Processing depends on accumulated state or previous records (e.g., `aggregate`, `join`, `windowed operations`).

### 9.3 Kafka Streams Architecture

**Application Instances:**
- Deployed as standard Java applications.
- Multiple instances can run in parallel for scalability and fault tolerance.

**Stream Partitions and Tasks:**
- **Partitions:** Kafka topic partitions serve as units of parallelism.
- **Tasks:** Kafka Streams divides processing into tasks, each handling one or more partitions.

**State Stores:**
- **Purpose:** Store state required for stateful operations like aggregations or joins.
- **Types:**
  - **Persistent State Stores:** Stored on disk using **RocksDB** (default).
  - **In-Memory State Stores:** Stored in memory for faster access.
- **Changelog Topics:** Backup state stores to Kafka topics for fault tolerance.

**Threading Model:**
- **Threads:** Managed within the application via the `num.stream.threads` property.
- **Configuration:** Controls the number of processing threads per instance.

### 9.4 Writing a Simple Kafka Streams Application

**Setting Up the Project:**
- **Maven Dependency:**
  ```xml
  <dependency>
      <groupId>org.apache.kafka</groupId>
      <artifactId>kafka-streams</artifactId>
      <version>3.5.0</version>
  </dependency>
  ```
- **Gradle Dependency:**
  ```groovy
  implementation 'org.apache.kafka:kafka-streams:3.5.0'
  ```

**Basic Components:**
- **StreamsConfig:** Holds configuration properties.
- **StreamsBuilder:** Constructs the processing topology.
- **KStream:** Represents a stream of records.
- **KTable:** Represents a changelog stream of updates.

**Example: Word Count Application**
```java
import org.apache.kafka.common.serialization.Serdes;
import org.apache.kafka.streams.*;
import org.apache.kafka.streams.kstream.*;

import java.util.Arrays;
import java.util.Properties;

public class WordCountApplication {
    public static void main(String[] args) {
        // Configuration
        Properties props = new Properties();
        props.put(StreamsConfig.APPLICATION_ID_CONFIG, "wordcount-app");
        props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        props.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG, Serdes.String().getClass());
        props.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG, Serdes.String().getClass());
        props.put(StreamsConfig.STATE_DIR_CONFIG, "/tmp/kafka-streams");

        // Topology
        StreamsBuilder builder = new StreamsBuilder();
        KStream<String, String> textLines = builder.stream("input-topic");
        KTable<String, Long> wordCounts = textLines
            .flatMapValues(value -> Arrays.asList(value.toLowerCase().split("\\W+")))
            .groupBy((key, word) -> word)
            .count(Materialized.as("counts-store"));
        wordCounts.toStream().to("output-topic", Produced.with(Serdes.String(), Serdes.Long()));

        // Start Streams
        KafkaStreams streams = new KafkaStreams(builder.build(), props);
        streams.start();

        // Shutdown Hook
        Runtime.getRuntime().addShutdownHook(new Thread(streams::close));
    }
}
```

### 9.5 Stateful Streams

Stateful stream processing involves maintaining state across multiple records, enabling complex operations like aggregations, joins, and windowing.

#### 5.1 State Storage in Kafka Streams

**Stateful Operations:**
- **Aggregations:** Counting, summing, averaging.
- **Joins:** Merging streams or tables based on keys.
- **Windowed Operations:** Aggregations over time windows.

**State Stores:**
- **Definition:** Local databases that store state required for stateful operations.
- **Types:**
  - **Persistent State Stores:** Stored on disk using **RocksDB**.
  - **In-Memory State Stores:** Stored in memory for faster access.
- **Changelog Topics:** Kafka Streams backs up state stores to changelog topics for fault tolerance.

**Configuration:**
- **State Directory:**
  ```java
  props.put(StreamsConfig.STATE_DIR_CONFIG, "/path/to/state/dir");
  ```
- **Changelog Topic Naming:** `<application-id>-<store-name>-changelog`.

#### 5.2 Handling Service Instance Failures and Cluster Changes

**Fault Tolerance:**
- **Automatic Failover:** Tasks from failed instances are reassigned to other instances.
- **State Restoration:** New instances restore state from changelog topics.
- **Standby Replicas:** Optionally, maintain standby copies of state stores for faster recovery.

**Rebalancing:**
- **When Instances Join/Leave:** Kafka Streams triggers a rebalance to redistribute tasks.
- **Impact:** Brief pause in processing during task reassignment and state restoration.

#### 5.3 Impact on Windowing

**Windowed Operations:**
- **Purpose:** Group records into finite sets based on time intervals for aggregations.
- **State Requirements:** Maintain state for each window to compute aggregates.

**Window Stores:**
- **Specialized State Stores:** Hold data for windowed aggregations.
- **Retention and Cleanup:** Configure retention times and grace periods to manage state store size.

#### 5.4 Use Cases for Stateful Streams

- **Aggregations:** Counting events, summing values per key.
- **Joins:** Enriching streams by joining with other streams or tables.
- **Windowed Analytics:** Real-time metrics over specific time intervals.
- **Pattern Detection:** Identifying sequences or anomalies in event streams.
- **Sessionization:** Tracking user sessions based on activity gaps.
- **Deduplication:** Removing duplicate records by tracking seen keys or values.

### 9.6 Integrating Kafka Streams with Spring Boot

**6.1 Code Organization**

To maintain clean and maintainable code in complex applications, separate concerns by modularizing Kafka Streams components.

**Separate Configuration:**
```java
@Configuration
public class KafkaStreamsConfig {
    @Bean(name = KafkaStreamsDefaultConfiguration.DEFAULT_STREAMS_CONFIG_BEAN_NAME)
    public StreamsConfig kStreamsConfigs() {
        Properties props = new Properties();
        props.put(StreamsConfig.APPLICATION_ID_CONFIG, "my-microservice-app");
        props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "broker1:9092,broker2:9092");
        props.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG, Serdes.String().getClass());
        props.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG, Serdes.String().getClass());
        return new StreamsConfig(props);
    }
}
```

**Define Topology Separately:**
```java
@Component
public class MyTopology {
    private final ProcessingService processingService;

    public MyTopology(ProcessingService processingService) {
        this.processingService = processingService;
    }

    @Bean
    public KStream<String, String> kStream(StreamsBuilder builder) {
        KStream<String, String> inputStream = builder.stream("input-topic");
        KStream<String, String> processedStream = inputStream.mapValues(processingService::processValue);
        processedStream.to("output-topic");
        return processedStream;
    }
}
```

**Encapsulate Processing Logic:**
```java
@Service
public class ProcessingService {
    public String processValue(String value) {
        // Complex business logic
        return value.toUpperCase();
    }
}
```

**6.2 Application ID and Consumer Groups**

- **Application ID:**
  - Serves as the **consumer group ID**.
  - Groups all Kafka Streams instances into the same logical application.

- **Instance Coordination:**
  - Instances coordinate via Kafka's group management protocol.
  - **Task Assignment:** Managed by Kafka Streams, ensuring each partition is processed by only one instance.

- **Scaling Limitations:**
  - **Parallelism** is limited by the number of partitions.
  - Adding more instances than partitions will leave some instances idle.

---