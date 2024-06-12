---
title: "How I Organize Work in Obsidian"
date: 2024-06-12 00:00:00-08:00
draft: false
tags: [organization, productivity]
author: Brittany Ellich
resources:
  - name: "featured-image"
    src: "obsidian.png"
---

Hello, my name is Brittany, and I have a problem. I am one of those weird people that is obsessed with "productivity hacks".

The biggest pitfall of being productivity-obsessed is the amount of time that I spend automating the work of being productive. I am constantly tweaking my workflows and setups as I learn new ways to make sure that things get done.

Using Obsidian is one of the things that has really unleashed my productivity obsession.

## How I use Obsidian

I roughly organize things in Obsidian using [the PARA model](https://fortelabs.com/blog/para/), or Projects, Areas, Research, and Archive. I really don't find much use for the Research section, as it tends to have a lot of overlap with Areas.

Projects for me include the things that I'm currently working on for work. These might be epics or initiatives that I'm involved in, or a subsection that is dedicated towards customer support issues that I have looked at.

Areas for me are topics that I'm interested in. Things like accessibility, azure, or distributed-systems. This is where I put my collection of notes and resources that I want to keep track of as I learn things in those areas. I also have an area folder called `backlog`, where I keep track of things like book, article, or video recommendations to work through.

## Calendar and Dataview

I use [the calendar plugin](https://github.com/liamcain/obsidian-calendar-plugin) to automatically generate daily and weekly pages from a template that I've created. The daily template roughly looks like this:

```md

## ToDos

- [ ] Meetings or things I need to do on a specific day

## Projects

\```dataviewjs
let curr = dv.current()
let today = curr.file.day.toISODate()

// PROJECT ITEMS ==============================
let projects = dv.pages('"projects"')
 .where(p => p && !p.file.path.includes("archive"))
 .file.tasks
 .where(t => t && (!t.completed || (t.completion && t.completion.toISODate() == today)))
 .sort(t => t.completed, 'asc');

if (projects.length) {
 dv.taskList(projects)
}
\```

## Areas

```dataviewjs
let curr = dv.current()
let today = curr.file.day.toISODate()

// PROJECT ITEMS ==============================
let areas = dv.pages('"areas"')
 .where(p => p && !p.file.path.includes("archive"))
 .where(p => p && !p.file.path.includes("backlog"))
 .file.tasks
 .where(t => t && (!t.completed || (t.completion && t.completion.toISODate() == today)))
 .sort(t => t.completed, 'asc');

if (areas.length) {
 dv.taskList(areas)
}
\```

## Backlog

\```dataviewjs
let curr = dv.current()
let today = curr.file.day.toISODate()

// PROJECT ITEMS ==============================
let areas = dv.pages('"areas/backlog"')
 .where(p => p && !p.file.path.includes("archive"))
 .file.tasks
 .where(t => t && (!t.completed || (t.completion && t.completion.toISODate() == today)))
 .sort(t => t.completed, 'asc');

if (areas.length) {
 dv.taskList(areas)
}
\```
```

The daily template has four sections: ToDos, Projects, Areas, and Backlog.

The ToDos section is where I keep track of things like meetings that I need to attend for the day or specific items that need to be done on a specific day. On Friday of each week I have a "Prep for next week" task where I generate all of the daily and weekly files for the next week and manually add meetings into the ToDos section.

The Projects, Areas, and Backlog sections are [dataviewjs scripts](https://blacksmithgu.github.io/obsidian-dataview/) that search through every file in the `projects`, `areas`, or `backlog` folder, respectively, and pulls every checkbox item that hasn't previously been completed into a tasklist. Since they are in a tasklist, dataview will add a date to an item when it is completed. This will make it so that an item that I complete on Tuesday won't show up again on Wednesday, even though the notes and everything related to that item will still remain in the file that the task lives in.

This roughly appears like the following each day:

```md

## ToDos

- [ ] 9 Standup

## Projects

Frontend Project Name
- [ ] Make a button clickable
 - [ ] Make the button work
 - [ ] Create PR
 - [ ] Post PR
 - [ ] Respond to PR comments
 - [ ] Queue
 - [ ] Merge

## Areas

Accessibility
- [ ] Read most recent Deque newsletter

## Backlog

Books
- [ ] Designing Data-Intensive Applications
- [ ] Radical Candor

```

For the weekly template I maintain a work log similar to the dataviewjs scripts in my daily template, but it keeps track of all of the checklist items completed for the week in either the Projects, Areas, or Backlog folders. This allows me to see everything that I worked on within a specific week in one view, and also allows me to archive my daily pages at the end of the week, as I tend to not review them again since my notes for each Project or Area are contained within their own pages.

My weekly template looks like the following:

```md

## Week at-a-glance

dataviewjs
let currentYear = new Date().getFullYear()
let curr = dv.current()
let week = parseInt(curr.file.name.replace(`${currentYear}-W`, ""))
var d = new Date("Jan 01, " + currentYear + " 01:00:00");
var w = d.getTime() + 604800000 * (week - 1);
var startOfWeek = new Date(w);
var endOfWeek = new Date(w + 518400000);

// PROJECT ITEMS ==============================
let projectTasks = dv.pages('"projects"')
 .file.tasks
 .where(t => t && (t.completed && (t.completion && new Date(t.completion) <= endOfWeek && new Date(t.completion) >= startOfWeek)))
 .sort(t => t.completed, 'asc')

if (projectTasks.length) {
 dv.taskList(projectTasks)
}

// AREA ITEMS ==============================
// My backlog folder is in the `areas` folder, so this pulls both area and backlog 
// tasks and aggregates them. I don't mind combining those in the weekly view but
// the backlog is long and I don't necessarily want to see all the open tasks 
// all the time in my daily view.
let areaTasks = dv.pages('"areas"')
 .file.tasks
 .where(t => t && (t.completed && (t.completion && new Date(t.completion) <= endOfWeek && new Date(t.completion) >= startOfWeek)))
 .sort(t => t.completed, 'asc')

if (areaTasks.length) {
 dv.taskList(areaTasks)
}
\```
```

Using the Calendar community plugin, I have these templates set for the daily/weekly templates in the plugin settings, which means that I can use the calendar in Obsidian to quickly create a new daily or weekly page, or navigate to the page if it already exists.

I have used this workflow for around a year now and it has been very helpful for me to manage All The Things that I need to keep track of. I would love to see how you use Obsidian and manage your daily work, too!
