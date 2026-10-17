> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de la V1 — ce qui est prouvé, ce qui ne l'est pas

Règle suivie : aucune ligne « prouvé » sans une commande et un rapport réel dans `preuves/`. Le reste est dit tel quel.

## Prouvé sur CE build (rapports dans `preuves/`)
- Installation / désinstallation silencieuses (`installer-check`), exécutable installé identique au build, auto-test de l'exe installé, 18 langues d'installateur compilées.
- Parcours en **fenêtre réelle** : accueil, projet, indexation, recherche, graphe, chat, permissions, terminal (liste fermée), lecture web, lecture Word/Excel/PowerPoint, modifications proposées/approuvées, compactage de conversation, agents locaux, routage entre modèles **avec bascule réelle**, mode/effort/commandes `/` du chat, limites de ressources, import de modèle refusé sans consentement, matrice de compatibilité, version web locale, i18n.
- **Inférence locale réelle** avec le modèle Qwen2.5 sous la garde de ressources : aucun échantillon à 80 % ou plus (CPU, RAM) pendant les scénarios.
- Tests de sources : Rust (`cargo test --lib`), TypeScript (`vitest`), types (`tsc`).

## NON prouvé ou partiel
| Sujet | Réalité |
|---|---|
| **Autre ordinateur** | Tout a été testé sur UNE machine (Windows 11, 16 Go de RAM, GTX 1070). Aucun test sur un autre PC. La compatibilité « tout matériel » est théorique (`docs/COMPATIBILITY.md`). |
| **Modèles** | **2 modèles seulement** sont référencés (Qwen2.5 0,5B et 1,5B, Q4_K_M). Les autres s'ajoutent par import GGUF local, après un test de démarrage réel. Pas de catalogue large. Les « paliers » de qualité sont déduits de la taille du fichier, pas mesurés. |
| **IA hors-ligne** | Le moteur est dans l'installateur, **pas le modèle** : le premier démarrage de l'IA exige Internet (téléchargement ≈ 0,5–1,1 Go, SHA-256 vérifié) ou un fichier GGUF déjà présent. |
| **GPU** | Runtime Vulkan optionnel : mesuré **hors fenêtre** sur une GTX 1070 (13 → 83 jetons/s, une exécution). Pas testé : CUDA, AMD, Intel, charge GPU prolongée, usage depuis la fenêtre. À 95 % d'utilisation de la carte, l'affichage Windows peut ralentir. |
| **Plafonds** | Politique de sécurité mesurée (échantillonnage ≈ 0,5 s), pas une garantie physique ; le GPU est mesuré, pas plafonné par le matériel. |
| **Terminal autonome (mode Auto)** | Prouvé par tests unitaires et d'intégration ; **pas** de scénario complet en fenêtre réelle avec un modèle qui enchaîne des commandes. |
| **Import GGUF depuis l'interface** | Backend prouvé sur un vrai fichier ; l'écran lui-même n'a qu'un test unitaire. |
| **Réseau local (HTTPS, port 8092)** | Testé en boucle locale et sur l'adresse privée de la machine ; **jamais depuis un autre appareil**. Certificat auto-signé (avertissement navigateur normal). Aucune règle de pare-feu n'est modifiée. |
| **Signature** | Installateur **non signé** (SmartScreen avertit). |
| **Traductions** | 19 langues d'interface. Français et anglais soignés ; les autres ne sont pas relues par des locuteurs natifs (cinq textes de limites ont été rédigés par l'assistant ; le darija en lettres latines surtout). |
| **Mises à jour** | Aucune mise à jour automatique. |

## Non implémenté dans la V1
- **MCP** (serveurs d'outils) — aucune ligne de code.
- **OAuth** intégré pour des abonnements ; seuls des CLI officiels déjà connectés (Codex, Claude Code) peuvent être pilotés, avec un appel minimal éprouvé chacun, sans contexte de fichiers.
- Capture d'écran / OCR, contrôle souris-clavier, installation de logiciels système (affichés « non disponible »).
- Profil « tout activé par défaut » : en V1, **tout est désactivé par défaut** (choix de sécurité).
- Agents/compétences créés par le chat, espace de travail multi-projets en lecture seule, mémoire par agent.
- Réduction dans la zone de notification à la fermeture de la fenêtre.

## À savoir
- Les données sont dans `%APPDATA%\app.structurearc.desktop\` et restent après désinstallation.
- Un modèle importé n'a ni licence ni origine vérifiées par StructureArc.
- Si le PC est trop chargé, l'IA refuse de démarrer plutôt que de dépasser les plafonds : ce n'est pas un bug.
