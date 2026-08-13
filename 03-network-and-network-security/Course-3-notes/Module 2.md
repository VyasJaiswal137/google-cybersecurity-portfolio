# Course 3 - Module 2

---

## 1. A summary of network protocols

A network protocol consists of a set of rules which are used by the devices on a network to specify the structure of the data and the order in which it is delivered. By means of protocols, devices all over the world are able to communicate with one another using a common language.

### Categories of Network Protocols

| Category                    | Definition & Function                                                               | Key Protocols               |
| :-------------------------- | :---------------------------------------------------------------------------------- | :-------------------------- |
| **Communication Protocols** | Specify the methods, timing, and way of recovering data that has been lost. | TCP, UDP, HTTP, DNS |
| Management Protocols | Are used for monitoring network activity, for reporting errors, and for optimising performance. | SNMP, ICMP |
| Security Protocols | Use encryption algorithms to guard data in transit against interception. | HTTPS, SFTP, IPSec, SSL/TLS

---

## 2. A Detailed Breakdown of the Core Network Protocols

### Communication Protocols

* **TCP (Transmission Control Protocol)**

  * **Layer:** Transport Layer
  * **Features:** It is a connection-oriented protocol and guarantees reliable delivery.
  * **Three-Way Handshake:** `SYN` → `SYN/ACK` → `ACK`

* **UDP (User Datagram Protocol)**

  * **Layer:** Transport Layer
  * **Characteristics:** It does not maintain a connection and is faster, but less reliable; it is best suited for real-time applications such as gaming and video streaming.

* **HTTP (Hypertext Transfer Protocol)**

  * **Layer:** Application Layer
  * **Port:** TCP Port 80
  * **Characteristics:** There is an insecure form of communication between the client browsers and the web servers.

* **DNS (Domain Name System)**

  * **Layer:** Application Layer
  * **Port:** UDP Port 53 (or TCP for large responses)
  * **Characteristics:** It converts readable domain names into IP addresses.

### Management Protocols

* **SNMP (Simple Network Management Protocol)**

  * **Layer:** Application Layer
  * **Characteristics:** They are used for monitoring and managing devices, resetting passwords, altering the configurations, and keeping record of bandwidth usage.

* **ICMP (Internet Control Message Protocol)**

  * **Layer:** Internet Layer
  * **Characteristics:** It signals transmission errors and sends status updates; it is used by commands such as ping to check connectivity and latency.

### Security Protocols

* **HTTPS (Hypertext Transfer Protocol Secure)**

  * **Layer:** Application Layer
  * **Port:** TCP Port 443
  * **Characteristics:** The web traffic is encrypted using SSL/TLS.

* **SFTP (Secure File Transfer Protocol)**

  * **Layer:** Application Layer
  * **Port:** TCP Port 22 (via SSH)
  * **Characteristics:** It uses AES encryption when encrypting file transfers and is often used for this purpose.

Note that while encryption protocols encrypt the payload they do not hide the source or destination IP addresses.

---

## 3. Other Important Protocols and Services

### Network Infrastructure & Addressing Protocols

* **NAT (Network Address Translation)**

  It translates private local IP addresses into a public IP address so that they can be routed on the internet.
  * Functions at both the Internet and Transport layers of the TCP/IP model.

* **DHCP (Dynamic Host Configuration Protocol)**

  It automatically assigns IP addresses, DNS server locations, and default gateways to devices.
  * **Ports:** The server uses UDP port 67; the client uses UDP port 68.

* **ARP (Address Resolution Protocol)**

  The IP addresses (logical) are mapped to the MAC addresses (physical) within a local network.
  It stores mappings in an ARP cache.

### Telnet vs. SSH

| Protocol               | Description                              | Port   | Security                             |
| :--------------------- | :--------------------------------------- | :----- | :----------------------------------- |
| **Telnet**             | Remote command-line management.      | TCP 23 | Not secure; sends data in plain text. |
| SSH (Secure Shell) | An encrypted alternative to Telnet which is secure. | TCP 22 | It is encrypted and secure. |

### Email Protocols

| Protocol                                    | Purpose                                                                                 | Unencrypted Port | Encrypted Port (TLS/SSL) |
| :------------------------------------------ | :-------------------------------------------------------------------------------------- | :--------------- | :----------------------- |
| **POP3 (Post Office Protocol)**           | It downloads emails directly to the local storage and may also remove or manage messages on the server. | TCP 110           | TCP 995                  |
| IMAP (Internet Message Access Protocol) | Enables email to be synchronized across various devices and maintains the content on the server. | TCP 143          | TCP 993                  |
| SMTP (Simple Mail Transfer Protocol) | Is used for routing and transmitting outgoing email between servers.              | TCP 25            | TCP 587                  |

---

## 4. The Evolution of Wireless Security Protocols

The wireless standards are regulated by the **IEEE 802.11** family.

```text
WEP (1999) ──► WPA (2003) ──► WPA2 (2004) ──► WPA3 (2018)
(Insecure)     (TKIP)         (AES / CCMP)    (SAE / 128–192 bit)
```

### 1. WEP (Wired Equivalent Privacy – 1999)

* **Status:** Outdated and high-risk.
**Flaws:** There are serious encryption vulnerabilities which make it easy to crack.

### 2. WPA (Wi-Fi Protected Access – 2003)

* **Improvement:** The introduction of the TKIP (Temporal Key Integrity Protocol) and the inclusion of message integrity checks.
* **Flaws:** It is susceptible to Key Reinstallation Attacks (KRACK).

### 3. WPA2 (2004)

* **Improvement:** It became the industry standard by using **AES** encryption and **CCMP**.
* **Modes:**

  * **Personal:** It makes use of a common passphrase; this is appropriate for home networks.
  The Enterprise system makes use of a central authentication server and is appropriate for businesses.
* **Flaws:** It is susceptible to KRACK attacks.

### 4. WPA3 (2018)

* **Improvement:** It provides protection against KRACK attacks by means of **SAE (Simultaneous Authentication of Equals)**.
* **Encryption:** The standard is 128 bits, with an optional enterprise mode providing 192 bits.

---

## 5. Subnetting and CIDR notation

### Subnetting

**Definition:** Dividing a range of network addresses into smaller logical networks (subnets).

**Benefits:**

It improves network performance and efficiency.
It saves bandwidth and IP address space.
It establishes separate **security zones**.

### CIDR (Classless Inter-Domain Routing)

We replaced the rigid classful addressing system (Class A to E) in order to help avoid exhaustion of IP addresses.
— for example, `198.51.100.0/24`
This results in smaller routing tables.
Optimises the allocation of IPv4 addresses.

---

## 6. Virtual Networks, Privacy and Security Tools

### Firewalls

* **Stateless Firewall:** Does not track session state and instead assesses traffic by using a set of fixed rules.
* **Stateful Firewall:** It keeps a record of active connections in a state table and automatically matches outgoing traffic.
* **NGFW (Next-Generation Firewall):** Provides advanced features such as:

  * Deep packet inspection
  * Application awareness
  * Intrusion Prevention System (IPS) capabilities
  * Malware sandboxing
  * URL/DNS filtering

### Proxy Servers

A proxy server functions as an intermediary between clients and servers.

* **Forward Proxy:** It provides protection for clients within the internal network when they request access to external resources.
* **Reverse Proxy:** It provides protection for internal servers that receive incoming requests from outside.

### VPNs & SD-WAN

* VPN (Virtual Private Network): It makes use of encapsulation in order to place encrypted packets inside other packets, thus securing the data during transmission and aiding in the hiding of the internal/private addressing of the connection.
* SD-WAN (Software-Defined Wide Area Network): it provides a secure connection between enterprise networks over large geographic distances.

---

## 7. VPN Protocols: WireGuard and IPSec

### Deployment Types

* **Remote Access VPN:** Provides a connection between a single device and a network.
* **Site-to-Site VPN:** It links up the entire network infrastructure of one branch with that of another located elsewhere.

### Protocol Comparison

| Feature                 | WireGuard VPN                                 | IPSec VPN                                                                              |
| :---------------------- | :-------------------------------------------- | :------------------------------------------------------------------------------------- |
| **Complexity** | The codebase is simple and lightweight. | Involves complex configuration and maintenance. |
| **Speed / Performance** | The speeds for downloading and streaming are extremely fast. | There is usually more overhead because of the wider range of features and the complexity of its configuration. |
| **Adoption**            | It is modern, open source, and easy to deploy.           | It has a historical presence and is natively supported on most operating systems.       |
| **Use Cases**           | Remote access and site to site connections.   | Mainly business site to site connections.                                         |

---

## Quick Revision Summary

| Topic             | Key Point                                                                |
| :---------------- | :----------------------------------------------------------------------- |
| **TCP**           | Reliable, connection-based transport protocol.                        |
| **UDP**           | Fast, connectionless transport protocol.                                 |
| **HTTP** | Refers to web traffic using the TCP port 80 and does not provide its own encryption. |
| HTTPS | Refers to web traffic that is encrypted and transmitted over TCP port 443. |
| **DNS** | Translates domain names into IP addresses; it usually operates on port 53. |
| **SNMP**          | Network monitoring and management.                                       |
| ICMP | Used for error reporting and for testing connectivity. |
| DHCP | Automatically assigns network configuration. |
| ARP | Assigns IP addresses to MAC addresses on a local network. |
| SSH | Administration remotely in a secure manner using the TCP port 22. |
| Telnet | Insecure remote administration using TCP port 23. |
| NAT | Carries out the translation of private addresses when communicating with the external network. |
| WEP | Is an obsolete and insecure wireless security protocol. |
| WPA/WPA2/WPA3 | The successive generations of Wi-Fi security. |
| **Subnetting** | Splitting a network into smaller logical networks. |
| **CIDR** | employs prefix notation in order to enable flexible IP addressing and routing. |
| Firewall | Regulates network traffic in accordance with security rules. |
| **VPN** | Achieves protection of network traffic by using tunneling or encapsulation together with encryption. |
| WireGuard | A modern and lightweight VPN protocol. |
| IPSec | is a VPN framework that is commonly used in enterprise environments. |
