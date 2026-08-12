# Course 3 - Module 1: Network Components, Architecture, and Models

## 1. Network Equipment and Architecture

### Core Network Devices
* **End-User Devices (Clients):** Includes workstations, laptops, mobile phones, and tablets. Each device contains a Network Interface Card (NIC), a unique MAC address, and an assigned IP address to send and receive data packets over wired or wireless connections.
* **Firewalls:** Hardware or software security devices that monitor and filter incoming and outgoing traffic based on configured security rules. Positioned at the boundary between trusted internal networks and untrusted external networks (e.g., the internet).
* **Servers:** Dedicated systems providing services to network clients (Client-Server Model).
  * **DNS Servers:** Convert readable domain names into IP addresses.
  * **File Servers:** Store and manage accessible files and databases.
  * **Mail Servers:** Process, store, and route corporate email.
* **Hubs vs. Switches:**
  * **Hub:** A physical-layer (Layer 1) device that connects multiple devices and broadcasts all incoming data out to every port. *Legacy device; rarely used in modern networks due to eavesdropping vulnerabilities.*
  * **Switch:** A data-link layer (Layer 2) device that maintains a table of MAC addresses matched to physical ports. Forwards packets only to the intended destination device.
* **Routers:** Layer 3 devices positioned between different networks that forward data packets based on destination IP addresses contained in the packet header. Many routers feature built-in firewall capabilities to block malicious incoming traffic.
* **Modems & Wireless Access Points (WAPs):**
  * **Modem:** Connects to an Internet Service Provider (ISP) via coaxial or telephone lines and converts analog ISP signals into digital signals for local routers. *(Enterprise networks generally use high-volume broadband connections instead of standard modems).*
  * **Wireless Access Point (WAP):** Sends and receives digital network signals via radio waves using Wi-Fi protocols, allowing wireless devices to connect.
* **Network Diagrams:** Topographical maps that use symbolic graphics and connection lines to display network device structures and data paths. Used by security analysts when designing, monitoring, and auditing network boundaries.

---

## 2. Cloud Computing and Software-Defined Networks (SDNs)

### Infrastructure Deployment Models
* **On-Premises Network:** Conventional network infrastructure completely located within physical facilities owned or operated by the organization.
* **Cloud Computing:** Utilizing remote servers, virtual storage, and network services provided over the internet by a Cloud Service Provider (CSP).
* **Hybrid Cloud:** An operational environment combining on-premises infrastructure and cloud services provided by a CSP.
* **Multi-Cloud:** Utilizing cloud services from more than one separate CSP.

### CSP Service Delivery Models
* **Software as a Service (SaaS):** Software applications completely managed by the cloud service provider and accessed remotely by end users (e.g., webmail, productivity suites).
* **Infrastructure as a Service (IaaS):** On-demand computing resources such as virtual servers, cloud storage, and containers configured via APIs or management consoles.
* **Platform as a Service (PaaS):** Cloud-hosted development frameworks and environment tools used by developers to build, test, and host custom applications.

### Software-Defined Networks (SDNs)
* **Definition:** Network architectures that substitute physical hardware setups with virtual networking components (such as virtual switches, virtual routers, and virtual firewalls) controlled by software.
* **Key Business Benefits:**
  * **Reliability:** Guarantees high uptime, redundant connectivity, and continuous resource availability.
  * **Cost Efficiency:** Cuts down on capital expenditures associated with physical hardware, installation, patching, and ongoing physical maintenance.
  * **Scalability & Agility:** Employs an elastic utility model ("pay for what you use") and enables the immediate deployment of security mechanisms such as Web Application Firewalls (WAFs) and Intrusion Detection/Prevention Systems (IDS/IPS).

---

## 3. Network Communication Models: TCP/IP and the OSI

### The TCP/IP Model (4 Layers)

1. **Network Access Layer (Data Link / Physical):** Responsible for transmitting data frames over local physical hardware, including cables, modems, NICs, hubs, and the **Address Resolution Protocol (ARP)** used for mapping IP addresses to MAC addresses on the local network.
2. **Internet Layer (Network):** Responsible for delivering packets across various networks.
   * **IP (Internet Protocol):** Responsible for logical addressing and routing packets from source to destination.
   * **ICMP (Internet Control Message Protocol):** Used for reporting transmission errors, connectivity status, dropped packets, and redirection data.
3. **Transport Layer:** Responsible for end-to-end communication, session reliability, and port mapping.
   * **TCP (Transmission Control Protocol):** Connection-oriented protocol that ensures reliable delivery using port numbers in the header and monitoring packet delivery.
   * **UDP (User Datagram Protocol):** Connectionless protocol providing lightweight delivery. Transmission is unchecked and optimized for real-time, performance-sensitive applications (e.g., video streaming).
4. **Application Layer:** Specifies protocols used for internet services accessed by applications and end users (e.g., HTTP, HTTPS, SMTP, SSH, FTP, and DNS).

---

### The OSI Model (7 Layers)

| Layer | Layer Name | Core Functions | Protocol / Component Examples |
| :---: | :--- | :--- | :--- |
| **7** | **Application** | Allows user applications to interact directly with network services. | HTTP, HTTPS, SMTP, DNS, FTP |
| **6** | **Presentation** | Handles data formatting, character set conversion, compression, and encryption. | SSL/TLS, JPEG, ASCII |
| **5** | **Session** | Sets up, manages, authenticates, checkpoints, and terminates persistent connections. | RPC, NetBIOS, Session Checkpoints |
| **4** | **Transport** | Handles end-to-end data transmission, traffic flow control, error checking, and segmentation. | TCP, UDP |
| **3** | **Network** | Performs logical network addressing (using IP) and routes packets between different networks. | IP, ICMP, Routers |
| **2** | **Data Link** | Delivers data frames between local nodes using physical addresses. | MAC Addresses, Switches, ARP, HDLC |
| **1** | **Physical** | Transmits raw, unstructured bit streams (0s and 1s) over physical media. | Cables, Hubs, Modems, Signals |

---

## 4. Communication within the Network Layer and IP Packets

### IPv4 Packet Structure
An IPv4 packet consists of a **Header** (ranging between 20 and 60 bytes) and a **Data Payload** (maximum total packet size is 65,535 bytes).

### The 13 Fields of an IPv4 Packet Header
1. **Version (VER):** A 4-bit field specifying the version of IP being used (e.g., IPv4).
2. **IP Header Length (HLEN / IHL):** Indicates where the packet header ends and the data begins.
3. **Type of Service (ToS):** Informs routers how to prioritize packets regarding Quality of Service (QoS).
4. **Total Length:** Communicates the total byte size of the packet (header plus data payload).
5. **Identification:** Unique identifier assigned to group fragments of an oversized original packet.
6. **Flags:** Determines whether packet fragmentation is allowed or if additional fragments exist.
7. **Fragmentation Offset:** Indicates the specific position of a fragment relative to the original unfragmented packet.
8. **Time to Live (TTL):** A hop counter decremented by 1 at each router to prevent packets from circulating indefinitely. When TTL reaches 0, the packet is discarded and an ICMP *Time Exceeded* message is returned.
9. **Protocol:** Specifies the higher-layer transport protocol used in the data portion (e.g., TCP or UDP).
10. **Header Checksum:** Contains a value used to detect header corruption during transit; corrupted packets are discarded.
11. **Source IP Address:** The 32-bit IPv4 address of the transmitting device.
12. **Destination IP Address:** The 32-bit IPv4 address of the receiving device.
13. **Options:** Optional fields (0 to 40 bytes) used for custom routing or security parameters (included only if HLEN is greater than 5).

---

### IPv4 vs. IPv6 Comparison

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Length** | 32 bits (4 bytes) | 128 bits (16 bytes) |
| **Format** | Dotted Decimal (e.g., `198.51.100.0`) | Hexadecimal notation (e.g., `2002:0db8:0000:0000:0000:ff21:0023:1234`) |
| **Address Capacity** | ~4.3 billion ($4.3 \times 10^9$) | ~340 undecillion ($3.4 \times 10^{38}$) |
| **Header Design** | Complex (includes IHL, Identification, Flags) | Streamlined fixed header format |
| **Special Features** | Requires NAT for internal addressing | Eliminates private IP collisions; includes **Flow Label** field for routing priority |
