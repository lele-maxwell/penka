# backend/ – the Penka server

Rust. Proposed: Axum (web framework), SQLx (database access), PostgreSQL, JWT + argon2 for login, Docker on a VPS.
No code yet. This file describes how the folder will be organised.

## Planned folders

```
backend/
├── src/
│   ├── main.rs        starts the server
│   ├── config.rs      reads settings from environment variables
│   ├── error.rs       one error type for the whole server
│   ├── routes/        which URL goes to which handler
│   ├── handlers/      thin: check input, call a service, return a response
│   ├── services/      the real work (rates, coverage, report text)
│   ├── repositories/  all SQL lives here, nowhere else
│   ├── models/        data shapes (database rows, requests, responses)
│   └── auth/          login, passwords (argon2), tokens (JWT), roles
├── migrations/        numbered SQL files that build the database
└── tests/
```

## Rules for this folder

- Order of layers: route → handler → service → repository → database. Never skip one.
- Functions that can fail return a `Result`. No `unwrap()` outside tests.
- Error messages sent to users never show internal details.
- Settings come from environment variables only (see `.env.example`).
- Sync endpoints must accept the same change twice without creating duplicates.
- Before "done": `cargo fmt`, `cargo clippy` and `cargo test` pass.
