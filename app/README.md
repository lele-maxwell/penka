# app/ – the Penka application

Expo + React Native + TypeScript. Runs on the web now; Android builds later through Expo EAS.
No code yet. This file describes how the folder will be organised.

## Planned folders

```
app/
├── src/
│   ├── app/          screens and navigation (Expo Router: one file = one screen)
│   ├── components/   reusable pieces of interface (buttons, cards, charts)
│   ├── features/     one folder per feature (progression, séquences, rapport, analyses)
│   ├── hooks/        data access used by screens
│   ├── api/          calls to the backend
│   ├── db/           local SQLite storage for offline use
│   ├── sync/         sends local changes to the server and fetches updates
│   ├── theme/        colours, fonts, spacing (see docs/design/ui-guidelines.md)
│   └── i18n/         French texts
├── assets/           icons and images
└── tests/
```

## Rules for this folder

- Install packages with `npx expo install <package>`, not `npm install <package>`.
- Expo changes often: check the docs for the Expo version in `package.json` before using an API.
- Never edit `ios/` or `android/` by hand; they are generated.
- Screens never call the API directly: screen → hook → `api/` or `db/`.
- Every teacher action is saved to SQLite first, then synced.
- Before "done": `npx expo lint` and `npx tsc --noEmit` pass.
