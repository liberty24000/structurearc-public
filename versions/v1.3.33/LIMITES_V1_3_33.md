> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.33 — Retour automatique des tests CommonJS

Les modifications de modules CommonJS peuvent maintenant déclencher leurs tests voisins, comme les modules ESM. Les fichiers test.cjs/test.mjs et les variantes .test/.spec correspondantes sont reconnus. Après une réparation du module, les tests sont relancés et leur résultat réel est transmis au modèle. La recherche reste limitée au dossier concerné et les autorisations du projet restent appliquées.

La revue des tests reconnaît aussi les fichiers test.cjs autonomes. Elle avertit le modèle lorsqu’un test ne fait qu’afficher une erreur sans assertion ni statut d’échec. Cet avertissement est heuristique : il ne remplace pas un contrôle indépendant et ne transforme pas une sortie terminal en preuve de conformité.

Un essai réel avec le modèle local 4B a confirmé que « continue » reprend l’exécution et les modifications. Le projet produit échoue cependant encore au contrôle indépendant. Cet essai n’est pas compté comme une réussite et ne qualifie pas l’autonomie générale du modèle.

Validation du moteur : 1 050 tests natifs réussis, aucun échec, 18 ignorés. Une régression reproduit l’absence de retour d’erreur avant correction, puis vérifie l’erreur JavaScript réelle, la réparation et le respect des droits d’exécution.

Limites : la qualification complète des petits modèles continue. Les contrôles automatiques ajoutés concernent les modules Node ESM/CommonJS ; ils ne choisissent pas arbitrairement un moteur pour TypeScript ou un autre framework. La conversation vocale et l’installation PWA sur le téléphone physique restent à confirmer. Moshi/Kyutai n’est pas intégré. Les fonctionnalités précédemment livrées sont conservées.

Installation réelle : signature valide, autotests du binaire brut et installé 18/18, projets/discussions/messages exactement conservés. Après relance, sept ressources mobiles répondent en HTTPS avec vérification stricte du certificat, sur le port 8092. Ces contrôles PC ne remplacent pas un essai sur le téléphone physique.
