---
title: "A Recap of GopherCon 2022"
date: 2022-10-10 T20:10:12-08:00
draft: true
tags: [tech, go]
author: Brittany Ellich
---

In October of 2022, hundreds of Gophers flocked to Chicago to celebrate their interest in Golang for the first time in three years.

## Compatibility - Russ Cox, Google

* Go 1 Compatibility - go.dev/doc/go1compat
  * "It is impossible to guarantee that no future change will break any program"
* Keep Go boring
  * API Checking
    * You can't take away API
    * Can't remove exported symbols without breaking anything
    * Use a list to keep track of all APIs are out, check that the package API matches each file
  * Testing
  *Adequate testing helps maintain compatibility
  * New Go versions are used within Google first
  Testing finds different kinds of incompatibility than API checks
* Why Programs Break Today
  * Output changes
    * A function gives a different output that's equally or more correct, but if code is expecting the old output it will break
    * If you need truly reproducible output you need to fork the code, but you'll be exposed to bug issues and won't be able to get new bug fixes
  * Input changes
    * Check syntax before calling parsers
    * Fork code to insulate from changes (but also bug fixes)
  * Protocol changes
    * HTTP/2 in Go 1.6
    * SHA 1 in Go 1.18 and 1.19
* Breaking Fewer Programs
  * Backward compatibility - New go, old code
    * Always add GODEBUG for likely problematic changes
    * Guarantee GODEBUG settings las for >= 2 years
    * Provide runtime/metrics counters to watch GODEBUG effects
    * Set specific GODEBUGs in source code for package main
    * Set default GODEBUGs using Go version in main module's go.mod.
  * Forward compatibility - Old go, new code
    * An older version of go will do a best-effort to compile, lets you know there's a go mismatch
  * Language compatibility
    * Every package has a go.mod with a Go version
    * Fix for-loop scoping
      * Vet looks for this problem
      * Use per-loop variables for go, the only complete solution would be to change the semantics.
      * Can use this with the go.mod compatible way to make that change
* An update on Go 2
  * Go 2 will never happen (or it has already happened)
    * They're going to double-down on compatibility
    * Compatibility is Go's most important feature
    * Existing code will continue to compile just as it always has

## How to Build a Distributed System (and should you) - Rebecca Bilbro, Rotational Labs

* Case Study: Signal for crypto
  * Building the Global Directory Service
    * Need a protocol that can run in parallel with blockchain that handles the PII data that you don't want public on the chain. Fast, secure, private, and decentralized. Like a signal for crypto.
    * Built this for TRISA. Organizations around the world can opt in through a web app. Get identity certificates and can use those to authenticate. Uses public key cryptography, messages are transmitted via mutula authentication. Use gRPC.
    * Problem: A centralized storage is an unfair advantage. Should it be in Germany, Singapore, the US, etc. Anybody co-located with the data will experience the low latency which is unfair.
* What is a distributed system?
  * A network of computers working together as to appear to the end-user as a single computer.
  * The computers are peers, working together to make the system more tolerant to failures like earthquakes and outages.
  * More available
  * Each peer has a copy of the database, and can respond independently
  * The complexity lies in synchronizing independent concurrent requests to update data. Sometimes the updates may cause the databases to become inconsistent.
    * There are several ways to synchronize peers, depending on how consistent the system needs to be.
      * Strong, Causal, Eventual.. What makes sense for your system and users.
      * Tradeoffs include: availability, staleness, cost
  * Opted for eventual consistency using a gossip protocol. Two peers randomly coordinate with each other and swap differences to coordinate. Eventually, all the peers will have the same version of the data.
    * Good option for low latency, high availability, and can tolerate some staleness.
  * Two open source packages:
    * Honu: Computes version vectors so that two peers can decide whose version is more up to date. The version vector allows comparing values and the number of times it has been updated so that it can decide if it should fast-forward its values or not.
      * Need a tie breaker for when two systems have updated their value and version at the same time. Have a PID that keeps track of times of updates
    * Trtl: Enables peers to periodically share their perspective with others in the system
* Mistakes we made
  * Go was an excellent choice for distributed systems
  * Bilateral Anti-Entropy is difficult because of the amount of concurrency that's happening
* What's on the horizon?
  * Not everyone needs a distributed system
  * Proposed new definition for distributed systems: A flow of eventss across time and space
  * The tools for the next generation of distributed systems may look familiar
  * Persistence by default
  * Geographic Event Encoding
    * Knowing where your events are coming from/going to is important for things like GDPR compliance
  * Total Ordering by Default
    * Total ordering requires consensus, which can impede performance
    * Can start to count on equitable global experience from everyone around the world
  * Automatic Reconfiguration
* Check them out at rotational.app

## Fuzz Testing Made Easy - Katie Hockman, DataDog

* Fuzz testing works around the edges of the system that you're already testing
* Exploring code paths that may be atypical
* Finds things that unit tests may miss
* How to fuzz - use `*testing.F`
  * Provide starting values to the fuzzer (optional), can leverage some of the inputs to your unit tests
  * Start fuzzing! A fuzzing engine will use the starting values, perform mutations, and then test! The Go fuzzer is very powerful
  * Will find bugs!

  ```go
  func FuzzFoo(f *testing.F) {
    f.Add(5, "hello") // Seed coprus addition
    f.Fuzz(func(t *testing.T, i int, s string( {
      out, err := Foo(i, s)
      if err != nil...
    })))

  }
  ```

* The corpus
  * A collection of inputs that guide fuzzing
    * Seed corpus: A user provided data set that is used to guide the fuzzer
    * Generated corpus: machine-generated and maintained by the fuzzing engine. Stored in the cache and only used by the fuzzing engine
* Fuzz Engine
  * Can use differential fuzzing to compare two functions (great for refactoring!!)
  * Returns a testdata file for issues that are found so you can see what inputs are used
  * Will automatically add the testdata files to your seed corpus in the future (regression testing!)
* `go test -fuzz`
* What makes it naive
  * Inputs unrelated
  * Ignores outcome
  * Structure agnostic
* Go's Fuzzing engine
  * Mutation-based (using existing inputs)
  * Coverage guided (pays attention to which code paths it hits in an attempt to expand code coverage)
  * Structured inputs

## Parsing without generators: Parser combinators in Go with Generics - Jeremy

* doomcheck.com
* Write the work plan in markdown. Estimates go in curly braces as ranges.
* Go does their markdown parsing, number cunrching, and some other stuff. Wrote a markdown parser
* Parser combinators in Go with generics
* Parsing
  * Taking a stream of tokens and turning them into a data structure
  * Textbook parsing
    * Lexing: Turn a raw data stream into a token stream
    * Parsing: Take the stream of tokens and turn them into the data structure
  * Handwritten parsing functions (ex. parseFile)
* A simple language example
  * comman mark spec on markdown
  * Composing a parser from small functions of the built parser package
  * github.com/golang/go/issues/49085 --> Non-starter unless someone can explain how to implement it
* Go generics
* Composable packages
* gocloc summary
  * parser.go
  * grammer.go
* Parser combinators
  * Accepts several parsers as input and returns a single parser as output
  * <https://en.wikipedia.org/wiki/Parser_Combinator>
* Engineering view
  * with parser combinators:
    * A parser is a data structure
    * Parsers are composable
    * Parsers are piecewise-testable
    * Easy to build a parser combinator toolbox
      * No non-core dependencies
      * Easy to customize
      * No code generation required
* Language processing view
  * Recognize languages that resists goyacc-style grammars
  * Backtracking gives you parsing superpowers
    * Must be careful to avoid terrible performance!
  * Anecdotally, comparatively easy to produce helpful error messages
* Go-specific thoughts
  * Why did we use generics?
    * What if it was just interface{} everywhere?
      * Panic factory. Type assertions everywhere.
    * generics are anti-panic sauce. They move a lot to compile time.
* Key inspiration: Elm parser
  * Elm is a front-end programming language that compiles to javascript
  * The API this talk is based on is based loosely on Elm's parser package
  * Demystifying parsers talk
* github.com/jhbrown-veradept/gophercon22-parser-combinators
  * exercises! Look at the loop implementation

## Lightning Talks Resources

* <https://blog.khanacademy.org/statically-typed-context-in-go/>
* gRPC

## Sponsors

* goland from jet brains

## Other things to look into

* WebAssembly

## Collect First, Ask Questions Later - Zach Wasserman, Fleet

* Fleet manages osquery on 100,000+ devices
* Two classes of client that interact with their server:
  * Osquery agent: Retrieving configurations, sending collected data
  * API clients: humans or scripts modifying configurations or retrieving data
* Use pprof comparison tools.
* Make collection of data a standard part of the runbook.
* Find out what information we request of users when something goes wrong. If you ask for it more than once and it's a resonable cost to collect, collect it automatically so that it's all in one place when an issue occurs.
* Identify "local state" vs. "system state".
* Collect errors across all different processes that are running, store those in redis, and then pull them out as system state when you create the debug archive.
* Collect everything in one place.
* Use the http/pprof "index" to see profile types.
  * Use pprof -http to view profiles
  * Use pprof comparison tools
  * Iterate!

## Exploring Network Programming by Building a Toxiproxy Clone - Jordan Neufeld, Shopify

* Site Reliability Engineer at Shopify
* Self-Taught Gopher
* What is Network Tooling?
  * Application (HTTP) - JSON layer
  * Transport (TCP and UDP) - Where we are going to focus
  * Internet - routing IP addresses
  * Network Access - Drivers, putting bits on the wire
* Why Go?
  * Cross-compile portable binaries
  * Standard Library Support (might not even need dependencies)
  * Accessible way to solve for custom needs
* Why would I build transport-layer tools?
  * At Shopify:
    * E-commerce platform
    * Hybrid architecture. A monolith with a bunch of services
    * Design for resiliency.
  * How do you test things like a flaky network?
* Chaos testing (Game Days) for testing resiliency assumptions
  * Introduce failure, observe results
  * Testing or Production environments (if controlled enough)
    * "The only substitute for production is production". You get a lot more value out of this but need to be a bit more careful.
  * Simulate slow or down connection between app and dependencies
* Toxiproxy: github.com/Shopify/toxiproxy
  * Open source tool written in Go
  * Proxy to simulate slow or broken netowkr conditions
  * Transport Layer (TCP)
  * Example use case: Put Toxiproxy between a web app and MySQL db
    * Add "toxics" on the upstream or downstream link (like a "Latency Toxic") to simulate a slow network response coming back from MySQL
* Demo
  * `net.Listen("tcp4", "0.0.0.0:8080")` puts the listener on TCP
  * Use netcat to connect on localhost to open the connection and test it
  * github.com/neufeldtech/tinytoxy
  * Use sleep latency to simulate a slow connection

  ```go
  func main() {
    listener, err := net.Listen("tcp4", "0.0.0.0:1337")
    defer listener.Close()
    for {
      downstreamConn, err := listener.

      go func(downstreamConn net.Conn) {
        defer downstreamConn.Close()
        _, err := downstreamConn.write([]byte("hi\n"))
        ...
      }
    }
  }

  ```

* Recap
  * It's productive, didn't have to do anything super fancy.
  * It's accessible, using Go to build tooling like this is easy to use and understand
  * It's fun
