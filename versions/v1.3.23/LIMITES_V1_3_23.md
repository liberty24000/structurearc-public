> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.23

Le contrôle Claude prouve uniquement qu’une petite requête est acceptée à un instant donné. Il n’affiche pas un montant de crédit, ne réserve pas de budget et ne peut garantir qu’un long travail dispose de fonds suffisants jusqu’à sa fin. Les refus ultérieurs de crédit interrompent le parcours concerné. Après une panne réseau, l’accès reste non vérifié ; la clé n’est pas déclarée vide ou invalide par supposition.

Les tests natifs utilisent des serveurs locaux avec des clés fictives pour les cas crédit, authentification, délais, cache, concurrence, remplacement de clé, changements de modèle et erreurs pendant le flux de réponse. Les tests de l’interface utilisent un moteur fictif. Aucun de ces tests ne mesure le crédit du compte réel.

Le jalon de création autonome d’un projet complet reste non atteint : les essais réels 12 à 15 ont échoué. Le dernier essai a terminé l’analyse puis échoué à produire des fichiers et tests corrects ; sa vérification indépendante a été bloquée. La correction d’interface et de crédit ne transforme pas ces échecs en réussites. Moshi/Kyutai n’est pas intégré ; aucun essai physique sur téléphone ou de conversation vocale acoustique bidirectionnelle n’est revendiqué ici.

L’accès réseau nécessite que le PC et l’application restent ouverts, le certificat approuvé et l’appareil appairé. Aucun service Windows, changement de pare-feu ou modification de confiance système n’est ajouté. La réserve connue du certificat existant face à VERIFY_X509_STRICT de Python 3.13 reste applicable (Authority Key Identifier absent) ; les essais HTTPS précédents ne prouvent pas la compatibilité de tous les navigateurs.

Les projets, données personnelles et secrets restent exclus des ressources installées et de la publication publique. Une mise à niveau sur le compte existant ne remplace pas un essai isolé de désinstallation et réinstallation.


## Clés liées aux espaces

La lecture administrative des espaces peut être refusée avec une clé valide pour l’inférence. Aucun droit de compte n’est modifié ; un espace doit alors être configuré. La découverte est bornée en taille, pages et durée. Une réponse ambiguë est refusée. Un contrôle valide sans texte est accepté ; les flux tronqués, mal formés ou contenant un outil inattendu restent refusés.

## Contrôles de cette version

Suite native finale : **977 réussis, 0 échec, 18 ignorés sur 995**, en **198,36 secondes**. Interface : **147 tests réussis dans 12 fichiers** ; TypeScript vérifié. Ces nombres ne prouvent pas toutes les fonctions matérielles ou l’autonomie complète.

## Paquet installé et contrôlé

Production TypeScript/Vite et compilation Windows réussies. Autotests brut et installé : **18/18 chacun**, code **0**. Installateur et exécutable installé : signatures Authenticode **Valid**. Mise à niveau réelle au code **0**, avec égalité exacte des données contrôlées avant/après et intégrité SQLite correcte avant le premier lancement normal. Aucun aller-retour de désinstallation isolée.

Le catalogue a réellement affiché **14 modèles** dans l’application installée. Un contrôle natif minimal sans contenu de projet a été accepté par Anthropic avec l’espace configuré. Cela ne prouve ni un montant de solde ni une réserve pour un projet complet.

HTTPS a redémarré automatiquement au port **8092** ; page de connexion, manifeste et deux icônes répondent **200** avec vérification de chaîne et de nom/IP dans le client de test. La réserve VERIFY_X509_STRICT déjà décrite reste applicable ; aucun magasin de confiance système ni pare-feu modifié. Aucun téléphone physique testé.

Installateur `StructureArc_1.3.23_x64-setup.exe` : **24249984 octets**, SHA-256 `94fe55744bb3712e2264fb70d1c5a329db8e29d8a7913687f666bc410be36eac`. Binaire brut : `e9b1281c783776415fcfe34ca29ac6426a1e68ff08d7ee2ba86cf81327a81171`. Exécutable installé : `43464f58943dd3bb2befb399d81b593219cf8192b82a63f54584e682371d90d3`.

Le contenu NSIS examiné comprend l’application, le runtime local vérifié et les composants d’installation ; aucun projet, historique, code source privé, secret ou base personnelle.

## Accès au code pour l’auto-amélioration

Une clé API fournit un modèle, pas un accès au PC ou à un dépôt privé. Modifier StructureArc suppose que son dossier source soit présent et autorisé comme projet. Le paquet public ne fournit pas ce dossier source ni un accès au dépôt du propriétaire. La préparation d’une copie isolée ne constitue pas encore un parcours automatique complet de livraison depuis le chat.
