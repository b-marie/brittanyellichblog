---
title: "React Hooks: An Overview and Recommendations for Trying Them Out"
date: 2022-01-30 T20:10:12-08:00
draft: true
tags: [tech, front end, react]
author: Brittany Ellich
---

## Overview

React hooks are a set of API functions that give developers the ability to access things like state in a react component without the need to use classes. The feature was released in react 16.8. They aren't a complete replacement for classes, nor are they at all necessary to use, but after doing some research I certainly believe that it is a feature that is worthwhile to learn if you do any regular work with react.

## Useful Hooks and What They Do

## How to Use with Redux

So, now that react hooks exist, do we even need redux? The short answer is yes. React hooks really aren't a replacement for redux or any other state management tool. Sure, they're very handy, but in the end you still need something more robust to manage the state in your react apps.

Where react hooks shine as a complete replacement for deterministic state management is for individual components that don't necessarily need to share state with other components. A great use case is managing state for a single component, while using redux for managing state across your application. For example, using useState to keep track of ephemeral form data. This frees you from adding that low-complexity and low-use-case state to redux, further contributing to abstraction and confusion within your application. If there's state that a component cares about but the overall application doesn't, use react hooks. Otherwise, use redux.

I wouldn't recommend rewriting all of your react applications to use react hooks (and neither would the Facebook team that created them). They will certainly make your applications much simpler and cleaner, but it's not necessarily the highest priority tech debt item. However, I personally plan to use react hooks for any future projects or components that I'm working on, in order to reduce the use of classes and make my JavaScript code more functional (like it arguably should be).
