# Module 4: Tools & Practices for Protecting Operations

> 💡 **Overview:** Essential security tools, forensic playbooks, programming languages, and core defensive concepts simplified for quick revision.

---

## 🛠️ 1. Security Tools & Monitoring Systems

* **SIEM (Security Information and Event Management):** Software that collects and analyzes system **logs** (records of events). Instead of manually reviewing data for days, SIEM automatically alerts analysts to specific threats.
* **Network Protocol Analyzer (Packet Sniffer):** A tool that captures and records data traffic moving across a network for analysts to inspect.
* **IDS (Intrusion Detection System):** Monitoring software that scans **network packets** (small chunks of data sent over a network) and alerts teams if unauthorized access or suspicious activity is detected.
* **Antivirus Software (Anti-malware):** Software that scans device memory and files to find, block, and delete viruses and malware.

---

## 📖 2. Security Playbooks & Digital Forensics

A **playbook** is a step-by-step manual that guides analysts through specific security tasks and incident response steps.

### A. Chain of Custody Playbook
* Documents everyone who handles digital evidence during an investigation (**Who, What, Where, and Why**).
* Every time evidence is moved or touched, it must be logged to ensure it stays safe and valid.

### B. Protecting and Preserving Evidence Playbook
* Rules for handling fragile digital evidence without altering or destroying it.
* **Order of Volatility:** The sequence showing which data to save first before it disappears *(e.g., volatile data lost as soon as a computer turns off)*.
* **Golden Rule of Forensics:** Always make copies of digital evidence and perform investigations on the copies—never on the original data.

---

## 💻 3. Programming & Operating Systems

### A. Programming Languages
* **Python:** Used by analysts to write scripts for **automation** (running repetitive tasks automatically to save time and reduce human error).
* **SQL (Structured Query Language):** Used to search, manage, and extract specific **data points** (pieces of information) from large **databases**.

### B. Operating Systems (OS)
* An OS is the software interface between computer hardware and the user *(e.g., Windows, macOS, Linux)*.
* **Linux:** An **open-source** operating system (meaning its source code is free for anyone to view and modify). It uses a **Command-Line Interface (CLI)** to interact with the system using text-based commands.

---

## 🔒 4. Defensive Concepts & Testing

* **Web Vulnerability:** A flaw or weak spot in a web application that hackers can exploit to steal data or install malware.
  * **OWASP Top 10:** A regularly updated list of the 10 most critical web application security risks.
* **Penetration Testing (Pen Testing):** A authorized, simulated cyberattack used to test defenses and find system weaknesses before real hackers can exploit them.

### Encryption vs. Encoding

| Concept | What It Does | Main Purpose |
| :--- | :--- | :--- |
| **Encryption** | Converts readable text (**Plaintext**) into scrambled, unreadable text (**Ciphertext**). | Keeps data secret (**Confidentiality**). |
| **Encoding** | Translates data into a standard format using a public algorithm. | Helps different computer systems share data easily *(not for secrecy)*. |