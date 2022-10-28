---
title: "Dynamo: Amazon's Highly Available Key-value Store"
date: 2022-10-26T00:00:00+08:00
draft: false
tags: [distributed systems, cloud, aws]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Computer Science History](../../content/7-computer-science-history) / [Dynamo: Amazon's Highly Available Key-value Store](./)

**Author(s):** Giuseppe DeCandia, Deniz Hastorun, Madan Jampani, Gunavardhan Kakulapati, Avinash Lakshman, Alex Pilchin, Swaminathan Sivasubramanian, Peter Vosshall and Werner Vogels

**Date:** 2007

## Notes

* Didn't invent any new algorithms, but does show how they can compile them together into a new product.
* Relational databases weren't ideal for a lot of use cases at Amazon that just required storing and retrieving data by a primary key.
* System Assumptions:
  * Query model is simple read/write operatoins to a data item identified by a primary key.
  * To avoid the poor availability consistent with ACID guarantees, dynamo works best for applications that don't require consistency, does not provide any isolation guarantees, and only permits single key updates.
  * Must meet stringent SLAs and latency requirements.
  * Prioritizing writes over reads, eventually consistent.
* Interestingly, called out in the requirements is that Dynamo is only used by Amazon's internal services, and that the operation environment is assumed to be non-hostile for security purposes. Clearly this was before it was released for public use. Security is largely up to the user in AWS so it's possible there were relatively few changes that had to be made to make it generally available.
* Amazon describes all of their SLAs at the 99.9th percentile at the minimum, as opposed to using average, median, and expected variance. This is because customers with more data and longer histories typically require more processing but are also the most valuable customers. 99.9 was chosen over an even higher percentile after a cost-benefit analysis demonstrated a significant increase in cost to improve performance that much more.
* Dynamo has two operations:
  * get(key): locates the object and replicas associated with the key and returns a single object or a list of objects with the conflicting versions
  * put(key, context, object): Place the object and write the replicas to disk. Context encodes metadata like the version and stored with the object. Applies a MD5 hash on the key to generate a 128-bit identifier which is used to determine which node to store the object on.
* Dynamo uses eventual consistency, which means that a get(key) operation may not be returning the latest version of an object. This allows for faster writes, as writes can be sent to replicas asynchronously. Certain Amazon applications using Dynamo are okay with this model, such as Adding to Cart. The cart needs to remember something was added, but it doesn't necessarily need to be reflected immediately after something is added to the cart.
* Use virtual nodes, which means any node could have multiple actual nodes to account for imbalances.
* Use a data structure called Vector Clocks. These are used to determine if an event occurred before another event (two writes). You can identify if A causes B, B causes A, or both A and B are independent.
* Handle temporary failures with hinted handoff and permanent failures with syncs using Merkle trees.
* Gossip protocol. At every epoch, each node transmits its membership list to b nodes. If a node is stated as unavailable for more than M epochs, it's announced dead. Given no additional changes, protocol converges in O(log2N) steps.

### Highlights

* Reliability is one of the most important requirements because even the slightest outage has significant financial consequences and impacts customer trust. In addition, to support continuous growth, the platform needs to be highly scalable.
* Dynamo is used to manage the state of services that have very high reliability requirements and need tight control over the tradeoffs between availability, consistency, cost-effectiveness and performance.
* There are many services on Amazon’s platform that only need primary-key access to a data store. For many services, such as those that provide best seller lists, shopping carts, customer preferences, session management, sales rank, and product catalog, the common pattern of using a relational database would lead to inefficiencies and limit scale and availability. Dynamo provides a simple primary-key only interface to meet the requirements of these applications.
* Dynamo targets applications that need to store objects that are relatively small (usually less than 1 MB).
* Experience at Amazon has shown that data stores that provide ACID guarantees tend to have poor availability.
* From the very early replicated database works, it is well known that when dealing with the possibility of network failures, strong consistency and high data availability cannot be achieved simultaneously [2, 11]. As such systems and applications need to be aware which properties can be achieved under which conditions.
* Dynamo is designed to be an eventually consistent data store; that is all updates reach all replicas eventually.
* First, Dynamo is targeted mainly at applications that need an “always writeable” data store where no updates are rejected due to failures or concurrent writes.
* Dynamo is built for an infrastructure within a single administrative domain where all nodes are assumed to be trusted.
* Dynamo can be characterized as a zero-hop DHT, where each node maintains enough routing information locally to route a request to the appropriate node directly.
* Consistent Hashing: Dynamo uses a variant of consistent hashing (similar to the one used in [10, 20]): instead of mapping a node to a single point in the circle, each node gets assigned to multiple points in the ring. To this end, Dynamo uses the concept of “virtual nodes”. A virtual node looks like a single node in the system, but each node can be responsible for more than one virtual node. Effectively, when a new node is added to the system, it is assigned multiple positions (henceforth, “tokens”) in the ring

## Resources

* [Papers We Love Presentation](https://www.youtube.com/watch?v=hMt9yFp0JKM)
* [Other Papers We Love Presentation](https://www.youtube.com/watch?v=w96lLsbI1q8)
