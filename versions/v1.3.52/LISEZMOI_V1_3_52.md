> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.52

Cette version améliore les reprises des modèles locaux lorsqu’une mission se bloque avant une action réelle.

- Après une réponse sans inspection, une reprise ciblée propose les outils de lecture déjà autorisés avec un budget court, puis rétablit le fonctionnement normal après une observation réelle.
- La correction d’un plan exige désormais un appel d’outil dans la requête au fournisseur. Un plan admis ne signifie toujours pas que le projet est réalisé.
- Sur le moteur local b11643 reconnu, les reprises d’actions requises peuvent utiliser un objet JSON strict : un seul outil déclaré et ses arguments. Ce format passe par les mêmes exécuteurs et permissions. Le JSON technique n’est pas affiché comme une réponse dans le chat.
- Si le contexte exact déborde et que le compactage ne peut plus le réduire, le maximum de réponse peut être rééquilibré avec la place restante, en conservant une marge de 32 jetons et un minimum de 256 jetons de réponse. La requête finale est recomptée avant génération ; aucune consigne n’est supprimée pour la faire tenir.

Les mécanismes de la 1.3.51 restent présents : compactage automatique du contexte, conservation des objectifs, décisions, observations et historique enregistré.

Les vérifications natives couvrent les réponses tronquées, les outils non déclarés, les budgets incohérents, la conservation exacte du contexte et le retour aux outils ordinaires après inspection. Les résultats des modèles réels et leurs limites sont décrits dans LIMITES_V1_3_52.md. La réussite d’un contrôle de protocole ne qualifie pas une autonomie générale.

Sur un moteur local dont la fenêtre est mesurable, les groupes d’outils sont désormais chargés progressivement dès que leur déclaration occupe une part trop importante de cette fenêtre. Les outils de base restent présents et les autres groupes peuvent être chargés à la demande. Le contrôle exact du contexte reste exécuté avant chaque génération.

Si une analyse a réellement inspecté le projet et enregistré un plan valide, un dépassement de contexte lors du commentaire final ne détruit plus ce travail : un compte rendu natif des observations transmet le plan à la réalisation. Une définition modifiée invalide toujours l’ancien plan ; les contrôles des livrables et des tests restent obligatoires.
