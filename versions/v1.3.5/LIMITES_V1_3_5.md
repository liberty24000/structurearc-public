> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.5 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `fb7059f957d7…`, installateur standard signé `4066daf2d084…`, installateur hors-ligne signé `ee74e5b4e1e7…`, sources `12fab378f69f`)
- **Registre : 34 rapports « courant » = 32 PASS + 1 INCONCLUSIVE + 1 FAIL conservé** (chaîne `chain86-summary.log` : 28 PASS, puis rejeux rattachés par empreinte). L'INCONCLUSIVE est `ui-agents-routing` (14/14, 1 « non testé » : le routage a choisi le Qwen3.5 4B, la bascule vers le 1,5B n'a donc pas été exercée ici ; la bascule réelle est couverte par `ui-model-switch` 13/13). Le FAIL est `ui-i18n` dans la chaîne (12/13 : « délai dépassé : arabe après redémarrage ») : cause TROUVÉE et corrigée dans le **script de test** (il relançait l'application avant la fin réelle de l'instance précédente, que la charge de la chaîne retardait ; l'instance neuve se fermait en « second lancement ») ; rejoué 4 fois sur le MÊME exécutable : 14/14 à chaque fois. Le script corrigé n'est pas dans l'empreinte des sources du registre (modifié après le build) ; l'exécutable est identique.
- **Décodage spéculatif par n-grammes** : `ui-agents-parallel` 13/13 en fenêtre réelle avec le Qwen2.5 1,5B ET avec le Qwen3.5 4B (ligne de commande du vrai `llama-server` contenant `--spec-type ngram-simple`, sans `--spec-draft`), mesures au banc `bench-ngram.mjs` (citation ×2,4 sur 4B, ×4,3 sur 0,5B ; génération libre ×1,00).
- **Agents simultanés** : `ui-agents-parallel` : 3 tâches, 1,5B : 28,7 s en série contre 13,2 s en parallèle ; 4B : 39,7 s contre 22,1 s. Plafond de mémoire engagée par emplacement (`guard::ai_memory_limit_bytes_with_slots`, test unitaire : ≥ 8 434 Mo mesurés pour 4 emplacements du 4B).
- **Qualité à 4 agents** : `bench-models.mjs --np=4` : mêmes scores par classe qu'à 1 agent pour les trois modèles (0,5B, 1,5B, 4B).
- **Tests automatiques** : `test.ps1` PASS au **3e passage** (1er : un test d'interface instable, corrigé ; 2e : étapes « binaire obsolète » déclarées PARTIAL parce que l'exécutable a été reconstruit ensuite). Ce 3e passage s'est exécuté sur l'exécutable recompilé par la fabrication de l'installateur hors-ligne (`a96357a1c2cc…` : mêmes sources, ressources embarquées différentes), pas sur l'exécutable de la chaîne (`fb7059f957d7…`) ; `cargo test` 540 réussis / 0 échec / 9 ignorés ; Vitest 163 réussis ; typecheck PASS. Un test d'interface de la calibration (écrit dans cette série de versions) était INSTABLE (lecture d'un état asynchrone sans attente) : corrigé, rejoué 6 fois stable.
- **Installateur** : installation/désinstallation 16/16 ; `update-real` 33/33 ; runtime embarqué ; inférence installée PASS. **Hors-ligne** : `offline-installer-check` 9/9 et `model-embed-check` 8/8.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Gain des n-grammes** | Dépend entièrement de la part de texte recopié : ×1,00 en génération libre (mesuré). Sorties du 4B en « citation » : divergence tardive (caractère 463 sur ≈ 1 150) par rapport à la génération sans spéculation, reproductible, sans dégradation mesurée (5 articles sur 6 recopiés contre 4 sur 6 sans) ; cause supposée : arrondis de la vérification groupée, NON démontrée. Non mesuré sur processeur seul ni avec experts en RAM (désactivé dans ces cas). Trois modèles Qwen, un PC, une série par charge. |
| **Agents simultanés** | Désactivé par défaut (réglage 1). Deux mesures en fenêtre réelle (×2,17 et ×1,79, sorties courtes) et un banc (×1,6 à 4 agents). Agents externes (Claude Code, Codex) toujours en série (pas de budget agrégé). |
| **Qualité multi-agents** | Mesurée sur le petit banc maison seulement (3 à 7 essais par classe, un tirage à température 0, groupes d'items différents, pas N copies du même prompt). |
| **Calibration automatique après un vrai téléchargement** | Couverte par tests unitaires ; la calibration manuelle est prouvée en fenêtre réelle. |
| **30B-A3B (expérimental)** | Lecture du prompt ≈ 30-40 jetons/s : missions longues inutilisables ; qualité mesurée seulement sur le petit banc maison. |
| **Garde GPU : durée tolérée** | Charge GPU soutenue 10 s avant interruption ; un prompt de ≈ 3 600 jetons ou plus d'un seul bloc dépasse ce budget sur ce PC. |
| **Scripts Windows** | Simulation par défaut ; leur application (administrateur) n'a pas été exécutée par cette livraison. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable qu'il contient est DIFFÉRENT de celui de l'installateur standard (couvert par la chaîne). Il n'est vérifié que par `offline-installer-check` et `model-embed-check`. |
| **Une machine, un essai** | Toutes les mesures viennent d'un seul PC (Ryzen 7 2700, GTX 1070 8 Go, 16 Go). GPU AMD/Intel/CUDA, ARM, autres Windows : non testés. |
| **Mise à jour** | Éditeur épinglé par sujet partiel ; manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire par le propriétaire ; SmartScreen peut avertir. |


## Errata (ajoutée le 19 octobre 2026, après la publication de la V1.3.5)

La ligne « **Agents simultanés** » de la section « Prouvé » cite des durées tirées de passages ANTÉRIEURS au build final et non toutes incluses dans les preuves de cette livraison :
- **Qwen2.5 1,5B** : le texte donne « 28,7 s en série contre 13,2 s en parallèle » ; le rapport inclus (`ui-agents-parallel`, exécutable `fb7059f957d7…`, 13/13) donne **28,6 s contre 13,2 s** (×2,17).
- **Qwen3.5 4B** : le texte donne « 39,7 s contre 22,1 s » ; AUCUN rapport inclus dans cette livraison ne porte cette mesure. Elle a été refaite APRÈS la livraison sur le MÊME exécutable `fb7059f957d7…` (13/13, calibration réelle : 32 couches, `--spec-type ngram-simple` dans la ligne de commande réelle) : **39,7 s en série, 22,0 s en parallèle (×1,80)**, rapport `20261019125704-816`, conservé par le titulaire mais non inclus dans le dossier de preuves de la V1.3.5.
Les gains de la section « Prouvé » doivent donc être lus : 1,5B ×2,17 (rapport inclus) ; 4B ×1,8 (mesure postérieure, même exécutable, rapport non inclus). Aucun autre chiffre n'est modifié. Le dossier de livraison reste figé ; les preuves correspondantes seront incluses dans la livraison suivante.
