# Kafka

Kafka is a message broker. A producer will produce message to a kafka topic and consumers will consume from the topic. 

## How Kafka was developed and for what purpose?

At LinkedIn, the company had a huge appetite to learn about it's user's behaviour and experience in realtime. So for that, they 
want to track how the user is operating. We can imagine the amount of data being produced every minute and how fast they want 
to process these data and make it available as analytics. To solve this problem, they have tried using Hadoop with ActiveMQ as 
message broker. But the system was never able to cope up with the performance and the entire process was becoming slower as users 
grow. Jay Kreps, Jun Rao, & Neha decided to build a distributed message broker system that will address this issue and so they 
hopped on this project and it became very successful both in terms of scaling and performance. 


## Message
The basic unit of data stored in Kafka is called `message`. Messages are produced to topics in batches, thereby increasing throughput but not latency. Batches are also compressed to transfer the messages and stored efficiently at the cost of some processing power. 

## Schemas
Although, Kafka keeps the producers and consumers highly decoupled so that any producer can publish message of any type and consumers can receive any from the topics. But it is recommeneded that messages be stored in some format so that it can easily be understood without coordination. Apache Avro is a good format for Kafka. I don't know what or how about it yet. 


## Topics and Partitions
Topics can be thought of as a database table or a folder into which messages will be stored. A topic can have multiple partitions wich can be hosted on different servers. Partition is the way Kafka provides redundancy and scalablity. For example; single topics can be hosted on multiple server to provide performance far beyond what a single server can provide. 


## Stream
Stream is considered to be single topic of data, regardless of the number of partitions. 

## Producers and Consumers
In Kafka distribute data store system, producers are the one who produces messages into kafka topics. The message published will be forwarded to a partition to be stored. The partition is chosen by the kafka system by default in a way that maintains balance the topic across partitions evenly. The producer can use custom partitioner to map message to partitions. 

Consumers can subscribe to one or more topics and subscribe to messages in order they were arrived. Consumer keep track of which messages it has already read by using offset which is set by the partition while storing the message. The offset of the consumer is a metadata that is stored in Zookeeper or by the Kafka itself. A consumer can therefore resume, stop and restart the read position. 

## Broker
A single kafka server is called a broker. Broker will receive messages from producer and store it in partition on it's disk. Broker also communicates with consumers so that a partition is read only by single consumer. Multiple brokers can be connected together to form cluster. And Kafka broker are scalable in a cluster. One of the broker in a cluster will act as a controller who is responsible for assigning partitions to other brokers and also monitors and responds in case a broker fails.

A partition is owned by a single broker and that broker is called leader of that partition. A partition is replicated across brokers so that other brokers can pick up the role of any broker that goes down. Leader will select the partition to which the message will be written. In case the leader is down, new leader will be elected and all consumers and producers will talk to that leader. 

# Multiple clusters
As Kafka usages grow, it is good and beneficial to have multiple clusters for following purposes

- Segregation of types of data
- To address security requirements
- Multiple data centers for disaster recovery


When working in multiple clusters, it is often required to copy messages between clusters. Kafka does not do it magically. However you can use a tool called MirrorMaker to channel the message from one cluster to an another. 

# Awesome features to note
- Multiple producers (For example: logs from different areas of stack for a user click can be written to a topic) can write to single topic. And then consumers can read them from one topic. 
- Messages are stored in disks and consumers can read stream of data or minor chunks anytime. Unlike message queueing system, where once a message is read by a client, it is not available to others.
- Consumer group is a feature I still don't have much idea.
- Flexible retention rules and deletes data automatically if size limit crossed.
- Kafka can scale while the cluster is active without disturbing any brokers. We can configure higher replication factor to provide better availablity in times of multiple broker failure. 
- All part of Kafka pubsub system can scale; producer, consumer and broker which can make the cluster handle large amount of stream and serve it to consumers in subseconds time.

