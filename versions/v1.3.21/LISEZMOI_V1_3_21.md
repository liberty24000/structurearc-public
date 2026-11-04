> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.21

**3 novembre 2026 — accès web local automatique sur le port 8092.**

À chaque lancement de StructureArc, l’accès HTTPS démarre sur l’adresse privée du PC, toujours au **port 8092**, sans activation dans les paramètres. Le PC et StructureArc doivent rester ouverts ; la réduction dans la zone de notification conserve le service. Quitter complètement l’application le ferme. Cela n’installe aucun service Windows et ne lance pas StructureArc à l’ouverture de Windows.

En l’absence de réseau privé, le service attend et réessaie toutes les trois secondes. Il suit les changements d’adresse IP. Si le port 8092 est occupé, il affiche le problème et réessaie au même port, sans fermer une autre application ni choisir un port de remplacement. Une adresse IP peut changer selon le routeur ; le port reste fixe.

Les paramètres indiquent l’état et permettent d’obtenir le lien de connexion ou le certificat public pour le téléphone. Un arrêt explicite ne vaut que pour la session en cours : le prochain lancement réactive le service. L’arrêt d’urgence reste respecté.

La connexion du téléphone utilise HTTPS et l’appairage existant. Le certificat d’autorité doit être approuvé sur le téléphone et le pare-feu doit permettre l’accès sur le réseau privé. Cette version ne change pas automatiquement les permissions du système. Le téléphone peut ensuite retrouver sa session appairée ; une première connexion demande toujours un lien depuis le PC.

Le serveur local et le serveur réseau partagent leur relais de commandes ; les identifiants de requête sont uniques pour éviter les collisions entre navigateurs. Les nouvelles tentatives ne renouvellent pas les liens de connexion déjà obtenus.

Vos projets, conversations, clés et bases personnelles ne font pas partie de l’installateur ni du dépôt public.

## Vérifications

- Suite native finale : **952 réussis, 0 échec, 18 ignorés sur 970**, en **211,30 secondes**.
- Interface ciblée : **36 cas uniques réussis**, contrôle TypeScript réussi. Les échecs initiaux de fixtures et leurs corrections restent consignés dans les journaux.

Lire `LIMITES_V1_3_21.md` pour la portée des tests. Cette livraison ne prouve pas l’autonomie complète sur tout projet ; les essais réels précédents 12 et 13 ont échoué. Aucune nouvelle validation d’appel Anthropic authentifié, de téléphone physique, d’annulation acoustique d’écho ou d’intégration Moshi n’est revendiquée.

## Paquet installé et contrôlé

Production TypeScript/Vite et compilation Windows réussies. Autotests du binaire brut et installé : **18/18 chacun**, code **0**. Installateur et exécutable installé : signatures Authenticode **Valid**. Mise à niveau réelle silencieuse au code **0**, avec égalité exacte des données contrôlées avant/après et intégrité SQLite correcte avant le premier lancement normal. Aucun aller-retour de désinstallation isolée.

Deux lancements réels successifs de la version installée ont été contrôlés **sans activation manuelle** : écoute sur l’IP privée au port **8092**, connexion HTTPS avec autorité explicitement approuvée seulement dans le client de test et vérification du nom/IP, page de connexion, manifeste et icônes répondant **200**. Le certificat d’autorité est conservé entre les deux lancements. Aucun changement du pare-feu ou du magasin de certificats du système n’a été réalisé. Cela valide le service sur le PC hôte, pas l’accès physique depuis un téléphone à travers le réseau.

Installateur `StructureArc_1.3.21_x64-setup.exe` : **24241976 octets**, SHA-256 `335425c0b5f12fe10c658a41083648a8563fe9e024f1f7f3147988513ce89dc2`. Binaire brut SHA-256 `102c3281a206d72d727ab1781cb33b68640e445fa02d7fe0fe022f7259a40789`. Exécutable installé : **15236256 octets**, SHA-256 `0cac1ffdd372f90bb9550b47327cd7dd57e8b5affe355ef45137597925c3be72`.

Le contenu de l’installateur a été examiné : application, runtime local vérifié et composants d’installation ; aucun projet, historique, secret ou base personnelle.

Le profil supplémentaire `VERIFY_X509_STRICT` de Python 3.13 refuse le certificat existant pour absence d’Authority Key Identifier. Les contrôles HTTPS ci-dessus conservent la vérification obligatoire de chaîne et de nom/IP, avec ce seul profil strict supplémentaire désactivé dans le client de test. Ils ne prouvent pas la conformité à ce profil strict OpenSSL ni la compatibilité de tous les navigateurs. Aucun certificat système ni paramètre de l’application n’a été modifié pour ce contrôle.
