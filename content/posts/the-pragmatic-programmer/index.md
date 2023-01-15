---
title: "Book Review: The Pragmatic Programmer"
date: 2022-02-14 10:00:00-08:00
draft: false
tags: [tech, continuous education, book review]
author: Brittany Ellich
---

[Get it on Amazon](https://read.amazon.com/kp/embed?asin=B07VRS84D1&preview=newtab&linkCode=kpe&ref_=cm_sw_r_kb_dp_5Y2239G0BEN58Z5FJCR2&tag=brittanyellich-20)

This was a truly excellent book that I have had on my list to read for a very long time.

[![The Pragmatic Programmer by David Thomas and Andrew Hunt](tpp20.jpeg)](https://read.amazon.com/kp/embed?asin=B07VRS84D1&preview=newtab&linkCode=kpe&ref_=cm_sw_r_kb_dp_5Y2239G0BEN58Z5FJCR2&tag=brittanyellich-20)

The Pragmatic Programmer is a book of programming best practices, learned from years of experience. The two authors of the book thoughtfully combined the best nuggets of wisdom from their time building software on how to be a “good” programmer. Note that some of the content is their opinion, but they are generally opinions that are widely held by the software community.

I read the 20th anniversary edition of the book, which apparently had been updated to make the examples in it a bit more timeless. Most of the code examples were of languages I was unfamiliar with, but it was still easy enough to follow along with the general concepts.

Below are some of the insights that I learned from the book, but I highly recommend reading it yourself. It is on the shortlist for me of the most important books on programming to read.

## Career Advice

- Software development is one of the best careers to be in right now, in terms of job opportunities and control over your work environment.
- Try to change your work environment to work for you, but don’t try forever. Like Martin Fowler says, “You can change your organization or change your organization.”
- Take charge of your career. If you don't, someone else will take charge of it for you.
- "People find it easier to join an ongoing success". If you show people a future that they're interested in, they will rally around it. Use this to create a better organization that more people want to be a part of.

### Pursuing Continuous Education

- Your experience and knowledge are the most valuable assets you have professionally. But you need to keep up on your knowledge, since the technology world moves so quickly. That framework or language you work with can quickly become obsolete.
- Manage your knowledge like an investor would manage an investment portfolio. Diversification and balance is key. Review periodically and rebalance areas where your knowledge may be lacking.
- Try to learn one new language each year. Or at least on some semi regular cadence. New languages require you to think in different ways, which will improve the way you write code using your existing languages. You might also find something new to take back to your team.
- Read one technical book per month. Technical books are ideal over blogs as you can go much deeper on a subject in a long-form book vs. an article. Study the languages and frameworks you currently use, and then once you've exhausted the best resources there, branch out to others. Also, focus on reading books about technology leadership, if either management or an individual contributor leadership path is something that you're interested in. I personally try to alternate a technical book with a leadership book every other month.
- Participate in meetups as much as is possible for you and as much as you are interested in it. It can be a bit difficult during times of pandemic, or when you have a young family you want to be around for. But there are meetups you can attend during the work day, or virtually, as well. Go and actively participate. Meet new people and make connections.
- Stay up to date with topics in the industry. Twitter is a great place for this, or blogs and newsletters.
- The process part of learning new things is what's most important. Get yourself in the habit of learning things, and borrowing ideas from the new things that you learn. Try to apply what you've learned to your current project.
- Be critical of what someone may call a "best practice". Think about who is writing it and consider who it may be a best practice for.
- "As Pragmatic Programmers, our base material isn't wood or iron, it's knowledge".
- Try to lose your mouse or trackpad and do all of your work with just the keyboard. The better you get into the habit of using keyboard shortcuts, the more productive you will be. Check out vim.
- Learning on your own is great, but some things are more effective when learned as a team.

## Gathering Requirements

- No decision is set in stone. Expect requirements to change as you're working, and write your code accordingly.
- The more you try and predict the future, the more you incur risk that you'll be wrong. Only plan out as far as you can see and what you can with the knowledge you currently have.
- Write code that is as flexible as possible, because you can almost guarantee it will change at the current pace of change
- The customer isn't always right. Ask lots of questions to get the root of an issue that a customer wants to solve to make sure you are finding the right issue to fix.
- Never stop gathering requirements when working on a project. There is always more clarification, and could be more things learned once a user gets to start using the project.
- See if you can observe the current process to get a better idea of what may be required to make the process better.

## Documentation

- Document your assumptions. Communicate your assumptions to others.
- Don't over-document requirements. The client isn't going to read them and you need to be able to stay flexible. Only document as much as is needed for the development team to understand the constraints they are working under. Being too specific will create a worse product.
- Create a project glossary to make sure that users and developers are calling things by the same names

## Design

- Understanding the bigger picture of what you are building is important for making informed decisions in the development process.
- Be as lazy as possible. Accept very little as inputs and promise little in return, to keep your codebase from blowing up unnecessarily (and giving yourself unnecessary maintenance work to do)
- Wherever a resource is allocated, that module is also responsible for deallocating it
- Use state machines for event-driven applications. Define the current state of the system based on the events that have occurred.
- Parameterize code where possible. If there are values that may change after the application goes live, store those elsewhere. Same with if you have environment or customer-specific values that shouldn't live within the app.
- Store static configuration in an external service API, instead of in a flat file or database. Multiple applications can share config information and you can better control access to it on a per-app basis
- Actors are independent processors with its own local, private state. They work to process messages at the end of a queue. This is like an elastic beanstalk worker which pulls values off of a SQS queue.
- Don't optimize prematurely. Make sure an algorithm really is a bottleneck before investing your time to improve it.
- When coming up with a name for something, ask yourself what your motivation is to create it. What you name things is important for communicating the intent behind it.

## Software Development Practices

### Good Enough Software

- Focus on writing software that is "good enough" instead of perfect. Good enough software lets you get something in front of users faster, which is important in today's world where iterating quickly is vital to your organization's business strategy.
- Perfect software doesn't exist. Don't waste your time chasing perfect.

### Easier to Change (ETC)

- Pick the design that is easiest to change (ETC). This works in almost all situations. Why is decoupling good? Because it's easiest to change. Why is the single responsibility principle good? Because it's easiest to change.
- Ask yourself after building something if what you just made makes the overall system easier or harder to change.
- Put third-party APIs behind your own layer of abstraction, which will make them easier to swap out in the future.
- Make sure your code is written in small modules that will be easy to break apart if you break your monolithic application into microservices in the future.
- Coupling makes code harder to change, because it links together stuff that has to be changed together. It's likely to break things or waste your time.
- Symptoms of coupling: Developers that are afraid to change code because they don't know what impact it may have, meetings where everyone has to attend because no one is sure who all is impacted by the change
- Prefer accessing things by methods instead of by properties. That way if the property changes, you can still maintain compatibility by mapping between the old API and the new one
- Inheritance introduces coupling. The child class is coupled to the parent and all other ancestors. Inheritance is OKAY but be sparse with what is inherited to avoid unnecessary bloat.

### Don't Repeat Yourself (DRY)

- Don't Repeat Yourself: "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system".
- If you find yourself copying and pasting something, you're probably not being very DRY.
- DRY also refers to the duplication of knowledge and intent. You should only be expressing business logic and knowledge in a single place, which will make those things easier to change in the future. If you change one thing, and realize that you also have to change many other things to accommodate it, your code isn't very DRY.
- Sometimes it makes sense to have some duplication if two different functions are validating two separate things that just happen to have the same rules. That will make those things easier to change in the future, and in that case it's okay to have code duplication and still be DRY.
- The hardest type of duplication to target is what occurs when different developers work on a project. To combat this it's important to build a team with good communication.

### Using Interfaces

- Use interfaces to hide the implementation from users. This doesn't mean you don't want users to not know how your code works, you just only want them to have to worry about providing their input and getting the output they expect.
- Try to make interfaces as generic as possible. Modules should provide a uniform experience for the user.
- Use OpenAPI or a similar standard for your APIs to make it easier to integrate with the service in a uniform way.
- Require multiple pieces of data for your API to be in a key/value data structure like a map, with a validation table to make sure you have what you're looking for, to make it easy to add and remove things when needed.
- Components should be self-contained, independent, and have a single purpose. When components are isolated, you can change one without having to worry about changing others. As long as the interface doesn't change, you don't have to worry about problems that may ripple through the entire system, and you reduce the risk associated with those changes.

### Global Data

- Every time you reference global data, you're tying your component into that shared data and likely introducing risk to your system. Any required context should be stated directly in the module, instead of relying on global data.
- Global data introduces coupling, which is bad.
- If it's important enough to be global, it should be an API

## Testing

- Writing unit tests is a good test of how coupled your code is. How much do you have to provide to get a unit test to build and run? If you have to import a lot to get a unit test to run, then it isn't decoupled very well.
- The biggest benefit from testing comes from writing the tests, not necessarily running them regularly. Writing tests helps to guide your code.
- The TDD cycle is to decide on a piece of functionality to create, write a test that will pass once it's implemented, implement the functionality, and see that the test passes. TDD is great for writing tests as you go, defining small, low coupled functions, but make sure you don't write too many tests for the sake of writing tests (ex., a test that only tests the function name probably isn't great).
- Unit tests should be testing against the contract to verify that the code meets the contract, and verify that your assumptions about the contract are correct.
- You can either test first, test during, or test never. Planning to write tests after the feature is complete means you will never actually write those tests.
- Use property-based tests (ex., using faker.js) to test wide varieties of inputs instead of the happy path that you hard-code into your unit tests. This will act more like a regression test since it will generate random values to see how it acts. If you come across a failure in a property-based test, save those values and write a specific test with them in your unit test suite to verify that the bug caused by those values is fixed and stays fixed.
- Integration tests focus on making sure that the major pieces of your application work correctly.
- Each bug should have its own test to trap it in the future, where practical. If a specific property was causing a bug, create a test using that property to make sure it doesn't happen again.

## Technical Debt

- Technical debt is an optimistic term. Some people put tasks in this category thinking that one day they will be paying back that debt. They probably won't.
- In cities, a single broken window signals to the world that that building is in disrepair, and it's okay for it to be in disrepair. Once that first window is broken, other windows start getting broken, and there's litter everywhere, and the building starts falling apart, and eventually that building needs to be condemned. The broken window is a psychological signal that that building has been written off. This also relates to your codebase. "Hopelessness can be contagious". Don't allow broken windows in your code (bad designs, poor code, TODOs, etc.). Fix it as soon as you see it, so you don't start the psychological damage for your team that that piece of the codebase doesn't matter. That we don't have time to fix those things. Because if you don't, it's just going to get worse.
- Don't cause collateral damage when trying to fix a P1 issue. Get the issue fixed and immediately deal with any broken windows

## Quality

- Quality is a team issue. If only one developer on the team really cares about quality, it likely won't go anywhere. You need a team effort to avoid the kind of entropy that results in low-quality products.
- Have pride in what you build. Stand by your work and make sure you have your name on it, so that people associate your name with good code.

## Maintenance and Refactoring

- Maintenance doesn't begin when the application is released. Programmers are always doing maintenance. Requirements change, the environment changes, libraries change… It should be a routine part of the process, not something that you start at the end.
- Be constantly critical of your code, finding opportunities to reorganize or improve it.
- From Martin Fowler, refactoring is "a disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior".
- Refactoring should be happening constantly, taking small steps to slowly improve behavior as part of your day-to-day tasks, instead of large rewrites which should be their own tasks.
- You need good automated unit tests to validate the behavior of code before you can safely refactor code.
- Code should be refactored for a variety of reasons. For example, if you find duplication, find coupling, see outdated knowledge, something that isn't performing well, or something that isn't used anymore. Slowly improve the codebase by refactoring things to make them better (but remember that nothing is perfect and we shouldn't strive for perfect).
- Time should never be the blocker for refactoring something, because if refactoring doesn't occur now it will be a much bigger investment down the road. There will never be more time. Refactor now.
- Refactoring should be a separate step from adding new functionality.

## Tooling and Debugging

- Set compiler warnings as high as possible so that you don't have to waste your time finding bugs that the computer can find for you, and you can focus on the more complicated stuff.
- Is the problem a bug or a symptom of a different problem?
- Is the bug in a tool that you're using, instead of in your code? Check Google for similar issues, there may be a GitHub issue reported already for it and a simple upgrade or downgrade of the library may fix it.
- Did the unit tests for it pass? If so, are the unit tests complete enough? Try running the unit tests again using the data that caused the bug to see if they still pass.
- Write down the problem. Often times writing down and describing the problem will rubber-duck you to a solution.
- Random failures are probably a concurrency problem

## Communication

- The best idea is useless without a way to effectively communicate it.
- Plan out what you want to say. Write an outline, and make sure that it communicates what you want to communicate. Keep refining until you get there.
- People won't listen to you unless you listen to them. Ask good questions, and get them engaged in the conversation. And listen. Really listen to what they have to say. Restate what they are saying to show that you are paying attention.
- Respond to every email and voicemail, even if only to say that you'll get back to them later on the subject (and then actually get back to them).
- Communication is more important than any technical skill you may accumulate. The more effectively that you communicate your ideas, the more influential you will become.
