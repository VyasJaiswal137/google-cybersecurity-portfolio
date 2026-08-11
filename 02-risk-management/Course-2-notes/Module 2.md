# Course 2 - Module 2: Frameworks, Controls, and Security Audits

## Frameworks vs. Controls

* **Security Frameworks:** Guidelines used to build structured plans that mitigate risk and protect data and privacy. They assist organizations in adhering to industry compliance laws and regulations (e.g., healthcare organizations using frameworks to comply with HIPAA).
* **Security Controls:** Specific safeguards and actionable measures designed to reduce defined security risks. Controls operationalize frameworks (e.g., implementing Multi-Factor Authentication (MFA) on patient portals to meet HIPAA access mandates).

### Specific Frameworks

* **Cyber Threat Framework (CTF):** Developed by the U.S. government (Office of the Director of National Intelligence) to establish a common language for describing and communicating cyber threat activity, enabling security teams to share threat intelligence and respond faster.
* **ISO/IEC 27001:** An internationally recognized standard (part of the ISO 27000 family) outlining requirements for an Information Security Management System (ISMS). It provides best practices and a comprehensive library of security controls tailored for organizations of any size or sector.

---

## Control Categories

| Category | Definition | Examples |
| :--- | :--- | :--- |
| **Physical Controls** | Tangible safeguards protecting physical assets, facilities, and environments. | Gates, fences, locks, security guards, CCTV/surveillance cameras, motion detectors, keycard access badges. |
| **Technical Controls** | Hardware, software, or logical mechanisms designed to protect network infrastructure and data. | Firewalls, Multi-Factor Authentication (MFA), antivirus software. |
| **Administrative Controls** | Organizational policies, managerial procedures, and operational guidelines governing employee behavior. | Separation of duties, authorization matrices, asset classification schemes. |

---

## The CIA Triad

* **Confidentiality:** Ensures data and assets are restricted exclusively to authorized users.
  * *Implementation:* Enhanced using the **principle of least privilege** to limit user access solely to essential job functions.
* **Integrity:** Guarantees that data remains verifiably correct, authentic, uncorrupted, and reliable throughout its lifecycle.
  * *Implementation:* Uses **cryptography** and **encryption** (e.g., encoding internal chat messaging traffic) to prevent unauthorized tampering.
* **Availability:** Guarantees that data and critical systems remain reliably accessible to authorized users whenever required.
  * *Implementation:* Securely enabling remote access protocols for off-site workers while enforcing strict role-based access limits.

---

## OWASP Security Principles

### Foundational Principles
* **Minimize Attack Surface Area:** Reduce the overall number of accessible vulnerabilities a threat actor could exploit.
* **Principle of Least Privilege:** Limit user rights to the absolute minimum necessary for daily duties.
* **Defense in Depth:** Deploy multiple redundant security layers to mitigate threats if a primary control fails.
* **Separation of Duties:** Require multiple individuals to execute critical actions to prevent fraud or single points of failure.
* **Keep Security Simple:** Avoid unnecessary complexity; streamlined designs are easier to secure, monitor, and maintain.
* **Fix Security Issues Correctly:** Identify root causes, contain impacts, patch underlying vulnerabilities, and thoroughly test fixes post-incident.

### Core Operational Principles
* **Establish Secure Defaults:** The baseline, out-of-the-box configuration of an application must be its most secure state, requiring deliberate effort to lower protection.
* **Fail Securely:** When a security control or system component encounters an error or crash, it defaults to a locked state (e.g., a failing firewall drops all network traffic rather than permitting open connections).
* **Don’t Trust Services:** Treat third-party systems and partner integrations as untrusted environments; independently validate all incoming data before processing or storing it.
* **Avoid Security by Obscurity:** Never rely on keeping system design details or source code secret as the primary defense; security must rely on robust passwords, defense in depth, and architectural controls.

---

## Security Audits

A **security audit** is an independent review evaluating an organization’s security controls, policies, and operational procedures against established criteria:
* **Internal Criteria:** Organizational policies, internal SOPs, and industry best practices.
* **External Criteria:** Federal regulations, state laws, and statutory compliance frameworks.

### Goals and Objectives
* Verify that IT practices align with organizational standards and regulatory rules.
* Identify operational gaps, weaknesses, and non-compliance issues before they result in data breaches, regulatory fines, or penalties.
* Establish structured mitigation plans for security remediation and operational improvement.

### Influencing Factors
An organization's audit requirements are shaped by its **industry vertical**, **organizational size**, **geographical jurisdiction**, **government affiliations**, and **voluntary compliance decisions**.

### The Security Audit Lifecycle

1. **Identify the Audit Scope:** Define specific assets to evaluate (e.g., firewall configs, PII storage, physical locks), set business goals, establish audit frequency, and review operational policies.
2. **Complete a Risk Assessment:** Analyze identified organizational risks concerning budget, technical controls, internal processes, and regulatory mandates.
3. **Conduct the Audit:** Perform testing and verification on all systems, configurations, and physical controls defined within the audit scope.
4. **Create a Mitigation Plan:** Formulate actionable risk-reduction strategies to address discovered vulnerabilities, policy violations, or compliance gaps.
5. **Communicate Results to Stakeholders:** Deliver a comprehensive report outlining audit findings, prioritizing required remediation steps, and detailing necessary compliance adjustments.