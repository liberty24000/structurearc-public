# Pourquoi StructureArc ?

Beaucoup d'outils savent faire tourner une IA sur votre ordinateur. StructureArc vise à **orchestrer les capacités réellement disponibles dans chaque build pour avancer sur des projets complexes avec de petits modèles**, grâce au découpage des tâches et à des optimisations mesurées. Ce texte ne promet pas que tous les outils, toutes les machines ou tous les gros modèles sont déjà pris en charge.

Voici ce que nous faisons, et pour chaque point **ce qui est prouvé** (scénarios exécutés dans la vraie application, résultats publiés dans le fichier *LIMITES* de chaque version).

## 1. Des outils séparés, avec une disponibilité vérifiable par version
- Fichiers, terminal, web et recherche, lecture Office, serveurs MCP (outils externes), agents et compétences créés par l'IA : **chaque outil est une capacité séparée** que vous activez, projet par projet, dans la mesure où le build le prend en charge. La capture/OCR et les actions machine (souris/clavier et installation de logiciels) ont des limites propres ; elles ne doivent pas être présentées comme entièrement validées dans le public V1.3.1. L'objectif est l'autonomie : vous donnez une mission (`/mission`), l'IA planifie, agit, vérifie et rend compte.
- Un cadre garde la main entre vos mains sans freiner le travail : permissions par projet (lecture, proposition, exécution), confirmation des actions les plus sensibles, **journal d'audit**, **arrêt d'urgence**, périmètre de fichiers. Ce cadre est volontairement réglable : plus vous ouvrez, plus l'IA peut seule.
- *Prouvé dans le périmètre V1.3.1* : missions réelles avec un modèle local de 4 milliards de paramètres (lecture, commandes, recherche Internet, propositions de modification, arrêt d'urgence) ; refus par défaut, périmètre de dossier, audit sans contenu — voir les fichiers *LIMITES* pour MCP, capture/OCR et les fonctions non implémentées.

## 1 bis. Une méthode de découpage pensée pour les petits modèles
- Un petit modèle ne lit pas un gros projet d'un coup. StructureArc **découpe le travail** : plan en étapes qui tiennent dans la fenêtre du modèle, tâches avec dépendances, contrats entre modules, contexte compilé et borné (carte du projet, extraits ciblés, projets liés), rapports qui remontent par groupes jusqu'à une synthèse, reprise après interruption, états « prête / en cours / terminée / vérifiée ».
- *Prouvé* : plans de dizaines de tâches sur des dépôts de 600 fichiers (étapes bornées à la fenêtre de 2 048 à 8 192 jetons), exécution réelle de plans à tâches dépendantes par un modèle local, rappel de recherche mesuré sur un dépôt synthétique. *Limite* : les mesures de rappel sont faites sur des projets d'essai favorables.

## 1 ter. Des optimisations pour petits ET gros modèles
- Estimation mémoire **mesurée** (avec ou sans carte graphique), déport de couches sur la carte, cache de contexte réduit, chargement sans copie du modèle en RAM (3,4 Go → 1,2 Go sur un modèle de 4 milliards de paramètres), plafond de charge pour ne pas saturer la carte, choix du modèle par tâche d'après un banc de qualité et d'appels d'outils.
- Les mêmes mécanismes sont conçus pour s'adapter d'un petit modèle sur un portable à un modèle plus gros sur un poste équipé ; **la preuve publique reste limitée à la machine de référence** et ne vaut pas certification pour tous les PC (`MESURES_PC`).
- *Prouvé* : mesures sur une machine (GTX 1070, 16 Go) ; *non prouvé* : autres matériels (AMD, Intel, sans carte graphique, peu de RAM) — voir les limites.

## 2. L'IA propose, vous décidez
- Quand l'IA veut modifier un fichier, créer un agent ou une compétence, elle **propose** : vous relisez le texte exact (ou la différence) et vous cliquez. **Une proposition ne crée et ne modifie rien.**
- Une tâche terminée par un agent n'est « **vérifiée** » que si c'est **vous** qui la validez.
- *Prouvé* : propositions d'agents faites par un vrai modèle local et non appliquées avant approbation ; statut « vérifiée » impossible à s'attribuer par un plan modifié.

## 3. Votre ordinateur reste utilisable
- Une **garde de ressources** vise **80 % du processeur et de la mémoire** et jusqu'à 95 % de la carte graphique (réglable). Elle est réactive, pas prédictive : un dépassement transitoire a été observé à 95,5–96,3 % avant interruption. Si la machine est trop chargée, StructureArc peut refuser ou interrompre le modèle et vous explique pourquoi, plutôt que de tout figer.
- *Prouvé* : refus expliqués, interruption en cours de génération, plafond mesuré pendant les scénarios (un seul ordinateur testé).

## 4. Le bon petit modèle pour votre machine et votre tâche
- StructureArc **mesure votre ordinateur** (mémoire, processeur, carte graphique et sa mémoire vidéo), calcule ce qui tient avec une marge de sécurité, et **choisit un petit modèle adapté** à la tâche (recherche, résumé, architecture, code, correction, relecture). Il peut **basculer** d'un modèle à l'autre en gardant l'état de la tâche et en vous disant pourquoi ; vous pouvez **verrouiller** votre choix.
- Un écran montre la **compatibilité** de chaque modèle avec votre machine (chiffres annoncés comme des estimations).
- *Prouvé* : sélection et bascule réelles entre deux modèles, accélération graphique Vulkan (jusqu'à ×6 mesuré sur la machine de test), import de modèles GGUF vérifiés par un vrai démarrage.

## 5. Un logiciel qui se vérifie lui-même, et qui le dit
- **Installateur signé**, empreinte SHA-256 publiée pour chaque version, modèles et moteur d'IA **vérifiés par empreinte** avant usage, téléchargements **toujours soumis à votre consentement**.
- Pour **chaque version**, un fichier *LIMITES* liste **ce qui a été prouvé et ce qui ne l'a pas été** (y compris les échecs de test conservés). Nous ne publions pas de promesse sans preuve.
- *Prouvé sur le build public concerné* : installation et désinstallation automatisées (le nombre exact de contrôles est indiqué dans le fichier *LIMITES* de la version), données conservées à la désinstallation.

## 6. Pas de prérequis, pas de cloud
- Pas de Docker, de Python, de Git ni d'abonnement ; **aucun compte, aucune télémétrie** ; vos données restent sur votre ordinateur ; les secrets (clés, mots de passe) sont **masqués** avant d'être montrés à l'IA ou écrits dans un journal.
- Interface en **19 langues**, installateur en 18 langues.

## 7. Des mises à jour en un clic, mais sûres
- StructureArc **détecte** qu'une version plus récente existe et propose « Mettre à jour » : un clic suffit. Avant d'installer quoi que ce soit, il **vérifie l'empreinte et la signature de l'éditeur** du fichier téléchargé, **sauvegarde votre base de données**, puis redémarre. Un fichier non signé, altéré ou signé par un autre éditeur est **refusé** : rien n'est lancé.
- La détection se fait au plus une fois par jour, ne transmet aucune donnée personnelle et se désactive dans les paramètres.
- *Prouvé sur le périmètre indiqué par la version* : mise à jour réelle sur une installation (refus d'un installateur non signé et d'un installateur altéré, mise à jour, relance automatique, projets et réglages conservés). La portée exacte — version simulée, version publiée, ou les deux — est indiquée dans *LIMITES* ; elle ne doit pas être généralisée.

## 8. Pensé pour de gros projets
- Indexation, recherche par symbole, graphe de dépendances, contexte **borné et sourcé** pour que de petits modèles restent utiles sans lire tout le projet.
- **Livré depuis la V1.2.2** : **contrats** de modules versionnés et validés (avec détection des ruptures de compatibilité) et **liaisons en lecture seule** entre projets, toujours explicites, jamais implicites. Les limites de la version publique indiquent ce qui a été réellement observé dans la fenêtre de l'application.

---

## Ce que nous ne prétendons pas
- Nous **n'affirmons pas** que StructureArc est plus rapide ou plus intelligent qu'un autre outil : **aucun comparatif mesuré n'a été publié**. Les petits modèles locaux restent limités et se trompent parfois.
- Les preuves viennent d'**un seul ordinateur** (Windows 11, 16 Go, carte NVIDIA GTX 1070) ; d'autres configurations ne sont pas testées.
- Notre différence est **la manière de travailler** (permissions, validation humaine, limites de ressources, honnêteté des preuves), pas un record de performance.

Vous voulez qu'on compare StructureArc à un outil précis ? Ouvrez un ticket : nous le ferons avec des mesures publiques et des sources, pas avec des impressions.

## 8. Des missions autonomes, mais dans le cadre que vous fixez *(V1.3.1)*
- `/mission <objectif>` : le chat enchaîne lui-même les étapes (lire des fichiers, lancer une commande autorisée, chercher sur le web, **proposer** une modification) jusqu'à un compte rendu, avec un budget **borné** (30 appels d'outils, 20 minutes), l'arrêt d'urgence toujours prioritaire et **aucune permission contournée** : une commande sensible reste soumise à votre confirmation et une modification de fichier n'est écrite que si vous l'approuvez.
- **Recherche web** et **serveurs MCP** (outils externes) : désactivés par défaut, par projet ; le web « autonome » est un choix explicite ; chaque outil MCP est « à confirmer » tant que vous ne le passez pas en « automatique » ; le chat ne peut ni ajouter ni activer un serveur.
- **Capture d'écran avec lecture du texte en local** : capacité séparée, révocable, coupée par l'arrêt d'urgence ; les limites V1.3.1 précisent ce qui a été testé sur image de test et ce qui n'a pas été observé dans une vraie fenêtre utilisateur.
- *Prouvé* : mission réelle avec un modèle local de 4 milliards de paramètres sur la carte graphique (20 contrôles : appels enchaînés, commande sensible jamais exécutée sans confirmation, vraie recherche sur Internet, modification proposée mais non appliquée, arrêt d'urgence) ; serveur MCP réel déclaré, découvert, exécuté, audité et supprimé depuis l'interface. *Réserve* : le parcours MCP manuel est prouvé, mais l'appel MCP piloté par le modèle en fenêtre réelle reste irrégulier (voir LIMITES).

## 9. Le meilleur modèle de votre PC, mesuré et non supposé *(V1.3.1)*
- Un banc mesure vitesse, mémoire et réussite (recherche, résumé, architecture, code exécuté, correction, appels d'outils) ; le tableau complet de la machine de référence est publié. Exemple mesuré : un modèle plus gros n'est pas meilleur — Qwen3.5 9B donne les mêmes résultats que le 4B, plus lentement et avec plus de mémoire.
- L'application tient compte de la mémoire **réellement mesurée** (avec ou sans carte graphique) et limite la part du modèle placée sur la carte quand elle la ferait dépasser sa limite de charge.
