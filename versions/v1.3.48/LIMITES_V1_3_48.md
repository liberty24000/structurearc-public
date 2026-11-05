> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# Limites — StructureArc 1.3.48

- La reprise d'un appel local incomplet reste unique par tour. Elle change le profil demandé au runtime, sans garantir que le modèle réussira. Une nouvelle erreur est signalée ; aucun résultat incomplet n'est exécuté et aucune permission supplémentaire n'est accordée.
- Le profil de reprise concerne le fournisseur local. Les modèles cloud conservent leur protocole existant. Les mécanismes de raisonnement et de parallélisme habituels sont rétablis après une réponse complète.
- La reprise du scénario Qwopus9B P2 r04 sous le code de la 1.3.47 a échoué après 754806 ms sur deux limites de sortie consécutives. Deux sous-étapes sur six étaient terminées et README.md manquait. Le vérificateur indépendant a échoué. Les fichiers du modèle n'ont pas été réparés par le relecteur.
- L'essai frais P2 r05 du candidat 1.3.48 s'est arrêté après 418362 ms sur des relectures sans progression avec un contrôle échoué. Le plan de dix étapes ne respectait pas le format admis. Seuls cli.cjs et package.json étaient présents ; le parsing des arguments échoue aussi dans le contrôle externe. Aucune reprise de protocole n'a eu lieu dans cet essai : il ne mesure donc pas l'efficacité de cette correction sur un vrai modèle.
- Aucun modèle local n'est déclaré capable de réaliser tout projet. Les critères de qualification par scénarios et essais répétés restent ouverts.
- Les précisions d'équipe sont limitées au cycle natif concerné, aux messages admis avec provenance et au budget de contexte. Une session active est nécessaire à leur admission. Les adaptateurs CLI externes ne sont pas couverts par cette transmission.
- Les parcours mobiles vérifiés dans Chrome sur PC et les entrées audio synthétiques ne remplacent pas un essai physique sur Android. Le démarrage à froid du moteur vocal peut prendre plusieurs dizaines de secondes ; aucune latence instantanée n'est promise.
- La cohabitation du modèle local 9B et de Kyutai sur 8 Go de mémoire graphique n'est pas qualifiée : le modèle chargé ne laissait qu'environ 3 Go libres, sous le seuil de 5 Go exigé par le moteur vocal installé. Les essais vocaux de livraison restent séparés de cette combinaison.
- Les modèles et packs vocaux locaux dépendent des ressources disponibles. Un nombre illimité d'agents ou de modèles simultanés n'est pas garanti.
- Le subconscient reste un service de mémoire et de consolidation vérifiable, sans conscience ou sentiments humains affirmés.
