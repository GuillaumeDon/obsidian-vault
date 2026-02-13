
## tags: [ #SY0-701, #SecurityPlus, #Fundamentals, #CIA, #ZeroTrust ] date: 2026-02-10 topic: Fundamentals of Cybersecurity

# 🛡️ Fundamentals of Cybersecurity

## 1. Executive Summary

This section establishes the bedrock of cybersecurity, exploring the inherent tension between **Security and Convenience**. It defines key frameworks used to secure data and systems, specifically the **CIA Triad** (Confidentiality, Integrity, Availability), the **AAA framework** (Authentication, Authorization, Accounting), and the modern **Zero Trust** model ("Never trust, always verify").

## 2. Core Concepts

### 🔹 Security vs. Convenience

- **Definition:** The operational balance where increasing security often decreases usability (convenience), and vice versa.
    
- **Context/Usage:** Security professionals must find the "sweet spot" where systems are secure enough to thwart attackers but usable enough that employees do not bypass controls.
    
- **Example:** A router comes with a complex 20-character password (High Security, Low Convenience). Users often change it to "password123" (Low Security, High Convenience), making it vulnerable.
    

### 🔹 Info Security vs. Info System Security

- **Information Security:** Protecting the **data** itself (from unauthorized access, modification, destruction).
    
- **Information _System_ Security:** Protecting the **systems/devices** (hardware, servers, smartphones) that hold and process the data.
    

### 🔹 The CIA Triad (The Pillars of Security)

- **Confidentiality:** Ensures information is accessible _only_ to authorized entities.
    
    - _Key Tech:_ Encryption, Access Controls.
        
- **Integrity:** Ensures data remains accurate and unaltered.
    
    - _Key Tech:_ Hashing, Checksums, Digital Signatures.
        
- **Availability:** Ensures resources are accessible when needed.
    
    - _Key Tech:_ Redundancy, Backups, High Availability clusters.
        

### 🔹 Non-Repudiation

- **Definition:** A guarantee that a sender cannot deny having taken a specific action or sent a message.
    
- **Context/Usage:** Critical for legal and banking transactions.
    
- **Example:** Using a **Digital Signature** on an email proves who sent it; the sender cannot later claim "It wasn't me."
    

### 🔹 The AAA Framework

- **Authentication (AuthN):** Verifying the **identity** of a user (Who are you?).
    
    - _Ex:_ Entering a Username and Password.
        
- **Authorization (AuthZ):** Determining **permissions** (What can you do?).
    
    - _Ex:_ You are allowed to _read_ a file but not _delete_ it.
        
- **Accounting:** Tracking and recording **activity** (What did you do?).
    
    - _Ex:_ Logs showing User X logged in at 9:00 AM and accessed File Y.
        

### 🔹 Zero Trust Model

- **Definition:** A security model based on the principle "Never trust, always verify." No user or system (internal or external) is trusted by default.
    
- **Architecture:**
    
    - **Control Plane:** Managing access. Includes _Adaptive Identity, Threat Scope Reduction, Policy-Driven Access, Secured Zones_.
        
    - **Data Plane:** The actual connection. Includes _Subject/System, Policy Engine, Policy Administrator, Policy Enforcement Points_.
        

## 3. 🚨 Exam Tips & Pitfalls

- **AuthN vs. AuthZ:** Do not confuse **Authentication** (checking ID) with **Authorization** (checking permissions). You must be authenticated _before_ you are authorized.
    
- **Accounting is Passive:** Accounting doesn't stop an attack; it records it for auditing/forensics.
    
- **CIA Keywords:**
    
    - Confidentiality $\rightarrow$ Encryption / Permissions.
        
    - Integrity $\rightarrow$ Hashing / SHA-256 / Checksums.
        
    - Availability $\rightarrow$ Redundancy / RAID / Load Balancing.
        

## 4. 🔠 Acronyms List

- **CIA:** Confidentiality, Integrity, Availability
    
- **AAA:** Authentication, Authorization, Accounting
    
- **ISP:** Internet Service Provider
    

## 5. 🧠 PBQ Scenario (Concept Application)

**Scenario:** A disgruntled employee deletes critical project files before quitting. The IT department restores the files from a backup created last night, but they cannot prove exactly _when_ the employee deleted the files because the server logs were disabled to save space.

**Question:** Which principles of the CIA Triad and AAA framework were compromised or failed?

<details>

<summary>Click for Solution</summary>

1. **Integrity (Failed):** The files were deleted (unauthorized modification/destruction).
    
2. **Availability (Restored):** Availability was initially lost but restored via backup (successful resilience).
    
3. **Accounting (Failed):** Because logs were disabled, there is no record of the user's activity. The company lacks _Non-Repudiation_ evidence.
    
    </details>


## tags: [ #SY0-701, #SecurityPlus, #RiskManagement, #Threats, #Vulnerabilities ] date: 2026-02-10 topic: Threats, Vulnerabilities, and Risk

# 🛡️ Threats and Vulnerabilities

## 1. Executive Summary

This lesson defines the fundamental components of risk management. It distinguishes between **Threats** (external/uncontrollable events) and **Vulnerabilities** (internal/controllable weaknesses). The core principle is that **Risk** exists only where a threat intersects with a vulnerability. Security professionals primarily manage risk by controlling vulnerabilities since threats are often beyond their control.

![Image de cybersecurity risk assessment matrix](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcS1QpJmgqHR22iZMgxSz2KSS7-Kxoa6lLLqQJ47wL7sSriHN3MNhn8RpT7V-gI6p4Du7RUXlVASsRgGXk-3ZAT0W-FHGl4qKOEL3MOcC03rMnTTDDs)

Shutterstock

Explorer

## 2. Core Concepts

### 🔹 Threat

- **Definition:** Any potential occurrence (malicious or accidental) that could cause harm, loss, damage, or compromise to systems.
    
- **Context/Usage:** Threats are generally **external** and **uncontrollable**. You cannot stop an earthquake or a hacker from _trying_, but you can prepare for it.
    
- **Examples:** Natural disasters, cyber attacks, data breaches, impatient drivers (in the commute analogy).
    

### 🔹 Vulnerability

- **Definition:** A weakness in system design, implementation, software, or process.
    
- **Context/Usage:** Vulnerabilities are generally **internal** and **controllable**. It is the security professional's job to identify and fix these.
    
- **Examples:**
    
    - Missing security patches.
        
    - Misconfigured firewalls.
        
    - Lack of physical security.
        
    - "Forgot to get gas" (in the commute analogy).
        

### 🔹 The Risk Equation

- **Definition:** Risk is the intersection of a Threat and a Vulnerability.
    
    - $$Risk = Threat \times Vulnerability$$
        
- **Key Principle:**
    
    - If there is a Threat but **no** Vulnerability $\rightarrow$ No Risk.
        
    - If there is a Vulnerability but **no** Threat $\rightarrow$ No Risk.
        
- **Mitigation:** Actions taken to reduce the likelihood or impact of a risk (e.g., waking up an hour early acts as a buffer/mitigation for traffic).
    

## 3. 🚨 Exam Tips & Pitfalls

- **Control:** Remember that you generally **cannot control threats**, but you **can control vulnerabilities**.
    
- **Scenario Analysis:** In exam questions, identify if the problem is a _Flaw_ (Vulnerability) or an _Event_ (Threat).
    
    - "Server is unpatched" = Vulnerability.
        
    - "Hacker launches DDoS" = Threat.
        
    - "Server crashes due to DDoS because it was unpatched" = Risk Realized.
        

## 4. 🔠 Acronyms List

- _None specifically introduced in this lesson, but standard terms apply._
    

## 5. 🧠 PBQ Scenario (Risk Identification)

**Scenario:** You are auditing a company's security posture. You find the following:

1. The data center is located in a flood zone.
    
2. The servers are placed on the ground floor.
    
3. The company has no offsite backups.
    

**Task:** Map the components to Risk Terminology.

<details>

<summary>Click for Solution</summary>

- **Threat:** Heavy Rain / Flood (External, Uncontrollable).
    
- **Vulnerability:**
    
    1. Servers on ground floor (Internal weakness).
        
    2. Lack of offsite backups (Internal weakness).
        
- **Risk:** Loss of data and hardware destruction due to flooding.
    
- **Mitigation:** Move servers to a higher floor (Fixing Vulnerability 1) or implement cloud backups (Fixing Vulnerability 2).
    
    </details>