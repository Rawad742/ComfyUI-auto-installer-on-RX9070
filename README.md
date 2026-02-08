# ComfyUI auto-installer pour RX 9070 — README (amélioré)

Ce dépôt fournit un installateur entièrement automatisé, idempotent et résilient au redémarrage pour déployer un environnement local de génération d'images basé sur AMD ROCm et ComfyUI sur une machine équipée d'un GPU AMD RX 9070.

Auteur de la base du projet : Claude Opus 4.6

---

## Objectif (court)
Fournir un script fiable et reproductible qui installe, configure et vérifie :
- AMD ROCm (driver + stack)
- PyTorch compatible ROCm (wheels officiels)
- ComfyUI (upstream officiel)
- Checkpoint SDXL Turbo (Stability AI / Hugging Face)

Le tout pour Ubuntu LTS (cible : Ubuntu 24.04) sur une machine équipée d’un AMD RX 9070 (gfx1201 / RDNA 4).

---

## Points forts
- Installation 100 % automatisée et non interactive (exécution avec sudo requise)
- Idempotence : ne réinstalle pas les composants déjà validés
- Résilience au redémarrage : reprend là où elle s’est arrêtée
- Logs détaillés et mécanisme de persistance d’état pour reprise fiable
- Désinstallation propre automatique une fois l’installation terminée
- Conçu pour s’appuyer uniquement sur des sources officielles

---

## Public cible
Utilisateurs intermédiaires à avancés souhaitant un environnement local ROCm + ComfyUI prêt à l’emploi sur un système Ubuntu LTS propre.

---

## Configuration matérielle et logicielle ciblée
- GPU : AMD RX 9070 (16 Go VRAM, gfx1201 / RDNA 4)
- RAM : conçu initialement pour 32 Go (voir notes du script)
- Disque : ≥ 150 Go d'espace disponible recommandé
- CPU : x86_64 (ex. Ryzen 7 7800X3D)
- OS : Ubuntu LTS (dernière version stable — ciblé : 24.04)
- Exécution : toujours avec sudo (root)

---

## Ce que fait l’installateur
- Installe les drivers AMD officiels et le stack ROCm (version ciblée dans le script)
- Installe PyTorch construit pour ROCm (wheels officiels de repo.radeon.com)
- Clône et installe ComfyUI (version upstream officielle)
- Télécharge et installe le checkpoint SDXL Turbo (Stability AI / Hugging Face) si demandé
- Gère redémarrages, erreurs transitoires et reprise automatique
- Produit des logs détaillés (chemin système défini dans le script)
- Supprime automatiquement le mécanisme de démarrage et le script à la fin (système propre)

---

## Avant de commencer (prérequis)
- Système Ubuntu LTS fraîchement installé ou partiellement configuré
- Session avec un utilisateur disposant de sudo (le script suppose sudo valide)
- Connexion Internet durant l’installation (les modèles et paquets sont téléchargés depuis sources officielles)
- Sauvegarde des données importantes recommandée avant exécution (script peut redémarrer le système)

---

## Utilisation rapide
1. Récupérer le script depuis ce dépôt (exemple) :
   - Télécharger ou cloner le dépôt localement.
2. Lancer le script en root (exécution unique — il s’auto-installe pour reprise au boot) :
   - Exécuter le script avec sudo comme indiqué dans le dépôt.
3. Attendre la fin de l’installation. Le script :
   - redémarrera la machine si nécessaire,
   - reprendra automatiquement au démarrage,
   - supprimera ses traces après succès complet.

(Remarque : le README du dépôt contient le script d’installation complet et les instructions détaillées pour l’exécuter et le déboguer.)

---

## Journalisation et état
- Logs détaillés : positionnés dans un emplacement système approprié (configurable dans le script)
- Fichiers d’état persistants : utilisés pour la reprise précise des étapes en cas d’arrêt/redémarrage

---

## Comportement en cas d’erreurs
- Pour chaque commande critique, le script :
  - réessaie automatiquement (configurable, par défaut 2 tentatives),
  - tente des corrections basiques automatiques en cas d’erreurs communes,
  - en cas d’échec final : arrête l’installation, écrit un log détaillé et affiche un message d’erreur explicite avec action recommandée.

---

## Désinstallation / Fin propre
- Une fois l’installation validée et réussie :
  - le script désactive et supprime son mécanisme de lancement automatique,
  - le script lui‑même et les fichiers d’état sont supprimés,
  - le système est conservé propre et opérationnel pour un usage manuel de ComfyUI.

---

## Dépannage minimal — erreurs ROCm courantes
- Problèmes courants :
  - incompatibilité du kernel / package amdgpu : vérifier que la version du kernel est supportée par la version ROCm ciblée
  - manque d’headers du kernel : installer `linux-headers-$(uname -r)`
  - conflits avec pilotes propriétaires antérieurs : purger les paquets amdgpu/dkms précédents si nécessaire
- Pour chaque erreur, consultez d’abord les logs générés par le script dans le répertoire de logs système (chemin fourni par le script).

---

## Contribuer
- PRs bienvenues pour améliorer la robustesse, la compatibilité et la documentation.
- Respecter la philosophie : s’appuyer sur sources officielles uniquement pour les composants critiques.

---

## SOURCES OFFICIELLES
https://rocm.docs.amd.com/projects/radeon-ryzen/en/latest/
https://rocm.docs.amd.com/projects/radeon-ryzen/en/latest/docs/install/installrad/native_linux/install-radeon.html
https://rocm.docs.amd.com/projects/radeon-ryzen/en/latest/docs/install/installrad/native_linux/install-pytorch.html
https://rocm.docs.amd.com/projects/radeon-ryzen/en/latest/docs/advanced/advancedrad/linux/comfyui/installcomfyui.html
https://repo.radeon.com/amdgpu-install/7.2/ubuntu/noble/
https://repo.radeon.com/rocm/manylinux/rocm-rel-7.2/
https://github.com/comfyanonymous/ComfyUI
https://huggingface.co/stabilityai/sdxl-turbo
