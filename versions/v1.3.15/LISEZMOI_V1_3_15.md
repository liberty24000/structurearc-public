> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.15

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_15.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.15
- **Fiabilité des appels d'outils** : un tour terminé sans texte produit un résumé clair ; les échecs d'outils ont des codes typés (« outil inconnu » distinct de « arguments invalides ») ; les jetons spéciaux sont neutralisés dans les résultats d'outils ; les boucles alternées (A, B, A, B) sont détectées ; une proposition de fichier issue d'une réponse coupée est refusée.
- **Régulation CPU du moteur local** : le quota du moteur d'IA est abaissé par paliers plutôt que de couper le moteur ; le changement de modèle depuis le chat est raccordé à l'application.
- **Matrice de compatibilité** : nouvelle colonne « Lançable ici ». Le bouton « Télécharger le modèle » prend la même décision GPU que l'affichage ; le modèle se nomme NeoHorse 1-9B.
- **Reste de la 1.3.14** : les copies d'auto-amélioration ne s'accumulent plus.

## En préparation (présent dans le code, **non utilisable** dans cette version)
- **Multi-GPU** : testé sur machines simulées seulement, non branché au démarrage du moteur.
- **Règle de ressources finale dans le produit** (3 Go de RAM disponible + 5 % de CPU disponible) : elle n'existe pour l'instant que dans les outils de test ; la garde du produit garde l'ancienne règle en pourcentage.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.15_x64-setup.exe` | **Installateur Windows signé** (livraison PRIVÉE, version non publiée ; à lancer seulement par son destinataire) |
| `StructureArc_1.3.15_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_15.md` / `LIMITES_V1_3_15.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
