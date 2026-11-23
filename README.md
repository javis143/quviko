# QUVIKO

**Where Knowledge Meets Opportunity**  
Connect. Collaborate. Create.

QUVIKO is an early multidisciplinary community and collaboration platform prototype. It is designed to help people share knowledge, ask questions, discover collaborators, and explore projects and opportunities.

## Current status

This repository contains the front-end prototype in `index.html`. It is a static demonstration, not yet a production-ready community platform.

- Demo profile creation is browser-local only.
- Posts, likes, saved items, and responses use browser `localStorage` and are not shared between visitors.
- Authentication, shared database storage, moderation, and production security still need to be implemented.
- Sample member profiles, posts, and opportunities are illustrative.

## Run locally

Open `index.html` in a modern browser. No build step or external JavaScript library is required.

## Planned backend

Supabase is planned for authentication and shared data storage. Before enabling public member activity, configure Row Level Security policies and use only a publishable/anon key in browser code. Never expose a Supabase service-role or secret key in this repository.

## License

No license has been assigned yet. All rights are reserved by the repository owner unless a license is added.
