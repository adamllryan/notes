# What is the Internet?

The internet is a network of networks. It is loosely hierarchical and there is a difference between public internet vs private intranet.


## Things we need to connect to the internet
We need:
- IP Address
- Subnet Mask
- Default Router
- Local/Default DNS
## Protocols

There are different methods of sending/receiving messages:

- TCP
- IP
- HTTP
- FTP
- PPP

### Internet Standards

-RFC: Request For Comments
-IETF: Internet Engineering Task Force

`Protocol` is a governing body that regulates all communication activity over the internet. They define:

- Types of messages
- syntax of those messages
- semantics of the messages
- rules associated with the messages

# Network Edge

The network edge consists of clients/users and servers that serve data to clients. The standard model is client/server, where the client hosts requests and receives a response from the server that services request.
A second model is the peer-to-peer model that hosts interactions symmetrically (Bitcoin as an example).

The purpose of the network edge is data transfer between end systems. Apps that use TCP are good for HTTP, FTP, Telnet, and SMTP transfer. Apps that use UDP are normally streaming media, teleconferencing, and internet telephony.

# Network Core

The network core is the mesh of interconnected routers. It connects client and servers.

Data is transferred through the network via:

- Circuit switching, where a dedicated circuit is used per call (like a telephone network)
- Packet switching, where data is sent through network in discrete 'chunks'

## Circuit Switching

Network resources are divided into pieces which are then allocated into calls. A resource piece is idle if it is not being used by owning call (no sharing).

FDM vs TDM

`From the graph, looks like FDM constantly sends user data every unit time meanwhile TDM chunks users and alternates every time unit between users.`

## Packet Switching

Each E2E data stream is divided into packets. Every packet will use full link bandwidth and resources are used _as needed_.

`Resource Contention`: aggregate resource demand can exceed total amount available. `Congestion` can occur where packets queue and wait for link use. `Store and forward`: packets move one hop at a time, transmit over link, wait turn at next link.

Packet switching allows more users to use the network at the same time.

[Datagram network]: destination address determines next hop. Routes may change during session.

[Virtual circuit network]: each packet carries a tag (virtual circuit ID) and tag determines next hop. Fixed path determined at call setup time, remains fixed through call and routers maintain per-call state.

### Structure of the internet

Roughly hierarchical, supported by `national/international backbone providers (NBP)`. NBPs connect with each other privately or at public Network Access Points (NAP). Regional ISPs connect directly to these NBPs and Local ISPs connect to regional ISPs.

# Delay, Loss, Throughput in Networks

All packets experience delay on an E2E path. There are four sources of delay on each hop:

- Nodal processing: check bit errors and determine output link
- Queueing: time waiting at output link for transmission, depends on congestion of router
  - Traffic intensity = La/R where
    - R = Link bandwidth
    - L = Packet length
    - a = Average packet arrival
    - TI ~ 0 means average delay small, 1 delays large, >1 average delay infinite
- Transmission delay:
  - R = Link bandwidth (bps)
  - L = Packet length (bits)
  - Time to send bits into link = L/R
- Propagation Delay:
  - d = length of physical link
  - s = propagation speed in medium (~2e8m/s)
  - s and R are very different

`traceroute` command

# Protocol Layers, Service Models

Internet is hard to organize!

Split into the [Internet Protocol Stack]:

- Applications: supporting network applications
  - FTP, SMTP, HTTP
- Transport: host-host data transfer
  - TCP, UDP
- Network: routing of datagrams from source to destination
  - IP, routing protocols
- Link: data transfer between neighboring network elements
  - PPP, Ethernet
- Physical: bits "on the wire", "over the air"

Each layer distributes entities that implement layer functions at each node. Each entity performs actions, exchange messages with peers.

Transport layers take data from app adds addressing sends datagram for peer waits for peer to ack receipt.

# History

OSI model layers: Application, Presentation, Session, Transport, Network, Data Link, Physical

TCP/IP model layers: Application, Transport, Internet, Network Access

Routers use all 5 layers of the OSI model: Network, Data Link, Physical, Transport, Application.

We need 4 things configured on a device for it to connect to the internet: IP address, subnet mask, default gateway, DNS server.


Nodal processing takes time on the end station
Queueing delay on router?


Need 4 things to connect to internet
IP Address - IPv4
Subnet Mask
Default Router - how to get off router
Local DNS - phone book of IP addresses

www is host name
center is domain
suffix is category


.com is top level dns

TTL - Time to live


