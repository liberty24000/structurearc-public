> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.35

- Whisper base local améliore le cas français testé, mais peut encore se tromper ou produire une transcription incorrecte. Aucune correction du texte par un modèle de chat ne prétend reconstituer ce que l’utilisateur a réellement dit.
- Reconnaissance par segments, pas de transcription neuronale mot à mot en streaming. La capture et la synthèse restent simultanées ; l’interruption sonore repose sur la détection acoustique du navigateur.
- Environ trois secondes de reconnaissance CPU mesurées sur de courts extraits synthétiques, après la fin de parole. Les performances varient selon le PC et sa charge.
- Audio de 25 secondes maximum par segment, deux segments en attente. Une saturation ou erreur est signalée ; les sons et transcriptions ne sont pas écrits dans les journaux.
- Français uniquement dans ce parcours ; Windows avec une voix de synthèse française installée requis. L’installateur inclut environ 160 Mo de ressources vocales non personnelles.
- Pas de preuve de qualité acoustique générale sur Android. L’utilisateur a confirmé que la conversation fonctionne avec la version précédente, mais a signalé sa mauvaise transcription ; le nouveau moteur reste à éprouver sur sa voix.
- Les projets et conversations personnels ne sont jamais fournis dans l’installateur. L’autonomie générale et la qualification des petits modèles restent en cours.
