---
title: Interpreting the Brief and Defining My Initial Prototype Scope
date: 2026-03-27
author: Jesse Gao
summary: This post interprets the BlaBla brief and defines the initial functional direction for my A2 web app prototype.
tags:
  - project-brief
  - functional-requirements
  - scope
---

# Interpreting the Brief and Defining My Initial Prototype Scope

The BlaBla Corp brief asks us to design a tailored community hub, not just a normal information website. This distinction is important for my A2 prototype because a static website can present content, but it cannot properly support changing community information, user contribution, or personalised interaction. In the discovery stage, I therefore need to ask what the client actually values: not just pages, but a platform where information and experience are shared in a way that keeps a specific community returning.

My initial direction is an indie music community hub for people who are interested in underground or independent music. This community is more specific than “people who like music”. It includes users who want to discover lesser-known artists, share recommendations, discuss local gigs, and find music through trusted community knowledge rather than only through mainstream algorithmic platforms. Existing services such as Spotify, YouTube, Instagram, or TikTok already support music discovery, but they are usually designed around large-scale recommendation systems, popularity metrics, and short-form promotion. My prototype should explore a smaller and more community-centred experience.

The core problem I am defining at this stage is:

**Indie music listeners need a focused community space to discover, share, and discuss independent music because mainstream platforms often prioritise popularity, algorithmic recommendations, and passive consumption rather than community knowledge and meaningful discussion.**

From this problem, I can identify several initial functional requirements. Users should be able to browse a feed or list of music recommendations. They should be able to open a detail page for a specific post, including information such as artist name, genre, description, link, tags, and the person who shared it. Users should also be able to contribute their own recommendation or event post, and other users should be able to respond through lightweight comments or reactions. Search or filtering by genre, mood, location, or tag would also help users find relevant content more efficiently.

At the same time, I need to make clear scope decisions. The BlaBla platform already assumes user login and profiles, so I should not spend my main effort rebuilding authentication. I should also avoid trying to create a full music-streaming service, ticket-selling system, private messaging system, or complex recommendation algorithm. These features may sound attractive, but they would make the prototype too broad and technically unrealistic. A stronger MVP is to focus on the key community action: sharing and discovering useful music-related information.

The technical direction also needs to match the course stack. Mojo.js routes and controllers can handle user requests, SQLite can store posts, tags, comments, and reactions, and server-rendered templates can display dynamic content. TypeScript is useful because it makes the expected shape of data clearer, especially when handling form input or database results. From Week 5, I also need to think carefully about request methods: browsing and filtering should mainly use GET requests, while creating posts or comments should use POST requests because they change server-side data. HTMX could improve the experience by allowing comments, filters, or reactions to update part of the page without requiring a full reload.

For evaluation and responsibility, I will need to test whether the prototype is understandable, responsive on mobile and desktop, and accessible enough for users with different needs. I also need to handle user-generated content responsibly by validating and sanitising inputs, avoiding unnecessary personal data collection, and using the existing BlaBla session system rather than adding extra tracking. My next step is to turn this concept into a clearer user flow and decide which data objects are essential for the first build.