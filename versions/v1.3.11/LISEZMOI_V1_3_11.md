> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.11

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_11.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.11
- **Reprise de projet prouvée en fenêtre réelle** : nouveau scénario `ui-resume` (15/15) — rouvrir un dossier qui contient déjà `.structurearc/` restaure les conversations et la définition du projet, jamais les autorisations ; chaque échange écrit `chats/<id>.json`, `project.json` et `RESUME.md` ; retrait puis réouverture retrouvent tout sans doublon.
- **L'IA tient mieux dans la fenêtre d'un petit modèle** : les outils déclarés et la réserve de réponse sont déduits du budget de l'historique ; en cas de dépassement de la fenêtre, l'historique est abrégé et l'appel repris (2 fois au plus) au lieu d'un tour perdu ; dans une copie d'auto-amélioration, seuls 7 outils sont déclarés (lire, lister, proposer, commande, indexer, définir, demander une autorisation).
- **Moins de boucles de lecture** : au plus 3 lectures paginées du même fichier entre deux actions ; le début du fichier « prochaines étapes » (`NEXT_STEPS.md`, `TODO.md`, `ROADMAP.md`) est injecté dans le contexte (900 caractères) pour donner la première tâche sans relire un gros document.
- **Appels d'outils mieux tolérés** : un appel écrit en XML par le modèle (`<tool_call><function=files_read>…`) est exécuté s'il est exactement cela ; des arguments d'outil non JSON refusés par le serveur sont renvoyés au modèle pour qu'il recommence (2 fois au plus).
- **Auto-développement : résultat honnête** : six observations libres cette nuit (Qwen3.5 4B, fenêtre 8192) : aucune n'a terminé une tâche ; la meilleure a écrit un fichier de test faux. Le logiciel ne se développe PAS encore seul avec ce modèle. Voir `LIMITES_V1_3_11.md`.
- **Reste de la V1.3.10** : GPU jusqu'à 100 % avec filet de température, tous les fichiers Markdown du projet dans le contexte, lecture par morceaux.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.11_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.11_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_11.md` / `LIMITES_V1_3_11.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
