# Introduction
The link layer is between two machines. It's the Uber, plane, and train system between locations. They have different services but do the same things. 

# Services

# Adapters
# Error Detection, Correction
We include a datagram EDC footer on each to use parity checking. Internal links can use single bit parity because it's much lower chance of having more than a single bit flipping, and we use two-dimensional bit parity so that we can detect and correct a flipped bit. 

## Cyclic Redundancy Check/Code
# Multiple Access Protocols
TDMA - code division multiple access.  like the talking stick. it splits bandwidth into chunks and users take turns. 
FDMA - frequency division. like CDMA but we are dividing bandwidth and sharing. 
CDMA - 

CSMA - Carrier sense multiple access. Listen before transmit. If a channel is sensed idle, transmit entire frame. 
# LANS
MAC address is like social security. 

## Addressing, ARP
Address Resolution Protocol. 
Used to determine interface's MAC address knowing its IP address. 
Creates an ARP table, where each IP node on LAN has a table. Maps an ip address into a mac address. 
If not in ARP table, host sends ARP query to every machine on LAN and every machine but intended recipient drops packet. Client then replies with mac address. 
Your MAC address never leaves your LAN. 

Router wants to send packet to Machine. 
Router doesn't have IP in ARP table, so Router sends ARP query packet containing Router's MAC address on broadcast. Every machine will then drop this packet but Machine. Machine will respond with its MAC address and returns to sender. 



## Ethernet
Early ethernet used bus tech where you would run a cable and then tap into that cable. All nodes are in the same collision domain (allows collisions). 
We use star now where a switch sits in the center then every machine attaches into the switch. Each spoke runs a separate ethernet protocol such that nodes cannot collide with each other. 
Ethernet is connectionless and unreliable. 
## Switches
Link layer device is a layer 2 device. 
Switch starts with empty switch table. Table contains mac address, interface, and time to live. It will receive a packet. 
Initially table is empty and the switch will *flood* every port until it receives a response. Then it will add the mac address to the switch table and be able to return data to only one interface until TTL expires (since machines move). 
## VLANs

Virtual LANs. 

# Link Virtualization

## MPLs

# Data Center Networking

# Web Request Day