> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.56

Le contexte est optimisé automatiquement lorsqu'il approche de la capacité du modèle. L'objectif complet, l'étape courante, les décisions et les résultats nécessaires à la reprise sont conservés. L'historique enregistré et les fichiers du projet ne sont pas supprimés.

La consigne exacte d'une sous-étape est maintenant placée après les rapports de référence, y compris lors de la reprise du contexte. Les nouvelles précisions utilisateur continuent de prévaloir. L'ordonnanceur enchaîne les étapes sans demander une commande « continue » pour chaque livrable.

Les sorties textuelles nommées reconnues demandent une lecture native complète. Une commande explicitement attendue doit réellement réussir ; une réussite antérieure à une modification ne valide pas la nouvelle version. Les livrables manquants disposent d'une reprise automatique bornée.

Les retours d'édition et d'exécution conservent désormais leurs diagnostics courts lorsque le contexte est réduit. Les extraits ordinaires de fichiers restent compressibles. Aucun bouton supplémentaire n'est nécessaire.

Ces améliorations ne garantissent pas la réussite de tout projet avec tout modèle. Voir les limites jointes.
