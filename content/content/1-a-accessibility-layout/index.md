---
title: "Accessibility Layout"
lastmod: 2022-10-14T00:00:00+08:00
draft: false
tags: [accessibility]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Accessibility](../1-accessibility) / [Accessibility Layout](./)

## Overview

* HTML layout is one of the most important things to be aware of for screen readers. A screen reader will read the HTML of a website from top to bottom, using headings to differentiate sections of the content. If your website is not properly structured it will be far more difficult to navigate.
* The safest way to structure your HTML is in a way that makes the most sense if you were to print it all out without any formatting.
* Every interactive element should be accessible with only a mouse and only a keyboard
* Don't override the default forward and back button unless you have a really good reason to do so
* Keep backgrounds simple and muted
* Make sure your content is well-organized for users that are easily distracted. Use bulleted lists where possible to make things easier to understand
* Information that is particularly important shouldn't be buried in blocks of text. Call out the very important things

### Pop-Ups

* Probably just don't use them
* Make sure they're easy to close if you do use them. The close icon should be fairly big and easy to click on.
* Make sure they can be closed with the `esc` key, and also make sure that is written on the pop-up so a user knows that that's an option

### CAPTCHAs

CAPTCHAs can be a huge issue for a screen reader as alt text can't be included of the letters on the image.

* Always make sure that there is an accessible alternative for screen reader users if a CAPTCHA is absolutely required for your website (or just don't include it at all).
* If it times out, make sure it doesn't time out too quickly such that individuals that are slower at typing won't be able to pass it

### Timers

* Use the ARIA timer role to indicate to a screen reader user that something is counting down. By default, these won't announce the changes to the user, but this can be overridden by a developer. Be careful not to be too annoying, though!

### Advertisements

Avoid them if you can. If you can't:

* Vet the advertiser to make sure the ad isn't too distracting
* Never use advertisements that play sound, or at least not unless the user explicitly asks for it
* Only display static ads if possible
* If an ad has a video element to it, only loop through it once
* Place the add horizontally across an entire page, so that a user can scroll past it if needed to hide it
* Don't put any content too close to an ad
* Align vertical ads to the right side of the page, so that a user can make the window smaller and avoid seeing it
