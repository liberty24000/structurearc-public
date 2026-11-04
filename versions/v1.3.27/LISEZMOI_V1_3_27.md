> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.27

## Chat, reprise et décisions

Une demande en langage courant peut lancer le cycle d’analyse, de réalisation et de vérification. « Continue » reprend uniquement le cycle associé à cette conversation, en conservant les étapes terminées. Les anciennes tâches d’un autre chat ne sont pas reprises par simple ressemblance de texte.

Les confirmations concernent le bouton et la demande choisis. Les autorisations déjà accordées sont reconnues. Une confirmation de commande sensible reste limitée à cette commande précise, une seule fois et pendant cinq minutes ; elle ne crée pas une autorisation générale.

Les questions de l’agent proposent des choix et une réponse libre. La réponse rejoint réellement la conversation et les tentatives suivantes du cycle courant. Une réponse à une question ne constitue pas une autorisation d’exécuter un outil.

La capacité de travail parallèle est calculée selon la charge, les emplacements du serveur local, la mémoire disponible et le modèle sélectionné. Les tâches dépendantes restent ordonnées ; une capacité inconnue ou insuffisante conserve l’exécution séquentielle.

## Sorties Claude interrompues

Le diagnostic réel a identifié une limite de sortie atteinte pendant un lot d’outils. Le budget des missions cloud est augmenté dans le contexte autorisé, indépendamment du budget local. Une reprise bornée demande des appels plus petits après une coupure de sortie confirmée. Aucun appel provenant d’un lot incomplet n’est exécuté.

## Modèles et preuves

Les appels d’outils locaux incomplets ou interrompus ne sont pas exécutés. Les outils ne sont jamais exécutés à partir d’une simple annonce de réussite du modèle. Les commandes et lectures simples explicitement demandées doivent correspondre à des preuves natives du travail courant.

Les sorties des processus en arrière-plan restent lisibles et structurées. Les écritures de conversations attendent correctement les autres écritures simultanées. Le contexte cloud dispose de son budget propre ; le budget d’un modèle local reste indépendant.

Les erreurs de protocole Anthropic sont accompagnées d’un diagnostic structurel local, sans recopier le raisonnement caché, les signatures, les arguments ou la clé dans le journal.

## Téléphone

Le serveur HTTPS reste au port **8092**. Le certificat serveur contient désormais l’identifiant de son autorité ; un ancien certificat serveur est remplacé sous la même autorité locale. La confiance déjà installée sur le téléphone est conservée. Le renouvellement est contrôlé aussi pendant le fonctionnement du serveur.

L’autorité locale est valable dix ans et les certificats serveur 90 jours. Leur renouvellement ne nécessite pas de réinstaller l’autorité. Aucun certificat éternel ni installation garantie sur tous les téléphones n’est annoncé. Il faut ouvrir la page HTTPS sans avertissement et installer l’autorité sur le téléphone si elle n’y est pas déjà reconnue. L’interface signale désormais un refus de préparation de l’application par le navigateur.

Les projets, conversations, clés, bases, certificats propres au PC et sources privées ne font pas partie de l’installateur ou du dépôt public.

Voir aussi le document LIMITES de cette version pour distinguer les contrôles automatisés, les essais réels et les validations restant à effectuer sur téléphone.

## Vérifications de cette livraison

**1043 tests natifs réussis, 0 échec, 18 ignorés sur 1061**, **208.33 s** ; **492 tests UI** sur 58 fichiers, TypeScript/Vite réussis. Autotests brut/installé **18/18**, signatures **Valid**, mise à niveau réelle code **0**, lignes des projets, conversations et messages exactement conservées.

Un petit projet Node.js sans dépendance a été créé par le vrai chat avec Sonnet 5.5 : quatre fichiers, trois étapes terminées, 16 tests écrits par le modèle et sept groupes de tests indépendants réussis ; 24 fichiers préexistants conservés. Les fichiers n’ont pas été écrits ou réparés par le réviseur. Ce résultat borné ne prouve pas la réussite de tout projet.

HTTPS strict (chaîne et adresse vérifiées) et six ressources PWA contrôlés sur l’application installée, autorité locale conservée. Aller-retour vocal français réel via HTTPS avec interruption et arrêt contrôlés, sans microphone ni haut-parleur. Cinq modèles locaux installés chargés séparément : quatre ont réellement lu un fichier et exécuté Node ; aucun des cinq n’a respecté tous les critères de réponse finale. Quatorze contrôles minimaux d’admission cloud acceptés, sans revendiquer quatorze projets complets. Installation physique téléphone, annulation acoustique d’écho et Moshi non validés.
