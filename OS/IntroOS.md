# Introduction to Operating Systems (Course@Udacity) 


### 1. Introduction

* Preview
	- What is an operating system?
	- What are key components of an operating system?
	- Design and implementation considerations of operating systems


* An Operating system is a layer of software that:
	- directly has privileged access to the underlying hardware
	- hides the hardware complexity
	- manages hardware on behalf of one or more applications according to some predifined policies
	- ensures that applications are isolated and protected from one another


* OS Elements
	- Abstraction: process, thread, file, socket, memory page
	- Mechanisms: create, schedule, open, write, allocate
	- Policies: LRU(Least Recently Used), EDF(Earliest Deadline First)
	
	![OS_elements](imgs/IntroOS_1_1.png)


* Design Principles
	- Separation of mechanism & policy: implement flexible mechanism to support  many policies
	- Optimize for common case 


* User/Kernel Protection Boundary
	- User-level: applications
	- Kernel-level: OS kernel, privileged direct hardware access


* User/kernel switch is supported by hardware:
	- trap instructions
	- system call: open(file), send(socket), malloc(memory)
	- signals

	![protection_boundary](imgs/IntroOS_1_2.png)


* To write a system call, an application must:
	- write argument
	- save relevant data at well-defined location
	- make system call

	![system_call](imgs/IntroOS_1_3.png)


* User/Kernel transitions
	- involves a number of instructions, e.g. ~50-100ms on a 2GHz machine running linux
	- switch locality: affects hardware cache
	- not cheap!


* OS services
	- process management
	- file management
	- device management
	- memory management
	- security
	- ...

	![system_call_list](imgs/IntroOS_1_4.png)


* Monolithic OS
	-  [Monolithic kernel](https://en.wikipedia.org/wiki/Monolithic_kernel)

	![Monolithic_OS](imgs/IntroOS_1_5.png)


* Modular OS
	
	![Monolithic_OS](imgs/IntroOS_1_6.png)


* Microkernel
	- [Micorkernel](https://en.wikipedia.org/wiki/Microkernel)

	![Monolithic_OS](imgs/IntroOS_1_7.png)


* Linux architecture

	![Monolithic_OS](imgs/IntroOS_1_8.png)


* Mac OS Architecture

	![Monolithic_OS](imgs/IntroOS_1_9.png)


* Summary
	- OS elements: abstractions, mechanisms, and policies
	- Communication between applications and OS via system calls


* Recommended Textbooks
	- Operating System Concepts
	- Operating System Concepts Essentials
	- Modern Operating Systems
	- [Operating Systems: Three Easy Pieces](http://pages.cs.wisc.edu/~remzi/OSTEP/)


### 2. Processes and Process Management



### 3. Threads and Concurrency



### 4. PThreads



### 5. Thread Design Consideration



### 6. Thread Performance Consideration



### 7. Scheduling



### 8. Memory Management



### 9. Inter-Process Management



#### 10. Synchronization



### 11.  I/O Management



### 12. Virtualization



### 13. Remote Procedure Calls



### 14. Distributed File Systems



### 15. Distributed Shared Memory



### 16. DateCenter Technologies