> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.1

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_1.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.1
- **Le meilleur modèle de votre PC est choisi sur des mesures** : sur la machine de référence (carte GTX 1070 8 Go, 16 Go de RAM), **Qwen3.5 4B** réussit tous les tests de qualité et d'appels d'outils. Il est ajouté au catalogue ; sans carte graphique utilisable, l'application recommande Qwen2.5 1,5B (le 4B est trop lent sur processeur seul). Le tableau des mesures est dans `docs/MESURES_PC.md`.
- **Mémoire mieux estimée** : l'application tient compte de la mémoire réellement mesurée (avec ou sans carte graphique), charge les poids sans mappage quand ils sont sur la carte (RAM utilisée : 3,4 Go → 1,2 Go sur Qwen3.5 4B) et limite la part du modèle sur la carte quand elle la ferait dépasser sa limite de charge.
- **Missions autonomes** : `/mission <objectif>` (ou le bouton « Lancer une mission autonome ») : le chat enchaîne les appels d'outils (fichiers, terminal, web, propositions de modifications) dans les limites des autorisations du projet, 30 appels et 20 minutes au plus ; une modification n'est jamais écrite sans votre approbation.
- **Recherche web** : outils `web_search` et `web_fetch` ; le niveau « autonome » de l'autorisation web est un choix explicite par projet (sinon chaque lecture demande votre confirmation).
- **Connecteurs MCP** (écran Autorisations) : vous déclarez un serveur d'outils externe ; il est désactivé par défaut et chaque outil est « à confirmer » tant que vous ne le passez pas en « automatique ».
- **Capture d'écran + OCR local** (autorisation « capture / OCR », lecture) : l'outil est prévu pour lire localement du texte ; la limite V1.3.1 ne publie pas encore de scénario complet en vraie fenêtre utilisateur. Aucune image n'est conservée ni envoyée.
- **Agents de mission** : option (désactivée par défaut) pour créer automatiquement les agents et compétences proposés pendant une mission.
- **Mise à jour plus sûre** : verrou entre processus, refus d'une architecture ou d'une version trop ancienne avant tout téléchargement.
- **Interface** : les onglets qui ne tiennent pas dans la fenêtre passent sous « Plus » ; explications longues repliées.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.1_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_1.md` / `LIMITES_V1_3_1.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
