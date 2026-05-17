---
title: From a Music Website to Interactive Sound Rooms
date: 2026-04-03
author: Jesse Gao
summary: This post maps the application flow of the Sound Room prototype and explains how user actions, page structure, and technical constraints shape the project scope.
tags:
  - A1
  - application-flow
  - Sound-Rooms
  - functional-requirements
  - Week-7
---

# From a Music Website to Interactive Sound Rooms

After the first stage of planning, I realised that our project should not simply be a “music website”. A normal website can display artists, playlists, events, or articles, but the BlaBla brief asks for a web application that supports community-specific interaction. This changed how I understood our concept. The important question is no longer only “what music content should we show?” but “what task does the user complete, and how does the system respond?”

Our current idea is an interactive Sound Room feature for an indie music community hub. A Sound Room is a user-created space where members can share a track, describe its mood or background, and invite discussion from others. The value is not just the music itself, but the shared interpretation around it: why someone posted it, what feeling it creates, and how other community members respond. This makes the concept more suitable for BlaBla than a generic music forum, because it focuses on a specific community experience rather than copying standard social media features.

To clarify the scope, I started mapping the application flow.![Sound Room application flow diagram](/deco2017-a1-dev-blog/assets/sound-room-flow.png) A traditional sitemap felt too limited because it mainly shows page hierarchy. For this project, the important part is not just where pages are located, but what users can do on them. My current structure is:

Home / Sound Room Feed → Sound Room Detail → Create Sound Room → Search or Filter Rooms → User Profile

Sound Room Detail → Listen to Track → Read Comments → Add Comment → Add Bullet Comment

This helped me separate essential functions from attractive but risky extras. The must-have flow is: users open the feed, browse existing Sound Rooms, enter one room, listen to the track, read the discussion, and add a response. A second essential flow is creating a new Sound Room with a title, track link or embedded media, description, and mood tags. Features such as real-time chat, complex recommendations, private messaging, or advanced audio editing are interesting, but they would add too much technical scope for the A2 prototype.

Week 7’s discussion of user flow diagrams and wireflows was useful here. A simple sitemap can show that the feed connects to the detail page, but a user flow shows the actual decision points: does the user want to browse, create, search, or interact? A wireflow would be even more useful later because some interactions may happen without changing the whole page. For example, adding a comment or bullet comment could update only part of the Sound Room Detail page instead of reloading everything.

This also connects directly to the required technical stack. MojoJS can handle routes such as the feed page, room detail page, and create-room form. SQLite can store rooms, users, tags, and comments. HTMX can support smaller interactive updates, such as submitting a comment and replacing only the comment section. This means the flow is not just a visual planning exercise; it also helps me understand which routes, templates, and database relationships the prototype will need.

There are still important constraints. Since BlaBla already handles login, I should not rebuild authentication. The prototype also needs to remain responsive, accessible, and realistic within the course timeline. For accessibility, the Sound Room pages need clear form labels, keyboard-accessible buttons, readable contrast, and meaningful text alternatives for embedded content. For evaluation, I can later test whether users understand how to enter a room, create a room, and post a response without extra explanation.

At this stage, the biggest design decision is to prioritise a small but complete interaction loop over a large collection of unfinished features. If users can smoothly discover a Sound Room, understand its context, listen, and respond, then the prototype already demonstrates the core value of the community hub.