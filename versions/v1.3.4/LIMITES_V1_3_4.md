> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.4 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `e291c71c9795…`, installateur standard signé `55242cc4b76c…`, installateur hors-ligne signé `99dba3889bc2…`, sources `4e932bd45e32`)
- **Registre : 30 rapports « courant » = 28 PASS + 1 INCONCLUSIVE + 1 FAIL conservé.** Le FAIL est le **premier passage** de `ui-i18n` (12/13 : « délai dépassé : arabe après redémarrage », dépassement de délai au redémarrage de l'application) ; rejoué seul sur le même exécutable : **14/14 PASS**. Cause du délai non élucidée (échec non reproduit). L'INCONCLUSIVE est `ui-agents-routing` (14/14, 1 « non testé » : le routage a choisi le Qwen3.5 4B, la bascule vers le 1,5B n'a donc pas été exercée ici ; la bascule réelle est couverte par `ui-model-switch` 13/13).
- **Agents locaux simultanés** : `ui-agents-parallel` 12/12 en fenêtre réelle (vrai Qwen2.5 1,5B sur le GPU, modèle verrouillé, calibration réelle préalable, 3 tâches indépendantes) : 28,6 s en série contre 13,2 s en parallèle avec `-np 3`, trois tâches lancées dans le même lot, RAM ≤ 46 %, GPU ≤ 68 %, fichiers du projet inchangés. Tests unitaires : planificateur (nombre d'emplacements limité par la VRAM, refus en déport partiel ou avec débordement en RAM, arguments `-np`/`-c`) et ordonnanceur (`local_parallel_for` : séquentiel sans verrou, sans modèle chargé, avec un fournisseur externe ou un seul emplacement).
- **Tests automatiques** : `test.ps1` PASS dès le premier passage (typecheck ; Vitest 161 réussis ; `cargo test` 539 réussis / 0 échec / 9 ignorés ; auto-test moteur, fenêtre native, fumée UI, écran IA).
- **Installateur** : installation/désinstallation 16/16 ; `update-real` 33/33 ; runtime embarqué ; inférence installée PASS. **Hors-ligne** : `offline-installer-check` 9/9 et `model-embed-check` 8/8.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Gain des agents simultanés** | UNE mesure en fenêtre réelle (×2,17 sur 3 courtes tâches) et un banc (×1,6 à 4 agents, 4B et 1,5B). Ne pas généraliser : sorties courtes, un seul PC, deux modèles ; chaque agent est plus lent (15 contre 36 jetons/s au banc) ; le débit sature vers 4 à 8 agents. |
| **Conditions d'activation** | Désactivé par défaut (réglage 1). Il faut un modèle ENTIÈREMENT sur la carte (calibré), le modèle verrouillé et chargé, des tâches 100 % locales ; sinon l'exécution reste en série. Non mesuré sur processeur seul ni en déport partiel. Le nouvel emplacement ne s'applique qu'au prochain démarrage du modèle. |
| **Agents externes en parallèle** | Toujours en série : le budget agrégé de ressources pour les fournisseurs externes (Claude Code, Codex) n'existe pas (`AGGREGATE_BUDGET_IMPLEMENTED = false`). |
| **Qualité avec plusieurs agents** | Non mesurée : seule l'identité des 120 premiers caractères de la sortie de l'agent 1 entre 1 et N agents a été vérifiée (banc), pas la qualité des réponses de chaque agent. |
| **Calibration automatique après un vrai téléchargement** | Le déclenchement automatique n'est couvert que par tests unitaires ; la calibration manuelle est prouvée en fenêtre réelle. |
| **30B-A3B (expérimental)** | Lecture du prompt ≈ 30-40 jetons/s : missions longues inutilisables ; qualité mesurée seulement sur le petit banc maison. |
| **Garde GPU : durée tolérée** | Charge GPU soutenue 10 s avant interruption ; un prompt de ≈ 3 600 jetons ou plus d'un seul bloc dépasse ce budget sur ce PC. |
| **Scripts Windows** | Simulation par défaut ; leur application (administrateur) n'a pas été exécutée par cette livraison. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable qu'il contient est DIFFÉRENT de celui de l'installateur standard (couvert par la chaîne). Il n'est vérifié que par `offline-installer-check` 9/9 et `model-embed-check` 8/8. |
| **Une machine, un essai** | Toutes les mesures viennent d'un seul PC (Ryzen 7 2700, GTX 1070 8 Go, 16 Go). GPU AMD/Intel/CUDA, ARM, autres Windows : non testés. |
| **Mise à jour** | Éditeur épinglé par sujet partiel ; manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire par le propriétaire ; SmartScreen peut avertir. |
