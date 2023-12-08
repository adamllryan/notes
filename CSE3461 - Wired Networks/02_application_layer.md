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











## Sockets

Processes send and receive messages to and from its `sockets`.

In order to receive a message, a process must have an _identifier_. A host device has a unique 32 bit IP address. _Identifier_ has both IP address and port numbers associated with process on the host.

An [app layer protocol] defines `type of messages exchanged`, `message syntax`, `message semantics`, `rules`. Protocols

Data integrity, throughput, timing, and security are necessities for transport services that an app may need.

# Web and HTTP

A web page consists of objects addressed by a URL. A user agent for web is called a web browser. Most web pages consist of a _base HTML page_ and several referenced _objects_.

## HTTP Protocol

Stands for HyperText Transfer Protocol.
Uses client server model where client browser requests, receives, and displays web objects and server sends objects in response to requests.

### Process

Http is a TCP transport service where the client creates a socket and then initiates a TCP connection to a socket on the server (port 80 by default). HTTP messages are then exchanged between browser and web server. Connection is then closed. HTTP is stateless where the server maintains no information about past client requests.

## Persistent and Nonpersistent connections

HTTP/1.0 uses non-persistent connections where client requests, server responds, then TCP is closed.

HTTP/1.1 uses persistent connections where requests are placed on same connection instead of closing and reopening requests.

Many browsers can utilize parallel TCP connections, where multiple are opened at once.

## HTTP Message format

An HTTP request:

GET $path$ $protocol$
User-agent: $OS$
Accept: $type$,
Accept-language: $language

GET /path/ HTTP/1.1
User-agent: Mozilla/4.0
Accept: text/html, image/gif, image/jpeg
Accept-language: en-us
(extra carriage return, line feed)

An HTTP response:

$protocol$ $status code$
Date: $date$
Server: $OS$
Last-Modified: $date$
Content-Length: $len$
Content-Type: $type$
$DATA$

HTTP/1.0 200 OK
Date: Thu, 06 ...
Server: Apache/1.3.0 (Unix)
Last-Modified: Mon, 22,...
Content-Length: 6821
Content-Type: text/html
DATA HERE

## HTTP Status codes

200 OK - success
301 Moved Permanently - new location
400 Bad Request - message not understood by server
404 Not Found - requested document not found by server
505 HTTP Version Not Supported - no support

## Cookies

Many websites use cookies. A cookie has four components: cookie header line of response message, header line in next http request message, cookie file kept on user's host, managed by user's browser, and a backend database at website.

SLIDE 34

# FTP

# Email: SMTP, POP3, IMAP

# DNS

# P2P Applications

# Socket Programming with UDP and TCP
