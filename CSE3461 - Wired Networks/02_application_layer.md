# Principles of Network Applications

We need to write programs that run on different _end systems_, communicate over network, and run in a way that promote rapid app development and allow the developer to not write software for network-core devices.

We use two structures for applications:

- client-server
- peer-to-peer (P2P)

## Client server architecture

A [server] is an always-on host. It has a permanent IP address and can be in data centers for scalability.

A [client] communicates with the server. May be intermittently connected, have a dynamic IP address, and cannot communicate directly with other [clients].

## P2P Architecture

There is no always-on [server] in this case. Arbitrary end systems directly communicate with each other.

Peers request service from other peers and provide service in return to other peers. P2P architecture is `self-scalable`. When you add a new peer, that peer brings new service capacity but also service demands. Peers are intermittently connected and change IP addresses. Lots of management.

## Processes

A [process] is code running within a host. Within the same host, two processes communicate using `inter-process communication`, defined by the OS.

Client process: process that initiates communication.
Server process: Listener process waiting for contact.

P2P Arch applications use client/server processes.

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
