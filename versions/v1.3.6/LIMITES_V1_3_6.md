> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.6 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `51f5bafb4684…`, installateur standard signé `0b55b477217a…`, installateur hors-ligne signé `ef364afc0d86…`, sources `8de60143d5f4`)
- **Chaîne de vérifications en fenêtre réelle** (`chain88-summary.log`) : 29 PASS + 1 INCONCLUSIVE. L'INCONCLUSIVE est `ui-agents-routing` (14/14, 1 « non testé » : le routage a choisi le modèle déjà chargé, donc aucune bascule n'a été observée). Registre de build : 30 rapports rattachés à ce build par empreinte exacte.
- **Calibration réelle sous la garde de l'application** (`ui-calibration`, un passage chacun) : NeoHorse 1 9B, QwenPaw Flash 9B, Qwopus3.5 9B Coder et Qwen3.5 9B : 16/16 (32 couches sur la carte, ≈ 22-23 jetons/s). **Gemma 4 12B (Q3) : 15/16, FAIL conservé** — la calibration aboutit (48 couches, 11,6 jetons/s) mais le GPU dépasse 80 % pendant 12 échantillons sur 23 (pic 88,6 %), au-dessus du critère strict du scénario (la garde de l'application tolère 95 %).
- **Table de routage** : 2 tests unitaires sur le catalogue embarqué (chaque catégorie vers le modèle désigné, verrou manuel prioritaire, modèle absent ou trop gros jamais forcé) ; `cargo test --lib` 546 réussis, 0 échec ; Vitest 163 réussis.
- **Démarrage** : mesure avant/après (≈ 19,4 Go lus en ≈ 30 s avant correction) ; après correction `ui-calibration` du 9B passe 16/16, CPU max 51,6 % (84,6 % avant).
- **Cache de préfixe** (`bench-prefix-layout.mjs`, 4B, options de l'application) : préremplissage par question 8,3 s → 2,3 s avec 15 outils déclarés (−73 %), sans outils −27 %.
- **Correctif de démarrage explicite** : `ui-import-gguf` 16/16 (échouait 15/16 avant le correctif, cause : calibration automatique en arrière-plan).
- **Installateur** : installation/désinstallation 16/16 ; `update-real` 33/33 ; runtime embarqué ; inférence installée PASS. **Hors-ligne** : `offline-installer-check` 9/9 et `model-embed-check` 8/8.
- **Tests automatiques** : `test.ps1` PASS au **2e passage** (1er passage : `cargo test` en échec parce que l'éditeur de liens de Windows `link.exe` a planté pendant la construction du binaire de test — incident de l'environnement ; `cargo test --lib` relancé seul : 546 réussis, 0 échec). Le 2e passage s'est exécuté sur l'exécutable restauré du build final (`51f5bafb4684…`).

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Le chat ne route pas encore** | La table de préférences sert aux agents et à la commande de choix de modèle ; le chat ne change pas de modèle tout seul (prévu V1.3.7). |
| **Classification de la demande** | Heuristique par mots-clés (français), jamais mesurée : précision inconnue. |
| **Gain du routage** | Simulation hors ligne +5 points (97 % contre 92 %), **surestimée** (mêmes essais pour choisir et mesurer, rechargement de modèle ≈ 8 s non compté). |
| **NeoHorse « recommandé »** | Choix du propriétaire d'après un classement dont l'écart avec le Qwen3.5 4B (92 % contre 91 %) est dans le bruit ; petits jeux de tâches (2 à 5 passages), une seule machine. |
| **Classement des modèles** | Petits jeux (5 à 8 tâches par catégorie), recherche web **simulée**, français seulement, code et contexte long saturés (non discriminants). Chiffres de vitesse : n-grammes actifs. |
| **Gemma 4 12B** | Lent (12,6 jetons/s), 6,1 Go de VRAM, GPU > 80 % à la calibration ; clé de cache de contexte = borne haute documentée, non mesurée. |
| **xLAM-2 8B** | Mesuré mais NON ajouté (licence non commerciale, résultats faibles). |
| **Qwen3.5 9B** | « En évaluation » : calibré 16/16 une fois ; ancien pic CPU de 84,6 % corrigé (cause : relecture des modèles au démarrage), un seul passage après correction. |
| **Cache de préfixe** | Mesure synthétique (4B, 15 outils factices) ; pas mesuré en fenêtre réelle ni sur le 9B ; qualité des réponses avec la nouvelle disposition non rejouée. |
| **Décodage spéculatif par n-grammes** | Gain dépend de la part de texte recopié (×1,00 en génération libre). |
| **Agents simultanés** | Désactivé par défaut. Agents externes (Claude Code, Codex) en série ; les CLI n'ont pas été éprouvées en vrai. |
| **Garde GPU : durée tolérée** | Charge GPU soutenue 10 s avant interruption. |
| **Scripts Windows** | Simulation par défaut ; leur application (administrateur) n'a pas été exécutée. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable qu'il contient est DIFFÉRENT de celui de l'installateur standard. Il n'est vérifié que par `offline-installer-check` et `model-embed-check`. |
| **Une machine, un essai** | Toutes les mesures viennent d'un seul PC (Ryzen 7 2700, GTX 1070 8 Go, 16 Go, **une seule barrette de 16 Go en simple canal**). GPU AMD/Intel/CUDA, ARM, autres Windows : non testés. |
| **Mise à jour** | Éditeur épinglé par sujet partiel ; manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire par le propriétaire ; SmartScreen peut avertir. |
