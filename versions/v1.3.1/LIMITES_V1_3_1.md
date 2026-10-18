> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.1 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build 85 (exe `1fc3ad6a6602…`, installateur signé `b99e83d13157…`)
- **Registre : 30 rapports « courant » = 29 PASS + 1 non-PASS conservé** (`ui-mcp` INCONCLUSIVE : l'appel d'un outil MCP par le modèle n'a pas été observé dans cette exécution ; voir plus bas). Premier passage de `test.ps1` : échec de COMPILATION par l'erreur Windows `os error 1117` (erreur de lien, 4ᵉ occurrence, journal conservé `test-ps1-1-echec-lien-1117.log`), second passage PASS..
- Installateur 16/16 ; mise à jour réelle `update-real` 33/33 ; runtime embarqué 8/8 ; inférence installée PASS ; `test.ps1` PASS au second passage (tests Rust 500 réussis / 0 échec / 6 ignorés, Vitest 154).
- Fenêtre réelle avec Qwen3.5 4B sur le GPU : **mission** 20/20 (appels d'outils enchaînés, commande sensible jamais exécutée sans confirmation, recherche web réelle sur Internet, **proposition de modification** non appliquée, arrêt d'urgence) ; HTTPS local, import GGUF, GPU, changement de modèle, agents, contrats, compactage, terminal, Office, modifications : voir `preuves/chain-summary.log`.
- Mesures de ce PC (Mistral 7B en 7 configurations, Qwen3.5 4B et 9B, Qwen2.5 0,5B/1,5B, Llama, Gemma, Phi, SmolLM2, Granite) : `docs/MESURES_PC.md` et `docs/mesures/*.json`.
- Connecteurs MCP : serveur réel (Node) — déclaration, découverte, exécution manuelle, changement de mode, audit sans contenu, arrêt d'urgence, suppression : prouvés en fenêtre réelle (`ui-mcp`) ; chemin chat → MCP → serveur prouvé par un test du vrai chat contre le vrai modèle.
- Capture d'écran + OCR local : lecture réelle d'une image et de l'écran, secrets masqués, audit sans le texte (tests).

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **MCP piloté par le modèle en fenêtre réelle** | INCONCLUSIVE : le modèle 4B appelle l'outil MCP dans environ une exécution sur deux (observé : appel exécuté et résumé correctement une fois ; texte sans appel d'autres fois). Le reste du scénario est prouvé. Cause de l'irrégularité non élucidée : la requête exacte relevée dans la fenêtre, rejouée contre le même modèle, déclenche l'appel 8 fois sur 8, et le vrai code du chat contre le vrai modèle l'exécute 6 fois sur 6 hors de la fenêtre. |
| **Capture d'écran / OCR** | Pas de scénario en fenêtre réelle (l'écran de l'utilisateur serait lu). L'écran peut montrer des données d'AUTRES applications : accorder l'autorisation le temps nécessaire seulement. |
| **Une machine, un essai** | Toutes les mesures viennent d'un seul PC (Ryzen 7 2700, GTX 1070 8 Go, 16 Go), un seul essai (sauf mention « n=10 »), petits jeux de questions. Le cas « plus gros que la carte graphique » n'est PAS mesuré (un 7B de 4,4 Go tient dans 8 Go) ; il est seulement simulé par un nombre de couches réduit. |
| **Qwen3.5 4B sur ce PC** | Le déport de couches est plafonné à 3/4 (24 sur 32 couches) pour rester sous la limite de charge de la carte : 12,8 jetons/s au lieu de 47 à pleine charge. Sans carte graphique utilisable : 4,2 jetons/s (non recommandé). |
| **Garde de ressources** | Un échantillon de charge GPU à 95,5-96,3 % a été observé deux fois dans des scénarios avant le plafonnement ; la garde est réactive (elle interrompt après deux mesures), pas prédictive. |
| **Création d'agents sans approbation** | Option disponible mais testée seulement par tests unitaires, pas en fenêtre réelle. |
| **Souris/clavier, installation de logiciels** | Non implémentés (V1.4). |
| **Autre ordinateur** | UN seul PC testé. GPU AMD/Intel/CUDA non testés. |
| **Certificat** | Affiche l'ancienne adresse de l'entreprise (Sigean ; déménagement à Agen le 10 août 2026) : réémission par Certum à faire par le propriétaire ; le type « Open Source Developer » reste à vérifier avec Certum ; SmartScreen peut avertir. Après réémission, revérifier l'éditeur épinglé de la mise à jour. |
| **Mise à jour** | Pas de signature du manifeste ni de retour arrière automatique des binaires (V1.6). |
| **Installateur hors-ligne** | Non fait (V1.3.2). |
