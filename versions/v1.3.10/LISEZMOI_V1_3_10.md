> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.10

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_10.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.10
- **Carte graphique jusqu'à 100 %** (décision du propriétaire) : la limite de charge GPU se règle de 50 à 100 % (défaut **100 %**). À 100 %, la charge n'interrompt plus la génération ; le filet de sécurité devient la **température** de la carte (arrêt préventif vers 89 °C soutenus, dépassement au-delà de 95 °C, lue par `nvidia-smi`). Le processeur et la mémoire restent plafonnés à **80 %**, sans exception.
- **Reprise de projet** : le dossier `.structurearc/` du projet garde la définition du projet, chaque conversation (`chats/`, secrets masqués) et un résumé `RESUME.md`. En rouvrant le dossier (autre machine, réinstallation), les conversations et la définition sont retrouvées. **Les autorisations ne sont jamais restaurées.**
- **Tous les fichiers Markdown du projet** (racine et sous-dossiers, y compris `.claude`, `.codex`, `.cursor`, `.gemini`, `.github`, `.agents`) sont inventoriés dans le contexte de l'IA ; `CLAUDE.md`, `AGENTS.md` et la mémoire du projet sont prioritaires. Sans Markdown, `project_index` crée `.structurearc/` (memory, skills, notes, decisions, reports) si l'écriture est autorisée, sans rien écraser.
- **L'IA lit les gros fichiers par morceaux** (`files_read` avec `offset`) et ne relit plus en boucle le même fichier.
- **Calibration** : l'état « en cours » vient du moteur (plus d'écran figé sur « Mesure 0/4 »).
- **Reste de la V1.3.9** : demandes d'autorisation dans le chat, « Tout autoriser / Tout révoquer », outil d'indexation, auto-amélioration encadrée.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.10_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.10_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_10.md` / `LIMITES_V1_3_10.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
