> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.2.3 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 68 : **27 rapports « courant » = 27 PASS + 0 non-PASS**. Cette fois la chaîne complète est passée du premier coup, machine au repos (l'application ChatGPT de bureau fermée, comme le préconisait le fichier de limites de la V1.2.2) ; les échecs et résultats non concluants des builds précédents restent dans leurs propres dossiers.

## Prouvé sur le build 68 (V1.2.3)
- **Mise à jour réelle `update-real` 33/33** sur une VRAIE installation (dossier isolé) avec un serveur local jouant le dépôt public : l'installateur de départ ET l'exécutable installé sont signés (Authenticode `Valid`, éditeur attendu) ; la bannière apparaît ; un installateur NON signé (même avec le bon SHA-256) est refusé, rien n'est lancé, le fichier est supprimé, aucune sauvegarde n'est faite ; un installateur ALTÉRÉ est refusé ; avec l'installateur signé : la progression passe par la vérification de la signature puis l'installation, l'application se ferme, **l'installateur la relance seul**, le MÊME dossier de données est retrouvé, le projet et le réglage modifiés avant sont conservés, la sauvegarde SQLite est vérifiable, l'application installée reste signée ; la désinstallation est propre.
- **Défaut trouvé par ce test et corrigé** : l'installateur passif restait bloqué sur son sélecteur de langue quand aucune langue n'était mémorisée (installation silencieuse ou ancienne) ; l'installateur mémorise maintenant sa langue et l'application la rétablit avant de lancer la mise à jour (cas testé : valeur supprimée avant la mise à jour).
- Tests Rust (13 sur la mise à jour : signature `Valid` + éditeur épinglé, rejet réel par Windows d'un fichier non signé et d'un fichier signé par Microsoft, ordre « vérifier avant de sauvegarder », 3 sauvegardes conservées, arguments de l'installateur) ; interdiction des commandes de mise à jour depuis le navigateur du mode web.
- `test.ps1` PASS global (477 tests Rust, 147 Vitest). Installateur 16/16 ; comparaison octet par octet de l'exécutable installé avec celui du build : marqueur Tauri, en-tête de signature et bloc de signature expliqués, aucun autre octet différent.
- Contrats et projets liés 35/35 ; états de tâche 14/14 ; agents 18/18 ; routage 17/17 ; terminal autonome 17/17 ; import GGUF 16/16 ; GPU 14/14 ; changement de modèle 13/13 ; HTTPS réseau local 20/20 ; zone de notification 11/11 (+ 9/9) ; runtime embarqué 8/8.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Changement de version observé** | Le test annonce la version suivante (patch + 1) mais sert l'installateur de la version INSTALLÉE : la mécanique est réelle, le passage d'un numéro de version à un autre n'est pas observé. À observer à la première vraie mise à jour entre deux versions publiées. |
| **Mise à jour via Internet** | Testée avec un serveur local (HTTP sur 127.0.0.1, mode test réservé aux dossiers de données alternatifs) ; pas encore depuis le dépôt public réel. Le manifeste public existe et répond. |
| **Anciennes versions** | Les versions ≤ 1.2.2 ne contiennent pas la mise à jour : installer la 1.2.3 une première fois à la main. |
| **Retour arrière** | La base est sauvegardée (3 dernières) mais les binaires ne sont pas restaurés automatiquement ; la version précédente se réinstalle depuis les Releases du dépôt public. Pas de signature du manifeste lui-même (la confiance repose sur HTTPS + signature de l'éditeur de l'installateur). |
| **Page de licence** | Compilée dans l'installateur ; son affichage en mode interactif n'a pas été testé (les tests utilisent les modes silencieux et passif). |
| **Registre après désinstallation** | Comportement voulu de l'installateur : l'emplacement d'installation et la langue restent dans `HKCU\Software\StructureArc` tant que « supprimer les données de l'application » n'est pas coché (pour qu'une réinstallation retrouve ses repères). Ce n'est pas une clé vide ni un défaut ; cocher l'option les supprime. (Rectifié après la livraison : la première version de ce fichier parlait à tort d'un résidu à corriger.) |
| **Certificat** | Il affiche encore l'ancienne ville (Sigean) ; type « Open Source Developer » à vérifier avec Certum ; SmartScreen peut avertir tant que le certificat n'a pas de réputation. L'éditeur est reconnu par son nom et l'autorité de certification, pas par l'empreinte du certificat (renouvellement possible). |
| **Détection automatique** | Activée par défaut : au plus une requête HTTPS par 24 h au dépôt public (adresse IP vue par GitHub), aucune donnée personnelle ; désactivable dans Paramètres. |
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). |
| **Autres limites** | HTTPS depuis un autre appareil, GPU AMD/Intel/CUDA, modèles (2 livrés), IA hors-ligne, traductions non relues : voir `LIMITES_V1_2_2.md`. |

## Non implémenté (voir `docs/VERSIONS.md`)
Catalogue large (V1.3) ; capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4) ; MCP (V1.5) ; signature du manifeste, activation atomique et retour arrière des binaires (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
