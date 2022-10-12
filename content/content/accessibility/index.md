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
* Every interactive element should be accessible with only a mouse and only a keyboard
* Don't override the default forward and back button unless you have a really good reason to do so
* Keep backgrounds simple and muted
* Make sure your content is well-organized for users that are easily distracted. Use bulleted lists where possible to make things easier to understand
* Information that is particularly important shouldn't be buried in blocks of text. Call out the very important things

#### Headers

* Headers are used by screen readers to allow users to jump around in documents. If there aren't adequate headers on a page, a user must sit through the entire screen to find what they're looking for or interested in learning from your site.
* Headers should descend logically to break up the information on your page (H1, H2, H3, etc.)

#### Text

* Contrast between the background and the foreground on text should be as high as possible
* Surprisingly, pure black and pure white actually aren't the best option. The most readable is off-black against off-white.
* If you can, include a font that can be used on your site for individuals who are dyslexic to easily use. Comic Sans is surprisingly one of the more easy to read ones.
* Sans Serif fonts should be used for blocks of text, as they're easier to read.
* Keep sentences short.
* Keep paragraphs short.
* Justified text, while it looks nice, causes uneven spaces between words and lettering that can be difficult for an individual with dyslexia to read, so avoid it.
* Font should be no smaller than 12pt, with 14pt being preferable
* Lines of text shouldn't be longer than 60-70 characters
* Keep instructions on the site as simple as possible

#### Navigation

* You should allow screen reader users to skip your navigation so that they don't have to sit through it on every page load.
* This includes both your main site navigation as well as any content navigation on the specific page.
* There's an ARIA tag for navigation. A page can have several of them.
* Give dropdowns in navigation a Tree or Treegrid ARIA role.
* Text in navigation should be super readable and in colors that all users can see.
* Avoid nested dropdowns where possible, as they can be frustrating for users with physical disabilities. If you do include them, make sure they have tolerance for a wavering mouse and don't snap back to closed if a user's mouse navigates away momentarily.
* Add familiar icons to navigation to make it easier for a user to glance at the word and know where it leads.
* Navigation should be the same regardless of where a user is in the site
* Include a site map as a backup for users that have difficult moving through navigation

#### Menus

* There's an ARIA rol for menu or menubar which makes it easier for screen readers to interact with

#### Images

* Almost all images should have alt text, which is the tag that is read by the screen reader to the user. If that alt text doesn't exist the screen reader will skip over the image entirely.
* The description in alt text should be a description of what the image contains. You don't have to say "An image of..." as that will be apparent already. Include what is significant about that image and why it was included on the page for sighted users.
* Don't repeat the alt text in the caption if the image has a caption. Screen reader users would then have to hear that text twice. Imagine the caption as an extension of what's included in the alt text.
* Images of graphs require a bit of extra consideration, to make sure that the feel of the content of the graph is conveyed to the user through the alt text and caption (if applicable).
* Images used for branding or layout, such as spacers, don't need alt text. These may fail on automated tests of accessibility for your website, but that's one of many reasons why fully automated tests shouldn't be relied on completely for testing your website for accessibility.
* Images with a key shouldn't be reliant just on color to convey what they are representing for color blind users.
* Any image used to convey information to the user, such as scientific images where details are important, should be visible for users that have difficult discerning colors.
* Maps and icons should have a key to determine meaning for users that have difficulty seeing color.
* Use useful images to break up blocks of text
* Never put images behind text

#### Forms

* Always use labels for each form field, to help a screen reader user navigate through the form. The only exception here is for buttons, since the text of the button already explains what it is.
* Using the proper input type is also important to convey to the user what type of field they are interacting with.
* Make current fields highlighted to make them easier to see for users with low vision
* Radio buttons and check boxes should be both tab and arrow-friendly. They should also be large enough for a user with a physical disability to click on them with limited range of motion.
* Display all items vertically, one right after another, instead of placing them side-by-side, to make them easier to tab through.
* Use tab-order if needed to make sure that your form tabs through in the correct order
* For radio buttons and checkboxes, only the first element should be included on a tab order. If the user hits tab again, they should move to the next form element, not the next button or box.
* Dropdowns should begin with unique information to make it easier for a user to type in a response. You can use `OPTGROUP` to group entries in a dropdown visually.
* Allow ample time for a user to fill out a form, and save their data as often as possible so that if the form times out they can come back to it and don't have to start from the beginning.
* Allow users to save their progress, or break a long form up into multiple sections to make it easier to navigate
* Check how long your form can sit before it times out.

#### Tables

* Tabular data belongs in tables, rather than a series of divs. Screen readers are better at navigating through tables and make the content easier to follow.
* Always include scopes in the HTML of a table to make it easier for a screen reader user to follow.
* Tables should always include a summary with a description of the data it contains.
* Don't repeat the summary information in the table caption, forcing a screen reader user to go through that content twice.

#### Frames

Frames and iFrames can be difficult for screen readers to interact with.

#### Audio

* If your site includes audio, make sure there is no vital data that is kept from users that cannot hear audio. Offer that in text form as well.
* Audio indicators, like a bell (ex. for chat apps), should have a visual indicator as well.
* Don't worry about providing a visual experience for things like ambient sounds or background music, since they aren't vital to the experience.
* If possible, include live transcribing for any experiences that are happening live
* Audio shouldn't autoplay

#### Video

* If there's an audio component to a video, include subtitles. These are best in a band underneath the video so it can't obscure the action. Use fonts that are highly readable on a light background. Avoid all caps.
* When close captioning video, avoid transcribing vocal pauses and verbal missteps.
* Make sure video is large enough and clear enough that a user can see the facial expressions and hand movements of whoever is on video
* Videos shouldn't autoplay

#### Pop-ups

* Probably just don't use them
* Make sure they're easy to close if you do use them. The close icon should be fairly big and easy to click on.
* Make sure they can be closed with the `esc` key, and also make sure that is written on the pop-up so a user knows that that's an option

#### Animations

Try to avoid animations wherever possible, as they can be distracting.
If you can't avoid them:

* Make them only loop once
* Make only one animation happen at a time
* Show the animation statically until a user chosses to animate them

#### CAPTCHAs

CAPTCHAs can be a huge issue for a screen reader as alt text can't be included of the letters on the image. 

* Always make sure that there is an accessible alternative for screen reader users if a CAPTCHA is absolutely required for your website (or just don't include it at all).
* If it times out, make sure it doesn't time out too quickly such that individuals that are slower at typing won't be able to pass it

#### Access Keys

An access key is added through an attribute to an anchor tag. It allows a user to hit a certain key combination to easily move to a certain element on a web page, or to set pages within a website.
There are very few standards on access keys out there as of 2012.

#### ARIA

ARIA allows disabled users to interact with more complex applications by declaring the role of certain items on the page.

* [ARIA site](http://www.w3.org/TR/wai-aria/)

#### Alerts

* ARIA tags can help alert the user when there's an alert on a screen, like if the user will soon be timed out.
* A status role can be added to the alert for "polite" or "assertive" alerts.
  * "Polite" will interrupt a user once the screen reader is done with whatever it's doing
  * "Assertive" will interrupt a user immediately

#### Timers

* Use the ARIA timer role to indicate to a screen reader user that something is counting down. By default, these won't announce the changes to the user, but this can be overridden by a developer. Be careful not to be too annoying, though!

#### Add-Ons

Some users will use add-ons, like Grease Monkey, to interact with your site and make it more readable for them, so making sure that your site is still usable with add-ons is a good idea.

#### Design

* Avoid using `outline: none` as a blanket on the page. You'll have to go back in and add focus and it's easy to forget to add it to some elements on the page.

#### Advertisements

Avoid them if you can. If you can't:

* Vet the advertiser to make sure the ad isn't too distracting
* Never use advertisements that play sound, or at least not unless the user explicitly asks for it
* Only display static ads if possible
* If an ad has a video element to it, only loop through it once
* Place the add horizontally across an entire page, so that a user can scroll past it if needed to hide it
* Don't put any content too close to an ad
* Align vertical ads to the right side of the page, so that a user can make the window smaller and avoid seeing it

#### Search

Include fuzzy checking or spell check on search for a user that may mispell a word

### Accessibility Testing

There are several automated testing options to test your site for accessibility.

#### Automated Testing

Here are some automated testing options

#### Manual Testing

* A FireFox add-on called Fangs will render a page as it may be seen on a screen reader.
* Use `CTRL + +` on your site to see how the text grows for users that may need larger text
  * Are all navigation elements still visible and readable?
  * Is everything approximately in the same place as it was before?
  * Are images growing as well?
  * Are embedded objects growing along with the rest of the site?
  * Are all major browsers responding the same way?
* There are plug-ins available to test for various types of color blindness.
* Navigate the website with your non-dominant hand to simulate users with physical disabilities
* Navigate the website with just a mouse
* Navigate the website with just a keyboard

#### Screen Readers

Screen readers:

* List out headers for the user
* Tead alt tags for images
* Rist links on a page
* Use access keys
* Read out tables in the column:content format
* Will not read out `display: none` or `visibility: hidden`

All major operating systems also come equipped with a screen reader. However, it can be difficult to learn to use a screen reader if it's something that you aren't familiar with.

### Accessibility Standards

508 standards for the US government

Any others that we should be aware of?

## Learning Resources

### Courses

* [ ] [Gerard Cohen Courses on Pluralsight](https://gerardkcohen.me/courses/courses.html)
* [ ] [Accessibility for Web Design](https://www.linkedin.com/learning/accessibility-for-web-design/welcome?u=3322)

### Articles

* [ ] [Deque: Accessibility in Design](https://www.deque.com/accessible-design/)
* [ ] [Deque: Accessibility in Development](https://www.deque.com/accessible-development/)
* [ ] [The Web Accessibility Introduction I wish I had](https://dev.to/maxwell_dev/the-web-accessibility-introduction-i-wish-i-had-4ope)
* [ ] [Comebacks for Five (Wrong) Arguments Against Accessibility](https://dev.to/maxwell_dev/comebacks-for-five-wrong-arguments-against-accessibility-5g5j)
* [ ] [Foundations: HTML Semantics](https://tetralogical.com/blog/2022/10/05/foundations-html-semantics/)
* [ ] [Is Your Organization Inclusive of Deaf Employees?](https://hbr.org/2022/10/is-your-organization-inclusive-of-deaf-employees)

### Videos

* [ ] [How Persons with Disabilities Use the Web](https://accessibility.deque.com/on-demand-how-persons-with-disabilities-use-the-web)
* [ ] [A11y cast series on Google Chrome developers channel](https://www.youtube.com/watch?v=HtTyRajRuyY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

### Books

* [ ] [Accessibility for Everyone by Laura Kalbag](https://abookapart.com/products/accessibility-for-everyone)
* [ ] [Practical Web Inclusion & Accessibility by Ashley Firth](https://learna11y.com/)
* [x] [Accessibility Handbook](https://www.oreilly.com/library/view/accessibility-handbook/9781449322847/)
