> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.13 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `412627f33957…`, installateur standard signé `49dfff31265701…`, installateur hors-ligne signé `e1d8db420b3e…`)
- **Build contrôlé** : compilé à **1 tâche** (`CARGO_BUILD_JOBS=1`, sans symboles de débogage) avec relevé mémoire : RAM système de 55 % à **71,4 % max** pendant l'étape LTO, CPU max 26,6 % (`preuves/system-samples.json`, 253 échantillons). Un build à 2 tâches avec 72 % de RAM avait échoué sans diagnostic (agent de revue, même jour).
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, 36 scénarios) : **32 PASS** au premier passage, dont `ui-agents-routing` 17/17 (routage réel), `ui-resume` 15/15, `ui-chat-modes` 22/22, `ui-import-gguf` 16/16. Relances (`rerun-1313.log`) : `ui-agents-parallel` 12/13 puis **13/13** après alignement du critère (le GPU peut être utilisé à 100 %, demande du propriétaire ; CPU/RAM restent plafonnés à 80 %) ; `ui-mission` a échoué **trois fois** (délai d'ouverture du projet, puis aucun appel d'outil) avant de passer **20/20** — cause trouvée, voir le défaut ci-dessous. Deux INCONCLUSIVE déclarés : `ui-selfimprove-real` ×2 (15/15 vérifications mais le modèle n'a rien écrit).
- **Tests automatiques** : `test.ps1` — voir `preuves/test.log` (résultat reporté tel quel dans ce dossier, à lire ; à 1 tâche cargo, RAM < 65 % au départ).
- **Installateurs** : standard signé (Valid, ssign) ; hors-ligne signé (Valid, ssign) ; `offline-installer-check` 9/9 et `model-embed-check` 8/8.
- **Mise à jour** : `update::` 16/16 (4 nouvelles assertions : certificat Certum homonyme refusé ; empreinte épinglée acceptée ; nom exact sans autorité Certum refusé ; nom exact + Certum accepté).

## DÉFAUT PRODUIT connu, non corrigé dans cette version
**Copies d'auto-amélioration fantômes** : chaque auto-amélioration enregistre sa copie jetable comme projet, mais l'abandon de la copie (`selfimprove_discard`) supprime le dossier **sans désenregistrer le projet ni purger son index** (≈ 2 000 fichiers par copie). Après des dizaines d'essais, la base de test pesait 590 Mo avec 65 projets à racine inexistante et l'ouverture d'un projet dépassait 20 s. Un utilisateur qui lance beaucoup d'auto-améliorations subira le même grossissement de SA base. Contournement : supprimer à la main les projets « introuvables » depuis l'accueil. Correctif prévu en 1.3.14 (désenregistrement + purge de l'index à l'abandon, avec test).

## Auto-développement : 17 observations, aucune tâche terminée
| N° | Modèle / build | Résultat |
|---|---|---|
| 1–6 | Qwen3.5 4B, 1.3.10–1.3.11 | Aucun code ou test faux ; boucles de lecture ; coupures de fenêtre |
| 7–14 | Qwen3.5 9B, 1.3.11–1.3.12 | Test écrit puis coupé ; mauvais cadre (`vitest` vs `node:test`) ; fonctions inventées ; décision du propriétaire supprimée (désormais refusé) ; 9 propositions bouclant sur un test qui échoue |
| 15–16 | Qwopus 9B coder, 1.3.12 | Modèle non chargé (marqueur avec BOM, puis garde mémoire à 55 % de RAM) |
| 17 | Qwopus 9B coder, 1.3.12, RAM 48 % | **Meilleur résultat** : fichier `node:test` de 81 lignes, **10/13 tests passants**, aucune fonction inventée ; puis un appel d'outil de 8,4 Ko refusé par le serveur (HTTP 500) et deux tours sans aucun appel. Tâche non terminée. |
Dans les 17 cas, le dépôt d'origine n'a jamais été touché par l'agent (invariants 10/10, sauf n°13 attribuable à un commit concurrent de l'auteur). **Le logiciel ne se développe pas seul avec ces modèles.** Causes résiduelles côté application : appel d'outil > 8 Ko refusé ; après une erreur serveur le modèle ne relance pas d'appel. Traces : `preuves/rapports/*trace.json`.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Auto-amélioration** | Voir ci-dessus. Le modèle Qwopus (9B coder) n'est pas dans le catalogue téléchargeable par défaut ; conservé ou supprimé selon décision de l'agent de revue. |
| **Routage automatique** | Prouvé **une fois** sur cette machine (17/17). Classification par mots-clés (français) : précision non mesurée. |
| **Chat : suivi pendant la génération** | « Rester en haut quand on lit pendant que des jetons arrivent » est codé mais non prouvé en fenêtre réelle avec un modèle. |
| **ssign** | Outil tiers (MIT) non audité ; graine chiffrée utilisable par tout programme du compte Windows de l'auteur sur ce PC. |
| **Filet de température GPU** | Simulation seulement ; `ui-gpu` 14/14. |
| **Journaux Windows** | 3 écrans bleus 0xD1 en octobre (pilote non identifié, vidage non analysé) ; `link.exe` 1117 intermittent sur le SSD de travail (corrélé au parallélisme et à la RAM > 70 %, cause racine non élucidée) ; blocs défectueux du SSD système : **sauvegarde conseillée**. |
| **Scénarios instables** | `ui-mission` (voir défaut ci-dessus), `ui-i18n`, `runtime-embed-check` : échecs ponctuels puis PASS. |
| **Gain du subconscient, cache par conversation** | Inchangés : non prouvés / non faits. |
| **Hérité** | Une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go) ; GPU AMD/Intel/CUDA et ARM non testés ; manifeste de mise à jour non signé ; certificat avec l'ancienne adresse (Sigean) — la 1.3.13 accepte d'avance le futur certificat « Agen » par nom exact. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : exécutable contenu DIFFÉRENT de celui de l'installateur standard ; vérifié par `offline-installer-check` et `model-embed-check` seulement. |
