# Cybersecurity Incident Report: Network Traffic Analysis

![TCPDUMP Logs](./TCPDUMP%20logs.png)

---

## Part 1: Problem Summary (DNS & ICMP Traffic Log)

* **The UDP protocol reveals that:** The client system (`192.51.100.15`) attempted to send DNS query requests to the DNS server (`203.0.113.2`) on destination UDP port 53 to resolve the IP address for `yummyrecipesforme.com`, but the server failed to process the requests.
* **This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message:** `ICMP 203.0.113.2 udp port 53 unreachable`.
* **The port noted in the error message is used for:** Domain Name System (DNS) services, which map human-readable domain names (e.g., `www.yummyrecipesforme.com`) to numerical IP addresses over UDP port 53.
* **The most likely issue is:** The DNS service on server `203.0.113.2` is either inactive/offline, or a network security control (such as a firewall rule) is actively blocking UDP traffic on port 53, preventing clients from completing DNS resolution.

---

## Part 2: Incident Analysis & Root Cause Identification

### Incident Metadata
* **Time Incident Occurred:** First observed at **13:24:32** (1:24 PM), with recurring failures logged at **13:26:32** and **13:28:32**.

### Incident Investigation Workflow

#### 1. Identification & Alerting
The IT support team became aware of the incident after multiple customers reported being unable to reach `www.yummyrecipesforme.com`, experiencing page load timeouts ending in a `destination port unreachable` error.

#### 2. Technical Investigation & Verification
* A cybersecurity analyst replicated the issue by attempting to visit the website and confirmed receiving the `destination port unreachable` error.
* The analyst initiated a packet capture using `tcpdump` on the local system and executed subsequent network calls to monitor traffic flow.

#### 3. Log Analysis Key Findings

| Attribute | Captured Value | Context |
| :--- | :--- | :--- |
| **Source IP & Port** | `192.51.100.15:52444` | Local client device initiating the DNS lookup. |
| **Destination IP & Port** | `203.0.113.2:53` | Target DNS server handling domain requests. |
| **Requested Resource** | `yummyrecipesforme.com` | Standard `A` record DNS lookup. |
| **Response Protocol** | `ICMP` | Return traffic indicating network protocol errors. |
| **Error Returned** | `udp port 53 unreachable` | Confirms destination host refuses UDP port 53. |

* **Impact Chain:** Because the browser could not complete the DNS lookup over UDP port 53, it never received the target web server's IP address. As a result, the client browser could not initiate the standard HTTPS request (TCP Port 443) to load the website content.

---

## Likely Root Causes

1. **DNS Service Outage:** The DNS service daemon running on target host `203.0.113.2` stopped running or crashed, causing the operating system to reject incoming UDP packets on port 53 with an ICMP Port Unreachable message.
2. **Firewall / Security Policy Misconfiguration:** A firewall rule was introduced or modified on network host `203.0.113.2` (or an intermediate network firewall) that explicitly blocks inbound UDP traffic directed at port 53.
3. **Denial of Service (DoS):** A volumetric or resource exhaustion attack on DNS server `203.0.113.2` caused the DNS service to fail, leaving port 53 unresponsive to legitimate user traffic.
