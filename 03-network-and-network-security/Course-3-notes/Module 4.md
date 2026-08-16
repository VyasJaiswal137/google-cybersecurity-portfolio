# Course 3 — Module 4 Notes

## Network Hardening, Cloud Security & Cryptography

---

## 1. Brute Force Attacks & Prevention Measures

### Brute Force Attack Types

- **Simple Brute Force Attack:** A trial-and-error process in which an attacker manually or automatically tries different combinations of usernames and passwords until a valid match is found.
- **Dictionary Attack:** Uses automated scripts to test lists of commonly used passwords, dictionary words, and previously compromised credentials.

### Prevention & Mitigation Strategies

- **Password Salting and Hashing:**
  - **Hashing** converts plaintext credentials into a fixed-length value using a one-way function.
  - **Salting** adds random data to a password before hashing, making password cracking and rainbow-table attacks more difficult.
- **Multi-Factor Authentication (MFA) & 2FA:** Requires users to provide two or more independent authentication factors:
  - Something you know — password/PIN
  - Something you have — security token/phone
  - Something you are — fingerprint/face
- **CAPTCHA / reCAPTCHA:** Uses challenges to distinguish human users from automated bots and scripts.
- **Password Policies:** Enforce security requirements such as:
  - Account lockouts after repeated failed attempts
  - Minimum password length
  - Strong password requirements
  - Password policies aligned with current NIST guidance

---

## 2. Testing & Isolation Environments

### Virtual Machines (VMs)

- A **Virtual Machine (VM)** is a software-based computer that runs in an isolated environment on a physical host.
- VMs are useful for:
  - Testing suspicious files
  - Analyzing malware
  - Testing software and patches
  - Creating isolated security environments
  - Rolling back systems using **snapshots**

### Sandboxes

- A **sandbox** is an isolated testing environment that can be physical, virtual, or cloud-based.
- Sandboxes are commonly used to:
  - Execute untrusted software safely
  - Analyze malware behavior
  - Test security patches
  - Evaluate suspicious applications

> **Note:** Advanced malware may contain **VM/sandbox detection** techniques. Such malware can identify virtualized environments and change or suppress its malicious behavior to avoid detection.

---

## 3. Network Defense Technologies & Architecture

Using multiple security controls creates **Defense in Depth**, which protects the network at multiple layers.

| Defensive ToolPrimary FunctionOperational Placement & MechanismKey Limitations |                                                                                                                 |                                                                                                  |                                                                                                                           |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **Firewall (Stateless / Stateful / NGFW)**                                     | Filters incoming and outgoing network traffic based on security rules.                                          | Typically placed at network boundaries and on individual hosts. Acts as a first line of defense. | May not detect complex, context-aware attacks or insider threats that bypass traditional rules.                           |
| **Intrusion Detection System (IDS)**                                           | Passively monitors traffic and generates alerts for suspicious activity, known attack signatures, or anomalies. | Usually positioned behind the firewall to inspect network traffic.                               | Passive only; it detects and alerts but does not normally block traffic.                                                  |
| **Intrusion Prevention System (IPS)**                                          | Detects and actively blocks suspicious network traffic.                                                         | Deployed inline, typically behind the firewall and before protected network resources.           | False positives can block legitimate traffic. Because it is inline, failures can potentially affect network connectivity. |
| **Security Information & Event Management (SIEM)**                             | Collects, correlates, and analyzes logs and security events from multiple systems.                              | Provides a centralized dashboard for SOC analysts.                                               | Requires skilled analysts to tune rules, reduce alert noise, and investigate incidents.                                   |
| **Full Packet Capture Devices**                                                | Records raw network packets for detailed forensic analysis.                                                     | Deployed at network taps or mirror/SPAN ports.                                                   | Requires significant storage capacity, especially for long-term retention.                                                |

### Defense in Depth

**Defense in Depth** means using multiple layers of security controls so that if one security mechanism fails, other mechanisms can still provide protection.

**Example:**

`Internet → Firewall → IDS/IPS → Network → Servers → SIEM Monitoring`

---

## 4. Cloud Security Considerations & Hardening

### Core Cloud Security Challenges

#### 1. Identity and Access Management (IAM)

- Overly permissive IAM roles can allow users or applications to access resources they do not need.
- Organizations should follow the **principle of least privilege**.

#### 2. Misconfigurations

- Incorrect cloud configurations are a major source of security incidents.
- Examples include:
  - Publicly exposed storage
  - Excessive permissions
  - Unsecured databases
  - Weak security-group rules

#### 3. Expanded Attack Surface

- Using multiple cloud applications and services increases the number of potential entry points.
- Each service must be properly configured, monitored, and secured.

#### 4. Zero-Day Vulnerabilities

- A **zero-day vulnerability** is a previously unknown or unpatched security vulnerability that can be exploited by attackers.
- Cloud Service Providers (CSPs) are responsible for securing infrastructure components such as hypervisors and underlying hardware.

#### 5. Visibility & Tracking

- Customers generally do not have direct access to the physical infrastructure operated by the CSP.
- Cloud-native monitoring tools can provide visibility into network activity, including:
  - **VPC Flow Logs**
  - **Packet mirroring**
  - Cloud monitoring and logging services

---

### Cloud Hardening Techniques

#### Baselining

**Baselining** establishes a known, secure configuration that can be used as a reference.

Examples include:

- Restricting administrative portal access
- Enforcing database encryption
- Removing unnecessary services
- Applying secure IAM defaults
- Standardizing network security configurations

### Hypervisors

A **hypervisor** is software that creates and manages virtual machines.

#### Type 1 — Bare-Metal Hypervisor

- Runs directly on physical hardware.
- Does not require a conventional host operating system underneath it.
- Commonly used in enterprise data centers and cloud environments.
- **Example:** VMware ESXi

#### Type 2 — Hosted Hypervisor

- Runs on top of an existing host operating system.
- Commonly used on desktops and personal computers.
- **Example:** VirtualBox

### VM Escape

**VM Escape** is an attack in which an attacker breaks out of a virtual machine and gains access to the underlying hypervisor or potentially other virtual machines.

---

## 5. Cloud Shared Responsibility Model

The **Shared Responsibility Model** defines which security responsibilities belong to the **Cloud Service Provider (CSP)** and which belong to the **customer**.

### Customer Responsibilities

The customer is generally responsible for:

- Customer data and assets
- Identity and Access Management (IAM)
- Application security
- Application configurations
- Operating system security in IaaS environments
- Network traffic rules and security configurations

### CSP Responsibilities

The Cloud Service Provider is generally responsible for:

- Physical data center security
- Physical hardware
- Hypervisors
- Core host operating systems
- Underlying network infrastructure
- Global cloud infrastructure and edge networking

### Simplified Model

```
+---------------------------------------------------------------+
|                   CUSTOMER RESPONSIBILITY                     |
|                                                               |
|  - Customer Data & Assets                                     |
|  - Identity & Access Management (IAM)                         |
|  - Application Security & Configurations                       |
|  - Operating System & Network Rules (IaaS)                    |
+---------------------------------------------------------------+

                              ||

+---------------------------------------------------------------+

|                      CSP RESPONSIBILITY                        |
|                                                               |
|  - Physical Data Center Security                              |
|  - Hardware Infrastructure & Hypervisors                       |
|  - Core Host Operating Systems                                 |
|  - Network Infrastructure & Global Edge                       |
+---------------------------------------------------------------+
```

> **Key Point:** The CSP secures the underlying cloud infrastructure, while the customer is responsible for securing what they deploy and configure within the cloud.

---

## 6. Cryptography & Key Management

### Encryption

**Encryption** is the process of converting readable **plaintext** into unreadable **ciphertext** using a cryptographic algorithm and key.

The main goals are:

- **Confidentiality** — prevents unauthorized users from reading data.
- **Integrity** — helps detect unauthorized modification.
- **Authentication** — can help verify the identity or origin of data, depending on the cryptographic mechanism.

### Cryptographic Erasure (Crypto-Shredding)

**Cryptographic erasure**, also called **crypto-shredding**, is a data-destruction technique in which the encryption keys required to decrypt data are permanently destroyed.

Once the keys are destroyed:

```
Encrypted Data + Destroyed Key
            ↓
     Data becomes unreadable
```

This can make encrypted data effectively inaccessible without physically destroying the storage device.

---

## 7. Key Management Storage Solutions

### Trusted Platform Module (TPM)

A **Trusted Platform Module (TPM)** is a dedicated hardware security component built into or attached to a computer.

It can securely store and protect:

- Encryption keys
- Certificates
- Password-related secrets
- Other cryptographic material

TPMs can also support platform integrity and secure boot mechanisms.

### Cloud Hardware Security Module (CloudHSM)

A **CloudHSM** is a dedicated hardware security module provided in a cloud environment.

It is designed to securely:

- Generate cryptographic keys
- Store cryptographic keys
- Perform cryptographic operations
- Protect sensitive key material from unauthorized access

---

# Quick Revision Summary

| TopicKey Point            |                                                                     |
| ------------------------- | ------------------------------------------------------------------- |
| **Simple Brute Force**    | Tries many username/password combinations.                          |
| **Dictionary Attack**     | Uses lists of common or compromised passwords.                      |
| **Salting**               | Adds random data before hashing a password.                         |
| **MFA/2FA**               | Uses multiple authentication factors.                               |
| **VM**                    | Isolated virtual computer environment.                              |
| **Sandbox**               | Isolated environment for testing suspicious software.               |
| **Firewall**              | Filters network traffic according to security rules.                |
| **IDS**                   | Detects and alerts on suspicious activity.                          |
| **IPS**                   | Detects and actively blocks suspicious activity.                    |
| **SIEM**                  | Centralizes and correlates security logs and events.                |
| **Packet Capture**        | Records raw packets for forensic analysis.                          |
| **IAM**                   | Controls identities, permissions, and resource access.              |
| **Baselining**            | Establishes a known secure configuration.                           |
| **Type 1 Hypervisor**     | Runs directly on physical hardware.                                 |
| **Type 2 Hypervisor**     | Runs on top of a host OS.                                           |
| **VM Escape**             | Attack that breaks out of a VM to the host/hypervisor.              |
| **Shared Responsibility** | CSP and customer share cloud security duties.                       |
| **Encryption**            | Converts plaintext into ciphertext.                                 |
| **Crypto-Shredding**      | Destroys encryption keys to make data unreadable.                   |
| **TPM**                   | Hardware component for protecting cryptographic secrets.            |
| **CloudHSM**              | Cloud-based dedicated hardware for secure cryptographic operations. |



