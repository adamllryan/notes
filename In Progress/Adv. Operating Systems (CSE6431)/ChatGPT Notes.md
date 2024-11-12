---
completed: false
next: 
prev: 
---
### Lecture 5: Database Systems and Transactions

#### Synchronization and Efficiency
- **Correctness vs Efficiency**: Achieving synchronization in database systems is complex. While using a global lock simplifies the process, it is inefficient. Fine-grained locking improves efficiency but is error-prone.
  - Ideal: A system where the programmer focuses solely on application logic, and the runtime handles synchronization. Database systems partially realize this goal.

#### Database Systems Overview
- **Database**: A collection of shared data objects (d1, d2, …, dn) accessed by users.
  - Correctness constraints (consistency assertions or integrity constraints) must be met for the database to be considered consistent.
  - Users interact with databases through **transactions**—complex operations that include reads, writes, and computations on data objects.
  - Example: online booking, bank teller operations.

#### Transactions and the ACID Properties
- **Transactions**: Group actions on a database into a single logical unit.
  - Types:
    - **Query**: A read-only transaction.
    - **Update**: Modifies at least one object.
  - Assumptions:
    - Transactions preserve consistency.
    - They terminate in finite time.
- **ACID Properties**:
  - **Atomicity**: All or nothing.
  - **Consistency**: Maintains consistent rules.
  - **Isolation**: Transactions do not interfere with one another.
  - **Durability**: Committed transactions are preserved.

#### The Transaction Model
- **Transaction Primitives**:
  - `BEGIN_TRANSACTION`: Starts a transaction.
  - `END_TRANSACTION`: Ends and commits the transaction.
  - `ABORT_TRANSACTION`: Cancels the transaction and restores previous values.
  - `READ`/`WRITE`: Read from/write to the database.
  
- **Example**:
  - Transaction to reserve three flights either commits successfully or aborts if a flight is unavailable.

#### Achieving ACID
- **Atomicity**: Ensured by the all-or-nothing approach, where failure triggers a rollback.
- **Consistency**: Developers ensure correct transactions.
- **Isolation**: Prevents one transaction from seeing another's internal state.
- **Durability**: Achieved by writing data to persistent storage.

#### Write-Ahead Logs (WAL)
- A common method for maintaining consistency. The log records each operation before it is executed, allowing for rollback in case of failure.
  - **Example**: If a transaction modifies a value, the original and modified values are logged, enabling recovery after crashes.
  
- **Challenges**:
  - If a machine crashes during a transaction, the log can be checked for incomplete entries, allowing rollback or replay as needed.
  - **Idempotent operations**: Certain operations (e.g., `x=0/1`) can be repeated without adverse effects, ensuring safe log replay.

#### Concurrency Control
- **Goal**: Ensure consistency and isolation, even when multiple transactions are executed simultaneously.
  - **Managers**:
    - **Data Manager**: Manages database objects.
    - **Scheduler**: Ensures proper transaction order.
    - **Transaction Manager**: Manages transaction execution.
  
#### Concurrency Control Theory
- **Serial Execution**: Transactions execute one at a time, preserving consistency but being inefficient.
- **Interleaved Execution**: Transactions run concurrently, but consistency and isolation must be ensured.

- **Logs**: Capture the order of transaction operations. Two logs are equivalent if they result in the same database state.
  - **Serializable Log**: A log that mirrors the effect of serial execution.
  - **Conflict Serializability**: Detects conflicts between transactions to ensure serializability.

#### Lock-Based Concurrency Control
- **Static Locking**: All locks are acquired at the start and released at the end.
  - Simple but limits concurrency.
  
- **Two-Phase Locking (2PL)**: A dynamic approach where locks are acquired and released as needed. Transactions have a **growing phase** (acquiring locks) and a **shrinking phase** (releasing locks).
  - **Strict 2PL**: Locks are held until the transaction commits, reducing issues like deadlock and rollback.

#### Timestamp-Based Concurrency Control
- **Basic Timestamp Ordering (BTO)**: Transactions are assigned timestamps to ensure proper execution order. Operations are aborted if their timestamp violates read/write rules.

- **Example**: A transaction with an earlier timestamp cannot overwrite values written by a later timestamp.

#### Summary and Explanation
- **Explanation**: This lecture covers the essential principles of database transactions and how they achieve the ACID properties (Atomicity, Consistency, Isolation, Durability). It emphasizes the complexity of synchronization and concurrency control in database systems, explaining various models like write-ahead logs, two-phase locking, and timestamp-based algorithms. The importance of ensuring transaction consistency through serializability is discussed in detail, along with the mechanisms used to achieve it. The lecture concludes by comparing different concurrency control algorithms and their applications in ensuring database integrity.

### Lecture 7: Deadlock

#### Introduction to Deadlock
- **Deadlock**: Occurs when a set of processes is blocked, each waiting for resources held by other processes in the set. This creates a **circular wait**, meaning no process can proceed.
- **Starvation**: Happens when a process waits for a resource that continually becomes available but is never assigned to it due to priority issues or design flaws.

#### Differences Between Deadlock and Starvation
- **Deadlock**: Processes are permanently blocked because resources are never released.
- **Starvation**: A process may eventually get the resource, but it's uncertain when or if it will happen.
- **Resource Status**:
  - In deadlock: Contended resources are not in use.
  - In starvation: Contended resources are in continuous use by other processes.

#### Causes of Deadlocks
Deadlock occurs when the following four conditions hold simultaneously:
1. **Exclusive access**: Resources can only be held by one process at a time.
2. **Hold and wait**: Processes hold on to resources they’ve already acquired while waiting for additional resources.
3. **No preemption**: Resources cannot be forcibly taken from a process.
4. **Circular wait**: A cycle of processes exists, where each process holds a resource the next one needs.

These conditions are often desirable to preserve resource integrity and maximize utilization but can lead to deadlocks.

#### Deadlock Handling Policies
- **Deadlock detection**: The system periodically checks for deadlocks and initiates a recovery process if one is found.
- **Deadlock avoidance**: The system grants resources only if doing so ensures a safe state where all processes can complete.
- **Deadlock prevention**: The system is designed in such a way that deadlocks are never possible.

#### Deadlock Analysis
- Analyzing deadlock is complicated by the numerous variations of process-resource relationships:
  - How many resources are needed?
  - How many resources can be used simultaneously?
  - How are these resources allocated and shared?

#### Types of Deadlock Models
- **Single-unit request model**: Requests only one resource at a time.
- **AND request model**: Needs multiple resources simultaneously (e.g., CPU AND printer).
- **OR request model**: Needs one of several resources (e.g., CPU OR printer).
- **AND-OR request model**: A combination of AND and OR requests (e.g., CPU AND (printer OR disk)).
- **P-out-of-Q request model**: Needs a subset of resources (e.g., 3 out of 5 votes).

#### Deadlock Detection
- **Cyclic wait detection**: The system checks for cycles among processes and resources. If such a cycle is found, deadlock is confirmed.
  - However, checking each thread one-by-one is not always effective because the situation may change dynamically (e.g., a lock may be released before deadlock is detected).
  - **False alarms**: A process may appear to be in a deadlock when, in reality, it can proceed after a small delay.
  
- For databases, false alarms are acceptable since the system can abort transactions and retry them without significant consequences.

#### Deadlock Avoidance: Banker’s Algorithm
- **Banker’s Algorithm**: Designed by Dijkstra, it prevents deadlock by only granting resources if the system will remain in a safe state.
  - Each process must declare the maximum number of resources it may need.
  - When a process requests resources, the system checks if granting the request could lead to deadlock in the worst-case scenario (where every process requests its maximum resources).
  
- **Steps of Banker’s Algorithm**:
  1. Check if any process’s maximum minus currently held resources can be satisfied.
  2. If yes, grant the resource, allowing the process to proceed and release its resources upon completion.
  3. If no process can proceed, the system is in deadlock.

- **Limitations**: 
  - Estimating the maximum number of resources required is difficult.
  - The computation overhead can be high with many threads, making this algorithm impractical in many systems.

#### Deadlock Prevention
- A common strategy to prevent deadlocks is to impose an **ordering** on the acquisition of locks (e.g., ensure all processes acquire locks in a specific order).
  - This ordering breaks the cycle of circular wait, preventing deadlock.
  - Example: In the dining philosopher’s problem, four philosophers can pick their left fork first, and one picks their right fork first, breaking the cycle.

#### Practical Considerations
- In practice, most operating systems (e.g., Linux) and programming languages (e.g., C, Java) do not provide built-in mechanisms to prevent or detect deadlock. Developers are responsible for ensuring their programs avoid deadlocks.
  - Tools like **pstack** (for C) or **jstack** (for Java) can be used to analyze deadlocks when they occur.
  - **Database Systems**: Deadlock detection is often done internally, typically by using timeouts to abort and retry transactions that appear to be deadlocked.

#### Summary of Deadlock Handling Policies
1. **Deadlock Detection**: Periodic or on-demand checks for cycles among resource-holding processes.
2. **Deadlock Avoidance**: Grant resources only if the system remains in a safe state (e.g., using Banker’s algorithm).
3. **Deadlock Prevention**: Enforce lock ordering or design systems to avoid deadlock conditions from arising.

#### Conclusion
This lecture systematically introduces deadlock, its causes, handling policies, and various models for analysis. It emphasizes the differences between deadlock and starvation and discusses practical solutions like the Banker’s algorithm for avoiding deadlocks. The lecture concludes by noting that deadlock prevention is often the responsibility of the developer, especially in real-world systems like operating systems and databases.

### Lecture 8: Distributed Systems

#### Definition of a Distributed System
- A **Distributed System** consists of a collection of independent computers that appear to users as a single coherent system. Each machine in the system operates independently but communicates and coordinates with others to provide a unified experience.

#### Distributed System Organization
- **Middleware-based Organization**: Distributed systems often use middleware to handle communication and coordination between machines. The middleware layer can vary in thickness, from minimal integration to very thick layers that offer a high level of abstraction and coordination between components.

#### Hardware Organization
- **Current Model**: 
  - Each machine in a distributed system has its own memory, storage, and processing power. Machines communicate via network packets over a connected network.
- **Shared-Memory Model**: 
  - In this model, each machine can access all memory with load/store instructions, similar to building a multi-threaded program. While it can be emulated in a networked system, this remains an open research topic.

#### Key Terminologies in Distributed Systems
- **Throughput**: The number of requests the system can process per second.
- **Latency**: The time taken by the system to process a single request.
- **Scalability**: The system's ability to gain throughput by adding more machines.

- **Consistency**: Ensures the correct behavior of the system, typically requiring that all users see the same data at the same time.
- **Availability**: Measures how quickly the system can respond to client requests, often quantified by the system's tail latency.
- **Liveness**: The system’s ability to eventually complete processing a request, even if it takes a long time.
- **Durability**: Ensures that once a transaction is complete, its data will not be lost.

#### Relationship Between Throughput, Latency, and Scalability
- **Analogy**: These properties are akin to traffic flow on a highway. Throughput depends on the number of lanes and the distance between cars, while latency depends on the distance and car speed. Traffic jams (where demand exceeds throughput) lead to queuing delays and increased latency. Scalability is the ability to improve throughput by adding more lanes (machines).

#### Fault Tolerance in Distributed Systems
- **Challenges**: Ensuring consistency, liveness, and durability is straightforward without considering failures. However, failures are common in large distributed systems (e.g., machine crashes, lost network links, disk failures).
- The key challenge becomes maintaining these properties in the presence of failures.

#### Process Communication Models
- **Message Passing Model**: Processes interact explicitly by sending and receiving messages (e.g., using **Sockets**, **MPI**).
- **Remote Procedure Call (RPC)**: Conceptually, this model mimics a local procedure call, but in reality, processes communicate through messages (e.g., **Java RMI**, **Google protobuf**, **Apache Thrift**).
- **Remote Direct Memory Access (RDMA)**: Allows a client to read or write data directly into a remote machine’s memory, bypassing the CPU and OS of the remote machine. It provides high performance but is more complex to use.

#### Message Passing in Distributed Systems
- **Explicit Communication**: Programmers use explicit `send` and `receive` operations, controlling both data transport and synchronization.
- Messages serve two purposes:
  1. Exchanging data between processes.
  2. Synchronizing the execution of processes.

#### Remote Procedure Call (RPC) Model
- **Implicit Communication**: While the underlying processes still communicate via messages, RPC abstracts this, presenting the communication as if it were a local procedure call. It simplifies development but involves complexities behind the scenes.

#### Steps in a Remote Procedure Call:
1. Client calls the client stub (a local function).
2. Client stub builds a message and sends it to the server’s OS.
3. Server OS passes the message to the server stub.
4. Server stub unpacks the message, calls the server procedure.
5. Server does the work and sends the result back via the stub and OS to the client.
6. The client stub unpacks the result and returns it to the client.

#### Remote DMA (RDMA) Model
- **High-Performance Communication**: RDMA allows clients to read or write directly to a remote machine’s memory without involving the remote CPU or OS. This model is used for very high-performance applications but requires careful management.

#### Distributed System Challenges
- **Distributed Deadlock Detection**: Identifying deadlocks in distributed systems can be more complex due to the distributed nature of resources and locks.
  - **Global State and Distributed Snapshot**: Techniques that help take snapshots of the system state to identify deadlocks.
  - **Logical Clock and Vector Clock**: Methods to keep track of time and events in distributed systems.
  
- **Distributed Mutual Exclusion**: Ensures that when multiple processes need access to a shared resource, only one process can access it at a time.
  
- **Distributed Transaction Execution**: Handling transactions across distributed systems while maintaining consistency and durability.

- **Fault Tolerance**:
  - **Quorum-Based Approach**: A subset of the system (quorum) agrees on the state or decisions.
  - **Leader-Based Approach (e.g., Paxos and PBFT)**: A designated leader coordinates the processes and decisions.

- **Consistency Models**: Defining how and when updates to distributed systems are visible to users, balancing performance with strict consistency.

#### Explanation
This lecture introduces the fundamental concepts of distributed systems, covering their structure, communication models, and key challenges such as fault tolerance, consistency, and scalability. It explores both theoretical concepts (e.g., distributed deadlock detection, scalability) and practical models like message passing, RPC, and RDMA for enabling efficient communication across distributed machines. It also highlights common fault tolerance strategies and the complexity of ensuring consistency and liveness in distributed systems.

### Lecture 9: Global State in Distributed Systems

#### Topics in Distributed Systems
- **Distributed Deadlock Detection**: Involves determining if there is a deadlock in a distributed environment where no single machine holds all the state information.
- **Global State and Distributed Snapshot**: Capturing the global state of a distributed system for deadlock detection or other uses.
- **Logical and Vector Clocks**: Used to order events and capture the state of distributed systems.
- **Distributed Mutual Exclusion**: Ensuring only one process at a time accesses a critical resource.
- **Fault Tolerance**: Using approaches like quorum-based and leader-based mechanisms (e.g., Paxos and PBFT) to ensure system reliability.
- **Consistency**: Ensuring that all nodes in the system agree on the same state.

#### Distributed Systems Model
- **Network Model**: A number of machines connected by a network where message transfer has non-negligible delay:
  - **Synchronous Model**: Delay has a known upper bound.
  - **Asynchronous Model**: No upper bound on message delay.

#### Problem of Global State
- No single machine in a distributed system has complete knowledge of the system's state. However, some operations require knowledge of the global state, such as:
  - Detecting deadlock.
  - Checking the total money in a bank.
  - Taking a checkpoint for recovery.

A naive approach (simply querying machines for their states) can lead to inaccurate conclusions due to delays in communication and lack of synchronization between machines.

#### Deadlock Detection Example
- Consider a scenario where a monitor queries each process for its state. While the monitor gathers responses, the states of the processes may change, making it difficult to correctly identify deadlocks. For instance:
  - A process may acquire or release resources after the monitor queries it but before the monitor receives the response.
  - This leads to incorrect conclusions, such as detecting or missing deadlocks when the actual state changes dynamically.

#### The Need for Consistent Global State
- Simply combining the state of each node does not work unless done with proper timing. However, achieving synchronization across distributed systems is difficult because:
  - There is no global clock.
  - Message transfer delays are non-negligible.
  
Thus, the challenge is to capture a **consistent global state**, where events are logically ordered, not necessarily in real-time but in a sequence that reflects the system's possible state transitions.

#### Happened-Before Relation (Lamport, 1978)
- A binary relation `→` that defines the order of events:
  1. If two events `e_k` and `e_l` happen in the same process and `k < l`, then `e_k → e_l` (events in a local history are totally ordered).
  2. If `e_i` is the sending of a message and `e_j` is the receiving of that message, then `e_i → e_j`.
  3. Transitivity: If `e → e'` and `e' → e''`, then `e → e''`.

- **Consistent Global State**: A global state is considered consistent if, for any two events `e_i` and `e_j`, if `e_j` occurs after `e_i`, then `e_i` must be included in the global state if `e_j` is included.

#### Space-Time Diagrams
- Space-time diagrams graphically represent the events and message passing between processes in a distributed system. They help visualize the ordering of events and whether a global state is consistent or not.

#### Chandy-Lamport Distributed Snapshot Protocol
- **Purpose**: Capturing a consistent global state in a distributed system.
- **Assumptions**:
  - Each node has a local state (registers, memory, disk state) and communicates with others via message-passing channels.
  - Messages are recorded on the receiving side to capture the state of communication channels.

- **Procedure**:
  1. A node initiates the snapshot by sending a "take snapshot" message to itself and then to all other nodes.
  2. When a node receives a "take snapshot" message for the first time, it:
     - Records its local state.
     - Starts recording all incoming messages.
     - Relays the "take snapshot" message to other nodes.
  3. A node stops recording messages from another node once it receives the "take snapshot" message from that node.
  
  This ensures that messages sent after the snapshot request are not included in the snapshot, avoiding inconsistencies.

#### Example of Chandy-Lamport Protocol
- If `p1` takes a snapshot at a particular point in time, the system ensures that any messages sent after that point are not included in the snapshot of other nodes, maintaining consistency.
  
- The protocol ensures that if a message `m` was sent from `p0` to `p1`, and `p1` includes the reception of `m` in its snapshot, then `p0` must have sent `m` before it took its snapshot.

#### Stable Properties in Distributed Systems
- **Stable Property**: A condition that, once true, remains true in all future states of the system.
  - Examples include:
    - **Deadlock**: Once a deadlock occurs, it persists until resolved.
    - **Termination**: Once a process terminates, it stays terminated.
    - **Garbage Collection**: Once a resource is unreachable, it remains unreachable.

- **Unstable Properties**: Properties that can change over time, such as the number of online users or the amount of money in a bank. Estimating unstable properties often requires rough estimates or stronger assumptions.

#### Conclusion
The Chandy-Lamport protocol provides a mechanism for capturing a consistent global state in a distributed system, which is essential for tasks such as deadlock detection and checkpointing. The lecture also emphasizes the importance of understanding "happened-before" relationships to maintain consistency across distributed events, ensuring that the system behaves as if it had a global view.

### Lecture 10: Logical Clocks in Distributed Systems

#### Topics in Distributed Systems
- **Distributed Deadlock Detection**: Includes techniques like global state snapshots, logical clocks, and vector clocks.
- **Distributed Mutual Exclusion**: Ensuring only one process can access a critical resource at a time.
- **Fault Tolerance**: Approaches such as quorum-based and leader-based algorithms (e.g., Paxos and PBFT).
- **Consistency**: Maintaining a uniform view across distributed systems.

#### Absence of a Global Clock
- **Problem**: Synchronizing activities across distributed systems is challenging due to the absence of a global clock.
  - A single shared clock isn't feasible because different processes may observe the clock at different times due to transmission delays.
  - Even radio-synchronized clocks face propagation delay issues.
  
To address these challenges, software approaches such as **clock synchronization algorithms** and **logical clocks** are employed.

#### Cristian's Algorithm
- **Basic Idea**: Synchronize time by requesting the current time from a central time server.
- **Issues**: Time correction on clients must be gradual due to communication delays, which are estimated as `(T1 - T0 - I)/2`.

#### The Berkeley Algorithm
- A **time daemon** requests clock values from other machines, averages them, and instructs machines to adjust their clocks accordingly.

#### Logical Clocks: Motivation
- Logical clocks were introduced to tackle the issue of monitoring distributed events continuously without relying on heavy protocols like global snapshots, which are inefficient for frequent events.
  
In distributed systems like deadlock detection, the monitor needs to continuously observe events (e.g., resource requests and grants) to decide if the system is in a deadlock.

#### Message Delivery and Causal Delivery
- **Message Reception**: A node receives a message from the network.
- **Message Delivery**: The node processes the message, potentially updating a deadlock graph and checking for cycles.
  - Delivering messages in the wrong order can lead to false alarms in deadlock detection.
  
- **Causal Delivery**: Ensures messages are delivered in the correct order based on the causal relationship between events.
  - TCP guarantees causal delivery when the sender and receiver are the same, but not when they differ.

#### Logical Clocks (Lamport Clocks)
- **Logical Clock**: A simple software clock that assigns a local integer value (LC) to each event in a process.
- **Properties**:
  - Satisfies the **clock condition**: If event `e` happens before `e'`, then `clock(e) < clock(e')`.
  - Cannot differentiate between **concurrent** and **related** events, leading to potential delays in message delivery.

#### Limitations of Logical Clocks
- Logical clocks are not perfect because they cannot differentiate between concurrent and causally related events.
  - This can result in unnecessary delays, as messages from unrelated processes may need to be delivered in sequence when they could be processed independently.

#### Vector Clocks
- **Vector Clocks**: Provide a stronger method for capturing the causal relationships between events.
  - A vector clock represents the **minimal consistent cut** that includes an event, providing a more accurate way to track and compare the causality of events across processes.

- **Vector Clock Operations**:
  - Each process maintains a vector, where each entry corresponds to the number of events at that process.
  - If event `e` on process `i` has a vector clock `VC(e) = [v1, v2, ..., vn]`, this means that `v_i` events have occurred on process `i`, and for each other process `j`, the clock indicates how many events from `j` happened before `e`.

#### Comparing Vector Clocks
- To compare vector clocks of two events `e` and `e'`, one checks if the clock of `e` is less than or equal to the clock of `e'` in every dimension:
  - If `VC(e) < VC(e')` in all dimensions, then `e` happened before `e'`.
  - If neither clock is strictly less than the other, then the events are **concurrent**.

#### Solution for Causal Delivery with Vector Clocks
- The monitor can use vector clocks to ensure messages are delivered in the correct order:
  - When the monitor receives a message `m` with vector clock `VC(m)`, it can deliver `m` only after it has delivered all messages that causally precede `m` (i.e., all events with vector clocks less than `VC(m)`).
  
The monitor maintains an array `D[1-n]` to track the highest event delivered from each process, and uses this information to ensure causal delivery.

#### Properties of Vector Clocks
1. **Strong Clock Condition**: `e → e'` if and only if `VC(e) < VC(e')`.
2. **Concurrent Events**: Events `e` and `e'` are concurrent if neither vector clock is strictly less than the other.
3. **Causal Consistency**: Ensures that the monitor can detect the correct causal relationships between events.

#### Practical Use Case: Data Race Detection
- **Data Race**: Occurs when two or more processes access a shared variable without proper synchronization, potentially leading to inconsistent results.
  - Vector clocks can be used to detect data races by tracking the causal relationships between **lock** and **unlock** events.

#### Summary
This lecture introduces **logical clocks** and **vector clocks**, which are essential tools for capturing the causal relationships between events in a distributed system. While logical clocks offer a simple way to order events, they cannot distinguish between concurrent and related events. Vector clocks provide a more powerful mechanism for tracking these relationships, ensuring **causal delivery** of messages and enabling more efficient detection of deadlocks, data races, and other distributed system issues.

### Lecture 11: Distributed Mutual Exclusion

#### Introduction to Mutual Exclusion in Distributed Systems
- In distributed systems, mutual exclusion ensures that only one process can access a critical resource (or critical section, CS) at a time.
- Unlike traditional solutions (e.g., semaphores, monitors) that rely on shared memory, distributed systems face challenges such as:
  - Lack of shared memory.
  - Absence of a common physical clock.
  - Unpredictable communication delays.
  
Several algorithms have been developed to handle distributed mutual exclusion with various performance trade-offs:
- **Token-based solutions**.
- **Permission-based solutions**.

#### Centralized Algorithm
- A **centralized solution** involves one control site that grants permission for processes to enter the critical section.
  - Requires three messages for each access to the CS (request, grant, release).
  - Time to grant permission: 2T, where T is the average message delay.
  
- **Drawbacks**:
  - Single point of failure: if the control site crashes, no process can access the CS.
  - Bottleneck: the control site becomes a bottleneck as system load increases.

#### Lamport's Algorithm
- Assumptions:
  - Messages are delivered in **FIFO order** (first-in-first-out).
  - Each process maintains a **logical clock** for timestamping events.
  
- **Requesting the CS**:
  - Process `Pi` sends a `REQUEST(ti, i)` message (with its timestamp) to all other processes.
  - Each process receiving a request returns a **REPLY** to `Pi` and enqueues the request in its own request queue, ordered by timestamp.
  
- **Executing the CS**:
  - `Pi` enters the CS only when:
    1. `Pi` has received REPLY messages from all other processes.
    2. Its own request is at the head of its request queue.
  
- **Releasing the CS**:
  - After exiting the CS, `Pi` removes its request from the queue and sends a `RELEASE` message to all processes.
  - Other processes remove `Pi`'s request from their queues.

#### Proof of Correctness (Lamport's Algorithm)
- **Proof by contradiction**:
  - Assume processes `Pi` and `Pj` are both in the CS simultaneously, and `Pi`'s timestamp is smaller than `Pj`'s.
  - For `Pj` to enter the CS, it must have received a REPLY from `Pi` with a larger timestamp, indicating that `Pj` acknowledged `Pi`'s request.
  - This creates a contradiction, as `Pi`'s request should have been at the head of the queue.
  - Therefore, `Pi` and `Pj` cannot be in the CS at the same time.

#### Ricart-Agrawala Algorithm
- An **optimization** of Lamport’s algorithm that reduces the number of messages.
  
- **Requesting the CS**:
  - `Pi` sends a `REQUEST(ti, i)` message to all other processes.
  - Each process returns a REPLY to `Pi` if:
    1. It is not in the CS or hasn't requested the CS.
    2. It has a smaller timestamp than `Pi`.
    3. Otherwise, it defers the request.
  
- **Executing the CS**:
  - `Pi` enters the CS after receiving a REPLY from all processes.
  
- **Releasing the CS**:
  - After exiting the CS, `Pi` sends REPLY messages to all deferred requests.

#### Comparison of Lamport’s and Ricart-Agrawala Algorithms
- Ricart-Agrawala merges RELEASE messages with REPLY messages, reducing the number of required messages for each CS access.
  - **Lamport’s Algorithm**: 3(N-1) messages.
  - **Ricart-Agrawala**: 2(N-1) messages.

#### Maekawa’s Algorithm
- **Key Idea**: Instead of requesting permission from all processes, a process requests permission only from a subset of processes, known as the **request set**.
  - The request sets of any two processes must intersect (i.e., have at least one process in common).
  
- **Steps**:
  1. **Requesting the CS**: `Si` sends a `REQUEST(i)` message to all processes in its request set `Ri`.
  2. **Executing the CS**: `Si` enters the CS after receiving REPLY messages from all processes in `Ri`.
  3. **Releasing the CS**: `Si` sends a RELEASE message to all processes in `Ri`.

- **Request Set Construction**:
  - Request sets are constructed to satisfy the following:
    1. Request sets of any two sites intersect.
    2. Each site belongs to its own request set.
    3. All request sets are of equal size (K), ensuring load balancing.
  
  - For large systems, the size of the request set is approximately √N, reducing the number of messages to 3√N.

- **Problem**: Maekawa’s algorithm is prone to **deadlocks**. A variant with priority-based preemption can prevent deadlocks, but at the cost of requiring more messages.

#### Summary
This lecture introduces several algorithms for solving the mutual exclusion problem in distributed systems, each with different performance trade-offs:
- **Lamport's algorithm** ensures mutual exclusion but requires a large number of messages.
- **Ricart-Agrawala’s algorithm** optimizes Lamport’s by reducing the number of messages.
- **Maekawa’s algorithm** reduces the number of messages further but introduces the possibility of deadlocks.

### Lecture 12: Distributed Atomicity

#### Topics of Distributed Systems
- **Distributed Deadlock Detection**: Using global state snapshots and logical clocks.
- **Distributed Mutual Exclusion**: Ensuring only one process can access a resource at a time.
- **Distributed Transaction Execution**: Managing transactions across multiple sites.
- **Fault Tolerance**: Approaches like quorum-based and leader-based systems (e.g., Paxos, PBFT).
- **Consistency**: Ensuring all sites have the same state after a transaction.

#### Review of Atomicity
- **Atomicity**: Ensures that a transaction is either fully completed or not executed at all ("all or nothing").
  - Example: Transferring money between accounts. Both balances must be updated simultaneously or not at all.

#### Global Atomicity
- In a **distributed database**, data may be spread across multiple sites.
  - For example, the `source_balance` is stored on `site1`, and the `destination_balance` is on `site2`.
- **Global Atomicity**: Ensures that either all sites commit the transaction or all sites abort it.

#### Common Knowledge in Distributed Systems
- **Common Knowledge**: Refers to knowledge that is not only shared by everyone but also known by everyone to be shared.
  - In distributed systems, achieving common knowledge is essential for global atomicity, but it is difficult due to unreliable communication.
  
#### The Two-Generals Problem
- A classic problem demonstrating the difficulty of achieving common knowledge. Two generals must coordinate an attack on a hill, but communication between them is unreliable. If only one attacks, they will be defeated. This scenario illustrates the challenge of reaching a consensus in distributed systems.
  - **Key Insight**: It is impossible to guarantee that both parties will act at the same time under unreliable communication or unbounded delays.

#### Solving the Two-Generals Problem in Practice
- **Practical Solutions**:
  - **Probabilistic Solutions**: Sending multiple messages to increase the likelihood of success.
  - **Relaxing Synchronization Requirements**: Instead of requiring actions to happen at the exact same time, systems can achieve **eventual consistency**, where all sites will eventually commit or abort.
  
#### Two-Phase Commit Protocol (2PC)
- **Goal**: Ensure global atomicity for transactions involving multiple sites.
  - Either all sites commit the transaction, or all abort.

- **Assumptions**:
  1. Sites may crash temporarily but no permanent failure occurs.
  2. Each site has persistent and reliable storage.
  3. Each site knows whether it can commit or not.

- **General Idea**:
  - One site acts as the **coordinator** and others as **cohorts**.
  - Important decisions are logged to persistent storage to ensure recovery in case of failure.

#### Two-Phase Commit Protocol: Steps

1. **Phase I: Voting Phase**:
   - The **coordinator** sends a `COMMIT-REQUEST` message to all cohorts.
   - Each cohort checks if it can commit. If yes, it logs the transaction in the **UNDO** and **REDO** logs and sends an `AGREED` message. Otherwise, it sends an `ABORT` message.

2. **Phase II: Commit/Abort Phase**:
   - If all cohorts agree to commit, the coordinator logs the `COMMIT` and sends a `COMMIT` message to all cohorts.
   - If any cohort aborts, the coordinator sends an `ABORT` message to all cohorts.
   - Each cohort either commits the transaction or undoes it based on the coordinator's message and then sends an acknowledgment.

#### Two-Phase Commit Protocol: Handling Failures
- Various failures can occur during the protocol. Some of the key scenarios include:
  1. **Coordinator crashes before sending anything**: It can abort after rebooting.
  2. **Coordinator crashes after sending COMMIT**: Upon reboot, the coordinator reads the log and resends the message.
  3. **Cohort crashes after voting AGREED**: It can ask other cohorts or the coordinator for the decision after rebooting.
  4. **Messages are lost**: Messages like `COMMIT`, `ABORT`, or acknowledgments can be lost. The protocol allows for resending the message or aborting if needed.

- **Key Point**: Once the coordinator logs the `COMMIT` message, it cannot abort the transaction. If failures occur before this point, the coordinator can still decide to abort.

#### Summary of the Two-Phase Commit (2PC)
- 2PC is designed to ensure **global atomicity** across distributed systems.
- The protocol requires two round trips of communication and is widely used in practice, although research continues to find ways to reduce its overhead. 

#### Failure Scenarios and Mitigations
- **Cohort and coordinator crashes**: Cohorts may need to wait for the coordinator to recover. In some cases, cohorts can follow the decision of other cohorts if they have received a commit or abort message.
  
- **Lost ACKs**: If acknowledgments are lost, the coordinator resends the `COMMIT` or `ABORT` message until all cohorts respond.

The lecture provides a comprehensive overview of how distributed systems achieve atomicity, using the two-phase commit protocol to ensure consistency and recover from failures.