> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.19

**3 novembre 2026 — analyse mieux encadrée et continuité des longues conversations.**

Application Windows x64 pour travailler sur des projets avec une IA locale. Cette version corrige trois défauts du moteur et de l’historique ; elle ne valide pas la réalisation autonome d’un projet complet.

## Ce qui change depuis 1.3.18

- **Analyse en lecture seule** : la règle de la phase prime l’objectif de réalisation recopié dans son contexte. Après des lectures répétées, le rappel au modèle reste compatible avec cette règle. Une inspection réellement obtenue est nécessaire ; une simple déclaration ne suffit pas. Une réorientation pendant le travail nécessite de nouvelles observations adaptées à la demande.
- **Mémoire des échanges** : les compactages successifs reprennent le résumé précédent, avec une limite de **6 000 caractères Unicode**. Ce résumé reste une synthèse ; les messages originaux sont conservés en base.
- **Longues conversations** : la lecture de l’historique retourne les **1 000 derniers messages dans leur ordre chronologique**, plutôt que les premiers. Les messages plus anciens ne sont pas supprimés de la base.

Ces corrections n’accordent aucun droit supplémentaire et ne confirment pas automatiquement une opération refusée.

## Validation et limites

Code gelé `740dea0` : suite native complète **911 réussis, 0 échec, 18 ignorés**, soit **929 tests**, en **205,99 s**. Les scénarios comprennent un fournisseur simulé ; ils ne constituent pas un nouvel essai réussi d’un modèle réel.

Les essais réels **6 à 11 ont échoué**. L’essai **12 est en cours à la rédaction ; aucun résultat terminal réel n’est retenu**. La capacité d’autonomie complète reste non validée. L’interface est inchangée ; les anciens résultats voix et interface ne sont pas présentés comme de nouveaux tests 1.3.19.

La PWA et HTTPS sont disponibles depuis 1.3.17. Le PC doit rester allumé, l’application ouverte et un modèle prêt. Le microphone reste soumis à une activation explicite. Aucun essai physique téléphone ni validation acoustique d’annulation d’écho n’est établi. Moshi/Kyutai et l’API Anthropic directe ne sont pas intégrés.

Lire `LIMITES_V1_3_19.md` pour la portée des preuves.

## Paquet construit et contrôlé

Production TypeScript et Vite réussis. L’installateur `StructureArc_1.3.19_x64-setup.exe` de **24 065 808 octets** est signé Authenticode **Valid** ; SHA-256 `ebe1ff017ce553f6620536b0a5b183d3846f6e3e6b96fea718d403ab877c5efb`.

Le binaire brut et l’exécutable installé ont chacun réussi leur autotest **18/18**, avec code de sortie **0**. L’exécutable installé est signé **Valid** ; SHA-256 `4e3d29be4f59096d8e8323ea7a4c21a47c4caac4f998081eaaf7aae9d5cf4041`.

La mise à niveau réelle silencieuse (`/S`) s’est terminée au code **0**, avec version **1.3.19** enregistrée. Les empreintes contrôlées avant/après sont identiques pour **2 projets, 35 conversations et 345 messages** ; l’intégrité SQLite est correcte. Aucun aller-retour de désinstallation isolée n’a été réalisé. Ces contrôles du paquet ne certifient pas l’autonomie du modèle.

Le périmètre de publication se limite aux documents de livraison et aux installateurs contrôlés, sans sources privées, conversations, clés ou bases utilisateur.
