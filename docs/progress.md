# Roadmap and progress

Work on the first unchecked item. Tick it (`[x]`) when it is done.

## Phase 0 – Foundations
- [x] Clickable prototype with fake data (`prototype/`)
- [x] Repository structure and rules
- [x] Confirm backend stack (decision 0001)
- [x] Choose login and database: Supabase (decision 0002)
- [ ] Architecture talk: frontend, backend, data model, offline sync, deployment
- [ ] Data model written in `architecture/data-model.md`

## Phase 1 – Teacher basics (offline)
- [ ] Set up the Expo app in `app/`
- [ ] Local SQLite storage
- [ ] Teacher: tick lessons done against the fiches de progression
- [ ] Teacher: enter class counts per séquence

## Phase 2 – Server and sync
- [ ] Set up the Rust backend in `backend/`
- [ ] Create the Supabase project; login for teachers and HOD
- [ ] Sync between app and server

## Phase 3 – HOD and reports
- [ ] HOD dashboard
- [ ] "Analyses et statistiques" tab
- [ ] Generated Rapport du Conseil d'Enseignement

## Phase 4 – Release
- [ ] Deploy backend with Docker on a VPS
- [ ] Android build with Expo EAS
