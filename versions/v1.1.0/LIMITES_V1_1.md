> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.1.0 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 62 : **32 rapports « courant » = 24 PASS + 8 non-PASS**, tous conservés dans `preuves/rapports` :
- `ui-tray` FAIL ×3 : mon test regardait une fenêtre interne invisible et concluait à tort ; corrigé (`scripts/lib/win-visible.ps1`), puis `ui-tray` 11/11 PASS et `ui-tray --off` 9/9 PASS.
- `runtime-embed` FAIL ×1 : **disque plein** (0,7 Go libre) ; après nettoyage d'un cache de compilation, 8/8 PASS.
- `ui-chat-auto` INCONCLUSIVE ×2 et FAIL ×2 : le modèle n'émet pas toujours l'appel d'outil demandé ; deux essais ont subi une surcharge de la machine (RAM > 80 % causée par d'autres applications) et la garde a interrompu le modèle. **Le dernier essai ne passe pas** et un essai suivant avec le petit modèle a été refusé par la garde (mémoire insuffisante à cet instant).

## Prouvé sur le build 62 (V1.1.0)
- `test.ps1` : verdict global PASS (typecheck, vitest, scripts, **431 tests Rust**, échec de démarrage explicite, auto-test moteur, fenêtre native, smoke UI, écran IA).
- Fenêtre réelle, PASS : routage 17/17 (bascule réelle), modèle 12/12, référence 34/34, Office 16/16, terminal 21/21, modifications 19/19, i18n 14/14, web 25/25, agents 24/24, compactage 19/19, chat modes 19/19, **import GGUF 16/16**, **GPU Vulkan 14/14**, **changement de modèle en pleine génération 13/13**, **HTTPS réseau local 20/20** (client réseau sur l'adresse privée de la machine, empreinte du certificat identique à celle affichée), **zone de notification 11/11** (+ 9/9 sans l'option), installateur 16/16, runtime embarqué 8/8, inférence installée PASS.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Terminal autonome (mode Auto) sur CE build** | Moteur : exécution, audit, refus des commandes sensibles, mode manuel, arrêt d'urgence prouvés par `real_tool_calling` (cargo) et par `ui-chat-auto` 17/17 PASS sur le build 61. Sur le build 62, `ui-chat-auto` donne INCONCLUSIVE (17/17 vérifications réussies, 2 NON TESTÉ : le modèle n'a pas émis d'appel d'outil pour la commande sensible ni en mode manuel), puis FAIL sous surcharge. **Verdict honnête : non concluant sur ce build.** |
| Qualité du petit modèle | Il n'émet pas toujours l'appel d'outil demandé ; 6/6 réponses correctes après la reformulation (n = 6, faible échantillon). |
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). Aucun test ailleurs. |
| **HTTPS depuis un autre appareil** | Testé avec un client réseau SUR la machine (adresse privée), pas depuis un téléphone ou un autre PC. |
| **Modèles** | 2 modèles livrés (Qwen2.5 0,5B et 1,5B Q4_K_M) ; autres par import local après test de démarrage. |
| **GPU** | NVIDIA via Vulkan seulement ; AMD, Intel, CUDA non testés ; mesure de débit (13 → 83 jetons/s) faite hors fenêtre, une exécution. |
| **IA hors-ligne** | Le modèle n'est pas dans l'installateur : premier démarrage de l'IA = téléchargement ou fichier GGUF déjà présent. |
| **Signature, mises à jour** | Installateur non signé ; pas de mise à jour automatique. |
| **Traductions** | Non relues par des natifs (cinq textes de limites rédigés par l'assistant, darija en lettres latines surtout). |
| **Machine très chargée** | Si la RAM dépasse le seuil préventif, l'IA refuse de démarrer ou s'interrompt : c'est voulu, mais cela peut empêcher l'usage tant que d'autres applications occupent la mémoire. |

## Non implémenté (prévu dans `docs/VERSIONS.md`)
MCP, OAuth intégré, capture d'écran/OCR, souris/clavier, installation de logiciels, profil « tout activé », agents/compétences créés par le chat, espace multi-projets, mise à jour automatique, signature de code. Linux, Raspberry Pi et processeurs sans AVX2 sont **hors périmètre** de la V2 (décision du propriétaire : « pas encore »).

## ADDENDUM (ajouté après l'audit de Codex, le même jour) — terminal autonome rejoué sur LE MÊME exécutable
Après libération de mémoire sur la machine (RAM à ≈ 50 % au lieu de ≈ 70 %), le scénario `ui-chat-auto` (modèle 0,5B, nouvelle conversation pour chaque question sensible ou manuelle) a été rejoué **3 fois de suite sur l'exécutable de la V1.1.0** (`a138b8a38390…`, hash relevé dans chaque rapport) : **3 PASS 17/17, 0 NON TESTÉ**, aucun échantillon de charge ≥ 80 %. Rapports : `preuves/rapports-complementaires/` (runs 20261017162001-50428, 20261017162111-27528, 20261017162209-74732).
Ces rapports ne sont PAS dans le registre `build-registry.json` (les sources ont été modifiées après la publication — un correctif du message système — donc `publish-build.mjs` refuse de les rattacher) : le registre du build 62 continue d'afficher les FAIL/INCONCLUSIVE d'origine, qui restent valables pour les essais sous surcharge. **Lecture honnête : le terminal autonome fonctionne de façon reproductible quand la machine dispose de mémoire ; sous forte charge la garde de ressources interrompt ou refuse le modèle (comportement voulu).**
Mesure complémentaire (`real_tool_calling`, 0,5B, conversation neuve, 6 essais par cas) : appel d'outil émis 6/6 pour la lecture seule, 6/6 pour la commande sensible et 6/6 pour le mode manuel, avec l'ancien comme avec le nouveau message système : **aucun gain mesuré** du correctif de message ; les cas « non testés » viennent de la longueur de la conversation et de la charge de la machine.
