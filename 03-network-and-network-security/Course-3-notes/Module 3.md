# Course 3 - Module 3 Study Notes: Network Intrusions & Packet Analysis

## 1. How Intrusions Compromise Systems

Networks contain vulnerabilities that attackers can exploit. Attackers may be motivated by money, politics, personal reasons, or other goals.

Security analysts monitor networks to detect and respond to these threats.

### Common Intrusion Methods

#### Network Interception

* **Packet Sniffing:** Capturing and analyzing data traveling across a network.
* **Traffic Alteration:** Intercepting and changing data while it is being transmitted.

#### Backdoor Attacks

A **backdoor** is a way to bypass normal authentication and security controls.

Backdoors can be:

* **Intentional:** Created by developers or administrators for troubleshooting or maintenance.
* **Malicious:** Installed by attackers after compromising a system.

Attackers can use backdoors to:

* Install malware
* Steal sensitive information
* Launch DoS attacks
* Change security settings
* Maintain long-term access

### Impact of Cyber Attacks

| Impact            | Description                                                                                    |
| ----------------- | ---------------------------------------------------------------------------------------------- |
| **Financial**     | Lost revenue, downtime, fines, legal costs, and customer compensation                          |
| **Reputational**  | Loss of customer trust and damage to the organization's reputation                             |
| **Public Safety** | Attacks against critical infrastructure can cause physical harm and disrupt essential services |

---

## 2. Network Protocol Analyzers & `tcpdump`

A **network protocol analyzer** captures and examines network traffic.

Common tools include:

* SolarWinds NetFlow Traffic Analyzer
* ManageEngine OpManager
* Azure Network Watcher
* **Wireshark** — graphical interface
* **tcpdump** — command-line interface

### What is `tcpdump`?

`tcpdump` is a lightweight command-line packet analyzer that uses the `libpcap` library.

Key features:

* Runs from the command line
* Commonly available on Linux and macOS
* Uses relatively few system resources
* Can display traffic in the terminal or save it to a file

### Common `tcpdump` Output

| Field                   | Description                          |
| ----------------------- | ------------------------------------ |
| **Timestamp**           | Time the packet was captured         |
| **Source IP/Port**      | Device and port that sent the packet |
| **Destination IP/Port** | Device and port receiving the packet |

> **Note:** By default, `tcpdump` may convert IP addresses to hostnames and port numbers to service names.

### Why Use `tcpdump`?

Security analysts can use it to:

* Monitor normal network traffic
* Identify unusual or malicious traffic
* Investigate security incidents
* Create traffic-based detection rules
* Identify unauthorized applications or devices
* Measure network traffic and capacity

---

## 3. Case Study: 2016 Dyn DNS DDoS Attack

On **October 21, 2016**, the DNS provider **Dyn** was targeted by a large Distributed Denial of Service (**DDoS**) attack.

The attack affected many popular websites and services in North America and Europe.

### Attack Flow

```text
Mirai Botnet
     ↓
Source Code Leaked
     ↓
More Compromised Devices
     ↓
Massive DNS Request Flood
     ↓
Dyn DNS Infrastructure Overwhelmed
     ↓
Websites Become Unreachable
```

### What Happened?

1. **Botnet Creation**
   The Mirai malware was used to create a botnet made up of compromised Internet-connected devices.

2. **Source Code Released**
   The Mirai source code was published online, allowing other attackers to create their own botnets.

3. **DDoS Attack**
   Attackers used the botnet to send a huge number of DNS requests to Dyn.

4. **Service Disruption**
   The traffic overwhelmed Dyn's infrastructure, making many websites unreachable.

5. **Recovery**
   Dyn restored its services and used additional infrastructure and scaling to help handle later attacks.

### Key Lesson

A large number of compromised devices can be combined into a **botnet** and used to generate massive amounts of malicious traffic.

---

## 4. Interception and Spoofing

### Promiscuous Mode

Normally, a Network Interface Card (**NIC**) processes packets intended for its own MAC address.

In **promiscuous mode**, the NIC can capture and process packets from other devices on the same network segment.

This is useful for:

* Network monitoring
* Troubleshooting
* Packet analysis
* Security investigations

---

## 5. Common Attack Techniques

### 5.1 On-Path Attack

An **on-path attack** occurs when an attacker places themselves between two communicating devices.

The attacker can then:

* Intercept network traffic
* Steal credentials
* Modify data
* Intercept DNS requests
* Send fake DNS responses
* Redirect users to malicious websites

**Defense:**

* Use end-to-end encryption
* Use TLS/HTTPS
* Properly validate certificates

---

### 5.2 Smurf Attack

A **Smurf attack** is a type of DoS attack that uses:

* IP spoofing
* ICMP traffic
* Network broadcast addresses

### How It Works

```text
Attacker
   ↓
ICMP Request with Spoofed Victim IP
   ↓
Network Broadcast Address
   ↓
Many Devices Respond
   ↓
Victim Receives Large Number of Responses
   ↓
DoS
```

1. The attacker sends an ICMP Echo Request.
2. The source IP is spoofed to appear as the victim's IP.
3. The request is sent to a broadcast address.
4. Multiple devices respond to the victim.
5. The large number of responses can overwhelm the victim.

**Defense:**

* Block external broadcast requests
* Use firewalls
* Monitor for unusual ICMP traffic
* Use network traffic filtering

---

## 6. IP Spoofing vs. Standard DoS

| Attack           | IP Address                                 | Response                            | Goal                                                                |
| ---------------- | ------------------------------------------ | ----------------------------------- | ------------------------------------------------------------------- |
| **IP Spoofing**  | Fake or impersonated IP                    | Usually goes to the spoofed address | Hide the attacker's identity, mislead systems, or exhaust resources |
| **Standard DoS** | Typically uses the attacker's real address | Not necessarily relevant            | Overwhelm a service and prevent legitimate access                   |

### What is IP Spoofing?

**IP spoofing** means changing the source IP address in a packet so that it appears to come from another device.

> Spoofing can make traffic harder to trace and is often used as part of other attacks.

---

## 7. Defense in Depth

**Defense in depth** means using multiple layers of security instead of relying on one security control.

### Important Layers

* **Encryption:** Protect data while it is traveling across the network.
* **Firewalls:** Filter traffic and detect suspicious activity.
* **Monitoring:** Identify unusual network behavior.
* **Redundancy:** Use additional infrastructure to handle failures or traffic spikes.
* **Scaling:** Increase available resources during large traffic events.

### Key Takeaway

> No single security control can stop every network attack. Layered security provides stronger protection.

---

## Quick Revision

| Concept              | Remember                                                 |
| -------------------- | -------------------------------------------------------- |
| **Packet Sniffing**  | Capturing and analyzing network packets                  |
| **Backdoor**         | A way to bypass normal security controls                 |
| **tcpdump**          | Command-line packet analyzer                             |
| **Promiscuous Mode** | Allows a NIC to process packets beyond its own traffic   |
| **On-Path Attack**   | Attacker intercepts communication between two parties    |
| **Smurf Attack**     | ICMP + IP spoofing + broadcast traffic                   |
| **IP Spoofing**      | Faking the source IP address                             |
| **DDoS**             | Many systems overwhelm a target with traffic             |
| **Botnet**           | Network of compromised devices controlled by an attacker |
| **Defense in Depth** | Multiple layers of security controls                     |

## Key Takeaways

1. Network attacks can involve **interception, spoofing, malware, or traffic flooding**.
2. **Packet analyzers** help analysts understand and investigate network traffic.
3. `tcpdump` is a useful lightweight tool for command-line packet analysis.
4. **On-path attacks** allow attackers to intercept or modify communications.
5. **Smurf attacks** use spoofed ICMP traffic to overwhelm a victim.
6. **Botnets** can generate massive amounts of traffic for DDoS attacks.
7. **Defense in depth** reduces the impact of attacks by using multiple security controls.
