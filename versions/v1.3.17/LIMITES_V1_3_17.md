> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.17

## Ce qui a été exercé

- Installation mobile : manifeste, icônes réelles 192/512 pixels, lancement sans jeton dans l’URL, écran de connexion et écran hors connexion. Six tests des fichiers publics vérifient aussi que le service worker ne conserve ni API, ni chat, ni audio.
- Serveur mobile : authentification, origine, sessions prolongées sur choix explicite, révocation, isolation des flux vocaux et fermeture lors de l’expiration/arrêt. Certificats persistants vérifiés par un vrai client TLS après rechargement ; mauvais nom et certificat expiré refusés ; clés privées dans le coffre Windows.
- Voix réelle en développement : HTTPS, deux cookies indépendants et vrai moteur vocal Windows. Le serveur a renvoyé un WAV de 219 608 octets, reconnu quatre des cinq mots attendus, rejeté les anciens audios après interruption puis fermé le Job. Test réussi en 11,67 s. Seul un son synthétique en mémoire a été utilisé : aucun microphone, haut-parleur ou fichier audio.
- Interface : tests d’installation, réorientation, durée de vie des sessions, réponses audio périmées et lecture de réponses longues. Les journaux complets et les empreintes du paquet distinguent les tests de développement du binaire livré.

## Ce qui n’est pas revendiqué

- Aucun essai physique sur Android/iPhone ni mesure acoustique d’annulation d’écho n’a été réalisé par ces tests. La permission du micro, la confiance du certificat et l’installation doivent être confirmées sur le téléphone du propriétaire. La compatibilité varie selon le navigateur. L’acceptation d’une demande d’installation n’est pas une preuve que le système a installé l’application.
- Le PC doit rester allumé, StructureArc ouvert et un modèle chargé. La version mobile ne fait pas tourner le modèle sur le téléphone. Une autre adresse IP constitue une autre origine pour le navigateur.
- Le moteur vocal est celui de Windows en français, pas un runtime Moshi/Kyutai installé. Les moteurs français correspondants doivent exister sur le PC. Le passage en arrière-plan arrête l’écoute ; une nouvelle activation explicite est nécessaire.
- L’API Anthropic avec clé saisie dans l’application reste absente. Claude Code CLI est une intégration distincte.
- Les essais de création autonome de projet par le modèle local ont encore échoué. Les corrections de coordination et les contrôles réellement exécutés évitent certains faux succès, sans garantir qu’un modèle livrera correctement tout projet. Les vérifications automatiques restent liées aux critères du projet et ne sont pas une preuve universelle de qualité.
- OCR, contrôle du poste, Office et certains tests dépendent des logiciels, moteurs et autorisations présents. Un test ignoré ou un adaptateur simulé n’est jamais compté comme une preuve de fonctionnement physique.

## Connexion et données

Le premier certificat doit être approuvé manuellement sur le téléphone, après comparaison de son empreinte. Les clés privées restent sur le compte Windows et aucun certificat n’est installé automatiquement dans le système. Les liens de connexion sont à usage unique et expirent après deux minutes. Le choix de rester connecté prolonge la session pour trente jours ; « Déconnecter cet appareil » révoque cette confiance et arrête son flux vocal.

Les autorisations du développeur ne sont pas distribuées aux autres utilisateurs. Le dépôt public contient l’installateur signé et les notes, sans sources privées, conversations, clés ou données de test.
