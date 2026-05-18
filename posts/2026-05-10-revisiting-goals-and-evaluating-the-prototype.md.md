---
title: "Revisiting Goals and Evaluating the Prototype"
date: "2026-05-10"
author: "Jesse Gao"
summary: "This final post reflects on integration, testing, accessibility, and how evaluation helps check whether the prototype actually meets its functional requirements."
tags:
  - A1
  - testing
  - integration
  - accessibility
  - evaluation
---

At this stage, my thinking has moved from “can I build this feature?” to “how do I know this feature actually works for users?” Earlier posts focused on interpreting the brief, defining the core workflow, planning modular structure, designing data, and considering API or external integration. Now, as the A1 blog reaches its final post, the main issue is integration and evaluation. A prototype can look finished on the surface, but still fail if the core task is confusing, slow, inaccessible, or technically unreliable.

The functional requirement I want to check is still the same core community workflow: a user should be able to browse shared content, open a detailed view, and respond or interact in a lightweight way. This requirement matters because it is the basic loop that makes the application more than a static website. If users cannot understand where to go, if the detail page does not show the right connected information, or if submitting a response gives no clear feedback, then extra features will not save the prototype.

Week 11’s focus on the fidelity ladder helped me think more carefully about testing. I do not need the most complex test for every question. For example, if I want to know whether a user understands the page structure, a quick paper test or clickable static stub may be enough. If I want to know whether a button sends the correct request and updates the right part of the interface, then I need a higher-fidelity test. If I want to check whether a real route, template, and database query work together, then Test::Mojo or another integration test becomes more useful.

This changes how I define “done.” Earlier, I might have thought a feature was done when it appeared on the page. Now I think a feature should have a clearer user story and observable acceptance criteria. For example, instead of writing “make response feature,” a better definition is: as a logged-in community member, I want to submit a short response on a content detail page so that my contribution appears in the correct discussion area. The acceptance criteria could be that the form has a clear label, invalid input gives a readable error, and a successful response appears under the correct content item without confusing the user.

This also connects to technical decisions. Since the prototype uses MojoJS, SQLite, and HTMX, I need to test not only isolated pages but the relationship between routes, database data, templates, and partial updates. HTMX can improve the experience by updating only part of a page, but it also creates a responsibility: the replaced fragment must still be accessible, understandable, and visually consistent. SQLite supports persistent content, but the data model needs to remain clean enough for reliable queries. Integration is where earlier planning decisions either become useful or reveal problems.

Accessibility is another part of evaluation, not a final decoration. The brief requires AA accessibility, so I should check the interface through both automated and manual methods. Lighthouse, axe, or WAVE can help find obvious problems, but they cannot fully judge whether the interaction makes sense. I also need to test keyboard navigation, visible focus states, form labels, heading order, colour contrast, and whether screen reader users can understand the content and feedback messages. The POUR principles are useful here because they turn accessibility into practical questions: can users perceive it, operate it, understand it, and rely on it across different technologies?

There are also responsibilities around data. If users create content or responses, the prototype should avoid collecting unnecessary information and should handle user input carefully. Even in a student prototype, it is important to show awareness of privacy, data minimisation, and safe error handling. A system that stores too much, exposes too much, or fails unclearly would not be responsible just because it technically runs.

My main conclusion from this final stage is that evaluation is not separate from design. Testing helps reveal whether my functional requirements were realistic, whether my technical choices supported them, and whether my assumptions were correct. The goal for A2 should not be to add more and more features. The better goal is to make the core workflow understandable, testable, accessible, and stable enough to show the intended community experience.
![Final evaluation plan](assets/images/final_evaluation_plan_.png)

*Figure 1. A focused evaluation plan for checking the core workflow through usability, technical reliability, and accessibility tests.*