# Linux Privilege Escalation - Introduction & Enumeration : Strategic Analysis

## 💀 The Hack : Concepts & Mécanique

L'énumération est la fondation de l'attaque. Si tu ne trouves pas la faille, tu ne peux pas l'exploiter. Ici, on cherche tout ce qui dévie de la configuration standard "clean". Une simple erreur d'inattention de l'admin devient notre porte d'entrée.

1.  **Délégation de Privilèges (Sudo Rights) :**
    * *Le concept :* `sudo` permet à un utilisateur d'exécuter des commandes en tant que root. C'est le vecteur #1.
    * *La faille :* Si l'admin t'a donné le droit de lancer `/bin/vi` ou `/usr/bin/find` en sudo sans mot de passe, tu peux "t'échapper" de l'éditeur pour obtenir un shell root (technique *GTFOBins*).

2.  **Systèmes de Fichiers & Disques (Unmounted File Systems) :**
    * *Le concept :* Les admins montent parfois des disques de sauvegarde ou des partages temporaires, puis les démontent... mais oublient de supprimer l'entrée dans la configuration.
    * *La faille :* En inspectant `/etc/fstab` ou `lsblk`, tu peux trouver des disques cachés contenant des données sensibles ou des backups que tu peux remonter.

3.  **Services & Noyau (Kernel & Services) :**
    * *Le concept :* Le noyau (Kernel) est le maître absolu. Les services (Web, DB) tournant en root sont des cibles prioritaires.
    * *La faille :* Une version obsolète du noyau (ex: *Dirty COW*) ou d'un service (ex: *Screen 4.5.0*) permet une exploitation publique pour passer root.

4.  **Secrets & Historique (Credential Hunting) :**
    * *Le concept :* L'erreur humaine. Mots de passe tapés en clair, clés SSH oubliées dans `/home`, fichiers de configuration avec des identifiants DB.

## 🛡️ The GRC Pivot : Business Impact

* **Le Risque (CIA Triad) :**
    * **Confidentialité (Confidentiality) :** Des disques non montés contenant des backups non chiffrés exposent la propriété intellectuelle.
    * **Intégrité (Integrity) :** Un droit `sudo` mal configuré permet de contourner tout le contrôle d'accès (Access Control).
    * **Disponibilité (Availability) :** L'utilisation d'exploits Kernel instables risque de crasher le serveur (Kernel Panic).

* **Standards & Compliance :**
    * **ISO 27001 (A.9.4 - Access Control) :** Le principe de **Moindre Privilège (Least Privilege)** est violé si un utilisateur a des droits `sudo` excessifs ou inutiles pour sa fonction.
    * **PCI-DSS (Req 8) :** L'authentification et l'accès aux composants système. Les clés SSH sans passphrase trouvées sur le disque sont une violation directe.
    * **GDPR / RGPD :** L'accès root non autorisé sur une machine contenant des données personnelles constitue une brèche critique.

## 💾 The Armory : Essential Tech Terms

| Terme FR | Terme EN (Industry Standard) | Contexte d'usage |
| :--- | :--- | :--- |
| Droits Sudo | Sudo Privileges | La commande qui permet d'agir comme root. |
| Système de fichiers | File System / Mount point | Organisation des disques. Cible pour trouver des backups cachés. |
| Fichiers cachés | Dotfiles | Fichiers de config utilisateur (`.bash_history`, `.ssh/`). |
| Outils automatisés | Automated Tools | Scripts (LinEnum, LinPEAS) qui scannent tout le système. |
| Exploit Noyau | Kernel Exploit | Code attaquant le cœur de l'OS pour devenir root. |
| Processus Root | Running Process as Root | Service actif avec les droits maximums. |

## 🛠️ Tactical Toolkit : Commandes & Outils

*Ta boîte à outils opérationnelle extraite du module.*

| Vecteur / Cible | Commande Clé | Pourquoi l'utiliser ? |
| :--- | :--- | :--- |
| **Sudo Check** | `sudo -l` | **CRITIQUE.** Liste ce que tu peux lancer en tant que root. Premier réflexe à avoir. |
| **OS & Kernel** | `cat /etc/issue`, `uname -a` | Identifier la version pour chercher des exploits (ex: CVE-2016-5195). |
| **Services Root** | `ps aux \| grep root` | Voir quels processus tournent en root. Cible d'attaque prioritaire. |
| **Disques & Montages** | `cat /etc/fstab`, `lsblk` | Trouver des disques non montés ou des partages oubliés. |
| **Réseau** | `ip a`, `route`, `arp -a` | Comprendre avec qui la machine communique (pivot potentiel). |
| **Secrets (User)** | `ls -la /home/user/` | Chercher `.ssh`, `.bash_history` ou des fichiers de config. |
| **Automated (Script)**| `LinEnum.sh`, `linpeas.sh` | Lancer un scan complet. À utiliser *après* l'énumération manuelle. |

## 🧠 Q&A Rapide

**Question :** *"Cipher, j'ai trouvé une ligne dans `sudo -l` qui dit que je peux lancer `wget` sans mot de passe. C'est grave ?"*

**Réponse :** C'est *Game Over*. Si tu peux lancer `wget` en root, tu peux écraser n'importe quel fichier système (comme `/etc/shadow`) en téléchargeant un fichier malveillant par-dessus, ou exfiltrer des fichiers sensibles vers ton serveur attaquant. C'est un exemple classique de binaire "inoffensif" qui devient une arme fatale via `sudo`.