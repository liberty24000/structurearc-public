> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.37 — Reprise locale et suivi de l’installation mobile

L’invitation mobile reste visible après une demande acceptée par Chrome : elle indique l’attente puis l’absence de confirmation éventuelle. Elle disparaît lorsque le navigateur confirme l’installation, ou lorsque vous la masquez. Le téléchargement du certificat et les étapes Android restent disponibles dans les paramètres. Le certificat existant est conservé ; cette version ne prétend pas résoudre à elle seule tous les refus d’installation Android.

Une mission locale peut reprendre une fois après un lot d’outils tronqué ou une limite de sortie atteinte. Le lot incomplet est entièrement rejeté ; les actions précédentes confirmées sont conservées. La reprise conserve les autorisations, l’annulation et les budgets existants. Les diagnostics distinguent les catégories d’erreurs sans journaliser le contenu du modèle.

Le retour au modèle repère mieux les tests qui affichent des erreurs sans faire échouer le programme : console.assert, exceptions absorbées et mots « throw » présents seulement dans un message. Il ne transforme pas artificiellement le code de sortie du processus. La commande npm test n’est plus assimilée à un outil de test particulier. La matrice des modèles précise le dossier de banc utilisé pour son inventaire.

Les essais réels restent distincts des tests du logiciel. Le modèle 9B Coder a repris après une sortie tronquée, mais n’a pas terminé le projet dans les quinze minutes prévues. Le modèle 1,5B a échoué à inspecter le projet avant de commencer. Aucun de ces résultats ne constitue une qualification de projet autonome. Les projets et conversations personnels restent hors de l’installateur.

Validation du logiciel : 1 065 tests natifs réussis, 20 essais explicites ignorés ; 515 tests d’interface réussis. Les tests de logiciel et les essais réels de modèles restent deux preuves distinctes.
