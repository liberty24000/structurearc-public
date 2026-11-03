> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.21

**3 novembre 2026 — démarrage automatique HTTPS local, port 8092.**

La suite native finale compte **952 réussis, 0 échec, 18 ignorés sur 970**, en **211,30 secondes**. Les ignorés ne sont pas des réussites. Les six tests de régression supplémentaires couvrent attente réseau, port occupé, changement d’adresse, arrêt de session, arrêt d’urgence/reprise du listener, concurrence entre arrêt et création et unicité des identifiants de requête.

Les scénarios réseau isolés utilisent de vraies sockets loopback, un moteur simulé et une identité de fixture ; ils ne constituent pas un essai HTTPS sur un téléphone. Le premier passage a échoué sur un en-tête Host incorrect dans une fixture utilisant une seconde adresse loopback ; seule la fixture a été corrigée. Le deuxième exécutable de tests ne se chargeait pas car le stockage concret du relais introduisait des dépendances d’interface Windows dans le banc de tests. Le relais partagé utilise désormais l’interface Backend, avec la même implémentation Tauri en production ; le passage final complet est réussi.

Les **36 cas d’interface uniques** et le contrôle TypeScript sont réussis. Les premières erreurs de fixtures sont conservées, et les suites ne sont pas additionnées en un total général.

## Conditions d’accès

StructureArc doit tourner sur le PC, y compris minimisé dans la zone de notification. Le réseau privé doit être accessible ; aucun démarrage automatique de Windows, service permanent, réservation DHCP ou ouverture automatique du pare-feu n’est ajouté. L’adresse peut changer ; le port demeure 8092. Un port déjà occupé entraîne une attente explicite, jamais l’arrêt de son propriétaire ou un autre port.

La confiance dans le certificat, l’appairage et les permissions du navigateur restent nécessaires. Une nouvelle adresse est une nouvelle origine pour le navigateur et peut nécessiter de réouvrir le lien ou d’actualiser le raccourci installé. Aucun essai sur téléphone physique ni test acoustique n’a été exécuté pour cette version.

## Fonctionnalités héritées

Le fournisseur Anthropic facultatif et les fonctions vocales existantes sont conservés ; aucun appel réel avec une clé Anthropic ni nouvelle validation matérielle n’est revendiqué. Moshi/Kyutai n’est pas intégré. Les essais réels de projet autonome 12 et 13 ont échoué : ce correctif ne démontre pas qu’un modèle peut réussir tout projet sans intervention.

Les données personnelles restent sur le PC ; elles ne sont pas des ressources de l’installateur et ne sont pas publiées.

## Paquet installé et contrôlé

Production TypeScript/Vite et compilation Windows réussies. Autotests du binaire brut et installé : **18/18 chacun**, code **0**. Installateur et exécutable installé : signatures Authenticode **Valid**. Mise à niveau réelle silencieuse au code **0**, avec égalité exacte des données contrôlées avant/après et intégrité SQLite correcte avant le premier lancement normal. Aucun aller-retour de désinstallation isolée.

Deux lancements réels successifs de la version installée ont été contrôlés **sans activation manuelle** : écoute sur l’IP privée au port **8092**, connexion HTTPS avec autorité explicitement approuvée seulement dans le client de test et vérification du nom/IP, page de connexion, manifeste et icônes répondant **200**. Le certificat d’autorité est conservé entre les deux lancements. Aucun changement du pare-feu ou du magasin de certificats du système n’a été réalisé. Cela valide le service sur le PC hôte, pas l’accès physique depuis un téléphone à travers le réseau.

Installateur `StructureArc_1.3.21_x64-setup.exe` : **24241976 octets**, SHA-256 `335425c0b5f12fe10c658a41083648a8563fe9e024f1f7f3147988513ce89dc2`. Binaire brut SHA-256 `102c3281a206d72d727ab1781cb33b68640e445fa02d7fe0fe022f7259a40789`. Exécutable installé : **15236256 octets**, SHA-256 `0cac1ffdd372f90bb9550b47327cd7dd57e8b5affe355ef45137597925c3be72`.

Le contenu de l’installateur a été examiné : application, runtime local vérifié et composants d’installation ; aucun projet, historique, secret ou base personnelle.

Le profil supplémentaire `VERIFY_X509_STRICT` de Python 3.13 refuse le certificat existant pour absence d’Authority Key Identifier. Les contrôles HTTPS ci-dessus conservent la vérification obligatoire de chaîne et de nom/IP, avec ce seul profil strict supplémentaire désactivé dans le client de test. Ils ne prouvent pas la conformité à ce profil strict OpenSSL ni la compatibilité de tous les navigateurs. Aucun certificat système ni paramètre de l’application n’a été modifié pour ce contrôle.
