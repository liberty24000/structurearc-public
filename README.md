# StructureArc

Application de bureau **locale** pour Windows 11 (x64) : organiser de gros projets, discuter avec une IA locale par projet, avec permissions séparées, journal d'audit et arrêt d'urgence. Aucun compte, aucune télémétrie.

> **Ce dépôt ne contient que les publications** (installateurs signés en pièces jointes de Release, empreintes, notes et limites de chaque version). Aucun code source n'est publié ici.

## Télécharger
Dernière version : **1.2.2** — page *Releases* → `StructureArc_1.2.2_x64-setup.exe`. Vérifiez toujours la signature et l'empreinte : voir [VERIFIER.md](VERIFIER.md).

| Version | Installateur signé | Taille | SHA-256 | Détails |
|---|---|---|---|---|
| 1.2.2 | `StructureArc_1.2.2_x64-setup.exe` | 22.3 Mo | `198844b331a6bd49…` | [notes et limites](versions/v1.2.2/) |
| 1.2.1 | `StructureArc_1.2.1_x64-setup.exe` | 22.3 Mo | `bd0f9027f1124489…` | [notes et limites](versions/v1.2.1/) |
| 1.2.0 | `StructureArc_1.2.0_x64-setup.exe` | 22.3 Mo | `8f217a503585a17a…` | [notes et limites](versions/v1.2.0/) |
| 1.1.0 | `StructureArc_1.1.0_x64-setup.exe` | 22.2 Mo | `658e6271cfe3eb5e…` | [notes et limites](versions/v1.1.0/) |
| 1.0.0 | `StructureArc_1.0.0_x64-setup.exe` | 22.2 Mo | `4b8bf6bc63da27df…` | [notes et limites](versions/v1.0.0/) |

## Pourquoi StructureArc ?
Beaucoup d'outils font tourner une IA sur votre ordinateur. StructureArc cherche à la laisser **travailler sur vos projets sans lui donner les clés de la machine** :

- **Permissions par projet, désactivées par défaut**, confirmation des actions sensibles, journal d'audit et **arrêt d'urgence**.
- **L'IA propose, vous décidez** : rien n'est modifié ni créé sans votre validation, et seul vous marquez une tâche comme « vérifiée ».
- **Votre ordinateur reste utilisable** : l'IA est plafonnée à 80 % du processeur et de la mémoire, et refuse de démarrer plutôt que de tout figer.
- **Le bon petit modèle pour votre machine** : mesure du matériel, choix et bascule entre modèles selon la tâche, écran de compatibilité.
- **Un logiciel qui prouve ce qu'il dit** : installateur signé, empreintes SHA-256, et pour chaque version la liste de ce qui est prouvé… et de ce qui ne l'est pas.
- **Aucun prérequis, aucun cloud** : pas de Docker, Python, Git, abonnement ni télémétrie.

Détails, preuves et ce que nous ne prétendons pas : **[POURQUOI.md](POURQUOI.md)**.

## État honnête
- Testé sur **un seul** ordinateur (Windows 11, 16 Go, GTX 1070). Chaque version a son fichier de limites (`LIMITES_*.md`) : lisez-le avant d'installer.
- Le modèle d'IA n'est pas dans l'installateur ; il est installé ou importé par l'utilisateur, avec vérification d'empreinte.
- Usage gratuit, sans exploitation commerciale par autrui : voir [LICENSE.md](LICENSE.md).

## Édité par
**[le-bon.contact](https://le-bon.contact)** — assistance et dépannage informatique à Agen.

- Site de l'entreprise : <https://le-bon.contact>
- Projet personnel et présentation : <https://kevin-moniaux.com>

## Contenu du dépôt
- `releases.json` — index lisible par machine (versions signées) ; `update/latest.json` — manifeste de la dernière version signée.
- `versions/vX.Y.Z/` — présentation, nouveautés, limites et empreintes de chaque version.
- [POURQUOI.md](POURQUOI.md) · [CHANGELOG.md](CHANGELOG.md) · [VERIFIER.md](VERIFIER.md) · [SECURITY.md](SECURITY.md) · [LICENSE.md](LICENSE.md) · [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
