# gRPC

gRPC is a way to build microservices with the notion of invoking method calls remotely in a distributed systems which is also called RPC. 


## Characteristics
- Distributed remote procedures
- Uniform
- Cross platform


## gRPC Client
The client side has a stub with a channel. All we need is to call the remote method using stub. And channel knows where the method is 
located. 


## gRPC Server
The server side is has the service or the method definition which will execute once the request is received from the client, and returns
the response to the client.






