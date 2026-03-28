### Task 1: What is Offensive Security?

Offensive Security is the proactive approach to cybersecurity. Instead of just waiting to defend against an attack, professionals simulate the methods, tools, and mindsets of real-world hackers. The goal is to identify and exploit vulnerabilities (software bugs or configuration errors) in a controlled environment to find weaknesses before a malicious actor does. It follows the philosophy: _"To outsmart a hacker, you need to think like one."_

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.8 - Management of technical vulnerabilities.** This control requires organizations to obtain information about technical vulnerabilities and take appropriate measures.
    
- **Implementation:** As a Lead Implementer, you wouldn't necessarily perform the hack yourself, but you would establish the **Policy for Vulnerability Management**. You would define how often "Penetration Testing" (offensive security) occurs and ensure the findings are remediated (fixed) to maintain the **ISMS** (Information Security Management System) integrity.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 2.0: Threats, Vulnerabilities, and Mitigations.** Specifically, understanding the difference between "Ethical Hacking" (Offensive) and "Malicious Attacks."
    
- **Key Terminology:** * **Penetration Testing:** A simulated cyberattack against your computer system to check for exploitable vulnerabilities.
    
    - **Ethical Hacker:** A security professional who uses their skills legally to improve security.
        
    - **Vulnerability:** A weakness in an asset or control that can be exploited by a threat.
        

#### 🏷️ Keywords & Links

#TryHackMe #OffensiveSecurity #ISO27001 #SecurityPlus701 #GRC #[[VulnerabilityManagement]] #[[EthicalHacking]]


### Task 2: Hacking your first machine

In this practical exercise, we simulate a **web application attack**. The process involves three main phases:

1. **Reconnaissance:** Finding hidden files/folders using a tool called `Gobuster`.
    
2. **Exploitation:** Navigating to a hidden administrative page found during the scan.
    
3. **Post-Exploitation:** Manipulating the application (in this case, a bank transfer) to achieve an unauthorized goal.
    

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.5 - Secure configuration.** This task demonstrates what happens when a web server is not securely configured (e.g., leaving sensitive "hidden" pages accessible).
    
- **Implementation:** A Lead Implementer ensures that **Vulnerability Scanning** and **Penetration Testing** results are integrated into the Risk Treatment Plan. You would audit the "Change Management" process to ensure developers don't leave administrative backdoors or hidden pages in production environments.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0: Security Architecture.** Understanding how insecure web application design can lead to unauthorized access.
    
- **Key Terminology:**
    
    - **Directory Brute-Forcing:** Using a tool (like `Gobuster`) to guess hidden directory names on a web server.
        
    - **Broken Access Control:** A vulnerability where a user can access resources or perform actions outside of their intended permissions.
        
    - **Command Line Interface (CLI):** The text-based interface used to run the hacking tools in this lab.
        

#### 🏷️ Keywords & Links

#TryHackMe #WebSecurity #Gobuster #ISO27001 #SecurityPlus701 #[[VulnerabilityScanning]] #[[AccessControl]]

---

### ⌨️ Task 2 Mini-Cheat Sheet

|**Tool / Action**|**Purpose**|
|---|---|
|`Gobuster`|Brute-forcing URLs and directories in websites.|
|`Hidden Directory`|A folder on a web server not linked to the main page (e.g., `/bank-transfer`).|


### Task 3: Careers in Cyber Security

This section outlines the professional roles within the offensive security landscape. It emphasizes that anyone, regardless of their previous background, can enter the field by building a habit of hands-on practice. The focus is on the distinction between testing (Penetration Tester), simulating a full-scale adversary (Red Teamer), and building defenses (Security Engineer).

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 6.3 - Information security awareness, education, and training.**
    
- **Implementation:** A Lead Implementer must ensure that personnel have the necessary skills for their roles. This task highlights the specialized roles that an organization might hire or contract to fulfill its **security monitoring and testing requirements** defined in the ISMS.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 1.0: General Security Concepts.** Understanding different security roles and responsibilities within an organization.
    
- **Key Terminology:**
    
    - **Penetration Tester:** Focuses on finding specific vulnerabilities in a scoped environment.
        
    - **Red Teamer:** Uses a goal-oriented approach to test an organization's detection and response capabilities (often without the defensive team's knowledge).
        
    - **Security Engineer:** Focuses on the design and implementation of security controls to protect assets.
        

#### 🏷️ Keywords & Links

#TryHackMe #CareerPath #RedTeaming #ISO27001 #SecurityPlus701 #[[SecurityRoles]] #[[PenTesting]]

---

### 📑 Executive Room Summary

- **Core Concepts:** This room provided an introduction to **Offensive Security** through a practical web application attack. It covered the basic methodology of reconnaissance using `gobuster`, exploitation of hidden directories, and the different professional roles (Penetration Tester, Red Teamer, Security Engineer) that perform these tasks.
    
- **GRC Strategic Impact:** From an ISMS perspective, offensive security is a critical part of **Continuous Improvement** and **Vulnerability Management**. It provides objective evidence of the effectiveness of existing technical controls.
    
- **Study Focus:** For ISO 27001, focus on **Annex A 8.8 (Technical Vulnerabilities)**. For Security+, focus on the definitions of **Penetration Testing** and the specific duties of **Security Roles**.
    

### ⌨️ Command Cheat Sheet

| **Command**                           | **Description / Purpose**                                    |
| ------------------------------------- | ------------------------------------------------------------ |
| `gobuster dir -u [URL] -w [wordlist]` | Scans a website for hidden directories and files.            |
| `http://[IP]/[hidden-page]`           | Accessing non-linked administrative or sensitive interfaces. |
