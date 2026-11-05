> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.51

Le chat optimise automatiquement son contexte avant saturation : il estime le poids des messages, des outils et de la réponse réservée avant chaque requête. À partir de 85 % de la fenêtre estimée, il prépare un point de reprise et l'utilise seulement s'il économise réellement de la place.

L'objectif complet, les précisions utilisateur, les décisions enregistrées, le plan, les fichiers déjà écrits, les processus lancés, les fragments incomplets et les vérifications en échec restent disponibles. Les échanges récents et les diagnostics d'exécution sont conservés ; les longs extraits de lecture peuvent être abrégés avec une indication explicite de relecture. La demande actuelle est placée après les observations pour rester clairement identifiable par les petits modèles.

Cette optimisation ne supprime pas la conversation enregistrée, ne modifie aucun fichier et n'exécute aucun outil. Elle ne crée aucune permission. Elle ne demande pas un nouveau message « continue ». Les journaux indiquent les tailles estimées avant/après, le déclencheur et la réserve de réponse, sans recopier les contenus privés.

Le runtime local b11643 mesure ensuite la requête réellement formatée et réserve sa sortie avant génération. Si le fournisseur refuse encore la taille, une réduction supplémentaire peut reprendre le travail. Une requête impossible à réduire n'est pas renvoyée indéfiniment ; les exigences ne sont jamais supprimées pour annoncer une réussite artificielle.

La version inclut également les protections locales de la 1.3.50 : contenus d'écriture structurés et bornés, suivi des fragments à poursuivre, reprise des sous-étapes et correction du format des plans. La navigation mobile, le chat général, les appareils de confiance et la voix française féminine Kyutai sont conservés.

Les projets, conversations, clés et certificats privés restent personnels et ne sont pas distribués. Voir LIMITES_V1_3_51.md pour le périmètre vérifié et les limites restantes.
