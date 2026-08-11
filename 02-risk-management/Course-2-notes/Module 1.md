# Course 2 - Module 1: Security Domains & Risk Management

## Eight Cybersecurity Domains

* **Domain 1: Security and Risk Management**  
  Focuses on establishing an organization's overall security posture—its capacity to defend critical assets and adapt to changes. Includes security goals, risk mitigation, compliance, business continuity plans, legal regulations, and ethics. Encompasses core InfoSec design processes such as incident response, vulnerability management, application security, cloud security, and infrastructure security (e.g., adjusting PII handling for GDPR compliance).

* **Domain 2: Asset Security**  
  Focuses on managing physical and virtual data throughout its lifecycle: storage, maintenance, retention, and destruction. Key practices include asset inventory, security impact analysis, data exposure management, establishing recovery plans, and maintaining backups.

* **Domain 3: Security Architecture and Engineering**  
  Focuses on managing data security through effective systems, tools, and design principles. Emphasizes key concepts including:
  * **Shared Responsibility:** All individuals involved take an active role in lowering risk during the design and maintenance of a security system.
  * **Threat Modeling:** Identifying, prioritizing, and analyzing potential security threats and vulnerabilities to proactively design safeguards.
  * **Least Privilege:** Restricting user and system access permissions to only the absolute minimum required to perform a specific task.
  * **Defense in Depth:** Layering multiple redundant security controls so that if one defensive mechanism fails, others step in to prevent a breach.
  * **Fail Securely:** Ensuring systems default to a protected, locked state whenever a system crash, error, or failure occurs.
  * **Separation of Duties:** Dividing critical tasks and authorization rights among multiple individuals to prevent single points of failure or abuse.
  * **Keep It Simple:** Minimizing architectural complexity to make security systems easier to implement, monitor, and audit.
  * **Zero Trust:** Assuming no network, user, or device is inherently trustworthy, requiring strict verification for every access request regardless of origin.
  * **Trust but Verify:** Granting necessary access while continuously logging, auditing, and inspecting actions to ensure compliance and detect unauthorized behavior.  
  *(Example: Deploying SIEM tools to monitor for unauthorized login activity).*

* **Domain 4: Communication and Network Security**  
  Focuses on securing physical networks, wireless communications, cloud connections, and remote/hybrid work environments through restricted network access controls.

* **Domain 5: Identity and Access Management (IAM)**  
  Focuses on authenticating user identities and authorizing access to physical and logical assets. Operates strictly on the **principle of least privilege**, granting only the minimum access needed to complete a specific task.

* **Domain 6: Security Assessment and Testing**  
  Focuses on identifying vulnerabilities, evaluating internal security controls, performing penetration testing ("pen testing"), conducting data analysis, and running security audits (e.g., auditing user permissions).

* **Domain 7: Security Operations**  
  Focuses on investigating potential breaches and implementing post-incident preventative measures. Encompasses training, documentation, intrusion detection/prevention, SIEM log management, playbooks, post-breach forensics, and documenting lessons learned.

* **Domain 8: Software Development Security**  
  Focuses on embedding secure programming practices throughout every phase of the Software Development Life Cycle (SDLC). Involves running application security tests, quality assurance, pen testing executables, and implementing proper encryption protocols.

---

## Risk Management & Assets

### Organizational Assets
* **Digital Assets:** Social Security Numbers (SSNs), dates of birth, bank account numbers, mailing addresses.
* **Physical Assets:** Payment kiosks, servers, desktop computers, office spaces.

### Core Risk Management Strategies
| Strategy | Description |
| :--- | :--- |
| **Acceptance** | Acknowledging and accepting a risk to avoid disrupting business operations. |
| **Avoidance** | Establishing a proactive plan to bypass or eliminate the risk entirely. |
| **Transference** | Shifting risk ownership and management to a third party. |
| **Mitigation** | Implementing controls to lessen the impact or likelihood of a known risk. |

### Key Frameworks & Catalogs
* **NIST Risk Management Framework (RMF)** - Structured process for identifying and managing system risks.
* **HITRUST** - Cybersecurity framework commonly used to manage compliance and risk.
* **NIST National Vulnerability Database (NVD)** - Standardized repository of security vulnerabilities.
* **CISA Known Exploited Vulnerabilities (KEV) Catalog** - Official database tracking active, real-world exploited vulnerabilities.

---

## Common Threats, Risks, and Vulnerabilities

### Threats
* **Insider Threats:** Authorized personnel or vendors abusing access privileges to compromise data.
* **Advanced Persistent Threats (APTs):** Sophisticated actors maintaining persistent, undetected access over extended periods.

### Risk Factors
* **External Risk:** Threat actors outside the organization attempting unauthorized access.
* **Internal Risk:** Risk originating from current/former employees, vendors, or trusted partners.
* **Legacy Systems:** Outdated or unmaintained hardware/software (e.g., old mainframe terminals or connected legacy kiosks) expanding the attack surface.
* **Multiparty Risk:** Intellectual property or data exposure resulting from third-party vendor access.
* **Software Compliance/Licensing:** Unpatched applications, outdated software, or licensing non-compliance.
* **OWASP Web Application Risks:** Top security risks including *Insecure Design*, *Software and Data Integrity Failures*, and *Server-Side Request Forgery*.

### Notable Vulnerabilities
* **ProxyLogon:** A pre-authenticated vulnerability in Microsoft Exchange servers allowing remote code execution.
* **ZeroLogon:** A critical exploit targeting Microsoft's Netlogon authentication protocol.
* **Log4Shell:** A severe Java-based flaw allowing remote arbitrary code execution and full system takeover.
* **PetitPotam:** An attack technique targeting Windows NTLM authentication over local area networks (LANs).
* **Security Logging & Monitoring Failures:** Insufficient logging visibility that lets threat actors operate undetected.
* **Server-Side Request Forgery (SSRF):** A web application flaw manipulating a server into reading or modifying backend resources.