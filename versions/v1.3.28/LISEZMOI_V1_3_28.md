> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.28 — Certificat directement sur le téléphone

La page de connexion propose **Télécharger le certificat**, accessible avant connexion, et les étapes Android/Chrome. Le fichier public arrive directement dans Téléchargements sur le téléphone. Le même lien est présent dans les paramètres web. Aucun transfert manuel depuis le PC n’est nécessaire.

Le téléchargement fournit uniquement l’autorité publique propre au PC, sous le nom StructureArc-local.cer, avec le type de certificat adapté. Il conserve les contrôles HTTPS et d’hôte. La clé privée n’est jamais servie.

Validation : **47 tests natifs web réussis, aucun échec, trois ignorés** ; **neuf tests d’interface mobile réussis** ; TypeScript/Vite et fabrication signée réussis ; autotests brut/installé **18/18**. Mise à niveau réelle réussie, données contrôlées exactement conservées. Après relance, sept ressources contrôlées en HTTPS strict ; certificat téléchargé sans session identique octet pour octet à l’autorité du PC.

Au premier accès, Chrome peut afficher un avertissement avant de charger la page : un bouton du site ne peut pas supprimer cet écran. L’installation du certificat reste une action dans les paramètres Android. Comparez l’autorité avec celle affichée sur votre PC avant de lui faire confiance. Fermez puis rouvrez Chrome après installation ; la page doit ensuite s’ouvrir sans avertissement. Installation physique sur téléphone non testée. Le PC doit rester ouvert et joignable sur le même réseau.

L’autorité reste valable dix ans ; les certificats serveur se renouvellent sous cette autorité. Aucun certificat illimité n’est annoncé. Aucun projet personnel, historique, clé privée ou certificat propre au PC n’est embarqué dans l’installateur public.
