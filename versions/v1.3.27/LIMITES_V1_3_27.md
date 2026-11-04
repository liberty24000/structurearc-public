> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.27

- Un petit modèle peut encore mal choisir un outil, produire des arguments incorrects ou ne pas parvenir au résultat. Le durcissement du protocole empêche les faux succès ; il ne garantit pas la réussite de tout projet avec tout modèle.
- Les commandes simples et chemins clairement reconnus sont rapprochés des preuves d’exécution. Une formulation ambiguë ou une commande complexe n’est pas annoncée comme entièrement comprise ou vérifiée sémantiquement.
- Le travail parallèle dépend des ressources mesurées et des dépendances entre tâches. Une limite configurée est un plafond, pas un nombre d’agents systématiquement lancés. L’augmentation du contexte cloud et du parallélisme peut augmenter la consommation de l’API.
- Les tâches des anciens chats sans association native certaine ne sont pas attribuées automatiquement à une conversation par recherche dans leur texte.
- Une question de l’agent suspend le travail jusqu’à la réponse humaine. Une permission manquante, un arrêt explicite, un refus du fournisseur ou une ressource indisponible restent des états réels à signaler.
- Les outils conservent leurs validations propres. Un bouton d’autorisation ne rend pas disponible un programme absent et ne transforme pas une commande invalide en commande exécutable.
- Le renouvellement du certificat serveur conserve l’autorité locale. Une autorité absente, corrompue ou expirée n’est pas remplacée silencieusement : sa confiance doit être rétablie explicitement.
- La validation HTTPS stricte sur le PC et les tests de migration ne prouvent pas une installation sur un téléphone physique. L’autorité doit être reconnue par le téléphone. Passer outre un avertissement HTTPS ne suffit pas.
- Un changement d’adresse IP change l’adresse de l’application pour le navigateur. Le port reste 8092. Le PC et StructureArc doivent rester ouverts et joignables.
- Selon le navigateur Android, l’ajout à l’écran d’accueil peut être un raccourci plutôt qu’un paquet WebAPK. Sur iPhone, l’ajout passe par le menu Partager. Aucun magasin de confiance du téléphone n’est modifié depuis le PC.
- La conversation vocale utilise les moteurs de reconnaissance et de synthèse disponibles, pas un modèle Moshi intégré. La compatibilité acoustique et les interruptions vocales doivent être validées sur l’appareil réel.
- L’API Anthropic ne fournit pas ici un solde exact en euros. L’admission d’une requête vérifie l’accès observé ; elle ne réserve pas les crédits pour toutes les requêtes suivantes.
- L’installateur ne contient pas les projets personnels ou les sources privées. La modification du logiciel par un agent nécessite l’accès autorisé à un véritable dossier de sources ; l’application distribuée n’accorde pas cet accès aux autres utilisateurs.

## Vérifications de cette livraison

**1043 tests natifs réussis, 0 échec, 18 ignorés sur 1061**, **208.33 s** ; **492 tests UI** sur 58 fichiers, TypeScript/Vite réussis. Autotests brut/installé **18/18**, signatures **Valid**, mise à niveau réelle code **0**, lignes des projets, conversations et messages exactement conservées.

Un petit projet Node.js sans dépendance a été créé par le vrai chat avec Sonnet 5.5 : quatre fichiers, trois étapes terminées, 16 tests écrits par le modèle et sept groupes de tests indépendants réussis ; 24 fichiers préexistants conservés. Les fichiers n’ont pas été écrits ou réparés par le réviseur. Ce résultat borné ne prouve pas la réussite de tout projet.

HTTPS strict (chaîne et adresse vérifiées) et six ressources PWA contrôlés sur l’application installée, autorité locale conservée. Aller-retour vocal français réel via HTTPS avec interruption et arrêt contrôlés, sans microphone ni haut-parleur. Cinq modèles locaux installés chargés séparément : quatre ont réellement lu un fichier et exécuté Node ; aucun des cinq n’a respecté tous les critères de réponse finale. Quatorze contrôles minimaux d’admission cloud acceptés, sans revendiquer quatorze projets complets. Installation physique téléphone, annulation acoustique d’écho et Moshi non validés.
