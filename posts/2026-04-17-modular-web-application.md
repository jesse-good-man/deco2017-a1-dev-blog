---
title: "Turning Pages into a Modular Web Application"
date: "2026-04-17"
author: "Jesse Gao"
description: "This post reflects on how modular design, reusable components, partial views, and MVC can make the prototype easier to maintain."
tags:
  - A1
  - modularity
  - reusable-components
  - partial-views
  - MVC
---

This week, my thinking shifted from “what pages should the prototype have?” to “how should the system be broken into reusable parts?” Earlier planning helped me understand the basic flow of the application, but Week 8 made me realise that a web application cannot be designed as a group of isolated pages. If every page is built separately, small changes can become painful later. A better approach is to identify what repeats, what changes, and which parts should become reusable components.

The main functional requirement I am focusing on is still the core community interaction: users need to browse shared content, open a detailed view, and perform actions such as submitting, filtering, or responding. These actions may look different depending on the final content type, but the structure is similar. For example, a content card, a detail section, a form, a response list, and a feedback message are all reusable patterns. This means I should not design each screen as a unique layout from scratch. I should design a small system of parts that can be reused across the prototype.

Week 8’s discussion of Bootstrap and Material Design helped me think about this trade-off. Bootstrap is useful because it provides ready-made components and speeds up prototyping, but it can also make a project look generic if used without enough adjustment. Material Design is more complete as a design system, but it may be too heavy for a small prototype because it includes detailed rules for colour, spacing, motion, typography, and component behaviour. For my prototype, I do not think the best decision is to copy either system completely. Instead, I want to borrow the idea behind them: consistent components need shared rules.

This affects my technical planning as well. In the required stack, the modular approach can be supported through layouts, partial views, MVC, and ES modules. A layout should contain the repeated page structure, such as the head, navigation, and footer. Partial views should handle repeated blocks such as cards, list items, forms, and feedback messages. This would make the interface easier to repair because changing one partial could update the same pattern everywhere. It also reduces the risk of slightly different versions of the same component appearing across pages.

I also started to understand MVC more clearly as a way to organise responsibility. The model should handle database-related logic, the view should handle what the user sees, and the controller should connect requests, data, and rendering. This matters because the prototype will likely include user input and database-driven content. If database queries, route logic, and HTML rendering are all mixed together, the project may still work at first, but it will be difficult to debug or extend. A modular structure gives the group a clearer way to divide tasks and review each other’s work.

There is still a trade-off. More modularity can make the project cleaner, but it can also feel slower at the beginning because I need to decide the structure before building everything quickly. However, this delay is useful. For a group project, a shared component structure can reduce duplicated work and make collaboration safer. It also connects to evaluation later: a consistent interface should be easier to test for usability, accessibility, and responsiveness.

My current decision is to treat modularity as a scope-control method, not just a coding style. The goal is not to build a huge design system, but to create enough reusable structure so that the prototype remains understandable, maintainable, and realistic within the A2 constraints.