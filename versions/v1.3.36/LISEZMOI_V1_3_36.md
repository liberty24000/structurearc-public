> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.36 — Installation mobile et mémoire des modèles locaux

Le parcours mobile attend désormais l’activation effective du composant hors ligne. Un enregistrement initial réussi ne masque plus un échec ultérieur de préparation. Des diagnostics bornés distinguent permission, réseau, activation, délai et navigateur incompatible. Aucun message privé, son, URL ou jeton n’est ajouté à ces journaux.

Après une demande d’installation acceptée, l’interface attend la confirmation de Chrome. Sans confirmation après une minute, elle indique que l’installation n’est pas confirmée. Elle ne prétend ni installer un APK elle-même ni connaître toutes les erreurs internes d’Android. Le téléchargement du certificat d’autorité et les instructions restent disponibles dans les paramètres mobiles. Le certificat existant est conservé.

Le moteur local conserve ses diagnostics après un plantage. Le plafond de mémoire engagée tient compte de l’augmentation du contexte par rapport au benchmark du modèle. Avant le lancement, le plan réduit le nombre d’agents ou le contexte si nécessaire pour conserver une réserve mémoire. Si aucune configuration ne tient, le refus est explicite. Il ne supprime pas le plafond et ne transforme pas une estimation en garantie de réussite du modèle.

Whisper français local, la synthèse et le bouton vocal unique de la version précédente sont conservés. Les projets et conversations personnels ne sont pas inclus dans l’installateur.

Validation du candidat : 1 059 tests natifs réussis, 20 essais explicites ignorés ; 514 tests d’interface réussis. Sur un essai réel Qwen 4B, le moteur termine sans planter avec un pic de mémoire engagée de 4 870 Mio, au-delà de l’ancien plafond de 4 787 Mio. Le projet généré échoue néanmoins au vérificateur indépendant : quatre fichiers existent, mais une erreur de validation des données n’est pas corrigée par l’agent. Cet essai est donc un échec de qualification du projet, pas un succès annoncé.
