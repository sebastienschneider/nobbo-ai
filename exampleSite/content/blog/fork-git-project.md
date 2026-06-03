+++ 
title = "Fork git Project" 
date = "2026-05-22" 
description = "Fork git Project"
tags = [ 
"git"
] 
+++

Quand tu forks un projet GitHub, ton fork contient toutes les branches du dépôt au moment du fork.

Quelques nuances :
- Sur GitHub, le fork est une copie complète du dépôt, y compris les branches existantes.
- Lorsque tu clones ensuite ton fork en local, Git ne récupère généralement que la branche par défaut en checkout, mais les autres branches existent comme références distantes (origin/nom-branche).
- Tu peux voir toutes les branches distantes avec ``git branch -r``et créer une branche locale à partir d'une branche distante avec ``git checkout -b ma-branche origin/ma-branche``

**Exemple**

Si le dépôt d'origine possède :
```bash
main
develop
feature/login
release/v2
```

Après le fork :
```bash
ton-fork/main
ton-fork/develop
ton-fork/feature/login
ton-fork/release/v2
```
seront présents.

Attention aux nouvelles branches

Le fork n'est pas mis à jour automatiquement si le dépôt source crée de nouvelles branches après ton fork. 

Pour récupérer les évolutions du dépôt original, on ajoute généralement un remote upstream :
```bash
git remote add upstream https://github.com/OWNER/REPO.git
git fetch upstream
```

Tu verras alors également les nouvelles branches créées dans le dépôt d'origine :
```bash
git branch -r
```
et tu pourras les récupérer si besoin.
