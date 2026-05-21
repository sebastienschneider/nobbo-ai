+++ 
title = "Supabase Codex local manual Migration" 
date = "2026-05-17" 
description = "Supabase Codex local manual Migration"
tags = [ 
"Supabase", "Codex", "MCP", "Migration"
] 
+++
**Étape 1 — Connecter MCP au projet local**

Supabase expose aussi un MCP local :
```bash
http://localhost:54321/mcp
```
Tu peux connecter Codex directement au local.

Dans :
```bash
~/.codex/config.toml
[mcp_servers.supabase_local]
url = "http://localhost:54321/mcp"

[features]
rmcp_client = true
```
Puis :
```bash
codex
```
Et dans Codex :
```bash
/mcp
```
**Étape 2 — Utiliser Codex comme auditeur de drift**

Le workflow le plus utile :
```bash
Compare mon projet local et mon projet cloud Supabase.
Détecte :
- policies manquantes
- fonctions absentes
- extensions différentes
- buckets storage manquants
- edge functions absentes
- secrets référencés mais non définis
```
Le MCP peut :
- lire le schéma
- inspecter les fonctions
- lire les logs
- inspecter les migrations
- générer du SQL
- Synchroniser les Edge Functions

Codex peut :
- lister les fonctions distantes
- récupérer leur contenu
- générer les dossiers locaux
- générer les commandes deploy

Exemple :
```bash
Utilise Supabase MCP pour :
- lister toutes les edge functions cloud
- créer leur structure locale
- générer les commandes de déploiement
```

Le MCP expose :
- list_edge_functions
- get_edge_function
- deploy_edge_function
- Synchroniser les secrets

Le MCP ne donne pas accès aux valeurs des secrets (heureusement).

Mais Codex peut détecter :
- quels secrets sont utilisés
- lesquels manquent
- lesquels doivent être créés

Exemple :
```bash
Analyse mes edge functions et détecte tous les secrets requis.
Génère ensuite les commandes supabase secrets set.
```

Puis Codex produit :
- supabase secrets set OPENAI_API_KEY=...
- supabase secrets set STRIPE_SECRET_KEY=...

Très utile pour éviter les oublis.

**3. Synchroniser le Storage**

Le MCP peut lister les buckets si la feature storage est activée.

Configurer :
```bash
[mcp_servers.supabase]
url = "https://mcp.supabase.com/mcp?features=storage,database"
```

Puis demander :
```bash
Liste les buckets storage et génère un script de synchronisation cloud vers local.
```
Codex peut alors générer :
- supabase storage ls avatars --linked --experimental
- supabase storage cp ...

ou un script Node.js utilisant :
- @supabase/storage-js
- Synchroniser Auth

Codex peut auditer :
- providers OAuth manquants
- redirect URLs
- templates email
- RLS liées à auth.users

Exemple :
```bash
Inspecte mon auth Supabase et détecte les différences entre local et cloud.
Générer automatiquement les types TS
```
Très utile après migration :

**4. Génère les types TypeScript à partir du schéma local.**

Le MCP possède :
- generate_typescript_types

Codex peut ensuite :
- écrire database.types.ts
- mettre à jour ton SDK
