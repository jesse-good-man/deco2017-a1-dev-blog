From a Music Website to Interactive Sound Rooms
2026-04-03

Gaolilong Gao

After the first stage of planning, I realised that our project should not simply be a “music website”. A normal website can display artists, playlists, events, or articles, but the BlaBla brief asks for a web application that supports community-specific interaction. This changed how I understood our concept. The important question is no longer only “what music content should we show?” but “what task does the user complete, and how does the system respond?”

Our current idea is an underground indie music community hub based around Sound Rooms. A Sound Room is a user-created space where members can share a track, describe its mood or background, and invite discussion from others. The value is not just the music itself, but the shared interpretation around it: why someone posted it, what feeling it creates, and how other community members respond. This makes the concept more suitable for BlaBla than a generic music forum, because it focuses on a specific community experience rather than copying standard social media features.

To clarify the scope, I started mapping the application flow. A traditional sitemap felt too limited because it mainly shows page hierarchy. For this project, the important part is not just where pages are located, but what users can do on them. My current structure is:

Home / Sound Room Feed
→ Sound Room Detail
→ Create Sound Room
→ Search or Filter Rooms
→ User Profile

Sound Room Detail
→ Listen to Track
→ Read Comments
→ Add Comment
→ Add Bullet Comment

This helped me separate essential functions from attractive but risky extras. The must-have flow is: users open the feed, browse existing Sound Rooms, enter one room, listen to the track, read the discussion, and add a response. A second essential flow is creating a new Sound Room with a title, track link or embedded media, description, and mood tags. Features such as real-time chat, complex recommendations, private messaging, or advanced audio editing are interesting, but they would expand the technical scope too much for the A2 prototype.

Thinking through the user flow also made me consider system responses more carefully. For example, when a user submits a comment, the system should not only “show text on the page”. It needs to check the input, save the comment with the current user identity, connect it to the correct Sound Room, and display the updated discussion clearly. This connects directly to the required stack: MojoJS can handle the route, SQLite can store rooms and comments, templates can render the page, and HTMX could support partial updates so the comment area refreshes without reloading the whole page.

The main trade-off at this stage is between atmosphere and feasibility. An indie music community should feel expressive and personal, but if we focus too early on visual style, the project may become a static gallery again. For this reason, I want to prioritise structure before surface design. The feed, room detail page, creation form, comments, and profile/history area need to work clearly before the interface becomes more visually ambitious.

For evaluation, I will need to test whether users understand what a Sound Room is without extra explanation, whether they can move from browsing to listening to commenting smoothly, and whether the interface remains usable on mobile. Accessibility also matters because music-based content should not rely only on audio. Titles, descriptions, tags, and readable discussion text need to carry meaning for users who cannot or do not want to listen immediately.

At this point, my clearest insight is that application flow is where the project becomes real. The Sound Room concept only works if the user journey is simple enough to understand, but specific enough to feel different from a standard music feed.

Tags: A1, application-flow, Sound-Rooms, functional-requirements, Week-7