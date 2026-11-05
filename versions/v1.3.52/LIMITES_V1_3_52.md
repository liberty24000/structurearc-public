> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.52

- La reprise structurée est réservée au moteur local b11643 reconnu. Elle impose une forme d’action, mais ne garantit ni la pertinence de l’outil, ni l’exactitude des arguments, ni la justesse du code. Le fournisseur cloud et les moteurs non reconnus conservent leur protocole.
- Une réponse incomplète ou un outil non déclaré est refusé. Les permissions existantes restent appliquées par les exécuteurs ; le format JSON n’accorde aucun accès supplémentaire.
- Un contexte trop grand même avec le budget minimal reste impossible à exécuter. Le rééquilibrage ne crée pas de mémoire et ne remplace pas les exigences par un résumé fictif. Les sorties peuvent encore atteindre leur limite ; elles restent soumises aux contrôles de complétude.
- L’essai P2 r14 sur Qwen1,5B a validé une inspection après reprise ciblée et un plan natif, puis échoué pendant la réalisation. L’essai r15 avec reprise structurée a produit des appels, mais répété une lecture sur un chemin inexistant sans créer de livrable. L’essai r16 sur Qwen4B a répété des questions de méthode déjà résolues automatiquement, sans réaliser le projet. Ces échecs ne sont pas effacés des preuves.
- Le prototype synthétique JSON a choisi les deux outils attendus, mais a utilisé « root » au lieu de « . » pour un chemin : un format correct ne vaut pas des arguments corrects.
- Le premier essai 9B r17 a été arrêté par un dépassement de contexte mesuré ; son résultat ne valide pas le rééquilibrage ajouté ensuite. Les essais successifs restent séparés.
- Aucun nouvel essai sur téléphone Android physique ni nouvelle exécution vocale complète n’est revendiqué ici. La voix locale, les associations mobiles et les données personnelles restent des vérifications distinctes.
- La cohabitation d’un modèle 9B et de Kyutai sur 8 Go de mémoire graphique n’est pas qualifiée. Le subconscient demeure un mécanisme de mémoire et de consolidation, sans affirmation de conscience ni de sentiments humains.

Aucun succès de projet complet sur tous les petits modèles n’est revendiqué.

Le test r18 a validé le rééquilibrage mesuré sur le 9B et terminé l’analyse avec cinq étapes. La réalisation a ensuite échoué : son entrée seule occupait 4 318 jetons pour une fenêtre de 4 096. Aucun livrable et aucun succès de projet complet. Cet essai précède le chargement des outils adapté à la fenêtre.

Le test r19 a lui aussi échoué sans livrable : le plan était admis, puis le commentaire final de l’analyse dépassait le contexte. La transmission native ajoutée ensuite est conditionnée à une inspection réelle et à un plan courant validé ; elle ne qualifie pas la réalisation.

Le test r20 confirme la transmission native et le démarrage automatique de la réalisation sur Qwopus9B. Il a créé package.json, puis échoué après deux lectures : 3 841 jetons d’entrée, 256 réservés pour la sortie et 32 de marge dépassent la fenêtre de 4 096. Les trois autres fichiers requis sont absents ; le vérificateur indépendant retourne un échec. Aucun fichier du modèle n’a été réparé manuellement et aucun critère n’a été retiré.
