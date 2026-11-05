> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.53

L’optimisation automatique du contexte réduit désormais les répétitions du plan de travail entre les sous-tâches d’une mission. Le plan complet reste enregistré ; chaque étape reçoit toujours son instruction et l’objectif global complet. Les observations et les résultats des étapes précédentes restent disponibles.

Seule la copie d’un plan strictement identique au plan enregistré est retirée des rapports transmis. Les fichiers personnels, plans différents ou ambigus et rapports d’erreur ne sont pas remplacés. La reprise des étapes interrompues et la vérification finale restent obligatoires.

Mesure contrôlée avec Qwen3.5 4B : la même requête passe de 4 606 à 4 283 jetons d’entrée, soit 323 jetons économisés, avec le même objectif et les mêmes outils. Cette mesure concerne un cas précis ; elle ne prouve pas la réussite d’un projet complet.

Les mécanismes précédents restent actifs : compactage préventif du chat, comptage exact sur le moteur local reconnu, rééquilibrage de la sortie et chargement progressif des outils. Aucun bouton supplémentaire n’est nécessaire.
