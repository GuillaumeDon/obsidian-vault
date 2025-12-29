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