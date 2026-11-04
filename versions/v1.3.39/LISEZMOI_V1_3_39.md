> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.39 — Conversation naturelle et voix française locale

Le mode vocal propose un écran dédié avec un orbe animé, l'état d'écoute, la transcription et un bouton micro pour couper ou réactiver l’écoute, et un bouton pour revenir au chat. Fermer cet écran arrête le microphone et la lecture vocale sans annuler les actions, agents ou réponses du chat en cours.

L'installateur de base contient Kyutai Pocket TTS avec la voix française Estelle sur processeur. Cette version prend également en charge un pack GPU séparé : Moshi 0.2.13 avec Kyutai `tts-1.6b-en_fr` et la voix féminine `developpeuse-3`. Ce pack de 8,58 Go est installé sur le poste de référence, mais n'est pas embarqué dans l'installateur de base et sa distribution publique reste à préparer. Il ne faut donc pas interpréter le téléchargement du seul installateur comme l'installation de Moshi. La synthèse et la reconnaissance fonctionnent localement, sans service vocal cloud.

Avec le pack Moshi, l'audio est transmis par fragments et les fragments annulés sont invalidés lors d'une interruption. Whisper continue d'écouter indépendamment de la synthèse. Le modèle de chat sélectionné produit les réponses : le moteur français de synthèse n'est pas le modèle de dialogue Moshi anglophone.

Une salutation simple, comme « Salut ! », n’injecte plus automatiquement la définition du projet, son inventaire et les rappels d’échecs dans la réponse. L’historique de la discussion reste disponible. Une formule mixte, comme « Salut, corrige ce fichier », conserve le contexte normal du projet. Les consignes privilégient une conversation chaleureuse et des pauses naturelles, sans imposer des hésitations à chaque phrase.

La diction d’Estelle est ralentie de 15 % sans baisser la hauteur de sa voix, grâce à Sonic (Apache-2.0). L’intonation produite par le moteur est conservée ; aucune hésitation artificielle n’est ajoutée systématiquement. Le réglage a été comparé sur 24 échantillons synthétiques, avec un contrôle séparé de la hauteur, de la durée, des limites et de l’annulation. Le choix de timbre reste une préférence d’écoute.

Cette version inclut aussi la consolidation de mémoire par lots avec reprise persistante, ainsi que la décomposition structurée de la réalisation d’un projet. Un plan mal formé peut être reformulé une fois par le modèle. Les étapes terminées gardent leurs comptes rendus ; les contrôles de réussite restent indépendants de ces comptes rendus.

Le moteur Moshi a passé un essai natif réel de synthèse, reconnaissance française par Whisper, interruption, reprise et arrêt sous la limite mémoire Windows de l'application. Les essais utilisent des phrases synthétiques, sans enregistrer le microphone. La qualité acoustique sur téléphone reste distincte de ces contrôles.

Les projets, discussions, clés API et mémoires personnels ne sont jamais inclus dans l’installateur. Le certificat local et les associations mobiles existants sont conservés lors de la mise à jour.

Le lien HTTPS associe désormais le navigateur comme appareil de confiance par défaut. Sa connexion survit aux redémarrages et mises à jour ; elle est renouvelée à l'ouverture de l'application, avec une limite d'un an sans utilisation. La déconnexion explicite et l'effacement des données du navigateur retirent cet accès. Le choix peut être désactivé dans les paramètres du téléphone.

Le lecteur des fragments audio tente de réveiller un contexte suspendu et affiche une erreur s'il reste bloqué, au lieu de planifier silencieusement du son inaudible. Les étapes de synthèse, décodage, lecture et arrêt de la vue sont journalisées sans enregistrer les paroles ou l'audio. L’utilisateur a confirmé le son sur Android avec la version 1.3.38. La version 1.3.39 réduit les attentes de synthèse et ajoute le bouton micro ; ces nouveaux réglages restent à qualifier sur le téléphone physique.

Attributions : [Kyutai Pocket TTS](https://github.com/kyutai-labs/pocket-tts), code MIT ; poids et embeddings CC BY 4.0 ; enregistrement de référence Estelle/developpeuse-3 sous CC0. Les mentions et licences accompagnent les ressources vocales installées.

Validation : les résultats antérieurs Pocket TTS ne constituent pas une validation du nouveau moteur Moshi. Pour les changements Moshi, interface et appareils de confiance : 172 tests ciblés d'interface/voix/mobile, 29 tests natifs web et trois tests du stockage des appareils ont réussi. Le scénario web de redémarrage conserve un appareil associé sans nouveau lien et vérifie sa révocation. L'essai réel Moshi + Whisper sous Windows a réussi. Un vrai Chrome a rendu trois fragments avec un signal mesuré après reprise d'un contexte audio suspendu ; ce test n'enregistre aucun microphone réel et ne mesure pas un haut-parleur physique. La confiance du certificat et l'installation de la PWA Android ont été confirmées par l'utilisateur, indépendamment de la nouvelle voix. L'écoute et l'interruption acoustique de cette voix sur téléphone restent à qualifier.

## V1.3.39 — 4 novembre 2026 — Microphone, réouverture mobile et latence

- Dans l’écran vocal, un bouton permet de couper et réactiver le microphone tout en continuant à écouter la réponse. Il ne suspend pas les actions du chat. La phrase déjà prononcée peut encore être transcrite ; les nouveaux échantillons sont remplacés par du silence lorsque le microphone est coupé.
- La page de connexion recherche une session existante avant de demander un nouveau lien. Cela couvre notamment une première navigation sans cookie Strict et un ancien lien de lancement expiré. La connexion reste révocable ; aucun jeton n’est placé dans le stockage JavaScript.
- Le pack Moshi féminin transmet des fragments de 400 ms au lieu de 800 ms. Sur trois phrases synthétiques locales, le premier fragment arrive vers 1,61 s, contre 1,96–1,99 s auparavant. Aucun trou entre fragments n’a été calculé dans ces trois essais. Une variante plus agressive a été rejetée car elle créait des coupures.
- Whisper utilise jusqu’à six fils de calcul, dans la moitié des processeurs disponibles, avec un plafond global CPU de 50 %. Son modèle français, sa recherche de transcription et sa tolérance aux pauses restent identiques. Cela ne garantit pas une latence totale donnée : le modèle du chat et la charge du PC interviennent aussi.
- Validation : 181 tests ciblés interface/voix/mobile/chat ; récupération de session après fermeture complète de Chrome, navigation externe et ancien lien, sans récupérer un appareil révoqué. Les tests navigateur utilisent des appareils audio synthétiques. L’utilisateur a confirmé le son sur Android avec la version 1.3.38 ; les nouveaux parcours physiques restent à confirmer après mise à jour.

Contrôles supplémentaires de cette livraison : 29 tests du serveur web et 10 tests du protocole vocal réussis, trois tests de segmentation réussis. Dans Chrome réel, trois fragments audio ont été lus jusqu’au bout pendant la coupure puis la réactivation du microphone ; les trois blocs capturés pendant la coupure étaient silencieux. Le signal audio a été mesuré, pas écouté sur le téléphone.

Livraison contrôlée : installateur et application installée signés, mise à jour réussie avec données et appairages préservés, autotests de l’exécutable installé 18/18. Serveur HTTPS et ressources vocales installées vérifiés. Le parcours Moshi via le serveur de la version installée livre son premier fragment en 1,79 seconde sur la phrase synthétique testée et reprend après interruption sans ancien fragment. Un redémarrage réel conserve la session associée.
