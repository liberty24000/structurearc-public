> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.16

Application Windows x64 pour travailler sur des projets avec une IA locale, des outils autorisés par projet et un plan de travail persistant.

## Nouveautés

- Chat réorientable pendant une réponse : envoyez une nouvelle consigne sans arrêter manuellement la génération. L'interface distingue son enregistrement de sa prise en compte.
- Choix du modèle dans le chat, conservé face au routage automatique.
- Plan de travail utilisable : objectifs, dépendances, états, rapports, interruption et reprise des tâches inachevées. Un bouton crée une équipe Analyse → Réalisation → Vérification.
- Processus en arrière-plan : démarrage, suivi, arrêt ciblé et résultats conservés. Deux processus indépendants peuvent travailler simultanément.
- Lectures de fichiers indépendantes en parallèle lorsque les ressources le permettent ; améliorations de l'indexation et de la mémoire des erreurs.
- Recherche et lecture de sites publics sous autorisation ; prise en charge des scripts PowerShell, pwsh et bash de projet et des opérations Git locales.
- Un seul bouton vocal dans le chat : un clic pour démarrer la discussion, un clic pour l'arrêter. Les réglages techniques et commandes secondaires ne sont plus affichés sous la saisie. La lecture audio suspend le micro.
- Écran de configuration du shell avancé : périmètre, durée et budget d'actions choisis explicitement par le propriétaire.

## Installation

Lancez `StructureArc_1.3.16_x64-setup.exe`. Cette édition en ligne contient l'application et le runtime CPU ; le modèle IA est téléchargé séparément depuis le catalogue, avec contrôle de taille et SHA-256. Une connexion Internet est nécessaire pour ce téléchargement initial. Les modèles déjà présents sont conservés.

Vérifiez la signature Windows et le SHA-256 du téléchargement. Les autorisations sont accordées par projet ; les droits choisis sur la machine de développement ne sont pas distribués aux autres utilisateurs.

Consultez `LIMITES_V1_3_16.md` pour les vérifications effectuées et les fonctionnalités qui restent expérimentales.

Le dossier complet conservé par l'éditeur contient aussi l'EXE de référence, les empreintes et les preuves. Le dépôt public distribue l'installateur signé et les notes de version, sans les sources ni les données de développement.
