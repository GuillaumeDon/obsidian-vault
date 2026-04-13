Excellent! Moving from "what is inside a computer" to **Computer Types** is a strategic leap. In GRC, this expands our view from a single machine to the entire **ecosystem of assets** an organization must manage.

---

### Task 1: Introduction

This task introduces the concept that computers are no longer just desktop towers or laptops. Using the example of a **Smart Fridge**, it highlights that computing power is now embedded in everyday objects. For a security professional, this means the **Attack Surface** has expanded to include "hidden" computers that we often forget to secure.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 5.9 (Inventory of information and other associated assets) & Annex A 8.1 (User endpoint devices).
    
- **Implementation:** As a Lead Implementer, the biggest challenge is **Shadow IT**. If a smart device (IoT) is connected to the corporate WiFi without being in the asset inventory, it violates the ISMS policy. Every "hidden" computer is an entry point that must be documented and governed.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 2.0 Threats, Vulnerabilities, and Mitigations (2.1 Compare and contrast common threat actors and motivations).
    
- **Key Terminology:**
    
    - **IoT (Internet of Things):** Physical objects embedded with sensors and software for the purpose of connecting and exchanging data.
        
    - **Embedded Systems:** A computer system with a dedicated function within a larger mechanical or electrical system.
        
    - **Attack Surface:** The total number of points (devices) where an attacker can attempt to enter an environment.
        

#### 🏷️ Keywords & Links

#TryHackMe #ComputerTypes #IoT #AssetInventory #ISO27001 #SecurityPlus701 #[[ShadowIT]] #[[AttackSurface]]

Sophia's first month at Nova Labs introduces a critical concept for GRC: **Asset Categorization**. Not all "boxes" are created equal, and their security requirements vary based on their role in the organization.

---

### Task 2: Sophia's Summer of Hidden Computers - Month 1

This task distinguishes between computers we sit in front of versus those that power the background. The main takeaway is that **form follows function**:

|**Computer Type**|**Key Characteristic**|**Main Purpose**|
|---|---|---|
|**Laptop**|Portable & Battery-powered|On-the-go productivity.|
|**Desktop**|Fixed location & Better cooling|Sustained performance and consistency.|
|**Workstation**|Specialized/High-end components|Precision, reliability, and complex computations.|
|**Server**|No screen/keyboard; continuous run|Providing services to many users over a network.|

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 8.1 (User endpoint devices) vs. Annex A 8.20 (Network security).
    
- **Implementation:** A Lead Implementer treats a **Server** differently than a **Laptop**.
    
    - **Laptops:** Require **Annex A 7.10 (Storage media)** and **Annex A 8.1 (Mobile device policy)**—focusing on encryption and physical theft risk.
        
    - **Servers:** Require **Annex A 7.4 (Physical security monitoring)** and **Annex A 8.24 (Use of privileged utility programs)**—focusing on uptime and access control since they host organizational data.
        

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 3.0 Architecture and Design (3.1 Explain the importance of hardware assurance).
    
- **Key Terminology:**
    
    - **Headless System:** A computer (usually a server) that operates without a monitor, keyboard, or mouse.
        
    - **Availability:** The "A" in the CIA Triad. Servers and Workstations are prioritized for availability to ensure business continuity.
        
    - **Form Factor:** The physical size and shape of the hardware (Laptop vs. Rack-mounted Server).
        

#### 🏷️ Keywords & Links

#TryHackMe #AssetClassification #Servers #Workstations #ISO27001 #SecurityPlus701 #[[EndpointSecurity]] #[[Availability]]

### Task 3: Sophia's Summer of Hidden Computers - Month 2

This task categorizes devices based on their integration into daily life and their connectivity:

|**Type**|**Definition**|**Key Security Difference**|
|---|---|---|
|**Smartphone**|High-performance, pocket-sized, connectivity-focused.|Constant data transmission/GPS tracking.|
|**Tablet**|Touch-first, larger screen than phones.|Often used for "kiosk" modes or light work.|
|**IoT Device**|Single-purpose, network-connected (e.g., Smart Doorbell).|**Connected:** Provides a remote entry point.|
|**Embedded Computer**|Built into another device (e.g., Coffee maker chip).|**Internal:** Often performs tasks without a network.|

**Crucial Distinction:** **IoT** vs. **Embedded**.

- **IoT** devices are designed to talk to the internet/cloud.
    
- **Embedded** systems might be "dumb" (not connected) but still control critical physical functions.
    

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 5.14 (Information security in supplier relationships) & Annex A 8.33 (Information system testing and acceptance).
    
- **Implementation:** * **IoT Security:** An LI must evaluate the **Security-by-Design** of these devices. Many IoT devices have "hardcoded passwords" that cannot be changed, violating **Annex A 8.5 (Secure authentication)**.
    
    - **Embedded Systems:** In an industrial or office setting (like automatic doors), these are part of **Annex A 7.12 (Physical security of facilities)**. If the embedded chip in the door is hacked, the physical "Castle" is breached.
        

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 2.0 Threats, Vulnerabilities, and Mitigations (2.4 Explain the importance of vulnerability management).
    
- **Key Terminology:**
    
    - **Smart Devices / Wearables:** Personal devices (Fitness trackers) that often lead to **BYOD (Bring Your Own Device)** policy risks.
        
    - **Shadow IoT:** Unauthorized IoT devices on a network (the biggest nightmare for a SOC).
        
    - **Firmware:** The permanent software programmed into a read-only memory of an embedded system.
        

#### 🏷️ Keywords & Links

#TryHackMe #IoT #EmbeddedSystems #MobileSecurity #ISO27001 #SecurityPlus701 #[[BYOD]] #[[FirmwareSecurity]]

### Task 4: Why Computers Come in Different Flavors

This task explains that there is no "perfect" computer; there is only the **right tool for the job**. Every design choice involves a compromise:

- **Mobility vs. Power:** Laptops sacrifice sustained performance (due to heat and battery) for portability.
    
- **Reliability vs. Cost:** Servers and critical infrastructure use **Redundancy** (extra power supplies, multiple disks) to avoid failure, which increases cost significantly.
    
- **Purpose-Driven Design:** A smartphone is optimized for touch and connectivity, while an IoT sensor is built to be "quiet" and efficient, demanding little attention but serving a specific data point.
    

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 5.30 (ICT readiness for business continuity) & Annex A 8.25 (Secure development life cycle).
    
- **Implementation:** An LI must ensure that the "flavor" of computer chosen matches the **Business Impact Analysis (BIA)**.
    
    - If a process is "Mission Critical," the LI mandates hardware with **High Availability (HA)** features.
        
    - If mobility is required, the LI mandates **Annex A 8.1 (User endpoint devices)** controls like Remote Wipe and Full Disk Encryption (FDE).
        

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 3.0 Architecture and Design (3.1 Explain the importance of hardware assurance & 3.2 secure network designs).
    
- **Key Terminology:**
    
    - **Redundancy:** The inclusion of extra components that are not strictly necessary to functioning, in case of failure (e.g., dual PSUs).
        
    - **High Availability (HA):** Systems that are durable and likely to operate continuously without failure for a long time.
        
    - **MTBF (Mean Time Between Failures):** A key metric for assessing hardware reliability.
        

#### 🏷️ Keywords & Links

#TryHackMe #ComputerArchitecture #Redundancy #HighAvailability #ISO27001 #SecurityPlus701 #[[RiskManagement]] #[[BusinessContinuity]]