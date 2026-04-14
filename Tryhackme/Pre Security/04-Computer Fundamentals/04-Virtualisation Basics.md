### Task 1: Introduction to Virtualisation

This task introduces virtualization as the solution to hardware inefficiency and high costs. Instead of a 1:1 ratio between physical servers and applications, virtualization allows one physical machine to host multiple isolated "virtual" systems. This is the bedrock of modern cloud computing and scalable IT infrastructure.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.31 - Separation of development, test and production environments**.
    
- **Implementation:** As a Lead Implementer, you use virtualization to achieve **logical separation**. Instead of buying three physical servers, you govern the creation of virtual instances to ensure that the "Production" environment is logically isolated from "Development," reducing the risk of unauthorized changes or data leaks.
    
- **Governance Note:** Virtualization also touches on **Annex A 8.1 - User endpoint devices** and **Annex A 5.30 - ICT readiness for business continuity**.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0 Architecture and Design** (3.2 - Summarize the significance of virtualization and cloud computing).
    
- **Key Terminology:**
    
    - **Virtualization:** The process of creating a software-based (virtual) representation of something, such as virtual applications, servers, storage, and networks.
        
    - **Resource Pooling:** Combining physical resources to serve multiple virtualized entities.
        
    - **Scalability:** The ability to increase or decrease resources based on demand.
        

#### 🏷️ Keywords & Links

#TryHackMe #Virtualization #CloudSecurity #ISO27001 #SecurityPlus701 #[[EnvironmentIsolation]] #[[ResourceEfficiency]]

### Task 2: Virtualization Overview

This task contrasts the traditional "One Server, One Application" model with modern virtualization. It highlights the inefficiencies of physical hardware (high costs, low utilization, slow deployment) and introduces the **Hypervisor**—the critical software layer that enables multiple Virtual Machines (VMs) to share physical resources safely. The task uses an apartment building analogy: the building is the hardware, the apartments are the VMs, and the building manager is the hypervisor.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.1 - User endpoint devices** & **Annex A 8.13 - Information backup**.
    
- **Implementation:** A Lead Implementer views virtualization as a tool for **Asset Management**. By consolidating servers, you reduce the physical footprint (Annex A 7.1 - Physical security perimeters) but increase the criticality of the host machine. You must govern the **Host-to-Guest isolation** to ensure that a compromise of one VM does not lead to a "breakout" affecting others.
    
- **Governance Note:** Virtualization simplifies **Business Continuity (ISO 22301)** because VMs can be backed up as single files and restored on different hardware quickly.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0 Architecture and Design** (3.5 - Explain the security implications of different infrastructure models).
    
- **Key Terminology:**
    
    - **Hypervisor:** The software that creates and runs virtual machines.
        
    - **VM (Virtual Machine):** A software-defined computer that runs its own Operating System (OS).
        
    - **Host Machine:** The physical hardware providing the resources (CPU, RAM, Storage).
        
    - **Guest Machine:** The virtual instance running on the host.
        

#### 🏷️ Keywords & Links

#TryHackMe #Hypervisor #Virtualization #ISO27001 #SecurityPlus701 #[[ResourceOptimization]] #[[VMIsolation]]

### Task 3: Virtualisation Components

This task breaks down the technical specifics of **Hypervisors** (Type 1 vs. Type 2), **Virtual Machines (VMs)**, and **Containers**. It establishes the hierarchy of virtualization: Type 1 hypervisors run on bare metal (enterprise), while Type 2 run on an existing OS (home/labs). It also introduces **Containers** as a lighter alternative to VMs, sharing the host's kernel rather than simulating an entire hardware set.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.22 - Segregation in networks** & **Annex A 8.32 - Change management**.
    
- **Implementation:** An LI must distinguish between VM isolation and Container isolation. While VMs provide stronger isolation (better for **Annex A 8.31** compliance), containers require stricter governance over the **shared kernel** to prevent "container escape" attacks.
    
- **Governance Note:** Type 1 Hypervisors are preferred for **Production Environments** due to reduced attack surface and higher performance/reliability.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0 Architecture and Design** (3.2 - Summarize the significance of virtualization and cloud computing).
    
- **Key Terminology:**
    
    - **Type 1 Hypervisor (Bare Metal):** Runs directly on hardware (e.g., VMware ESXi, Microsoft Hyper-V).
        
    - **Type 2 Hypervisor (Hosted):** Runs on top of an OS (e.g., Oracle VirtualBox, VMware Workstation).
        
    - **Containers:** Lightweight, isolated environments that share the host OS kernel (e.g., **Docker**).
        
    - **Sandboxing:** Using a VM to test malicious files safely without infecting the host.
        

#### 🏷️ Keywords & Links

#TryHackMe #HypervisorTypes #Containers #Docker #ISO27001 #SecurityPlus701 #[[BareMetal]] #[[Containerization]]