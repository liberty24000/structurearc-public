> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.60

Le contexte local est compté exactement avant génération avec le moteur compatible. Tant qu’il tient, les lectures restent complètes ; si la capacité est insuffisante, un checkpoint conserve les consignes, le plan et les contrôles en échec, puis le contexte est recompté. Les autres moteurs gardent la compression estimée. Après un échec de protocole local, la reprise structurée impose aussi des fragments plus courts dans son schéma.

Le pilotage autonome conserve mieux les observations utiles après compression : la dernière lecture exploitable reste accessible, et une lecture retirée du contexte peut être refaite sous les mêmes autorisations. Les petits résultats et les diagnostics restent lisibles. Une compression ne relance ni commande ni écriture et n'efface aucun contrôle en échec.

Les livrables ne confondent plus une technologie citée, comme Node.js, avec un fichier obligatoire. Les nouveaux plans refusent les contrôles JavaScript manifestement appliqués à des données JSON. Un module Node .cjs ou .mjs sans test voisin peut recevoir un contrôle de syntaxe, si le terminal automatique est autorisé.

Les écritures locales utilisent une borne adaptée à la réserve de sortie réellement disponible. Une proposition partielle à la borne ne peut plus remplacer silencieusement un fichier déjà assemblé plus long. Le chat reste central, sans nouvel écran de configuration ni service Harness externe.
