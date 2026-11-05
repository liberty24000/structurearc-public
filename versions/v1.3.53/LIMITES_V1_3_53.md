> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.53

- L’optimisation économise du contexte, mais ne rend pas un petit modèle infaillible. Elle ne supprime aucune exigence pour faire tenir une requête.
- La comparaison de jetons porte sur une requête réelle Qwen3.5 4B, avec restauration de la seule copie du plan comme témoin. Aucun résultat de vitesse ou de réussite générale n’en est déduit.
- Deux tentatives 9B ont été refusées avant le démarrage par le contrôle de mémoire disponible. Aucune génération n’a eu lieu et aucune amélioration 9B n’est revendiquée à partir de ces refus.
- Le modèle 1,5B n’a pas enregistré la définition demandée et n’a créé aucun livrable dans l’essai r22. Le format structuré ne garantit pas la pertinence des actions.
- L’essai complet 4B r24 échoue après 591 715 ms, sans annulation externe. Il a créé package.json et un cli.cjs incomplet, ainsi que deux fichiers de contrôle auxiliaires. test.cjs et README.md manquent. Le vérificateur indépendant échoue ; le moteur a refusé un flux local invalide après sa reprise. Neuf compactages automatiques et une reprise de sous-tâche ont réellement eu lieu, mais ils ne prouvent pas la réussite du projet. Aucun livrable du modèle n’a été corrigé manuellement.
- Aucun nouvel essai Android physique ni nouvelle exécution vocale complète n’est revendiqué. La voix locale et la confiance mobile restent des vérifications distinctes.
- Aucun succès de projet complet sur tous les modèles n’est revendiqué. La cohabitation 9B/Kyutai sur 8 Go reste non qualifiée.
