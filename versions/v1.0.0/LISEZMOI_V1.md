> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.0.0

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, agents externes).

> Cette V1 est une **première version fonctionnelle**, pas un produit fini. Le fichier `LIMITES_V1.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.0.0_x64-setup.exe` | **Installateur Windows** (à lancer) |
| `structurearc.exe` | Exécutable seul (pour vérification ; l'installateur contient le même) |
| `SHA256SUMS.txt` | Empreintes SHA-256 pour vérifier les fichiers |
| `LISEZMOI_V1.md` | Ce guide |
| `LIMITES_V1.md` | Ce qui est prouvé, ce qui ne l'est pas, ce qui manque |
| `FEUILLE_DE_ROUTE_V2.md` | Ce qui viendra ensuite |
| `docs/` | Exigences (avec preuves), compatibilité, modèle de menaces, architecture, matrice des modèles |
| `preuves/` | Rapports de test réels rattachés à CE build (JSON), manifeste de build, liste des fichiers sources suivis |

## Installer

1. Double-cliquez sur `StructureArc_1.0.0_x64-setup.exe`. Choisissez la langue (18 disponibles).
2. L'installation se fait **pour votre compte uniquement** : pas de droits administrateur. Elle ajoute un raccourci dans le menu Démarrer.
3. Windows SmartScreen peut afficher un avertissement : **l'installateur n'est pas signé** (aucun certificat de signature de code n'est configuré). Vérifiez l'empreinte SHA-256 avec `SHA256SUMS.txt` avant de continuer.
4. Au premier lancement, ouvrez un dossier de projet : StructureArc l'indexe **en lecture seule**. Vos fichiers ne sont jamais modifiés sans un changement que vous approuvez.

Désinstaller : Paramètres Windows → Applications. Vos données (`%APPDATA%\app.structurearc.desktop\`) sont **conservées** ; supprimez ce dossier à la main si vous voulez tout effacer.

## Activer l'IA locale

Le moteur d'inférence (`llama.cpp`, CPU) est **déjà dans l'installateur**. Il manque le modèle :

1. Ouvrez l'écran **IA / Modèles**.
2. Cochez le consentement puis lancez l'assistant : il télécharge un petit modèle (Qwen2.5 0,5B ou 1,5B, de 0,5 à 1,1 Go) depuis Hugging Face, **vérifie sa taille et son SHA-256**, puis le démarre. **Internet est nécessaire pour cette étape uniquement.**
3. Si votre ordinateur est trop chargé en mémoire, l'application **refuse de démarrer le modèle** et vous dit pourquoi (c'est voulu : plafond de sécurité). Fermez des applications et réessayez.

Vous pouvez aussi **importer un modèle GGUF déjà présent sur votre disque** (carte « Importer un modèle GGUF ») : l'application lit l'en-tête, calcule l'empreinte, puis exige un test de démarrage réel (« Vérifier la compatibilité ») avant d'autoriser son usage.

### Plafonds de ressources

- **Processeur et mémoire (RAM) : 80 %** de la machine, arrêt préventif 5 points avant, jamais d'arrêt d'un autre programme.
- **Carte graphique : 95 % par défaut**, réglable de 50 à 95 % dans Paramètres.
- Ce sont des **politiques de sécurité mesurées**, pas des garanties physiques : un pic très bref ou la charge d'autres applications ne peut pas être exclu.

### Accélération par carte graphique (optionnelle)

Si votre carte est détectée avec sa mémoire vidéo, l'écran IA propose un **runtime GPU Vulkan** (≈ 32 Mo, source officielle `llama.cpp`, SHA-256 affiché). Il n'est téléchargé qu'avec votre accord. Mesure sur une GTX 1070 (une exécution, Qwen2.5 1,5B) : 13 → 83 jetons/s. Ce n'est PAS testé sur d'autres cartes.

## Le chat

- Un chat **par projet**, conversations à gauche.
- **Mode Auto / Manuel** et **Effort** (faible / moyen / élevé) au-dessus de la zone de saisie ; **Modèle** pour changer de modèle (la génération en cours est annulée proprement).
- Commandes : `/mode auto|manuel`, `/effort faible|moyen|élevé`, `/compact`, `/stop`, `/aide`.
- **Auto** : le modèle peut lancer des commandes du terminal **si** vous avez accordé la permission « terminal » au projet ; une commande sensible n'est **jamais** exécutée sans votre confirmation. **Manuel** : les commandes sont seulement proposées.

## Permissions et sécurité

- Tout est **désactivé par défaut** : fichiers, terminal, web, Word/Excel… s'activent projet par projet, avec périmètre, niveau, expiration, révocation et **journal d'audit** (sans contenu).
- **Arrêt d'urgence** : coupe tout accès outil immédiatement.
- Les secrets connus (clés, jetons) sont masqués dans les sorties, journaux et contextes.

## Version web

Icône StructureArc dans la zone de notification (en bas à droite) → **Ouvrir la version web** : l'interface s'ouvre dans votre navigateur, sur **127.0.0.1 uniquement**, avec un jeton à usage unique.
Accès depuis le **réseau local** : Paramètres → « Accès depuis le réseau local (HTTPS) » (désactivé par défaut, consentement requis, certificat auto-signé généré sur place ; le navigateur affichera un avertissement la première fois, comparez l'empreinte affichée). **Non testé depuis un autre appareil.**

## Vérifier l'intégrité

```powershell
Get-FileHash .\StructureArc_1.0.0_x64-setup.exe -Algorithm SHA256
```
Comparez avec `SHA256SUMS.txt`.
