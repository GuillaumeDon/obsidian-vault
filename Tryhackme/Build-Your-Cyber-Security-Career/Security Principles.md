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