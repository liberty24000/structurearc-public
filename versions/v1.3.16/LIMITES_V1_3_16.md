> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.16

## Fonctionnement vérifié pendant le développement

- Réorientation avec un modèle local réel : une nouvelle consigne envoyée pendant une réponse a remplacé la réponse en cours. Un scénario court a terminé 4,15 secondes après la nouvelle consigne ; ce résultat n'est pas une garantie générale de latence.
- Plan : une tâche interrompue puis relancée a réellement exécuté les huit tests du projet de démonstration. Un cycle de trois étapes a terminé ; l'analyse et la vérification ont réellement exécuté les tests. La réalisation a repris le rapport précédent sans nouvelle exécution propre.
- Deux vrais processus ont fonctionné ensemble ; l'arrêt du premier a laissé le second fonctionner et terminer. Les résultats sont restés distincts après réouverture du stockage.
- Les suites automatisées couvrent notamment le chat, la reprise, l'isolation, les processus, les autorisations, les scripts de projet, l'OCR et les composants vocaux. Les fournisseurs et microphones simulés dans ces suites ne prouvent pas une performance générale du modèle ou du matériel.

Les contrôles de l'installateur et du binaire de production sont enregistrés séparément dans les preuves de livraison de l'éditeur. Un contrôle non exécuté ou non concluant n'est pas compté comme réussi.

Contrôles finaux sur cette livraison : 297 tests d'interface réussis ; suite native principale 791 réussis et 15 ignorés ; démarrage et auto-test du binaire réussis ; 107 contrôles de fenêtre, 16 contrôles IA avec modèles locaux réels, 23 contrôles de présentation du chat et 17 contrôles d'installation réussis. Les 36 scénarios de la chaîne historique complète n'ont pas été rejoués. Un test de fenêtre attendait encore quatre modules à venir : son attente a été mise à jour à trois après livraison des tâches, puis le scénario entier a réussi. Le premier journal global conserve cet échec initial et un scénario IA non exécuté ; leurs rejeux sont conservés séparément.

## Limites connues

- Autonomie et auto-amélioration expérimentales : aucun résultat ne garantit la réalisation de n'importe quel projet sans intervention. Un rapport d'agent ne remplace pas un contrôle indépendant.
- Les nouvelles consignes visent le tour ou les workers actifs. Les prochaines étapes déjà enregistrées ne sont pas systématiquement réécrites. Une opération synchrone déjà lancée peut finir avant la prise en compte d'une nouvelle consigne ; l'attente du premier fragment du modèle peut aussi retarder cette prise en compte.
- Les dépendances du plan imposent un ordre. Plusieurs processus ou lectures simultanés ne signifient pas plusieurs générations simultanées : cela dépend du runtime, du modèle et des ressources disponibles.
- La mémoire des erreurs est une mémoire d'observations, pas une conscience ni une preuve d'amélioration générale de l'intelligence.
- Voix : moteurs Windows détectés et composants testés, mais reconnaissance micro et lecture audible de bout en bout non validées sur toutes les machines. Le micro se coupe pendant la lecture. Moshi, Unmute, Kyutai STT et Pocket TTS ne sont pas installés ni intégrés dans cette livraison.
- Web : lecture HTTPS de texte public. Les sites nécessitant JavaScript, connexion ou CAPTCHA ne sont pas universellement pris en charge. L'accès depuis un téléphone dépend également de l'appairage et de la configuration réseau locale.
- Les sorties des processus en arrière-plan sont disponibles à la fin, sans diffusion continue. Après un arrêt de l'application, les processus interrompus ne sont pas relancés automatiquement.
- Les scripts du terminal ordinaire et le shell avancé suivent des autorisations différentes. L'activation du shell avancé reste explicite et bornée. Les commandes s'exécutent avec les droits du compte Windows.
- La validation matérielle reste limitée à une machine Windows ; compatibilité multi-GPU, tous les sites et toutes les applications du bureau ne sont pas déclarés validés.
