Learn about the ISO OSI model and the TCP/IP protocol suite.

# 🌐 Networking Concepts: Introduction
#TryHackMe #Networking #Basics #GRC

## 1. ⚙️ The Technical Core
Ce module est la fondation de toute communication informatique.
* **Key Topics:**
    * **OSI & TCP/IP Models:** Les standards qui régissent comment les données voyagent.
    * **Addressing:** IP Addresses, Subnets, Routing.
    * **Transport:** TCP vs UDP, Port numbers.
    * **Practice:** Se connecter manuellement à un port (ex: via Telnet).

## 🌍 Vision GRC (Consultant Focus)
Pourquoi un Consultant doit maîtriser le Réseau ?
* **Audit de Conformité (ISO 27001 / PCI DSS) :** De nombreuses exigences parlent de "Ségrégation réseau" (Subnets, VLANs). Tu dois vérifier que la compta n'est pas sur le même sous-réseau que le Wi-Fi invités.
* **Analyse de Risque :** Un port ouvert inutile sur Internet (ex: Telnet) est une "Vulnérabilité" critique.
* **Crédibilité :** Pour discuter avec les équipes Ops/Infra, tu dois parler leur langue.

## 🧠 Rappel Mémoire
"Pas de Réseau = Pas de Cyber. C'est l'autoroute sur laquelle roulent les données (et les attaques)."



# 🌐 OSI in Action:  exemple Sending a PDF (Technical Flow)
#TryHackMe #Networking #OSI #Encapsulation

## ⬇️ The Descent (Encapsulation)
Du clic de souris jusqu'au câble réseau.

### 1. Application Layer (L7) - The Data
* **User Action:** Tu uploades `file.pdf` sur un site web sécurisé.
* **Protocol:** **HTTP/HTTPS**.
* **Data:** Le navigateur prend le contenu brut du PDF.
* *Etat de la donnée :* "Raw Data" (Lisible).

### 2. Presentation Layer (L6) - The Formatting & Encryption
* **Action:** Le navigateur voit que c'est du HTTPS. Il demande au module **TLS/SSL** de chiffrer la donnée.
* **Result:** Le fichier PDF devient une bouillie illisible de caractères chiffrés.
* *Etat de la donnée :* "Encrypted Data".

### 3. Session Layer (L5) - The Conversation
* **Action:** Le système d'exploitation marque ce flux de données avec un **Session ID** unique pour ne pas le mélanger avec ton onglet YouTube ouvert à côté.

### 4. Transport Layer (L4) - The Segmentation (TCP)
* **Problem:** Le PDF fait 1 Mo. Le réseau ne peut pas avaler ça d'un coup (Max ~1500 octets).
* **Action:** **TCP** découpe le PDF chiffré en ~700 petits morceaux appelés **Segments**.
* **Header ajouté :**
    * **Source Port:** 49152 (Ton PC).
    * **Dest Port:** 443 (Serveur Web HTTPS).
    * **Sequence Number:** "Paquet 1 sur 700".

### 5. Network Layer (L3) - The Routing (IP)
* **Action:** On prend chaque segment TCP et on le met dans une enveloppe appelée **Packet**.
* **Header ajouté :**
    * **Source IP:** `192.168.1.15` (Ton PC).
    * **Dest IP:** `203.0.113.5` (Le Serveur Web).
* *Note :* Ici, le routeur sait où aller (l'adresse finale).

### 6. Data Link Layer (L2) - The Local Hop (Ethernet)
* **Action:** Pour quitter ton bureau, le paquet doit aller à ta **Box/Routeur** (Gateway).
* **Header ajouté (Frame) :**
    * **Source MAC:** `AA:BB:CC:DD:EE:FF` (Ta carte réseau).
    * **Dest MAC:** `11:22:33:44:55:66` (L'adresse physique de ta Box).
* **Trailer ajouté :** **FCS/CRC** (Une formule mathématique pour vérifier si le paquet arrive cassé).

### 7. Physical Layer (L1) - The Transmission
* **Action:** La carte réseau convertit la Frame (qui est logicielle) en signaux physiques.
* **Medium :**
    * Si Ethernet : Variations de voltage (+5V / 0V).
    * Si Fibre : Impulsions lumineuses.
    * Si Wi-Fi : Ondes radio.
* **Result:** `010101010...` part sur le fil.

---

## 🌍 Vision GRC (Data Protection Focus)
C'est ici qu'on place les contrôles de sécurité (Security Controls) :

* **DLP (Data Loss Prevention) - L7:** Un logiciel DLP scanne le PDF au moment de l'envoi (L7). S'il détecte le mot "Confidentiel", il bloque l'envoi avant même que le chiffrement ne commence.
* **Firewalling - L3/L4:** Le pare-feu de l'entreprise regarde les Headers L3 et L4.
    * *Rule:* "Autoriser IP Interne vers Port 443 (Web)". -> Le PDF passe.
    * *Rule:* "Bloquer IP Interne vers Port 21 (FTP)". -> Le PDF est détruit.
* **VPN (Tunneling) - L3:** Si tu utilises un VPN, tout ton paquet L3 est *ré-encapsulé* dans un autre paquet pour cacher ta destination finale.

## 🧠 Rappel Mémoire
"**S**ome **P**eople **F**ear **B**irthdays"
(Pour retenir le nom des unités de données de bas en haut : **S**egment, **P**acket, **F**rame, **B**its).
*Attention, l'ordre technique est Segment (L4) -> Packet (L3) -> Frame (L2) -> Bits (L1).*


# 🌐 The TCP/IP Model (Internet Protocol Suite)
#TryHackMe #Networking #TCPIP #Standards #GRC

## 1. ⚙️ The Concept
Contrairement aux 7 couches théoriques de l'OSI, le modèle TCP/IP condense tout en **4 Layers** (parfois 5 dans les livres modernes). C'est le langage universel d'Internet.

* **Origin:** Department of Defense (DoD) - 1970s.
* **Goal:** Robustesse et interopérabilité.

## 2. 🏗️ The 4 Layers (Mapping to OSI)
Le tableau de la Task 3 est fondamental. Voici la correspondance :

| TCP/IP Layer | OSI Equivalence | Protocols (Examples) | Role |
| :--- | :--- | :--- | :--- |
| **1. Application** | **L7, L6, L5** (App, Pres, Sess) | **HTTP, HTTPS, SSH, SMTP** | Gère tout ce qui est "Software" et Data. Tout est regroupé ici. |
| **2. Transport** | **L4** (Transport) | **TCP, UDP** | Gère la fiabilité et les ports. |
| **3. Internet** | **L3** (Network) | **IP, ICMP, IPSec** | Gère le routage et les adresses IP. |
| **4. Link Layer** | **L2, L1** (Data Link, Physical) | **Ethernet, Wi-Fi** | Gère l'accès physique au média. |

> *Note:* Certains manuels (comme Kurose & Ross) ajoutent une 5ème couche "Physical" distincte, mais le modèle original DoD en a 4.

---

## 🌍 Vision GRC (Consultant Focus)
* **Legacy Protocols & Compliance:**
    * Regarde la liste des protocoles dans la couche Application : `HTTP, FTP, Telnet`.
    * **Audit Reflex:** Ce sont des protocoles en texte clair (Clear Text). Si tu trouves du **Telnet** ou du **FTP** lors d'un audit -> **Non-Conformité Majeure** (Manque de Confidentialité). Il faut exiger **SSH** (Secure Shell) ou **SFTP**.
* **Resilience (Availability):**
    * L'histoire du DoD nous rappelle que TCP/IP est conçu pour la **Continuité d'Activité** (Business Continuity). Le réseau cherche toujours une route alternative si un nœud tombe.

## 🧠 Rappel Mémoire
"**TCP/IP** est un **OSI** simplifié pour le combat :
On garde le Cœur (Transport & Internet) et on simplifie les Extrémités (Application & Link)."


# 📍 IP Addresses and Subnets
#TryHackMe #Networking #IP #Subnetting #GRC

## 1. ⚙️ The Anatomy of an IP Address
Une adresse IPv4 est une série de **4 octets** (nombres de 0 à 255) séparés par des points.
* **Format:** `x.x.x.x` (ex: `192.168.1.1`)
* **Split Personality:** Une IP est divisée en deux parties via le **Subnet Mask** :
    1.  **Network Address:** L'identifiant de la rue (ex: `192.168.1`).
    2.  **Host Address:** Le numéro de la maison (ex: `.1`).

## 2. 🏠 Public vs Private (RFC 1918)
C'est la distinction la plus importante pour un auditeur.
* **Public IP:** Routable sur Internet. Une seule machine au monde la possède. (C'est la façade du magasin).
* **Private IP:** Non routable sur Internet. Utilisée uniquement en interne (LAN). (C'est l'arrière-boutique).

**Les 3 plages privées réservées (RFC 1918) :**
* `10.0.0.0` — `10.255.255.255` (Grandes entreprises)
* `172.16.0.0` — `172.31.255.255` (Moyennes entreprises / Cloud)
* `192.168.0.0` — `192.168.255.255` (Réseaux domestiques / TPE)

> **⚠️ Loopback Address:** `127.0.0.1` (Localhost). C'est toi-même. "There's no place like 127.0.0.1".

## 3. 💻 Essential Commands
Comment connaître son IP ?
* **Windows:** `ipconfig`
* **Linux / Mac:** `ifconfig` ou `ip addr`

---

## 🌍 Vision GRC (Consultant Focus)
* **Asset Management (ISO 27001 - A.8):** Tu ne peux pas protéger ce que tu ne connais pas. Un inventaire précis des IPs (Public & Private) est obligatoire.
* **Attack Surface Management:**
    * Une **IP Publique** est exposée à toute la planète. Elle doit être scannée et patchée en priorité.
    * Une **IP Privée** est "protégée" derrière le routeur (NAT), mais si un attaquant rentre dans le réseau, il peut l'attaquer.
* **Network Segregation:** Si tu vois des serveurs de Prod (`10.10.x.x`) et des PC Wifi Invités (`192.168.x.x`) qui communiquent sans firewall, c'est une faille critique.

## 🧠 Rappel Mémoire
"**192.168** c'est à la Maison.
**10.** c'est au Boulot.
Le reste, c'est souvent Internet."


# 🚚 UDP and TCP (Transport Protocols)
#TryHackMe #Networking #TCP #UDP #Handshake #GRC

## 1. ⚡ UDP (User Datagram Protocol)
Le protocole de l'urgence.
* **Concept:** **Connectionless** (Sans connexion). On envoie les paquets sans vérifier si le destinataire est prêt.
* **Philosophy:** "Fire and Forget" (Tirer et oublier).
* **Reliability:** Aucune. Pas d'**Acknowledgment** (Accusé de réception). Si un paquet est perdu, tant pis.
* **Use Cases:** Streaming vidéo, Jeux en ligne, VoIP (Skype). On préfère une image qui saute une micro-seconde plutôt qu'un lag de 3 secondes pour vérifier.
* *Analogie :* La Poste standard (Lettre verte). Tu la mets dans la boîte, tu espères qu'elle arrive, mais tu n'as pas de preuve.

## 2. 🤝 TCP (Transmission Control Protocol)
Le protocole de la fiabilité.
* **Concept:** **Connection-oriented** (Orienté connexion). On doit établir une relation avant de parler.
* **Philosophy:** "Trust but Verify".
* **Reliability:** Totale. Utilise des **Sequence Numbers** pour remettre les paquets dans l'ordre et redemander ceux qui manquent.
* **Use Cases:** Web (HTTP), Email (SMTP), Transfert de fichiers (FTP). On veut 100% du fichier, pas 99%.

### The Three-Way Handshake 🤝
Avant d'envoyer la moindre donnée, TCP effectue une poignée de main en 3 étapes :
1.  **SYN** *(Synchronize)* : Le Client dit "Bonjour, je veux te parler".
2.  **SYN-ACK** *(Synchronize-Acknowledge)* : Le Serveur répond "Bonjour reçu, je suis prêt".
3.  **ACK** *(Acknowledge)* : Le Client répond "Parfait, on commence".
-> *La connexion est établie (Established).*

## 3. 🚪 Ports (The Doors)
TCP et UDP utilisent des **Ports** pour savoir à quelle application parler.
* **Range:** 0 à 65 535.
* **Reserved:** Le port 0 est réservé.

---

## 🌍 Vision GRC (Consultant Focus)
* **DDoS Attacks (Availability):**
    * Une attaque classique est le **SYN Flood**. L'attaquant envoie des milliers de paquets **SYN** (Etape 1) mais ne répond jamais au **SYN-ACK**. Le serveur attend bêtement et sature sa mémoire -> Le site tombe.
* **Firewall Audit:**
    * Bloquer UDP sur les serveurs critiques (sauf DNS/NTP) est une bonne pratique pour éviter l'exfiltration de données rapide.
    * Autoriser TCP permet le contrôle de flux.

## 🧠 Rappel Mémoire
* **UDP** = **U**rgence (**D**émerde-toi, **P**arti !).
* **TCP** = **T**chatche (**C**onversation **P**olie).


# 📦 Encapsulation & Decapsulation
#TryHackMe #Networking #PDU #Basics #GRC

## 1. ⚙️ The Process (Encapsulation)
L'encapsulation est le processus d'ajout d'informations (Headers/Trailers) à la donnée à chaque descente de couche.

**La Hiérarchie des Noms (PDU - Protocol Data Units) :**
C'est LA terminologie à connaître par cœur pour ne pas passer pour un débutant.

1.  **Application Data:** La donnée brute (ex: Email, Photo).
2.  **Transport Layer (L4):**
    * Si TCP : On appelle ça un **Segment**.
    * Si UDP : On appelle ça un **Datagramme** (Datagram).
3.  **Network Layer (L3):**
    * On ajoute l'IP Header. On appelle ça un **Paquet** (Packet).
4.  **Data Link Layer (L2):**
    * On ajoute Header + Trailer (Fin). On appelle ça une **Trame** (Frame).

> *Note:* Sur le schéma, tu vois bien que la **Trame (Frame)** est la plus grosse, car elle contient le Paquet, qui contient le Segment, qui contient la Data.

## 2. ♻️ The Lifecycle (Send & Receive)
* **Emission (Encapsulation) :** Data -> Segment -> Packet -> Frame -> Bits.
* **Réception (Decapsulation) :** Le routeur ou le PC fait l'inverse. Il "ouvre le carton" (Frame), regarde l'adresse (Packet), et passe le contenu au dessus.

---

## 🌍 Vision GRC (Audit & Privacy)
* **Deep Packet Inspection (DPI) :**
    * Pour auditer le contenu (Data), un pare-feu doit être capable de "Décapsuler" toutes les couches jusqu'en haut.
* **Tunneling & VPN :**
    * Les attaquants cachent souvent des données volées en les encapsulant dans des protocoles inoffensifs (ex: *DNS Tunneling*). Ils cachent des "Segments" secrets dans des "Paquets" DNS.
    * *Règle GRC :* "Inspecter ce qui est encapsulé, pas juste l'étiquette sur le carton."

## 🧠 Rappel Mémoire (Les Unités)
"**S**ome **P**eople **F**ear **B**irthdays" (Encore lui !)
* **S**egment (L4)
* **P**acket (L3)
* **F**rame (L2)
* **B**its (L1)

# 🦖 Telnet (Teletype Network)
#TryHackMe #Networking #Legacy #Insecure #GRC

## 1. ⚙️ The Concept
Un protocole antique (Layer 7) qui permet d'accéder à une machine à distance en ligne de commande.
* **Port standard:** **23** (parfois déplacé).
* **Mechanism:** Ouvre une session texte brute entre ton PC et le serveur.

## 2. 💀 The Security Flaw (Clear Text)
Le problème mortel de Telnet est qu'il transmet tout en **Clear Text** (Texte clair).
* **Scenario:** Si tu tapes ton mot de passe `admin123`, il voyage tel quel sur le câble.
* **Attaque:** N'importe qui sur le réseau (avec Wireshark) peut voir le mot de passe passer.

## 3. 🛠️ The Practical Use (Debug)
Bien que mort pour l'administration système (remplacé par **SSH**), Telnet reste un outil génial pour **debugger**.
* *Pourquoi ?* Comme il envoie du texte brut, tu peux l'utiliser pour parler manuellement à d'autres services (Web, Mail) pour voir s'ils répondent.
* *Commande :* `telnet [IP] [PORT]`

---

## 🌍 Vision GRC (Audit & Compliance)
* **Vulnerability Management:**
    * Trouver le port 23 ouvert lors d'un pentest est une **Vulnérabilité Critique** (High/Critical).
* **Compliance (PCI-DSS / ISO 27001):**
    * L'usage de Telnet pour administrer des systèmes contenant des données sensibles est strictement interdit car il viole le principe de "Protection des données en transit".
    * **Action Consultant :** Si tu vois Telnet, tu exiges son remplacement immédiat par **SSH** (Port 22, chiffré).

## 🧠 Rappel Mémoire
"**Telnet** = **Tell** it to the **Net** (Dis-le à tout le réseau, sans chuchoter)."