Apache Kafka is an **event-streaming** platform. Event streaming is a mechanism that allows the continuous flow of events among the components of a system through the usage of an event bus. An **event bus** collects, processes, and stores data as a stream of continuous records. Evidently, it is a good microservice capable of handling enterprise system levels of messages and data. 

Kafka is:
- high-throughput.
- low-latency.
- fault-tolerant.
- scalable.

## Throughput
Kafka maintains an append-only, time-ordered sequence of records. That means it *processes data as a queue*. New requests are appended to the end of the bus and the oldest requests are handled first. 

## Data storage
In Kafka, events are stored as atomic units of data. Storage is internally divided into topics, which are split into buckets, which then become partitions. 

**Topics** are for event categorization. They should be separated by type of data. 
**Buckets** are for handling priority. Higher priority buckets are handled first. 
**Partitions** handle horizontal scaling. They may be distributed across machines, allowing for multiple streams of processing. 
A **producer** is a client that publishes messages to a topic. These messages may contain partition names or keys. 
As expected, **consumers** read messages from partitions in a time-ordered fashion. 
Each Kafka server is a **broker**, a **cluster** is a group of broker nodes (must be assigned a controller node), and a **Kraft** is a required consensus protocol for keeping replicas in sync.

How to use Kafka in Django:
https://medium.com/@mansha99/microservices-using-django-and-kafka-3776e8592ef3