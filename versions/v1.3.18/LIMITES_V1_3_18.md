> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.18

**3 novembre 2026 — production et mise à niveau contrôlées ; essais réels 6 à 10 en échec.**

## Validations de développement et du paquet construit

| Vérification | Résultat | Portée |
| --- | --- | --- |
| Suite native complète | **902 réussis, 0 échec, 18 ignorés ; 920 au total**, en **207,89 s** | Code moteur `306fd06` ; les tests ignorés ne comptent pas comme réussis. |
| Interface ciblée et TypeScript | **33 tests réussis**, contrôle TypeScript réussi | UI `79a0bb5`, notamment affichage de l’état d’installation et simplification de l’accueil. |
| Suite ciblée voix | **135 tests réussis** | Coordination logicielle, dont la course ancienne interruption / nouvelle lecture ; pas une mesure acoustique sur téléphone. |
| Ancien autotest du binaire debug | **18/18, ancien code `f37476b` uniquement** | Ne valide pas le candidat `306fd06` avec l’UI `79a0bb5`, ni l’installateur final ou sa signature. |
| Nouveau binaire brut de production `306fd06` | **Autotest 18/18 réussi** | Contrôle du binaire construit ; distinct de la réussite d’un projet par un modèle. |
| Exécutable installé `306fd06` | **Autotest 18/18 réussi**, signature Authenticode **Valid** | Exécuté après la mise à niveau réelle de l’installation préexistante. |
| Installateur et mise à niveau silencieuse | Signature Authenticode **Valid**, exécution `/S` au code **0** | 2 projets, 30 conversations et 319 messages contrôlés : empreintes avant/après exactement identiques. |

Le premier passage natif de ce lot donnait **901 réussis, 1 échec et 18 ignorés** : une assertion de test exigeait le texte de lecture complet malgré un compactage borné autorisé. Seule cette assertion a été corrigée, sans modification du code produit pour cette correction. La suite complète a ensuite été relancée avec le résultat **902/0/18** ci-dessus. Les suites ciblées interface et voix ne sont pas additionnées en un total global.

Les scénarios du moteur utilisent notamment un fournisseur SSE simulé, de vrais fichiers temporaires et de vraies commandes dans des environnements isolés. Ils vérifient le comportement du moteur face à des réponses déterminées. Ils ne mesurent pas la fiabilité générale d’un modèle réel.

## Essais réels d’autonomie

| Essai | État à la rédaction |
| --- | --- |
| 6 | Échec |
| 7 | Échec |
| 8 | Échec |
| 9 | Échec terminal : Analyse marquée terminée mais inspection non obtenue, Réalisation en échec, Vérification bloquée |
| 10 | **Échec terminal** : Analyse marquée terminée, Réalisation en échec, Vérification bloquée ; seul le fichier de tests existe, 17 fichiers préexistants contrôlés inchangés |

Ces échecs ne sont pas requalifiés en succès par les corrections ultérieures ni par les tests automatiques. Les essais 9 et 10 n’ont pas livré de projet complet validé. **Le jalon n’est pas atteint et la capacité d’autonomie complète n’est pas validée.** Qwopus 9B Coder reste limité dans les conditions essayées ; ces observations ne constituent pas une mesure de tous les modèles.

### Constats du neuvième essai

- Analyse marquée terminée : seule la définition a été enregistrée via `project_define`, sans écriture de livrable ; l’inspection des fichiers demandée n’a pas été obtenue. Le rapport reconnaît ne pas disposer de données fiables sur l’état actuel du projet et devoir encore l’inspecter. La restriction typée de lecture seule a été respectée, mais tous les critères d’analyse ne sont pas satisfaits. La Réalisation est en échec et la Vérification bloquée par cette dépendance.
- `package.json` et le fichier de tests ont été créés. Le module demandé et le README sont absents.
- Les tests du projet et le contrat indépendant terminent tous deux avec le code de sortie **1**, pour module absent. La relecture des tests générés révèle également des fixtures erronées concernant l’immutabilité ; leur simple présence ne valide donc pas le contrat demandé.
- Les **15 fichiers préexistants contrôlés sont inchangés**. Cette intégrité du périmètre ne transforme pas la réalisation incomplète en succès.
- Les retours observés comprennent des arguments JSON invalides, puis une réponse HTTP tronquée pendant le routage. La cause racine de l’arrêt et l’origine de la troncature ne sont pas établies.

### Constats du dixième essai

- Analyse marquée terminée, Réalisation en échec, Vérification bloquée. Le statut de l’analyse ne prouve pas à lui seul que tous ses critères sont satisfaits.
- Seul le fichier de tests de **3 606 octets** a été créé. Les trois autres livrables attendus, `package.json`, le module et le README, sont absents.
- Les tests du projet et le contrat indépendant terminent tous deux au code **1** pour module absent. Le contenu des tests générés réintroduit une attente de même référence de tableau, contraire au nouveau tableau exigé par le contrat ; la qualité des tests n’est donc pas validée.
- Les **17 fichiers préexistants contrôlés sont inchangés**.
- **Reprise de protocole prouvée en réel** : deux appels aux arguments JSON invalides ont été refusés, puis un nouvel appel au fournisseur a permis une réécriture de tests effectivement appliquée dans la même conversation et le même processus. Le troisième appel invalide a épuisé les deux reprises autorisées.
- Aucune panne HTTP terminale n’a été observée dans cet essai. Le diagnostic de l’échec courant a été affiché correctement. Ce succès de traitement du protocole ne valide pas la réalisation du projet.

Le correctif de protocole est également testé automatiquement dans le code `306fd06`. Les arguments JSON invalides ou non objets sont exclus de l’historique natif ; les lots mixtes ne conservent que les appels valides appariés à leurs résultats. Les diagnostics courants d’échec, de blocage ou d’interruption sont persistés et ne sont pas remplacés par un ancien rapport de réussite. Les statuts HTTP disponibles sont conservés ; les diagnostics sont bornés et les secrets connus masqués.

Ces tests et la reprise réelle du dixième essai n’établissent pas la cause racine de l’arrêt de l’essai 9. Les deux essais restent en échec. Le précédent bilan natif **889/0/18** et l’autotest debug **18/18** concernent l’ancien code `f37476b` ; les contrôles du nouveau binaire de production sont consignés séparément. Les preuves détaillées des essais et de la validation automatique sont conservées dans le dossier privé, hors publication des installateurs.

La détection des lectures répétées, les diagnostics de plusieurs contrôles, la distinction Analyse/Réalisation et les reprises bornées corrigent des défauts précis. Ils ne garantissent pas qu’un modèle choisira les bonnes opérations, préservera toutes les exigences ou réparera correctement ses erreurs. Une commande réellement exécutée avec succès prouve son résultat, pas à elle seule la conformité à toutes les attentes de l’utilisateur.

## Contexte, mémoire et permissions

Le contexte récupéré par défaut exclut les chemins d’état généré identifiés de StructureArc, notamment les conversations sauvegardées et le résumé généré. Cela évite de les présenter comme des extraits du code du projet. L’index général et les lectures explicites restent disponibles sous les mêmes autorisations. Les notes, mémoires et contrats utilisateur ne sont pas supprimés ; l’historique courant, son résumé compacté et les rappels du subconscient restent des mécanismes distincts.

Cette exclusion utilise les chemins réservés à l’état généré : une modification manuelle dans ces emplacements ne les transforme pas en sources sélectionnées par défaut. Une lecture explicite reste possible. Le filtre ne certifie pas la justesse des autres documents ni des souvenirs conservés.

La phase Analyse est en lecture seule pour les fichiers ; la mise à jour encadrée des métadonnées du projet reste distincte d’une écriture de code. Les contrôles d’action et d’arguments obligatoires n’accordent aucune autorisation supplémentaire et ne confirment pas automatiquement une opération refusée. Deux reprises correctives au plus sont prévues pour ce contrôle ; la mission peut rester incomplète.

## Voix, mobile et fonctions non revendiquées

- PWA, HTTPS local et connexion prolongée sur choix explicite sont des fonctions de **1.3.17**, conservées dans cette mise à jour. Elles ne sont pas présentées comme de nouvelles fonctions 1.3.18.
- Aucun essai physique Android/iPhone, microphone/haut-parleur du téléphone ou mesure acoustique d’annulation d’écho n’est revendiqué par les validations de cette version. La compatibilité dépend du téléphone, du navigateur, de ses permissions et de la confiance accordée au certificat.
- Le PC doit rester allumé et l’application ouverte. Le modèle et les moteurs vocaux français tournent sur le PC ; le modèle ne tourne pas sur le téléphone. Une autre adresse IP constitue une autre origine pour le navigateur.
- Moshi/Kyutai n’est pas intégré. L’API Anthropic directe avec clé saisie dans l’application reste absente ; une intégration Claude Code CLI est distincte.
- OCR, Office, contrôle du poste et autres adaptateurs dépendent des logiciels, moteurs et autorisations disponibles. Un test simulé ou ignoré ne prouve pas leur fonctionnement physique.
- Ni autonomie universelle, ni auto-amélioration fiable sur tout projet, ni conformité générale à partir d’un seul contrôle vert ne sont revendiquées.

## Livraison et publication

| Artefact contrôlé | SHA-256 | Contrôle |
| --- | --- | --- |
| `StructureArc_1.3.18_x64-setup.exe` — 24 064 248 octets | `1d4f876199befa4a893abbaf06ac6bd87835fa99334e302541789baef8daee5d` | Signature Authenticode Valid ; mise à niveau `/S` au code 0. |
| `structurearc.exe` installé | `0854e346ad92cbcdb4d911e0ce1cbe277fff3266b2dce4e9e63840d3d9affe84` | Signature Authenticode Valid ; autotest 18/18. |
| Binaire brut de production | `64862782fb98df7a4d63df9f6a49e974f468f568f656ead8246d8015e4167cf7` | Autotest 18/18 ; équivalence avec l’exécutable installé contrôlée hors marqueur du bundler et signature. |

La comparaison brut/installé est conforme hors **3 octets du marqueur du bundler** et **10 400 octets de signature**. La mise à niveau réelle a conservé exactement les empreintes des données contrôlées : **2 projets, 30 conversations, 319 messages**. Aucun aller-retour désinstallation/réinstallation isolé n’a été réalisé : l’installation utilisateur préexistante a été conservée. Cette validation porte sur une mise à niveau, sans généralisation à une installation propre ou à tous les postes.

Les contrôles du paquet sont établis. L’essai réel 10 s’est terminé en échec. Une signature valide et un autotest installé réussi ne constituent pas une certification d’autonomie. Les preuves détaillées de l’installation restent dans le dossier privé de livraison.

Le périmètre de publication se limite aux documents de livraison et aux installateurs validés. Il ne comprend ni sources privées, ni conversations, ni clés, ni bases utilisateur ou données d’essai. Les documents et paquets 1.3.17 restent inchangés.
