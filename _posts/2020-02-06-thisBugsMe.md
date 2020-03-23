---
layout: post
title:  "This Bugs Me"
date:   2020-02-06 17:47:39 -0500
categories: blogPost
permalink: /:categories/:year/:month/:day
---

Report on TOS 6.4, 6.5, 6.6, 6.7
This is not the oldest bug but this is the one we are working on with our project. The issue we have chosen is "Issue #2168" *memory leak?*. This is a major issue that was brought up by a developer. What is happening in the issue is that when there is a loop or multiple threads created Sonic Pi crashes because of a stack overflow. This stack overflow is caused by the memory not being garbage collected or the memory is constantly allocated without being deallocated when the program needs memory.
The priority was to find the leak so that low memory systems like the Raspberry Pi can still be used.

### Edit 03/10/2020
The creator of the project reported that he fixed the issue. There were three leaks that he found. Two of the issues are caused by tight looping a function called in_thread, which creates threads inside a function allocating its own memory. Other causes of the leaks were due to dependency issues. 
