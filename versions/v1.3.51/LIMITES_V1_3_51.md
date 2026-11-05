> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.51

- L'optimisation préventive repose sur une estimation. Le comptage exact est réalisé pour le runtime local b11643 reconnu ; il ne faut pas confondre les chiffres estimés et mesurés. Les autres fournisseurs conservent leur contrôle de taille et la récupération sur refus.
- Un objectif, des décisions ou un catalogue d'outils obligatoires peuvent dépasser à eux seuls la fenêtre disponible. L'optimiseur ne peut pas inventer de mémoire supplémentaire ni supprimer ces exigences. La capacité effective du modèle et les ressources matérielles restent déterminantes.
- La conservation d'un contexte compact et une réponse correcte sur un cas synthétique ne prouvent pas la réussite d'un projet complet. Les essais P2 antérieurs sur Qwen4B et Qwopus9B ont échoué ; le vérificateur indépendant et ses exigences restent inchangés.
- L'échec initial du test synthétique sur Qwen0,5B a montré que le modèle pouvait demander des précisions alors que l'objectif était présent. L'ordre du point de reprise a été corrigé ensuite, mais ce modèle échoue encore à ce contrôle. Qwen1,5B, Qwen4B, NeoHorse9B et Qwopus9B le réussissent. Les anciennes preuves et les nouveaux essais restent séparés.
- Les lectures longues peuvent être présentées sous forme d'extraits : le modèle doit relire les parties nécessaires. Les fichiers, l'historique enregistré et les diagnostics réels des commandes ne sont pas supprimés par cette optimisation.
- Les protections des écritures bornées restent conservatrices : un fichier valide exactement à la borne peut être signalé comme fragment. Un texte plus court ne prouve pas sa justesse fonctionnelle.
- Aucun nouvel essai physique sur Android ni de synthèse vocale complète n'est revendiqué dans cette livraison du moteur de contexte. Les contrôles d'installation vérifient séparément les ressources vocales et les associations conservées.
- La cohabitation d'un modèle 9B et de Kyutai sur 8 Go de mémoire graphique n'est pas qualifiée. Le subconscient reste un mécanisme de mémoire et consolidation, sans affirmation de conscience ou de sentiments humains.

Les preuves finales de cette version sont renseignées dans les documents de livraison ; aucune preuve d'une autre version n'est assimilée à une validation de celle-ci.

- Sur cette version, le projet complet P2 avec Qwen1,5B échoue après 51 secondes au stade de l’analyse : la définition est enregistrée mais aucune inspection réelle n’est obtenue, et aucun livrable n’est produit. La fenêtre de 12288 jetons suffit à ces trois échanges ; cet échec ne vient donc pas d’un déclenchement de la compression. Aucun succès de projet complet n’est revendiqué.
