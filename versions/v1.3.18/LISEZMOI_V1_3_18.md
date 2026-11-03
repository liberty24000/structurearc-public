> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.18

**3 novembre 2026 — paquet construit, signé et mise à niveau contrôlée.**

Application Windows x64 pour travailler sur des projets avec une IA locale. Cette mise à jour corrige la coordination des interruptions vocales et plusieurs défauts du moteur de tâches. Elle ne constitue pas une validation de la création autonome de tout projet.

## Installation sur le PC

L’installateur construit et contrôlé est `StructureArc_1.3.18_x64-setup.exe`. L’installateur en ligne contient l’application et le runtime CPU ; le modèle se télécharge séparément depuis le catalogue, avec contrôle de taille et SHA-256.

- Installateur : **24 064 248 octets**, signature Authenticode **Valid** ; SHA-256 `1d4f876199befa4a893abbaf06ac6bd87835fa99334e302541789baef8daee5d`.
- Exécutable installé : signature Authenticode **Valid** ; SHA-256 `0854e346ad92cbcdb4d911e0ce1cbe277fff3266b2dce4e9e63840d3d9affe84` ; autotest **18/18 réussi**.

Une mise à niveau réelle et silencieuse (`/S`) de l’installation préexistante s’est terminée avec le code **0**. Les empreintes des données contrôlées avant/après correspondent exactement : **2 projets, 30 conversations et 319 messages**. Aucun aller-retour désinstallation/réinstallation n’a été exécuté, afin de conserver l’installation utilisateur préexistante. Ces contrôles ne certifient pas l’autonomie du modèle.

## Ce qui change depuis 1.3.17

- Voix : correction d’une course entre l’interruption d’une ancienne réponse et la mise en lecture d’une nouvelle phrase, afin que cette ancienne interruption n’annule pas la nouvelle lecture.
- Moteur de tâches : traitement des lectures répétées et conservation des diagnostics de plusieurs contrôles. Un contrôle vert ne doit pas effacer l’échec d’un autre contrôle.
- Contexte du modèle : les historiques et états générés par StructureArc sont exclus des extraits de projet récupérés par défaut. Les lectures explicites restent possibles sous les autorisations du projet ; les notes, mémoires et contrats utilisateur sont conservés.
- Coordination : phase Analyse distincte de la réalisation, en lecture seule pour les fichiers ; contrôle des demandes de réalisation et des arguments obligatoires des outils. Les reprises correctives de ce contrôle sont bornées à deux. Un simple compte rendu positif ne constitue pas une preuve d’action exécutée.
- Protocole : les appels aux arguments JSON invalides ou non objets sont exclus de l’historique natif transmis au modèle. Dans les lots mixtes, seuls les appels valides appariés à leurs résultats sont conservés.
- Retours de tâches : les diagnostics de l’exécution courante sont conservés, y compris les blocages et interruptions ; un ancien rapport positif ne remplace pas le diagnostic actuel. Le statut HTTP disponible est conservé dans des retours bornés et débarrassés des secrets connus.
- Interface : la carte d’installation du chat disparaît quand le runtime et au moins un modèle sont installés. L’accueil ne présente plus la mention fixe « aucun modèle » et masque la rubrique « À venir » lorsque sa liste est vide.

## Accès depuis le téléphone et voix

La version web installable et HTTPS ont été livrés en **1.3.17**. La 1.3.18 les conserve et corrige la coordination vocale décrite ci-dessus.

Laisser le PC allumé, StructureArc ouvert et un modèle prêt. Sur le PC, utiliser Paramètres → Accès depuis le téléphone, puis le guide de préparation. Le certificat public doit être transféré et approuvé manuellement après comparaison de son empreinte. Ouvrir ensuite le lien HTTPS depuis le téléphone, puis utiliser l’installation proposée par son navigateur. La connexion prolongée reste un choix explicite ; la déconnexion la révoque.

Dans le chat, activer explicitement le bouton vocal et autoriser le microphone du téléphone. Le téléphone assure capture et lecture audio ; les moteurs français de Windows et le modèle tournent sur le PC. Aucun runtime Moshi/Kyutai n’est intégré. Aucun nouvel essai physique téléphone ou d’annulation acoustique d’écho n’est revendiqué pour cette version.

## État des validations

Suite native complète du code moteur `306fd06` : **902 réussis, 0 échec, 18 ignorés**, soit **920 tests**, en **207,89 s**. Interface `79a0bb5` : **33 tests ciblés réussis** et contrôle TypeScript réussi. Suite ciblée voix : **135 tests réussis** ; ces nombres de suites ciblées ne sont pas additionnés en un total global.

L’ancien autotest **debug 18/18** concerne uniquement `f37476b`. Le nouveau binaire de production `306fd06` et son exécutable installé disposent désormais chacun d’un autotest **18/18 réussi**. Leur équivalence a été contrôlée hors **3 octets de marqueur du bundler** et **10 400 octets de signature** ; voir les empreintes détaillées dans les limites.

Ces tests comprennent des réponses de fournisseur SSE simulées ainsi que de vrais fichiers et commandes dans des environnements isolés. Les essais réels **6 à 10 ont échoué**. Au dixième essai, l’analyse est marquée terminée, la réalisation échoue et la vérification reste bloquée. Seul le fichier de tests de **3 606 octets** existe ; `package.json`, le module et le README sont absents. Les tests du projet et le contrat indépendant terminent avec le code **1** pour module absent. Les **17 fichiers préexistants contrôlés sont inchangés**.

La reprise de protocole a néanmoins été observée en réel : après deux refus d’arguments JSON invalides, le fournisseur a été rappelé et les tests réécrits puis appliqués dans la même conversation et le même processus. Le troisième appel invalide a épuisé les deux reprises autorisées. Le diagnostic courant a été correctement affiché, sans panne HTTP terminale observée cette fois.

Ce progrès ne valide pas le projet : le contenu des tests générés attend encore une même référence de tableau alors que le contrat exige un nouveau tableau. **Le jalon de réalisation complète n’est pas atteint ; la capacité d’autonomie complète n’est pas validée.** Qwopus 9B Coder reste limité dans les conditions essayées. Voir les constats détaillés dans les limites.

Lire `LIMITES_V1_3_18.md`. L’autonomie universelle, l’API Anthropic directe et une validation physique téléphone/AEC ne sont pas déclarées livrées.
