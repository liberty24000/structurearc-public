> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.7

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_6.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.7
- **Routage automatique du modèle dans le chat** : selon la nature de votre demande (rédaction, raisonnement, code, recherche web, contexte long, agent), le chat peut passer au modèle désigné par la table du propriétaire (V1.3.6). Une ligne sous la conversation indique le modèle choisi et la raison ; un anti-aller-retour limite les bascules ; le verrouillage manuel du modèle reste prioritaire ; le réglage « routage automatique » permet de le couper. Jamais de modèle absent ou trop gros pour la mémoire.
- **Garde-fou contre les boucles d'outils** : un appel d'outil identique répété est interrompu.
- **Subconscient (nouveau, section dédiée)** : une couche légère, **sans modèle**, qui observe le résultat des actions (terminal, modifications, agents, outils), mémorise les expériences dédupliquées dans une base locale dédiée et en tire des **rappels prudents** avant une action (jamais des ordres, jamais une permission). Un réflexe n'est proposé qu'après plusieurs observations vérifiées, une comparaison avec/sans, un contrôle des facteurs de confusion et une validation prospective ; il est retiré automatiquement s'il se dégrade. Secrets masqués avant stockage. Interrupteur, consultation, validation/invalidation, oubli, export/import, effacement par projet ou total et réglages (conservation, taille, budget) dans la section « Subconscient ». Refus de toute modification pendant l'arrêt d'urgence.
- **Correctif important trouvé pendant la livraison** : une première version du subconscient pouvait **figer l'application** à l'application d'une modification (verrou pris deux fois) ; corrigé et couvert par un test de non-régression avant cette livraison.
- **Reste de la V1.3.6** : table de routage par tâche, NeoHorse 1 9B recommandé, cache de préfixe, démarrage allégé.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.7_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.7_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_6.md` / `LIMITES_V1_3_6.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
