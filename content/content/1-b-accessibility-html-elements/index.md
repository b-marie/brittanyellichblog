---
title: "HTML Elements"
lastmod: 2022-11-13T00:00:00+08:00
draft: false
tags: [accessibility]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Accessibility](../1-accessibility) / [HTML Elements](./)

## Overview

### HTML Basics

* Each page should always have a `DOCTYPE` specified
* Each page should have a `<html>` tag with a lang set (ex. en for english)
* Each `<head>` tag should have a meta sharset, like `utf-8`
* Each page should have a page title, which should be unique and should describe the page
* Header, Nav, Main, Footer, and Aside are major landmarks that should be used throughout a page to describe the layout of the content. Form and Section are also important, but aren't considered landmarks. Not every page should have each of these, but they're important for things like skip links, which can skip from nav to main. Each page should always have a Main landmark

### Headers

* Headers are used by screen readers to allow users to jump around in documents. If there aren't adequate headers on a page, a user must sit through the entire screen to find what they're looking for or interested in learning from your site.
* Headers should descend logically to break up the information on your page (H1, H2, H3, etc.)
* Ideally you should always use the native h1-h6 HTML elements for headings, but you can also use the ARIA role `heading` if you absolutely have to as well. Example below:

```HTML
<h2>I am a heading level 2</h2>
 
<div role="heading" aria-level="2">I am also a heading level 2</div>
```

### Buttons and Links

* Links are for navigation or change of context
  * Links like "learn more" aren't great as they don't describe exactly where they will navigate you to
  * Accesisbility properties in Google CHrome's dev tools will show the computed properties and calculated accessible name for each link, which is worth checking
* Buttons are for actions
* Don't try to use links for buttons or buttons for links

### Text

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

### Navigation

* You should allow screen reader users to skip your navigation so that they don't have to sit through it on every page load.
* This includes both your main site navigation as well as any content navigation on the specific page.
* There's an ARIA tag for navigation. A page can have several of them.
* Give dropdowns in navigation a Tree or Treegrid ARIA role.
* Text in navigation should be super readable and in colors that all users can see.
* Avoid nested dropdowns where possible, as they can be frustrating for users with physical disabilities. If you do include them, make sure they have tolerance for a wavering mouse and don't snap back to closed if a user's mouse navigates away momentarily.
* Add familiar icons to navigation to make it easier for a user to glance at the word and know where it leads.
* Navigation should be the same order regardless of where a user is in the site
* Include a site map as a backup for users that have difficult moving through navigation

### Menus

* There's an ARIA rol for menu or menubar which makes it easier for screen readers to interact with

### Images

* Almost all images should have alt text, which is the tag that is read by the screen reader to the user. If that alt text doesn't exist the screen reader will skip over the image entirely. This should be implemented with the alt attribute, an aria-label, or aria-labelledby which links to something else that describes the image.
* The description in alt text should be a description of what the image contains. You don't have to say "An image of..." as that will be apparent already. Include what is significant about that image and why it was included on the page for sighted users.
* Don't repeat the alt text in the caption if the image has a caption. Screen reader users would then have to hear that text twice. Imagine the caption as an extension of what's included in the alt text.
* Images of graphs require a bit of extra consideration, to make sure that the feel of the content of the graph is conveyed to the user through the alt text and caption (if applicable).
* Images used for branding or layout, such as spacers, don't need alt text. These may fail on automated tests of accessibility for your website, but that's one of many reasons why fully automated tests shouldn't be relied on completely for testing your website for accessibility.
* Images with a key shouldn't be reliant just on color to convey what they are representing for color blind users.
* Any image used to convey information to the user, such as scientific images where details are important, should be visible for users that have difficult discerning colors.
* Maps and icons should have a key to determine meaning for users that have difficulty seeing color.
* Use useful images to break up blocks of text
* Never put images behind text

### Forms

* Always use labels for each form field, to help a screen reader user navigate through the form. The only exception here is for buttons, since the text of the button already explains what it is.
* Using the proper input type is also important to convey to the user what type of field they are interacting with. Each input should have a type associated with it.
* Make current fields highlighted to make them easier to see for users with low vision
* Display all items vertically, one right after another, instead of placing them side-by-side, to make them easier to tab through.
* Use tab-order if needed to make sure that your form tabs through in the correct order
* Dropdowns should begin with unique information to make it easier for a user to type in a response. You can use `OPTGROUP` to group entries in a dropdown visually.
* Allow ample time for a user to fill out a form, and save their data as often as possible so that if the form times out they can come back to it and don't have to start from the beginning.
* Allow users to save their progress, or break a long form up into multiple sections to make it easier to navigate
* Check how long your form can sit before it times out.
* Use autocomplete where available.
* Use the `required` attribute where needed, but also communicate to the user what is required through text.
* Disabled inputs need to have the disabled tag on the input.
* If an error occurs, there should be aria-describedby or some other way to indicate which error is associated with each input programmatically.

### Radio Buttons and CheckBoxes

* Radio buttons and check boxes should be both tab and arrow-friendly. They should also be large enough for a user with a physical disability to click on them with limited range of motion.
* For radio buttons and checkboxes, only the first element should be included on a tab order. If the user hits tab again, they should move to the next form element, not the next button or box.
* Ideally you should use the native input types of "radio" or "checkbox", but you can also accomplish the same goal using the ARIA roles of "radio" and "checkbox" and manually managing tab orders.
* Fielsets should always have a legend, which is the first child of the fieldset.

```HTML
<fieldset>
  <legend>Favorite Food</legend>
    <label for="pasta">Pasta</label>
    <input id="pasta" name="food" type="radio" />
    <label for="pizza">Pizza</label>
    <input id="pizza" name="food" type="radio" />
</fieldset>

<div role="radiogroup" aria-labelledby="group-label">
  <h2 id="group-label">Favorite Food</h2>
  <div id="pasta-label">Pasta</div>
  <div tabindex="0" role="radio" aria-labelledby="pasta-label"></div>
  <div id="pizza-label">Pizza</div>
  <div tabindex="-1" role="radio" aria-labelledby="pizza-label"></div>
</div>
```

### Tables

* Tabular data belongs in tables, rather than a series of divs. They should also only be used for tabular data. Screen readers are better at navigating through tables and make the content easier to follow.
* Always include scopes in the HTML of a table to make it easier for a screen reader user to follow.
* Tables should always include a summary with a description of the data it contains.
* Don't repeat the summary information in the table caption, forcing a screen reader user to go through that content twice.

### Frames

Frames and iFrames can be difficult for screen readers to interact with.

### Lists

* Always use a list for anything that is a list (a list of 3 or more items)
* Lists should be implemented using the native `ul` and `li` HTML elements, but if needed they can also be implemented with the ARIA roles of `list` and `listitem`.

```HTML
<ul>  
  <li>One</li>
  <li>Two</li>
</ul>

<div role="list">
  <div role="listitem">One</div>
  <div role="listitem">Two</div>
</div>
```

### Audio

* If your site includes audio, make sure there is no vital data that is kept from users that cannot hear audio. Offer that in text form as well.
* Audio indicators, like a bell (ex. for chat apps), should have a visual indicator as well.
* Don't worry about providing a visual experience for things like ambient sounds or background music, since they aren't vital to the experience.
* If possible, include live transcribing for any experiences that are happening live
* Audio shouldn't autoplay

### Video

* If there's an audio component to a video, include subtitles. These are best in a band underneath the video so it can't obscure the action. Use fonts that are highly readable on a light background. Avoid all caps.
* When close captioning video, avoid transcribing vocal pauses and verbal missteps.
* Make sure video is large enough and clear enough that a user can see the facial expressions and hand movements of whoever is on video
* Videos shouldn't autoplay

### Animations

Try to avoid animations wherever possible, as they can be distracting.
If you can't avoid them:

* Make them only loop once
* Make only one animation happen at a time
* Show the animation statically until a user chosses to animate them

### Access Keys

An access key is added through an attribute to an anchor tag. It allows a user to hit a certain key combination to easily move to a certain element on a web page, or to set pages within a website.
There are very few standards on access keys out there as of 2012.

### TabIndex

Use tabindexes to allow keyboard users to focus elements that may not typically be focusable, like divs or spans. Ex., `tabindex="0"`. To make them activatable with a keyboard, use JavaScript to make sure that hitting the enter or space bar will interact with the element in the way you expect. This isn't necessary if you use the native button and link elements, but is necessary if `button` and `link` in the examples below are `div` or `a` tags.

```JavaScript
button.addEventListener('keydown', function (e) {
  // if ENTER or SPACE was pressed
  if (e.which === 13 || e.which === 32) {
    e.preventDefault();
    e.target.click();
  }
});
 
link.addEventListener('keydown', function (e) {
  // if ENTER was pressed
  if (e.which === 13) {
    e.target.click();
  }
});
```

### Alerts

* ARIA tags can help alert the user when there's an alert on a screen, like if the user will soon be timed out.
* A status role can be added to the alert for "polite" or "assertive" alerts.
  * "Polite" will interrupt a user once the screen reader is done with whatever it's doing
  * "Assertive" will interrupt a user immediately
