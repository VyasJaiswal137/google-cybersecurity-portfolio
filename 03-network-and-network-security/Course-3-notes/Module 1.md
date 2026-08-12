# Course 3 - Module 1: Network Components, Architecture, and Models

## 1. Network equipment and architecture

### Core Network Devices
* End-user devices (clients): these include workstations, laptops, mobile phones, and tablets. Each of these devices has a network interface card (NIC), a unique MAC address, and an assigned IP address so as to be able to send and receive data packets over wired or wireless connections.
**Firewalls:** These are security devices that can be hardware or software which monitor and filter traffic going in and out by referring to the security rules that have been set up. They are positioned at the boundary between trusted internal networks and untrusted external networks (for example, the internet).
* **Servers:** These are dedicated systems which provide services to network clients (the Client-Server Model).
  * DNS Servers: Convert readable domain names into IP addresses.
  * File servers are used for storing and managing files and databases that are accessible.
  * **Mail Servers:** They process, store, and route corporate email.
* **Hubs vs. Switches:**
  * **Hub:** This is a device at the physical layer which connects various devices and sends all the data that comes in to each of the ports. *It is a legacy device and is seldom used in modern networks because of its eavesdropping vulnerabilities.*
  * **Switch:** A device at the data-link layer which keeps a table of MAC addresses matched to the physical ports on the switch. It forwards packets only to the intended destination device.
**Routers:** These are Layer 3 devices which are positioned between different networks and forward data packets by referring to the destination IP addresses contained in the IP packet header. A large number of routers have built-in firewall filtering capabilities which allow them to block malicious incoming traffic.
* **Modems & Wireless Access Points (WAPs):**
  * **Modem:** Connects to an Internet Service Provider (ISP) through coaxial or telephone lines and converts the analog signals from the ISP into digital signals for use by local routers. (Enterprise networks generally make use of high-volume broadband connections instead of standard modems.)
  * Wireless Access Point (WAP): Sends and receives digital network signals via radio waves using Wi-Fi protocols, which allows wireless devices to connect.
* **Network Diagrams:** These are topographical maps that use symbolic graphics and lines to show the structure of network devices and the paths of data. They are used by security analysts when designing, monitoring, and auditing network boundaries.

---

## 2. Cloud computing and software-defined networks (SDNs)

### Infrastructure Deployment Models
* **On-premises network:** The conventional network infrastructure is completely located within physical facilities that are owned or operated by the organization.
* Cloud computing involves using remote servers, virtual storage, and network services that are provided over the internet by a Cloud Service Provider (CSP).
* **Hybrid Cloud:** This refers to an operational environment that uses both on-premise infrastructure and cloud services provided by a cloud service provider.
* **Multi-Cloud:** Using cloud services from more than one separate CSP.

### CSP Service Delivery Models
* Software as a Service (SaaS): These are software applications which are completely managed by the cloud service provider and which are accessed remotely by end users (for example, webmail and productivity suites).
* Infrastructure as a Service (IaaS): Computing resources such as virtual servers, cloud storage, and containers that can be obtained on demand and are configured using APIs or management consoles.
* Platform as a Service (PaaS): These are development frameworks and environment tools hosted on the cloud and are used by developers for building, testing, and hosting custom applications.

### Software-Defined Networks (SDNs)
* **Definition:** Network architectures which substitute the use of physical hardware setups with virtual networking components (such as virtual switches, virtual routers, and virtual firewalls) that are controlled by software.
* **Key Business Benefits:**
  * **Reliability:** It guarantees a high level of uptime, provides redundant connectivity, and ensures that resources are always available.
  * In terms of cost efficiency, it cuts down on the capital expenditures associated with physical hardware, its installation, patching, and the continuous physical maintenance.
  * Scalability and agility: It employs an elastic utility model ("pay for what you use") and enables the immediate deployment of security mechanisms such as Web Application Firewalls (WAFs) and Intrusion Detection/Prevention Systems (IDS/IPS).

---

## 3. Network Communication Models: TCP/IP and the OSI

### The TCP/IP Model (4 Layers)

1. **Network Access Layer (Data Link/Physical):** It is responsible for the transmission of data frames over the local physical hardware, and this includes cables, modems, NICs, hubs, and the **Address Resolution Protocol (ARP)** which is used for mapping IP addresses to MAC addresses on the local network.
2. **Internet Layer (Network):** It is responsible for delivering packets across various networks.
   * **IP (Internet Protocol):** It is responsible for carrying out logical addressing and for routing packets from the source to the destination.
   * ICMP (Internet Control Message Protocol) is used for reporting transmission errors, connectivity status, dropped packets, and redirection data.
3. **Transport Layer:** It is responsible for end-to-end communication, ensuring session reliability and carrying out port mapping.
   * **TCP (Transmission Control Protocol):** It is connection-oriented and ensures reliable delivery by using port numbers in the header and by monitoring the delivery of packets.
   * UDP (User Datagram Protocol): It is connectionless and provides lightweight delivery. Transmission is not checked and is optimized for applications that are sensitive to performance and require real-time operation (for example, video streaming).
4. **Application Layer:** It specifies the protocols used for internet services that are accessed by applications and end users (such as HTTP, HTTPS, SMTP, SSH, FTP, and DNS).

---

### The OSI Model (7 Layers)

| Layer | Layer Name | Core Functions | Protocol / Component Examples |
| :---: | :--- | :--- | :--- |
| 7 | Application | It allows user applications to interact directly with network services. | HTTP, HTTPS, SMTP, DNS, FTP |
| 6 | Presentation | It deals with data formatting, character set conversion, compression, and encryption. | SSL/TLS, JPEG, ASCII
| 5 | Session | It sets up, manages, authenticates, checks at intervals, and ends persistent system connections. | RPC, NetBIOS, Session Checkpoints |
4. Transport — end-to-end data transmission, traffic flow control, error checking, and segmentation. — TCP, UDP
| 3 | Network | The process of carrying out logical network addressing (using IP) and routing packets between different networks. | IP, ICMP, Routers
| 2 | Data Link | The delivery of data frames between local nodes using physical addresses. | MAC Addresses, Switches, ARP, HDLC |
| 1 | Physical | The transmission of raw, unstructured bit streams (consisting of 0s and 1s) over physical media. | Cables, Hubs, Modems, Signals |

---

## 4. Communication within the Network Layer and IP Packets

### IPv4 Packet Structure
The data in an IPv4 packet consists of a header (which is between 20 and 60 bytes) and a data payload (the total size of the packet being no more than 65,535 bytes).

### The 13 Fields of an IPv4 Packet Header
1. **Version (VER):** A 4-bit field that specifies the version of IP being used (for example, IPv4).
2. **IP Header Length (HLEN / IHL):** It indicates the point at which the packet header comes to an end and the data starts.
3. **Type of Service (ToS):** It tells routers how to prioritize packets with regard to Quality of Service (QoS).
4. **Total Length:** This refers to the total byte size which is made up of the header and the data payload.
5. **Identification:** A unique identifier is assigned to a group of fragments from an oversized original packet.
6. **Flags:** Determine whether packet fragmentation is allowed or whether further fragments exist.
7. **Fragmentation Offset:** This indicates the specific position of a fragment in relation to the original, unfragmented packet.
8. **Time to Live (TTL):** At each router the hop counter is decreased by 1. It stops packets from circulating indefinitely and when the TTL reaches 0 the packet is discarded together with the sending of an ICMP *Time Exceeded* message.
9. **Protocol:** This refers to the higher-layer transport protocol contained in the data section (for example, TCP or UDP).
10. **Header Checksum:** It contains a value which is used to detect any corruption of the header during transmission and packets that are corrupted are discarded.
11. **Source IP Address:** the 32-bit IPv4 address of the device that is transmitting.
12. **Destination IP Address:** the 32-bit IPv4 address of the device which is to receive the data.
13. **Options:** Fields that are optional (occupying 0 to 40 bytes) and are used for custom routing or security parameters (these fields are included only if HLEN is greater than 5).

---

### IPv4 vs. IPv6 Comparison

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Length** | 32 bits (4 bytes) | 128 bits (16 bytes) |
| **Format** | Dotted Decimal (for example, `198.51.100.0`) | Hexadecimal notation (for example, `2002:0db8:0000:0000:0000:ff21:0023:1234`) |
| Address Capacity | about 4.3 billion (4.3 × 10⁹) | about 340 undecillion (3.4 × 10³⁸) |
| **Header Design** | Complex (includes IHL, Identification, Flags) | Streamlined fixed header format |
| **Special Features** | Requires NAT for internal addressing | Eliminates private IP collisions; includes **Flow Label** field for routing priority |
