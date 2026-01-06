
An introduction to the main components of the Metasploit Framework.

# Ⓜ️ Metasploit Framework (Introduction)
#TryHackMe #Metasploit #Pentesting #Standard #GRC

## 1. ⚙️ The Concept
Metasploit est le **Framework** d'exploitation le plus utilisé au monde. Il ne sert pas juste à lancer une attaque, il couvre tout le cycle de vie d'un test d'intrusion :
* **Reconnaissance** (Info Gathering).
* **Exploitation** (Hack).
* **Post-Exploitation** (Vol de données, persistance).

## 2. 🧬 Two Versions
Il est crucial de distinguer les deux :
1.  **Metasploit Pro :** Version commerciale, payante, avec une **GUI** (Interface Graphique). Automatisée, utilisée par les entreprises pour gérer les campagnes de tests.
2.  **Metasploit Framework (MSF) :** Version Open-Source, gratuite, en **Ligne de Commande (CLI)**. C'est celle qui est installée sur Kali Linux et l'AttackBox. C'est celle que nous allons apprendre.

## 3. 🏗️ Core Components
L'architecture repose sur quelques piliers :
* **msfconsole :** L'interface de commande principale (le cockpit).
* **Modules :** Les briques logicielles (Exploits, Payloads, Scanners).
* **Tools :** Outils autonomes comme **msfvenom** (pour créer des virus/payloads).

---

## 🌍 Vision GRC (Consultant Focus)
* **Risk Scoring (CVSS):**
    * Dans le calcul du score CVSS v3/v4, il y a une métrique appelée **"Exploit Code Maturity" (E)**.
    * *Règle d'or :* Si une CVE possède un module Metasploit public, le score de risque réel augmente drastiquement. Pourquoi ? Parce que n'importe qui peut l'utiliser sans être un expert en C++ ou en Assembleur.
* **Shadow IT / Rogue Devices:**
    * Un auditeur vérifie souvent si des outils offensifs (comme Metasploit) sont installés sur des serveurs de production. C'est strictement interdit. Metasploit ne doit vivre que sur des machines d'audit dédiées (AttackBox / Kali).

## 🧠 Rappel Mémoire
"Metasploit est le **IKEA** du Hacking :
Tu n'as pas besoin de fabriquer la chaise (l'exploit) toi-même. Tu prends les pièces (Modules), tu suis la notice, et tu as le résultat."

