> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.40 — Reconnaissance française locale

Cette version sait utiliser le pack optionnel faster-whisper : small sur GPU compatible avec assez de mémoire disponible, base int8 sur CPU sinon. Le moteur reste chargé pendant la session vocale. Le pack GPU est séparé de l’installateur; sans ce pack, le moteur embarqué continue de fonctionner.

La voix féminine Moshi/Kyutai est conservée. Les deux moteurs coordonnent leur utilisation du GPU pour éviter la concurrence observée pendant les essais. L’écoute et les interruptions restent actives. Le tampon audio absorbe mieux les petits retards entre fragments. Fermer la vue vocale laisse les actions du chat continuer.

Sur 12 extraits humains français publics : erreurs de mots 32,09 % avec l’ancien moteur contre 14,17 % avec small GPU; transcription médiane 3,27 s contre 0,565 s. Ces mesures ne sont pas le délai complet d’une conversation sur téléphone et ne garantissent pas toutes les voix, tous les accents ou le bruit.

Les projets personnels, clés API, conversations, certificats privés et appairages ne sont pas distribués dans l’installateur.

Contrôle après installation : 18/18 autotests, reconnaissance GPU et phrase française synthétique via HTTPS, interruption/reprise Moshi, connexion conservée après redémarrage. Le contexte excessif de certaines conversations locales reste un chantier distinct : cette version ne garantit pas une réponse vocale instantanée.
