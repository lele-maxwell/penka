# Penka

Penka is a facilitator tool for SVTEEHB teachers and heads of department (HOD) in a Cameroonian secondary school.
Teachers record their progress through the national *fiches de progression* and enter **class counts** after each séquence.
The system computes success rates (girls / boys) and prepares the *Rapport du Conseil d'Enseignement*.

The interface is in French. It must work offline.

## What is in this repository

| Folder | What it holds | Status |
|---|---|---|
| `app/` | The application: Expo + React Native + TypeScript. Runs on the web now, Android later. | Empty, planned |
| `backend/` | The server: Rust (Axum + SQLx + PostgreSQL). | Empty, planned |
| `docs/` | Everything we decided: product, design rules, architecture, roadmap. **Start here.** | Started |
| `prototype/` | The clickable demo with fake data. Reference only, never extended. | Frozen |
| `reference/` | Official documents (programmes, fiches, CE report). Not stored on GitHub. | Local only |
| `scripts/` | Helper scripts. | Empty |

## Where to start reading

1. `docs/README.md` – the index of all documents.
2. `docs/progress.md` – what is done and what comes next.
3. `AGENTS.md` – the rules every contributor (human or AI helper) follows.

## Running things

There is no application code yet. When there is, each folder's `README.md` will say how to run it.
