> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.34 — Décisions recommandées en mode Auto

Les questions du chat présentent des choix numérotés. Le premier est signalé « recommandé » et sélectionné par défaut. En mode Auto, une décision de méthode est prise automatiquement et le travail continue sans attendre un clic. Les anciennes questions en attente sont également traitées à la réouverture de leur chat ; plusieurs choix successifs déclenchent une seule reprise finale.

Chaque réponse automatique reste identifiée comme une décision du logiciel dans l’historique et le journal. Elle n’est pas présentée comme un message écrit par l’utilisateur. Le mode manuel conserve le choix explicite. Si une information indispensable est inconnue, le modèle peut la demander avec une vraie pause ; une recommandation ne crée pas de nouvelle autorisation d’accès.

Validation : 1 054 tests natifs réussis, aucun échec, 18 ignorés ; 505 tests d’interface réussis dans 60 fichiers. Les scénarios couvrent la poursuite de la boucle d’outils après un choix, plusieurs questions successives, la persistance, l’absence de doublons et la distinction entre décision automatique et réponse humaine. Le protocole d’outil reste compact pour les petits modèles.

Limites : ces tests contrôlent le logiciel et des scénarios de fournisseur simulé. Ils ne garantissent pas que chaque modèle proposera une bonne recommandation ni qu’il terminera tout projet. La qualification complète du modèle local 4B reste en cours après un essai réel en échec. La conversation vocale et l’installation PWA sur téléphone physique restent à confirmer ; Moshi/Kyutai n’est pas intégré.

Installation réelle : installateur et application installée signés et vérifiés ; autotests brut et installé 18/18. Projets, conversations et messages exactement conservés avant/après mise à jour. Version 1.3.34 visible après relance ; sept ressources locales vérifiées en HTTPS strict sur le port 8092, certificat racine inchangé.
