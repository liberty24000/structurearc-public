> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.4

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_4.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.4
- **Agents locaux simultanés** : plusieurs tâches d'un plan peuvent partager UN seul modèle local entièrement chargé sur la carte graphique (un seul parcours des poids sert tous les agents). Mesuré sur le PC de référence avec le vrai Qwen2.5 1,5B : 3 tâches en 28,6 s en série contre 13,2 s en parallèle (une mesure, sorties courtes) ; au banc, ≈ ×1,6 de débit total à 4 agents, chaque agent plus lent.
- **Prudent par défaut** : réglage Paramètres → « Agents simultanés » (1 à 4, **1 par défaut** = comportement historique, pris en compte au prochain démarrage du modèle). Le plan ne s'exécute en parallèle que si le serveur a plusieurs emplacements, que le modèle est **verrouillé** et chargé, que **toutes** les tâches sont locales (aucun fournisseur externe) et que la RAM reste sous 65 %. Au plus 3 tâches à la fois ; la VRAM de chaque contexte supplémentaire est comptée.
- **Reste de la V1.3.3** : calibration automatique du déport GPU par modèle et par machine, modèle à experts 30B-A3B « expérimental », garde GPU à durée soutenue.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.4_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.4_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_4.md` / `LIMITES_V1_3_4.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
