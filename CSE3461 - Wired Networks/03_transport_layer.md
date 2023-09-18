# Transport Layer

At the application level, this is a message. It is then given a header at the transport layer and it becomes a segment. A message can also be split into multiple segments.

TCP: The transport layer on the sender side is responsible for ripping up the message into segments and sending. The receiving side is responsible for putting it together and knowing that that message could be delivered in the wrong order or missing pieces and making sure that is addressed. Will not hand to application layer unless it knows it is complete.

UDP: everything is sent as a single segment. Either it is all received or none of it is.

TCP is connection oriented and UDP is connectionless.

## Multiplexing and Demultiplexing

Multiplexing: taking multiple streams of data and putting them into a single stream of data.
Demultiplexing: taking a single stream of data and splitting it into multiple streams of data.

Basically just sorting and mixing data.

[Congestion Control]: # Congestion Control

# Congestion Control

Flow control is when your machine takes a more external view about other's network speeds and then adjusts its own speed accordingly. Avoids oversending data when the recipient is unable to take extra data.

### UDP Segment Header

