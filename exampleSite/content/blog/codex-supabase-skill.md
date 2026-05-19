+++ 
title = "Migrer Supabase en local avec Codex" 
date = "2026-05-19" 
description = "Migrer Supabase en local avec Codex"
tags = [ 
"Supabase", "Codex", "Migration"
] 
+++

# Méthode recommandée: Remote MCP

## 1. Installer Codex CLI
```bash
npm install -g @openai/codex
```
## 2. Ajouter le serveur MCP Supabase
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

