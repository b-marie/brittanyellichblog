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

Code reviews make everyone a better engineer and result in a better product over time.

### What is a Code Review?

Code reviews fall into the immense bucket of things that I couldn't really "learn on my own" before starting a career in Software Engineering. It's part of the loose set of skills that doesn't fit into boxes like "Learn CSS" or "Learn JavaScript".

A code review is simply a packaged set of code changes that one developer makes that is then reviewed by another developer before those changes can make it into production. One developer checks another developer's work for errors to make sure that the changes won't break anything and that the code will be maintainable over time.

### Benefits

* Spot-checking a coworker's work for errors
* Learning new ways to solve problems
* Breaking down silos within your domain by sharing knowledge

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

### Tone

It is very hard to convey emotion through text, so it is important that you check your tone to make sure it comes across the way you want it to. This is a great thing to discuss in team agreements to make sure that everyone on your team is on the same page.

* Ask open-ended questions
* Avoid strong or opinionated statements
* Be empathetic. A lot of effort went into this change (probably)
* Point out things that you like or things that you thought the author did well

## Learning Resources

### Articles

* [x] [How to Make Good Code Reviews Better](https://stackoverflow.blog/2019/09/30/how-to-make-good-code-reviews-better/)
* [x] [Google Code Review Best Practices](https://google.github.io/eng-practices/review/reviewer/)
* [ ] [SmartBear Guide to Code Review Process](https://smartbear.com/learn/code-review/guide-to-code-review-process/)
* [ ] [Philipp Hauer Code Review Best Practices](https://phauer.com/2018/code-review-guidelines)
* [ ] [Joel Kemp on Giving Better Code Reviews](https://medium.com/@mrjoelkemp/giving-better-code-reviews-16109e0fdd36)

### Videos

* [ ] [Code Review Best Practices Video](https://www.youtube.com/watch?v=3pth05Rgr8U)
