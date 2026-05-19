+++ 
title = "Migrer Supabase en local avec Codex" 
date = "2026-05-19" 
description = "Méthode recommandée: Remote MCP"
tags = [ 
"Supabase", "Codex", "Migration"
] 
+++

### Méthode recommandée: Remote MCP

Installer Codex CLI
```bash
npm install -g @openai/codex
```

Ajouter le serveur MCP Supabase
```bash
codex mcp add supabase --url https://mcp.supabase.com/mcp
```
Ou manuellement dans:
```bash
~/.codex/config.toml
```
avec
```toml
[mcp.servers.supabase]
url = "https://mcp.supabase.com/mcp
```

Toujours dans ```~/.codex/config.toml```:
```toml
[features]
rmcp_client = true
```

Pour s'authentifier, on lance:
```bash
codex mcp login supabase
```

On vérifie que ça marche en lançant codex:
```bash
codex
```
puis dans le chat Codex:
```bash
/mcp
```
ou directement:
```bash
Liste des tables de ma base Supabase avec MCP
```
