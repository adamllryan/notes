# Transport Layer

At the application level, this is a message. It is then given a header at the transport layer and it becomes a segment. A message can also be split into multiple segments.

TCP: The transport layer on the sender side is responsible for ripping up the message into segments and sending. The receiving side is responsible for putting it together and knowing that that message could be delivered in the wrong order or missing pieces and making sure that is addressed. Will not hand to application layer unless it knows it is complete.

UDP: everything is sent as a single segment. Either it is all received or none of it is.

TCP is connection oriented and UDP is connectionless.
## Transport-layer services
### Transport services and protocols
### Transport vs. network layer
### Internet transport-layer protocols
## Multiplexing and Demultiplexing

Multiplexing: taking multiple streams of data and putting them into a single stream of data.
Demultiplexing: taking a single stream of data and splitting it into multiple streams of data.

Basically just sorting and mixing data.

[Congestion Control]: # Congestion Control
### How demultiplexing works
### Connectionless demultiplexing
### Connection oriented demux
###
## Congestion Control

Flow control is when your machine takes a more external view about other's network speeds and then adjusts its own speed accordingly. Avoids oversending data when the recipient is unable to take extra data.

### UDP Segment Header






> [!error]
> redo all slides 0-checksum
## Check Sum
Computers are good at adding, anding, oring. 
Take the 1s complement of the sum of all the header stuff split into 16 bits. 

1. Sum the 16 bit numbers and wrap the carry number at the end (if there is) until it also fits into 16 bits. 
2. Take the 1s complement and that is the checksum. 
## Reliable Data Transfer

> [!NOTE] 
This is important in application, transport ant link layers!

### Types of RDT
> [!ERROR]
> FINISH SLIDES 25-28
#### RDT1.0:  Reliable transfer over a reliable channel. 
1. Application layer hands data to transport layer. 
2. Transport layer puts headers on it. 
3. Recipient transport layer strips headers. 
4. Transport layer passes data back to application layer. 
#### RDT2.0: Channel with bit errors. 

We use this when the `underlying channel may flip bits`. 

How do we detect errors?

We use **acknowledgements (ACKs)** where the receiver explicitly tells the sender that packet was received okay, and **negative acknowledgements (NAKs)**. 

Now, the server will hold a copy of the packet until **ACK** is received. 

> [!Question] What happens if an ACK/NAK is corrupted?
> The sender doesn't know what happened. 



