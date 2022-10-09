---
title: "A Recap of GopherCon 2022"
date: 2022-10-09 00:00:00-08:00
draft: false
tags: [tech, go, conferences]
author: Brittany Ellich
resources:
  - name: "featured-image"
    src: "featured-image.jpeg"
---

In October of 2022, hundreds of Gophers flocked to Chicago to celebrate their love of Golang and the Go community for the first time since 2019. The entire experience was an absolute blast. I enjoyed all of the presentations, the lightning talks, having chats with the sponsors, and meeting so many passionate engineers from around the world.

Here I summarize some of my key takeaways, insights, and things that I want to take back with me to my own Go programming experience.

## Compatibility

The first presentation was a keynote from [Russ Cox](https://twitter.com/_rsc) at Google on Go compatibility. One of the leading principles behind the language is to keep go boring to prevent compatibility issues and changes that may break other people's code.

Testing is an important part of compatibility. Besides integration testing, unit testing, and fuzz testing (discussed later!), new Go versions are used first at Google before they are made public. This has apparently caught quite a few bugs before new versions were released.

The Go team focuses on backward compatibility, forward compatibility, and language compatibility.

Backward compatibility represents new versions of Go with old code. Recommendations here are to always use `GODEBUG` for any problematic changes. `GODEBUG` settings last for a minimum of 2 years, so it should catch the majority of compatibility issues you may come across.

Forward compatibility refers to old versions of Go with new code. In this case, older versions of Go will attempt a best effort at compilation, and will let you know if there are any version mismatches that may require an upgrade.

Finally, language compatibility allows you to specify different Go versions in each package's `go.mod` file, allowing you to upgrade only where you need to.

Finally, Russ provided us an update on Go 2. Both that it probably won't ever happen, and that it already has. Go's compatibility promises make it so that a Go 2, or a version that creates significant breaking changes, likely won't ever happen. And isn't that a good thing, given how confusing referring to "Go 2" would be!

## Distributed Systems

There were a few talks that focused on distributed systems, which makes a lot of sense for a Go conference. [Rebecca Bilbro](https://twitter.com/RebeccaBilbro) from Rotational Labs discussed how her team implemented a distributed global directory service to run alongside blockchains, providing important identification information for regulatory purposes that you wouldn't want public on the chain.

There was a unique constraint that required a distributed system. A centralized database would create variations in latency throughout the world that would disrupt the "fairness" of the system. Creating a distributed system would make for a more consistent experience for all users.

As is common in distributed systems, however, when you store copies of databases throughout the world that can be updated simultaneously, records can possibly be updated on different databases at the same time. This requires resolving those updates to maintain a consistency. Deciding which update to keep isn't trivial, and is something that the Rotational Labs team solved for by choosing an eventual consistency model with a gossip protocol.

What this means is that, given enough time to resolve changes between databases, each database will "eventually" have the same and the correct updates. A gossip protocol refers to how computers holding these databases can "gossip" with one another, or compare their updates and decide on which ones to keep if there are conflicting changes.

The rotational labs team created two open source packages, both named after turtles which is super cool.

* [Honu](https://github.com/rotationalio/honu): Provides versioning of changes so that two computers can decide which version is the most recent.
* Trtl: Allows two computers to periodically share their changes with one another

Another distributed systems talk came from [Nathanial Murphy](https://twitter.com/pokenettle) at CrowdStrike, presenting how their distributed system can dynamically scale to support more than 1 Trillion events per day.

The key here were using [AIMD](https://en.wikipedia.org/wiki/Additive_increase/multiplicative_decrease) to automatically monitor capacity and adjust queueing systems to react to changes in the system. This means adjusting the number of processes in your workers that are pulling items off a message queue for processing in reaction to how well the system is performing. This looks a little something like this:

```go
var limit float64 = 1
var slowStart float64 = 99999999

err := doSomething()
if err == nil {
  if limit >= slowStart {
    limit += 1/limit
  } else {
    limit += 1
  } else {
    prev, next := limit, limit * 0.9
    slowStart = (prev + next) / 2
    limit = next
  }
}
```

This seems like a great way to handle automated autoscaling of your system, and has opened my eyes to an entire world of academic papers on the AIMD algorithm that I can't wait to dive into!

## Testing

There were multiple talks on testing, which is a subject near and dear to my heart. One of which was a technique that is entirely new to me that I **can't wait** to try out called [Fuzzing](https://go.dev/security/fuzz/).

[Katie Hockman](https://twitter.com/katie_hockman) from DataDog presented how to get started with fuzz testing in Go. Fuzz testing works by taking specified inputs for a test and mutating them over time to test the edges of your system and find new code paths that may be atypical. To write a fuzz test you take a normal unit test and wrap it in a fuzz test, like this:

```go
func FuzzFoo(f *testing.F) {
  f.Add(5, "hello") // Seed corpus addition, AKA the starting values
  f.Fuzz(func(t *testing.T, i int, s string( {
    out, err := Foo(i, s)
    if err != nil...
  })))
}
```

Fuzzing in Go will then take those starting values and modify them, continuously testing the unit of code with new values. You'll be alerted about anything "interesting" that causes errors in your code or that doesn't match your assertions. Inputs that cause these will be saved into a `testData` folder and automatically added to your starting values for the next time the tests are run, which is a great way to automatically add regression tests!

Another talk on testing was a case study on integration testing at Intel from [Sam Coyle](https://twitter.com/thesamcoyle), a smart and super cool lady that has given talks at many conferences. I can't wait to follow what she does in the future!

She presented her experience and pitfalls she ran into while adding integration testing to one of Intel's IoT offerings, their [video capture smart city solution](https://www.intel.com/content/www/us/en/internet-of-things/smart-cities.html).

The packages that they used include [test-containers-go](https://github.com/testcontainers/testcontainers-go) and [go-test-report](https://github.com/vakenbolt/go-test-report). She talked through the issues they came across and managed to resolve by finding old issues in GitHub describing an error in how go-test-report interprets results. How handy to have that kind of documentation to refer to!

## TinyGo

There were several opportunities to interact with and hear about TinyGo at GopherCon this year. [TinyGo](https://github.com/tinygo-org/tinygo) is a Go compiler built for small places, dramatically reducing the size of your application to run on things like microcontrollers that don't have a ton of space. One of my favorite talks was from [Donia Chaiehloudj](https://twitter.com/doniacld) at Powder.

Donia presented how she used TinyGo with an Arduino Nano 33 and a DHT sensor to monitor the temperature and humidity of her hen house. She used Grafana for visualizations that tracked the temperature and humidity changes over time. It was a beautiful example of over-engineering with microcontrollers!

Donia also mentioned several ways to get involved with TinyGo. Getting hardware can be a bit tough with parts shortages these days, but there's a [TinyGo Playground](https://play.tinygo.org/) available online that can simulate hardware. The TinyGo team is also looking for contributors to TinyGo, and there's a slack channel in the [Gopher slack](https://gophers.slack.com/messages/general/) to coordinate efforts.

[Ron Evans](https://twitter.com/deadprogram) from The Hybrid Group also gave us a few updates on what's happening in the TinyGo world. He [showed off one of the TinyGo Helmets](https://twitter.com/deadprogram/status/1578807043305385984?s=20&t=nk2n7t95GL27X_qqXKEzFA) and discussed some projects that have come up in the last year. His [GopherBot](https://twitter.com/furriebot) is super cool!

## Sponsors

There were a [ton of excellent companies sponsoring the event](https://www.gophercon.com/page/2035126/sponsors). It is wonderful to see organizations supporting the Go community by helping to make GopherCon happen. The majority of sponsors also made it very clear that they are hiring (sorry folks, I'm a happily employed Hubber). There were also a few that had some other suggestions for how to engage.

CockroachDB was calling for contributions to their open source packages, which would be a great way to get started in open source. Especially during the month of [Hacktoberfest](https://hacktoberfest.com/)!

JetBrains was there with [GoLand](https://www.jetbrains.com/go/) tutorials which were **very** cool, and has definitely convinced me to give it a shot. The syntax highlighting is very nice, and it feels very familiar after using IntelliJ for Java!

## Conclusion

I feel extremely fortunate that I had the opportunity to attend GopherCon 2022. The Go community is incredibly welcoming, even to new Gophers like me!

I highly recommend checking out the talks once they are available on YouTube if you missed any of them. While they were all really well done and insightful, here's a list of my favorite must-watch talks from the conference if you have time for them. I'll add links to the talks once they are up on YouTube:

* Compatibility: How Go Programs Keep Working by [Russ Cox](https://twitter.com/_rsc), Distinguished Engineer at Google
* Fuzz Testing Made Easy by [Katie Hockman](https://twitter.com/katie_hockman), Team Lead at DataDog
* Tiny Go: Getting the Upper Hen by [Donia Chaiehloudj](https://twitter.com/doniacld), Software Engineer at Powder

Also, here are a few that I missed that I really wanted to watch after hearing some great things about them from other attendees.

* Aerospace Go by [Patricio Whittingslow](https://linkedin.com/in/patriciowhittingslow), Systems Engineer at LIA Aerospace
* Secure Coding in Go: Avoiding Common Vulnerabilities to Better Secure Your Code by [Benji Vesterby](https://twitter.com/benivesterby), Principal Engineer at Synsaber
* Safe, Fast, and Easy: Building a Plugin System with WebAssembly by [Kyle Conroy](https://twitter.com/kyle_conroy), Engineering Manager at Retool

I'm looking forward to hopefully attending the next GopherCon in [San Diego](https://twitter.com/erikstmartin/status/1579088487802077186?s=20&t=nk2n7t95GL27X_qqXKEzFA) in 2023!
