+++ 
title = "Change git Remote Address" 
date = "2026-05-21" 
description = "Change git Remote Address"
tags = [ 
"git"
] 
+++

Tu peux modifier l'URL du remote existant avec :
```bash
git remote set-url origin <nouvelle-url>
```
Par exemple :
```bash
git remote set-url origin git@github.com:mon-compte/mon-projet.git
```
ou
```bash
git remote set-url origin https://github.com/mon-compte/mon-projet.git
```

Pour vérifier :
```bash
git remote -v
```
Tu verras quelque chose comme :
```bash
origin  git@github.com:mon-compte/mon-projet.git (fetch)
origin  git@github.com:mon-compte/mon-projet.git (push)
Cas fréquent : passer du dépôt original à ton fork
```

Supposons que ton dépôt local pointe vers :
```bash
origin -> git@github.com:organisation/projet.git
```
et que tu as créé un fork :
```bash
git@github.com:toi/projet.git
```
Tu peux :
```bash
git remote set-url origin git@github.com:toi/projet.git
```
Puis ajouter le dépôt original comme upstream :
```bash
git remote add upstream git@github.com:organisation/projet.git
```
Vérification :
```bash
git remote -v
```

Résultat :
```bash
origin    git@github.com:toi/projet.git (fetch)
origin    git@github.com:toi/projet.git (push)
upstream  git@github.com:organisation/projet.git (fetch)
upstream  git@github.com:organisation/projet.git (push)
```

C'est la configuration standard lorsqu'on travaille avec un fork GitHub.
