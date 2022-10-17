---
title: "Golang"
lastmod: 2022-10-06T00:00:00+08:00
draft: false
tags: [go]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Golang](./)

Integrity is an important part of Go. It has zero value. Any variable allocated in memory is automatically set to its zero value (no undefined)

## Simplicity

* Go is successful because of simplicity
  * Lots of languages are turning into the same language
    * Sapir-Whorf Hypothesis: Language influences thought
    * If all languages converge to the same language, we'll all be thinking the same way, which is dangerous
    * These languages are evolving by adding features. They're becoming more complicated and more similar to each other. "Bloat without distinction"
  * Go isn't like that. No significant changes to the language since Go 1
* Design by consensus
* Overriding decisions made when building Go by optimizing for Readability
  * Readable means Reliable
* People ask for map and filter and the maintainers say no, because they become more expensive and a simple for loop is fine
* Go's goals
  * clean procedural language build for scalability
  * Mostly server software
* Simple can be expressive
  * Simplicity is the art of hiding complexity.
    * Garbage collection
      * No programmer interface for garbage collection. But lots of complexity in the background
      * No mention of garbage collection in the spec. You don't have to think about it
    * Concurrency
      * Write your program as independently executing pieces. In Go, concurrency has three elements:
        * goroutines (execution)
          * Start with the go keyword: `go`
          * Extremely simple UI. Minimal design that hides all of its complexity
        * channels (communication)
        * select (coordination)
    * Constants
      * In Go, constants are just numbers, even though (because) it is strongly typed
      * Simple to use, but complicated behind the scenes
      * One of the hardest thing about designing Go
    * Interfaces
      * Just a set of methods. No data. Simple idea, but more complex than expected

## Syntax

* Variables
  * You can declare variables with the keyword `var`, which sets things to its zero value state
  * If you use just `int`, the compiler will choose the integer size we use. You don't have to use precision-based integers until you really have to.
  * `floats` you have to choose a precision, either `float64` or `float32`
  * To declare variables and initialize, use the short variable declation operator:
        aa := 10
        bb := "hello"
        cc := 3.14159
        dd := true
  * Casting variables (conversion instead of casting)
        aaa := int32(10)
  * Strings
    * Under the surface, the string has the pointer to the value and the number of bytes that it takes
  * Struct
    * Make user-defined types using structs
    * Define the values with `name` then `type`

        ```go
        type example struct {
            flag    bool
            counter int16
            pi      float32
        }
        ```

    * Go also has literal construction like this:

        ```go
        e1 := example{}
        e2 := example{
            flag:       true,
            counter:    10,
            pi:         3.141592,
        }
        ```

* Printing
  * `fmt.Println("Messaging", a, b, c, d)` --> Just for basic printing
  * `fmt.Printf("var a int \t %T [%v]\n", a, a)` --> Printf is for special formatting

## Go Proverbs

* The game of go is very easy to learn and very hard to master
* [Go Proverbs](https://go-proverbs.github.io/)
* Good for code reviews or StackOverflow responses:
* Don't communicate by sharing memory, share memory by communicating
  * Passing on a channel. If you send the object over a channel without a pointer, you don't have access to it anymore
* Concurrency is not parallelism.
  * Beginners often confuse them. Concurrency is a way of structuring your program to make it easier to understand and scalable. Parallelism is the execution of multiple go routines in parallel.
* Channels orchestrate; mutexes serialize
  * If you put a mutex on a variable, only one thing can ever happen at a time to that variable
* The bigger the interface, the weaker the abstraction
  * In Go, the smaller the interface, the easier it is to work with
* Make the zero value useful
  * Try to arrange the API of your package to have the zero values be useful out of the box.
* interface{} says nothing
  * It carries no information. Think very hard if you really should have an empty interface.
* Gofmt's style is no one's favorite, yet gofmt is everyone's favorite
  * The way that it formats isn't anyone's favorite. No one likes how it formats but everyone likes that it formats
* A little copying is better than a little dependency
  * You can make your programs better and faster if you use fewer dependencies. If you can just copy and not add dependencies, do that
* Syscall must always be guarded with build tags
  * If you import syscall into your package, you MUST have a build tag. Syscall isn't portable.
* Cgo must always be guarded with build tags
  * Very non-portable. Make sure that the Cgo you're calling in is protected.
* Cgo is not Go
  * It's a trap to be able to easily connect to C, or other languages in general.
* With the unsafe package there are no guarantees.
* Clear is better than clever.
  * Write simple/clear code rather than trying to make the densest code that you can.
* Reflection is never clear.
  * Very few people should be playing with reflection. It's very powerful but very difficult to use.
* Errors are values.
  * The aren't exceptions.m
* Don't just check errors, handle them gracefully.
  * Think if you should be doing something with that error. A big part of programming is how you handle errors.
* Design the architecture, name the components, document the details.
  * Name things while you're designing the architecture. The name should carry a fair bit of the weight of what you architected.
* Documentation is for users.
  * Think about what the function is actually for, not just what it does. When would you use it. Think of yourself as the user of the package, not just the impementer.

## Learning Resources

### Articles

* [ ] [Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments)
* [ ] [Go By Example](https://gobyexample.com/)
* [ ] [Uber Go Style Guide](https://github.com/uber-go/guide/blob/master/style.md)
* [x] [Go Proverbs](https://go-proverbs.github.io/) with a [video](https://www.youtube.com/watch?v=PAAkCSZUG1c)
* [ ] [100 Go Mistakes](https://github.com/teivah/100-go-mistakes)
* [ ] [Learn Go With Tests](https://quii.gitbook.io/learn-go-with-tests/)
* [ ] [Defer, Panic, and Recover in Go](https://go.dev/blog/defer-panic-and-recover)

### Books

* [ ] [Mastering Go](https://www.amazon.com/Mastering-Go-professional-utilities-concurrent/dp/1801079315/ref=sr_1_1?crid=3477MH5Z40C9J&keywords=mastering+go&qid=1665114312&qu=eyJxc2MiOiIxLjI2IiwicXNhIjoiMC44NCIsInFzcCI6IjAuOTAifQ%3D%3D&sprefix=mastering+%2Caps%2C104&sr=8-1)
* [ ] [Learning Go](https://learning.oreilly.com/library/view/learning-go/9781492077206/)
* [ ] [The Go Programming Language](https://www.gopl.io/)

### Courses

* [ ] [Ultimate Go Training](https://www.ardanlabs.com/training/ultimate-go/)

### Meetups

* [ ] [Gophercon](https://www.gophercon.com/)

### Videos

* [ ] [A Theory of Modern Go](https://peter.bourgon.org/blog/2017/06/09/theory-of-modern-go.html)
