> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.0 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build 70
- **Registre : 27 rapports « courant » = 26 PASS + 1 FAIL conservé.** Le FAIL est le premier passage d'`installer-check` (15/16, hook de langue « contenu=null ») : un `structurearc.exe` du dossier de compilation était resté ouvert (lancé par l'explorateur, hors scénario) ; rejoué seul après sa fermeture : 16/16. Cause exacte du premier échec non démontrée au-delà de cette corrélation.
- Fenêtre réelle : routage 17/17, modèle 12/12, référence 34/34, Office 16/16, terminal 21/21, modifications 19/19, i18n 14/14, web 25/25, agents 24/24, compactage 19/19, modes du chat 19/19, chat auto 17/17, import GGUF 16/16, GPU 14/14, changement de modèle 13/13, HTTPS local 20/20, zone de notification 11/11 (+ 9/9), agents définis 18/18, états de tâche 14/14, contrats 35/35 ; installateur 16/16 ; mise à jour réelle `update-real` 33/33 ; runtime embarqué 8/8 ; inférence installée PASS.
- `test.ps1` PASS global (tests Rust 478 réussis, 0 échec, 4 ignorés ; Vitest 150).
- **Téléchargement réel d'un modèle du catalogue par le code de l'application** : Llama 3.2 1B, 807 694 464 octets, SHA-256 recalculé = celui du manifeste (`6f85a640…df83`), 41 s ; second appel = vérification sans retéléchargement (test ignoré `real_catalogue_download_is_verified_and_idempotent`).
- Banc de 8 modèles (`bench-gpu-20261017225530.json`) : mesures réelles ; catalogue généré par `scripts/make-catalog.mjs` à partir de ce fichier.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Qualité mesurée** | UNE machine (GTX 1070, Vulkan), UN essai à température 0, petits échantillons (3 à 5 questions par classe). Indications comparatives, pas des garanties. Qwen 0,5B et 1,5B ne réussissent qu'1 question d'architecture sur 3 ; Phi-3.5 n'en réussit qu'1 de résumé sur 3 ; Gemma, Granite, Phi-3.5 et SmolLM2 n'ont réussi aucun appel d'outil au banc. |
| **Les 6 nouveaux modèles** | Mesurés au banc et téléchargeables ; seul Llama 3.2 1B a été téléchargé par l'application. Aucun n'a été utilisé dans les scénarios de fenêtre réelle (ils utilisent Qwen). Livrés dans le catalogue, pas dans l'installateur. |
| **Licences** | Llama 3.2 (licence Meta) et Gemma (conditions Google) imposent des conditions d'usage propres : à lire avant usage ; aucune relecture juridique. |
| **Installateur hors-ligne** | Non fait (V1.3.2). |
| **Gros modèles sur petite VRAM** | Non fait (V1.3.1) ; exige un nouvel accord pour télécharger des modèles plus grands. |
| **Autre ordinateur** | UN seul PC testé. GPU AMD/Intel/CUDA non testés. |
| **Certificat** | Affiche encore l'ancienne ville (Sigean) ; type « Open Source Developer » à vérifier avec Certum ; SmartScreen peut avertir. |
| **Mise à jour** | Pas de signature du manifeste ni de retour arrière automatique des binaires (V1.6). |
| **Autres limites** | HTTPS depuis un autre appareil, traductions non relues : voir `LIMITES_V1_2_2.md` dans les versions précédentes. |

## Non implémenté (voir `docs/VERSIONS.md`)
Petite VRAM (V1.3.1), hors-ligne (V1.3.2), capture/OCR, souris/clavier, installation, profil « tout activé » (V1.4), MCP (V1.5), **mission autonome** (V1.5.1), signature du manifeste et retour arrière (V1.6). Linux, Raspberry Pi et processeurs sans AVX2 : hors périmètre de la V2.
