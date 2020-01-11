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
