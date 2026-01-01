Learn about the security triad and common security models and principles.


# 🏁 Security Principles: Introduction & Context
#TryHackMe #SecurityPrinciples #Intro #GRC

## 1. 🎯 The Core Philosophy
Security is not an absolute state; it is defined by the **Context**.
* **Buzzword Warning:** Many companies claim "security" without defining it.
* **No 100% Security:** Perfect security is impossible. The goal is to raise the cost/difficulty for the attacker so it's not worth their effort.

## 2. 🎭 Threat Modeling (Know Your Enemy)
You cannot protect a system if you don't know *who* you are fighting.
* **Scenario A:** Protecting a laptop from a **Toddler** 👶 -> Simple password.
* **Scenario B:** Protecting technical designs from **Industrial Spies** 🕵️ -> Encryption, MFA, Air-gap.
> **Rule:** The defense mechanism must match the value of the asset and the capability of the adversary.

---

## 🌍 Vision GRC (Consultant Focus)
* **📉 Residual Risk:** Since "100% security" doesn't exist, the risk that remains after applying controls is the **Residual Risk**. Management must accept this.
* **💰 Proportionality (Cost/Benefit):** Never spend $1 Million to protect a $10 asset. This is the basis of **Risk Assessment**.
# 🛡️ Security Principles: CIA Triad & Parkerian Hexad
#TryHackMe #SecurityPrinciples #CIA #GRC #Revision

## 1. 🔺 The CIA Triad (The Core)
The three non-negotiable pillars. If one fails, the system is compromised.

### 🔒 Confidentiality (Privacy)
* **Definition:** Only authorized people can access the data.
* **💥 Attack:** Data Breach, Snooping, Eavesdropping.
* **🛡️ Defense:** Encryption (AES), Access Controls (ACL), MFA.

### ✍️ Integrity (Accuracy)
* **Definition:** The data has not been altered or tampered with.
* **💥 Attack:** Man-in-the-Middle (changing bank details), Database injection.
* **🛡️ Defense:** Hashing (SHA-256), Digital Signatures, Checksums.

### ⏱️ Availability (Uptime)
* **Definition:** The system is accessible when needed.
* **💥 Attack:** DoS/DDoS, Ransomware (locking data), Power Failure.
* **🛡️ Defense:** Redundancy, RAID, Backups, Load Balancing.

> **💀 The Anti-Triad (DAD):**
> * 👁️ **D**isclosure (vs Confidentiality)
> * ✏️ **A**lteration (vs Integrity)
> * 💣 **D**estruction/Denial (vs Availability)

---

## 2. 🚀 Beyond CIA (Advanced Concepts)

* **🆔 Authenticity:** Verifying the *origin*.
    * *Question:* Is this email *really* from the CEO? Is this update *really* from Microsoft?
* **📜 Non-Repudiation:** The *legal proof*.
    * *Definition:* The sender cannot deny their action later.
    * *Context:* Essential for banking & contracts. (e.g., "I didn't order these 1000 cars" -> Logs + Signature prove you did).

---

## 3. 🧩 The Parkerian Hexad ("CIA + 3")
An expanded model adding three granular elements:

1.  **🎒 Possession:** Holding the physical media.
    * *Example:* A thief steals your encrypted hard drive. They have **Possession**, but not Confidentiality (can't read it).
2.  **🔧 Utility:** The data is useful.
    * *Example:* You lose the decryption key. You have the drive (Possession), the file is there (Availability), but it's garbage code -> Zero **Utility**.
3.  **🆔 Authenticity:** (See above).

---

## 🌍 Vision GRC (Consultant Focus)
* **⚖️ Compliance & Law:**
    * **Confidentiality** is the heart of **GDPR** (Art. 5: Integrity and Confidentiality).
    * **Non-Repudiation** makes logs admissible in court (Forensics).
* **💼 Business Impact:**
    * **Availability** = **SLA** (Service Level Agreements). Downtime = Money lost.
* **📊 Risk Assessment:**
    * Always map risks to CIA. *"This vulnerability affects **Integrity**, which is critical for our financial records."*



# 3. 😈 The DAD Triad (The Anti-CIA)
#TryHackMe #DAD #Attacks #Revision

## 1. The Concept
The DAD triad represents the failures or attacks against the CIA triad.

| CIA (Defense) 🛡️ | DAD (Attack) ⚔️ | Definition |
| :--- | :--- | :--- |
| **Confidentiality** | **Disclosure** | Data is accessed by unauthorized people (Leaks). |
| **Integrity** | **Alteration** | Data is modified or corrupted (Defacement). |
| **Availability** | **Destruction / Denial** | System is broken or unreachable (DDoS, Physical damage). |

## 2. Examples
* **Disclosure:** A hacker dumps the database of user passwords online.
* **Alteration:** A student hacks the university DB to change their grade from F to A.
* **Destruction/Denial:** An attacker cuts the fiber optic cable of the data center.

---

## 🌍 Vision GRC (Consultant Focus)
* **Incident Response:** When classifying an incident, we use DAD terms to describe the *impact*.
    * *"We have a confirmed **Disclosure** of PII (Personally Identifiable Information)."*
* **Business Continuity Plan (BCP):** Focuses primarily on preventing **Destruction/Denial** to ensure the business keeps running.


# 4. 🏛️ Security Models (The Architecture)
#TryHackMe #SecurityModels #BellLaPadula #Biba #Revision

## 1. Bell-LaPadula Model (The Military 🪖)
**Focus:** **CONFIDENTIALITY** (Keeping secrets).
* **Context:** Used in Government/Military.
* **The Rules:**
    1.  **No Read Up (Simple Property):** A lower level cannot read high-level secrets.
    2.  **No Write Down (Star * Property):** A high level cannot write to a lower level (to prevent accidental leaks).
* **Mnemonic:** "No Read Up, No Write Down".

## 2. Biba Model (The Scientist 🧪)
**Focus:** **INTEGRITY** (Keeping data pure).
* **Context:** Medical, Scientific, Software Development.
* **The Rules:** (Exact opposite of Bell-LaPadula)
    1.  **No Read Down (Simple Property):** Do not read from unreliable sources (don't contaminate your mind).
    2.  **No Write Up (Star * Property):** Unreliable people cannot change high-integrity data.
* **Mnemonic:** "No Read Down, No Write Up".

## 3. Clark-Wilson Model (The Bank 🏦)
**Focus:** **TRANSACTIONS**.
* **Concept:** Users cannot touch data directly. They must use a program/interface (Transformation Procedure).
* **Key Term:** **CDI** (Constrained Data Item) = The protected data (e.g., Bank Balance).

---

## 🌍 Vision GRC (Consultant Focus)
* **Access Control Policies:** When writing an ISP (Information Security Policy), you define these rules via **RBAC** (Role-Based Access Control).
* **Data Classification:** You cannot apply Bell-LaPadula if you haven't classified your data (Public, Internal, Confidential, Restricted). This is a requirement of **ISO 27001 (A.8.2)**.

# 5. 🧅 Defence-in-Depth (Multi-Level Security)
#TryHackMe #DefenceInDepth #Strategy #Revision

## 1. The Concept
Never rely on a single protection. Security must be layered like an onion.
* **Goal:** It is NOT to stop 100% of attacks (impossible).
* **Real Goal:** To **slow down** the attacker enough to detect them before they reach the data.

## 2. The Layers (The "Onion" Model)
If an attacker bypasses one layer, the next one should catch them.

1.  **Physical Controls:** Fences, Guards, CCTV, Locked Doors.
2.  **Technical Controls:** Firewall, Antivirus, Encryption, MFA.
3.  **Administrative Controls:** Policies, Awareness Training, Background Checks.

> **Example:**
> A hacker steals a password (User layer fails).
> -> **MFA** asks for a code (Technical layer blocks them).
> -> If MFA is bypassed, the **EDR** detects strange behavior (Monitoring layer blocks them).

---

## 🌍 Vision GRC (Consultant Focus)
* **Single Point of Failure (SPOF):** In an audit, if you see a critical asset protected by only *one* mechanism (e.g., just a password), it's a critical finding.
* **Cost vs Risk:** Adding layers costs money. You don't put an electric fence around the cafeteria menu. You put it around the Data Center.
* **ISO 27001:** This standard is built entirely on this principle (Annex A controls cover Physical, People, Tech, and Org).

# 6. 🏗️ ISO/IEC 19249 (Secure Architecture)
#TryHackMe #ISO19249 #Architecture #GRC

## 1. Architectural Principles (The Structure)
How we build the system physically or logically.
1.  **Domain Separation:** Grouping related components. Each entity has its own domain (e.g., Kernel run level vs User run level).
2.  **Layering:** Structuring into levels (like the OSI model). Allows forcing security checks at each layer.
3.  **Encapsulation:** Hiding internal details (OOP). You use an interface (API) instead of touching the data directly.
4.  **Redundancy:** Ensuring availability. Example: Dual power supplies or RAID disks. If one fails, the other takes over.
5.  **Virtualization:** Sharing hardware securely. It provides sandboxing (malware in a VM doesn't infect the host).

## 2. Design Principles (The Logic)
How we write the rules and code.
1.  **Least Privilege:** Give the minimum permissions needed (Need-to-know basis).
2.  **Attack Surface Minimisation:** Disable everything you don't need (ports, services, features). Less stuff = Less risks.
3.  **Centralized Parameter Validation:** Check all inputs in one place to avoid exploits like SQL Injection.
4.  **Centralized Security Services:** Don't reinvent the wheel. Use a central server for Authentication (SSO) instead of building login forms everywhere.
5.  **Error & Exception Handling:** When it crashes, fail safe. Don't leak info in error messages.

---

## 🌍 Vision GRC (Consultant Focus)
* **Security by Design:** L'ISO 19249 est la définition même du "Security by Design" exigé par le **GDPR (Art 25)**.
* **Hardening:** Le principe "Attack Surface Minimisation" est la base des procédures de **Hardening** (durcissement) des serveurs avant mise en production.

# 7. 🚫 Zero Trust vs. Trust but Verify
#TryHackMe #ZeroTrust #Strategy #GRC

## 1. Trust but Verify (Legacy Model 👴)
* **Philosophy:** "I trust you because you are inside the network/building, but I will log your actions just in case."
* **The Problem:** Once an attacker gets past the firewall (perimeter), they can move freely (Lateral Movement).
* **Implementation:** Firewalls, IDS/IPS, Logging.

## 2. Zero Trust (Modern Standard 🛡️)
* **Philosophy:** "Trust is a vulnerability." Treat every user and device as hostile/untrusted, even if they are the CEO or on the office Wi-Fi.
* **Motto:** **"Never trust, always verify."**
* **Implementation:**
    * **Identity First:** Authenticate & Authorize every single request.
    * **Microsegmentation:** Cutting the network into tiny zones (down to the single host). If one computer is infected, it cannot infect the neighbor.
* **Benefit:** If a breach occurs, the damage is contained (Blast Radius is minimized).

---

## 🌍 Vision GRC (Consultant Focus)
* **NIST SP 800-207:** C'est la bible du Zero Trust Architecture (ZTA).
* **De-perimeterization:** On ne protège plus le "réseau" (car le Cloud n'a pas de murs), on protège la **Donnée** et l'**Identité**.

# 8. ⚠️ Threat vs Vulnerability vs Risk
#TryHackMe #Vocabulary #RiskManagement #GRC

## 1. The Definitions (The Equation)
To understand Risk, you must distinguish its components.

* **🔓 Vulnerability (The Weakness):**
    * *Definition:* A flaw or weakness in the system.
    * *Example:* A server running Windows XP (outdated), a password written on a post-it, a glass door.
    * *Key:* It's internal to the system.

* **🥷 Threat (The Potential Danger):**
    * *Definition:* A potential danger associated with the vulnerability.
    * *Example:* A hacker, a malware, an earthquake, a thief with a hammer.
    * *Key:* It's external (usually).

* **📉 Risk (The Probability & Impact):**
    * *Definition:* The likelihood of a threat exploiting a vulnerability + the impact on the business.
    * *Formula:* `Risk = Likelihood x Impact` (or `Risk = Threat x Vulnerability`).

> **💡 The Showroom Analogy:**
> * **Vulnerability:** The door is made of standard glass (it breaks easily).
> * **Threat:** Someone might break it (burglar, storm).
> * **Risk:** The probability that it breaks AND the cost of replacing the stolen items.

---

## 🌍 Vision GRC (Consultant Focus)
* **Risk Assessment:** We never "fix" threats (we can't stop hackers from existing). We fix **Vulnerabilities** to lower the **Risk**.
* **Zero Risk:** Does not exist. There is always **Residual Risk**.


# 9. ☁️ Conclusion & Shared Responsibility Model
#TryHackMe #CloudSecurity #SharedResponsibility #Revision

## 1. Summary of Achievements 🏆
We have mastered the core language of Security:
* **The Triads:** CIA (Defense) vs DAD (Attack).
* **The Models:** Bell-LaPadula (Confidentiality), Biba (Integrity), ISO/IEC 19249.
* **The Strategy:** Defence-in-Depth, Trust but Verify vs Zero Trust.
* **The Vocabulary:** Vulnerability, Threat, Risk.

## 2. The Shared Responsibility Model (Cloud Context)
With the increased reliance on cloud services, security requires a joint effort.

* **Definition:** A cloud security framework to ensure that each party (Provider & User) is aware of its responsibility.
* **The Logic:** Security depends on the access level the user has.

### Service Models & Responsibilities:
* **IaaS (Infrastructure as a Service):**
    * *User Status:* Has **complete control (and responsibility)** over the Operating System (OS).
    * *Implication:* You must patch and secure the OS yourself.
* **SaaS (Software as a Service):**
    * *User Status:* Has **no direct access** to the underlying Operating System.
    * *Implication:* The Provider secures the OS/App. The User secures their data and access.

> **Key Takeaway:** Achieving security in the cloud necessitates both the cloud service provider and the user to do their parts.