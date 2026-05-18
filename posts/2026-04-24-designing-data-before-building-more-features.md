---
title: "Turning Interface Ideas into Data Requirements"
date: "2026-04-24"
author: "Jesse Gao"
summary: "This post reflects on how data design helped me connect functional requirements, interface structure, database relationships, and realistic prototype scope."
tags:
  - A1
  - data-design
  - functional-requirements
  - ERD
  - SQLite
---

After thinking about application flow and modular structure, I realised that the next problem is not only how the prototype should look, but what information it needs to remember. A web application is different from a static website because the interface should respond to user actions and show content that comes from somewhere. This means the data structure is not just a technical detail. It is part of deciding whether the functional requirements are actually realistic.

The main requirement I am focusing on is the core community workflow: users should be able to browse shared content, open a detailed view, and respond through lightweight interaction. On the screen, this may look like a few simple cards, buttons, forms, and response lists. However, each visible element depends on data. A card may need a title, author, category, short description, date, and link to a detail page. A response area needs the response text, the person who wrote it, the time it was created, and the content item it belongs to. So the interface is not just a layout; it is a view of stored information.
![Interface to data requirements map](assets/images/data_requirements_map.png)

*Figure 1. Mapping visible interface elements to the data needed behind them.*

This is where the Week 9 work on data design helped me rethink the prototype. Earlier, I could imagine the application as a set of pages and reusable partial views. Now I need to ask what data sits behind those views. If I put everything into one large table, it might seem easier at the beginning, but it would quickly become hard to maintain. User information, shared content, responses, and categories have different purposes, so they should not all be treated as the same kind of data.

The relationship between data also affects the scope of the project. Some relationships are straightforward: one user can create many content items, and one content item can receive many responses. These are essential because they directly support the basic community experience. Other relationships are more complex. For example, categories or tags may become a many-to-many relationship, because one content item can have several tags, and one tag can belong to many content items. Storing several tags as one comma-separated text value would be quicker, but it would make filtering and querying less reliable later. A junction table is more difficult to understand at first, but it supports the functional requirement more properly.
![Core data relationship diagram](assets/images/core_data_relationship.png)

*Figure 2. A simplified ERD showing users, content items, responses, tags, and the junction table between content and tags.*

This also connects to technical decisions. Since the prototype uses SQLite, the database should be designed in a way that can support clear queries. If the detail page needs to show one content item together with its creator and responses, then the system may need to query more than one table. If users need to browse by category, the category data must be stored in a searchable structure rather than only written into the HTML. In this sense, joins are not just a database exercise. They are what allow the interface to show connected information from different parts of the system.

There is an important trade-off here. A more structured data model can make the prototype cleaner and more flexible, but too many tables and relationships could make the project harder to finish. A simpler model would be faster to build, but it might weaken the application if it cannot properly support browsing, filtering, or responses. My current decision is to design only for the core workflow first, then treat extra features as optional unless they clearly support the main user task.

This changes how I think about the task list as well. Instead of writing broad tasks like “build homepage” or “make detail page,” the work needs to include defining the data each page needs, creating tables, checking relationships, and testing whether the page can display real database results. This makes the prototype feel less like a static mock-up and more like an application with structure behind it.

For evaluation later, this data structure will also matter. If the database is too messy, the application may become slower, harder to debug, and less reliable for users. If user-generated content is stored, I also need to consider responsible handling of information, including not collecting unnecessary data and making sure user input is treated carefully. At this stage, my main insight is that good functional requirements must be supported by good data decisions. Otherwise, the interface may look complete, but the system behind it will not be strong enough.