> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.12

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_12.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.12
- **Chat** (demande du propriétaire) : la zone de saisie reste visible en bas ; seul le fil des messages défile et il suit tout seul les nouveaux messages et les jetons reçus (sauf si vous êtes remonté lire plus haut ; envoyer un message ramène en bas). Prouvé en fenêtre réelle (`ui-chat-modes`).
- **Auto-développement, durci par 14 observations réelles** : contexte réel de 12 288 jetons avec la carte graphique (au lieu de 8 192), réserve de réponse de 3 000 jetons (plus de fichier proposé coupé), appels d'outil abrégés dans la fenêtre, retours immédiats au modèle quand il invente une fonction absente du module, écrit un test pour le mauvais cadre (`vitest` vs `node:test`) ou supprime une ligne portant une décision du propriétaire (refusé), lecture tolérante des arguments mal formés, 7 outils seulement déclarés dans une copie de travail. **Résultat honnête** : même ainsi, le modèle Qwen3.5 9B n'a terminé aucune des tâches de test confiées (voir `LIMITES_V1_3_12.md`).
- **Signature sans SimplySign Desktop** : `ssign` (configuré par le propriétaire, graine chiffrée par Windows) signe les builds ; cet installateur hors-ligne est le premier signé ainsi. Repli signtool conservé.
- **Reste de la V1.3.11** : reprise de projet dans `.structurearc/`, fenêtre d'un petit modèle mieux gérée, lecture par morceaux.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.12_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.12_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_12.md` / `LIMITES_V1_3_12.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
