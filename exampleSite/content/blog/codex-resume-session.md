+++ 
title = "Codex Resume Session" 
date = "2026-05-20" 
description = "Codex Resume Session"
tags = [ 
"Codex"
] 
+++

Si tu interromps une session Codex (Ctrl+C, fermeture terminal, crash), tu peux la reprendre :

**Reprendre la dernière session**
```bash
codex resume --last
```
ou
```bash
codex resume -l
```

**Choisir une session dans la liste**
```bash
codex resume
```
Ça ouvre un picker interactif avec les sessions récentes.

**Reprendre une session précise**

Si tu connais l’ID :
```bash
codex resume <session-id>
```

**Si tu changes de dossier**

Par défaut, Codex privilégie les sessions du répertoire courant. Pour voir toutes les sessions :
```bash
codex resume --all
```

**Où sont stockées les sessions**

En local :
```bash
~/.codex/sessions/
```
Typiquement :
```bash
~/.codex/sessions/2026/05/20/
```
Donc au pire :
```bash
ls ~/.codex/sessions
```
**Le plus propre**

Dans Codex, quitte avec :
```bash
/quit
```
ou
```bash
/exit
```
Ça ferme proprement la session interactive, qui reste ensuite reprenable via 
```bash
codex resume
```
ou 
```bash
codex resume --last
```
