# Study Notes — Fundamentals of Security

**Exam objectives covered:** 1.1 (Security Controls) & 1.2 (Fundamental Security Concepts)

---

## The Security vs. Usability Trade-Off

This is a core principle you'll encounter throughout the entire course: there is always a tension between security and convenience. The more secure you make a system, the harder it becomes for users to use. The more convenient, the more vulnerable. Users will actively try to bypass controls that feel too restrictive (e.g., replacing a complex Wi-Fi password like `3%1WT&!92#SXH` with `cupcake#1`). Your job as a security professional is to find the sweet spot. In 2022, the average cost of a data breach for a major company was **$4.35 million** — often because organizations made the wrong trade-offs.

---

## Two Key Definitions

|Term|Protects…|Example|
|---|---|---|
|**Information Security**|The _data itself_ — from unauthorized access, modification, disruption, disclosure, destruction|Encrypting a confidential database|
|**Information Systems Security**|The _systems that hold the data_ — computers, servers, network devices, smartphones|Hardening a web server's configuration|

---

## The CIA Triad

The three foundational pillars of security:

**Confidentiality** — Information is accessible only to authorized people. Key methods: encryption, access controls, data masking, physical security measures, training & awareness.

**Integrity** — Data remains accurate and unaltered unless intentionally modified by an authorized user. Key methods: hashing, digital signatures, checksums, access controls, regular audits.

**Availability** — Information and systems are accessible and functional when needed. Key methods: redundancy (server, data, network, power), load balancing, failover configurations, UPS and backup generators.

> **Exam shortcut:** Confidentiality → Encryption | Integrity → Hashing | Availability → Redundancy

---

## CIANA Pentagon

The CIA Triad has been expanded with two additions, forming five pillars:

**Non-Repudiation** — Guarantees that an action or event cannot be denied by the parties involved. Achieved through **digital signatures** (message is hashed, then the hash is encrypted with the sender's private key using asymmetric encryption). Important for confirming authenticity, ensuring integrity of communications, and providing accountability.

**Authentication** — Verifying that someone is who they claim to be. Five authentication factors:

|Factor|Category|Example|
|---|---|---|
|Something you **know**|Knowledge|Password, PIN|
|Something you **have**|Possession|Smart card, token|
|Something you **are**|Inherence|Fingerprint, retina scan|
|Something you **do**|Action|Typing pattern, gesture|
|Somewhere you **are**|Location|GPS-based access|

Using two or more of these factors = **Multi-Factor Authentication (MFA)**.

---

## The AAAs of Security

**Authentication** → Verifying identity (e.g., username + password checked against stored credentials).

**Authorization** → What an authenticated user is _allowed_ to do (e.g., read-only vs. read-write permissions on a database).

**Accounting** → Tracking and logging user activities for auditing, monitoring unusual behavior, and maintaining regulatory compliance. Creates an **audit trail** — a chronological record that can trace changes or unauthorized access back to a specific source and time.

---

## Security Controls

**Categories** (how the control is implemented):

|Category|Description|
|---|---|
|**Technical**|Implemented through technology (firewalls, encryption, IDS)|
|**Managerial**|Policies, procedures, risk assessments|
|**Operational**|Day-to-day procedures carried out by people (security guards, training)|
|**Physical**|Tangible barriers (locks, fences, cameras)|

**Types** (what the control does):

|Type|Purpose|
|---|---|
|**Preventative**|Stop an incident before it happens|
|**Deterrent**|Discourage a threat actor from acting|
|**Detective**|Identify that an incident has occurred|
|**Corrective**|Fix/restore after an incident|
|**Compensating**|Alternative control when the primary one isn't feasible|
|**Directive**|Guide behavior through policies or instructions|

---

## Zero Trust Model

Operates on the principle: **never trust, always verify** — no one inside or outside the organization is trusted by default.

**Control Plane** (the decision-making layer): adaptive identity, threat scope reduction, policy-driven access control, secured zones.

**Data Plane** (the execution layer): subject/system, policy engine, policy administrator, policy enforcement points.

---

## Threats & Vulnerabilities (preview from Study Guide)

**Threat** = anything that could cause harm (natural disasters, cyber-attacks, data breaches, disclosure of confidential info).

**Vulnerability** = any weakness in design or implementation (software bugs, misconfigurations, missing patches, lack of physical security).

**Risk exists where threats and vulnerabilities intersect.** No matching vulnerability for a threat = no risk. No threat targeting a vulnerability = no risk. **Risk management** = minimizing the likelihood of a negative outcome.