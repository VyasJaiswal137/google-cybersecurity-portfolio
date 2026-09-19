
# Course 4 — Module 2 Notes: Linux Architecture, Distributions, & Package Management

---

## 1. Linux Architecture & Data Flow

To really get how Linux is laid out, we have to follow the path a request takes as it moves through the system layers.


[ User ] ──► [ Applications ] ──► [ Shell ] ──► [ FHS ] ──► [ Kernel ] ──► [ Hardware ]


### Components of the Architecture

* **User:** Linux is multi-user by design, which means several users can access and share the same underlying system resources at the same time.
* **Applications:** These are software packages built to handle specific tasks. They get installed and managed through package managers.
* **Shell:** This is a text-based command-line interpreter. Think of it as the translator sitting between what the user types and the Linux kernel.
* **Filesystem Hierarchy Standard (FHS):** This is the specification that defines the directory structure — basically, it decides where data gets stored across the operating system.
* **Kernel:** The core piece of the system. It manages processes, system memory, and how hardware is allocated. It also talks to applications so commands get routed efficiently.
* **Hardware:** The physical parts of the computer, split into two categories — internal or peripheral:
* **Peripheral Devices:** Non-essential devices you attach (e.g., monitors, keyboards, mice, printers).
* **Internal Hardware:** Core components attached to the main circuit board (motherboard) that are required to run the system:
* **Central Processing Unit (CPU):** The main processor that executes program instructions.
* **Random Access Memory (RAM):** Volatile short-term storage that temporarily holds active program data; it gets cleared when the power goes off.
* **Hard Drive:** Non-volatile long-term storage that keeps persistent data and applications.

---

## 2. Major Linux Distributions in Cybersecurity

Security operations teams use different Linux distributions depending on what the job requires.

| Distribution | Parent / Family | Primary Focus & Characteristics |
| --- | --- | --- |
| **Kali Linux™** | Debian-derived | The industry-standard open-source distribution, pre-packaged with offensive security tools for penetration testing and digital forensics. |
| **Ubuntu** | Debian-derived | A user-friendly distribution with extensive community support, both CLI and GUI options, and broad adoption in cloud infrastructure. |
| **Parrot** | Debian-derived | A security-focused distribution offering lightweight desktop environments and built-in forensic/pen-testing tools. |
| **Red Hat® Enterprise Linux® (RHEL)** | Red Hat Family | An enterprise, subscription-based distribution built for enterprise stability and dedicated technical support. |
| **CentOS** | Red Hat Family | An open-source distribution derived from Red Hat source code, relying on community-driven support. |

---

## 3. Package Managers & Management Tools

Software packages contain the application binaries and dependencies (the supplemental files needed for execution). Keeping software updated ensures systems stay current with security patches and bug fixes.



| Distribution | Package File Type | Low-Level Manager | CLI Management Tool |
| --- | --- | --- | --- |
| Debian / Ubuntu | .deb | dpkg | APT |
| Red Hat / CentOS | .rpm | RPM | YUM |


### Low-Level Package Managers

* **dpkg:** A package manager built for Debian-derived software using `.deb` archive formats.
* **RPM (Red Hat Package Manager):** A package manager built for Red Hat family distributions using `.rpm` archive formats.

### Command-Line Package Management Tools

* **APT (Advanced Package Tool):** A command-line utility for Debian-based distributions used to search, configure, install, and update packages along with their dependencies.
* **YUM (Yellowdog Updater Modified):** A command-line utility for Red Hat-derived distributions used to fetch and manage `.rpm` packages and dependencies.

---

## 4. Linux Shell Types & Terminal Environments

A shell interprets text commands and translates them into instructions passed directly to the kernel.

### Common Shell Environments

* **Bash (Bourne-Again Shell):** The default and most widely used command-line interpreter in cybersecurity and Linux distributions. It uses the `$` prompt symbol for regular users.
* **Korn Shell (ksh):** An alternative shell that also uses the `$` prompt indicator.
* **Z Shell (zsh):** A more advanced shell featuring enhanced tab completion, using the `%` prompt indicator by default.
* **C Shell (csh) & Enhanced C Shell (tcsh):** Shell variants that adopt syntax styles similar to the C programming language.
