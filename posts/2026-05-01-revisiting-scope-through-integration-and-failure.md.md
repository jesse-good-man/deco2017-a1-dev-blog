---
title: "Revisiting Scope Through Integration and Failure"
date: "2026-05-01"
author: "Jesse Gao"
summary: "This post revisits prototype scope by considering external API integration, graceful failure, caching, security, and whether extra features actually support the core user experience."
tags:
  - A1
  - integration
  - API
  - scope
  - responsible-design
---

After working through application flow, modular structure, and data requirements, I now feel that the prototype is becoming more concrete. Earlier in the project, I mainly thought about what the application should include: pages, cards, forms, responses, and database relationships. At this stage, the more important question is slightly different: which features are actually worth adding, and which ones might make the prototype harder to finish without improving the core experience?

The main functional requirement has not changed. The application should support a focused community workflow where users can browse shared content, open a detailed view, and respond through lightweight interaction. This means any new feature should be judged by whether it strengthens that workflow. If an external API provides useful extra context or helps users make a better decision, then it may be valuable. If it only makes the project look more advanced, then it is probably a distraction.
![API integration decision map](assets/images/API_Integration_Decision_Map.png)

*Figure 1. A decision map for judging whether an API feature should be included or left out of the A2 prototype.*

This changed how I understand integration. In Week 10, the API examples used weather and geocoding, but the more important lesson was not about weather itself. The important pattern was that a web application can request data from another system, receive structured JSON, process it on the server, and then render something useful for the user. That sounds powerful, but it also creates a new dependency. Unlike local database content, external API data is not fully under my control.

Because of that, I need to design for failure, not just success. An API request might timeout, return an error, reach a rate limit, or send back data in an unexpected structure. If the prototype depends too heavily on that API, then one external problem could break the user experience. A better decision is to make API integration optional and fail-safe. The core database-driven workflow should still work even if the external feature cannot load.

This also affects technical planning. If I add an API feature, the route should use clear error handling, such as `try/catch`, status checks, and a fallback message. The user should not see a broken page or a confusing blank area. Instead, the interface should explain that the extra information is unavailable while keeping the main content usable. This supports usability because the system still gives feedback, even when something goes wrong.
![Graceful failure flow](assets/images/graceful-failure-flow-diagram.png.png)

*Figure 2. A graceful failure flow showing how the prototype can handle external API problems without breaking the core user experience.*

Caching is another important decision. If the application requests the same external data every time a user repeats an action, it may become slower and less responsible. A simple cache with a time limit can reduce repeated API calls, improve response speed, and lower the risk of hitting API limits. This connects directly to the brief’s performance expectations because the prototype should not become slower just because I added one “interesting” feature.

Security also matters here. Some APIs require keys, and these should not be written directly into the code or committed to GitHub. They should be stored in a configuration file such as `config.yml`, which is ignored by Git. This is not just a technical detail. It is part of responsible implementation because leaking keys would make the project unsafe and difficult to maintain.

My current decision is to treat integration as a possible value-adding layer, not the foundation of the prototype. The first priority is still the core application: persistent data, clear interaction, and a usable flow. If there is enough time, an API feature can be added only if it supports the user task and can fail gracefully.

For evaluation later, I would test whether the feature genuinely improves the experience. I would check loading speed, observe whether users understand the fallback state, and confirm that the application still works when the API returns no result. This post therefore revisits my earlier assumption that more features automatically make the prototype stronger. At this stage, a stronger prototype is not the one with the most functions, but the one where every function has a clear reason to exist.