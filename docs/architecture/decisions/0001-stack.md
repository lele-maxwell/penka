# 0001 – Technology stack

**Status:** accepted (login and database: see 0002)
**Date:** 2026-11-24

## Decision
- One repository with `app/` and `backend/`.
- App: React Native + Expo + TypeScript; web first, Android next; SQLite for offline storage.
- Backend: Rust (owner's choice): Axum, SQLx.
- Login, database and files: hosted Supabase (see 0002).
- Hosting: Rust API in Docker on a small server; Supabase hosted by Supabase. Mobile builds: Expo EAS.

## Why
- One codebase for web and phone.
- Rust gives a fast, safe server and is what the owner wants to learn.
- Teachers often have weak connections, so offline storage is required.

## Left out on purpose
Keycloak, Redis, Grafana and Terraform: too heavy for one school department.
