### **Exercise 1: Basic Producer and Consumer**
**Scenario:**  
You have a Kafka topic named `user-signups`.  
**Tasks:**  
- **Producer:** Implement a producer that sends `UserSignup` events containing `userId`, `username`, and `signupTimestamp` to the `user-signups` topic.
- **Consumer Group:** Implement a consumer group that listens to the `user-signups` topic and logs each received `UserSignup` event.

**Hint:**
Command to create the topic:
```console
./kafka-topics.sh --create --topic user-signups --bootstrap-server localhost:9092
```
---
