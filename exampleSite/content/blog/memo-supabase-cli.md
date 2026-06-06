+++ 
title = "Supabase CLI Memo" 
date = "2026-05-24" 
description = "Supabase CLI Memo"
tags = [ 
"Supabase"
] 
+++

Voici un mémo Supabase CLI de base.

### Aide / version
```bash
supabase --help
supabase --version
```

### Init local
```bash
supabase init
```

### Login / user connecté
```bash
supabase login
supabase logout
supabase projects list   # si ça marche, tu es bien authentifié
```

### Voir les projets remote disponibles
```bash
supabase projects list
```

#### Lier le dossier local à un projet remote
```bash
supabase link --project-ref <project-ref>
```

### Vérifier le remote lié
```bash
cat supabase/.temp/project-ref
supabase status
```

## Local Supabase :

### Lancer le serveur local
```bash
supabase start
```

### Voir si le serveur local tourne + URLs + clés locales
```bash
supabase status
```
### Stopper
```bash
supabase stop
```bash

### Stopper et reset les données locales
```bash
supabase stop --no-backup
```

## DB remote/local :

### Pull du schéma remote vers une migration locale
```bash
supabase db pull
```

### Push des migrations locales vers le remote
```bash
supabase db push
```

### Reset DB locale et rejouer les migrations
```bash
supabase db reset
```

### Créer une migration vide
```bash
supabase migration new <nom_migration>
```

### Voir les migrations appliquées
```bash
supabase migration list
```

## Edge Functions :

### Créer une function
```bash
supabase functions new <function-name>
```

### Servir/tester une function en local
```bash
supabase functions serve <function-name>
```

### Servir toutes les functions
```bash
supabase functions serve
```

### Déployer une function
```bash
supabase functions deploy <function-name>
```

### Déployer toutes les functions
```bash
supabase functions deploy
```

### Télécharger/récupérer une function remote
```bash
supabase functions download <function-name>
```

### Lister les functions remote
```bash
supabase functions list
```

## Secrets / env Edge Functions :

### Ajouter des secrets remote
```bash
supabase secrets set MY_SECRET=value
```

### Charger depuis un fichier .env
```bash
supabase secrets set --env-file .env
```

### Lister les secrets
```bash
supabase secrets list
```

### Supprimer un secret
```bash
supabase secrets unset MY_SECRET
```

## Types :

### Générer les types depuis le projet linked remote
```bash
supabase gen types typescript --linked > src/types/supabase.ts
```

### Depuis local
```bash
supabase gen types typescript --local > src/types/supabase.ts
```

## Workflow courant :

```bash
supabase login
supabase init
supabase projects list
supabase link --project-ref <project-ref>
supabase db pull
supabase start
supabase db reset
```
supabase functions serve
supabase db push
supabase functions deploy
