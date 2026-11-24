# 0002 – Supabase for login, database and file storage

**Status:** accepted
**Date:** 2026-11-24

## Context
Penka needs user accounts with two roles (enseignant, HOD), a PostgreSQL database and a place for generated files (reports). The owner is learning the stack and wants deployment to stay light.

Options compared:
- **A. Supabase (hosted)** – database, login, roles and file storage managed for us.
- **B. Keycloak + PostgreSQL** – everything self-hosted; Keycloak is heavy (Java, about 1 GB of memory) and built for large organisations.
- **C. PostgreSQL + our own login in Rust** – cheapest, but we write login, password reset and backups ourselves.

## Decision
Use **hosted Supabase** (option A):
- **Database:** Supabase PostgreSQL. The Rust backend connects to it directly with SQLx.
- **Login:** Supabase Auth (email + password). The app signs in with the Supabase client and gets a token.
- **Roles:** a `profiles` table (one row per user: role `enseignant` or `hod`, school, classes). Rust reads the role from there.
- **Files:** Supabase Storage for generated reports and exports.

## How the pieces talk
- The app uses Supabase **only to sign in**. Everything else goes through the Rust API.
- The app sends the login token with each request. Rust checks it with Supabase's public keys, then loads the user's role.
- Rust uses the private service key (server only, never in the app) for database and storage.
- Row Level Security is switched on for every table, with no public access, as a safety net.

## Consequences
- We do not write password storage, password reset or backups ourselves.
- Free plan limits: about 500 MB database, 1 GB files, and the project **pauses after about a week without activity** (school holidays). Plan to move to the paid plan (about $25/month) before real use, or keep it active.
- Data is hosted outside Cameroon.
- Supabase is plain PostgreSQL underneath: moving later to our own PostgreSQL (option C) stays possible.
- Offline use is still our job (SQLite on the phone + sync); Supabase does not do it for us.
