> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.59

Le pilotage des agents conserve maintenant les contrôles encore en échec entre deux tentatives, dans un registre natif lié au projet, au cycle et à la sous-étape. Une correction en cours de réponse ne vide plus ce registre. La nouvelle tentative reçoit les contrôles à reprendre ; une réussite sur un autre contrôle ou dans un autre dossier ne peut pas les valider.

Une sous-étape peut bénéficier d'une reprise automatique supplémentaire lorsque son diagnostic natif confirme des vérifications persistées en attente. Cette reprise est limitée à une tentative, conservée après redémarrage, et garde les étapes déjà terminées. Le contrôle final du projet reste obligatoire.

Le chat reste l'interface centrale. Aucun service Harness ni framework externe n'est installé.
