> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.57

Les erreurs de syntaxe détectées lors du lancement direct d’un script Node restent désormais des contrôles à résoudre. Une écriture suivie d’une relecture ne suffit plus à valider l’étape. Le chat peut corriger puis vérifier le fichier dans la même discussion, sans nouvelle confirmation lorsque les autorisations existent déjà.

Les erreurs du fichier principal et celles des modules importés sont distinguées. Vérifier uniquement la syntaxe du fichier principal ne valide pas un module importé défectueux. Les erreurs normales sur des arguments ou des données JSON invalides ne sont pas confondues avec ces erreurs de programme.

Les accès courts au coffre Windows sont coordonnés entre les certificats locaux et les clés API. Le défaut intermittent reproduit dans les tests HTTPS parallèles ne se reproduit plus dans vingt séries avec ce correctif sur le poste de référence.

La navigation mobile permet de changer de projet et de revenir à la discussion générale. Le contexte continue à s’optimiser automatiquement, sans bouton supplémentaire. Les limites de qualification sont décrites dans le document joint.
