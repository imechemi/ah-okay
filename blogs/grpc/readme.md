# gRPC

gRPC in full form stands for **G**RPC **R**emote **P**rocedure Call. It does not stand for Google RPC. 

It is a framework to build microservices with the notion of invoking method calls remotely in a distributed systems AKA RPC.


## Characteristics
- Distributed remote procedures
- Uniform
- Cross platform
- Efficient over wire
- Consistency between client and server


## gRPC Client
The client side has a stub with a channel. All we need is to call the remote method using stub. And channel knows where the method is located. Channel is abstraction over the TCP connection that gRPC sets up for us.


## gRPC Server
The server side is has the service or the method definition which will execute once the request is received from the client, and returns the response to the client.






