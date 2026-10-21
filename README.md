# StructureArc

Application de bureau **locale** pour Windows 11 (x64) : confier de gros projets à une IA locale (missions, outils disponibles dans le build, méthode de découpage pour petits modèles), avec un cadre de permissions que vous réglez. Aucun compte, aucune télémétrie.

> **Ce dépôt ne contient que les publications** (installateurs signés en pièces jointes de Release, empreintes, notes et limites de chaque version). Aucun code source n'est publié ici.

## Télécharger
Dernière version : **1.3.12** — page *Releases* → `StructureArc_1.3.12_x64-setup.exe`. Vérifiez toujours la signature et l'empreinte : voir [VERIFIER.md](VERIFIER.md).

| Version | Installateur signé | Taille | SHA-256 | Détails |
|---|---|---|---|---|
| 1.3.12 | `StructureArc_1.3.12_x64-setup.exe` | 22.7 Mo | `48a0e0e4f246e93c…` | [notes et limites](versions/v1.3.12/) |
| 1.3.11 | `StructureArc_1.3.11_x64-setup.exe` | 22.7 Mo | `ea80b00f2e4989e9…` | [notes et limites](versions/v1.3.11/) |
| 1.3.10 | `StructureArc_1.3.10_x64-setup.exe` | 22.7 Mo | `b9904cf6f80c9ace…` | [notes et limites](versions/v1.3.10/) |
| 1.3.9 | `StructureArc_1.3.9_x64-setup.exe` | 22.6 Mo | `96ddfb90d406ffa3…` | [notes et limites](versions/v1.3.9/) |
| 1.3.8 | `StructureArc_1.3.8_x64-setup.exe` | 22.6 Mo | `b64a02e44186fecf…` | [notes et limites](versions/v1.3.8/) |
| 1.3.7 | `StructureArc_1.3.7_x64-setup.exe` | 22.6 Mo | `e1fe9395f27f90e1…` | [notes et limites](versions/v1.3.7/) |
| 1.3.6 | `StructureArc_1.3.6_x64-setup.exe` | 22.5 Mo | `0b55b477217aa2d4…` | [notes et limites](versions/v1.3.6/) |
| 1.3.5 | `StructureArc_1.3.5_x64-setup.exe` | 22.5 Mo | `4066daf2d0840ffe…` | [notes et limites](versions/v1.3.5/) |
| 1.3.4 | `StructureArc_1.3.4_x64-setup.exe` | 22.5 Mo | `55242cc4b76c638f…` | [notes et limites](versions/v1.3.4/) |
| 1.3.3 | `StructureArc_1.3.3_x64-setup.exe` | 22.5 Mo | `11b0b908463f3715…` | [notes et limites](versions/v1.3.3/) |
| 1.3.2 | `StructureArc_1.3.2_x64-setup.exe` | 22.5 Mo | `cd925a1ae42ac9d5…` | [notes et limites](versions/v1.3.2/) |
| 1.3.1 | `StructureArc_1.3.1_x64-setup.exe` | 22.5 Mo | `b99e83d13157efd0…` | [notes et limites](versions/v1.3.1/) |
| 1.3.0 | `StructureArc_1.3.0_x64-setup.exe` | 22.4 Mo | `557400b5409540fc…` | [notes et limites](versions/v1.3.0/) |
| 1.2.4 | `StructureArc_1.2.4_x64-setup.exe` | 22.4 Mo | `363d436dea3db456…` | [notes et limites](versions/v1.2.4/) |
| 1.2.3 | `StructureArc_1.2.3_x64-setup.exe` | 22.4 Mo | `40da6e568df47068…` | [notes et limites](versions/v1.2.3/) |
| 1.2.2 | `StructureArc_1.2.2_x64-setup.exe` | 22.3 Mo | `198844b331a6bd49…` | [notes et limites](versions/v1.2.2/) |
| 1.2.1 | `StructureArc_1.2.1_x64-setup.exe` | 22.3 Mo | `bd0f9027f1124489…` | [notes et limites](versions/v1.2.1/) |
| 1.2.0 | `StructureArc_1.2.0_x64-setup.exe` | 22.3 Mo | `8f217a503585a17a…` | [notes et limites](versions/v1.2.0/) |
| 1.1.0 | `StructureArc_1.1.0_x64-setup.exe` | 22.2 Mo | `658e6271cfe3eb5e…` | [notes et limites](versions/v1.1.0/) |
| 1.0.0 | `StructureArc_1.0.0_x64-setup.exe` | 22.2 Mo | `4b8bf6bc63da27df…` | [notes et limites](versions/v1.0.0/) |

## Pourquoi StructureArc ?
Beaucoup d'outils font tourner une IA sur votre ordinateur. StructureArc est conçu pour l'aider à **travailler sur de gros projets, avec les outils réellement disponibles et documentés dans chaque version** — même quand le modèle est petit :

- **Des outils activables par mission et par version** : fichiers, terminal, web/recherche, lecture Office, agents et compétences ; MCP et lecture d'écran ne sont annoncés que selon les limites du build. Les actions machine (souris/clavier et installation de logiciels) ne doivent pas être supposées disponibles : elles sont explicitement signalées comme non implémentées dans les limites publiques V1.3.1.
- **Une méthode de découpage pour petits modèles** : un gros projet est découpé en étapes qui tiennent dans la fenêtre d'un petit modèle (plan, tâches dépendantes, contrats, contexte compilé, rapports qui remontent), au lieu d'exiger un modèle géant.
- **Des optimisations mesurées pour petits ET gros modèles** : choix du modèle par tâche d'après des mesures, estimation fine de la mémoire (avec ou sans carte graphique), déport de couches, cache réduit, chargement sans copie en RAM, plafond de charge — avec une preuve publique encore limitée à la machine de référence, pas une garantie pour chaque PC.
- **Le bon modèle pour votre machine** : mesure du matériel, banc de qualité et d'appels d'outils, tableau publié, bascule entre modèles selon la tâche.
- **Un cadre qui vous garde le contrôle sans freiner le travail** : permissions par projet que vous ouvrez aussi largement que vous le voulez, journal d'audit, arrêt d'urgence, ressources de l'ordinateur protégées.
- **Aucun prérequis, aucun cloud** : pas de Docker, Python, Git, abonnement ni télémétrie ; installateur signé, empreintes publiées, limites de chaque version écrites noir sur blanc.

Détails, preuves et ce que nous ne prétendons pas : **[POURQUOI.md](POURQUOI.md)**.

## État honnête
- Testé sur **un seul** ordinateur (Windows 11, 16 Go, GTX 1070). Chaque version a son fichier de limites (`LIMITES_*.md`) : lisez-le avant d'installer.
- La version publique **1.3.12** propose aussi un installateur hors-ligne avec un modèle embarqué ; son fichier, sa taille et son empreinte sont publiés dans la page de version. Le modèle n'est pas automatiquement activé sans votre choix.
- Usage gratuit, sans exploitation commerciale par autrui : voir [LICENSE.md](LICENSE.md).

## Édité par
**[le-bon.contact](https://le-bon.contact)** — assistance et dépannage informatique à Agen.

- Site de l'entreprise : <https://le-bon.contact>
- Projet personnel et présentation : <https://kevin-moniaux.com>

## Contenu du dépôt
- `releases.json` — index lisible par machine (versions signées) ; `update/latest.json` — manifeste de la dernière version signée.
- `versions/vX.Y.Z/` — présentation, nouveautés, limites et empreintes de chaque version.
- [POURQUOI.md](POURQUOI.md) · [CHANGELOG.md](CHANGELOG.md) · [VERIFIER.md](VERIFIER.md) · [SECURITY.md](SECURITY.md) · [LICENSE.md](LICENSE.md) · [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
