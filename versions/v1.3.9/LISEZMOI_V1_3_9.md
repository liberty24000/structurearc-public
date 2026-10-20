> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.9

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_9.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.9
- **L'IA peut demander une autorisation dans le chat** : elle indique la capacité, le niveau minimal et la raison ; une carte « L'IA demande une autorisation » apparaît avec **Oui / Non** (ou répondez « oui » / « non » dans le chat : seules des réponses courtes et sans ambiguïté comptent). Une demande n'accorde rien par elle-même. **En mode Auto, les demandes ordinaires sont accordées d'office** et l'IA s'en sert dans le même tour ; l'installation de logiciels et le contrôle souris/clavier demandent toujours votre réponse. Tout est journalisé et révocable.
- **« Tout autoriser » / « Tout révoquer »** (onglet Autorisations) : accorde en un clic (avec confirmation) TOUTES les capacités à leur niveau maximal permis par le moteur ; le plafond reste la limite (installation et souris/clavier confirmées action par action, terminal : seules les commandes sûres s'exécutent seules, web en lecture seule).
- **Nouvel outil d'indexation du projet pour l'IA** (`project_index`) : elle peut lancer l'indexation (mêmes droits qu'une lecture, une seule à la fois, 180 s maximum).
- **Auto-amélioration encadrée** (section dédiée) : l'application peut travailler sur le code d'un projet (par exemple le sien) dans une COPIE de travail git isolée, sur une branche `auto/…`. Chemins protégés refusés (règles de permissions, terminal, scripts de signature et de publication, `release/`, `.git`, clés…), briefing de reprise, copie jetable. Elle ne signe ni ne publie jamais : ces actions restent les vôtres.
- **Reste de la V1.3.8** : correction de latence et contexte appris du Subconscient.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.9_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.9_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_9.md` / `LIMITES_V1_3_9.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
