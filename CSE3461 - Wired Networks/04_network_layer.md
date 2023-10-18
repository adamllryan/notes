# Network Layer

## Two key functions

## Data plane

## Control Plane

### Per router

### Logically centralized

## Network Service Model

### Models

# Router Architecture

## Input port functions

## Destination-based forwarding

## Longest Prefix matching

## Switching fabrics

### via memory

### via a bus

### Interconnection network

## Input port queueing

## Output ports

## Output port queueing

## Buffering?

## Scheduling mechanisms

## Scheduling policies priorities

## more

## still more

# The internet network layer

# IP datagram format

# IP fragmentation and reassembly

# IP addressing introduction

# Subnets
Any time we leave a router interface, we are in a new subnet. 
# CIDR
Classless interDomain Routing. 
# Non-routable IP Addresses

# IP addresses tutorial
request from ip
divide nets by bit
# DHCP 
Application layer model. Used to dynamically assign IP Addr

Steps:
1. Computer broadcasts on 0.0.0.0:67 that it wants an ip. Chooses random transaction_ID
2. All DHCP servers reply with offer of ip and returns transaction_ID. Sends over 255.255.255.255:68
3. Computer chooses one and creates new message with transaction_id+1, 0.0.0.0:67, sends. 
4. DHCP server replies with confirmation. It may offer same ip to many but the first to accept gets it. 
# Hierarchical addressing

# NAT
Network Address translation. Translates local nonroutable IP to another address. 

Holds a table that maps WAN side address to LAN side address. Any new unknown address gets a new mappable address and is stored. A WAN side address is an adapter. 
# IPv6

## Datagram format

## Other changes from IPv4

## Transition

## Tunneling

## Adoption

# Generalized Forwarding 

# SDN

# OpenFlow abstraction

# 