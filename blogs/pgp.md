# What is PGP?

It's a Pretty Good Privacy.

PGP is a cryptographic system that uses asymmetric keys to hold a secure encrypted communication. The key to this system is that a user generates
a PGP user generates a key pairs which are called public and private keys. Part of the reason why these are called asymmetric keys is that one key cannot be used to 
know about the other key. They keys can be generated using:

        ssh-keygen -T 
        
It will generate by default `id_rsa` and `id_rsa.pub` keys in your computer's `~/.ssh/` directory. The `id_rsa` is your private key and `id_rsa.pub` is your public key. 

Lets says Bob wants to send a secret message to Alice. What Bob need is the public key of Alice so that the message can only by 
decrypted by Alice using her private key. 

# How it happens?

1. Alice will share a public key to Bob
2. Bob will use Alice's public key to encrypt the message. 
3. And then Bob will send the encrypted message to Bob.
4. Bob can use his private key to decrypt the message. 
5. He can read the message

But what is Alice's public key gets compromised somehow. Then the ill-fated user can read all the encrypted message sent to Alice. So to prevent that,
Bob can sign the message before encrypting using his private key. And then encrypt the message. This time Bob will send the signature and the encyrpted message to Alice. And keep in mind that
Alice will need Bob's public key to verify that the package signed was from Bob. 

This system is compromisable only if the man in the middle have public key of the sender and the receiver. Otherwise, the system has been used very consistent since 1990s and it's been a popular 
cryptographic system still today. 
