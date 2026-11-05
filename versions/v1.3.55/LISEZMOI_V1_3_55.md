> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.55

L'optimiseur de contexte reste automatique : il tient compte des messages, des outils et de la réserve de réponse, conserve l'objectif et les résultats des actions, puis reprend le travail lorsque le contexte peut être réduit. Le moteur local vérifié mesure aussi les jetons avant génération et peut récupérer un dépassement sans demander « continue ».

Les modifications de fragments utilisent désormais la version issue de la lecture réelle du fichier, y compris en lecture parallèle. Une modification identique ne compte plus comme progrès. Un fragment peut être contrôlé une première fois ; sa correction est ensuite prioritaire avant de répéter les mêmes vérifications. Les contrôles avant écriture restent actifs.

Lorsqu'une analyse locale a inspecté le projet et transmis un plan valide, le moteur peut passer directement à la réalisation sans demander une reformulation supplémentaire. Une nouvelle consigne, une question humaine ou un changement de définition dans le même lot reste pris en compte.

Ces changements améliorent la continuité du travail, sans garantir la réussite de n'importe quel projet sur n'importe quel modèle. Aucun nouveau bouton de configuration n'est nécessaire.
