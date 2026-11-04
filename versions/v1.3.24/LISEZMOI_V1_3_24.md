> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.24

**3 novembre 2026 — compatibilité du raisonnement Claude et des appels d’outils.**

Le modèle sélectionné dans le chat reste celui qui exécute la demande. Le transport interroge ses capacités et choisit le mode de raisonnement compatible : désactivé, entre les outils ou adaptatif. Sonnet 5.5 ne reçoit plus la demande incompatible de désactiver son raisonnement. Aucun remplacement silencieux par un ancien modèle.

Les blocs de raisonnement signés nécessaires à une suite d’appels d’outils restent dans la mémoire native du tour courant. Ils ne sont pas exposés au navigateur, sérialisés dans l’historique ou affichés dans les journaux. Le tour actif reste intact pendant cette suite ; la compression habituelle des tours terminés reste possible. Un changement de clé, d’espace ou de modèle invalide la réutilisation correspondante. Les flux incomplets ou mal formés ne déclenchent pas d’outils.

Les refus de crédit ou d’authentification bloquent les appels concernés. Un refus d’accès limité à un modèle ne rend plus tous les autres modèles inaccessibles. Le contrôle d’admission utilise un message fixe sans contenu de projet, facturable : un jeton de sortie maximum pour les modes désactivé/entre outils ; plafond de 256 pour le mode adaptatif. Il ne fournit pas de montant de crédit et ne réserve pas de budget.

La clé et l’espace configurés restent locaux. L’accès HTTPS sur le réseau local conserve le port 8092 au démarrage de l’application. Les projets, historiques, clés et sources privées ne sont pas distribués.

## Contrôles

Suite native finale : **984 réussis, 0 échec, 18 ignorés sur 1002**, en **197,96 secondes**. Interface : **149 tests réussis dans 12 fichiers** ; contrôle TypeScript réussi. L’échec initial d’un test de flux signé a été corrigé puis la suite complète rejouée ; son journal est conservé.

Un essai Anthropic réel avec Sonnet 5.5 a réussi l’admission puis deux appels successifs à un outil de diagnostic synthétique et une réponse finale. Cet essai n’a pas produit de blocs signés ; leur conservation et leur exclusion des sorties publiques ont été vérifiées avec des flux synthétiques et le moteur natif d’outils en lecture seule. Un essai Opus 5.5 a reçu un refus du fournisseur ; aucun succès de ce parcours n’est revendiqué.

## Paquet installé et contrôlé

Compilation Windows/TypeScript/Vite réussie. Autotests brut et installé : **18/18 chacun**, code **0**. Installateur et exécutable installé : signatures **Valid**. Mise à niveau réelle : code **0**, égalité exacte des lignes des projets, conversations et messages contre la sauvegarde, intégrité SQLite correcte avant le premier lancement normal. Pas de désinstallation isolée.

Dans la version installée, Sonnet 5.5 sélectionné dans le chat a réellement obtenu le statut **CLAUDE API ACTIF** après une vérification acceptée par Anthropic. La demande d’audit précédemment bloquée a été relancée dans sa conversation d’origine ; son résultat complet n’est pas une condition déjà acquise de cette livraison.

HTTPS a redémarré automatiquement sur le port **8092** ; connexion, manifeste et deux icônes répondent **200** avec chaîne et nom/IP vérifiés dans le client de test. La réserve du profil supplémentaire VERIFY_X509_STRICT reste applicable ; aucun changement de confiance système ni essai sur téléphone physique.

Installateur `StructureArc_1.3.24_x64-setup.exe` : **24258000 octets**, SHA-256 `dfdde21ae0fbe288394ffaae8151b4fb25b21370348e833f71d7c0f9354059ee`. Binaire brut : `5f171c9f8702b657ede1e4d2a224e8f53cbf23fb95f70b0f37736bc567c87704`. Exécutable installé : `98592d73b5dd9306ea23f37c9c474edc228497ceaf9f1eb31d794dfe6af8b1b3`.
