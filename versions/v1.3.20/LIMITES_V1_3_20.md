> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites de StructureArc V1.3.20

**3 novembre 2026 — paquet construit, signé et mise à niveau contrôlée ; autonomie complète non validée.**

## Validation du moteur et de l’interface

| Contrôle | Résultat | Portée |
| --- | --- | --- |
| Suite native finale | **946 réussis, 0 échec, 18 ignorés sur 964**, **217,38 s**, code **0** | Inclut les régressions de confidentialité des anciens historiques liés et de type du manifeste. Les ignorés ne comptent pas comme réussis. |
| Mobile et voix | **141 tests réussis** | Scénarios synthétiques navigateur, audio et transport ; aucun matériel physique. |
| Interface ciblée | **95 cas réussis** | Passage de cette version antérieur à la correction de deux clés de libellés de configuration des modèles ; ne pas le présenter comme un rejeu après ces corrections. |
| Production TypeScript et Vite | **Réussis** | Contrôles et génération de l’interface finale ; distincts d’un rejeu des 95 cas. |
| HTTPS et moteurs français Windows réels | **1 réussi**, code **0**, **11,38 s** ; **4 mots attendus sur 5** reconnus | Transport HTTPS authentifié, isolation entre sessions, synthèse/reconnaissance Windows, interruption et arrêt ; sans microphone, haut-parleur ou téléphone. |

Le premier passage natif **944/0/18** précédait les deux dernières protections ; seul le bilan **946/0/18** ci-dessus est le résultat final. Les suites ne sont pas additionnées en un total global. Les tests du moteur comprennent des réponses de fournisseur simulées et des opérations isolées ; ils ne mesurent pas la fiabilité générale d’un modèle réel.

Le scénario vocal réel ne valide ni une réponse du modèle dans le chat, ni l’installation physique sur Android/iPhone, ni le microphone ou le haut-parleur du téléphone, ni l’annulation acoustique d’écho.

## API Anthropic facultative et confidentialité

L’API Claude est sélectionnable dans le même chat que les modèles locaux. La clé reste dans le coffre du PC hôte ; le choix cloud est explicite pour le projet. Le contexte nécessaire à une requête distante est envoyé à Anthropic : ce mode n’est pas local ou hors connexion. Les outils restent soumis au même moteur et aux mêmes permissions ; aucun fournisseur ne peut les élargir.

**Aucun appel Anthropic authentifié avec une vraie clé n’a été effectué pour cette validation.** Les scénarios simulés ne prouvent pas l’accès de votre compte, la disponibilité des modèles, la facturation, les quotas ou la qualité du service réel. L’intégration API est distincte de Claude Code CLI.

Une conversation contenant d’anciennes observations de projets liés sans autorisation cloud durablement établie est refusée pour l’envoi distant, y compris après compactage. L’historique n’est pas effacé. Il peut être nécessaire de continuer en local ou d’ouvrir une nouvelle conversation pour le cloud ; une liaison locale antérieure n’autorise pas automatiquement cet envoi.

## Mobile et voix dans le même chat

La PWA installée reste dépendante du PC allumé, de StructureArc ouvert, du réseau et du fournisseur sélectionné prêt. PWA et HTTPS ne sont pas de nouvelles fonctions de cette version. Cette version corrige le manifeste effectivement servi en `text/html` dans la version précédente : il est maintenant servi en `application/manifest+json`. Cela ne garantit pas l’installation dans tous les navigateurs.

Un bouton vocal unique commande l’écoute et la lecture. Une interruption parlée réoriente le même chat. Après une indisponibilité initiale du service, les vérifications reprennent toutes les **15 secondes lorsque la page est visible**, au retour du réseau ou au retour au premier plan. Elles ne changent pas le choix du bouton vocal, n’activent pas un microphone désactivé et ne rétablissent pas une session expirée ou déconnectée.

La confiance HTTPS, les permissions du navigateur et son comportement en arrière-plan restent des conditions d’utilisation. Aucun test physique téléphone ou acoustique n’est établi. Moshi/Kyutai n’est pas intégré.

## Autonomie réelle : objectifs non atteints

Les essais réels **12 et 13 se sont terminés en échec** ; ils ne constituent pas des projets complets validés. Les échecs précédents ne sont pas requalifiés par cette mise à jour.

Au treizième essai, avec Qwen 4B, une réinitialisation de connexion a été observée ; aucun fichier demandé n’a été créé et les fichiers préexistants contrôlés sont inchangés. La cause racine de la rupture n’est pas établie. Ce constat ne suffit pas à conclure à une fiabilité générale du modèle ou du moteur.

L’ajout d’un fournisseur, un test vert ou un compte rendu positif ne certifie pas une réalisation conforme au besoin. L’autonomie complète et l’auto-amélioration fiable sur tout projet restent non validées.

## Paquet et mise à niveau contrôlés

| Artefact | Taille | SHA-256 | Contrôle |
| --- | --- | --- | --- |
| `StructureArc_1.3.20_x64-setup.exe` | **24 238 960 octets** | `f44f6b43912c7fecf966b5e356f2ee7b6ddf6270e5c96d5e09ed630f3c055c30` | Authenticode **Valid**, mise à niveau `/S` au code **0**. |
| Binaire brut de production | **15 221 760 octets** | `41af96714335c9fb01a912fcec5580c162b458146314cbb267095d24484d2125` | Autotest **18/18**, code **0**. |
| Exécutable installé | **15 232 160 octets** | `a52c7506757471256599bf2e9152aca8cf62b675ee282ec14827f5b159030ca3` | Authenticode **Valid**, autotest **18/18**, code **0**. |

La mise à niveau réelle sur l’installation existante a conservé exactement les empreintes des données contrôlées ; l’intégrité SQLite est correcte. Aucun aller-retour de désinstallation/réinstallation isolée n’a été réalisé. Ce contrôle ne généralise pas à une installation propre, à tous les postes ou à toutes les données possibles. Signature et autotest ne constituent pas une certification d’autonomie.

Le périmètre de publication est limité aux documents de livraison et aux installateurs contrôlés. Il exclut les projets privés, conversations, secrets, bases utilisateur et artefacts d’essai. Les versions historiques restent inchangées.
