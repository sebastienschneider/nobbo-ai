+++ 
title = "Supabase Codex MCP Multiple Local Projects" 
date = "2026-05-19" 
description = "Supabase Codex MCP Multiple Local Projects"
tags = [ 
"Supabase", "Codex",
] 
+++

C’est le setup normal : un dossier/repo local = un projet Supabase local = une remote ref propre.

Dans chaque repo :
```bash
cd mon-projet-a
npx supabase link --project-ref REF_REMOTE_A
```
Puis dans un autre :
```bash
cd mon-projet-b
npx supabase link --project-ref REF_REMOTE_B
```
La ref est stockée localement dans :
```bash
supabase/.temp/project-ref
```
Donc chaque dossier peut pointer vers une remote différente.

Tu peux vérifier :
```bash
cat supabase/.temp/project-ref
```
ou :
```bash
npx supabase status
```
Structure typique :
```bash
projet-a/
  supabase/
    config.toml
    migrations/
    .temp/project-ref  -> remote A

projet-b/
  supabase/
    config.toml
    migrations/
    .temp/project-ref  -> remote B
```
Important : ne partage pas **supabase/.temp** dans Git. Garde seulement :
```bash
supabase/config.toml
supabase/migrations/
supabase/seed.sql
```
Donc oui : tu peux avoir autant de projets locaux que tu veux, chacun lié à son propre projet Supabase remote.
```bash
url = "https://mcp.supabase.com/mcp?project_ref=other456"
```
Comme ça Codex utilise automatiquement le bon projet selon le dossier.
