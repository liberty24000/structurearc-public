# Pourquoi StructureArc ?

Beaucoup d'outils savent faire tourner une IA sur votre ordinateur. StructureArc part d'une autre question : **comment laisser une IA locale travailler sur vos projets sans lui donner les clés de toute la machine, et sans que votre ordinateur en pâtisse ?**

Voici ce que nous faisons, et pour chaque point **ce qui est prouvé** (scénarios exécutés dans la vraie application, résultats publiés dans le fichier *LIMITES* de chaque version).

## 1. Une IA qui n'a accès à rien tant que vous ne le décidez pas
- Chaque projet a ses **propres permissions, désactivées par défaut** : fichiers, terminal, web, Word/Excel/PowerPoint. Rien n'est ouvert « globalement » ; une autorisation vaut pour **un projet, un dossier, un niveau** (lecture, proposition, exécution) et peut être **retirée** à tout moment.
- Les actions sensibles demandent votre **confirmation** ; un modèle ne peut jamais se l'accorder lui-même.
- **Journal d'audit** de ce qui a été demandé, autorisé ou refusé (sans le contenu de vos fichiers), et **bouton d'arrêt d'urgence** qui bloque tout instantanément.
- *Prouvé* : refus par défaut, périmètre de dossier (pas de sortie par `..`, liens ou chemins réseau), arrêt d'urgence, audit sans contenu — en fenêtre réelle pour les fichiers, le terminal, le web et les documents Office.

## 2. L'IA propose, vous décidez
- Quand l'IA veut modifier un fichier, créer un agent ou une compétence, elle **propose** : vous relisez le texte exact (ou la différence) et vous cliquez. **Une proposition ne crée et ne modifie rien.**
- Une tâche terminée par un agent n'est « **vérifiée** » que si c'est **vous** qui la validez.
- *Prouvé* : propositions d'agents faites par un vrai modèle local et non appliquées avant approbation ; statut « vérifiée » impossible à s'attribuer par un plan modifié.

## 3. Votre ordinateur reste utilisable
- Une **garde de ressources** limite l'IA à **80 % du processeur et de la mémoire** (carte graphique jusqu'à 95 %, réglable). Si la machine est trop chargée, StructureArc **refuse de lancer le modèle** et vous explique pourquoi, plutôt que de tout figer.
- *Prouvé* : refus expliqués, interruption en cours de génération, plafond mesuré pendant les scénarios (un seul ordinateur testé).

## 4. Le bon petit modèle pour votre machine et votre tâche
- StructureArc **mesure votre ordinateur** (mémoire, processeur, carte graphique et sa mémoire vidéo), calcule ce qui tient avec une marge de sécurité, et **choisit un petit modèle adapté** à la tâche (recherche, résumé, architecture, code, correction, relecture). Il peut **basculer** d'un modèle à l'autre en gardant l'état de la tâche et en vous disant pourquoi ; vous pouvez **verrouiller** votre choix.
- Un écran montre la **compatibilité** de chaque modèle avec votre machine (chiffres annoncés comme des estimations).
- *Prouvé* : sélection et bascule réelles entre deux modèles, accélération graphique Vulkan (jusqu'à ×6 mesuré sur la machine de test), import de modèles GGUF vérifiés par un vrai démarrage.

## 5. Un logiciel qui se vérifie lui-même, et qui le dit
- **Installateur signé**, empreinte SHA-256 publiée pour chaque version, modèles et moteur d'IA **vérifiés par empreinte** avant usage, téléchargements **toujours soumis à votre consentement**.
- Pour **chaque version**, un fichier *LIMITES* liste **ce qui a été prouvé et ce qui ne l'a pas été** (y compris les échecs de test conservés). Nous ne publions pas de promesse sans preuve.
- *Prouvé* : installation et désinstallation automatisées (16 contrôles), données conservées à la désinstallation.

## 6. Pas de prérequis, pas de cloud
- Pas de Docker, de Python, de Git ni d'abonnement ; **aucun compte, aucune télémétrie** ; vos données restent sur votre ordinateur ; les secrets (clés, mots de passe) sont **masqués** avant d'être montrés à l'IA ou écrits dans un journal.
- Interface en **19 langues**, installateur en 18 langues.

## 7. Des mises à jour en un clic, mais sûres
- StructureArc **détecte** qu'une version plus récente existe et propose « Mettre à jour » : un clic suffit. Avant d'installer quoi que ce soit, il **vérifie l'empreinte et la signature de l'éditeur** du fichier téléchargé, **sauvegarde votre base de données**, puis redémarre. Un fichier non signé, altéré ou signé par un autre éditeur est **refusé** : rien n'est lancé.
- La détection se fait au plus une fois par jour, ne transmet aucune donnée personnelle et se désactive dans les paramètres.
- *Prouvé* : mise à jour réelle sur une vraie installation (33 contrôles) — refus d'un installateur non signé et d'un installateur altéré, mise à jour, relance automatique, projets et réglages conservés. Pas encore observé entre deux versions publiées (voir les limites).

## 8. Pensé pour de gros projets
- Indexation, recherche par symbole, graphe de dépendances, contexte **borné et sourcé** pour que de petits modèles restent utiles sans lire tout le projet.
- *À venir dans la V1.2.2* : **contrats** de modules versionnés et validés (avec détection des ruptures de compatibilité) et **liaisons en lecture seule** entre projets, toujours explicites, jamais implicites.

---

## Ce que nous ne prétendons pas
- Nous **n'affirmons pas** que StructureArc est plus rapide ou plus intelligent qu'un autre outil : **aucun comparatif mesuré n'a été publié**. Les petits modèles locaux restent limités et se trompent parfois.
- Les preuves viennent d'**un seul ordinateur** (Windows 11, 16 Go, carte NVIDIA GTX 1070) ; d'autres configurations ne sont pas testées.
- Notre différence est **la manière de travailler** (permissions, validation humaine, limites de ressources, honnêteté des preuves), pas un record de performance.

Vous voulez qu'on compare StructureArc à un outil précis ? Ouvrez un ticket : nous le ferons avec des mesures publiques et des sources, pas avec des impressions.

## 8. Des missions autonomes, mais dans le cadre que vous fixez *(V1.3.1)*
- `/mission <objectif>` : le chat enchaîne lui-même les étapes (lire des fichiers, lancer une commande autorisée, chercher sur le web, **proposer** une modification) jusqu'à un compte rendu, avec un budget **borné** (30 appels d'outils, 20 minutes), l'arrêt d'urgence toujours prioritaire et **aucune permission contournée** : une commande sensible reste soumise à votre confirmation et une modification de fichier n'est écrite que si vous l'approuvez.
- **Recherche web** et **serveurs MCP** (outils externes) : désactivés par défaut, par projet ; le web « autonome » est un choix explicite ; chaque outil MCP est « à confirmer » tant que vous ne le passez pas en « automatique » ; le chat ne peut ni ajouter ni activer un serveur.
- **Capture d'écran avec lecture du texte en local** (aucune image conservée ni envoyée) : autorisation séparée, révocable, coupée par l'arrêt d'urgence.
- *Prouvé* : mission réelle avec un modèle local de 4 milliards de paramètres sur la carte graphique (20 contrôles : appels enchaînés, commande sensible jamais exécutée sans confirmation, vraie recherche sur Internet, modification proposée mais non appliquée, arrêt d'urgence) ; serveur MCP réel déclaré, découvert, exécuté, audité et supprimé depuis l'interface. *Non prouvé* : l'appel d'un outil MCP par le modèle en fenêtre réelle est irrégulier (voir LIMITES).

## 9. Le meilleur modèle de votre PC, mesuré et non supposé *(V1.3.1)*
- Un banc mesure vitesse, mémoire et réussite (recherche, résumé, architecture, code exécuté, correction, appels d'outils) ; le tableau complet de la machine de référence est publié. Exemple mesuré : un modèle plus gros n'est pas meilleur — Qwen3.5 9B donne les mêmes résultats que le 4B, plus lentement et avec plus de mémoire.
- L'application tient compte de la mémoire **réellement mesurée** (avec ou sans carte graphique) et limite la part du modèle placée sur la carte quand elle la ferait dépasser sa limite de charge.
