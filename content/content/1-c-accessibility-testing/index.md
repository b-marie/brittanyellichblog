---
title: "Accessibility Testing"
lastmod: 2023-01-20T00:00:00+08:00
draft: false
tags: [accessibility]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Accessibility](../1-accessibility) / [Accessibility Testing](./)

## Overview

There are several automated testing options to test your site for accessibility.

* Use the [w3 valudator for checking HTML validation](validator.w3.org/nu). This has some great guidance for some high-level things that can be caught for WCAG compliance.
* Browser Plugins
  * WAVE - Web Accessibility Evaluation Tool by WebAIM
    * Contrast checker and other tools based on WCAG
    * Available in Chrome (Chrome extension) and FireFox
      * For the extension, in the settings menu make sure you have allows access to file URLs for local testing
  * Tenon Check
    * Chrome extension, requires an API key (free on their website)
    * Keeps history of past issues
  * axe by Deque
    * Free and pro version
    * Chrome extension. Adds an axe tab to your dev tools
* Developer Tools
  * eslint-plugin-jsx-a11y
    * Tests your jsx for accessibility
    * Can integrate with your IDE with a VSCode extension
  * axe-core
    * Library to write tests with axe to make sure there are no accessibility violations

### Automated Testing

Here are some automated testing options

### Manual Testing

#### Keyboard Testing

* Navigate the website with just a keyboard
* Use the `tab` key to navigate focusable elements on the page
  * Focus should be easy to see with a high contrast ratio
  * You can use `document.activeElement` in the JavaScript console to see what is currently focused
* Is there a skip link for bypassing navigation?
* Can you navigate through radio buttons/checkboxes with widget navigation? 
  * Widget navigation:
    * Use tab to focus on the group
    * Use arrow keys to navigate
* Interactive form controls are activated with the space key
* Links are activated with enter

#### Mouse Testing

* Navigate the website with your non-dominant hand to simulate users with physical disabilities
* Navigate the website with just a mouse

#### Zoom and Large Text

* Use `CTRL + +` on your site to see how the text grows for users that may need larger text
  * Are all navigation elements still visible and readable?
  * Is everything approximately in the same place as it was before?
  * Are images growing as well?
  * Are embedded objects growing along with the rest of the site?
  * Are all major browsers responding the same way?
* Set your browser to use large text, is everything still visible and readable?

#### Colors

* There are plug-ins available to test for various types of color blindness.
* Cannot use color alone to signify meaning
* Emulate different vision deficiencies in Firefox with tools > rendering
  * Can emulate different color issues

#### Screen Readers

Screen readers:

* A FireFox add-on called Fangs will render a page as it may be seen on a screen reader.
* List out headers for the user
* Tead alt tags for images
* Rist links on a page
* Use access keys
* Read out tables in the column:content format
* Will not read out `display: none` or `visibility: hidden`
* Screen reader modes:
  * Browse Mode
    * This is the default mode. It intercepts keystrokes to perform specific actions
    * Common single-key shortcuts:
      * h - navigate headings
      * 1-6 - navigate specific heading levels
      * t - navigate tables
      * b - navigate buttons
      * g - navigate graphics
      * TAB - navigate all elements
    * Navigating content:
      * Up/down arrows navigate the next or previous line
      * Left/right to navigate next or previous letter
  * Forms/Focus Mode
    * For navigating modes
  * Application Mode
    * Custom widgets with custom keyboard interactions added with JavaScript, like for games

All major operating systems also come equipped with a screen reader. However, it can be difficult to learn to use a screen reader if it's something that you aren't familiar with.
