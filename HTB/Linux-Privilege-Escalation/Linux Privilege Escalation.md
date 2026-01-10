
# Linux Privilege Escalation : Strategic Analysis

## 💀 The Hack : Concepts & Mécanique

L'escalade de privilèges (Privilege Escalation) n'est pas de la magie, c'est de l'observation. Le concept repose sur le passage d'un utilisateur à faibles permissions (Low-privileged User) vers un utilisateur à hauts privilèges, généralement `root` (Vertical Escalation).

Pourquoi ça casse ? Parce que Linux est un système multi-utilisateurs complexe où la moindre erreur de configuration (Misconfiguration) ou de maintenance ouvre une brèche.
Voici les mécaniques principales couvertes par ce module :

1.  **L'Énumération (Enumeration) :** C'est la phase critique. On cherche ce qui sort de l'ordinaire : un fichier accessible en écriture, un binaire avec des capacités spéciales, ou des tâches automatisées. Sans bonne énumération, pas d'exploitation.
2.  **Exploits du Noyau (Kernel Exploits) :** Le noyau gère la communication entre le matériel et le logiciel. Si le noyau est obsolète (Outdated), un code malveillant peut corrompre la mémoire pour exécuter du code en tant que système. C'est violent et risqué.
3.  **Permissions & SUID :** Certains fichiers doivent s'exécuter avec les droits du propriétaire (souvent root) pour fonctionner (ex: `passwd`). Si ces fichiers (SUID Binaries) sont mal codés ou mal utilisés, on peut détourner leur fonction pour lancer un shell (Shell Spawning).
4.  **Détournement de Bibliothèques (Shared Object Hijacking) :** Les programmes appellent des bibliothèques externes (.so). Si on peut manipuler le chemin de recherche ou remplacer une bibliothèque manquante, le programme exécutera notre code malveillant avec ses privilèges.

**En résumé :** On cherche à forcer un processus légitime à haut privilège à exécuter nos instructions illégitimes.

## 🛡️ The GRC Pivot : Business Impact

Techniquement, tu deviens Dieu sur la machine. Mais pour le C-Level, voici la traduction :

* **Le Risque (CIA Triad) :**
    * **Confidentialité (Confidentiality) :** Rupture totale. `root` peut lire n'importe quel fichier, base de données ou clé de chiffrement présente sur le serveur.
    * **Intégrité (Integrity) :** L'attaquant peut modifier les logs système (Log Tampering) pour effacer ses traces, installer des portes dérobées (Backdoors) persistantes ou altérer les données métier.
    * **Disponibilité (Availability) :** Risque élevé de déni de service (DoS), surtout lors de l'utilisation d'exploits Kernel instables qui peuvent faire planter le serveur (Kernel Panic).

* **Standards & Compliance :**
    * **ISO 27001 :** Violation directe de l'annexe A.9 (Control of Access to Systems and Applications), spécifiquement la gestion des droits d'accès privilégiés (Privileged Access Management - PAM).
    * **NIST CSF :** Échec critique dans la catégorie "Protect" (PR.AC - Identity Management, Authentication, and Access Control).
    * **PCI-DSS :** Si le serveur traite des données de carte bancaire, l'escalade de privilèges viole l'exigence 7 (Restreindre l'accès aux données des titulaires de carte).

**Note pour l'audit :** L'existence de vecteurs d'escalade indique souvent un défaut dans le processus de gestion des correctifs (Patch Management) ou une absence de durcissement système (System Hardening).

## 💾 The Armory : Essential Tech Terms

| Terme FR | Terme EN (Industry Standard) | Contexte d'usage |
| :--- | :--- | :--- |
| Escalade de Privilèges | Privilege Escalation (PrivEsc) | Passer d'un utilisateur lambda à admin/root. |
| Énumération | Enumeration | L'art de fouiller le système pour trouver des failles. |
| Noyau | Kernel | Le cœur de l'OS. Une faille ici affecte tout le système. |
| Tâche planifiée | Cron Job | Tâches automatisées. Si modifiables, elles exécutent ton code. |
| Binaire SUID | SUID Binary (Set User ID) | Fichier s'exécutant avec les droits de son propriétaire (root). |
| Mauvaise configuration | Misconfiguration | Erreur humaine (permissions faibles, mots de passe par défaut). |
| Durcissement | Hardening | Processus de sécurisation pour réduire la surface d'attaque. |

## 🧠 Q&A Rapide

**Question :** *"Cipher, pourquoi ne pas simplement lancer un script automatisé (comme LinPEAS) et tout casser directement ?"*

**Réponse :** Calme-toi, script kiddie. Les scripts d'énumération automatisés (Automated Enumeration Scripts) sont bruyants. Dans un vrai engagement Red Team ou une infrastructure surveillée par un SOC, lancer LinPEAS sans réfléchir va déclencher toutes les alarmes. De plus, si tu ne comprends pas la sortie du script, tu passeras à côté de vecteurs subtils. Apprends à énumérer manuellement (Manual Enumeration) d'abord. Comprends la logique, ensuite tu pourras automatiser.