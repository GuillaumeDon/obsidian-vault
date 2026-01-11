# Linux Privilege Escalation - Environment Enumeration : Strategic Analysis

## 💀 The Hack : Concepts & Mécanique

L'énumération n'est pas une simple collecte de données, c'est l'acquisition de la **Conscience Situationnelle (Situational Awareness)**. Dès que ton *Reverse Shell* atterrit, tu es un étranger dans une maison inconnue. Tu dois cartographier les lieux sans déclencher l'alarme.

Voici les axes critiques de cette reconnaissance :

1.  **L'Identité & Le Contexte (User & OS Context) :**
    * *La logique :* Savoir qui tu es (`uid`, `gid`) détermine tes droits immédiats. Savoir où tu es (Ubuntu, CentOS, Kernel version) détermine ton arsenal d'exploits (Exploit Compatibility). Un noyau obsolète est une autoroute vers `root`.

2.  **L'Environnement Volatile (Environment Variables & Path) :**
    * *La logique :* Le `$PATH` dicte où le système cherche les exécutables. Si tu peux écrire dans un dossier du PATH, tu peux détourner des commandes (Path Hijacking). La commande `env` révèle parfois des clés d'API ou des mots de passe chargés en mémoire.

3.  **Les Secrets Dormants (Storage & Hidden Files) :**
    * *La logique :* Les administrateurs cachent la poussière sous le tapis.
    * **Fichiers cachés (Dotfiles) :** `.bash_history` est le journal intime de l'admin (commandes tapées, erreurs de mot de passe).
    * **Systèmes de fichiers (Filesystems) :** `/etc/fstab` et les disques non montés (`lsblk`) contiennent souvent des backups oubliés ou des identifiants de montage en clair.

4.  **Persistance Temporaire (`/tmp` vs `/var/tmp`) :**
    * *La logique :* Tu as besoin d'un espace de travail inscriptible (Writable Directory).
    * `/tmp` est vidé au redémarrage (Volatile).
    * `/var/tmp` survit au redémarrage (Persistent). Choisis ton camp selon la durée de l'opération.

## 🛡️ The GRC Pivot : Business Impact

* **Le Risque (CIA Triad) :**
    * **Confidentialité (Confidentiality) :** Exposition critique via les fichiers d'historique (`.bash_history`) ou les configurations de montage (`fstab`) contenant des *Cleartext Credentials*.
    * **Intégrité (Integrity) :** Des permissions laxistes sur les binaires ou le PATH permettent l'injection de code malveillant.
    * **Disponibilité (Availability) :** L'énumération agressive (scans) peut saturer les ressources, et l'exploitation de vieux noyaux (Kernel Panic) peut crasher la production.

* **Standards & Compliance :**
    * **ISO 27001 (A.12.6.1 - Gestion des vulnérabilités) :** L'utilisation de versions d'OS en fin de vie (End of Life - EOL) comme mentionné pour Ubuntu, est une non-conformité majeure.
    * **PCI-DSS (Requirement 8) :** Interdiction stricte de stocker des identifiants lisibles dans des scripts ou fichiers de config (`fstab`).
    * **NIST CSF (Identify - ID.AM) :** L'organisation doit connaître ses actifs (Asset Management). Si un attaquant trouve un disque "oublié" avant l'admin, c'est un échec de gouvernance.

## 💾 The Armory : Essential Tech Terms

| Terme FR | Terme EN (Industry Standard) | Contexte d'usage |
| :--- | :--- | :--- |
| Conscience Situationnelle | Situational Awareness | Comprendre l'environnement avant d'agir. |
| Fichiers cachés | Dotfiles | Fichiers commençant par `.` (ex: `.ssh`, `.bashrc`). |
| Point de montage | Mount Point | Répertoire où un système de fichiers est attaché. |
| Variable d'environnement | Environment Variable | Valeurs dynamiques (`PATH`, `USER`) affectant les processus. |
| Fin de vie | End of Life (EOL) | Version logicielle qui ne reçoit plus de correctifs de sécurité. |
| Table de routage | Routing Table | Carte des réseaux accessibles par la machine. |

## 🛠️ Tactical Toolkit : Commandes & Outils

*Voici les commandes manuelles pour cartographier ton environnement sans dépendre d'outils externes.*

| Vecteur / Cible | Commande Clé | Pourquoi l'utiliser ? |
| :--- | :--- | :--- |
| **Identité** | `whoami`, `id` | Vérifier tes droits et groupes actuels. |
| **OS Info** | `cat /etc/os-release` | Identifier la distribution pour adapter les outils/exploits. |
| **Kernel Info** | `uname -a` | **CRITIQUE.** Chercher la version précise pour les exploits Kernel (Dirty COW, etc.). |
| **Env & Path** | `env`, `echo $PATH` | Chercher des secrets en mémoire ou des chemins inscriptibles. |
| **Réseau** | `ip a`, `route`, `arp -a` | Identifier les interfaces, les voisins et les routes (Pivot). |
| **Services & Ports** | `netstat -rn` | Voir les connexions actives et ports en écoute. |
| **Disques** | `lsblk`, `df -h` | Lister les périphériques de stockage (même non montés). |
| **Secrets (Fstab)** | `cat /etc/fstab` | Chercher des mots de passe de montage ou des disques oubliés. |
| **Secrets (User)** | `find / -name ".*" 2>/dev/null` | Traquer les fichiers cachés (`.bash_history`, `.ssh`) accessibles. |
| **Shells** | `cat /etc/shells` | Vérifier la présence de `screen` ou `tmux` (utile pour la persistance). |

## 🧠 Q&A Rapide

**Question :** *"Cipher, pourquoi perdre du temps à taper toutes ces commandes alors que je peux juste lancer `LinPEAS.sh` ?"*

**Réponse :** C'est la différence entre un technicien et un ingénieur.
1.  **Discrétion (Stealth) :** LinPEAS est bruyant, il génère des milliers de logs. Dans un environnement surveillé (EDR/SIEM), tu te fais griller instantanément.
2.  **Dépendance :** Et si tu n'as pas internet pour télécharger le script ? Et si `curl` est bloqué ?
3.  **Compréhension :** LinPEAS te donne des pistes, mais l'énumération manuelle (Manual Enumeration) te donne le contexte. Tu dois valider chaque alerte du script manuellement de toute façon. Utilise l'automatisation comme complément, pas comme béquille.