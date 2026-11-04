> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la version 1.3.40

La reconnaissance fonctionne en français par segments, après une courte pause; il ne s’agit pas d’une transcription continue Kyutai STT. Les modèles peuvent encore se tromper, particulièrement avec du bruit, des noms propres ou des phrases coupées.

Le gain mesuré concerne la transcription. La pause de fin de parole, le réseau, le modèle du chat et la synthèse vocale ajoutent leur délai. Le chargement initial des moteurs et la vérification du pack demandent du temps avant « Je t’écoute ».

Le nouveau pack de reconnaissance et Moshi sont séparés de l’installateur de base. Small GPU nécessite un GPU NVIDIA compatible; le choix CPU reste possible automatiquement. Les gros modèles de chat peuvent réduire la mémoire disponible.

Les essais locaux utilisent un corpus public ou de l’audio synthétique. La qualité acoustique sur le téléphone et la latence bout en bout doivent être confirmées par un essai utilisateur. Les phases de qualification de l’autonomie M1–M4 restent ouvertes.
