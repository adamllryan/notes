When we create a network app, we want it to be able to run on different end systems. This means they need to be able to communicate with each other regardless of system architecture. This way, developers won't need to focus on developing the network-core software as well as the application itself. 

There are two structures for these applications:
- Client-server. 
- Peer-to-peer (P2P). 

# Client-Server Architecture

When we use **client-server** architecture, we have a client and a server. 

A **client** is you or your machine. The client's responsibility is the entity that is making web requests. Clients may be intermittently connected, have dynamic IP addresses, and do not communicate directly with each other. 

A **server** is your always-on host. It maintains a permanent IP address and is often found in a datacenter to allow for scalability. Servers traditionally cannot make their own requests. Instead, they sit in a permanent wait state until they receive a request. Then, they are allowed one response to the client, then reset. 

# Peer-to-peer Architecture
**P2P** differs from client server in that we treat everyone like a client. There is no longer an always-on server and instead of having clients, everyone is now a peer. 

**Peers** request services from each other and provide service in return to other peers. This introduces *self-scalability*, where peers bring new service capacity while also bringing new service demands. 

P2P requires complex management techniques because peers are connected with no discrete structure and may change IP addresses at any time. 


# Process Communication

A **process** is simply code running within a host. Within the same host, two processes communicate via [[5. Interprocess Communication|interprocess communication]]. Processes with different hosts can communicate via [[5. Interprocess Communication#Message Passing|message passing]]. 

The client process initiates a communication and the server process waits to be contacted. P2P applications have both a client and server process (at least one of each). 

A **socket** is a hook that processes may use to send and receive messages between themselves. A process has to connect to a socket and then send or receive messages from that socket. Once sent, we have to assume it will arrive at the end. 

For a process to receive a message, it needs an identifier. The **identifier** includes both the ip address and port number. For example, a router may use the IP and port combination of 192.168.1.1:80. Mail servers use the port 25. A host device has a unique 32 bit IP address, but we also need the port in order to connect with one of the many possible processes. 

The application layer protocol defines the following:
- types of messages - request and response
- message syntax - fields and delineation
- message semantics - meaning of info fields
- rules - how and when a process can act
Open protocols are defined in RFCs and allow for interoperability. Some common examples are HTTP and SMTP. Proprietary protocols are not meant for universal use and require explicit maintenance to continue use. For example, Skype has its own proprietary protocol. 

In order to determine the best transport service for an app, we need to consider its requirements:
- data integrity - do we need reliability?
- throughput - do we need a certain transfer rate?
- timing - do we need low delay?
- security - do we need encryption?

Here are the requirements for some common internet applications:

| Application | Data Loss | Throughput | Time Sensitive | Application Protocol |
| -------- | -------- | -------- | -------- | -------- | 
| File Transfer | None | Elastic | No | FTP |
| Email | None | Elastic | No | SMTP |
| Web Documents | None | Elastic | No | HTTP |
| Real-time Audio/Video | Tolerant | 5kbps/5mbps | Yes | SIP,RTP,proprietary |
| Stored Audio/Video | Tolerant | " | Yes | HTTP,RTP |
| Interactive Games | Tolerant | Some | Yes | ? |
| Text Messages | None | Elastic | Sometimes | ? |

# Web and HTTP

A webpage is made of objects addressed by a URL. Websites are rendered by a web browser, which requests a base HTML page along with several referenced objects. 

The **HTTP** protocol stands for HyperText Transfer Protocol and is the application layer protocol used for all websites. It uses the client/server model, where the client (browser) requests, receives, then displays web pages/objects. The server waits and services requests by returning web pages and objects. 

HTTP is a TCP transport service. First, a client creates a socket and initiates a TCP connection to a socket on the server (port 80). The server accepts that TCP connection and exchanges HTTP messages. Once all is completed, the connection is closed. HTTP is a *stateless* protocol, meaning that the server maintains no past information about past client requests. 

Note that stateful protocols have to maintain past history. If any endpoint crashes, the state view may be inconsistent or corrupted, requiring reconciliation. 

HTTP/1.0 is a non-persistent protocol. The server parses a request, responds, and closes. It uses 2 RTTs to fetch each object, meaning each object transfer suffers from a slow start. 

HTTP/1.1 uses a persistent protocol. The client sends requests for all objects as soon as the base HTML page is received. This results in fewer RTTs and less slow start. We are also able to pipeline object requests. 

Today, most browsers can utilize parallel TCP connections (open multiple at the same time). 

An HTTP message follows this format:

```
GET path protocol
User-agent: operating-system
Accept: filetypes,
Accept-language: langs
```

For example, a request may look like this:

```
GET /path/ HTTP/1.1
User-agent: Mozilla/4.0
Accept: text/html, image/gif, image/jpeg
Accept-language: en-us
```

The response for an HTTP request looks like this:
```
STATUS CODE
Date: DATE
Server: operating system
Last-Modified: DATE
Content-Length: LENGTH
Content-Type: TYPE
DATA...
```

Some common response codes are as follows:
- 200 OK - success
- 301 Moved Permanently - new location
- 400 Bad Request - message not understood
- 404 Not Found - requested document not found
- 505 HTTP Version Not Supported - no support

Cookies are a solution to the issue of statelessness in servers. A **cookie** is made up of four components:
- Header line of HTTP response
- Next header line for next HTTP request
- Cookie file on user's host
- Backend database in website

When we need to save something on the server, the server creates a cookie ID and enters it in a database. It returns this in HTTP to the client, so when they make the next request, they can include it and the server will remember them. 

A lot of the time, we don't need to even involve the origin server. We have cache servers that may be closer and save time. A **cache server** acts as a proxy server, where instead of accessing the web server, we go through the cache server. It stores base HTML pages of sites visited. If it does not have the base page, it requests it from the origin server and then returns to the client (as well as caching it for later use). 

Cache servers are usually installed by ISPs. Caching allows us to reduce response time AND traffic on access links. Because access links to the public internet are more expensive, ISPs typically install cache servers instead. Note that despite having a page cached on a cache server, the server still needs to contact the origin server to test if the page is up to date. It uses a conditional GET in this case, where if the page has not been modified, nothing happens. 
# FTP

**File transfer protocol** is a protocol used to transfer files between client and server. The client is the side that initiates transfer and the server is the remote host. FTP uses the port 21 for control and port 20 to transfer data. It requires two TCP connections to work.

Note that FTP is *not* secure. Commands are sent as ASCII text, including usernames and passwords. 

# Email: SMTP, POP3, IMAP

Email protocols have 3 major components:
- User agents. 
- Mail servers. 
- simple mail transfer protocol (SMTP). 

A **user agent** is the client that requests and sends emails. A **mail server** is made up of 3 segments. The **mailbox** contains incoming messages for users. The **message queue** holds messages that are waiting to be sent. Finally, the SMTP protocol between mail servers is used to send emails. 

**SMTP** uses TCP to reliably transfer email messages on port 25. SMTP uses three steps to transfer an email: handshaking, transferring, and closure. 

It uses similar command/response interactions like HTTP and FTP, however it differs in that SMTP uses persistent connections and it requires the header and body to by formatted in 7-bit ASCII. While HTTP uses a pull model, SMTP utilizes a push model. SMTP also uses a multiple object, multipart message. 

On top of SMTP, we need different protocols to retrieve emails from the servers. We use 3 main protocols for this: POP, IMAP, and HTTP. 

**POP3** is a simple protocol. It begins with an authorization where the user sends USER and PASS, and gets an ok or error response. Then, the user can list, retrieve, delete and quit. POP3 is stateless across sessions. 

**IMAP** keeps all messages in the server and allows the user to organize message in folders. State across sessions is maintained. 

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

# P2P Applications
Some endpoints use P2P architecture. The file distribution time is $D_{\text{P2P}}\geq\text{max}\{F/u_s,F/d_{\text{min}},NF/(u_s+\Sigma_iu_i)\}$ where $F$ is a file size and N is the number of clients. 
Meanwhile client-server architecture has $D_{c-s}\geq\text{max}\{NF/u_s,F/d_{\text{min}}\}$ where $d_{\text{min}}$ is the minimum client download time. Client server transfer time increases linearly, while P2P can transfer on a logarithmic scale. 
