## Traditional Routing Algorithms
### Routing Algorithm Classification
*Global*: All routers have complete topology. Everything has complete knowledge of everything, very expensive.
These use "link state" algorithms, usually for internal networks.
*Decentralized*: Get costs to neighbors and information from neighbors. Takes longer. Usually implemented with "Distance Vector" algorithms.
BGP Holds the internet together.
*Static*: Routes change slowly over time.
*Dynamic*: Routes change more quickly, with periodic updates or in response to link cost changes.

### Bellman Ford Equation

## SDN Controllers

## Internet Control Message Protocol

## Network Management

## OSPF

## BGP

## OpenFlow

## ODL

## ONOS

## Controllers

## ICMP
1. we have used this
2. network layer
## SNMP

Management software for internet connected devices. Called an agent, it collects data and sends it to a client. Sends data in a MiB, management information block. If there is a header that is unknown, it gets thrown away.

Two ways to implement:

pull model - request and response its like polling where it costs more but manager requests status every interval.

push model - trap model that relies on client to say if something is wrong.

Most use both - use traps to say if something is wrong, but every set interval we use a pull to make sure everything isn't off.