# Linux Privilege Escalation - Introduction & Enumeration : Strategic Analysis

## 💀 The Hack : Concepts & Mécanique

L'escalade de privilèges commence par une phase critique : l'**Énumération (Enumeration)**. C'est la reconnaissance du terrain une fois que tu as un pied dans la place (Initial Foothold).

Le principe est simple : chercher des anomalies, des erreurs de configuration ou des versions obsolètes qui permettent de passer de l'utilisateur standard à `root`.

Voici les vecteurs identifiés dans ton document :

1.  **L'OS et le Noyau (OS & Kernel Version) :**
    * *La logique :* Le noyau (Kernel) est le maître absolu. Si la version installée contient une vulnérabilité publique (Public Exploit) connue (comme *Dirty COW*), on peut corrompre la gestion mémoire pour obtenir les droits `root`. Attention, c'est instable et peut crasher la machine.

2.  **Services "Root" (Running Services as Root) :**
    * *La logique :* Un service (comme un serveur web ou une base de données) qui tourne avec les droits `root` est une cible prioritaire. Si tu trouves une faille dans ce service, le code que tu injecteras s'exécutera avec les privilèges du service... donc `root`.
    * *Exemple du texte :* Nagios, Exim.

3.  **L'Erreur Humaine & Historique (User History & Config Files) :**
    * *La logique :* Les administrateurs sont parfois paresseux ou imprudents. Ils laissent des mots de passe en clair dans des fichiers de configuration ou, pire, tapent des mots de passe directement dans le terminal, ce qui est enregistré dans le `.bash_history`.
    * *Le concept :* On cherche des secrets (Hardcoded Credentials) oubliés dans les répertoires personnels (`/home`).

4.  **Paquets Obsolètes (Outdated Packages) :**
    * *Exemple :* `Screen 4.5.0`. Un logiciel utilitaire banal qui, s'il n'est pas mis à jour, peut contenir une faille permettant l'escalade.

## 🛡️ The GRC Pivot : Business Impact

Pourquoi le business doit s'inquiéter de ton scan `ps aux` ? Parce que la compromission locale est souvent le prélude à la compromission du domaine.

* **Le Risque (CIA Triad) :**
    * **Confidentialité :** Une fois `root`, l'attaquant accède aux clés SSH et peut pivoter vers d'autres serveurs, voire attaquer l'Active Directory (Lateral Movement).
    * **Disponibilité :** Les exploits Kernel sont risqués. Tenter une escalade via le noyau peut provoquer un "Kernel Panic" et arrêter un serveur de production critique.
    * **Intégrité :** `root` peut modifier les binaires systèmes ou désactiver les logs d'audit.

* **Standards & Compliance :**
    * **ISO 27001 :**
        * **A.12.6.1 (Gestion des vulnérabilités techniques) :** L'organisation doit patcher ses noyaux et services (ex: Screen, Exim) pour éviter l'exploitation publique.
        * **A.9.4.3 (Gestion des mots de passe) :** La présence de mots de passe en clair dans `.bash_history` est une non-conformité majeure des pratiques de sécurité.
    * **GDPR / RGPD :** Si l'escalade permet d'accéder à des bases de données de clients (PII), c'est une violation de données qui doit être notifiée sous 72h.

## 💾 The Armory : Essential Tech Terms

| Terme FR | Terme EN (Industry Standard) | Contexte d'usage |
| :--- | :--- | :--- |
| Énumération | Enumeration | Collecte d'infos système pour trouver des failles. |
| Déplacement Latéral | Lateral Movement | Utiliser une machine compromise pour en attaquer une autre. |
| Fichiers cachés | Dotfiles (Hidden Files) | Fichiers commençant par `.` (ex: `.bash_history`) souvent ignorés mais critiques. |
| Exploit Public | Public Exploit / PoC | Code d'attaque disponible sur internet (ExploitDB, GitHub). |
| Processus en cours | Running Processes | Ce qui tourne actuellement (`ps aux`). |
| Version du noyau | Kernel Version | Cœur du système (`uname -a`). |

## 🧠 Q&A Rapide

**Question :** *"Cipher, pourquoi on regarde les paquets installés comme 'Screen' ? Ce n'est pas un service critique pourtant."*

**Réponse :** Excellente question. C'est souvent là que se cache le diable. Un logiciel comme `Screen` ou `Tmux` est souvent installé avec le bit **SUID** (Set User ID). Cela signifie qu'il s'exécute avec les droits de son propriétaire (souvent `root`), peu importe qui le lance. Si ce "petit" logiciel a une faille, il devient une arme mortelle pour obtenir un shell root. Ne néglige jamais les utilitaires.