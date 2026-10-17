> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.2.0 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 63 : **27 rapports « courant » = 26 PASS + 1 FAIL** (`runtime-embed` dans la chaîne, 4/8, cause non établie ; rejoué seul : 8/8 PASS). Toutes les dernières exécutions par type sont PASS. La première exécution de `test.ps1` a échoué à cause de l'erreur de lien transitoire Windows `os error 1117` ; rejouée : PASS global.

## Prouvé sur le build 63 (V1.2.0)
- **Agents (fenêtre réelle) : 18/18** — création par le formulaire, fichier dans le projet, identifiant réservé refusé, mémoire sans le secret, isolation entre deux projets, **proposition faite par le modèle 1,5B** (outil `propose_agent`) qui ne crée rien tant que non approuvée, texte exact affiché avant le clic, approbation, audit sans contenu, suppression (agent + mémoire), arrêt d'urgence.
- Terminal autonome `ui-chat-auto` 17/17 ; routage 17/17 ; import GGUF 16/16 ; GPU Vulkan 14/14 ; changement de modèle 13/13 ; HTTPS réseau local 20/20 ; zone de notification 11/11 (+ 9/9) ; installateur 16/16 ; runtime embarqué 8/8 ; référence, Office, terminal, modifications, i18n, web, agents (plan), compactage, chat modes : PASS.
- `test.ps1` : PASS global, 443 tests Rust, 135 Vitest.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). |
| **HTTPS depuis un autre appareil** | Testé avec un client réseau sur la même machine, pas depuis un téléphone ou un autre PC. |
| **Fiabilité du petit modèle** | Il n'émet pas toujours l'appel d'outil demandé (6/6 dans une conversation neuve, des cas non testés dans de longues conversations) ; sous forte charge la garde refuse ou interrompt le modèle (voulu). |
| **Modèles** | 2 modèles livrés ; autres par import local après test de démarrage. |
| **GPU** | NVIDIA via Vulkan seulement ; AMD, Intel, CUDA non testés. |
| **IA hors-ligne** | Le modèle n'est pas dans l'installateur. |
| **Signature, mises à jour** | Installateur non signé ; pas de mise à jour automatique. |
| **Traductions** | Non relues par des natifs ; les textes récents sont en français et en anglais, les autres langues affichent l'anglais. |
| **Agents** | Un agent n'est pas un processus autonome : c'est un rôle appliqué aux tâches d'un plan. Mémoire ajoutée à la main (pas d'écriture automatique par le modèle). |

## Non implémenté (voir `docs/VERSIONS.md`)
États de tâche « vérifiée », reprise après limite de contexte (V1.2.1) ; multi-projets en lecture seule, contrats (V1.2.2) ; catalogue large (V1.3) ; capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4) ; MCP (V1.5) ; mise à jour et signature (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
