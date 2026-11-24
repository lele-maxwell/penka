# Architecture overview

```mermaid
flowchart LR
    subgraph User["Phone or browser"]
        App["Penka app (Expo)<br/>local SQLite storage"]
    end
    subgraph Server["Our server (Docker)"]
        API["Rust API<br/>Axum + SQLx"]
    end
    subgraph Supa["Supabase (hosted)"]
        Auth["Auth<br/>login"]
        DB[("PostgreSQL")]
        Files["Storage<br/>reports"]
    end
    App -- "sign in only" --> Auth
    App <-- "HTTPS + JSON (sync)" --> API
    API --> DB
    API --> Files
    API -. "checks login token" .-> Auth
```

- The app saves everything locally first (SQLite), so it works offline.
- When online, the app syncs its changes with the server.
- The server is the shared source of truth for the whole department.
- The app signs in with Supabase Auth, then sends its token to the Rust API.
- The Rust API checks the token, reads the user's role and does all the school logic.
- PostgreSQL and file storage are hosted by Supabase.

See `decisions/0001-stack.md` and `decisions/0002-supabase.md`.
