# Architecture overview

```
 Phone / browser                         Server (VPS, Docker)
┌─────────────────────┐   HTTPS + JSON   ┌──────────────────┐     ┌────────────┐
│ app/  (Expo)         │ ───────────────▶ │ backend/ (Rust)   │ ──▶ │ PostgreSQL │
│ local SQLite storage │ ◀─── sync ────── │ Axum + SQLx       │     └────────────┘
└─────────────────────┘                  └──────────────────┘
```

- The app saves everything locally first (SQLite), so it works offline.
- When online, the app syncs its changes with the server.
- The server is the shared source of truth for the whole department.
- Login uses JWT tokens; passwords are hashed with argon2.

Status: proposed, see `decisions/0001-stack.md`.
