# Distributed systems for fun and profit

### 0. Introduction

* Much of distributed programming is about dealing with the implicationns of two consequences of distribution:
	- that information travels at (most) the speed of light
	- that independent things fail independently

### 1. Basics: Distributed systems at a high level

* Distributed programming is the art of solving the same problem that you can solve on a single computer using multiple computers

* Scalability
	- Scalability is the ability of a system, network, or process, to handle a growing amout of work in a capable manner or its ability to be enlarged to accommodate that growth 
	- Size scalability: adding more nodes should make the system linearly faster; growing the dataset should not increase latency
	- Geographic scalability: it should be possible to use multiple data centers to reduce the time it takes to respond user queries, while dealing with cross-data center latency in some sensible manner
	- Administrative scalability: adding more nodes should not increase the administrative costs of the system; e.g. the administrators-to-machines ratio
	- A scalable system is one that contines to meet the needs of its users as scale increases. There are two paticular relevant aspects: performance and availability


* Performance (and Lantency)
	- Performance is characterized by the amount of useful work accomplished by a computer system compared to the time and resource used. 
	- This may involve achieving one or more of the following:
		- Short response time, low lantency for a given piece of work
		- High throughput, rate of processing work
		- Low utilization of computing resosurces
	- There are tradeoffs involved in optimizing for any of these outcomes
	- Latency is the time between when something happened and the time it has an impact or becomes visible. 
	- For example, latency could be measured in terms of how long it takes for a write to become visible to readers.
	- In a distributed system, there is a minimum latency that cannot be overcome: 
		- the speed of light limits how fast information can travel, 
		- and hardware components have a minimum latency cost incurred per operation


* Availability (and fault tolerance)
	- The proportion of time a system is in a functioning condition. If a user cannot access the system, it is said to be unavailable
	- Distributed systems can take a bunch of unreliable components, and build a reliable system on top of them
	- Formulaically, availability is: Availability = uptime / (uptime + downtime)
	- The best we can do to achieve high availability is design for fault tolerance
	- Fault tolerance: ability of a system to behave in a well-defined manner once faults occur
	- You can't tolerate faults you haven't considered


* Constrains
	- Distributed systems are constrained by two physical factors:
		- the number of nodes, which increases with the required storage and computation capacity
		- the distance between nodes, information travels, at best, at the speed of light
	- Working within those constraints:
		- an increase in the number of independent nodes increases the probability of failure in a system, reducing availability and increasing administrative costs
		- an increase in the number of independent nodes may increase the need for communication between nodes, reducing performance as scale increases
		- an increase in geographic distance increases the minimum latency for communication between distant nodes, reducing performance for certain operations


* Abstractions and models
	- Abstractions make things more manageable by removing real-world aspects that are not relevant to solving a problem
	- Models describe the key properties of a distributed system in a precise manner
	- Models that will be discussed:
		- system model:  asynchronous/synchronous
		- failure model: crash-fail, patitions, Byzantine
		- consistency model: strong, eventual
	- A system that makes weaker guarantees has more freedom of action, and hence potentially greater performance, but it is also potentially hard to reason about
	- One can often gain performance by exposing more details about the internals of the system, while systems that hide details are easier to understand.
	- The ideal system meets both programmer needs (clean semantics) and business needs (availability/consistency/latency)


* Design techniques: partition and replicate
	- Partitioning is dividing the dataset into smaller distinct independent sets
		- Partitioning improves performance by limiting the amount of data to be examined and by locating related data in the same partition.
		- Partitioning improves availability by allowing partitions to fail independently, increasing the number of nodes that need to fail before availability is sacrificed 
	- Replication is making copies of the same data on multiple machines, which allows more servers to take part in the computation.
		- Replication improves performance by making additional computing power and bandwidth applicable to a new copy of the data.
		- Replication improves availability by creating additional copies of the data, increasing the number of nodes that need to fail before availability is sacrificed.
	- Replication allows us to achieve scalability, performance and fault tolerance. 
	- Replication is also the source of many of the problems: copies of the data that has to be kept in sync on multiple machines means ensuring that the replication follows a consistency model.


* Further Readings
	* [Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
	* [Notes on Distributed Systems for Young Bloods](https://www.somethingsimilar.com/2013/01/14/notes-on-distributed-systems-for-young-bloods/)


### 2. Up and down the level of abstraction


### 3. Time and order


### 4. Replication: preventing divergence


### 5. Replication: accepting divergence



