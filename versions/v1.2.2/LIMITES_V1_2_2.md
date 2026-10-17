> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.2.2 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 66 : **36 rapports « courant » = 25 PASS + 11 non-PASS conservés**.
- **5 INCONCLUSIVE « modèle non démarré » et 6 FAIL (un échantillon CPU ≥ 80 % sur 11 à 33)** : première passe de la chaîne faite alors que l'application ChatGPT de bureau occupait ≈ 1,7 cœur au repos et que la RAM libre n'était que de ≈ 4,5 Go (la garde refuse alors de démarrer le modèle : comportement voulu). Les scénarios concernés ont été rejoués après la fermeture de cette application : **tous PASS, CPU max 35 à 47 %**. La charge ambiante est une cause **mesurée** (CPU au repos 10–81 % avant, 2–9 % après), pas une hypothèse.
- `test.ps1` : PASS global (469 tests Rust, vitest, démarrage, fenêtre réelle).

## Prouvé sur le build 66 (V1.2.2)
- **Contrats et projets liés (fenêtre réelle) `ui-contracts-links` 35/35** : contrat non conforme refusé ; auto-acceptation impossible ; limites de vérification à approuver ; rupture de version refusée sans version majeure ; squelette affiché sans rien écrire ; aucune lecture d'un autre projet sans liaison explicite, même avec une autorisation dans la cible ; lecture sous les droits de la cible ; secret masqué ; sens unique ; audit des deux côtés sans contenu ; arrêt d'urgence.
- Tests Rust : moteur de contrats (10), liaisons (7), outils de chat sur projet lié (2), module de mise à jour (4 dont sauvegarde SQLite en mode WAL), refus des commandes de mise à jour depuis le mode web.
- Installateur 16/16 **sur le fichier non signé et sur la copie signée** (signature Authenticode `Valid`, horodatée).
- États de tâche 14/14 ; agents 18/18 ; routage 17/17 ; terminal autonome 17/17 ; import GGUF 16/16 ; GPU 14/14 ; changement de modèle 13/13 ; HTTPS réseau local 20/20 ; zone de notification 11/11 (+ 9/9) ; runtime embarqué 8/8.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Mise à jour réelle** | NON testée sur Windows (installation → mise à jour → conservation de la configuration) ; seul le téléchargement vérifié et la sauvegarde sont testés. Aucune signature du manifeste ni activation/rollback. La vérification s'exécute à l'ouverture de Paramètres SI une adresse de manifeste est configurée ; sans adresse, aucun accès réseau. |
| **Signature** | Seul l'**installateur** est signé ; l'application installée (`structurearc.exe`) ne l'est pas encore. |
| **Modèle et projets liés** | Le modèle 1,5B n'a pas utilisé l'outil `linked_read` lors de l'essai (observation, pas un test) ; les outils sont prouvés par des tests avec un faux serveur de modèle. |
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). |
| **HTTPS depuis un autre appareil** | Testé avec un client réseau sur la même machine seulement. |
| **Reprise après redémarrage** | Couverte par un test unitaire ; non rejouée avec un vrai redémarrage. |
| **Modèles** | 2 modèles livrés ; autres par import local. Mémoire/VRAM : estimations. |
| **GPU** | NVIDIA via Vulkan seulement ; AMD, Intel, CUDA non testés. |
| **IA hors-ligne** | Le modèle n'est pas dans l'installateur. |
| **Traductions** | Non relues par des natifs ; textes récents en français et anglais. |

## Non implémenté (voir `docs/VERSIONS.md`)
Catalogue large (V1.3) ; capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4) ; MCP (V1.5) ; mise à jour complète (signature du manifeste, activation, rollback) et signature de l'application (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
