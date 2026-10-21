> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.12 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `00fd448db88c…`, installateur standard signé `48a0e0e4f246…`, installateur hors-ligne signé `2c65a7e2a815…`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, 36 scénarios) : 30 PASS au premier passage. Relances (`rerun-1312.log`) : `ui-mission` a échoué deux fois sur un délai d'ouverture du projet puis **20/20** en relance manuelle ; `ui-import-gguf` 13/14 trois fois de suite — cause trouvée : depuis que des modèles de 2,6 et 5,3 Go sont dans le dossier analysé, la relecture après import est lente ; le scénario attend désormais la liste à jour (**16/16**), ce n'est pas un défaut du produit ; `runtime-inference-check` INCONCLUSIVE **par sécurité** (la garde CPU a interrompu la génération à 95 % de CPU, seuil 75 %) puis **PASS** en relance. Deux INCONCLUSIVE déclarés : `ui-agents-routing` (routage automatique non observé) et `ui-selfimprove-real` (15 et 17 vérifications mais le modèle n'a rien écrit).
- **Tests automatiques** : `test.ps1` verdict global **PASS au 1er essai** : typecheck, vitest, scripts node, **cargo test 653 réussis / 0 échec / 11 ignorés**, auto-test du moteur, fenêtre native, test de fumée, écran IA 16/16.
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid) **par `ssign`** (première livraison sans SimplySign Desktop), `offline-installer-check` 9/9 et `model-embed-check` 8/8. Les deux premiers essais de fabrication hors-ligne ont échoué : session SimplySign expirée, puis « accès refusé » au remplacement du fichier par ssign (corrigé : signature dans un dossier temporaire puis recopie).
- **Chat** : `ui-chat-modes` **22/22** avec 3 contrôles du fil (30 messages ouverts positionnés en bas, zone de saisie visible, redescente après envoi) sur l'exécutable 1.3.11 (k) ; vitest `ChatScreen` 22/22.

## Auto-développement : 14 observations libres, aucune tâche terminée
| N° | Modèle / build | Résultat |
|---|---|---|
| 1–6 | Qwen3.5 4B, 1.3.10–1.3.11 | Aucun code ou test faux ; boucles de lecture ; coupures de fenêtre |
| 7–10 | Qwen3.5 9B, 1.3.11 | Test écrit puis coupé (réserve 1 200 jetons, contexte réel 8 192) ; cadre `vitest` au lieu de `node:test` |
| 11–12 | 9B, contexte 12 288 | Plus de coupure ; fonctions inventées (`ramPercent`), 40 propositions sans succès |
| 13 | 9B, exports vérifiés | Modifie le module à tester (décision du propriétaire supprimée) ; comptes rendus au lieu d'agir ; invariant HEAD cassé par MON commit concurrent |
| 14 | 9B, garde-fous | Module intact (refus efficace) ; 9 propositions bouclant sur « le test 4 échoue » ; dernier fichier tronqué |
Dans les 14 cas, le dépôt d'origine n'a jamais été touché par l'agent (invariants 10/10, sauf n°13 attribuable à moi). **Le logiciel ne se développe pas seul avec ces modèles.** Traces : `preuves/rapports/*trace.json`.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Auto-amélioration** | Voir ci-dessus. Un autre modèle (9B « coder ») n'a pas été essayé (accord du propriétaire requis). |
| **Chat : suivi pendant la génération** | « Rester en haut quand on lit pendant que des jetons arrivent » est codé mais non prouvé en fenêtre réelle avec un modèle. |
| **ssign** | Outil tiers (MIT) non audité (lecture du source refusée par le contrôle d'autorisation) ; graine chiffrée utilisable par tout programme du compte Windows du propriétaire sur ce PC. |
| **Filet de température GPU** | Simulation seulement ; `ui-gpu` 14/14. |
| **Journaux Windows** | 3 écrans bleus 0xD1 en octobre (pilote non identifié, un seul vidage restant, non analysé) ; `link.exe` 1117 récurrent ; blocs défectueux du SSD système : **sauvegarde conseillée**. |
| **Scénarios instables** | `ui-mission` (délai d'ouverture), `ui-i18n`, `runtime-embed-check` : échecs ponctuels puis PASS. |
| **Routage automatique, gain du subconscient, cache par conversation** | Inchangés : non prouvés / non faits. |
| **Hérité** | Une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go) ; GPU AMD/Intel/CUDA et ARM non testés ; manifeste de mise à jour non signé ; certificat avec l'ancienne adresse (Sigean). |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : exécutable contenu DIFFÉRENT de celui de l'installateur standard ; vérifié par `offline-installer-check` et `model-embed-check` seulement. |
