# Module 2: Attacks, Domains & Threat Actors

> 💡 **Overview:** Common attack methods, the 8 CISSP security domains, and attacker profiles simplified for quick revision.

---

## 🎣 1. Common Attack Types

### A. Phishing Attacks
Phishing is tricking people through digital messages into sharing sensitive data or downloading bad software.

* **BEC (Business Email Compromise):** An email where a hacker pretends to be a trusted boss or vendor to trick someone into sending money or details.
* **Spear Phishing:** A custom, targeted email sent to a specific person or small group.
* **Whaling:** Spear phishing aimed directly at top company leaders (executives).
* **Vishing:** Phishing done through phone calls or voice messages.
* **Smishing:** Phishing done through SMS / text messages.

---

### B. Malware (Malicious Software)
Software designed to harm systems, spy on users, or steal money.

* **Virus:** Bad code that needs a person to click or open an infected file before it can spread and cause damage.
* **Worm:** Bad code that duplicates and spreads across network computers on its own without needing any user action.
* **Ransomware:** Locks (encrypts) an organization's files and demands money to restore access.
* **Spyware:** Secretly tracks user actions, reads private messages, and steals personal data without permission.

---

### C. Social Engineering
Tricking people by taking advantage of human trust and error.

* **Social Media Phishing:** Gathering personal details from social media profiles to plan a believable attack.
* **Watering Hole Attack:** Hacking a specific website that a target group visits regularly.
* **USB Baiting:** Leaving an infected USB drive in a public spot hoping an employee plugs it in.
* **Physical Social Engineering:** Impersonating a worker, customer, or repair person to walk inside a private building.

---

## 🛡️ 2. The 8 CISSP Security Domains

Cybersecurity responsibilities are categorized into 8 core areas known as domains:

1. **Security and Risk Management:** Defining security goals, policies, legal compliance, and overall risk management.
2. **Asset Security:** Protecting physical hardware, systems, and sensitive data types.
3. **Security Architecture and Engineering:** Building and designing safe computer systems and networks.
4. **Communication and Network Security:** Keeping network connections, channels, and transmitted data safe from tampering.
5. **Identity and Access Management (IAM):** Checking who users are and controlling what files or systems they can access.
6. **Security Assessment and Testing:** Testing systems through audits and checks to find weak spots before attackers do.
7. **Security Operations:** Day-to-day monitoring, investigation, and fixing security issues when alerts pop up.
8. **Software Development Security:** Making sure software and application code is written securely from start to finish.

---

## ⚔️ 3. Attack Categories & Domain Mapping

Different attack types fall under specific CISSP security domains:

| Attack Category | What It Means | Associated CISSP Domain |
| :--- | :--- | :--- |
| **Password Attack** | Trying to guess or break passwords (e.g., Brute force, Rainbow table). | Communication & Network Security |
| **Social Engineering** | Tricking people into sharing data or access (e.g., Phishing, Smishing, USB baiting). | Security & Risk Management |
| **Physical Attack** | Targeting physical items or hardware (e.g., malicious USB cables, card skimmers). | Asset Security |
| **Adversarial AI** | Manipulating artificial intelligence or machine learning systems to conduct attacks. | Communication & Network Security **AND** Identity & Access Management (IAM) |
| **Supply-Chain Attack** | Hacking a third-party seller or supplier to gain access to the main target. | Security & Risk Management, Security Architecture, **AND** Security Operations |
| **Cryptographic Attack** | Trying to break encrypted communications between sender and receiver (e.g., Birthday, Collision attacks). | Communication & Network Security |

---

## 👤 4. Threat Actor Types & Hackers

### A. Main Types of Threat Actors
* **Advanced Persistent Threats (APTs):** Highly skilled attackers who secretly break into major systems (like governments or large companies) and stay hidden for long periods. *(Goals: Stealing trade secrets or damaging power networks).*
* **Insider Threats:** Current or former employees, vendors, or partners who abuse their access. *(Goals: Stealing data, causing damage, or accidentally making security mistakes).*
* **Hacktivists:** Attackers driven by political or social views. *(Goals: Promoting social change, spreading propaganda, or seeking attention).*

---

### B. Categories of Hackers
A hacker is anyone using computers to access networks, systems, or data.

* **Authorized Hackers (Ethical / White Hat):** Follow the law and ethics to help companies test defenses and fix weaknesses.
* **Semi-Authorized Hackers (Researchers / Gray Hat):** Look for system bugs and weaknesses on their own, but do not steal or use them for harm.
* **Unauthorized Hackers (Unethical / Black Hat):** Break the law to steal, destroy, or sell confidential data for personal gain.
* **Unskilled / New Threat Actors:** Beginner attackers who use ready-made tools and scripts to learn, get attention, or seek revenge.