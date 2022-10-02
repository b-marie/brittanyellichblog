---
title: "MapReduce: Simplified Data Processing on Large Clusters"
date: 2022-09-02T00:00:00+08:00
draft: false
tags: [distributed systems]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

**Author(s):** Jeffrey Dean and Sanjay Ghemawat

**Date:** 2004

## Notes

* MapReduce
  * "Users specify a map function that processes a key/value pair to generate a set of intermediate key/value pairs, and a reduce function that merges all intermediate values associated with the same intermediate key."
  * Used for processing large data sets
  * Programs can be parallelized and executed on large clusters of machines, making it highly scalable
* Drawbacks
  * The distributed nature can have significant drawbacks if there is a lot of network latency between the machines
* Examples
  * Distributed Grep - The map function creates a line if it matches the pattern, the reduce function copies the intermediate data to the output
  * Count of URL Access Frequency - The map function processes logs of web page requests and outputs, the reduce function adds together all va lues for the same URL with a total count per URL pair
* In Practice
  * A user writes both the map and the reduce function for their dataset
  * The master computer divides the dataset into M map functions and R reduce functions and sends the details to the corresponding number of workers
  * Map workers perform the map function and then store the output on their local disks
  * Reduce workers reach out to the correct map workers (orchestrated by the master program) to get the data they need to perform the reduce function
  * Reduce workers output the result to R number of output files, which are then sent back to the user program by the master computer once the work is completed

## Resources

* [MIT Lecture](https://www.youtube.com/watch?v=WtZ7pcRSkOA)
