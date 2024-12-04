---
title: "How to organize and improve your documentation for your favorite repositories"
date: 2024-12-04 10:00:00-08:00
draft: false
tags: [tech, documentation, writing]
author: Brittany Ellich
resources:
  - name: "featured-image"
    src: "library.jpg"
---

Today is day 4 of #blogvent, where I'm writing a blog post every day for the month of December. [Shoutout to @cassidoo for the idea](https://bsky.app/profile/cassidoo.co/post/3lcbjdiahas2l)!

## Introduction

One of the things I love about working at GitHub is our hackathons. Every few months we have the opportunity to drop what we currently have going on and focus for a few days on something that we really care about. This is ridiculously cool.

For a recent hackathon I decided I wanted to do something a bit different and focus on documentation; specifically the documentation of an internal app that our team uses a LOT day to day, and that other folks in different parts of the org occasionally need to get running. Documentation was very top of mind, as I had just joined a new team and had been reading **a lot** of documentation.

During a recent [GoTime Podcast](https://changelog.com/gotime/307), the subject of knowledge management was brought up. It was specifically recommended within the podcast to hire folks that are experts at knowledge management to get information out of engineers and into documentation in an organized fashion to accelerate the engineering team.

There was a debate on the merits of hiring an individual specifically focused on this, however it got me thinking a lot about how knowledge is generated and managed within the context of internal documentation, things like playbooks, ADRs, feature docs, etc.

## Background

The best [overview that I found of why engineering knowledge management is important came from lifecycle insights](https://www.lifecycleinsights.com/tech-guide/engineering-knowledge-management/):

> "Good engineers aren’t born; they’re made. Over the course of their career, engineers make design decisions and subsequently learn from them. As a result, their decision-making almost always improves. In contrast, an organization’s collective decision-making doesn’t always improve. Instead, it rises as engineers learn and degrade as engineers leave. To improve organizations’ decision-making quality, engineering managers should search for ways to capture and leverage past design experience. Therein lies the genesis of Engineering Knowledge Management, which is a strategy to capture explicit and tacit design knowledge for reuse in product development."

It is clear why there is a benefit to writing down information and decisions that would otherwise live in an engineer's head, and thus would be gone as soon as that engineer leaves. But just writing down that information isn't sufficient. It needs to be written down in a way that it can be easy for other members of the team to process and use when they need it.

Thus why I began exploring the idea of content management and organization. There is a lot of information out there on this, and here are some key themes that I came across that are important for knowledge management.

### Clarity

Writing simple and easy to understand documentation is best for users. One way of doing so is to make sure that you are using easy to understand language. A recommendation that I consistently see is to use something like [Hemingway App](https://hemingwayapp.com/) to help assess the reading level of what you are writing. Additional recommendations that I found came from [the GitHub Docs contribution guide](https://docs.github.com/en/contributing/writing-for-github-docs/best-practices-for-github-docs#write-for-readability ):

>- **Use plain language.** Use common, everyday words, and avoid jargon when possible. Terms that are well known to developers are fine, but don't assume that the reader knows the details of how GitHub works.
>- **Use active voice.**

### Conciseness

From [The Elements of Content Strategy](https://elements-of-content-strategy.abookapart.com/01-foreword/ ), a key component of content is that it is concise. This can also be represented by one of the tenets from [The Zen of GitHub](https://ben.balter.com/2015/08/12/the-zen-of-github/):

>"Anything added dilutes everything else".

The more content that is out there, the more difficult it will be for an individual to grapple with the ideas.

### Organizing an individual document

Most people don't read content. They scan it. 

Documentation should be structured in a way to make it easy to skim or scan. From [this document from the GitHub Docs team on optimizing content for scanning or skimming](https://docs.github.com/en/contributing/writing-for-github-docs/best-practices-for-github-docs#format-for-scannability):

>- **Use text highlighting** such as boldface and hyperlinks to call attention to the most important points. Use text highlighting sparingly. Do not highlight more than 10% of the total text in an article.
>- **Use formatting elements** to separate the content and create space on the page. For example:
>    - Bulleted lists (with optional run-in subheads)
>    - Numbered lists
>    - [Alerts](https://docs.github.com/en/contributing/style-guide-and-content-model/style-guide#alerts)
>    - Tables
>    - Visuals
>    - Code blocks and code annotations

### Documentation Templates

Using a template can apply consistency to documentation and allow engineers to focus on the important parts: the content. [The Good Docs Project](https://thegooddocsproject.dev/about/ ) has a reference on engineering documentation templates, and was shared with me by [@zerowidth](https://zerowidth.com/). Some key items that should be included in a template include:

- Raw template
- Template guide (how to fill out each section in the template)
- Template theory (empower the author to think like a tech writer)
- Template checklist (confirm you have everything covered)


Here is the markdown version of the documentation template I started using for this effort.

<details>

<summary>Document Template</summary>

```

<!---
Theory: This is a standard template that can be used for feature documentation. Using a template helps to reduce cognitive load while reading documentation and to make it easier to find what you are looking for. Some things to think about when writing documentation:
- Think about the audience for this document and what you want them to know
- Favor conciseness and clarity when writing documentation
- Use simple language wherever possible
- Use headings, bullet points, and short paragraphs

Guide: Here is a guide to each section of this document and how to use it:
- Terminology: Add any terminology that you come across when writing up this document that the average person would not know. Consider this from the perspective of someont that does not work within your domain, and what definitions they would need when reading this document to best understand it.
- Feature details: Add a subsection here for any specific details about this feature. Try to group information together in a logical way.
- Troubleshooting: Add any common knowledge on how to troubleshoot this feature here
- FAQ: This is a great spot to add any common questions you have come across while working on this feature
- References: Include any documentation that you know of that is relevant to this feature, such as epics, ADRs, product spec documents, etc.

Checklist: Complete the following while writing up this document
- [ ] Complete the template with all items that are relevant to what you're trying to describe
- [ ] Remove any section that isn't relevant to what you're trying to describe
- [ ] Update the Table of Contents with all relevant sections for easy navigability
- [ ] Edit each section of the document for simplicity, favoring conciseness and clarity. Consider the following:
    - [ ] Could the document be improved with more images?
    - [ ] Could the document be more clear with diagrams, like entity-relationship diagrams?
    - [ ] Could linking to other documents make this document easier to understand?
- [ ] Use the documentation guide to determine where this document should live relative to other documents
-->

# Title

Description of the thing

## Table of Contents

- [Terminology](#terminology)
- [Details](#details)
  - [Product specific detail 1](#product-specific-detail-1)
  - [Product specific detail 2](#product-specific-detail-2)
- [Troubleshooting](#troubleshooting)
  - [Troubleshooting title 1](#troubleshooting-title-1)
  - [Troubleshooting title 2](#troubleshooting-title-2)
- [FAQ](#faq)
- [References](#references)

## Terminology

- **Common term**: definition

## Details

### Product specific detail 1

Details

### Product specific detail 2

Details

## Troubleshooting

### Troubleshooting title 1

Details

### Troubleshooting title 2

Details

## FAQ

- **Question** Answer
- **Question** Answer

## References

- Product spec doc
- Epic links to create this product
- ADRs or EDRs involved

```

</Details>

### Organizing folders of documents

The subject of knowledge management is hot right now, with a lot of information geared towards organizing an individual's content through initiatives like [Building a Second Brain](https://fortelabs.com/blog/basboverview/?_gl=1*1vfsuv7*_ga*MTY4NzkyMzEwMi4xNzE3NjAyNDQz*_ga_FL652M4V7S*MTcxNzYwMjQ0My4xLjEuMTcxNzYwMjQ1NS40OC4wLjA).

One common recommendation from folks following the permanent knowledge management movement is to organize your notes following [the PARA methodology](https://fortelabs.com/blog/para/ ), or "Projects", "Areas", "Resources", and "Archive". [I managed to find one example of an engineering team using that same methodology for their documentation](https://blog.dclg.net/organizing-your-teams-knowledge-with-para ), but it didn't seem to quite fit shared documents in a way that would be easy to navigate and find what you're looking for.

After reaching out to the incredibly talented engineers I work with about this, I landed on [diataxis](https://diataxis.fr/ ). Diataxis is a methodology of dividing documentation into the different sections of "Tutorials", "How-to guides", "Reference", and "Explanation". This seems a bit more relevant to the group of documents typically collected throughout the lifespan of a repository. Here's a high-level description of each of these categories:

- **Tutorials:** Learning-oriented experiences
	- Give your learner things to do through which they can learn
- **How-to guides:** Goal-oriented directions
	- Address a specific goal or problem (playbooks probably fit in here)
	- Write from the perspective of the user
	- Task-oriented, instead of learning-oriented like tutorials
- **Reference:** Information-oriented technical description
	- Reference material is useful when it is consistent
	- The structure of the documentation should mirror the structure of the product
	- Provide examples
- **Explanation:** Understanding-oriented discussion
	- Deepens and broadens the reader's understanding of a subject. Reflection is important. Explain why something is done a certain way

Organizing documentation in a group like this allows for managing the collection of documents holistically. It's a lot easier to see what is there and what is missing when all features are grouped together, or all product types are listed together.

## Goals

My goals for the hackathon were to:

1. Develop a strategy for managing internal documentation
2. Apply it as best as I could within the timeframe allotted

### Strategy

Below is the strategy that I used for internal documentation grooming as part of the hackathon, and that I hope to apply to more repositories in the future. If you have ideas on this, [I would love to hear them](https://bsky.app/profile/brittanyellich.com)!

- [ ] Develop a documentation template (or multiple) that can be applied to the documents within the repository
- [ ] Divide the documents into the diataxis folder structure, and add additional sub-folders as necessary
- [ ] Do a first pass of each document already in the folder
	- [ ] Apply the standardized template
	- [ ] Add a Table of Contents for sections of the document
	- [ ] Identify where the document belongs in the above folder structure
	- [ ] Write a standardized document name that matches other documents in the same folder
- [ ] Once the documents are in the standardized format, look at the collection of documents and the individual documents more holistically
	- [ ] Is anything duplicated across multiple documents?
	- [ ] Is there enough context on why this project exists in the first place?
	- [ ] Identify any gaps in knowledge and record them to update in the future. Things to think about include:
		- [ ] Could the document be improved with more images?
		- [ ] Could the document be more clear with diagrams, like entity-relationship diagrams?
		- [ ] Is there shared terminology that should be included?
		- [ ] Could linking to other documents make this document easier to understand?
- [ ] Identify each stakeholder that may access these documents and make sure there is a quick path to them finding what they need (stakeholders to think about: internal developers, integrators, product, support) s/o to [@sampart](https://www.samsolutions.co.uk/sam/) for this recommendation
- [ ] Write a documentation guide for the repository for future document creation and updating (where doc templates live, how to decide what folder docs go in, etc)

## Results

I applied the above strategy to our internal app and saw a lot of great feedback from team members after the hackathon.

But more telling were the comments I got from other individuals months later, as they had to interface with our application and saw my name in the commit history of the docs. Things like "Wow, these look great, and it was so easy to find what I was looking for!". That was enough for me to realize that the knowledge management efforts were totally worth it.
