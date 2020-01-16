# learning-kafka

This repository contains basic of apache kafka.

👉 Note that this project is meant to be used for learning purpose only nothing else.
# Basic of Kafka
Kafka is a distributed streaming platform that is used publish and subscribe to streams of records.

There are many things you need to know to starting kafka. Let's start.

1. **Kafka topic**:  
Kafka topic is base of everything. There is no topic, there is no kafka.Topic is a particular stream of data, like database. Every topic must have a name. Topic contain some buzzword.
    - Partitions:   
    Topics are split in partitions. Each partition are ordered by id, it called offset. Like partition 0, partition 1, ..... partition N.
    - Replication factor:  
      🙏 *Before read this, please read about the broker.(recommended)* 

      Replication factor create broker for tracking data. It makes copy of data in multiple broker. If one of our broker goes down, other brokers will send data. When copy the data in broker, first broker became a leader and others brokers became In-Sync-Replica(ISR).
2. **Kafka broker**:    
 Previous section we learn about kafka topic. Now question is where topic store? Topics are store in broker. Simply Brokers are server(bootstrap server). In kafka, there will have many brokers. Each broker are identify by their ids. Like Broker 1, Broker 2, ...., Broker N. Collection of broker become a kafka cluster. Each broker contains certain topic partitions, Not hole topic. Because kafka is distributed. And each broker knows about all brokers, topics and partitions. That's the reason when you connect to one broker, you are connect to the entire cluster.
  3. **Kafka producer API**:   
 Producer API permits an application to write or publish a stream of records or data to one or more Kafka topics. Producer automatically know to which broker and which partition to write to. You don't need to worry about that.
     - Producers acknowledgement/confirmation:  
     This is a confirmation from broker- Hey, I write data properly. Producer can choose to receive acknowledge of data writes.
         - acks = 0; Producer won't wait for acknowledgement.
         - acks = 1; Producer will wait for leader acknowledgement.
         - acks = all; Producer will wait for leader and replicas acknowledgement.
     - Message keys:  
     Producer can also send a message with a message key. A message key can be anything like number, string etc. If key is not sent key becomes null and message send as Round Robin style. Round Robin style means, If kafka cluster have 2 brokers. First message will go to first broker, second message will go to second broker. Then next message will go to first and next message second broker. And continuously will happen the same process. If key sent, then all message for that key will go to the same partition of a topic. Not like round robin. Say, we have a message with key of MSG_KEY. If MSG_KEY go to partition-3 it will always go to partition-3.
  4. **Kafka consumer API**:   
  Consumer API subscribe to one or more topics and process or read the stream of records produced to them in an application. records are read in order within each partitions like 0, 1, 2 ..., n in order.
       - Consumer group:  
       It is a list of consumer. Each consumer read data from unique partition. If there are more consumers than topic's partitions then other consumer will inactive.
       - Consumer offset:    
       Kafka stores the offsets at which consumer group has been reading. The offsets store live in a kafka topic named __consumer_offsets. When a consumer in a group has processed data received from kafka, it should be store the offsets. Storing that offset help when a consumer goes down, it will be able to read data where he left off when the consumer is back.
       - Delivery semantics:  
        By delivery semantics consumer decide when should store offset in __consumer_offset. There are 3 delivery semantics.
         - At most once:  
         Offset are stored as soon as the message received. If process goes wrong, message will be lost. Because it set that we read this message __consumer_topic and kafka only read unread message.
         - At least once: 
         Offset are stored after the message is processed.If process goes wrong, the message will be read again. Because it not set to the __consumer_offset as read. There will be a same message process twice. And duplicate process won't impact on our system.
         - Exactly once:  
         Can be achieved for kafka using kafka streams API. 
5. **Zookeeper**:   
Zookeeper manage brokers. It helps in performing leader election for partitions. It sent notifications to kafka when changes happen.

## Practice:
*There is enough theory, ✋stop here. Now is time to apply what we already know😎😎. **[Let's get started with CLI](https://github.com/akib22/learning-kafka/blob/master/practice.md)***
# Author 
Akibur Rahman (Akib) - [akib22](https://github.com/akib22)