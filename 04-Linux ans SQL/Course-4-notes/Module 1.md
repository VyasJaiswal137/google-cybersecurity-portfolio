# Course 4 — Module 1 Notes: Operating Systems, Virtualization & Interfaces

## 1. Operating Systems Comparison & Security Risks

### Common Operating Systems

- **Windows:** Introduced in 1985. It is a closed-source OS widely used in personal and corporate environments.
- **macOS:** Introduced in 1984. It uses an open-source kernel along with proprietary, closed-source components.
- **Linux:** Released in 1991. It is open-source and allows communities to create different distributions. Many Linux distributions are designed specifically for cybersecurity.
- **ChromeOS:** Launched in 2011. It is based on the open-source Chromium OS and is commonly used in educational environments.
- **Android & iOS:** Mobile operating systems used in smartphones, tablets, and wearables. Android was released in 2008 and iOS in 2007. Android is largely open-source, while iOS contains both open-source and proprietary components.

### Legacy Operating Systems & Vulnerabilities

- **Legacy OS:** An outdated operating system that is no longer supported or regularly patched by its vendor.
- Organizations may continue using legacy systems because of old software dependencies or industrial equipment that cannot easily be replaced.
- Since these systems may not receive security updates, newly discovered vulnerabilities can leave them exposed to attacks.

### Vulnerability Monitoring Resources

- **Microsoft Security Response Center (MSRC):** Provides security advisories for Microsoft products and services.
- **Apple Security Updates:** Provides security updates and information for Apple platforms.
- **Ubuntu CVE:** Tracks vulnerabilities affecting Ubuntu Linux.
- **Google Cloud Security Bulletin:** Provides information about security issues and fixes related to Google Cloud.

---

## 2. Operating System Architecture & Execution Flow

### System Booting Sequence

1. **BIOS / UEFI Activation**
   - **BIOS (Basic Input/Output System):** Older firmware that initializes hardware and starts the boot process.
   - **UEFI (Unified Extensible Firmware Interface):** Modern firmware that replaced traditional BIOS and provides faster startup along with additional security features.

2. **Hardware Diagnostics**
   - The firmware checks the system hardware and verifies that the required components are working correctly.

3. **Bootloader Invocation**
   - BIOS or UEFI starts the **bootloader**, which loads the operating system into system memory.

### Hardware–Software Interaction

A simple way to understand how a computer performs a task is:

$$
\text{User} \rightarrow \text{Application} \rightarrow \text{Operating System} \rightarrow \text{Hardware} \rightarrow \text{Output}
$$

- **User:** Gives a command or performs an action.
- **Application:** Receives the user's request and communicates with the OS.
- **Operating System:** Acts as a bridge between applications and hardware.
- **Hardware:** Performs the actual operations, such as CPU calculations or reading and writing data to storage.
- **Output:** The result is sent back through the OS and application to the user.

---

## 3. Virtualization & Hypervisors

### Core Concepts

- **Virtualization:** A technology that creates virtual versions of physical computer resources, allowing one physical machine to run multiple isolated systems.
- **Resource Partitioning:** The host's resources can be divided between multiple virtual machines. For example, a computer with **16 GB RAM** could allocate **4 GB to each of four virtual machines**.
- **Security Isolation:** Virtual machines are separated from one another, so a program running inside one VM normally cannot directly affect other VMs or the host.
- **VM Escape:** Virtualization is not completely secure. In rare cases, an attacker may exploit a vulnerability to escape the virtual machine and interact with the host system.

### Hypervisor

A **hypervisor** is the software layer responsible for creating and managing virtual machines. It controls how hardware resources such as CPU, memory, and storage are shared between the host and guest systems.

- **KVM (Kernel-based Virtual Machine):** An open-source virtualization technology built into the Linux kernel. It allows Linux systems to function as hosts for virtual machines.

---

## 4. User Interfaces: CLI vs. GUI

| Feature | GUI (Graphical User Interface) | CLI (Command-Line Interface) |
|---|---|---|
| **Display Style** | Uses windows, icons, buttons, and other visual elements. | Uses a text-based terminal where commands are entered. |
| **Task Execution** | Usually requires performing tasks step-by-step through menus and buttons. | Commands can be combined, automated, and executed through scripts. |
| **Auditability** | Activity history may not always be automatically preserved. | Command history, such as `.bash_history`, can help with investigation and reviewing previous actions. |
| **Security Use** | Useful for general users and applications that require a visual interface. | Widely used for security automation, system analysis, troubleshooting, and forensic investigations. |