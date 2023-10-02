Covers all of chapters 1, 2, and 3. 
Learn DNS
Skip connection management in chapter 3

Checksum both tcp and udp, checksum also http header, and total of 3

Pipelining is anything where we are sending more than one packet at a time. 

On TCP, the receiver does not have to buffer data. If it doesn't, the receiver will just throw it away and send back the last ack. By buffer I mean keep future packets in the case that one is lost using **fast retransmit**. 

Flow control is where we care about packets we send, where we try to not try to overflow our recipient's buffer. 

Congestion is similar, where we as a collective try to slow down when detected. 

Flow control is like one-one while congestion is many to many?

Flow control me to partner, congestion control is me to world. Flow is just making sure what I do does not overflow the buffer, congestion control is detecting congestion control not necessarily my fault but detecting it as a whole and slowing down. 

Tahoe triple duplicate ack makes us slam on the brakes. 

With TCP, the ack number is the initial sequence of data plus the offset. it is the byte you expect to receive next. **NOT THE SEQUENCE NUMBER OF THE PACKET** RENO is smarter than tahoe

On timeout:
Reno and Tahoe go to 1 or starting. 
On Triple Duplicate Ack:
Reno goes to ssthresh value. Tahoe goes to starting value. 


Go back n is cumulative ack

