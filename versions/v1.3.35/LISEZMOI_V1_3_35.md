> *Note : ce texte provient du paquet de livraison complet. Les renvois à `preuves/`, `docs/` ou `test.ps1` désignent des éléments conservés par le titulaire, non publiés dans ce dépôt.*

# StructureArc 1.3.35 — Reconnaissance vocale française locale

La reconnaissance du chat PC et mobile utilise désormais Whisper base multilingue, forcé en français. Le moteur et les poids vérifiés sont fournis avec l’installateur ; aucune clé API vocale ni transmission à un service externe n’est nécessaire. La synthèse française Windows reste utilisée pour les réponses. Le chat conserve un seul bouton vocal. Le texte reconnu suit ensuite le modèle choisi dans le chat, local ou cloud.

Le microphone reste actif pendant la transcription et la réponse. Les premières consonnes sont conservées dans une réserve audio de 300 ms, une pause de 700 ms termine la phrase, et la détection d’interruption accepte une voix plus faible. Le navigateur ajuste automatiquement le volume quand il le permet. Un indicateur signale la transcription ; si aucun texte n’est reconnu, le chat invite à répéter sans créer de message inventé.

Les sons restent en mémoire. La reconnaissance s’exécute sur le CPU avec quatre threads au maximum, un plafond par processus de 1 Gio et un Job Windows limité à 25 % du CPU total. Le traitement est arrêté à la désactivation du mode vocal. Les ressources sont vérifiées par SHA-256 ; les licences MIT des composants vocaux sont incluses.

La comparaison sur huit extraits français synthétiques reproduit une erreur de l’ancien moteur : « Salut » devenait « Fallu ». Whisper reconnaît « Salut » aux deux volumes testés. Le traitement prend environ trois secondes sur le PC de test ; une faute d’homophone reste possible (« Peut-tu »). Ce résultat ne constitue pas un benchmark de voix humaines.

Les tests d’interface, de segmentation et du circuit vocal réel synthétique sont conservés avec la livraison. Le test vocal natif valide « Salut, peux-tu continuer le projet ? », la synthèse parallèle, l’interruption et l’arrêt des processus. La qualité sur téléphone physique, le bruit ambiant et l’écho doivent encore être vérifiés par l’utilisateur. Moshi/Kyutai n’est pas intégré. Les autres objectifs d’autonomie restent en cours : cette version ne qualifie pas tous les projets ni tous les modèles.

Validation : 1 057 tests natifs réussis (20 essais explicites ignorés), 509 tests d’interface réussis. Les deux essais vocaux synthétiques réels ont aussi été rejoués après signature des composants : reconnaissance française, synthèse, interruption, arrêt et circuit HTTPS authentifié. Le code exécutable des treize composants signés a été comparé aux originaux ; seules les zones de signature diffèrent.

Mise à jour signée installée et relancée : 18/18 autotests sur le binaire final et installé, données des projets et conversations conservées par comparaison exacte avant/après. Les 14 ressources vocales installées correspondent aux empreintes compilées. Le moteur installé reconnaît « Salut ! » sur deux extraits synthétiques de volumes différents, en environ trois secondes. Les sept ressources mobiles contrôlées répondent en HTTPS avec validation du certificat, inchangé, sur le port 8092. La confirmation de qualité avec la voix réelle sur Android reste attendue.
