# Rules for working on Penka

Read this file before changing anything. It applies to people and to AI coding helpers.
Keep it short: if a rule is only about one folder, put it in that folder's `README.md`.

## 1. Before writing code

1. **Design first.** A new feature needs a short design note in `docs/` (copy `docs/templates/feature.md`). No note, no code. If the request is vague, stop and ask.
2. **Check the roadmap.** Open `docs/progress.md` and work on the next unchecked item only. Tick it when done.
3. **Big choices are written down.** A choice about stack, data or architecture gets a decision note in `docs/architecture/decisions/` (copy `docs/templates/decision.md`).
4. **Explain simply.** The project owner is learning this stack. Explain what you did and why in plain words, and avoid unexplained jargon.

## 2. Product rules (never break these)

- **No student names and no individual marks.** Teachers enter class counts per séquence only: number evaluated (girls / boys) and number with a mark ≥ 10 (girls / boys).
- **Subject scope is SVTEEHB only** for now. Do not generalise to other subjects without a decision note.
- **Offline first.** Every teacher action must work without a connection and sync later.
- **French interface.** All text shown to users is in French. Code, comments and commit messages are in English.

## 3. Design and wording rules

- Colours: deep navy `#172440` and white. Accent steel blue `#34548F`. Charts: boys `#3A5FA8`, girls ochre `#B8860B`, total grey `#A3ABBB`.
- **Never** bright blue, **never** pink, no background texture on the home page.
- **Never write "IA" or "l'IA"** in the interface. Write "Rédigé par le système" or "automatiquement".
- Dashboards stay light. Detailed charts go in the "Analyses et statistiques" tab.
- Penka has its own identity. Do not copy another product's look.
- Full details: `docs/design/ui-guidelines.md`.

## 4. How the code is organised

- `app/` talks to `backend/` only through the HTTP API. It never touches the database directly.
- Backend layers, in this order: **route → handler → service → repository → database**. Never skip a layer.
  Handlers stay thin (check input, call a service, return a response). SQL lives only in repositories.
- App: screens assemble components; data access goes through hooks; nothing in a screen calls the API directly.
- One file does one job. Split a file when it passes about 300 lines.

## 5. Safety

- Never commit passwords, keys or tokens. Use `.env` files (ignored by git); copy `.env.example`.
- Validate every input on the server, even if the app already checked it.
- The repository is **public**. Do not put the files from `reference/`, the prototype code, real school results or anyone's name on GitHub.

## 6. Git

- Branches: `feat/short-name`, `fix/short-name`, `docs/short-name`.
- Commits use Conventional Commits: `type(scope): what changed`, e.g. `feat(app): add séquence entry screen`.
  Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`.
- Small pull requests, one topic each, using the PR template.

## 7. Before saying "done"

- App: lint and typecheck pass.
- Backend: `cargo fmt`, `cargo clippy` and `cargo test` pass.
- `docs/progress.md` is updated.
