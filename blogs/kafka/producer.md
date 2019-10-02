# Producer 

Kafka producer are interface to producing message to Kafka brokers. Producer is not part of kakfa cluster, they are external.
However, producer is still provided and maintained by kakfa as a client in different languages and it is a component of kakfa. 

Producer will produce message to kafka brokers through some steps, which are illustrated below: 

1. Form a producer record with key, value, serializer and partition
2. When you send the message, producer will try to serialize your key and value to byte stream to send over wire to kakfa brokers
3. After serialization, it will determine which partition to write the message to. If partition is provided by user, then it 
will append the message to its batch ready to be send. 
4. The batch of message will be send when next thread is available. 


This is how producer works. The batch size is configurable, however setting larger batch memory does mean producer will wait for 
batch to get fill up. It will also look at `linger` time to send the message regardless of batch is full or not. Whether or not
batch will be send depends on thread availablity. 

