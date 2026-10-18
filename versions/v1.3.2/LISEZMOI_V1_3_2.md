> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.2

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_2.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.2
- **Installateur hors-ligne** (`StructureArc_1.3.2_x64-offline-setup.exe`, environ 1,1 Go) : même application, runtime llama.cpp CPU et modèle Qwen2.5 1,5B déjà inclus (taille et SHA-256 vérifiés à l'installation) ; aucun téléchargement n'est nécessaire pour avoir une IA locale prête. L'installateur standard reste disponible (téléchargement vérifié du modèle).
- **Actions « machine » proposées** (souris, clavier, installation de logiciel) : le modèle ne peut que PROPOSER ; rien ne s'exécute sans votre clic d'approbation sur cette action précise ; désactivé par défaut, auditée, coupée par l'arrêt d'urgence ; jamais disponible depuis l'interface web.
- **Contrôle d'ancrage des réponses** : sous chaque réponse, un badge indique combien de fichiers, adresses, identifiants et nombres cités sont retrouvés dans les sources réellement reçues par le modèle. C'est une ESTIMATION, pas une garantie ; « rien de vérifiable » n'est pas « vérifié ».
- **Outils sûrs** : un modèle n'est choisi pour une tâche à outils que s'il réussit les appels attendus ET ne fait aucun appel parasite au banc (Llama 3.2 3B et 1B en sont écartés). La matrice de compatibilité l'affiche, ainsi que l'état de la mémoire engagée (mesurée ou non).
- **Mise à jour : diagnostic plus clair** (vérification Authenticode indépendante de l'environnement PowerShell hérité, message explicite si elle est indisponible) et documentation alignée sur le comportement réel.
- **Textes publics resserrés** après relecture indépendante (portée des preuves : un seul PC).

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.2_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.2_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_2.md` / `LIMITES_V1_3_2.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
