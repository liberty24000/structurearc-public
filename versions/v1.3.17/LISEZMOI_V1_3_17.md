> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.17

Application Windows x64 pour travailler sur des projets avec une IA locale. Cette version ajoute l’application web installable sur téléphone et un transport vocal bidirectionnel relié au chat courant.

## Installation sur le PC

Lancer `StructureArc_1.3.17_x64-setup.exe`. L’installateur en ligne contient l’application et le runtime CPU. Le modèle se télécharge séparément depuis le catalogue avec contrôle de taille et SHA-256. Les modèles et projets déjà présents sont conservés.

## Installer sur le téléphone

1. Laisser StructureArc ouvert sur le PC et connecter le téléphone au même réseau.
2. Sur le PC : Paramètres → Accès depuis le téléphone. Activer l’accès, puis ouvrir « Préparer l’installation sur le téléphone ».
3. Enregistrer le certificat public, le transférer sur le téléphone et vérifier l’empreinte avant de l’ajouter à ses certificats de confiance. Aucun magasin de confiance n’est modifié automatiquement.
4. Ouvrir le lien HTTPS fourni par StructureArc. S’il a expiré, « Obtenir un nouveau lien de connexion » en crée un sans arrêter les autres appareils.
5. Android : Installer l’application dans le navigateur ou les paramètres web de StructureArc. iPhone : Partager → Sur l’écran d’accueil.

Le certificat local reste stable après redémarrage. Une connexion prolongée de trente jours est proposée dans les paramètres web, sur choix explicite. La déconnexion la révoque. Le cache hors connexion contient seulement un écran de reconnexion et des éléments publics, jamais les conversations ni l’audio.

## Utiliser la voix

Choisir le projet et le modèle dans le chat, puis appuyer sur l’unique bouton vocal et autoriser le micro du téléphone. L’écoute continue pendant la lecture ; une prise de parole interrompt la réponse et sa transcription rejoint le même fil. Le microphone et le son utilisent le téléphone, tandis que les moteurs français de Windows et le modèle tournent sur le PC.

L’application doit rester ouverte sur le PC. Le passage en arrière-plan ou une déconnexion ferme la capture. Les possibilités d’installation et d’annulation d’écho dépendent aussi du téléphone et du navigateur ; voir les limites.

## Autres corrections

Les demandes explicites de réalisation peuvent démarrer un cycle de tâches isolé avec une analyse, une réalisation et une vérification réelle. Les messages reçus pendant une réorientation sont mis en file. Les résultats d’équipe reviennent dans le chat d’origine. Un ancien contrôle vert ne valide pas automatiquement un nouvel objectif. Les diagnostics de commandes longues conservent l’erreur utile.

Consulter `LIMITES_V1_3_17.md` pour les preuves et les fonctionnalités encore incomplètes. L’API Anthropic directe et la réalisation fiable de tout projet sans intervention ne sont pas déclarées livrées.
