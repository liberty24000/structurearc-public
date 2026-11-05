> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites connues — StructureArc 1.3.56

La conservation du contexte est vérifiée séparément de la réussite du projet. L'essai Qwen3.5 4B r33, effectué pendant le développement avant le dernier correctif de conservation des diagnostics, conserve l'objectif dans 54 requêtes mesurées malgré 15 compactages. Il échoue au contrôle indépendant : seul le premier fichier est présent et il est incomplet. Le projet complet reste non qualifié. Aucun livrable n'a été réparé manuellement et aucun critère n'a été retiré.

La reconnaissance des sorties textuelles et commandes explicites est bornée ; elle ne comprend pas universellement toute formulation, tout format ou toute commande. Une lecture complète et une étape terminée ne remplacent pas la vérification fonctionnelle finale.

La mesure exacte concerne le moteur local reconnu. Les autres parcours conservent une estimation de contexte ; aucun comptage exact universel n'est revendiqué. Des instructions incompressibles trop volumineuses produisent une erreur explicite.

L'intermittence précédemment observée dans les tests parallèles du coffre Windows reste à expliquer. Les tests ignorés ne sont pas présentés comme réussis. Aucun nouveau contrôle physique Android ni essai acoustique n'est revendiqué.

Les projets personnels, conversations, mémoires, certificats privés et clés API ne font pas partie de l'installateur public. Les preuves de mise à jour contrôlent séparément leur conservation sur le poste testé.
