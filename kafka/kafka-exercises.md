### **Exercise 1: Basic Producer and Consumer**
**Scenario:**  
You have a Kafka topic named `user-signups`.  
**Tasks:**  
- **Producer:** Implement a producer that sends `UserSignup` events containing `userId`, `username`, and `signupTimestamp` to the `user-signups` topic.
- **Consumer:** Implement a consumer that listens to the `user-signups` topic and logs each received `UserSignup` event.

**Hint:**
Command to create the topic:
```console
./kafka-topics.sh --create --topic user-signups --bootstrap-server localhost:9092
```
---

### **Exercise 2: Consumer Group Load Balancing**
**Scenario:**  
Your application needs to process messages from the `transactions` topic with high throughput.  
**Tasks:**  
- **Producer:** Send `Transaction` events to the `transactions` topic.
- **Consumers:** Deploy three consumer instances in the same consumer group to consume from the `transactions` topic.
- **Observation:** Verify that the messages are distributed among the three consumers.

---

### **Exercise 3: Kafka Partitioners**
**Scenario:**  
Your application needs to process messages from the `transactions` topic with high throughput.  
**Tasks:**  
- **Producer:** Send `Transaction` events to the `transactions` topic.
- **Consumers:** Deploy three consumer instances in the same consumer group to consume from the `transactions` topic.
- **Observation:** Verify how messages are distributed to different partitions according to different partitioning algorithms.

---

### **Exercise 4: Configuring and Using Kafka Transactional APIs**
**Scenario:**  
Ensure atomicity when producing messages to multiple topics.  
**Tasks:**  
- **Producer Configuration:**  
  - Enable transactions by setting `transactional.id` in producer properties.
- **Transactional Producer Implementation:**  
  - Develop a producer that begins a transaction, sends messages to `topicA` and `topicB`, and commits the transaction.
  - Handle exceptions by aborting transactions when necessary.
- **Verification:**  
  - Ensure that either all messages in the transaction are successfully committed or none are, maintaining atomicity across multiple topics
