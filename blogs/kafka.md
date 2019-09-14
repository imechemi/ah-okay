# Kafka

Kafka is a message broker. A producer will produce message to a kafka topic and consumers will consume from the topic. 

## How Kafka was developed and for what purpose?

At LinkedIn, the company had a huge appetite to learn about it's user's behaviour and experience in realtime. So for that, they 
want to track how the user is operating. We can imagine the amount of data being produced every minute and how fast they want 
to process these data and make it available as analytics. To solve this problem, they have tried using Hadoop with ActiveMQ as 
message broker. But the system was never able to cope up with the performance and the entire process was becoming slower as users 
grow. Jay Kreps, Jun Rao, & Neha decided to build a distributed message broker system that will address this issue and so they 
hopped on this project and it became very successful both in terms of scaling and performance. 

