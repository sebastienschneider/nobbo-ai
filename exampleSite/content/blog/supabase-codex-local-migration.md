+++ 
title = "Supabase Codex local Migration" 
date = "2026-05-15" 
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
