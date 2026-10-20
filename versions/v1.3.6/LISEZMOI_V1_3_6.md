> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.6

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_6.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.6
- **Choix du modèle par type de tâche (table du propriétaire)** : rédaction → Gemma 4 12B (Q3) ; raisonnement → QwenPaw Flash 9B ; code, recherche web, contexte long, agent simple → **NeoHorse 1 9B** ; agent difficile → Qwopus3.5 9B Coder. NeoHorse 1 9B devient le modèle **recommandé** sur un PC qui le supporte (sinon le Qwen3.5 4B). Ces modèles ne sont jamais téléchargés sans votre accord ; le routage ne choisit que des modèles déjà installés, compatibles avec la mémoire de la machine, et le verrou manuel passe toujours en premier. **Pour l'instant le routage sert aux agents ; le chat lui-même ne change pas encore de modèle tout seul.**
- **Réponses plus rapides sur les longues conversations** : les extraits du projet ne sont plus mêlés au message système, qui reste identique d'une question à l'autre ; le serveur réutilise donc son cache (mesure synthétique : préremplissage 8,3 s → 2,3 s avec 15 outils déclarés).
- **Démarrage plus léger** : l'application ne relit plus les modèles du catalogue (≈ 19 Go lus au démarrage, mesuré) à chaque affichage ; la vérification complète de l'empreinte reste faite avant tout usage d'un modèle.
- **Correctif** : un démarrage de modèle demandé par l'utilisateur annule désormais une calibration automatique en arrière-plan au lieu d'être refusé.
- **Qwen3.5 9B** ajouté « en évaluation » (installable, jamais recommandé automatiquement). Un classement mesuré de douze modèles (rédaction, raisonnement, code, web simulé, contexte long, agents, vitesse) est fourni dans `docs/CLASSEMENT_LLM.md`.
- **Reste de la V1.3.5** : accélération par motifs répétés, agents locaux simultanés, calibration automatique du déport GPU.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.6_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.6_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_6.md` / `LIMITES_V1_3_6.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
