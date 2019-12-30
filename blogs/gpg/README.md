# GnuPG

GnuPG is a tool for communicating securely over network using asymmetric key pairs known as public and private key.

A simplest communication can happen by sharing public key of the receiver to the sender. Sender will encrypt the message using 
the public key and only the receiver who has the other pair of the key called private key can decrypt and read the message. Although
the level of the security can be enhanced by sending signature along with the encrypted message, which can be verified on the receiver 
side to confirm that it was sent by the person expected.


## Summary
When a sender wants to securely communicate to it's intented receiver, it should ask or know the public key of the receiver. 
It is important to verify that the key actually belongs to the receiver. One can confirm using the fingerprint which is easy 
to verify easily instead of comparing the content of the public key which would be a lengthy string.


In real world, Edward Snowden (Sender) tried to get public key of Laura Poitras (Receiver), a documentary film maker who has become an
critic of American foreign policy. Once he received the public key, he was able to send encrypted message to Poitras. 

Note: Snowden received the public key through someone who is working for EFF (Electronic Frontiers Froundation) and the public key
of the person was posted on EFF's website. And the public key has been signed by well knowned people which Snowden could verify easily. 
One thing I still don't know how Snowden shared his public key without which Micah would have never been able to share Poitra's 
encryption key. 










