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


#### RDT2.2: Sender and receiver fragments


#### RDT3.0: Channels with errors and loss

We now assume underlying channel can also lose packets (data and ACKs). 

Alternates packet/ack 0 and 1 so that 

TDM FDM
## Pipelined Protocol
*Go-back-N*: You have a window size n. There is a sender base pointer and sent 
Sliding window protocol. 
Steps:
Set window, say n=4 (size). 
Send each packet within window (in this case 4)
Once reciever gets a packet, send ack(n) back. 
If something is lost, send ack(n) where n is the last correct packet recieved. 
On sender side, keep sending whole window and discard any acks that aren't correct order. 
NOTE: if ack is received in incorrect order, doesn't matter because ack3 implies packet2 also received
Sender:
Set window (n=4)
Send every packet in window. 
Wait for timeout. 
Receive cumulative ack(n) that indicates everything up to n has been received. 
Slide window to ack(n)
after timeout, Repeat.
Ignore anything not max(n)
Reciever: 
Wait for packets. 
Send ack for max n packet received, but only if everything before it has also been received. 
If packet never received, ack last packet and disregard future packets until received in sequence. 
Gobackn does not buffer on receive side. 

*Selective repeat:* Same as before but:
Sender:
Each packet has a timer. 
Send every packet in window, and after timeout send again. 
If receive ack for that packet, mark as received. 
Slide window when sequence up to n has been received all in order. 
Receiver: 
Ack every packet received. 
Keep track of them in buffer
Selective repeat buffers on receiver side. 
if received out of order, mark as received out of order and if received a duplicate, send ack anyways. 

## TCP
Only does point to point
*point-to-point*: one sender one receiver
multi-cast: one sender multiple recipients who tune in
broadcast: one sender, everyone gets

Chooses one random start point, fills buffer, and then sends starting point to other side. Then sends len(buffer_data)+starting point back. 
If the starting point is 83, and we want to send "CAT", we write cat to buffer and then send ACK(83+len(CAT))

We use a weighted rtt calculation

$\text{EstimatedRTT} = (1-\alpha)\text{EstimatedRtt}_{n-1} + (\alpha)\text{SampleRTT}$
$\text{DevRTT} = (1-\beta)\text{DevRTT} + \beta|\text{SampleRTT - EstimatedRTT}|$
$\text{TimeoutInterval} = \text{EstimatedRTT} + (4)\text{DevRTT}$


