> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc V1.3.3

Application de bureau **locale** (Windows 11 x64) pour travailler sur de gros projets avec de **petits modèles d'IA qui tournent sur votre PC**. Rien n'est envoyé à un service distant, sauf ce que vous autorisez explicitement (téléchargement d'un modèle, lecture web, serveurs MCP que vous déclarez).

> Version fonctionnelle, pas un produit fini. `LIMITES_V1_3_3.md` dit honnêtement ce qui n'est pas prouvé ou pas fait. Lisez-le avant de compter dessus.

## Nouveautés de la V1.3.3
- **Calibration automatique du modèle sur votre machine** : après le téléchargement d'un modèle (ou la vérification d'un modèle importé), l'application mesure, avec le vrai modèle et sous la garde de ressources, le plus grand nombre de couches que votre carte graphique peut porter sans dépasser le budget de charge. Le résultat est enregistré par modèle, runtime et carte, et utilisé ensuite par le planificateur. Écran IA → « Calibration » : relancer, annuler, effacer ; réglage `ai_auto_calibrate` (activé par défaut). Sur le PC de référence, le Qwen3.5 4B passe de 13 à 38 jetons/s (toutes les couches sur la carte) sans interruption par la garde.
- **Planificateur par courbe de charge soutenue** : le déport GPU n'est plus plafonné aux 3/4 des couches par précaution ; il suit la courbe MESURÉE (charge ≥ 90 % soutenue au plus 5 s).
- **Modèle de prédiction du débit** (estimation affichée avec la calibration, jamais une décision de sécurité).
- **Modèle à experts « expérimental »** : Qwen3 30B-A3B en 2 bits (10,4 Go à télécharger, licence Apache-2.0, SHA-256 vérifié). Les experts d'une partie des couches restent en RAM (`--n-cpu-moe`). Jamais recommandé ni choisi automatiquement : verrouillage manuel seulement. Mesuré : ≈ 16 jetons/s, mais lecture du prompt ≈ 30-40 jetons/s (missions longues inutilisables).
- **Garde GPU plus fine** : une charge GPU doit être soutenue 10 s avant d'interrompre une génération (la lecture d'un prompt sature la carte quelques secondes).
- **Scripts Windows** (simulation par défaut, administrateur requis pour appliquer, sauvegarde/restauration) pour réduire la charge de Windows : fichier d'échange, services inutiles, télémétrie. Rien n'est appliqué sans commande explicite.

## Contenu du dossier

| Fichier / dossier | Rôle |
|---|---|
| `StructureArc_1.3.3_x64-setup.exe` | **Installateur Windows signé** (à lancer) |
| `StructureArc_1.3.3_x64-offline-setup.exe` | **Installateur hors-ligne signé** (modèle inclus, environ 1,1 Go) |
| `structurearc.exe` | Exécutable compilé non signé (référence de provenance) |
| `SHA256SUMS.txt` | Empreintes SHA-256 |
| `LISEZMOI_V1_3_3.md` / `LIMITES_V1_3_3.md` | Ce guide / ce qui est prouvé ou non |
| `docs/` | Architecture, exigences, menaces, compatibilité, mesures du PC |
| `preuves/` | Rapports JSON, registre de build, journaux de test |

Éditeur : **le-bon.contact** — https://le-bon.contact · https://kevin-moniaux.com. Licence : `LICENSE-STRUCTUREARC.md` (gratuit, pas d'exploitation commerciale par autrui).
