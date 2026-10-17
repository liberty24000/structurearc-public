> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.0

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, agents externes).

> Première version fonctionnelle, pas un produit fini. Le fichier `LIMITES_V1_3_0.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.0 — catalogue de modèles et routage mesuré
- **8 modèles de 6 familles** au catalogue (Qwen 2.5, Llama 3.2, Gemma 3, Phi-3.5, SmolLM2, Granite 3.1), chacun avec dépôt, **révision, taille et SHA-256 épinglés** et licence. Rien n'est téléchargé sans votre accord ; chaque fichier est vérifié par empreinte avant usage. Seuls Qwen 0,5B et 1,5B ont été livrés jusqu'ici : les six autres sont installables depuis l'écran IA.
- **Le choix du modèle repose sur des mesures** (banc `scripts/bench-models.mjs` : recherche, résumé, architecture, génération de code exécutée et testée, correction, appels d'outils), et non plus sur la seule taille du fichier. Un modèle qui n'a pas réussi au moins 4 appels d'outils sur 5 n'est jamais choisi pour une tâche qui exige des outils. Un modèle non mesuré (importé) est évalué par une estimation **étiquetée comme telle**.
- **Matrice de compatibilité** (écran IA) : colonnes « outils mesurés » et « qualité mesurée / vitesse ». Instantané : `docs/model-matrix.md`.
- **Modèle recommandé par défaut** : seulement parmi les modèles qui savent appeler des outils et dont la licence est permissive (Apache-2.0 ou MIT). Les autres restent au choix.
- Correction de la documentation de compatibilité GPU (contradiction relevée en revue).

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.0_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_0.md` / `LIMITES_V1_3_0.md` | Ce guide / ce qui est prouvé ou non |
| `INSTALLATEUR_SIGNE.txt` | Signature de l'installateur |
| `docs/` | Architecture, exigences, menaces, compatibilité, matrice des modèles |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
