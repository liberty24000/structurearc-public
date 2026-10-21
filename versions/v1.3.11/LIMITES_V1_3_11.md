> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.11 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `5321bcaf6218…`, installateur standard signé `ea80b00f2e49…`, installateur hors-ligne signé `a9095ffeb58b…`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-summary.log`, 36 scénarios dont le nouveau `ui-resume`) : 31 PASS au premier passage. Trois échecs expliqués et relancés (`rerun-1311.log`) : `ui-i18n` (délai « arabe après redémarrage », **14/14** seul) et `runtime-embed-check` (**8/8** seul) : instables dans la chaîne, pas un défaut constaté du produit ; `ui-gpu` attendait encore l'ancienne limite de 95 % : critère porté à 100 % (défaut de la 1.3.10), puis **14/14** — mais lors de cette relance aucune charge GPU n'a été mesurée (max 0 %), ce contrôle est donc faible. Deux INCONCLUSIVE déclarés : `ui-agents-routing` (routage automatique non observé) et `ui-selfimprove-real` (15/15 vérifications mais le petit modèle n'a rien écrit).
- **Tests automatiques** : `test.ps1` verdict global **PASS au 2e essai** (le 1er a échoué à la COMPILATION des tests Rust : `link.exe` « erreur de périphérique d'E/S 1117 », pas un test) : typecheck, vitest, scripts node, **cargo test 645 réussis / 0 échec / 11 ignorés**, auto-test du moteur, fenêtre native, test de fumée, écran IA 16/16.
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid), `offline-installer-check` 9/9 et `model-embed-check` 8/8. La première fabrication hors-ligne a échoué à la signature (session SimplySign expirée pendant la nuit) ; refaite le matin après reconnexion du propriétaire.
- **Reprise de projet** (`.structurearc/`) : `ui-resume` 15/15 en fenêtre réelle (restauration des conversations et de la définition, aucune autorisation restaurée, fichier invalide ignoré, sauvegarde après un échange, réouverture sans doublon) + 4 tests unitaires. Comble la réserve de la 1.3.10.
- **Fenêtre de contexte, 7 outils, reprise après arguments non JSON, lecture XML, pagination limitée** : tests unitaires ; en fenêtre réelle, lors de l'observation n°6, les erreurs visées (`HTTP 400 exceeds context`, tour perdu sur `HTTP 500 arguments`) ne sont plus apparues — mais cela n'a PAS suffi à faire aboutir une tâche.

## Auto-développement : ce qui a été réellement observé cette nuit (6 observations libres, Qwen3.5 4B)
| N° | Build | Ce que le modèle a fait | Tâche finie ? |
|---|---|---|---|
| 1, 2 | 1.3.10 / 1.3.11 | Relit en boucle `NEXT_STEPS.md` et `IMPLEMENTATION_LOG.md` (mon prompt le lui demandait) ; aucun code | non |
| 3 | 1.3.11 | Choisit la bonne tâche, écrit `scripts/lib/ram.test.mjs` ; `node --test` échoue ; 2 tours coupés par des arguments non JSON | non |
| 4 | 1.3.11 | Écrit un test faux (entier attendu, fonction asynchrone non attendue) ; 2 tours coupés par un dépassement de fenêtre | non |
| 5, 6 | 1.3.11 (fenêtre corrigée, 7 outils) | Aucun code ; répond qu'il ne peut pas lire des « extraits tronqués » alors que les lectures ont réussi | non |

Dans les six cas, les 10 invariants de sécurité ont tenu (dépôt d'origine intact, aucun chemin protégé touché, copie jetée, aucune branche résiduelle). **Conclusion : avec un modèle 4B à fenêtre de 8192 jetons, le logiciel ne se développe pas seul.** Un modèle plus grand (Qwen3.5 9B, autorisé) n'est pas téléchargé sur ce PC. Traces complètes : `preuves/rapports/*ui-selfimprove-free*` et `build/logs/runs/<id>/trace.json`.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Auto-amélioration** | Voir ci-dessus : aucune tâche terminée par le modèle seul ; prouvée uniquement sur un dépôt temporaire avec un bug trivial (scénarios guidés). |
| **Filet de température GPU** | Toujours validé par simulation seulement ; aucune montée en température réelle de la GTX 1070 ; sans `nvidia-smi` lisible, pas de filet. |
| **Journaux Windows** | 3 écrans bleus 0xD1 en octobre (pilote non identifié, vidages non analysés), 9 « blocs défectueux » sur le SSD système ; `link.exe` erreur d'E/S 1117 revenue cette nuit à la compilation. Aucun lien avec la charge GPU démontré ni exclu. **Sauvegardez le disque système.** |
| **Scénarios instables** | `ui-i18n` et `runtime-embed-check` ont échoué une fois dans la chaîne puis passé seuls : cause non élucidée (délai / charge de la machine). |
| **Routage automatique du chat** | Aucune bascule observée en fenêtre réelle ; classification par mots-clés, précision jamais mesurée. |
| **Gain du subconscient** | Mesuré par simulation seulement. |
| **Sauvegarde du cache par conversation, ordonnanceur d'emplacements** | Toujours non faits. |
| **Hérité** | Une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go) ; GPU AMD/Intel/CUDA et ARM non testés ; agents simultanés désactivés par défaut. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable contenu est DIFFÉRENT de celui de l'installateur standard ; vérifié par `offline-installer-check` et `model-embed-check` seulement. |
| **Mise à jour** | Manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire ; SmartScreen peut avertir. |
