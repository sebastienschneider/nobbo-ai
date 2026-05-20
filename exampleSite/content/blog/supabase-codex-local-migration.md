+++ 
title = "Supabase Codex local Migration" 
date = "2026-05-16" 
description = "Supabase Codex local Migration"
tags = [ 
"Supabase", "Codex", "Migration"
] 
+++
1. Initialiser le projet local
Dans ton dossier:
```bash
supabase init
supabase start
```
Ca démarre:
- Postgres local
- Auth
- Storage
- Studio
  Ensuite:
  ```bash
  supabase status
  ````
pour récupérer les URLs locales.

2. Lier le projet cloud
Récupère le ``project_ref`` dans l'URL Supabase:
```
https://supabase.com/dashboard/project/abcd1234
```
ici:
```
abcd1234
```
Puis:
```bash
supabase link --project-ref abcd1234
```
3. Pull du schéma cloud vers local
```bash
supabase db pull
```
- introspecte la DB cloud
- génère la migration SQL locale
- synchronise le schéma
Le fichier apparait dans
```
supabase/migrations/
```
4. Appliquer la migration localement
```
supabase db reset
```
ou
```
supabase migration up
```
5. Utiliser MCP avec Codex
Une fois le projet local prêt:
```
codex
```
puis
```
utilise Supabase MCP pour inspecter ma base locale
```
ou
```
Compare le schéma local avec les migrations
```
ou
```
Crée la SQL mogration pour une table profiles avec RLS
```
## Récupération des données
Utilise:
```
supabase db dump --data-only
```
ou dump complet
```
supabase db dump --file backup.sql
```
Puis restaure:
```
psql -f backup;sql
```
## Workflow complet
```
supabase init
supabase start

supabase login
supabase link --project-ref abcd1234

supabase db pull
supabase db reset

supabase db dump --data-only --file data.sql
psql postgresql://postgres:postgres@localhost:54322/postgres < data.sql
```
## Ce qui est récupéré automatiquement
Tu récupères surtout :
- tables
- vues
- fonctions SQL
- extensions
- triggers
- policies RLS
- types Postgres
