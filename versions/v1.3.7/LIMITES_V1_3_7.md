> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.7 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `1ac71d13e0d9…`, installateur standard signé `e1fe9395f27f…`, installateur hors-ligne signé `a57b0c8e3a08…`, sources `eb05840679b0`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, chaîne 90) : 29 PASS + 1 INCONCLUSIVE. L'INCONCLUSIVE est `ui-agents-routing` (14/14, 1 « non testé » : aucune bascule observée car le routage a choisi le modèle déjà chargé).
- **Tests automatiques** : `test.ps1` PASS au **2e passage**. Le 1er passage a échoué sur UN test de minutage de `core::job` (« la fermeture du Job tue le processus »), module non modifié, qui passe seul (3/3) et au 2e passage complet : cause non élucidée, probablement la charge de la machine. `cargo test --lib` 589 réussis, 0 échec ; Vitest 168 réussis.
- **Interblocage corrigé** : la chaîne 89 (build précédent) a révélé que l'application se figeait à l'application d'une modification (`ui-changes` en délai dépassé, fenêtre « ne répond pas ») ; après correction, `ui-changes` 19/19 et la chaîne 90 passe. Un test unitaire de non-régression existe (il n'a pas été vérifié en rouge sur l'ancien code).
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid), `offline-installer-check` 9/9 et `model-embed-check` 8/8 (relancés après libération d'espace disque : un premier passage avait échoué faute de place sur le disque de travail, pas à cause du produit).
- **Subconscient** : 36 tests dont durabilité après arrêt brutal, idempotence, 10 000 souvenirs (conseil p99 ≈ 20 µs, recherche ≈ 0,8 ms, profil debug), secrets jamais mémorisés (test de bout en bout du terminal). Ressources **en test debug** : 16,7 Mo de mémoire après 10 000 événements, 0 % de CPU au repos sur 20 s.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Gain du subconscient** | Mesuré uniquement par **simulation** à agent scripté (1er essai 51 % → 100 %, erreurs répétées 63,7 → 0 ; cas difficile avec bruit et leurre 62,9 % → 94,9 %, 0 réflexe parasite). Ce n'est PAS un modèle réel : le gain avec un vrai LLM est inconnu. |
| **Ressources du subconscient** | Mesurées en profil debug dans un test, pas dans l'application installée ; pas de mesure sur plusieurs heures ni de latence ajoutée dans un vrai chat. Le service partage le processus de l'application. |
| **Routage automatique du chat** | Testé par tests unitaires et un scénario d'interface, mais sans bascule observée en fenêtre réelle (`ui-agents-routing` INCONCLUSIVE). La classification de la demande est une heuristique par mots-clés (français), précision jamais mesurée. |
| **Sauvegarde du cache par conversation, ordonnanceur d'emplacements** | Prévus pour V1.3.7 initialement, **non faits** (reportés). |
| **Réflexes bloquants** | Le subconscient ne bloque jamais seul : un réflexe « bloquant » exige votre approbation explicite. |
| **Hérité de V1.3.6** | Classement des modèles sur petits jeux, recherche web simulée ; Gemma 4 12B lent ; Qwen3.5 9B « en évaluation » ; cache de préfixe mesuré en synthétique ; agents simultanés désactivés par défaut ; une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go simple canal) ; GPU AMD/Intel/CUDA, ARM : non testés. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable contenu est DIFFÉRENT de celui de l'installateur standard ; il n'est vérifié que par `offline-installer-check` et `model-embed-check`. |
| **Mise à jour** | Manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire ; SmartScreen peut avertir. |
