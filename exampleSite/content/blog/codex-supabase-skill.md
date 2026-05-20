+++ 
title = "Codex Supabase Skill" 
date = "2026-05-19" 
description = "Codex Supabase Skill"
tags = [ 
"Supabase", "Codex", "Skill"
] 
+++

### Méthode recommandée: Remote MCP

1. Installer Codex CLI
```bash
npm install -g @openai/codex
```

2. Ajouter le serveur MCP Supabase
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

3. Activer le support Remote MCP. Toujours dans ```~/.codex/config.toml```:
```toml
[features]
rmcp_client = true
```

4. S'identifier. Pour cela, on lance:
```bash
codex mcp login supabase
```
Un navigateur s'ouvre pour se connecter à Codex. Supabase utilise maintenant OAuth, donc plus besoin de PAT

5. On vérifie que ça marche. Pour cela, on lance Codex:
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
## Version sécurisée (read-only)
Très conseillé au début:
```toml
[mcp_servers.supabase]
url = "https://mcp.supabase.com/mcp?read_only=true"
```
Ou scoped à un projet:
```toml
[mcp_servers.supabase]
url = "https://mcp.supabase.com/mcp?project_ref=TON_PROJECT_REF&read_only=true"
```
## Mode local (stdio)
Utile pour:
- CI/CD
- token PAT
- offline-ish
Exemple:
```toml
[mcp_servers.supabase]
command = "npx"
args = ["-y", "@supabase/mcp-server-supabase@latest", "--project-ref=abc123"]

env = { SUPABASE_ACCESS_TOKEN = "sbp_xxx" }
```
## Où trouver project_ref
Dans l’URL Supabase : ``https://abcdefgh.supabase.co``

``abcdefgh`` = project_ref
