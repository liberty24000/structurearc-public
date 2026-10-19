> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.5

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_5.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.5
- **Accélération par motifs répétés** (décodage spéculatif par n-grammes, sans second modèle) : pour les modèles denses entièrement sur la carte graphique, le serveur propose la suite d'un passage déjà présent dans le contexte et la vérifie. Mesuré sur le PC de référence : jusqu'à ×2,4 (Qwen3.5 4B) à ×4,3 (Qwen2.5 0,5B) quand la réponse recopie ou modifie un texte fourni (citation, réécriture de code), **aucun effet** en génération libre. Activée par défaut ; case à cocher dans Paramètres (effet au prochain démarrage du modèle). Les sorties peuvent différer très légèrement (arrondis numériques).
- **Plafond mémoire corrigé pour les agents simultanés** : chaque emplacement supplémentaire réserve de la mémoire engagée (mesuré : 4,2 → 8,4 Go pour 4 agents sur le Qwen3.5 4B) ; le plafond de sécurité en tient compte.
- **Qualité mesurée avec plusieurs agents** : à 4 agents simultanés, mêmes scores de qualité qu'avec un seul sur les trois modèles testés.
- **Reste de la V1.3.4** : agents locaux simultanés (réglage « Agents simultanés », 1 par défaut ; modèle verrouillé, tâches 100 % locales), calibration automatique du déport GPU, modèle à experts 30B-A3B « expérimental ».

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.5_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.5_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_5.md` / `LIMITES_V1_3_5.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
