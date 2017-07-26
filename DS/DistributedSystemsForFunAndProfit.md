# Distributed systems for fun and profit

### 1. Basics: distributed systems at a high level

##### Introduction

* Distributed programming is the art of solving the same problem that you can solve on a single computer using multiple computers
* Much of distributed programming is about dealing with the implicationns of two consequences of distribution:
	- that information travels at (most) the speed of light
	- that independent things fail independently


##### Scalability and other good things to achieve

* Scalability 
	- Scalability is the ability of a system, network, or process, to handle a growing amout of work in a capable manner or its ability to be enlarged to accommodate that growth 
	- Size scalability: adding more nodes should make the system linearly faster; growing the dataset should not increase latency
	- Geographic scalability: it should be possible to use multiple data centers to reduce the time it takes to respond user queries, while dealing with cross-data center latency in some sensible manner
	- Administrative scalability: adding more nodes should not increase the administrative costs of the system; e.g. the administrators-to-machines ratio


* A scalable system is one that continues to meet the needs of its users as scale increases. There are two paticular relevant aspects: 
	- performance
	- availability


* Performance (and Latency)
	- Performance is characterized by the amount of useful work accomplished by a computer system compared to the time and resource used. 
	- This may involve achieving one or more of the following:
		- Short response time, low lantency for a given piece of work
		- High throughput, rate of processing work
		- Low utilization of computing resosurces
	- There are tradeoffs involved in optimizing for any of these outcomes
	- Latency is the time between when something happened and the time it has an impact or becomes visible. 
	- For example, latency could be measured in terms of how long it takes for a write to become visible to readers.
	- In a distributed system, there is a minimum latency that cannot be overcome: 
		- the speed of light limits how fast information can travel
		- hardware components have a minimum latency cost incurred per operation


* Availability (and fault tolerance)
	- The proportion of time a system is in a functioning condition. If a user cannot access the system, it is said to be unavailable
	- Distributed systems can take a bunch of unreliable components, and build a reliable system on top of them
	- Formulaically, availability is: Availability = uptime / (uptime + downtime)
	- The best we can do to achieve high availability is design for fault tolerance
	- Fault tolerance: ability of a system to behave in a well-defined manner once faults occur
	- You can't tolerate faults you haven't considered


##### Constrains

* Distributed systems are constrained by two physical factors:
	- the number of nodes, which increases with the required storage and computation capacity
	- the distance between nodes, information travels, at best, at the speed of light


* Working within those constraints:
	- an increase in the number of independent nodes increases the probability of failure in a system, reducing availability and increasing administrative costs
	- an increase in the number of independent nodes may increase the need for communication between nodes, reducing performance as scale increases
	- an increase in geographic distance increases the minimum latency for communication between distant nodes, reducing performance for certain operations


##### Abstractions and models

* Abstractions make things more manageable by removing real-world aspects that are not relevant to solving a problem
* Models describe the key properties of a distributed system in a precise manner
* Models that will be discussed:
	- system model:  asynchronous/synchronous
	- failure model: crash-fail, patitions, Byzantine
	- consistency model: strong, eventual


* A system that makes weaker guarantees has more freedom of action, and hence potentially greater performance, but it is also potentially hard to reason about
* One can often gain performance by exposing more details about the internals of the system, while systems that hide details are easier to understand.
* The ideal system meets both programmer needs (clean semantics) and business needs (availability/consistency/latency)


##### Design techniques: partition and replicate

* Partitioning is dividing the dataset into smaller distinct independent sets
	- Partitioning improves performance by limiting the amount of data to be examined and by locating related data in the same partition.
	- Partitioning improves availability by allowing partitions to fail independently, increasing the number of nodes that need to fail before availability is sacrificed 

	
* Replication is making copies of the same data on multiple machines, which allows more servers to take part in the computation.
	- Replication improves performance by making additional computing power and bandwidth applicable to a new copy of the data.
	- Replication improves availability by creating additional copies of the data, increasing the number of nodes that need to fail before availability is sacrificed.


* Replication allows us to achieve scalability, performance and fault tolerance. 
* Replication is also the source of many of the problems: copies of the data that has to be kept in sync on multiple machines means ensuring that the replication follows a consistency model


##### Further Readings

* [Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
* [Notes on Distributed Systems for Young Bloods](https://www.somethingsimilar.com/2013/01/14/notes-on-distributed-systems-for-young-bloods/)


### 2. Up and down the level of abstraction

##### A system model

* System model
	- a set of assumptions about the environment and facilities on which a distributed system is implement 
	- Programs in a distributed system:
		- run concurrently on independent node
		- are connected by a network that may introduce nondeterminism and message loss
		- have no shared memory or shared clock
	- There are many implications:
		- each node execute a program concurrently
		- knowledge is local: nodes have fast access only to their local state, and any information about global state is potentially out of date
		- nodes can fail and recover from failure independently
		- messages can be delayed or lost; independent of node failure
		- clocks are not synchronized across node
	- System models vary in their assumptions about the environment and facilities. These assumptions include:
		- what capabilities the nodes have and how they may fail
		- how communication links operate and how they may fail
		- properties of the overall system, such as assumptions about time and order
	- A robust system is one that makes the weakest assumptions, on the other hand strong assumptions make the system model easy to reason about


* Nodes in our system model
	- Nodes serve as hosts for compution and storage. They have:
		- the ability to execute program
		- the ability to store data into volatile memory, which can be lost upon failure, and into stable state, which can be read after a failure
		- a clock which may or may not be assumed to be accurate
	- There are many possible failure models which describe the ways in which nodes can fail.
		- most systems assume a crash-recovery failure model: nodes can only fail by crashing, and can (possibly) recover after crashing at some later point
		- Another alternative is to assume that nodes can fail by misbehaving in any arbitrary way. This is known as Byzantine fault tolerance.


* Communication links in our system model
	- Many distributed algorithms assume that there are individual links between each pair of nodes, that the links provide  FIFO order for message, that they can only deliver messages that were sent, and that send message can be lost
	- Some algorithms assume that the network is reliable, that messages are never lost and never delayed indefinitely.
	- A network partition occurs when the network fails while the nodes themselves remain operational. When this occurs, message may be lost or delayed until the network partition is repaired. Partition nodes may be accessible by some clients, and so must be treated differently from crash nodes.


* Timeing/ordering assumptions
	- Any message sent from one node to the others will arrive at a different time and potentially in a different order at the other nodes
	- The two main alternative timing assumption:
		- Synchronous model: processes execute in lock-step; ther is a known upper bound on message transmission delay; each process has an accurate clock
		- Asychronous system model: No timing assumption, processes execute at independent rates; there is no bound on message transmission delay; useful clocks do not exist
	- It is easier to solve problems in the synchronous system model, you can make inferences based on those assumptions and rule out inconvenient failure scenarios by assuming they never occur
	 - However, real world systems are at best partially synchronous


* The consensus problem
	- xxx


##### Two impossiblity results

* The ELP impoossibility result


* The CAP theorem


### 3. Time and order


### 4. Replication: preventing divergence


### 5. Replication: accepting divergence



