---
title: "Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations - A Review"
date: 2019-09-02 20:10:12-08:00
draft: false
tags: [tech, devops, book review]
author: Brittany Ellich
resources:
  - name: "featured-image"
    src: "featured-image.jpeg"
---

Working as a Software Engineer contractor at Nike for the past several months, I have been preached to about the gospel of the book [Accelerate](https://www.amazon.com/gp/product/1942788339/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1942788339&linkCode=as2&tag=jaquenetta-20&linkId=9f49054ce45424cbe1d929e0f6ad59fc) on more than one occasion. I finally had a gap in my reading schedule that allowed me to fit it in.

I wanted to summarize some of the key points I got out of the book. Which is easier said than done, considering I think more of the book is highlighted than isn't. I have to admit, I blog more for providing easy access to my notes for my future self than anything else. Thus, I wanted to organize the key takeaways I found.

The book summarizes several [years of survey-based research conducted and summarized by Puppet Labs](https://puppet.com/resources/whitepaper?topics%5B1076%5D=1076) (shoutout to PDX-based businesses!). Surveys were used as it's the easiest way to get a lot of data, quickly, and are relatively easy for comparing changes that occur year over year.

A common theme throughout the book is that there are certain practices and principles that set high-performing organizations apart from medium and low-performing organizations, and that those high-performing organizations tend to have better business results overall when compared to their counterparts. Essentially, following the practices outlined in the book statistically results in better organizations with better business results. Seems pretty straightforward, right?

## Measuring Software Team Results

One theme revolved around measuring the results of software teams. Something that, as a Software Engineer, is near and dear to my heart. One tidbit I found interesting is around velocity. "When velocity is used as a productivity measure, teams inevitably work to game their velocity". Thus, using velocity (or work completed over time, generally measured as story points) is not only useless as a measurement for comparison purposes, it also leads to mistrust and a focus on completing as many stories as possible over other far more important practices like collaborating with other teams.

So what should be measured? The team recommends defining your own organizational metrics, focusing on outcomes over output, and organization results instead of team-based results. Some suggestions included delivery lead time, deployment frequency, time to restore service, and change fail rate.

One measurement that seemed particularly useful was the amount of time spent on new work versus unplanned work or rework. This is a measure of how quickly features are getting built, which relies on a well-designed infrastructure that isn't going to fall apart in order to allow engineers the time to build new things. The high performing organizations reported 49% of their time on new work and 21% on unplanned work/rework, compared to 38% and 27% respectively for low-performers.

## Just Say No To Outsourcing

Another interesting takeaway from the book was that, since the overall performance of a software team has an affect on business results, outsourcing software that is extremely important to your business can have a detrimental effect on results. Building that software capability within your organization, if your product and business is dependent upon that, will improve your overall results dramatically when compared to outsourcing projects to another team.

Does this mean that all external software is bad? Definitely not. It would be absolutely ridiculous for an organization to build all of its own software. Think about it, email systems, word processors, project management software... It's definitely not worth reinventing that wheel. But having the control and expertise over mission-critical software is definitely a differentiator over competitors.

## Sharing is Caring

How information is spread through an organization has a major impact on employee performance, which in turn affects organizational performance. If you work in one of those organizations where people hoard information away from others, or use it as leverage to gain power, that's probably a sign that the organization itself isn't all that healthy. The book broke up organizations into three broad categories originally described by Westrum in 2014: pathological, bureaucratic, and generative.

Pathological organizations use fear and information holding for individuals to make political moves. It's probably pretty obvious, but this is a detrimental culture paradigm for technology (and basically any) organization. If individuals are constantly trying to show that they are better or know more than their peers in an attempt to get ahead, then that restricts the capability of teams to grow together.

Bureaucratic organizations put a lot of rules in place in to allow silos to maintain control over their own space. This can make things especially difficult for technology organizations that require getting to market quickly to maintain a competitive advantage.

Finally, generative organizations are mission-focused, and decisions that are made at every organizational level are focused on meeting goals. These organizations are typically characterized by good information flow, which in turn leads to them performing better than their pathological and bureaucratic peers.

## Continuous Delivery is King

One thing that was evident by the book and should come as no surprise is that continuous delivery is one things that separates high- and low-performing organizations. Adopting continuous delivery is critical to both ship fast and improve employee morale. If engineers are spending time on code deployment, that means that they aren't spending time building new features. Basically anything repetitive like deploying code, testing, or running scripts should be automated in some way or fashion in order to allow for engineers to focus on doing the things that truly matter.

One important feature that dramatically improves the performance in a continuous delivery environment is low-coupling. This means reducing dependencies on other teams and services so that changes can be made without impacting or consulting with other teams.

## Include Everyone in the Design Phase

Anyone whose input could dramatically change the outcome of the overall design of a project should be included in the design phase. This means including the security and operations folks up front, making tweaks in the beginning to a design as opposed to making dramatic changes down the line. It doesn't hurt if your developers have a bit of security and operations knowledge too.

This is definitely not a new concept, but seems to be new to software and is what sparked the 'DevOps' movement, bringing developers and operations closer together. Security folks are included, but unfortunately didn't make it into the acronym. Bringing teams together in the design phase has been widely practiced in manufacturing for years, so this really isn't a new concept. For example, safety should be involved in initial designs of a new manufacturing line, so that critical safety issues can be addressed before construction begins.

## Organizational Culture Matters

The final point I wanted to bring up was how organizational culture impacts the overall performance of the technology organization. In particular, cultures with high levels of burnout tend to have poorer performance overall than other organizations. Burnout can be the result of a lot of things, but in particular is brought on by a lot of overtime, poor requirements, bad deployment practices, or bad leaders. This is costly both due to employees not being able to perform well when they are at work and high turnover due to employees moving to greener pastures after high levels of burnout.

Having experienced burnout myself, this is something that I definitely care a lot about. For me, I get most frustrated and burnt out when I know I'm spending time doing work that doesn't matter, like repetitive testing or manual processes that could be automated, or when I don't fully understand the value that the work I'm doing brings to the customer.

As I had mentioned, I think I highlighted more of this book than I didn't. It was full of great insights, and I've only named a few of them here. I highly recommend picking up a copy for yourself, or checking out the State of DevOps report from Puppet, and keeping it as a reference to better understand the organizations you work for and how they can be improved. I'd love to hear your insights in the comments below, too!
