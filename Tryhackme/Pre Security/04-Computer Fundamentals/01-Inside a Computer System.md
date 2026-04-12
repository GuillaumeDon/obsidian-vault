### Task 1: Introduction

This task sets the stage using the **Castle Analogy**: To defend a castle, you must know its layout—where the treasure is kept, where the entrances are, and how the inhabitants move. In cybersecurity, the "castle" is the computer system. Before implementing security controls, a practitioner must understand the hardware components (building blocks) and how they interact to provide services.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 5.9 (Inventory of information and other associated assets) & Annex A 7.4 (Physical security monitoring).
    
- **Implementation:** A Lead Implementer knows that an **Information Security Management System (ISMS)** begins with an accurate asset inventory. You cannot apply security policies to hardware you don't know exists. Understanding "Inside the System" is the prerequisite for defining the **physical scope** of the ISMS.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 1.0 General Security Concepts (1.2 Explain the importance of security concepts in an organization).
    
- **Key Terminology:**
    
    - **Hardware:** The physical components (tangible assets) of the system.
        
    - **Security Posture:** The overall security status of the "castle" based on the components in place.
        
    - **Attack Surface:** The sum of all physical and logical points where an unauthorized user can try to enter or extract data.
        

#### 🏷️ Keywords & Links

#TryHackMe #HardwareBasics #AssetManagement #ISO27001 #SecurityPlus701 #[[PhysicalSecurity]] #[[CastleAnalogy]]

### Task 2: Inside a Computer System

This task breaks down the physical architecture of a computer. Every component has a specific role in processing, storing, or powering the system:

- **Motherboard (Skeleton & Nerves):** The main circuit board that connects all components.
    
- **CPU (The Brain):** Executes instructions and processes data.
    
- **RAM (Short-term Memory):** Volatile storage for quick data access.
    
- **HDD/SSD (Long-term Memory):** Non-volatile storage for permanent data.
    
- **GPU (Visual Cortex):** Handles complex mathematical calculations for rendering images.
    
- **PSU (Heart & Lungs):** Provides power to the entire system.
    

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 8.1 (User endpoint devices) & Annex A 8.22 (Segregation of networks).
    
- **Implementation:** An LI must consider the **Physical Destruction of Data (Annex A 7.14)**. When a system is decommissioned, the "Long-term memory" (HDD/SSD) must be wiped or shredded. Understanding the hardware allows you to write specific policies for **Removable Media (A.8.10)** and device hardening.
    
- **Redundancy:** The PSU and Storage relate to **Business Continuity (Annex A 5.30)**—ensuring power and data availability through hardware redundancy.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 3.0 Architecture and Design (3.1 Explain the importance of hardware assurance).
    
- **Key Terminology:**
    
    - **Volatile vs. Non-volatile:** RAM is volatile (clears when power is lost); SSD/HDD is non-volatile (persistent).
        
    - **TPM (Trusted Platform Module):** A physical chip on the motherboard used for hardware-level encryption (essential for 701).
        
    - **Supply Chain Security:** Ensuring the "Brain" (CPU) or "Skeleton" (Motherboard) hasn't been tampered with before arrival.
        

#### 🏷️ Keywords & Links

#TryHackMe #HardwareSecurity #CPU #RAM #StorageSecurity #ISO27001 #SecurityPlus701 #[[HardwareHardening]] #[[DataDestruction]]