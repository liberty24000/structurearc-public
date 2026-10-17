> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.2.4 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`. Registre du build 69 : **29 rapports « courant » = 29 PASS + 0 non-PASS**. Premier passage de `test.ps1` : échec de compilation de deux tests d'intégration par l'erreur Windows `os error 1117` (erreur d'entrée/sortie du disque au lien, déjà vue sur les builds 63 et 64, aucun test en échec) ; journal conservé dans `preuves/` ; second passage : PASS global.

## Prouvé sur le build 69 (V1.2.4)
- **Mise à jour réelle ENTRE DEUX VERSIONS PUBLIÉES** (`update-real --to=`, serveur local jouant le dépôt public) : on installe l'installateur 1.2.3 **tel que publié** (signé), on le met à jour vers le 1.2.4 construit ici : installateur non signé et altéré refusés ; mise à jour en un clic ; fermeture ; relance par l'installateur ; **« Applications installées » passe de 1.2.3 à 1.2.4** ; même dossier de données ; projet et réglage conservés ; sauvegarde SQLite vérifiable ; exécutable installé signé ; désinstallation propre — 33/33.
- Même scénario en mode ordinaire (installateur de la version installée annoncé « patch + 1 ») : 33/33 dans la chaîne.
- Décision « mise à jour réussie / n'a pas abouti / rien » : tests unitaires (8 cas : réussie, trop tôt pour conclure, échec après 10 minutes, mise à jour par une autre voie, premier démarrage, retour arrière, trace périmée) ; bannières testées (Vitest).
- `test.ps1` PASS global au second passage (478 tests Rust, 149 Vitest). Installateur 16/16 (octets de l'exécutable expliqués : marqueur Tauri + signature). Contrats et projets liés 35/35 ; états de tâche 14/14 ; agents 18/18 ; routage 17/17 ; terminal autonome 17/17 ; import GGUF 16/16 ; GPU 14/14 ; changement de modèle 13/13 ; HTTPS réseau local 20/20 ; zone de notification 11/11 (+ 9/9) ; runtime embarqué 8/8.

## Addendum (18 oct. 2026, après la publication) — mise à jour de bout en bout via Internet
- `update-internet --from-version=1.2.3` (rapport `preuves/rapports/20261017223731-43900__update-internet.result.json`) : **18/18** avec les fichiers RÉELLEMENT publiés, sans serveur local ni mode test : l'installateur 1.2.3 est téléchargé depuis la Release publique (SHA-256 identique à `releases.json`, signé), installé, puis l'application lit le VRAI manifeste public, télécharge l'installateur 1.2.4 sur GitHub, vérifie sa signature, se ferme, est relancée par l'installateur ; « Applications installées » passe de **1.2.3 à 1.2.4** ; même dossier de données ; projet et réglage conservés ; sauvegarde SQLite faite ; exécutable installé signé ; ensuite « vous avez la dernière version » ; désinstallation propre.
- Observation réelle : le fichier `update/latest.json` est servi par le cache de GitHub (`raw.githubusercontent.com`, `max-age=300`) ; juste après une publication, certains points d'accès annoncent encore l'ancienne version pendant quelques minutes (constaté pendant ce test). La détection d'une nouvelle version peut donc avoir jusqu'à environ 5 minutes de retard ; sans conséquence.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Mise à jour via Internet** | **Prouvée après la publication** (addendum ci-dessous). |
| **Message « mise à jour réussie »** | Non observable pour la transition 1.2.3 → 1.2.4 (la 1.2.3 ne mémorise ni sa version ni la mise à jour lancée) ; observable à partir de la 1.2.4 (prochaine mise à jour). Le code est prouvé par tests unitaires et Vitest, pas par une vraie mise à jour. |
| **Retour arrière** | La base est sauvegardée (3 dernières) mais les binaires ne sont pas restaurés automatiquement ; la version précédente se réinstalle depuis les Releases publiques. Pas de signature du manifeste lui-même. |
| **Registre après désinstallation** | Voulu par l'installateur : l'emplacement et la langue restent tant que « supprimer les données de l'application » n'est pas coché. |
| **Page de licence** | Compilée dans l'installateur ; affichage interactif non testé (tests en modes silencieux et passif). |
| **Certificat** | Affiche encore l'ancienne ville (Sigean) ; type « Open Source Developer » à vérifier avec Certum ; SmartScreen peut avertir tant que le certificat n'a pas de réputation ; l'éditeur est reconnu par son nom et l'autorité de certification (renouvellement possible). |
| **Détection automatique** | Activée par défaut : au plus une requête HTTPS par 24 h au dépôt public, aucune donnée personnelle ; désactivable. |
| **Autre ordinateur** | UN seul PC testé (Windows 11, 16 Go, GTX 1070). |
| **Autres limites** | HTTPS depuis un autre appareil, GPU AMD/Intel/CUDA, modèles (2 livrés), IA hors-ligne, traductions non relues : voir `LIMITES_V1_2_2.md` (dans les versions précédentes). |

## Non implémenté (voir `docs/VERSIONS.md`)
Catalogue large (V1.3) ; capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4) ; MCP (V1.5) ; signature du manifeste, activation atomique et retour arrière des binaires (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
