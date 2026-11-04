> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.31 - Chat mobile et diagnostic vocal

Correction vocale: l'enregistrement du premier message ne remonte plus le composant vocal. Le micro et la session peuvent rester actifs dans le nouveau chat. Defaut reproduit par un test avant correction; 141 tests vocaux passent apres correction. La validation sur un vrai telephone apres installation reste necessaire.

Le site ouvre directement un chat vierge dans le dernier projet disponible. Aucun chat vide n'est enregistre avant le premier message. Les projets archives ou dont le dossier est absent ne sont pas choisis automatiquement.

Une invitation discrete permet d'installer l'application lorsque le navigateur offre reellement cette possibilite. Elle peut etre masquee; le certificat et les instructions restent dans les parametres. L'acceptation d'une invitation n'est pas presentee comme une preuve d'installation terminee.

Les discussions peuvent etre supprimees individuellement avec confirmation. La memoire apprise du projet est conservee. Une suppression est refusee pendant une execution active afin de ne pas effacer une conversation encore utilisee.

Le mode vocal affiche son etat, le niveau du micro et les erreurs de demarrage. Des journaux limites en taille permettent de suivre les operations du pont et les etapes audio sans enregistrer les contenus de conversation ou les cles.

Validation de l'interface: 501 tests reussis sur 60 fichiers. Le code natif fonctionnel est celui de la version 1.3.29, dont 1046 tests passent (18 ignores); cette validation precedente ne remplace pas les controles de l'executable 1.3.31.

Installation reelle reussie, signature valide et autotests brut/installes 18/18. Projets, conversations et messages compares ligne par ligne: conservation exacte. Apres relance, sept ressources mobiles accessibles en HTTPS strict, autorite locale inchangee. Installation physique Android et correction vocale sur telephone a retester.
