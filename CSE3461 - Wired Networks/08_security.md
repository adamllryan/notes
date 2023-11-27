# Network Security

*Confidentiality*: Only the sender and receiver should be able to understand a message. (Encryption)
*Authentication*: Sender and receiver want to confirm the identity of each other. 
*Message Integrity*: Sender and receiver want to ensure message has not been altered at any point. 
*Access and availability*: Services must be accessible and available to users -- has to be practical, not using the cone-of-silence. 

# Security Risks
*Eavesdrop*: Interception of messages or insert messages into connection. 
*Impersonation*: Spoofing a source address in a packet. 
*Hijacking*: Take over an ongoing connection by removing sender or receiver, injecting self into their place. 
*Denial of Service*: Prevent service from being used by others. (such as overloading resources)

# Breaking Encryption
With cipher text only:
*Brute Force*: Search through all possible keys
*Statistical Analysis*: Analyze something like most common letter

Known-plaintext attack:


# RSA 
We use public/private key to encrypt data. You give public key to everyone so that they can encrypt a message to send you, and then your private key can decode. It can also be used to authenticate yourself. If you send a message encrypted by your private key, anyone with public key can know that it is you because only you can encrypt something with private key. 

# DSA
Shared secret, but much cheaper than RSA. We use public/private keys to exchange shared key, then use DSA shared key on top of that. 

# Authentication Protocols
Our first try was to just declare who you are. It came with the problem that anyone could lie and say they were someone else

The second try was to send an IP packet and then say who you were. This had the same issue where you could just spoof an IP. 

The third try included a secret password, which fixed the spoof issue. But now we can use a *playback attack* by recording the message and then sending it later. 

A modification of protocol 3.0 (now 3.1) encrypts the secret password. It has the same problem. 

Protocol *4.0* starts with identification, then the recipient sends a *random value* back and the sender then uses that to encrypt their data. It suffers from *man in the middle* attacks. 

Protocol *5.0* uses public key cryptography, so we are finally secure against being able to fake data, but now *man in the middle* attacks are still possible. 

# Digital Signatures

