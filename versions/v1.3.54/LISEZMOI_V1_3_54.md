> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.54

Le chat local reprend plus efficacement après un appel d’outil invalide. Lorsque des actions restent nécessaires, il conserve un format structuré pour la suite du tour au lieu de revenir immédiatement au format qui a échoué. Les résultats déjà obtenus sont conservés et les appels rejetés ne sont pas exécutés.

Lorsqu’un petit modèle atteint la limite d’un fragment de fichier, StructureArc lui propose de le poursuivre dès que ce fragment a été relu. Une modification refusée permet de relire l’état du fichier avant de réessayer. Les contrôles du contenu et les tests du projet restent nécessaires.

Pendant l’analyse locale, deux questions de méthode déjà répondues automatiquement peuvent déclencher une tentative ciblée d’enregistrement de l’objectif. Les vraies questions destinées à l’utilisateur restent disponibles ; aucun droit supplémentaire n’est accordé.

L’optimisation automatique du contexte reste active, sans bouton supplémentaire. Ces améliorations ne garantissent pas qu’un petit modèle termine correctement n’importe quel projet.
