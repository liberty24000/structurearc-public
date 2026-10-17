# Journal des versions de StructureArc

Ce journal décrit, version par version, ce qui change pour l'utilisateur. Chaque version a aussi un fichier **LIMITES** qui dit sans détour ce qui a été prouvé et ce qui ne l'a pas été. Tous les installateurs sont **non signés** pour l'instant : vérifiez toujours l'empreinte SHA-256 (voir `VERIFIER.md`).

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
