> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.19

**3 novembre 2026 — paquet construit, signé et mise à niveau contrôlée.**

## Ce qui a été vérifié

Les références relatives `build/logs/` ci-dessous désignent des preuves privées non publiées, citées comme identifiants de traçabilité et non comme liens disponibles dans le paquet.

Suite native complète du code gelé `740dea0` : **911 réussis, 0 échec, 18 ignorés sur 929 tests**, en **205,99 s**. Les tests ignorés ne comptent pas comme réussis. Le lot ajoute six tests chat et trois tests conversations.

Le premier passage donnait **909 réussis, 2 échecs et 18 ignorés** en **209,79 s**. Deux attentes de fixtures ont été corrigées : prise en compte du compactage autorisé d’un diagnostic et attente d’une analyse explicitement incomplète sans inspection. Aucun relâchement du produit, des permissions ou des budgets n’a été introduit pour ces corrections ; la suite complète a ensuite été relancée avec le bilan vert ci-dessus.

Les scénarios du moteur utilisent notamment un fournisseur SSE simulé et de vrais fichiers et commandes isolés. Ils vérifient des comportements déterminés du moteur, pas la fiabilité générale d’un modèle réel. Référence privée : `build/logs/autonomy-stage-validation-1.3.19.json`.

L’interface est inchangée. Les anciens bilans de 135 tests voix et 33 tests interface appartiennent à la validation précédente et ne sont pas des rejeux 1.3.19. Les étapes TypeScript et Vite de la construction de production ont réussi.

## Portée des trois corrections

- **Analyse** : la politique typée de lecture seule prime l’objectif de réalisation cité. Le rappel après des lectures répétées reste dans ce périmètre. L’inspection doit reposer sur une opération réellement obtenue et reconnue par le moteur ; une définition de projet, une lecture refusée ou de la prose ne la remplace pas. Une réorientation live renouvelle le suivi des observations, sans augmenter les droits. Cela ne garantit ni une inspection exhaustive ni la justesse des conclusions du modèle.
- **Résumé** : le compactage reprend le résumé précédent avec une borne de **6 000 caractères Unicode**. Une synthèse bornée peut perdre des détails ; elle ne constitue pas une mémoire intégrale. Les messages originaux restent conservés en base.
- **Historique** : la lecture retourne les **1 000 derniers messages**, remis dans l’ordre chronologique. Les originaux plus anciens restent en base, mais ne sont pas tous affichés ou injectés simultanément dans le contexte du modèle. Ce changement ne promet pas une navigation illimitée dans l’interface.

Ces corrections n’accordent aucune permission supplémentaire et ne transforment pas un refus en exécution.

## Autonomie réelle non validée

Les essais réels **6 à 11 sont en échec**. L’essai **12 est en cours à la rédaction ; aucun résultat terminal réel n’est retenu**. Ces résultats ne sont pas requalifiés par la réussite des tests automatiques.

Au onzième essai, l’analyse en lecture seule a reçu un guidage contradictoire réclamant des actions de réalisation après une boucle de lectures. Aucun livrable n’a été créé et les **18 éléments préexistants contrôlés sont inchangés** ; les tests du projet et le contrat indépendant terminent au code **1**. Les deux étapes suivantes restent bloquées. Le correctif traite cette contradiction, sans démontrer à lui seul que le modèle réalisera ensuite le projet.

La capacité d’autonomie complète reste non validée. Les limites observées avec Qwopus 9B Coder et NeoHorse ne constituent pas une comparaison générale de tous les modèles. Une analyse déclarée terminée ou une commande au code 0 ne prouve pas à elle seule que toutes les exigences de l’utilisateur sont satisfaites.

## Preuves OCR et web distinctes

- **OCR Windows réel** : le script de production utilisant `Windows.Media.Ocr` a reconnu exactement « STRUCTUREARC OCR PROOF 731928 » sur une image synthétique blanche de **1 400 × 260**, en français, sur une ligne ; processus au code **0**, **1 237 ms**. Preuve : `build/logs/ocr-synthetic-windows-proof-1.3.18.json`. Ce scénario ne capture ni écran ni fenêtre et ne prouve pas une vision multimodale ou le contrôle du poste.
- **Web public réel** : test isolé réussi sur l’ancien binaire de test identifié par l’empreinte commençant par `63ff1e` : récupération de `example.com` avec assertion HTTP 200 et texte attendu, puis recherche publique « Rust programming language » non vide. **1 test réussi**, code **0**, **1,07 s** ; preuve `build/logs/proof/web-public-20261103.json`. Les assertions ont réussi ; les réponses brutes et le nombre exact de résultats ne sont pas imprimés. Le grant permissif est limité à la base temporaire du test. Ce scénario ne valide ni les nouveaux correctifs 1.3.19, ni le parcours UI/chat, ni les sites nécessitant une connexion ou du JavaScript.

Ces preuves ponctuelles sont séparées de la suite native et ne valident pas un installateur 1.3.19.

## Voix, mobile et intégrations

PWA et HTTPS sont livrés depuis **1.3.17**. Aucun nouvel essai physique Android/iPhone, microphone/haut-parleur du téléphone ou mesure acoustique d’annulation d’écho n’est établi ici. Le PC doit rester allumé et l’application ouverte ; les moteurs tournent sur le PC. Le certificat doit être approuvé et le microphone activé explicitement.

Moshi/Kyutai n’est pas intégré. L’API Anthropic directe est absente ; une intégration Claude Code CLI est distincte. Aucun résultat ne certifie une autonomie universelle ou une auto-amélioration fiable sur tout projet.

## Contrôles du paquet et de la mise à niveau

| Artefact 1.3.19 contrôlé | Taille | SHA-256 | Résultat |
| --- | --- | --- | --- |
| `StructureArc_1.3.19_x64-setup.exe` | 24 065 808 octets | `ebe1ff017ce553f6620536b0a5b183d3846f6e3e6b96fea718d403ab877c5efb` | Signature Authenticode **Valid** ; mise à niveau `/S` au code **0**. |
| Binaire brut de production | 14 742 016 octets | `1bc7fe57d9390d55ddfb8fc61f4dcf5bf6a4fdd5ea38fd66e6829a7b4c81cfaf` | Autotest **18/18**, code de sortie **0** vérifié après attente effective du processus. |
| Exécutable installé | 14 752 416 octets | `4e3d29be4f59096d8e8323ea7a4c21a47c4caac4f998081eaaf7aae9d5cf4041` | Signature Authenticode **Valid** ; autotest **18/18**, code **0**. |

Code `740dea0`, version **1.3.19** enregistrée après installation. L’équivalence brut/installé a été contrôlée hors **3 octets de marqueur du bundler** et **10 400 octets de signature**.

La mise à niveau réelle a conservé exactement les empreintes des **2 projets, 35 conversations et 345 messages** contrôlés. **345 est le nombre de messages**, distinct de leur identifiant maximal 352. Le contrôle d’intégrité SQLite est `ok`. Une sauvegarde locale privée a été réalisée avant la mise à niveau. Aucun aller-retour de désinstallation isolée n’a été exécuté : l’installation utilisateur préexistante a été conservée. Cela ne généralise pas le résultat à une installation propre ou à tous les postes.

Le premier wrapper PowerShell de l’autotest brut n’attendait pas la fin du processus et lisait un ancien code de sortie. Son rapport 18/18 est conservé comme exécution sans attente ; un nouveau lancement avec attente explicite par `subprocess.wait` a confirmé **18/18 et code 0**. Aucun défaut du binaire n’a été observé dans ce constat de wrapper.

Preuves privées : `build/logs/autonomy-stage-production-candidate-1.3.19.json` et `build/logs/autonomy-stage-installed-upgrade-1.3.19.json`. Une signature valide et un autotest réussi ne constituent pas une validation d’autonomie.

Le périmètre de publication se limite aux documents de livraison et aux installateurs contrôlés. Il exclut les sources privées, conversations, secrets, bases utilisateur et artefacts d’essai. Les modèles de livraison et la release 1.3.18 restent inchangés.
