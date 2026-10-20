> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.8 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `354fd9830364…`, installateur standard signé `b64a02e44186…`, installateur hors-ligne signé `40f636765ec0…`, sources `5e771c8976d4`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, chaîne 91) : 29 PASS + 1 INCONCLUSIVE (`ui-agents-routing`, 14/14 dont 1 « non testé » : aucune bascule observée).
- **Tests automatiques** : `test.ps1` PASS **dès le 1er passage** ; `cargo test --lib` 590 réussis, 0 échec ; Vitest 168 réussis.
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid), `offline-installer-check` 9/9 et `model-embed-check` 8/8.
- **Latence du subconscient sous charge réelle** : médiane 110 ms avec / 109 ms sans (blocs alternés, 480 commandes, 192 réussites et 48 échecs par camp) ; avant correction : 118 / 109 ms. Mémoire du processus 36,1 → 36,7 Mo. 0 échec d'écriture, 0 événement perdu.
- **Repos** : 32,7 Mo, ≈ 0,11 % d'un cœur, avec ou sans subconscient (processus principal seul).

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Gain du subconscient** | Aucun gain démontré sous charge réelle : tout s'est passé dans UNE session, donc aucun réflexe validé et aucun rappel montré (2 hypothèses seulement). Gain mesuré uniquement par **simulation** à agent scripté (1er essai 51 % → 100 %, erreurs répétées 63,7 → 0 ; cas difficile avec bruit et leurre 62,9 % → 94,9 %, 0 réflexe parasite). Ce n'est PAS un modèle réel : le gain avec un vrai LLM est inconnu. |
| **Ressources du subconscient** | Mesurées dans l'application réelle mais seulement au repos (6 min) et sous 480 commandes ; pas de mesure sur plusieurs heures ni avec un vrai chat de modèle. La mémoire croît d'≈ 0,6 Mo sur 480 commandes (à surveiller). Le service partage le processus de l'application. |
| **Cause mal départagée** | Dans la charge synthétique, « après noop » et « après touch » sont indiscernables ; le système reste prudent (hypothèse seulement). |
| **Routage automatique du chat** | Testé par tests unitaires et un scénario d'interface, mais sans bascule observée en fenêtre réelle (`ui-agents-routing` INCONCLUSIVE). La classification de la demande est une heuristique par mots-clés (français), précision jamais mesurée. |
| **Sauvegarde du cache par conversation, ordonnanceur d'emplacements** | Prévus pour V1.3.8 initialement, **non faits** (reportés). |
| **Réflexes bloquants** | Le subconscient ne bloque jamais seul : un réflexe « bloquant » exige votre approbation explicite. |
| **Hérité de V1.3.6** | Classement des modèles sur petits jeux, recherche web simulée ; Gemma 4 12B lent ; Qwen3.5 9B « en évaluation » ; cache de préfixe mesuré en synthétique ; agents simultanés désactivés par défaut ; une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go simple canal) ; GPU AMD/Intel/CUDA, ARM : non testés. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable contenu est DIFFÉRENT de celui de l'installateur standard ; il n'est vérifié que par `offline-installer-check` et `model-embed-check`. |
| **Mise à jour** | Manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire ; SmartScreen peut avertir. |
