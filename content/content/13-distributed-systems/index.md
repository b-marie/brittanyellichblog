---
title: "Distributed Systems"
lastmod: 2022-10-08T00:00:00+08:00
draft: false
tags: [distributed systems]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Distributed Systems](./)

## Overview

A distributed system is a network of computers that are working together towards a common goal, appearing to the end-user as a single computer. The computers are peers, working together to make the system more tolerant to failures and more available.

Many distributed systems today are used for data-intensive applications, where the quantity, complexity, or speed at which data is changing would be a bottleneck if it weren't for a distributed system. Three ways to describe a distributed system are in terms of reliability, scalability, and maintainability.

### Reliability

Reliability means that you system will continue to work correctly even in the face of hardware faults, software faults, or human error. For a system to be reliable, it should be able to:

* Function as the user expects
* Tolerate user mistakes or using the software in unexpected ways
* Performance that is good enough for its use case under expected load and data volume
* Prevents unauthorized access and abuse

A reliable system should be fault-tolerant, which means that it anticipates and handles faults. Faults can be anything from exceptions in your code to hardware failures. This is different from a failure, where the entire system stops working. It is impossible to anticipate every fault, so it's usually best to handle faults that could lead to failures.

#### Classes of Faults

* Hardware Faults: These can typically be handled by introducing redundancy into the system (i.e., backup hard drives in a RAID configuration)
* Systematic Errors: These can be hard to anticipate and may be correlated across nodes. Examples are bugs that occur in a dependency, like the Linux Kernel, introducing a fault into all systems running that version of Linux. These bugs often lie dormant for a long time until they're triggered by unusual circumstances.

#### How to Make Systems More Reliable

* Use the Chaos Monkey approach of deliberately introducing faults to your system to see where it fails, and then handling that issue.
* Design systems that minimize the opportunity for human error, like providing a fully featured non-production sandbox environment for people to explore safely without affecting users.
* Test thoroughly from unit tests to integration tests to manual tests.
* Roll out new code gradually so that unexpected bugs only impact small numbers of users.
* Make it very easy and quick to roll back changes when needed to recover faster.
* Set up detailed and clear monitoring like performance metrics and error rates.

### Scalability

As the system grows in volume, traffic, or complexity it should be able to keep up with the growth. You can measure scalability in terms of:

* Latency: The duration a request is waiting to be handled
* Response Time: What the client sees as the actual time to process a request

### Maintainability

Many engineers over time should be able to work productively on the system.

A maintanable system is the following:

* Easy for the operations team to keep running
* Easy for new engineers to understand
* Easy for engineers to make changes to

#### Operations

An operations team working on a distributed system is responsible for:

* Monitoring the health of the system and quickly restoring service if it is in a bad state
* Tracking down the causes of system failures or degraded performance
* Keeping software and platforms up to date, like security patches
* Seeing how different systems affect each other
* Anticipating future problems before they occur
* Establishing good practices and tools for deployment, configuration management, and more
* Performing complex maintenance tasks
* Maintaining system security
* Defining processes to make operations predictable and keep the production environment stable
* Documenting and sharing knowledge about the system

#### Complexity

Complexity is unnecessary if it isn't inherent to the problem your software is trying to solve, but arises in the implementation [Moseley and Marks](http://curtclifton.net/papers/MoseleyMarks06a.pdf). The ease with which you can modify a system is linked to how simple it is. Easy-to-understand symptoms are easier to modify than complex ones. Symptoms of complexity in your system include:

* Tight coupling of modules
* Tangled dependencies
* Inconsistent naming and terminology
* Hacks to solve performance problems
* Special cases to work around issues

You can deal with complexity with abstractions that hide implementation detail behind a clean, simple-to-understance interface.

## Learning Resources

### Articles

* [ ] [Out of the Tar Pit](http://curtclifton.net/papers/MoseleyMarks06a.pdf)
* [ ] [Analyzing Software Evolvability](http://www.es.mdh.se/pdf_publications/1251.pdf)
* [ ] [Getting Real about Distributed System Reliability](https://blog.empathybox.com/post/19574936361/getting-real-about-distributed-system-reliability)
* [ ] [Principles of Software Engineering Part 1](http://nathanmarz.com/blog/principles-of-software-engineering-part-1.html)
* [ ] [AWS The Good The Bad and The Ugly](https://www.talisman.org/~erlkonig/misc/aws-the-good-the-bad+the-ugly/)
* [ ] [A Conceptual Framework for Fault Tolerance](https://resources.sei.cmu.edu/asset_files/TechnicalReport/1992_005_001_16112.pdf)

### Books

* [ ] [Designing Data Intensive Applications](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable-ebook/dp/B06XPJML5D/ref=sr_1_1?crid=2B4248NG1QVDC&keywords=designing+data-intensive+applications&qid=1666194849&qu=eyJxc2MiOiIxLjgwIiwicXNhIjoiMS4zMSIsInFzcCI6IjEuNDEifQ%3D%3D&sprefix=designing+data%2Caps%2C150&sr=8-1)

### Helpful Sites

* [Awesome Distributed Systems Repo](https://github.com/theanalyst/awesome-distributed-systems)
* [Software Architect Repo](https://github.com/justinamiller/SoftwareArchitect)

### Videos

* [ ] [Simple Made Easy](https://www.infoq.com/presentations/Simple-Made-Easy/)
