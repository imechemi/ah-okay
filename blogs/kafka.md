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
