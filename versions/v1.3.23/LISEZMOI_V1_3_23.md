> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.23

**3 novembre 2026 — chat central et vérification de l’accès Claude.**

Le chat est l’entrée du travail : les onglets de gestion manuelle des tâches et agents disparaissent. Une demande de projet utilise l’orchestrateur existant ; « reprends » reprend les tâches interrompues ou en attente sans recréer le plan ni relancer automatiquement tous les anciens échecs. L’activité reste consultable et les réglages du projet restent accessibles.

Les clés Anthropic non liées à un espace exigent un identifiant d’espace dans chaque requête. Le transport traite ce refus précis : résolution bornée du seul espace par défaut lorsque les droits le permettent, en-tête requis et reprise unique. Il ne choisit jamais un espace au hasard et ne modifie pas les droits du compte. Si cette lecture est refusée, un champ permet de conserver localement l’identifiant wrkspc_… visible dans la console Anthropic. Le changer révoque les anciennes générations et impose un nouveau contrôle d’accès.

Le choix du modèle reste dans le chat. Pour Claude, la présence d’une clé ne suffit plus : une requête minimale fixe, sans contenu du projet, vérifie que le modèle accepte les requêtes. Cette requête est facturable, avec un jeton de sortie au maximum. Une réponse positive est réutilisée pendant 60 secondes ; le moteur recontrôle ensuite l’accès avant un nouvel envoi ou une action. Une erreur de crédit ou d’authentification bloque les modèles utilisant cette clé, y compris en changeant de modèle. Après recharge, « Vérifier l’accès Claude » permet de refaire le contrôle. Une panne réseau ne devient jamais un faux solde nul.

Anthropic ne communique pas de solde exact avec ce contrôle. Consultez [la facturation Anthropic](https://platform.claude.com/settings/billing) pour ce montant. Les [API de suivi des coûts](https://platform.claude.com/docs/en/manage-claude/usage-cost-api) documentées utilisent une clé administrateur et ne remplacent pas un contrôle de crédit disponible. Un contrôle accepté ne réserve pas de crédit pour un long projet ; une autre utilisation du compte peut épuiser le crédit ensuite, auquel cas le moteur arrête les appels concernés.

La clé reste dans le coffre Windows ; elle n’est jamais renvoyée au navigateur. La découverte des modèles utilise une commande distincte qui renvoie seulement les métadonnées autorisées. Les échecs de catalogue sont distingués des échecs de configuration de clé ; un bouton de nouvelle tentative permet de récupérer un échec transitoire du contrôle de présence.

L’accès HTTPS local au port 8092 reste automatique lorsque StructureArc est ouvert. Vos projets, clés, historiques et bases personnelles ne font pas partie de l’installateur ou du dépôt public.

## Validation

Résultats de cette version : voir les preuves du paquet et les limites ci-jointes. La validation synthétique du refus de crédits ne prouve pas le solde de votre compte réel.

## Contrôles de cette version

Suite native finale : **977 réussis, 0 échec, 18 ignorés sur 995**, en **198,36 secondes**. Interface : **147 tests réussis dans 12 fichiers** ; TypeScript vérifié. Ces nombres ne prouvent pas toutes les fonctions matérielles ou l’autonomie complète.

## Paquet installé et contrôlé

Production TypeScript/Vite et compilation Windows réussies. Autotests brut et installé : **18/18 chacun**, code **0**. Installateur et exécutable installé : signatures Authenticode **Valid**. Mise à niveau réelle au code **0**, avec égalité exacte des données contrôlées avant/après et intégrité SQLite correcte avant le premier lancement normal. Aucun aller-retour de désinstallation isolée.

Le catalogue a réellement affiché **14 modèles** dans l’application installée. Un contrôle natif minimal sans contenu de projet a été accepté par Anthropic avec l’espace configuré. Cela ne prouve ni un montant de solde ni une réserve pour un projet complet.

HTTPS a redémarré automatiquement au port **8092** ; page de connexion, manifeste et deux icônes répondent **200** avec vérification de chaîne et de nom/IP dans le client de test. La réserve VERIFY_X509_STRICT déjà décrite reste applicable ; aucun magasin de confiance système ni pare-feu modifié. Aucun téléphone physique testé.

Installateur `StructureArc_1.3.23_x64-setup.exe` : **24249984 octets**, SHA-256 `94fe55744bb3712e2264fb70d1c5a329db8e29d8a7913687f666bc410be36eac`. Binaire brut : `e9b1281c783776415fcfe34ca29ac6426a1e68ff08d7ee2ba86cf81327a81171`. Exécutable installé : `43464f58943dd3bb2befb399d81b593219cf8192b82a63f54584e682371d90d3`.

Le contenu NSIS examiné comprend l’application, le runtime local vérifié et les composants d’installation ; aucun projet, historique, code source privé, secret ou base personnelle.
