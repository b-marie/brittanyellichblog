---
title: "Accessibility"
lastmod: 2022-10-05T00:00:00+08:00
draft: false
tags: [accessibility]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

## Overview

### Why is accessibility important?

* Good accessibility is good design. It allows anyone to experience what you've made regardless of what technology they use.
* Understanding the tools used to enhance accessibility on the web as well as how a user may be limited will improve the abilities of developers and designers to build more accessibile websites.

### HTML Elements for Better Accessibility

#### Layout

* HTML layout is one of the most important things to be aware of for screen readers. A screen reader will read the HTML of a website from top to bottom, using headings to differentiate sections of the content. If your website is not properly structured it will be far more difficult to navigate.
* The safest way to structure your HTML is in a way that makes the most sense if you were to print it all out without any formatting.

#### Headers

* Headers are used by screen readers to allow users to jump around in documents. If there aren't adequate headers on a page, a user must sit through the entire screen to find what they're looking for or interested in learning from your site.
* Headers should descend logically to break up the information on your page (H1, H2, H3, etc.)

#### Navigation

* You should allow screen reader users to skip your navigation so that they don't have to sit through it on every page load.
* This includes both your main site navigation as well as any content navigation on the specific page.

#### Images

* Almost all images should have alt text, which is the tag that is read by the screen reader to the user. If that alt text doesn't exist the screen reader will skip over the image entirely.
* The description in alt text should be a description of what the image contains. You don't have to say "An image of..." as that will be apparent already. Include what is significant about that image and why it was included on the page for sighted users.
* Don't repeat the alt text in the caption if the image has a caption. Screen reader users would then have to hear that text twice. Imagine the caption as an extension of what's included in the alt text.
* Images of graphs require a bit of extra consideration, to make sure that the feel of the content of the graph is conveyed to the user through the alt text and caption (if applicable).
* Images used for branding or layout, such as spacers, don't need alt text. These may fail on automated tests of accessibility for your website, but that's one of many reasons why fully automated tests shouldn't be relied on completely for testing your website for accessibility.

#### Forms

* Always use labels for each form field, to help a screen reader user navigate through the form. The only exception here is for buttons, since the text of the button already explains what it is.
* Using the proper input type is also important to convey to the user what type of field they are interacting with.

#### Tables

* Tabular data belongs in tables, rather than a series of divs. Screen readers are better at navigating through tables and make the content easier to follow.
* Always include scopes in the HTML of a table to make it easier for a screen reader user to follow.
* Tables should always include a summary with a description of the data it contains.
* Don't repeat the summary information in the table caption, forcing a screen reader user to go through that content twice.

#### Frames

Frames and iFrames can be difficult for screen readers to interact with.

### Other Website Features

#### CAPTCHAs

CAPTCHAs can be a huge issue for a screen reader as alt text can't be included of the letters on the image. Always make sure that there is an accessible alternative for screen reader users if a CAPTCHA is absolutely required for your website (or just don't include it at all).

### Accessibility Testing

There are several automated testing options to test your site for accessibility.

All major operating systems also come equipped with a screen reader. However, it can be difficult to learn to use a screen reader if it's something that you aren't familiar with.

## Learning Resources

### Courses

* [ ] [Gerard Cohen Courses on Pluralsight](https://gerardkcohen.me/courses/courses.html)
* [ ] [Accessibility for Web Design](https://www.linkedin.com/learning/accessibility-for-web-design/welcome?u=3322)

### Articles

* [ ] [Deque: Accessibility in Design](https://www.deque.com/accessible-design/)
* [ ] [Deque: Accessibility in Development](https://www.deque.com/accessible-development/)
* [ ] [The Web Accessibility Introduction I wish I had](https://dev.to/maxwell_dev/the-web-accessibility-introduction-i-wish-i-had-4ope)
* [ ] [Comebacks for Five (Wrong) Arguments Against Accessibility](https://dev.to/maxwell_dev/comebacks-for-five-wrong-arguments-against-accessibility-5g5j)

### Videos

* [ ] [How Persons with Disabilities Use the Web](https://accessibility.deque.com/on-demand-how-persons-with-disabilities-use-the-web)
* [ ] [A11y cast series on Google Chrome developers channel](https://www.youtube.com/watch?v=HtTyRajRuyY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

### Books

* [ ] [Accessibility for Everyone by Laura Kalbag](https://abookapart.com/products/accessibility-for-everyone)
* [ ] [Practical Web Inclusion & Accessibility by Ashley Firth](https://learna11y.com/)
* [ ] [Accessibility Handbook](https://www.oreilly.com/library/view/accessibility-handbook/9781449322847/)
