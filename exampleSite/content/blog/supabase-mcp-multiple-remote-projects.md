+++ 
title = "Supabase Codex MCP Multiple Remote Projects" 
date = "2026-05-18" 
description = "Supabase Codex MCP Multiple Remote Projects"
tags = [ 
"Supabase", "Codex", "MCP"
] 
+++

Si tu veux plusieurs projets Supabase distants avec Codex + MCP, le plus propre est de déclarer un serveur MCP par projet, chacun scoppé avec project_ref.

Supabase supporte explicitement project_ref dans l’URL MCP pour limiter un serveur à un projet précis

Exemple **~/.codex/config.toml** :
```bash
[features]
rmcp_client = true

[mcp_servers.supabase_dev]
url = "https://mcp.supabase.com/mcp?project_ref=abcdev123&read_only=true"

[mcp_servers.supabase_staging]
url = "https://mcp.supabase.com/mcp?project_ref=xyzstage456"

[mcp_servers.supabase_prod]
url = "https://mcp.supabase.com/mcp?project_ref=prod789xxx&read_only=true"
```
Puis login :
```bash
codex mcp login supabase_dev
codex mcp login supabase_staging
codex mcp login supabase_prod
```
Ensuite dans Codex :
```bash
/mcp
```
Tu verras les serveurs disponibles.

Recommandation pratique

### Pour éviter une catastrophe :

dev → accès écriture
staging → éventuellement écriture
prod → read_only=true

Exemple prod :
```bash
[mcp_servers.supabase_prod]
url = "https://mcp.supabase.com/mcp?project_ref=prod789xxx&read_only=true&features=database,docs"
```
Si tu veux switcher par repo

Encore mieux : config locale par projet.

Dans ton repo A :
```bash
.codex/config.toml
[features]
rmcp_client = true

[mcp_servers.supabase]
url = "https://mcp.supabase.com/mcp?project_ref=abcdev123"
```
Dans ton repo B :
```bash
[features]
rmcp_client = true

[mcp_servers.supabase]
url = "https://mcp.supabase.com/mcp?project_ref=other456"
```
Comme ça Codex utilise automatiquement le bon projet selon le dossier.
