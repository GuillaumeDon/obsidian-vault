# Linux Privilege Escalation - Service & Internal Enumeration : Strategic Analysis

## 💀 The Hack : Concepts & Mécanique

Après avoir visité la maison (fichiers), on écoute aux portes pour savoir ce que font les habitants. L'objectif est de comprendre la **logique interne (Internals)** du système pour retourner ses propres outils contre lui.

1.  **L'activité Humaine (User Behavior) :**
    * *Le concept :* Les admins laissent des traces.
    * *La faille :* L'historique des commandes (`history`, `.bash_history`) est souvent une mine d'or (mots de passe en clair, connexions SSH vers d'autres serveurs). Savoir qui est connecté (`w`, `lastlog`) te permet aussi d'éviter de te faire repérer (OpSec).

2.  **Les Processus & Services (Running Processes) :**
    * *Le concept :* Un service qui tourne en `root` est une cible.
    * *La faille :* Si un processus root exécute un script modifiable ou utilise une librairie vulnérable, tu peux détourner son exécution. Le système de fichiers `/proc` (Procfs) est une fenêtre directe sur le noyau et la mémoire de ces processus.

3.  **L'Arsenal Installé (Living off the Land) :**
    * *Le concept :* Utiliser les outils déjà présents sur la machine pour attaquer, sans rien télécharger.
    * *GTFOBins :* Des binaires légitimes (comme `awk`, `find`, `vim`) peuvent être utilisés pour "s'évader" et lancer un shell. Si un de ces binaires est mal configuré (SUID ou sudo), c'est gagné.

4.  **Le Tracage d'Exécution (System Call Tracing - `strace`) :**
    * *Le concept :* `strace` est un outil de diagnostic qui montre chaque appel système qu'un programme fait (ouvrir un fichier, envoyer un paquet réseau).
    * *L'attaque :* Si tu peux lancer `strace` sur un processus privilégié (ou un binaire SUID mal fait), tu peux voir quels fichiers il essaie d'ouvrir. S'il cherche un fichier de config qui n'existe pas, tu peux le créer et injecter ta config malveillante.

## 🛡️ The GRC Pivot : Business Impact

* **Le Risque (CIA Triad) :**
    * **Confidentialité :** `strace` peut intercepter des données non chiffrées en mémoire. L'historique Bash expose des secrets industriels ou des crédentials.
    * **Intégrité :** Des tâches planifiées (Cron Jobs) mal sécurisées permettent une modification persistante du système.
    * **Disponibilité :** Un "bruit" excessif dans les logs (généré par tes scans) peut masquer une vraie panne ou saturer le stockage.

* **Standards & Compliance :**
    * **PCI-DSS (Req 2.2) :** "Configuration standards". Laisser des compilateurs (`gcc`) ou des outils de debug (`strace`) sur un système de production est une violation des bonnes pratiques de durcissement (Hardening).
    * **ISO 27001 (A.12.4 - Logging and Monitoring) :** L'analyse des logs de connexion (`lastlog`) est une exigence défensive. Si l'attaquant peut lire ces logs, il peut aussi tenter de les altérer pour effacer ses traces.
    * **GDPR :** Si l'historique contient des données personnelles traitées manuellement par un admin, c'est une fuite de données potentielle.

## 💾 The Armory : Essential Tech Terms

| Terme FR | Terme EN (Industry Standard) | Contexte d'usage |
| :--- | :--- | :--- |
| Système de fichiers Proc | Procfs (`/proc`) | Système virtuel généré par le noyau. Contient l'état des processus en temps réel. |
| Appels Système | System Calls (Syscalls) | Demandes qu'un programme fait au noyau (ex: "ouvre ce fichier"). Visible via `strace`. |
| Tâches planifiées | Cron Jobs | Actions automatisées. Vecteur d'attaque classique si le script est modifiable. |
| GTFOBins | GTFOBins | Base de connaissance des binaires Unix légitimes exploitables pour l'escalade. |
| Historique | Shell History | Liste des commandes précédentes. Souvent négligé par les admins. |
| Paquets orphelins | Orphaned/Vulnerable Packages | Vieux logiciels installés (`apt list`) qui contiennent des failles connues. |

## 🛠️ Tactical Toolkit : Commandes & Outils

*Voici comment disséquer le système de l'intérieur.*

| Vecteur / Cible | Commande Clé / Syntaxe | Pourquoi l'utiliser ? |
| :--- | :--- | :--- |
| **Réseau Interne** | `cat /etc/hosts` | Voir les alias DNS internes (souvent des serveurs de dev ou de backup cachés). |
| **Activité Admin** | `history`, `cat ~/.bash_history` | **CRITIQUE.** Chercher des mots de passe tapés par erreur ou des connexions SSH. |
| **Qui est là ?** | `w`, `lastlog` | Voir si un admin est connecté (danger pour toi) ou quand il se connecte habituellement. |
| **Processus Root** | `ps aux \| grep root` | Lister les cibles potentielles. Cherche les logiciels non-standard tournant en root. |
| **Cron (Auto)** | `ls -la /etc/cron*` | Vérifier les scripts exécutés automatiquement. Sont-ils inscriptibles ? |
| **Analyse Dynamique**| `strace <commande>` | Voir ce qu'un programme "touche" (fichiers, réseau) lors de son exécution. |
| **Logiciels** | `apt list --installed` | Lister tout l'inventaire pour chercher des CVEs publiques. |
| **Scripts & Config** | `find / -type f -name "*.conf"` | Chercher des fichiers de config qui contiennent souvent des *hardcoded credentials*. |
| **GTFOBins Check** | *(Voir boucle for complexe dans le cours)* | Automatiser la vérification des binaires installés contre la liste GTFOBins. |

## 🧠 Q&A Rapide

**Question :** *"Cipher, j'ai trouvé un binaire `tar` sur la machine. C'est juste pour décompresser des archives, non ?"*

**Réponse :** Détrompe-toi. `tar` est un classique des **GTFOBins**. Si tu as le droit de l'exécuter en `sudo` ou s'il a le bit SUID (ce qui est rare mais possible), tu peux lui faire exécuter des commandes système via des options obscures (comme `--checkpoint-action`).
**Leçon :** Ne juge jamais un binaire par sa fonction officielle, juge-le par ce qu'il peut faire "en douce" (spawn shell, write file). Vérifie toujours sur [GTFOBins.github.io](https://gtfobins.github.io).