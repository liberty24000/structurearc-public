# Journal des versions de StructureArc

Ce journal décrit, version par version, ce qui change pour l'utilisateur. Chaque version a aussi un fichier **LIMITES** qui dit sans détour ce qui a été prouvé et ce qui ne l'a pas été. Tous les installateurs publiés ici sont **signés** (Authenticode) : vérifiez toujours la signature et l'empreinte SHA-256 (voir `VERIFIER.md`).

## V1.3.13 — 21 octobre 2026
**Mise à jour plus sûre et choix automatique du modèle.**
- Mise à jour : l'éditeur de l'installateur est vérifié par le nom exact du certificat ou son empreinte, et non plus par une simple correspondance partielle.
- Choix automatique du modèle : la bascule entre petits modèles (0,5B → 4B → 0,5B) et le verrouillage manuel ont été observés en fenêtre réelle, sur une seule machine de mesure.
- Installateur hors-ligne avec modèle embarqué ; signatures et empreintes vérifiables (voir `VERIFIER.md`).
- Défaut connu, non corrigé dans cette version : abandonner une copie d'auto-amélioration ne retire pas toujours le projet de la liste, ce qui peut ralentir l'ouverture des projets.
- Auto-développement toujours expérimental : aucun modèle local essayé n'a terminé une tâche seul, voir `LIMITES_V1_3_13.md`.

## V1.3.12 — 21 octobre 2026
**Un chat qui se lit comme les autres, et une signature plus simple.**
- Chat : la zone de saisie reste fixe en bas ; seul le fil des messages défile et il suit les nouveaux messages. Si vous remontez lire plus haut, il ne vous ramène pas en bas ; envoyer un message vous y ramène.
- Auto-développement (expérimental) : durci d'après 14 observations réelles. **Résultat honnête : aucun modèle local essayé n'a terminé une tâche seul**, voir `LIMITES_V1_3_12.md`.
- Les installateurs sont désormais signés sans l'application SimplySign Desktop ; la signature reste vérifiable (Authenticode).
- Une seule machine de mesure : voir `LIMITES_V1_3_12.md`.

## V1.3.11 — 21 octobre 2026
**Rouvrir un projet avec ses conversations.**
- Le dossier `.structurearc/` d'un projet garde de quoi le reprendre : définition, conversations (secrets masqués) et un résumé de reprise `RESUME.md`. À l'ouverture, les conversations absentes sont restaurées ; **les autorisations ne le sont jamais**.
- Fenêtre de contexte mieux gérée avec les petits modèles (reprise automatique après un dépassement, lecture d'un gros fichier par morceaux).
- Une seule machine de mesure : voir `LIMITES_V1_3_11.md`.

## V1.3.10 — 20 octobre 2026
**Plus de puissance de la carte graphique, avec un filet de sécurité.**
- Charge de la carte graphique réglable de 50 à 100 % (100 % par défaut) avec un arrêt préventif si elle chauffe trop (≈ 89 °C). Le processeur et la mémoire restent plafonnés à 80 %. Le filet de température n'a été éprouvé qu'en simulation.
- Tous les fichiers Markdown d'un projet (y compris ceux des dossiers d'agents `.claude`, `.codex`, `.cursor`…) sont inventoriés pour l'IA, en lecture seule.
- Une seule machine de mesure : voir `LIMITES_V1_3_10.md`.

## V1.3.9 — 20 octobre 2026
**L'IA peut demander une autorisation dans le chat.**
- Demandes d'autorisation oui/non directement dans la conversation, boutons « Tout autoriser » et « Tout révoquer », outil d'indexation du projet.
- Auto-amélioration encadrée : travail dans une copie isolée du projet, chemins protégés, briefing de reprise.
- Une seule machine de mesure : voir `LIMITES_V1_3_9.md`.

## V1.3.8 — 20 octobre 2026
**Le « subconscient » mesuré sous charge.**
- Surcoût de latence réduit de 9 ms à environ 1 ms par commande après un test sous charge réelle. Aucun gain d'intelligence n'est démontré à ce jour.
- Une seule machine de mesure : voir `LIMITES_V1_3_8.md`.

## V1.3.7 — 20 octobre 2026
**Choix automatique du modèle dans le chat (implémenté, non encore démontré en fenêtre réelle à cette version).**
- Le chat peut basculer entre petits modèles selon la tâche, avec une ligne qui explique la décision et un verrou manuel qui passe toujours en premier. (La démonstration en fenêtre réelle est venue plus tard.)
- Une première couche cognitive légère (mémoire des actions, réflexes prudents) qui ne charge aucun modèle.
- Une seule machine de mesure : voir `LIMITES_V1_3_7.md`.

## V1.3.6 — 20 octobre 2026
**Un modèle adapté à chaque type de tâche, et un démarrage plus léger.**
- Table de choix du modèle par type de tâche (rédaction, raisonnement, code, recherche web, contexte long, agents) ; NeoHorse 1 9B devient le modèle recommandé sur un PC qui le supporte, sinon le Qwen3.5 4B. Rien n'est téléchargé sans votre accord ; le verrou manuel passe toujours en premier. Pour l'instant ce choix sert aux agents, pas encore au chat.
- Conversations plus rapides : le message système ne change plus d'une question à l'autre (mesure synthétique : préremplissage 8,3 s → 2,3 s avec 15 outils).
- Démarrage plus léger : fin de la relecture des modèles du catalogue à chaque affichage.
- Quatre nouveaux modèles au catalogue (Gemma 4 12B, QwenPaw Flash 9B, Qwopus3.5 9B Coder, NeoHorse 1 9B) et un classement mesuré de douze modèles dans la documentation.
- Une seule machine de mesure : voir `LIMITES_V1_3_6.md`.

## V1.3.5 — 19 octobre 2026
**Réponses plus rapides quand l'IA recopie ou modifie un texte.**
- Accélération par motifs répétés (sans second modèle) pour les modèles chargés sur la carte graphique : jusqu'à ×2,4 (Qwen3.5 4B) quand la réponse cite ou réécrit un texte fourni, aucun effet en génération libre. Activée par défaut, désactivable dans Paramètres.
- Agents simultanés : plafond mémoire corrigé ; qualité vérifiée identique à 4 agents.
- Une seule machine de mesure : voir `LIMITES_V1_3_5.md`.

## V1.3.4 — 19 octobre 2026
**Plusieurs agents locaux en même temps sur un seul modèle.**
- Les tâches d'un plan peuvent partager un même modèle local chargé sur la carte graphique : sur le PC de test, 3 tâches passent de 28,6 s à 13,2 s. Réglage Paramètres → « Agents simultanés » (1 par défaut) ; le mode parallèle n'est actif que si le modèle est verrouillé et si toutes les tâches sont locales.
- Une seule mesure en conditions réelles, un seul PC : voir `LIMITES_V1_3_4.md`.

## V1.3.3 — 19 octobre 2026
**Calibration automatique de l'IA pour votre machine.**
- Après le téléchargement d'un modèle, l'application mesure le meilleur réglage de votre carte graphique (nombre de couches) sans dépasser les limites de charge ; résultat par modèle et par carte, modifiable dans l'écran IA. Sur le PC de test, le Qwen3.5 4B passe de 13 à 38 jetons/s (mesure du 18 octobre au banc et par calibration réelle, publiée dans les mesures du projet ; le rapport de calibration rattaché à une version livrée concerne le petit modèle 0,5B — celui du 4B sera rattaché à la version suivante).
- Modèle à experts Qwen3 30B-A3B (2 bits) proposé comme **expérimental** (verrouillage manuel, 10 Go) : ≈ 16 jetons/s mais lecture des longs textes lente.
- Garde de charge GPU plus fine ; scripts Windows optionnels d'allègement (simulation par défaut).
- Toutes les mesures viennent d'un seul PC : voir `LIMITES_V1_3_3.md`.

## V1.3.2 — 18 octobre 2026
**Installateur hors-ligne, actions proposées sur la machine, vérification des réponses.**
- **Installateur hors-ligne** (≈ 1,1 Go) : application, runtime et un petit modèle (Qwen2.5 1,5B) déjà inclus, vérifiés à l'installation ; l'installateur standard reste disponible.
- **Actions « machine »** (souris, clavier, installation de logiciel) : l'IA ne peut que PROPOSER ; rien ne s'exécute sans votre clic d'approbation sur cette action ; désactivé par défaut, journalisé, coupé par l'arrêt d'urgence.
- **Contrôle d'ancrage** : un badge sous chaque réponse indique combien de fichiers, adresses, identifiants et nombres cités sont retrouvés dans les sources reçues par le modèle (estimation, pas une garantie).
- **Outils sûrs** : un modèle n'est choisi pour une tâche à outils que s'il réussit les appels attendus ET ne fait aucun appel parasite au banc ; la matrice de compatibilité l'affiche.
- **Garde de ressources** : la charge GPU doit rester élevée 10 secondes d'affilée avant d'interrompre une génération (un long prompt sature brièvement la carte) ; la limite de 95 % est inchangée.
- Corrections : un modèle qui tourne sur la carte graphique n'est plus remplacé à tort par un plus petit ; mise à jour et publication durcies.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé ; très gros modèles non pris en charge).

## V1.3.1 — 18 octobre 2026
**Le meilleur modèle de votre PC, des missions autonomes, le web et des outils externes.**
- **Choix du modèle mesuré** : sur la machine de référence, Qwen3.5 4B réussit tous les tests de qualité et d'appels d'outils (le 9B donne les mêmes résultats, en plus lent). Le tableau des mesures est publié. Sans carte graphique utilisable, StructureArc recommande un modèle plus petit.
- **Mémoire mieux estimée** (avec ou sans carte graphique) et part du modèle sur la carte limitée quand elle dépasserait sa limite de charge.
- **Missions autonomes** : `/mission <objectif>` (ou le bouton « Lancer une mission autonome ») : le chat enchaîne les étapes (30 appels, 20 minutes au plus) sans contourner aucune permission ; une modification de fichier n'est jamais écrite sans votre approbation.
- **Recherche et lecture web** (niveau « autonome » : choix explicite par projet) ; **connecteurs MCP** (désactivés par défaut, chaque outil « à confirmer ») ; **capture/OCR local** avec limites de validation précisées dans le fichier LIMITES (aucune image conservée ni envoyée).
- Mise à jour plus sûre (verrou, refus d'architecture ou de version trop ancienne) ; onglets adaptatifs ; explications repliées.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé ; l'appel d'un outil MCP par le modèle est irrégulier ; installation hors-ligne et souris/clavier : versions suivantes).

## V1.3.0 — 18 octobre 2026
**Catalogue de modèles et choix fondé sur des mesures.**
- **8 modèles de 6 familles** (Qwen, Llama, Gemma, Phi, SmolLM2, Granite) au catalogue, chacun avec sa source, sa version, sa taille, son empreinte SHA-256 et sa licence. Rien n'est téléchargé sans votre accord et chaque fichier est vérifié avant usage.
- **Le choix du modèle repose sur des mesures** (recherche, résumé, architecture, code exécuté et testé, correction, appels d'outils) et non plus sur la seule taille du fichier. Un modèle qui réussit moins de 4 appels d'outils sur 5 n'est jamais choisi pour une tâche qui en exige. Ces mesures viennent d'un seul ordinateur et d'un essai : ce sont des indications, pas des garanties.
- La **matrice de compatibilité** (écran *IA*) affiche la qualité, les appels d'outils et la vitesse mesurés pour chaque modèle, ou « non mesuré » quand ce n'est pas le cas.
- Le modèle recommandé par défaut reste un modèle sous licence libre (Apache-2.0 ou MIT) qui sait appeler des outils.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé ; les six nouveaux modèles sont installables mais pas livrés dans l'installateur ; installation hors-ligne et gros modèles sur petite carte graphique : versions suivantes).

## V1.2.4 — 18 octobre 2026
**Retour d'information sur la mise à jour.**
- Au premier démarrage après une mise à jour, StructureArc vous le dit : « StructureArc a été mis à jour vers la version X. Vos projets et réglages sont intacts. »
- Si une mise à jour lancée n'a pas abouti, il le dit aussi honnêtement (« vous utilisez toujours la version X, vos données n'ont pas été modifiées, vous pouvez réessayer ») au lieu de rester silencieux.
- Première mise à jour réelle **entre deux versions publiées** (1.2.3 vers 1.2.4) vérifiée : le numéro de version change, l'application est relancée, vos projets et réglages sont conservés.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé).

## V1.2.3 — 17 octobre 2026
**Mise à jour en un clic.**
- StructureArc **détecte** qu'une version plus récente est publiée (une requête HTTPS au dépôt public, au plus une fois par jour, sans donnée personnelle ; désactivable dans *Paramètres*) et affiche une bannière **« Mettre à jour »**.
- Un clic suffit : téléchargement, **vérification de l'empreinte et de la signature de l'éditeur**, sauvegarde de votre base de données, installation, redémarrage. Vos projets et réglages ne sont pas modifiés. Un installateur non signé ou altéré est **refusé** : rien n'est lancé.
- L'installateur **et l'exécutable qu'il installe** sont maintenant **signés** (Authenticode, certificat Certum ; vérifié par le scénario de mise à jour réelle ; le binaire compilé seul n'est pas distribué) ; l'éditeur affiché est « le-bon.contact » ; la **licence** s'affiche à l'installation.
- Pour profiter de la mise à jour en un clic, installez cette version une première fois ; les versions précédentes ne savent pas se mettre à jour toutes seules.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé ; première mise à jour entre deux versions publiées pas encore observée).

## V1.2.2 — 17 octobre 2026
**Contrats, projets liés en lecture seule, vérification de mise à jour.**
- **Contrats** (écran *Agents*) : décrivez un module (entrées, sorties, chemins autorisés, capacités, règles à vérifier). Un contrat enregistré reste « proposé » tant que vous ne l'acceptez pas ; une règle en prose est signalée comme non vérifiable automatiquement ; changer le contenu public sans changer la version est refusé, et une rupture de compatibilité exige une nouvelle version majeure (avec la liste des contrats impactés).
- **Projets liés en lecture seule** (écran *Permissions*) : un projet peut lire (fichiers, recherche) un autre projet, **seulement après votre confirmation**, dans un seul sens, et **seulement ce que les autorisations de l'autre projet permettent**. Chaque lecture est journalisée des deux côtés, sans contenu. Le chat peut s'en servir via trois outils de lecture.
- **Mise à jour** (écran *Paramètres*) : si vous indiquez l'adresse (HTTPS) d'un manifeste de version, StructureArc peut vous dire qu'une version plus récente existe et la **télécharger après votre confirmation**, avec vérification de la taille et de l'empreinte SHA-256 et sauvegarde préalable de votre base. Il **n'installe rien automatiquement**. Ce n'est pas encore la mise à jour complète.
- Installateur **signé** (Authenticode, horodaté). Seul l'installateur est signé pour l'instant, pas encore l'application installée.
- Limites : voir le fichier LIMITES de cette version (un seul ordinateur testé ; mise à jour réelle Windows non testée).

## V1.2.1 — 17 octobre 2026
**États de tâche et compatibilité visible.**
- Dans l'écran *Agents*, une tâche dont toutes les dépendances sont terminées s'affiche **« Prête »**. Une tâche terminée peut être marquée **« Vérifiée »** par vous, et seulement par vous : ni un agent ni un plan modifié ne peut poser ce statut.
- Dans l'écran *IA*, une nouvelle zone **« Compatibilité des modèles »** montre, pour votre ordinateur : le verdict global, un tableau des modèles (taille, mémoire estimée, accélération graphique, appels d'outils déclarés) et le modèle que le routage choisirait pour chaque type de tâche. Les chiffres de mémoire sont des estimations.
- Testé sur un seul ordinateur (Windows 11, 16 Go de RAM, carte NVIDIA GTX 1070). Voir `LIMITES`.

## V1.2.0 — 17 octobre 2026
**Agents et compétences.**
- Vous pouvez créer des **agents** (un rôle avec des consignes et une mémoire propres au projet), ou laisser le chat en **proposer** : une proposition ne crée rien tant que vous n'avez pas relu le texte exact et cliqué « Approuver ». Un agent n'ajoute **aucune permission**.
- Mémoire par agent (bornée, secrets masqués), compétences (modèles de plan réutilisables) proposées de la même façon, isolation stricte entre projets.
- Correctif : le message système n'affirme plus « aucune commande possible » quand le terminal est proposé au modèle.

## V1.1.0 — 17 octobre 2026
- Option **« Fermer la fenêtre la réduit dans la zone de notification »** et bouton **« Ouvrir la version web »** (Paramètres).
- Le résultat d'une commande du terminal est remis au modèle avec une formulation explicite.
- Preuves en fenêtre réelle ajoutées : import de modèle GGUF, accélération graphique Vulkan, changement de modèle en pleine génération, accès HTTPS sur le réseau local, zone de notification.

## V1.0.0 — 17 octobre 2026
**Première version fonctionnelle.**
- Projets locaux, indexation, recherche, graphe de dépendances, **chat par projet** (modes Auto/Manuel, niveaux d'effort, commandes `/`).
- **Permissions séparées et désactivées par défaut** (fichiers, terminal, web, Word/Excel/PowerPoint), journal d'audit, **arrêt d'urgence**.
- **IA locale** (llama.cpp CPU embarqué ; modèle téléchargé avec votre consentement et vérifié par empreinte), garde de ressources (CPU/RAM limités à 80 %, carte graphique jusqu'à 95 %), accélération Vulkan optionnelle, import de modèles GGUF, routage entre petits modèles.
- Version web locale, accès réseau local en HTTPS, 19 langues d'interface, installateur en 18 langues.
- Aucun compte, aucune télémétrie : les données restent sur votre ordinateur.
