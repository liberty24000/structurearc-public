> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1.3.10 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans commande ni rapport réel dans `preuves/`.

## Prouvé sur le build final (exe `d52f5f1ecf19…`, installateur standard signé `b9904cf6f80c…`, installateur hors-ligne signé `36691b57080e…`)
- **Chaîne de vérifications en fenêtre réelle** (`chain-1310-e.log`) : 5 scénarios en échec au premier passage, tous expliqués et relancés (`rerun-1310.log`) : `ui-chat-modes` (attendait encore l'ancien défaut GPU de 95 % : scénario corrigé, **19/19**) ; `ui-selfimprove`, `ui-selfimprove-mission`, `ui-selfimprove-real` (refus « espace disque insuffisant : 3,3 à 4,4 Go libres pour 5 Go exigés » : espace libéré, **20/20, 14/14, 19/19**). Le dernier, `ui-selfimprove-real --autonomous`, reste **INCONCLUSIVE** (15/15 vérifications mais le petit modèle s'est arrêté sans écrire : 4 appels d'outil, 0 proposition). `ui-agents-routing` reste INCONCLUSIVE (14/14, routage automatique non observé). Les autres scénarios sont PASS, dont `ui-gpu` 14/14 avec la limite à 100 %.
- **Tests automatiques** : `test.ps1` verdict global **PASS** (typecheck, vitest, scripts node, **cargo test 640 réussis / 0 échec / 11 ignorés**, auto-test du moteur, fenêtre native, test de fumée, écran IA en fenêtre réelle 16/16) — journal `test-1310.log`.
- **Installateurs** : standard signé (Valid) ; hors-ligne signé (Valid), `offline-installer-check` 9/9 et `model-embed-check` 8/8. La première fabrication hors-ligne a échoué à la signature (« aucun certificat trouvé », session de signature interrompue) ; relancée avec succès après reconnexion.

## Nouveautés et ce qui les prouve
- **GPU à 100 %** (décision du propriétaire) : tests unitaires de la garde (31/31) ; `ui-gpu` 14/14 et les chats sans réponse vide. **Non prouvé** : le filet de température n'a été validé que par simulation (aucune montée en température réelle de la GTX 1070) ; sans `nvidia-smi` lisible, il n'y a pas de filet de température.
- **Journaux Windows** (`docs/mesures/JOURNAUX_WINDOWS_PLANTAGES_2026-10-20.md`) : 4 redémarrages inattendus en octobre dont 3 écrans bleus `0xD1` (pilote non identifié, vidages non analysés faute de droits administrateur), saturation mémoire le 15 oct., 9 événements « bloc défectueux » sur le disque système. Aucun lien avec la charge GPU n'est démontré, aucun n'est exclu. **Sauvegardez le disque système.**
- **Reprise de projet et Markdown du projet** (`.structurearc/`) : 11 tests unitaires (aller-retour dans une base vide sans autorisation, fichiers invalides ignorés, conversation d'un autre projet non volée, arrêt d'urgence, création idempotente sans écrasement, dossiers d'agents en sous-dossiers). **Non prouvé** : ouverture réelle en fenêtre d'un dossier contenant `.structurearc/chats`, enregistrement sur plusieurs heures, comportement avec des milliers de messages. La sauvegarde est silencieuse en cas d'échec.
- **`files_read` avec `offset` et relectures alternées** : tests unitaires ; **non prouvé** avec un modèle réel sur de gros fichiers.

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Auto-amélioration** | Prouvée sur un petit module avec un petit modèle (4/4 une fois, mais le dernier passage autonome n'a rien écrit : résultat variable). L'observation libre (« continue ton développement ») n'a modifié aucun fichier lors du seul essai réalisé : cause identifiée (garde GPU, document de reprise périmé, lecture tronquée) et corrigée, **non rejouée depuis**. |
| **Demandes d'autorisation par l'IA** | Prouvées avec UN modèle (Qwen3.5 4B). En mode Auto, « tout » exclut l'installation de logiciels et la souris/clavier (décision de prudence, non demandée par le propriétaire). |
| **Gain du subconscient** | Mesuré seulement par simulation ; aucun gain démontré sous charge réelle. |
| **Routage automatique du chat** | Tests unitaires et scénario d'interface, mais aucune bascule observée en fenêtre réelle ; classification par mots-clés, précision jamais mesurée. |
| **Sauvegarde du cache par conversation, ordonnanceur d'emplacements** | Toujours non faits (reportés). |
| **Hérité** | Classement des modèles sur petits jeux ; une seule machine (Ryzen 7 2700, GTX 1070 8 Go, 16 Go) ; GPU AMD/Intel/CUDA et ARM non testés ; agents simultanés désactivés par défaut. |
| **Provenance de l'installateur hors-ligne** | Sa fabrication recompile l'application : l'exécutable contenu est DIFFÉRENT de celui de l'installateur standard ; vérifié par `offline-installer-check` et `model-embed-check` seulement. |
| **Mise à jour** | Manifeste non signé ; pas de retour arrière automatique des binaires. |
| **Certificat** | Affiche l'ancienne adresse (Sigean ; déménagement à Agen) : réémission Certum à faire ; SmartScreen peut avertir. |
