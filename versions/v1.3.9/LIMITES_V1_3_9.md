> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.9 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `9e4a381992dd…`, installateur standard signé `96ddfb90d406…`, installateur hors-ligne signé `36fb850d3c24…`, sources `63a14c312434`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, chaîne 92, 33 scénarios) : **31 PASS + 1 INCONCLUSIVE + 1 FAIL**. L'INCONCLUSIVE est `ui-agents-routing` (14/14, 1 « non testé »). Le FAIL est **`ui-gpu` 13/14** : un échantillon de charge GPU à 98,2 % pour une limite de 95 % (CPU max 22 %, RAM max 46,5 %) ; **deux rejeux : 14/14** (GPU max 63,2 % puis 34,8 %). Cause du pic non élucidée (un seul échantillon) ; il n'est pas exclu qu'un prompt un peu plus long (outil de demande d'autorisation désormais toujours déclaré) y contribue. Le rapport en échec est conservé dans `preuves/`.
- **Scénarios avec un VRAI modèle (Qwen3.5 4B), dans la chaîne** : `ui-permission-request` 16/16 (demande, « oui » tapé, lecture du fichier avec le mot-témoin, « non », mode Auto dans le même tour, révocation ; RAM max 48 %) ; `ui-selfimprove-mission` 14/14 (le modèle lance le test, lit le fichier, propose la correction dans la copie isolée ; le test passe après approbation, code de sortie 0 relevé par le script) ; `ui-selfimprove` 20/20.
- **Tests automatiques** : `test.ps1` PASS, mais **au 4e essai** : les trois premiers ont échoué à la COMPILATION (éditeur de liens `link.exe`, erreur d'E/S 1117 : espace disque insuffisant au 1er, incident transitoire ensuite), pas sur un test ; compilés par tentatives répétées (journaux `test92-*.log`). Ces passages ont utilisé un profil de test sans informations de débogage (`CARGO_PROFILE_DEV_DEBUG=0`) pour ménager le disque. `cargo test --lib` 613 réussis, 0 échec ; Vitest 174 réussis.
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid), `offline-installer-check` 9/9 et `model-embed-check` 8/8.
- **Défauts trouvés par ces essais et corrigés avant livraison** : l'IA donnait le nom du projet comme périmètre d'une autorisation (sous-dossier inexistant → « hors du périmètre ») : le périmètre est ramené au dossier existant le plus proche ; le bouton « Tout autoriser » ne couvrait que les fichiers (retour du propriétaire) : il couvre toutes les capacités.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Demandes d'autorisation par l'IA** | Prouvées avec UN modèle (Qwen3.5 4B), un petit projet, un fichier : un autre modèle peut ne pas appeler l'outil (le scénario serait alors « non concluant »). En mode Auto, « tout » exclut l'installation de logiciels et la souris/clavier (décision de prudence, non demandée par le propriétaire). |
| **Auto-amélioration** | Prouvée sur un dépôt temporaire avec un bug très simple. Rien n'est prouvé sur des tâches réelles de développement de StructureArc par un modèle local ; la valeur démontrée est l'isolation, les chemins protégés, la reprise et la preuve par code de sortie. Le « plan de version » n'est pas écrit : signature et publication restent manuelles. |
| **Outil d'indexation du chat** | Couvert par la compilation et la chaîne, mais pas par un scénario dédié avec un modèle réel. |
| **Gain du subconscient** | Aucun gain démontré sous charge réelle : tout s'est passé dans UNE session, donc aucun réflexe validé et aucun rappel montré (2 hypothèses seulement). Gain mesuré uniquement par **simulation** à agent scripté (1er essai 51 % → 100 %, erreurs répétées 63,7 → 0 ; cas difficile avec bruit et leurre 62,9 % → 94,9 %, 0 réflexe parasite). Ce n'est PAS un modèle réel : le gain avec un vrai LLM est inconnu. |
| **Ressources du subconscient** | Mesurées dans l'application réelle mais seulement au repos (6 min) et sous 480 commandes ; pas de mesure sur plusieurs heures ni avec un vrai chat de modèle. La mémoire croît d'≈ 0,6 Mo sur 480 commandes (à surveiller). Le service partage le processus de l'application. |
| **Cause mal départagée** | Dans la charge synthétique, « après noop » et « après touch » sont indiscernables ; le système reste prudent (hypothèse seulement). |
| **Routage automatique du chat** | Testé par tests unitaires et un scénario d'interface, mais sans bascule observée en fenêtre réelle (`ui-agents-routing` INCONCLUSIVE). La classification de la demande est une heuristique par mots-clés (français), précision jamais mesurée. |
| **Sauvegarde du cache par conversation, ordonnanceur d'emplacements** | Prévus pour la V1.3.7 initialement, **toujours non faits** (reportés). |
| **Réflexes bloquants** | Le subconscient ne bloque jamais seul : un réflexe « bloquant » exige votre approbation explicite. |
| **Hérité de V1.3.6** | Classement des modèles sur petits jeux, recherche web simulée ; Gemma 4 12B lent ; Qwen3.5 9B « en évaluation » ; cache de préfixe mesuré en synthétique ; agents simultanés désactivés par défaut ; une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go simple canal) ; GPU AMD/Intel/CUDA, ARM : non testés. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable contenu est DIFFÉRENT de celui de l'installateur standard ; il n'est vérifié que par `offline-installer-check` et `model-embed-check`. |
| **Mise à jour** | Manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire ; SmartScreen peut avertir. |
