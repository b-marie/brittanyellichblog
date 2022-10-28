---
title: "Time, Clocks, and the Ordering of Events in a Distributed System"
date: 2022-08-01T00:00:00+08:00
draft: false
tags: [distributed systems]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Computer Science History](../../content/7-computer-science-history) / [Time, Clocks, and the Ordering of Events in a Distributed System](./)

**Author(s):** Leslie Lamport

**Date:** 1978

## Notes

* "A distributed system consists of a collection of distinct processes which are spatially separated, and which communicate with one another by exchanging messages."
* Clocks aren't perfectly accurate and aligning real clocks is difficult.
* How do we know the order of two events?
* We can't rely on ordering based on the clocks of the individual systems
* Partial Ordering
  * A simple "happens before" relationship to determine the order between two events within the same process (state machines)
  * When two events cross in the event stream, we can't really know which one came first. For partial ordering, it's arbitrary
* Logical Clocks
  * Sending a timestamp along with the message, the receiver can use the timestamp and increment it to a greater value, setting its own local clock
  * In a distributed system, each process keeps its own clock
* Total Ordering
  * Use logical clocks to order events and then use an arbitrary way to determine which came first for concurrent events
  * Can be used to solve the mutual exlusion problem. Only one process can use a resource at a time so the processes must
  * Each process maintains its own request queue which is never seen by another process.
  * Defines the following algorithm:
        1. Process P1 sends a message to all other processes to request a resource with a timestamp on the message
        2. All other processes acknowledge the request on their request queue, and send a timestamped acknowledgement message to P1
        3. P1 releases the resource by removing the requests resource message from its request queue and sends a timestamped releases resource message to all other processes
        4. All other processes receive that releases resource message and removes the requests resource message from their request queues
    * Process P1 gets the resource when there is a requests resource message in its request queue, ordered before any other request in its queue, and P1 has received a message from every other process acknowledging the request after its initial timestamp
    * This algorithm is ideal in situations where there is no central process or central storage
* Physical Clocks
  * A clock synchronizing algorithm to reduce drift among physical clocks using the current value of the process physical clock and the timestamp of the message received
* Drawbacks
  * Fails to call out retries or errors/failing scenarios
* "Almost nobody thought it was about state machines"..."Never understood why it's so important in computer science... but what people get out of it is a way of thinking about distributed systems that felt obvious to me but wasn't obvious...and got them thinking a different way". - [Interview with Leslie Lamport](https://www.youtube.com/watch?v=nfRouGH0oMg)
  * Thinks about this as a physics problem, not a math problem.

## Resources

* [Blog post summary](https://pages.cs.wisc.edu/~swift/classes/cs739-fa14/blog/2014/09/time_clocks_and_the_ordering_o.html)
* [Blog post](https://vaibhavsingh1993.github.io/blog/2019/01/19/review_time_clocks/)
* [Papers We Love Presentation](https://www.youtube.com/watch?v=hK6m6WBk-d8)
* [Interview with Leslie Lamport](https://www.youtube.com/watch?v=nfRouGH0oMg)
  * Awarded a Turing award for this paper in 2013
* [YouTube Video Summary](https://www.youtube.com/watch?v=ummQWQgkWOA)
* [A good summary of the paper](https://www.ics.uci.edu/~cs230/reading/time.pdf)
