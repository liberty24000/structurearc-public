> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.2.1 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 64 : **31 rapports « courant » = 28 PASS + 3 non-PASS conservés**. Les trois ont ensuite un rejeu PASS plus récent :
- `ui-task-states` INCONCLUSIVE 14/15 : premier essai, avec une ligne « non testé » (reprise après redémarrage) retirée du scénario ensuite ; rejeu PASS 14/14.
- `ui-model-switch` FAIL 12/13 : un échantillon CPU à 81,6 % sur 72 dans la chaîne complète (plafond 80 %) ; la cause n'est PAS établie (hypothèse : charge extérieure pendant la chaîne) ; rejeu seul PASS 13/13, CPU max 47 %.
- `runtime-embed` FAIL 4/8 dans la chaîne (déjà vu au build 63) : le runtime était bien extrait mais le test ne retrouvait pas sa ligne dans le journal partagé de %TEMP% ; script de test corrigé (journal dédié) ; rejeu PASS 8/8. La cause exacte des échecs passés reste une hypothèse.

`test.ps1` : 1re exécution FAIL (erreur de lien Windows `os error 1117`), 2e FAIL (un test de limite de connexions et le contrôle S4 du démarrage, tous deux sensibles au timing sous charge), 3e PASS global : 445 tests Rust, vitest, contrôles de démarrage. Le test de connexions sera rendu robuste en V1.2.2.

## Prouvé sur le build 64 (V1.2.1)
- **États de tâche (fenêtre réelle) `ui-task-states` 14/14** : « prête » affichée, vérification d'une tâche non terminée REFUSÉE, plan forgé sans statut « vérifiée » conservé, clic réel sur le bouton de vérification, annulation, fichiers du projet inchangés.
- **Matrice de compatibilité** : 2 modèles listés, verdict de la machine, aperçu de routage affichés dans l'écran IA.
- Installateur 16/16 ; agents 18/18 ; terminal autonome 17/17 ; routage 17/17 ; import GGUF 16/16 ; GPU Vulkan 14/14 ; HTTPS réseau local 20/20 ; zone de notification 11/11 (+ 9/9) ; runtime embarqué 8/8 ; référence, Office, terminal, modifications, i18n, web, compactage, chat modes : PASS.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). |
| **HTTPS depuis un autre appareil** | Testé avec un client réseau sur la même machine seulement. |
| **Reprise après redémarrage** | Couverte par un test unitaire ; non rejouée avec un vrai redémarrage. |
| **Fiabilité du petit modèle** | Il n'émet pas toujours l'appel d'outil demandé ; sous forte charge la garde refuse ou interrompt le modèle (voulu). |
| **Modèles** | 2 modèles livrés ; autres par import local après test de démarrage. Mémoire/VRAM : estimations. |
| **GPU** | NVIDIA via Vulkan seulement ; AMD, Intel, CUDA non testés. |
| **IA hors-ligne** | Le modèle n'est pas dans l'installateur. |
| **Signature, mises à jour** | Installateur NON signé (signature prévue en V1.6) ; pas de mise à jour automatique. |
| **Traductions** | Non relues par des natifs ; textes récents en français et anglais, anglais ailleurs. |

## Non implémenté (voir `docs/VERSIONS.md`)
Multi-projets en lecture seule, contrats (V1.2.2) ; catalogue large (V1.3) ; capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4) ; MCP (V1.5) ; mise à jour et signature (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
