> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.15 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `5ce15c1bf054…`, sources `f7e0f302c8f2…`, installateur standard signé `c8d9505ebbbf…`, hors-ligne signé `bc7f38d5c481…`)
- **Tests Rust** : `cargo test` **675 réussis / 0 échec / 12 ignorés** (`cargo-test-1315-d.log`), exécuté avec le dossier cible sur D: parce que l'éditeur de liens échoue sur W: (voir incidents).
- **`test.ps1` sur le binaire reconstruit : verdict global FAIL au 1er essai**, pour deux raisons : le `cargo test` ci-dessus n'a pas pu s'y exécuter (erreur de lien 1117, sans rapport avec le code) et le contrôle de démarrage S4 (seconde instance) a échoué une fois. Les autres étapes sont PASS (typecheck, vitest, tests Node, auto-test du moteur, fenêtre native, test de fumée, écran IA 16/16). **Il n'existe donc pas de `test.ps1` global PASS pour ce build** ; ses étapes ont été rejouées une par une.
- **Démarrage explicite** (`startup-check.mjs`) : l'échec S4 est **intermittent et sa cause n'est pas établie** ; rejoué seul : 24 contrôles PASS, sortie 0.
- **Chaîne de scénarios en fenêtre réelle (36)** : le premier passage n'est **pas** tout vert. `ui-mcp` 18/19, `ui-machine` 14/16 et `ui-model-switch` 12/13 ont échoué, et `ui-selfimprove-real` (simple et `--autonomous`) est resté INCONCLUSIVE. Rejeux : `ui-mcp` 19/19, `ui-machine` 16/16, `ui-model-switch` 13/13 (`rerun-1315b.log`). Causes probables notées dans le journal (charge de la machine par d'autres tâches pendant les contrôles, souris déplacée pendant `ui-machine`) mais **non démontrées**.
- **`ui-selfimprove-real`** : `--autonomous` PASS 17/17 au rejeu (`rerun-1315c.log`). Sans option : 17/17 contrôles réussis mais verdict **INCONCLUSIVE** (le petit modèle n'a pas mené la réparation à son terme) ; ce n'est pas un PASS. Une proposition de fichier protégé a été enregistrée une fois sans explication établie lors d'un essai antérieur ; la garde existe et les essais suivants sont conformes ; un test Rust déterministe reste à écrire.
- **Installateurs** : `installer-check` 16/16, `update-real` 1.3.14 vers 1.3.15 **33/33** (rejoué sur l'installateur reconstruit), `offline-installer-check` **9/9** (rejoué sur le hors-ligne reconstruit), `runtime-embed-check` 8/8, `runtime-inference-check` PASS.
- **Fiabilité des appels d'outils** : tests Rust unitaires pour chaque garde (G1 à G6) ; **G2 et G5 sont partiels**.
- **Provenance** : `make-release` a comparé les sources du build aux sources actuelles : identiques.

## Incidents de fabrication (rapportés tels quels)
- `link.exe` « erreur de périphérique d'E/S 1117 » sur le disque de travail W: : reproduit pour `cargo test` même avec 1 tâche et sans debug ; contourné avec un dossier cible sur D: (disque lent). Cause racine non élucidée.
- Les règles de charge des anciens scénarios (CPU < 80 %) datent de l'ancienne règle de ressources ; elles n'ont pas été alignées sur la règle finale.
- Audit npm : toutes les vulnérabilités sont dans l'outillage de développement (0 en production, 7 paquets) ; la mise à jour majeure est reportée.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Règle de ressources finale** | 3 Go de RAM disponible + 5 % de CPU disponible : appliquée aux **outils de test** seulement ; la garde du **produit** garde l'ancienne règle en pourcentage (décision D3 ouverte). |
| **Régulation CPU du moteur** | Écrite et testée en unités ; **non éprouvée sous charge réelle**. |
| **Multi-GPU** | Machines **simulées** uniquement, non branché ; jamais essayé avec deux cartes réelles. |
| **Auto-développement** | Qualité moyenne avec un petit modèle ; pas du développement autonome de gros projets. Un banc d'épreuve (P0 à P6) est en cours de préparation, hors produit ; aucun résultat à ce jour. |
| **Orchestrateur, subconscient** | Prouvés sur de petits modèles seulement / gain jamais mesuré. |
| **NeoHorse embarqué partout** | Décidé, **non fait** dans cette version (essai de faisabilité prévu pour la 1.3.16). |
| **Machine de mesure** | Une seule (Ryzen 7 2700, 32 Go, GTX 1070 8 Go) ; GPU AMD/Intel/CUDA et ARM non testés. |
| **Certificat** | Libellé de l'ancienne adresse ; manifeste de mise à jour non signé ; le futur certificat « Agen » est accepté d'avance par nom exact. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : exécutable contenu différent de celui de l'installateur standard ; vérifié par `offline-installer-check` et `model-embed-check` seulement. |
