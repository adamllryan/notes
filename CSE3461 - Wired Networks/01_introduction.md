# Internet
The internet consists of billions of connected computing devices. Essentially, it is a *network of networks* and is loosely hierarchical. It's built out of hosts (end systems) and clients (users). 

The internet relies on **packet switches** to forward packets or chunks of data. We call [[Router|routers]] and [[06_link_layer#Switches|switches]] to relay these packets between systems. We have divided the internet into a public internet and private intranet.

What do we need to have to connect to the internet? We need four items:
- IP Address - your address
- Subnet Mask - identifies host vs. network
- Default Router - how to get off LAN
- Local/Default DNS - phonebook of IP addresses

The internet, as a service, is infrastructure that provides services to applications. It provides functionality to *services* such as web, video, VoIP, email, e-commerce, social networks, and video games. It also provides *APIs* that interface into apps so we can use applications in other applications. 

To do so, we use some of the following protocols: **TCP**, **IP**, **HTTP**, **FTP**, and **PPP**. 

We also have **internet standards** to help manage the internet and its applications: 
- RFC: Request For Comments
- IETF: Internet Engineering Task Force
These are called protocols. 
## Protocol
A **protocol** is a governing body that regulates all communication activity over the internet. They define:

- Types of messages
- syntax of those messages
- semantics of the messages
- rules associated with the messages

A **network** is a group of interconnected machines. These machines can only communicate with members of the same network. 

# Network Edge

The **network edge** consists of clients/users and servers that serve data to clients. The standard model is client/server, where the client hosts requests and receives a response from the server that services request.
A second model is the peer-to-peer model that hosts interactions symmetrically (Bitcoin as an example).

The purpose of the network edge is data transfer between end systems. Apps that use TCP are good for HTTP, FTP, Telnet, and SMTP transfer. Apps that use UDP are normally streaming media, teleconferencing, and internet telephony. TCP uses application, transport layers and require Internet and network access. 

# Network Core

The **network core** is the mesh of interconnected routers. It connects client and servers.

Data is transferred through the network via:

- Circuit switching, where a dedicated circuit is used per call (like a telephone network)
- Packet switching, where data is sent through network in discrete 'chunks'

### Circuit Switching

With **circuit switching**, network resources are divided into *pieces*. Each "piece" is allocated to only one call (no sharing!) and if not in use, it is wasted. We have to divide bandwidth either vertically or horizontally:
- **Frequency division** (FDM) divides the whole bandwidth. Every user gets a certain fraction of network resources. 
- **Time division** (TDM) divides the network in intervals. Every user gets the whole bandwidth for a certain time interval, then waits for their next turn. 

### Packet Switching

**Packet switching** is when we divide each data steam into *packets*. In packet switching, every user has to share resources and each packet can use the full link bandwidth. The main functional difference is that resources are used *as needed*. 

However, this can lead to **resource contention**: aggregate resource demand can exceed available bandwidth, leading to congestion, where packets queue, waiting for link availability. Consider the concept **store and forward**, where packets move one hop at a time. They transmit over a link and then wait for their turn at the next link. 

Packet switching allows more users to use the network at the same time. However, we have the issues of resource contention. 

Since we are dealing with networks (represented as graphs), we need to use path-finding algorithms to get data from one place to another. [[path finding algorithms studied in chapter 4]] are some of the algorithms we use to get data there. 

We use [[datagrams]] to package data. It contains a *destination address* to determine next "hop". In a **datagram network**, routes may change during our session. 

In a **virtual circuit network**, each packet holds a tag that determines next hop. It has a fixed path determined at *call setup time* and remains fixed through call. 

The structure of the internet is *roughly hierarchical*. It's supported by national and international backbone providers, or NBPs. These NBPs are owned by companies like BBN/GTE, Sprint, AT&T, IBM, and UUNet. These NBPs connect to regional ISPs, which connect to local ISPs, who provide you your internet connection. 

# Network Error

All packets experience delay on an E2E path. There are four main sources of delay on each hop:

- **Nodal processing**, where we check for bit errors and determine output link. 
- **Queueing**, or the time spent waiting at an output link for transmission. This depends on congestion of router. 

$I_t=La/R$ where $L$ is packet length in bits, $R$ is link bandwidth in bits per second, and $a$ is the average packet arrival rate.

Generally, if $I_t$ is:
- ≈0, the average queueing delay is small. 
- =1, the delays become large. 
- >1, more work is arriving than can be done, resulting in infinite average delays. 

- **Transmission delay**, the time it takes to send bits into a link. 

$D_t=L/R$, where $R$ is the link bandwidth in bits per second and $L$ is the packet length in bits. 

- **Propagation Delay**, the time it takes for bits to travel across a link. 

$D_p=D/S$ where $D$ is the length of the physical link and $S$ is the propagation speed (normally ≈$2\times10^8\text{m/sec})$. 

NOTE: S and R are very different! (they are unrelated)

# OSI Protocol Layers

The internet is hard to organize!
Because of this, we split them into the **Internet protocol stack**:

Split into the **OSI Model Layer**, or **Internet Protocol Stack** (in order top to bottom):

- **[[02_application_layer|Application Layer]]**: supporting network applications
  - FTP, SMTP, HTTP
- **[[03_transport_layer|Transport Layer]]**: host-host data transfer
  - TCP, UDP
- **[[04_network_layer|Network Layer]]**: routing of datagrams from source to destination
  - IP, routing protocols
- **[[06_link_layer|Link Layer]]**: data transfer between neighboring network elements
  - PPP, Ethernet
- **[[PHYSICAL LAYER|Physical Layer]]**: bits "on the wire", "over the air"

Each layer is distributed. Layers are implemented with **entities** that handle layer functions. Each entity performs actions and exchange messages with peers.

As an example, let's say machine A wants to send data to machine B. A will pass data into its application layer, then transport, then network, link, and physical. That data, once passing through other links and reaching B, will enter through B's physical layer and pass back up. 

# Domain Name System
This was assigned as a self-learn topic. 
The **Domain Name System** is like a phonebook, but for the Internet. We are bad at remembering numbers, so we can assign domains to our IPs like www.google.com. The purpose of a DNS is to translate domain names to IP addresses so our computers can communicate with the machines we want. 

In order to use DNS, we need servers (DNS servers). We categorize four main types of DNS servers:
- DNS Recursors: receives queries from client machines and looks through the other servers to get an answer. 
- Root Nameservers: normally serve as references to more specific DNS locations. 
- Top Level Domain (TLD) Nameservers: are responsible for storing all addresses assigned to a specific TLD. 
- Authoritative Nameservers: are the final servers, responsible for returning the actual IP address back to the DNS Recursor. 

In a typical request, a client sends a request to a DNS Recursive Resolver, which then sends a request to a Root Nameserver, which sends a request to a TLD Nameserver, then an authoritative Nameserver, which then returns info to the Recursive Resolver. 

A **recursive resolver** responds to requests from a client and tries to track down a DNS record. It makes a series of requests until it reaches an authoritative DNS nameserver. It can also save time by caching addresses for later use. 

A **root server** will receive requests from a recursive resolver and gives it the address for a TLD server that matches the correct TLD. 

Once the recursive resolver gets the TLD nameserver IP, it makes a request to it. The **TLD nameserver** then returns the IP of the authoritative nameserver. 

The **authoritative nameserver** is responsible for actually holding the domain name records, and will do this for a fee.

How are domains organized? Consider the example "www\.google\.com". 

Domains are split by "." delimiters, and in this case, "www" represents the **host name**, and is the left-most grouping. 

Everything else is the "**domain**". The domain may contain multiple sections, and if so will be grouped in a hierarchical sense from right to left. In the above case, "com" is the top-level domain, and "google" is a **subdomain** of "com". If there were more to the left, they would be the subdomain of "google". 
