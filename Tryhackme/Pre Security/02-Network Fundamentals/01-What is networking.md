
### Task 1: What is Networking?

This task introduces networking as a system of interconnected devices (from 2 to billions) that exchange data. It draws parallels between real-world networks (postal systems, power grids) and computing networks. The core takeaway is that networking is the essential concept that allows devices to communicate via established rules called **protocols**.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.20 - Network Security.**
    
- **Implementation:** As a Lead Implementer, you must ensure the network is managed and controlled to protect information. This starts with defining the **Scope of the ISMS**—you cannot protect what you cannot map. Networking knowledge is required to identify all "Information Assets" that reside on the network.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0: Security Architecture.** (Understanding the fundamental connectivity required to implement security controls).
    
- **Key Terminology:** * **Network:** A group of interconnected systems.
    
    - **Nodes:** Any device (laptop, phone, traffic light) connected to the network.
        
    - **Protocols:** The set of rules that allow nodes to "speak" to each other.
        

#### 🏷️ Keywords & Links

#TryHackMe #NetworkingBasics #ISO27001 #SecurityPlus701 #[[NetworkArchitecture]] #[[AssetManagement]]

---

### 📑 Executive Room Summary (Partial - Room In Progress)

- **Core Concepts:** Introduction to how "things" connect and communicate.
    
- **GRC Strategic Impact:** Defines the physical and logical boundaries of the Information Security Management System (ISMS).
    
- **Study Focus:** Identification of network assets and the role of protocols in secure communication.
    

### ⌨️ Command Cheat Sheet

|**Concept**|**Description**|
|---|---|
|**Network Node**|Any device connected to a network|
|**Protocol**|The "language" or ruleset for communication|

### 🏷️ Final Tags

#RoomInProgress #Networking #Fundamentals #SecurityPlus

### Task 2: What is the Internet?

This task explores the **Internet** as a "network of networks." It uses an analogy of a multilingual person (Alice) acting as a bridge between different groups to explain how individual private networks connect through a larger public infrastructure. It covers historical milestones like **ARPANET** (late 1960s) and the creation of the **World Wide Web (WWW)** by Tim Berners-Lee in 1989. Key concepts include the distinction between **private networks** (internal) and **public networks** (the Internet).

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** **Annex A 8.22 - Segregation of Networks.**
    
- **Implementation:** From a GRC perspective, understanding the boundary between a private and public network is essential for **Risk Assessment**. A Lead Implementer must ensure that sensitive internal data is segregated from public-facing services. This task relates directly to how we define the "External Connectivity" section of an ISMS.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** **Domain 3.0: Security Architecture.** (Focus on network topology and the difference between LAN, WAN, and the Public Internet).
    
- **Key Terminology:**
    
    - **ARPANET:** The precursor to the modern Internet.
        
    - **World Wide Web (WWW):** The collection of information/websites accessed _via_ the Internet (often confused with the Internet itself).
        
    - **Private vs. Public IP:** Labels used to identify systems within an internal network versus on the global web.
        

#### 🏷️ Keywords & Links

#TryHackMe #InternetHistory #NetworkSegregation #ISO27001 #SecurityPlus701 #[[NetworkTopology]] #[[PublicVsPrivate]]


## Task 3: Identifying Devices on a Network

This task introduces the fundamental methods used to identify and communicate with devices within a network ecosystem. It focuses on the distinction between logical addressing (**IP Addresses**) and physical addressing (**MAC Addresses**), as well as the difference between private and public network visibility.

### 🌐 IP Addresses (Internet Protocol)

An IP address acts as a logical identifier for a device on a network.

- **IPv4:** The current standard, consisting of four octets (e.g., `192.168.1.1`).
    
- **Private vs. Public:** Private IPs are used within local networks (LAN), while Public IPs are unique across the entire Internet.
    
- **Dynamic vs. Static:** IPs can change (DHCP) or remain fixed for critical infrastructure.
    

### 🛠️ MAC Addresses (Media Access Control)

The MAC address is a unique, hardcoded physical identifier assigned to a Network Interface Controller (NIC) by the manufacturer. It is represented in hexadecimal format (e.g., `a4:c3:f0:85:ac:2d`). While IP addresses help route data across networks, MAC addresses are used for communication between devices on the same local segment.

#### 🛡️ ISO 27001 LI Alignment

- **Concept:** Annex A 8.8 (Management of technical vulnerabilities) & Annex A 8.16 (Monitoring activities).
    
- **Implementation:** A Lead Implementer ensures that **Asset Management (A.5.9)** includes a registry of MAC addresses and assigned IP ranges. This allows for the identification of unauthorized devices (Rogue Devices) attempting to connect to the ISMS scope.
    

#### 🔐 CompTIA Security+ 701 Focus

- **Exam Objective:** 3.0 Architecture and Design (3.2 Given a scenario, implement secure network designs).
    
- **Key Terminology:** * **IPv4 vs IPv6:** Understanding the exhaustion of IPv4 addresses.
    
    - **MAC Filtering:** A layer 2 security measure (though easily bypassed via spoofing).
        
    - **RFC 1918:** The standard defining private IP address ranges.
        

#### 🏷️ Keywords & Links

#TryHackMe #NetworkingBasics #IPAddressing #MACAddress #ISO27001 #SecurityPlus701 #[[AssetManagement]] #[[NetworkSecurity]]