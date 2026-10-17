# StructureArc

Application de bureau **locale** pour Windows 11 (x64) : organiser de gros projets, discuter avec une IA locale par projet, avec permissions séparées, journal d'audit et arrêt d'urgence. Aucun compte, aucune télémétrie.

> **Ce dépôt ne contient que les publications** (installateurs signés en pièces jointes de Release, empreintes, notes et limites de chaque version). Aucun code source n'est publié ici.

## Télécharger
**Aucun installateur n'est téléchargeable pour l'instant** : les installateurs ne sont publiés qu'une fois **signés**.

En attente de signature (documentées, pas encore téléchargeables) : v1.2.1, v1.2.0, v1.1.0, v1.0.0.

## État honnête
- Testé sur **un seul** ordinateur (Windows 11, 16 Go, GTX 1070). Chaque version a son fichier de limites (`LIMITES_*.md`) : lisez-le avant d'installer.
- Le modèle d'IA n'est pas dans l'installateur ; il est installé ou importé par l'utilisateur, avec vérification d'empreinte.
- Usage gratuit, sans exploitation commerciale par autrui : voir [LICENSE.md](LICENSE.md).

## Contenu du dépôt
- `releases.json` — index lisible par machine (versions signées) ; `update/latest.json` — manifeste de la dernière version signée.
- `versions/vX.Y.Z/` — présentation, nouveautés, limites et empreintes de chaque version.
- [CHANGELOG.md](CHANGELOG.md) · [VERIFIER.md](VERIFIER.md) · [SECURITY.md](SECURITY.md) · [LICENSE.md](LICENSE.md) · [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
