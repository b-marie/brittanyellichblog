---
title: "Code Reviews"
lastmod: 2022-10-03T00:00:00+08:00
draft: false
tags: [tech, code reviews]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes)

## Overview

Code reviews make everyone a better engineer and result in a better product over time. But developers tend to hate code reviews. It's always a source of tension between the author and the reviewer, because pointing out problems can take time and can make people feel bad.

### What is a Code Review?

Code reviews fall into the immense bucket of things that I couldn't really "learn on my own" before starting a career in Software Engineering. It's part of the loose set of skills that doesn't fit into boxes like "Learn CSS" or "Learn JavaScript".

A code review is simply a packaged set of code changes that one developer makes that is then reviewed by another developer before those changes can make it into production. One developer checks another developer's work for errors to make sure that the changes won't break anything and that the code will be maintainable over time.

### Benefits

* Ensure code meets whatever standards your team has
* Makes sure the solution does what it's supposed to do
* Verifies that the code is understandable by other engineers
* Spot-checking a coworker's work for errors
* Learning new ways to solve problems
* Breaking down silos within your domain by sharing knowledge
* They can be a good way to collaborate with your team on a design

### Things to Look For

* Check that the title, description, and issue related to the code review match what the code is trying to solve. Does the code do what the developer intended?
* Ensure all required metrics are passing (ex. unit tests, test coverage, etc)
* Note if there are too many changes within a single review. Perhaps it could be broken into multiple changes?
* Do the names that were chosen for variables and functions make sense?
* Is there anything that is difficult to understand that should have a comment explaining it?
* Are these changes going to be easy to maintain longterm?
* Are each of these changes necessary?
* Is there any complex logic that could be simplified?
* Do the unit tests truly test all of the introduced or changed functionality?
* Does the code require an update to documentation as well?
* Do UI changes match the designs?

### Anti-patterns

* Nit picking: not particularly helpful. Use code formatters where possible to avoid styling issues and make sure to communicate that what you're pointing out is a "nit"
* Requesting design changes when the code works: This is a waste of everyone's time unless there's a very good reason. This is an indication that you're looking at the code at the wrong time.
* Inconsistent feedback: Happens a lot when there aren't any standards on how your company does these and is an indication that standards should be introduced.
* Ghost reviewer: If your code change is too big you won't get an actual review.
* Ping pong reviews: Going back and forth and continuously requesting more changes. This happens when the goal of the review is to find problems. You can always find problems and this isn't an effective way to approach reviews. This is an indication that you need a better "definition of done" for your team.

### Tone

It is very hard to convey emotion through text, so it is important that you check your tone to make sure it comes across the way you want it to. This is a great thing to discuss in team agreements to make sure that everyone on your team is on the same page.

* Ask open-ended questions
* Avoid strong or opinionated statements
* Be empathetic. A lot of effort went into this change (probably)
* Point out things that you like or things that you thought the author did well

### Best Practices

* Understand why your team does code reviews
* Understand when the code review should occur
* Understand who will be responsible for the code review
* Know where to do the code review
* Remember that the goal is to ship the code

## Learning Resources

### Articles

* [x] [How to Make Good Code Reviews Better](https://stackoverflow.blog/2019/09/30/how-to-make-good-code-reviews-better/)
* [x] [Google Code Review Best Practices](https://google.github.io/eng-practices/review/reviewer/)
* [ ] [SmartBear Guide to Code Review Process](https://smartbear.com/learn/code-review/guide-to-code-review-process/)
* [ ] [Philipp Hauer Code Review Best Practices](https://phauer.com/2018/code-review-guidelines)
* [ ] [Joel Kemp on Giving Better Code Reviews](https://medium.com/@mrjoelkemp/giving-better-code-reviews-16109e0fdd36)

### Books

* [ ] [What to Look For in a Code Review](https://leanpub.com/whattolookforinacodereview)

### Videos

* [x] [Code Review Best Practices Video](https://www.youtube.com/watch?v=3pth05Rgr8U)
