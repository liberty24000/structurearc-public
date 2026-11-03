> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.20

**3 novembre 2026 — choix du fournisseur dans le chat et accès mobile amélioré. Paquet construit, signé et mise à niveau contrôlée.**

Application Windows x64 pour travailler avec une IA sur ses projets. Cette version ajoute l’API Claude d’Anthropic comme fournisseur facultatif et améliore l’application web installable sur téléphone. Elle ne certifie pas la réalisation autonome d’un projet complet.

## Choisir le fournisseur dans le même chat

Le sélecteur de modèles du chat permet de choisir un modèle local ou Claude via l’API Anthropic. La clé API reste dans le coffre du PC hôte. Le cloud nécessite une configuration valide et un choix explicite pour le projet ; le contexte nécessaire est alors envoyé au fournisseur distant. Ce mode n’est pas local ni hors connexion.

Les appels d’outils utilisent le même moteur d’exécution et les mêmes contrôles d’autorisation. Changer de fournisseur n’accorde aucun droit supplémentaire. Une ancienne conversation contenant des observations de projets liés sans provenance cloud établie peut nécessiter une nouvelle conversation pour le cloud ; le travail local et l’historique restent conservés.

**Aucune clé API réelle ni aucun appel authentifié à Anthropic n’a été utilisé pour valider cette livraison.** Les tests simulés ne prouvent pas le fonctionnement du service réel avec votre compte.

## Application mobile et voix

La PWA peut être installée sur l’écran d’accueil du téléphone et utilise le même chat. Le PC doit rester allumé, StructureArc ouvert, le réseau accessible et le fournisseur choisi prêt. Le téléphone ne reçoit ni le modèle ni les outils du PC.

Un seul bouton active ou désactive la voix. Parler pendant une réponse interrompt sa lecture ; la transcription rejoint la conversation courante. Après une indisponibilité initiale, la disponibilité vocale est vérifiée toutes les **15 secondes lorsque la page est visible**, ainsi qu’au retour du réseau ou de la page au premier plan. Ces contrôles n’activent pas un microphone désactivé et ne rétablissent pas une session déconnectée ou expirée.

Le manifeste d’installation est désormais servi avec le type `application/manifest+json` au lieu de `text/html`. PWA et HTTPS existaient déjà ; la confiance dans le certificat et les permissions du navigateur restent nécessaires. Aucun test physique téléphone ni validation acoustique de l’annulation d’écho n’est revendiqué. Moshi/Kyutai n’est pas intégré.

## Contrôles et installation

- Suite native finale : **946 réussis, 0 échec, 18 ignorés sur 964**, en **217,38 s**.
- Mobile/voix : **141 tests réussis** ; production TypeScript et Vite réussis.
- Scénario HTTPS avec les vrais moteurs français Windows : **1 test réussi**, **11,38 s**, reconnaissance de **4 mots attendus sur 5**, sans microphone, haut-parleur ni téléphone.
- Autotests du binaire brut et de l’exécutable installé : **18/18 chacun**, code **0**. Installateur et exécutable installé signés Authenticode **Valid**.

Installateur `StructureArc_1.3.20_x64-setup.exe` : **24 238 960 octets** ; SHA-256 `f44f6b43912c7fecf966b5e356f2ee7b6ddf6270e5c96d5e09ed630f3c055c30`.

La mise à niveau réelle silencieuse (`/S`) s’est terminée au code **0**. Les empreintes des données contrôlées sont exactement identiques avant/après et l’intégrité de la base est correcte. Aucun aller-retour de désinstallation isolée n’a été réalisé.

Les essais réels **12 et 13 ont échoué** ; aucun nouveau succès d’autonomie complète n’est revendiqué. Lire `LIMITES_V1_3_20.md` pour la portée des tests et les empreintes des exécutables.

Le périmètre de publication se limite aux documents de livraison et aux installateurs contrôlés, sans projets privés, conversations, secrets ni bases utilisateur.
