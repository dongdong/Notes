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
	- A set of assumptions about the environment and facilities on which a distributed system is implement 
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


* System models vary in their assumptions about the environment and facilities. These assumptions include:
	- what capabilities the nodes have and how they may fail
	- how communication links operate and how they may fail
	- properties of the overall system, such as assumptions about time and order
	

* A robust system is one that makes the weakest assumptions, on the other hand, strong assumptions make the system model easy to reason about


* Nodes in our system model
	- Nodes serve as hosts for computation and storage. They have:
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

	![network_partition](imgs/dsffap_2_1.png)


* Timing/ordering assumptions
	- Any message sent from one node to the others will arrive at a different time and potentially in a different order at the other nodes
	- The two main alternative timing assumption:
		- Synchronous model: processes execute in lock-step; ther is a known upper bound on message transmission delay; each process has an accurate clock
		- Asychronous system model: No timing assumption, processes execute at independent rates; there is no bound on message transmission delay; useful clocks do not exist
	- It is easier to solve problems in the synchronous system model, you can make inferences based on those assumptions and rule out inconvenient failure scenarios by assuming they never occur
	 - However, real world systems are at best partially synchronous


##### The consensus problem

* Several nodes achieve consensus if they all agree on some value. More formally:
	- Agreement: every correct process must agree on the same value.
	- Integrity: every correct process decides at most one value, and if it decides some value, then it must have been proposed by some process.
	- Termination: all processes eventually reach a decision.
	- Validity: if all correct processes propose the same value V, then all correct processes decide V


* The consensus problem is at the core of many commercial distributed systems. After all, we want the reliability and performance of a distributed system without having to deal with the consequences of distribution, such as disagreements or divergence between nodes. Moreover, solving the consensus problem makes it possible to solve several related, more advanced problems such as atomic broadcast and atomic commit.


##### Two impossiblity results

* The FLP impoossibility result
	- Particularly relevant to people who design distributed algorithms
	- Examines the consensus problem under the asynchronous system model and assumed that 
		- nodes can only fail by crashing; 
		- the network is reliable, 
		- there are no bounds on message delay
	- Under these assumptions, the FLP result states that "there does not exist a (deterministic) algorithm for the consensus problem in an asynchronous system subject to failures, even if messages can never be lost, at most one process may fail, and it can only fail by crashing (stopping executing)".
	- This impossibility result is important because it highlights that assuming the asynchronous system model leads to a tradeoff: algorithms that solve the consensus problem must either give up **safety** or **liveness** when the guarantees regarding bounds on message delivery do not hold.


* The CAP theorem
	- The theorem states that of these three properties:
		- Consistency: all nodes see the same data at the same time.
		- Availability: node failures do not prevent survivors from continuing to operate.
		- Partition tolerance: the system continues to operate despite message loss due to network and/or node failure
	- Only two can be satisfied simultaneously, then we get three different system types:
		- CA: consistency + availability, examples include full strict quorum protocols, such as two-phase commit
		- CP: consistency + partition tolerance, examples include majority quorum protocols in which minority partitions are unavailable such as Paxos
		- AP: availability + partition tolerance, examples include protocols using conflict resolution, such as Dynamo

	![CAP_theorem](imgs/dsffap_2_2.png)


* The CA and CP system designs both offer the same consistency model: **strong consistency**
	- CA system cannot tolerate any node failures
	- CP system can tolerate up to f faults given 2f+1 nodes in a non-Byzantine failure model.
	- CA system does not distinguish between node failures and network failures, and hence must stop accepting writes everywhere to avoid introducing divergence (multiple copies). It cannot tell whether a remote node is down, or whether just the network connection is down: so the only safe thing is to stop accepting writes
	- CP system prevents divergence (e.g. maintains single-copy consistency) by forcing asymmetric behavior on the two sides of the partition. It only keeps the majority partition around, and requires the minority partition to become unavailable (e.g. stop accepting writes), which retains a degree of availability (the majority partition) and still ensures single-copy consistency
	

* Assuming that a partition occurs, the theorem reduces to a binary choice between availability and consistency.
	
	![Partition_tolerance](imgs/dsffap_2_3.png)


* There are four conclusions that should be drawn from the CAP theorem:
	- Many system designs used in early distributed relational database systems did not take into account partition tolerance 
	- There is a tension between strong consistency and high availability during network partitions
		- Strong consistency guarantees require us to give up availability during a partition. This is because one cannot prevent divergence between two replicas that cannot communicate with each other while continuing to accept writes on both sides of the partition
		- Consistency can be traded off against availability and the related capabilities of offline accessibility and low latency. If "consistency" is defined as something less than "all nodes see the same data at the same time" then we can have both availability and some (weaker) consistency guarantee.
	- There is a tension between strong consistency and performance in normal operation
		- Strong consistency requires that nodes communicate and agree on every operation. This results in high latency during normal operation
		- If you can live with a consistency model that allows replicas to lag or to diverge, then you can reduce latency during normal operation and maintain availability in the presence of partitions
	- If we do not want to give up availability during a network partition, then we need to explore whether consistency models other than strong consistency are workable for our purposes


* Consistency and availability are not really binary choices, unless you limit yourself to strong consistency. But strong consistency is just one consistency model: the one where you, by necessity, need to give up availability in order to prevent more than a single copy of the data from being active.	


##### Consistency Model

* Consistency Model
	- A contract between programmer and system, wherein the system guarantees that if the programmer follows some specific rules, the results of operations on the data store will be predictable
	- Strong consistency models, capable of maintaining a single copy
		- Linearizable consistency
		- Sequential consistency
	- Weak consistency models, not strong
		- Client-centric consistency models
		- Causal consistency: strongest model available
		- Eventual consistency models
	- Consistency models are just arbitrary contracts between the programmer and system, so they can be almost anything.

 
* Strong consistency models
	- Linearizable consistency: under linearizable consistency, all operations appear to have executed atomically in *an order* that is consistent with the global real-time ordering of operations
	- Sequential consistency: under sequential consistency, all operations appear to have executed atomically in *some order* that is consistent with the order seen at individual nodes and that is equal at all nodes 
	- Sequential consistency allows for operations to be reordered as long as the order observed on each node remains consistent
	- Strong consistency models allow you as a programmer to replace a single server with a cluster of distributed nodes and not run into any problems


* A client-centric consistency model might guarantee that a client will never see older versions of a data item. This is often implemented by building additional caching into the client library, so that if a client moves to a replica node that contains old data, then the client library returns its cached value rather than the old value from the replica.


* Eventual consistency
	- The eventual consistency model says that if you stop changing values, then after some undefined amount of time all replicas will agree on the same value. 
	- It is implied that before that time results between replicas are inconsistent in some undefined manner. 
	- It's a very weak constraint, and we'd probably want to have at least some more specific characterization of two things:
		- how long is "eventually"? It would be useful to have a strict lower bound, or at least some idea of how long it typically takes for the system to converge to the same value
		- how do the replicas agree on a value? For example, one way to decide is to have the value with the largest timestamp always win


##### Further readings

* Impossibility of distributed consensus with one faulty process
* Perspectives on the CAP Theorem 
* [CAP Twelve Years Later: How the "Rules" Have Changed](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)
* [Replicated Data Consistency Explained Through Baseball](http://pages.cs.wisc.edu/~remzi/Classes/739/Papers/Bart/ConsistencyAndBaseballReport.pdf)
* [Life beyond Distributed Transactions: an Apostate’s Opinion](https://cs.brown.edu/courses/cs227/archives/2012/papers/weaker/cidr07p15.pdf)

	

### 3. Time and order




### 4. Replication: preventing divergence


### 5. Replication: accepting divergence



