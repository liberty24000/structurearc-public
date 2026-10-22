> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.13

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_13.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.13
- **Sécurité des mises à jour** : l'éditeur d'un installateur de mise à jour est désormais reconnu par le **nom exact** de son certificat (ou son empreinte épinglée) et une autorité « Certum Code Signing », plus par un simple « contient Moniaux / Certum » qui aurait accepté un certificat homonyme (audit de l'agent de revue ; tests `update::` 16/16).
- **Routage automatique PROUVÉ en fenêtre réelle** : bascule réelle 0.5B → 4B → 0.5B selon la tâche, verrou manuel respecté, modèle réellement chargé relu du moteur (`ui-agents-routing` 17/17). C'était un INCONCLUSIVE depuis plusieurs versions.
- **Téléchargement de modèle plus robuste** : script BITS (`fetch-model-bits.ps1`, reprise gérée par Windows) en plus de curl avec reprises ; marqueur de vérification écrit sans BOM (le moteur refusait le modèle sinon).
- **Fiabilité des tests** : Vitest borné à 2 workers (des workers mouraient quand la RAM dépassait 70 %) ; garde de provenance source → artefact dans la fabrication du dossier de livraison (un dossier ne peut plus être bâti sur des sources différentes de celles de l'exécutable).
- **Reste de la V1.3.12** : chat à zone de saisie fixe et fil qui suit les messages ; auto-développement durci par 14 observations réelles (toujours aucune tâche terminée, voir `LIMITES_V1_3_13.md`).

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.13_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.13_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_13.md` / `LIMITES_V1_3_13.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
