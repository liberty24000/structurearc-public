> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites 1.3.43

Comparaison exploratoire sur GTX1070 : trois réponses fixes de trois phrases par version, avec vrai Chrome et moteur local. Silence programmé médian entre phrases 1835 ms contre 869 ms (six transitions par version). Première sortie audio médiane 1819 ms contre 1841 ms : pas de gain démontré sur l’attente initiale. Ordre des variantes non randomisé et voix à échantillonnage variable; aucun gain universel ni mesure acoustique Android n’est revendiqué.

L’interruption synthétique passe par le gestionnaire réel pendant la lecture et annule également la phrase préparée. Elle ne qualifie pas la détection acoustique de toutes les voix ou de l’écho sur téléphone. La préparation concerne la sortie streaming; le chemin vocal ancien à fichier entier reste séquentiel.

La reconnaissance progressive, l’entrée texte continue dans Kyutai, le transport persistant et la coordination adaptative des ressources restent à développer et qualifier. Les petits modèles ne sont pas universellement autonomes; les phases M1–M4 restent ouvertes.
