+++ 
title = "Change git Remote Repository" 
date = "2026-05-23" 
description = "Change git Remote Repository"
tags = [ 
"git"
] 
+++

**1. Renommer le dépôt GitHub**

Sur GitHub :
- Ouvre ton dépôt.
-Va dans Settings.
- Dans Repository name, change le nom.
- Clique sur Rename.

GitHub redirigera automatiquement l'ancienne URL vers la nouvelle.

Par exemple :
```bash
https://github.com/moncompte/ancien-projet
```
devient :
```bash
https://github.com/moncompte/nouveau-projet
```

**2. Mettre à jour le remote Git local**

Dans ton projet local, vérifie l'URL actuelle :
```bash
git remote -v
```
Puis remplace-la :
```bash
git remote set-url origin https://github.com/moncompte/nouveau-projet.git
```

Vérifie :
```bash
git remote -v
```

**3. Renommer le dossier local (facultatif)**

Depuis le dossier parent :
```
mv ancien-projet nouveau-projet
```
Puis :
```bash
cd nouveau-projet
```
