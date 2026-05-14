---
title: Interpreting the Brief and Defining My Initial Web App Direction
date: 2026-05-14
author: Jesse Gao
summary: This post interprets the BlaBla community hub brief and defines the initial functional direction for my A2 web app prototype.
tags:
  - project-brief
  - functional-requirements
  - scope
---

# Interpreting the Brief and Defining My Initial Web App Direction

The BlaBla Corp brief asks us to design a tailored community hub where members with a common interest can share information and experience. My first design decision is to avoid treating this as a normal information website. A static website could describe a community, but it would not fully support the kind of changing, user-specific information that a community hub needs. For A2, I want to prototype a feature that helps a specific community make better decisions through shared, useful information.

My initial concept is a **BlaBla Campus Food Decision Hub** for University of Sydney students who need to choose food quickly between classes. The community is not simply “people who like food”; it is students who face a repeated decision-making problem on campus. They often have limited time, limited budget, and incomplete information about queues, distance, dietary options, or whether a place is actually worth choosing at that moment. Existing tools such as Google Maps or social media posts can provide general information, but they are not designed around the campus-specific context of fast student food decisions.

The key problem statement for my prototype is:

**USYD students need a quick and campus-specific way to choose food between classes because general platforms do not provide decision-ready information such as queue level, walking distance, price confidence, and student tips in one place.**

This problem suggests that the prototype should be a web application rather than a static page. The system needs to handle user input, update information over time, and organise data in ways that support decision-making. For example, students may need to filter food options by budget, distance, queue level, or dietary requirement. They may also benefit from short peer-submitted tips, such as whether a place is usually crowded or good for a quick meal. These interactions require dynamic content and persistent data rather than fixed text.

At this stage, I am identifying the core functional requirements as:

1. Students can browse a list of campus food options.
2. Students can filter options by practical decision factors such as price, distance, dietary needs, or queue level.
3. Students can open a detail view for a specific food option.
4. Students can contribute a short tip or update about a place.
5. The application can store and display updated community information.

I also need to make clear scope decisions. The BlaBla brief explains that core platform services such as login and user profiles are already handled by BlaBla, so I should not spend my prototype effort rebuilding sign-up or authentication. Similarly, I should avoid broad social media features such as private messaging, image feeds, or complex recommendation algorithms. These might be useful in a full product, but they would distract from the core value of the prototype.

The main trade-off is between usefulness and feasibility. A complete campus food platform could include live menus, payment integration, maps, rewards, and advanced personalisation. However, this would be too ambitious for the current prototype. A more realistic MVP is to focus on the decision moment: helping a student quickly compare food options using a small number of meaningful criteria.

My next step is to translate this concept into a clearer user flow and a more detailed set of functional requirements. I need to decide what the user sees first, what actions they can take, what information needs to be stored, and how each feature connects to the technical stack required by the BlaBla template.