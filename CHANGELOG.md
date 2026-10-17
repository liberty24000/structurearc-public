# Journal des versions de StructureArc

Ce journal décrit, version par version, ce qui change pour l'utilisateur. Chaque version a aussi un fichier **LIMITES** qui dit sans détour ce qui a été prouvé et ce qui ne l'a pas été. Tous les installateurs publiés ici sont **signés** (Authenticode) : vérifiez toujours la signature et l'empreinte SHA-256 (voir `VERIFIER.md`).

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
- L'exécutable **et** l'installateur sont maintenant **signés** ; l'éditeur affiché est « le-bon.contact » ; la **licence** s'affiche à l'installation.
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
