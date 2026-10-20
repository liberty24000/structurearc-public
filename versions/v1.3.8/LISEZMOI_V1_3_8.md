> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.8

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_6.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.8
Version de **correction et de mesure** du Subconscient, issue du premier test sous charge réelle (480 vraies commandes du terminal de l'application).
- **Surcoût de latence supprimé** : la V1.3.7 ajoutait ≈ 9 ms à chaque commande du terminal (ouverture d'une connexion de base à chaque vérification de l'arrêt d'urgence). La vérification est maintenant gardée 500 ms : surcoût mesuré ≈ 1 ms (dans le bruit). Les refus de l'arrêt d'urgence restent immédiats pour toutes les actions.
- **Le subconscient distingue les scripts** : `node build.cjs` et `node test.cjs` n'étaient qu'une seule action « node » ; le nom du script (caractères sûrs, jamais un chemin) fait désormais partie de l'action. Les deux dernières actions différentes servent de contexte (« après X, Y échoue »).
- **Mesures reproductibles** : deux scénarios en fenêtre réelle, `ui-sse-soak` (repos : 32,7 Mo, ≈ 0,1 % d'un cœur) et `ui-sse-load` (charge), et leurs rapports.
- **Reste de la V1.3.7** : routage automatique du modèle dans le chat, garde-fou d'appels d'outils identiques, section Subconscient.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.8_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.8_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_6.md` / `LIMITES_V1_3_6.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
