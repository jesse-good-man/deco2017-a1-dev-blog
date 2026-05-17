---
title: Turning Pages into a Modular Web Application
date: 2026-04-17
author: Jesse Gao
tags:
  - A1
  - modularity
  - reusable-components
  - partial-views
  - MVC
description: This post discusses how modular design helps turn separate prototype pages into a maintainable web application structure.
---

After mapping the main flow of the prototype, I realised that the next challenge is not simply adding more pages or making the interface look more complete. The more important question is how the application should be structured so that it can actually be built, tested, changed, and maintained by a group. A web application is not only a collection of screens. It is a system made from repeated interface patterns, data requests, user actions, and server responses.

This week’s focus on modular design helped me rethink the prototype from individual pages into reusable parts. At first, I was treating each page as a separate design problem: one page for browsing, one page for viewing details, one page for submitting content, and so on. This felt simple, but it would probably create duplicated code very quickly. For example, navigation, cards, buttons, forms, feedback messages, and content previews may appear in multiple places. If each page is built separately, changing one small design rule later could mean editing the same thing in many files. That increases the chance of inconsistency and bugs.

My current decision is to treat repeated interface elements as reusable components rather than one-off page sections. The main candidates are a shared navigation area, repeated content cards, form blocks, action buttons, and small status or error messages. This connects directly to the functional requirements because users need to browse, open, create, and respond to content smoothly. If the same type of content card appears in different contexts, it should behave consistently, otherwise users may not understand whether they are looking at the same kind of object.

This also affects the technical structure. Instead of building every screen as a complete independent page, I should use layout and partial views where appropriate. The layout can hold the repeated page skeleton, such as the head, navigation, and general page structure. Partial views can hold smaller repeated blocks, such as a content card or comment item. This is useful because the required stack already supports server-rendered templates, and HTMX can later update smaller parts of the page without forcing a full reload. In that sense, modularity is not separate from interaction design. It prepares the interface for partial updates.

However, modularity also has trade-offs. If I break the application into too many tiny files too early, the project may become harder to understand, especially for a small prototype and a team still learning the stack. A component system only helps if the parts are genuinely repeated or likely to change. For this reason, I should not modularise everything immediately. My current rule is simple: if a section repeats across pages or handles a clear reusable function, it can become a partial. If it only appears once and is still changing, it can stay inside the main view for now.

For group work, this structure also reduces collaboration risk. Different members can work on separate parts without constantly editing the same file. Clearer separation between Model, View, and Controller is useful here: the Model handles database logic, the View handles what users see, and the Controller connects requests, data, and rendering. This gives the project a more understandable architecture and makes later debugging easier.

To evaluate whether this decision works, I will check three things during development: whether repeated interface elements remain visually consistent, whether changes can be made without editing too many files, and whether the core user flow still feels clear after the interface is split into reusable parts. The goal is not to create the most complex architecture, but to make a small prototype that can grow without becoming messy.