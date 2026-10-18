> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.3 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `fb58ae7d188b…`, installateur standard signé `11b0b908463f…`, installateur hors-ligne signé `f373366d645c…`, sources `cc822d677e18`)
- **Registre : 28 rapports « courant » = 27 PASS + 1 INCONCLUSIVE** (chaîne `chain83-summary.log` + `ui-calibration`, rattachés à l'exécutable par empreinte). Le non concluant, `ui-agents-routing`, est **INCONCLUSIVE** (14/14 vérifications réussies, 1 « non testé » : le routage a choisi le Qwen3.5 4B, donc la bascule vers le 1,5B n'a pas été exercée dans ce scénario ; la bascule réelle de modèle est couverte par `ui-model-switch` 13/13). Missions avec modèle réel (`ui-mission` 20/20, `ui-mcp` 19/19, `ui-machine` 16/16, import GGUF, GPU, changement de modèle, chat automatique) sur le GPU.
- **Calibration** : `ui-calibration` 16/16 en fenêtre réelle (clic « Calibrer », progression, résultat « 24 couches » pour le Qwen2.5 0,5B à 150,8 jetons/s, effacement) ; ajouté à la chaîne.
- **Installateur** : installation/désinstallation 16/16 ; `update-real` 33/33 ; runtime embarqué 8/8 ; inférence installée PASS. **Hors-ligne** : `offline-installer-check` 9/9 et `model-embed-check` 8/8.
- **Tests automatiques** : `test.ps1` PASS (typecheck ; Vitest 161 réussis ; `cargo test --lib` 537 réussis / 0 échec / 9 ignorés ; auto-test moteur, fenêtre native, fumée UI, écran IA). Le **premier** passage avait signalé 2 échecs (`cargo test` et `startup-check`) qui ne se sont PAS reproduits (`cargo test` seul : 537/0 ; `startup-check` seul : 25/25 ; `test.ps1` relancé : PASS). **Cause non élucidée** ; une interférence avec des opérations en parallèle sur le poste est probable mais non démontrée.
- **Mesures de configuration** (Ryzen 7 2700, GTX 1070 8 Go) : Qwen3.5 4B 32 couches 37,6 jetons/s ; Qwen2.5 1,5B 28 couches 101 jetons/s ; Qwen2.5 0,5B 24 couches 160 jetons/s ; qualité du banc maison INCHANGÉE par rapport au réglage prudent (mêmes scores par classe) ; `-ub 512` déjà optimal ; cache de préfixe : un ajout en fin de conversation ne relit que 13 jetons sur 1 997.
- **Qwen3-30B-A3B 2 bits (expérimental)** : téléchargé par l'application (SHA-256 vérifié), démarré par le planificateur sous la garde (`--n-cpu-moe`), 15,7 jetons/s, RAM résidente ≈ 4 Go, VRAM ≈ 7 Go. Premier essai échoué (plafond de mémoire engagée) puis corrigé ; un essai a été refusé par la garde (RAM trop proche de la limite), comme prévu.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Calibration automatique après un vrai téléchargement** | Le déclenchement automatique n'est couvert que par tests unitaires ; aucun téléchargement n'a été lancé depuis l'interface pour le prouver en fenêtre réelle. La calibration manuelle l'est. |
| **Modèle de prédiction** | Approximation linéaire (écart < 10 % sur le 4B, < 15 % sur Mistral 7B à partir de 2 mesures extrêmes). N'entre dans AUCUNE décision de sécurité ; la charge GPU n'est pas prédite. |
| **30B-A3B** | Expérimental. Lecture du prompt ≈ 30-40 jetons/s : les missions longues sont inutilisables ; qualité mesurée seulement sur le petit banc maison ; une seule machine ; 10 Go à télécharger. |
| **Regroupement d'agents (`-np N`)** | MESURÉ (×1,6 de débit total à 4 agents) mais NON intégré : l'application exécute toujours les agents en série. |
| **Garde GPU : durée tolérée** | Charge GPU soutenue 10 s avant interruption ; un prompt de ≈ 3 600 jetons ou plus d'un seul bloc dépasse ce budget sur ce PC (préremplissage ≈ 365 jetons/s). Le choix de la durée est à valider. |
| **Qualité mesurée** | Banc maison (3 à 7 essais par classe, un tirage à température 0, modèles Qwen) : aucune garantie sur des tâches plus difficiles. |
| **Mémoire engagée (Job Windows)** | Mesurée pour le Qwen3.5 4B et le 30B-A3B seulement ; pour les autres, règle prudente. |
| **Scripts Windows** | Simulation par défaut ; leur application (administrateur) n'a pas été exécutée par cette livraison. L'écriture de la télémétrie reste refusée dans le script automatique (script autonome fourni). |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable qu'il contient (`2f355151aac3…`) est DIFFÉRENT de celui de l'installateur standard (`fb58ae7d188b…`, couvert par la chaîne). Il n'est vérifié que par `offline-installer-check` 9/9 et `model-embed-check` 8/8. |
| **Une machine, un essai** | Toutes les mesures viennent d'un seul PC. GPU AMD/Intel/CUDA, ARM, autres Windows : non testés. |
| **Mise à jour** | Éditeur épinglé par sujet partiel ; manifeste non signé ; pas de retour arrière automatique des binaires. Points de la revue de sécurité non corrigés. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire par le propriétaire ; SmartScreen peut avertir. |
