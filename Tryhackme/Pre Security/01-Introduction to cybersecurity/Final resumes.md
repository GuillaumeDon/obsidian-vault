
# 🚩 Room: Offensive Security Intro

**Status:** #RoomCompleted

**Date:** 2026-03-28

**Path:** Pre-Security > Introduction to Cyber Security

### 📑 Executive Room Summary

- **Core Concepts:** This room introduced the **Offensive Security** mindset: "thinking like a hacker to outsmart one." It demonstrated a basic web attack lifecycle: **Reconnaissance** (finding hidden areas), **Exploitation** (accessing unauthorized pages), and **Post-Exploitation** (manipulating data/transfers).
    
- **GRC Strategic Impact:** Within an **Information Security Management System (ISMS)**, this room illustrates the practical application of **Technical Vulnerability Management**. It proves that "Security by Obscurity" (hiding a page) is not a valid control; formal access controls and secure configurations are required.
    
- **Study Focus:** * **ISO 27001:** Focus on **Annex A 5.37** (Management of technical vulnerabilities).
    
    - **CompTIA SY0-701:** Focus on the definition of **Penetration Testing** vs. **Vulnerability Scanning**.
        

---

### 🛡️ ISO 27001 LI Alignment

- **Control Annex A 8.8 / 5.37:** This room demonstrates the need for regular **Penetration Testing**. As a Lead Implementer, you would use the results of these "hacks" to update the **Risk Treatment Plan**.
    
- **Control Annex A 8.5:** Secure configuration. The lab showed that a default or "hidden" directory is a configuration weakness that must be hardened.
    

### 🔐 CompTIA Security+ 701 Focus

- **Domain 2.0 (Vulnerabilities):** Identifying that "broken access control" allows a user to perform actions they shouldn't (like the bank transfer).
    
- **Domain 1.0 (Security Roles):** * **Penetration Tester:** Scoped, authorized testing.
    
    - **Red Teamer:** Full adversarial simulation.
        

---

### ⌨️ Command Cheat Sheet

|**Command**|**Description / Purpose**|
|---|---|
|`gobuster dir -u [URL] -w [wordlist]`|Tool used to find hidden directories (Brute-forcing).|
|`dir`|Common flag for "directory" mode in security tools.|
|`/admin` or `/.env`|Common sensitive hidden paths discovered during recon.|

### 🏷️ Final Tags

#RoomCompleted #Summary #CheatSheet #FullReview #OffensiveSecurity #ISO27001 #SecurityPlus701 #GRC #[[EthicalHacking]] #[[VulnerabilityManagement]]