Hidden terminal problem

# CDMA
Every user is assigned an 8-bit chipping code.

# 

Wireless vs Mobility are different. Wireless is the no wires connection, mobility is the ability to move and be mobile. 

### Elements of a wireless network
There is a base station, typically connected to a wired network with a relay that is responsible for extending the range of the wireless network so that mobile devices are able to connect to them in more places. Relay is responsibel for sending packets between wired network and hosts in its area

Multiple access protocol coordinates link access and relays create different bands and different transmission speeds and rates

Base station connects mobiles into wired network, and can handoff to other base stations to smoothly transition over distances.

Wireless Network Ad Hoc mode: no base stations and nodes can only transmit to other nodes within link coverage like a swarm. Nodes self organize into a network and provide routes. 

Networks can have infrastructure or none (Ad hoc) and transmit data in a single hop or multiple hop route. 

Single w/ Infrastructure (Wifi/cellular)


### Wireless Link Fading
Wireless radio signal attenuates as it propogates. Loses power as its space increases. 
Proportional: (fd)^2=Free space path loss

5G has shorter range because higher frequency than 4G when both are ran with the same power level. 

### Multipath Propogation
Radio signal reflects off objects, ground, built environment and arrives destination at slightly different times. 
Line of sight and reflected paths
Coherence time is amount of time bit is present

### Noise
Interference from other sources. 

SNR is signal to noise ration. Larger SNR means it is easier to extract a signal from noise

BER is Bit error rate. Increase transmission power to increase SNR and lower BER. 
SNR changes with mobility and environment

### Hidden Terminal Problem

Some computers in a relay and only some can communicate while some are obstructed from communication with others

Attenuation also causes hidden terminals because interference negates at certain spaces or signal strength has dropped off enough that it almost zero. 

ZigZag lets you alternate and decode conflicting packets. Find a chunk that is interference free and then decode and subtract from the other collision. Requires two repeated packets sent. 

CDMA Code division multiple access

Unique code assigned to each user, code set partitioning but is unique!!!
such that even when combined they can still be decoded
All users share same frequency but each user hasa own chipping squence/code to encode data
If all codes are orthogonal there is mu