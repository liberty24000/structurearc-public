> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites 1.3.44

Les tests mobiles couvrent quatre dimensions dans un vrai Chrome, avec navigation, discussion générale et visibilité de la saisie. Ils ne remplacent pas tous les téléphones, claviers ou tests acoustiques Android. Les mesures vocales emploient un microphone et une réponse synthétiques avec le moteur local réel.

La reprise de contexte est bornée à deux tentatives et conserve la demande courante; une demande qui dépasse à elle seule la capacité du modèle peut rester impossible. La reprise après une demande verbale de continuer est bornée et ne remplace pas les contrôles d’achèvement. La régulation CPU n’efface pas une vraie surcharge persistante, une pression RAM/GPU ou un arrêt explicite.

Les essais réels Qwen3.5 4B précédents ont échoué; aucun résultat universel d’autonomie n’est revendiqué. Le dernier essai P2 a tourné 408,9 secondes sans annulation CPU et créé trois fichiers, mais README.md manque et le vérificateur indépendant échoue. La séparation des contrôles de sous-étape et de la validation globale reste à corriger. Les phases M1–M4 et la qualification des projets complets restent ouvertes.

Version installée et vérifiée : 1089 tests natifs réussis, 25 ignorés explicitement, 170 tests UI, 169 tests vocaux et 18 autotests du binaire. Navigation et saisie validées sur le backend installé dans Chrome, sur cinq dimensions; voix locale mesurée avec microphone synthétique, interruption et reprise vérifiées. Projets, discussions, certificat et associations préservés. Aucun succès physique Android supplémentaire n’est revendiqué.
