> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.32 — Distinguer absence et refus d’accès

Un essai réel avec Qwen3.5 4B a montré une demande d’autorisation inutile : l’agent d’analyse interprétait un dossier nouveau comme un accès refusé. Aucun livrable n’avait été créé dans cet essai.

Le moteur signale maintenant un fichier ou dossier absent avec le code `not_found`, sans le présenter comme un refus de permission. Une erreur système de lecture n’est plus automatiquement convertie en absence. L’analyse rappelle que la création appartient à l’étape de réalisation et peut s’appuyer sur l’inspection du dossier parent existant.

Cette correction s’applique aux outils du chat et des agents, locaux et cloud. Elle ne change pas les autorisations et ne transforme pas une lecture échouée en preuve d’inspection réussie.

Les fonctionnalités livrées en 1.3.31 sont conservées, dont la continuité vocale lors du premier message, l’accueil mobile sur un chat vierge, l’invitation PWA et la suppression individuelle des discussions avec conservation de la mémoire apprise.

Limites : un test de régression ne prouve pas l’autonomie générale du modèle. Les essais complets de projets avec les modèles locaux continuent. Le parcours vocal et l’installation PWA sur le téléphone physique restent à confirmer. Le système de voix Moshi/Kyutai n’est pas intégré.

Validation : 1 047 tests natifs réussis, aucun échec, 18 ignorés (suite exécutée en série). Compilation TypeScript/Vite et installateur signé réussis. Autotests du binaire brut et installé : 18/18. Projets, conversations et messages comparés exactement avant/après installation ; sept ressources mobiles vérifiées en HTTPS strict après redémarrage. Essai réel du modèle après correction encore en cours.
