# StructureArc

Application de bureau **locale** pour Windows 11 (x64) : organiser de gros projets, discuter avec une IA locale par projet, avec permissions séparées, journal d'audit et arrêt d'urgence. Aucun compte, aucune télémétrie.

> **Ce dépôt ne contient que les publications** (installateurs en pièces jointes de Release, empreintes, notes et limites de chaque version). Aucun code source n'est publié ici.

## Télécharger
Dernière version : **1.2.1** — page *Releases* → `StructureArc_1.2.1_x64-setup.exe`. Vérifiez toujours l'empreinte : voir [VERIFIER.md](VERIFIER.md).

| Version | Installateur | Taille | SHA-256 | Détails |
|---|---|---|---|---|
| 1.2.1 | `StructureArc_1.2.1_x64-setup.exe` | 22.2 Mo | `855ce1d3c0d3a7eb…` | [notes et limites](versions/v1.2.1/) |
| 1.2.0 | `StructureArc_1.2.0_x64-setup.exe` | 22.2 Mo | `35d04cd871d2c109…` | [notes et limites](versions/v1.2.0/) |
| 1.1.0 | `StructureArc_1.1.0_x64-setup.exe` | 22.2 Mo | `d16896ce4cdece31…` | [notes et limites](versions/v1.1.0/) |
| 1.0.0 | `StructureArc_1.0.0_x64-setup.exe` | 22.2 Mo | `78a48df9ac0b4d40…` | [notes et limites](versions/v1.0.0/) |

## État honnête
- Testé sur **un seul** ordinateur (Windows 11, 16 Go, GTX 1070). Chaque version a son fichier de limites (`LIMITES_*.md`) : lisez-le avant d'installer.
- Installateurs **non signés** pour l'instant.
- Le modèle d'IA n'est pas dans l'installateur ; il est installé ou importé par l'utilisateur, avec vérification d'empreinte.

## Contenu du dépôt
- `releases.json` — index lisible par machine ; `update/latest.json` — manifeste de la dernière version.
- `versions/vX.Y.Z/` — présentation, nouveautés, limites et empreintes de chaque version.
- [CHANGELOG.md](CHANGELOG.md) · [SECURITY.md](SECURITY.md) · [LICENSE.md](LICENSE.md) · [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
