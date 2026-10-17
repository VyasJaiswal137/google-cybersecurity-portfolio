\# Module 1 - Risks, Threats, Vulnerabilities



\---



\## 1. Understanding Risk, Threat \& Vulnerability



Three foundational terms sit at the center of security work, and although they are often used interchangeably in everyday conversation, each carries a precise meaning.



\- \*\*Risk:\*\* Anything that can impact the confidentiality, integrity, or availability of an asset.

\- \*\*Threat:\*\* Any circumstance or event that can negatively impact assets.

\- \*\*Vulnerability:\*\* A weakness that can be exploited by a threat.



Risk is commonly expressed through a simple relationship:



```text

Likelihood × Impact = Risk

```



A practical illustration: driving to work carries the risk of arriving late. That outcome becomes more likely if a tire goes flat along the way, and the impact could be severe, such as losing a job. Organizations reason about security in much the same way.



Calculating risk helps a business:



\- Prevent costly and disruptive events

\- Identify improvements to systems and processes

\- Determine which risks can be tolerated

\- Prioritize the critical assets that require attention



\### Risk Factors



Two broad factors drive risk: \*\*threats\*\* and \*\*vulnerabilities\*\*. Whether an asset is harmed depends largely on whether a threat manages to exploit a vulnerability.



\### Categories of Threat



\- \*\*Intentional\*\* — a malicious actor gaining access to sensitive information by targeting a misconfigured application.

\- \*\*Unintentional\*\* — an employee holding a door open for an unknown person and granting access to a restricted area.



\### Categories of Vulnerability



\- \*\*Technical\*\* — misconfigured software that gives an unauthorized person access to important data.

\- \*\*Human\*\* — a forgetful employee who loses an access card in a parking lot.



\---



\## 2. Asset Management \& Classification



Asset management is the process of tracking assets and the risks that affect them. The principle behind it is straightforward: only what is known to exist can be protected. Assets generally fall into several groups:



\- \*\*Digital assets\*\* such as customer data or financial records

\- \*\*Information systems\*\* that process data, like networks or software

\- \*\*Physical assets\*\* including facilities, equipment, or supplies

\- \*\*Intangible assets\*\* such as brand reputation or intellectual property



Classification is the practice of labeling assets by sensitivity and importance, which requires knowing what an asset is, where it sits, who owns it, and how important it is.



\### Common Classification Levels



| Level | Description |

| --- | --- |

| \*\*Restricted\*\* | The highest level, reserved for highly sensitive, need-to-know information. |

| \*\*Confidential\*\* | Assets whose disclosure could cause a significant negative impact on the organization. |

| \*\*Internal-only\*\* | Assets available to employees and business partners. |

| \*\*Public\*\* | The lowest level; no negative consequences if released. |



Note: Government organizations often label their most sensitive assets as \*confidential\* rather than \*restricted\*, so variability exists at the highest levels.



\### Challenges of Classifying Information



Identifying an owner is simple for something like a building, but far harder for information. A company laptop issued to an employee is a clear example of the ambiguity, particularly when that device also holds personal files. Information can also carry multiple classification values at once — a mailed letter contains both a public name and a confidential address.



\---



\## 3. The Emergence of Cloud Security



Cloud computing is defined by the U.K. National Cyber Security Centre as an on-demand, massively scalable service, hosted on shared infrastructure and accessible via the internet. It lowered the cost and complexity of running an online business, allowing companies to scale quickly, but it also introduced a new set of security challenges.



\### Cloud Service Models



| Model | Description |

| --- | --- |

| \*\*SaaS (Software as a Service)\*\* | Front-end applications accessed through a web browser, with the provider hosting and maintaining all backend systems (e.g., Gmail, Slack, Zoom). |

| \*\*PaaS (Platform as a Service)\*\* | Back-end application development tools accessed online, used to write, build, and deploy applications while the provider maintains the underlying hardware and software (e.g., Google App Engine, Heroku, VMware Cloud Foundry). |

| \*\*IaaS (Infrastructure as a Service)\*\* | Remote access to provider-hosted backend systems such as data processing servers, storage, and networking, licensed as needed. |



\### The Shared Responsibility Model



Responsibility is divided rather than eliminated. Clients typically secure anything directly within their control:



\- Identity and access management

\- Resource configuration

\- Data handling



The share delegated to the provider varies depending on whether SaaS, PaaS, or IaaS is in use.



\### Cloud Security Challenges



\- \*\*Misconfiguration\*\* — customers configure their own security environments and often rely on out-of-the-box settings that miss their objectives.

\- \*\*Cloud-native breaches\*\*, which are more likely where services are misconfigured.

\- \*\*Monitoring access\*\*, which becomes difficult depending on the client and service level.

\- \*\*Regulatory compliance\*\*, particularly for industries bound by HIPAA, PCI DSS, and GDPR.



\---



\## 4. Security Guidelines in Action: The NIST CSF



The NIST Cybersecurity Framework was released in 2014 to protect critical infrastructure in the United States, and was later adapted to suit public and private sector organizations of any size. Its major strength is flexibility — it can be applied across industries.



\### Components of the Framework



\- \*\*Core:\*\* A set of desired cybersecurity outcomes organized into five functions — Identify, Protect, Detect, Respond, and Recover. These guide organizations in locating their most important assets, safeguarding them, and planning detection and recovery.

\- \*\*Tiers:\*\* A 1-to-4 scale measuring the sophistication of an organization's cybersecurity program, with Tier 1 indicating a limited set of implemented controls. Tiers assess posture and highlight areas for improvement.

\- \*\*Profiles:\*\* Pre-made templates developed by industry experts, tailored to the risks of a specific organization or industry, and used to set a baseline or compare posture against a standard.



Note: Regulations are rules that must be followed, whereas frameworks are resources an organization chooses to adopt.



\### Implementation Guidance



The U.S. Cybersecurity and Infrastructure Security Agency outlines a practical sequence:



1\. Create a current profile of security operations and outline the specific needs of the business.

2\. Perform a risk assessment to identify which operations meet business and regulatory standards.

3\. Analyze and prioritize existing gaps that place assets at risk.

4\. Implement a plan of action to achieve the organization's goals.



Current risk, threat, and vulnerability trends should always be weighed when applying the framework.



\### Key Takeaway



The CSF is a voluntary, flexible resource that aligns with security practices across the global economy. It supports regulatory compliance and helps organizations avoid financial and reputational risk, though its level of detail can make implementation demanding.

