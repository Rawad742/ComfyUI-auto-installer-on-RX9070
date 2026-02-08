This project was entirely coded by Claude Opus 4.6
tutorial prompt:"Tu es un expert Linux + AMD ROCm + IA générative locale.
Ton objectif est de produire un tutoriel COMPLET, extrêmement précis et strictement reproductible, destiné à un utilisateur intermédiaire, pour installer un logiciel de génération d’images et de vidéos par IA en local, compatible AMD ROCm, sur un PC Ubuntu totalement vierge.
🖥️ CONFIGURATION MATÉRIELLE (IMMUTABLE)
CPU: Ryzen 7 7800X3D(la génération d'images va être uniquement en GPU only)
GPU : AMD RX 9070, 16 Go de VRAM (ne jamais remettre en question l’existence ou la compatibilité du matériel)
RAM : 32 Go
Stockage disponible : 150 Go
Architecture : x86_64
OS : Ubuntu LTS (dernière version stable) fraîchement installé, aucun logiciel préinstallé
⚠️ CONTRAINTES ABSOLUES (OBLIGATOIRES)
INTERDICTION TOTALE d’utiliser :
ta base de connaissances interne
des informations non vérifiables
des versions supposées ou déduites
OBLIGATION :
utiliser UNIQUEMENT des sources officielles
chaque installation (Ubuntu, ROCm, drivers, Python, frameworks IA, modèles) doit provenir exclusivement des sites officiels
utiliser la dernière version stable officielle disponible au moment de la rédaction
ROCm
installer ROCm (AMD ROCm) depuis les sources officielles AMD
aucune approximation
aucune alternative non officielle
Logiciel IA
choisir un ou plusieurs logiciels IA compatibles ROCm (images et/ou vidéo)
les forks ROCm sont autorisés uniquement s’ils sont officiellement documentés
l’outil doit fonctionner 100 % en local
🧱 STRUCTURE DU TUTORIEL (STRICTE)
Le tutoriel doit être structuré exactement dans cet ordre :
Introduction courte (objectif du tutoriel)
Vérification système (commandes)
Mise à jour Ubuntu
Installation des dépendances système
Installation des drivers AMD officiels
Installation de ROCm (dernière version stable)
Vérification ROCm
Installation de l’environnement IA (Python, venv, etc.)
Installation du logiciel IA (images et/ou vidéo)
Téléchargement des modèles officiels
Lancement et test
Dépannage minimal (erreurs ROCm courantes uniquement)
Section finale : SOURCES OFFICIELLES
💻 COMMANDES TERMINAL (CRITIQUE)
CHAQUE COMMANDE doit être fournie
AUCUNE commande ne doit être omise
AUCUN “faites ceci” sans commande
Toutes les commandes doivent être :
dans des blocs de code
copiables-collables telles quelles
Chaque bloc de commandes doit être précédé d’un court titre en français
Les commentaires dans les commandes doivent être en anglais
🌍 LANGUE
Tutoriel : français
Commentaires dans le terminal : anglais
🔐 SOURCES (OBLIGATION FORMELLE)
À la toute fin du document :
Ajouter une section intitulée exactement :
SOURCES OFFICIELLES
Cette section doit contenir :
uniquement des liens officiels
aucun commentaire
aucune phrase explicative
un lien par ligne
❌ INTERDICTIONS
❌ Aucune supposition
❌ Aucun raccourci
❌ Aucun outil propriétaire non officiel
❌ Aucun usage de base de connaissances interne
❌ Aucun commentaire personnel
✅ OBJECTIF FINAL
À la fin du tutoriel, l’utilisateur doit :
avoir un environnement ROCm fonctionnel
pouvoir générer des images et/ou des vidéos par IA en local
sans dépendre d’Internet après l’installation
avec une solution stable, officielle et maintenable
Commence immédiatement la rédaction du tutoriel."
script prompt :"Tu es un architecte systèmes Linux senior, spécialisé en automatisation d’installation, AMD ROCm, IA locale, et scripts résilients de niveau production.
Tu dois produire UN UNIQUE SCRIPT, dans le langage de programmation de ton choix, optimisé pour la fiabilité maximale sur Ubuntu LTS.
OBJECTIF GLOBAL
Créer un script d’installation automatique capable de :
installer tout l’environnement IA locale AMD ROCm décrit dans le tutoriel fourni
fonctionner sur un Ubuntu fraîchement installé ou partiellement configuré
reprendre exactement là où il s’était arrêté, même après :
redémarrage obligatoire
crash
coupure volontaire
se lancer automatiquement au démarrage du PC
se désinstaller proprement une fois l’installation réussie
produire des logs détaillés système
fonctionner 100 % sans interaction utilisateur
CONTRAINTES SYSTÈME (IMMUTABLES)
OS : Ubuntu LTS (dernière version stable)
GPU : AMD RX 9070 – 16 Go VRAM
RAM : 16 Go
Architecture : x86_64
Exécution : TOUJOURS avec sudo
L’IA finale NE DOIT PAS se lancer automatiquement
Le script d’installation DOIT se lancer automatiquement au boot
SOURCE DE VÉRITÉ
Le tutoriel précédemment généré est la référence principale
Tu DOIS t’y conformer
Tu AS le droit d’aller chercher des informations supplémentaires UNIQUEMENT sur Internet
Tu DOIS privilégier :
sources officielles
méthodes ayant le meilleur taux de réussite réel
COMPORTEMENT DU SCRIPT (OBLIGATOIRE)
1️⃣ Détection intelligente (idempotence)
Au démarrage, le script doit :
détecter précisément :
ce qui est déjà installé
ce qui est partiellement installé
ce qui est absent
ne jamais réinstaller inutilement
sauter automatiquement les étapes validées
2️⃣ Système de reprise robuste (CRITIQUE)
Le script doit implémenter :
un système de persistance d’état robuste (le meilleur possible)
capable de :
reprendre exactement à la commande précise
survivre à plusieurs redémarrages
aucune perte de contexte autorisée
3️⃣ Gestion avancée des erreurs
Pour CHAQUE commande critique :
Réessayer automatiquement 2 fois
Si échec :
analyser dynamiquement l’erreur
tenter une correction logique
Si échec final :
arrêt immédiat
message clair, explicite, actionnable
log détaillé
4️⃣ Redémarrages
Si un redémarrage est requis :
le script doit :
le déclencher automatiquement
se relancer automatiquement au boot
reprendre à l’étape exacte précédente
5️⃣ Démarrage automatique
Utiliser le mécanisme le plus simple et le plus fiable
Objectif :
lancement automatique du script au démarrage
exécution en root
reprise transparente
6️⃣ Journalisation
Logs détaillés
PAS dans le dossier du script
Emplacement système approprié
Inclure :
timestamps
étape courante
erreurs
décisions automatiques
7️⃣ Fin propre (OBLIGATOIRE)
Une fois l’installation entièrement réussie :
désactiver le démarrage automatique
supprimer :
le script lui-même
les services/timers associés
les fichiers d’état
laisser le système propre
ne rien casser
8️⃣ Sécurité & Non-interaction
Script 100 % non interactif
Aucun prompt utilisateur
Aucune confirmation manuelle
Sudo supposé valide au lancement
Si nécessaire, ouvrir la session root au boot pour permettre la saisie du mot de passe
FORMAT DE SORTIE (STRICT)
Produire UNIQUEMENT le script
Aucun texte explicatif
Aucun commentaire hors du code
Commentaires dans le code autorisés et encouragés
Le script doit être :
lisible
structuré
modulaire
maintenable
OBJECTIF FINAL
À la fin :
l’environnement IA ROCm est installé et fonctionnel
le script n’existe plus
le système est propre
l’utilisateur peut lancer l’IA manuellement quand il le souhaite
Commence immédiatement par produire le script."
