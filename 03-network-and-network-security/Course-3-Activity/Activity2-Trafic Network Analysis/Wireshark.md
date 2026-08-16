# Cybersecurity Incident Report: TCP SYN Flood Analysis

```text
No.  Time      Source        Destination   Protocol Info
47   3.144521  198.51.100.23 192.0.2.1     TCP      42584->443 [SYN] Seq=0 Win-5792 Len=120...
48   3.195755  192.0.2.1     198.51.100.23 TCP      443->42584 [SYN, ACK] Seq=0 Win-5792 Len=120...
49   3.246989  198.51.100.23 192.0.2.1     TCP      42584->443 [ACK] Seq=1 Win-5792 Len=120...
50   3.298223  198.51.100.23 192.0.2.1     HTTP     GET /sales.html HTTP/1.1
51   3.349457  192.0.2.1     198.51.100.23 HTTP     HTTP/1.1 200 OK (text/html)
...
52   3.390692  203.0.113.0   192.0.2.1     TCP      54770->443 [SYN] Seq=0 Win=5792 Len=0...
57   3.664863  203.0.113.0   192.0.2.1     TCP      54770->443 [SYN] Seq=0 Win=5792 Len=0...
59   3.795332  203.0.113.0   192.0.2.1     TCP      54770->443 [SYN] Seq=0 Win-5792 Len=120...
...
73   6.230548  192.0.2.1     198.51.100.16 TCP      443->32641 [RST, ACK] Seq=0 Win-5792 Len=120...
77   7.330577  192.0.2.1     198.51.100.5  TCP      HTTP/1.1 504 Gateway Time-out (text/html)
```

---

## Guide: How to Read the Wireshark TCP Log

* **Time Recording:** Log entry No. 47 begins at 3.144521 seconds after capture start, tracking elapsed time in milliseconds to log rapid network events.
* **Source & Destination IPs:** `192.0.2.1` identifies the target web server, `198.51.100.0/24` represents internal employee workstations, and `203.0.113.0` represents an external host.
* **Protocol Column:** Captures Transport-layer traffic (TCP) establishing connection channels before transitioning to Application-layer traffic (HTTP).
* **Info Column:** Maps communication ports (`Source Port -> Destination Port`) where port 443 denotes encrypted web traffic (HTTPS).
* **TCP Control Flags:** Tracks connection handshake stages including `[SYN]`, `[SYN, ACK]`, `[ACK]`, and session resets (`[RST, ACK]`).
* **[SYN] Packet:** Initial synchronization request initiated by a client to request a server connection.
* **[SYN, ACK] Packet:** Server response acknowledging the client's request and allocating resources for the pending session.
* **[ACK] Packet:** Final acknowledgment sent by the client to finalize connection setup.

---

## Section 1: Identify the Type of Attack

* **One potential explanation for the website's connection timeout error message is:** A Denial of Service (DoS) attack, specifically a SYN flood targeting port 443 on the company's web server.
* **The logs show that:** An external IP address (`203.0.113.0`) is transmitting a massive volume of rapid `[SYN]` requests to `192.0.2.1:443` without ever sending final `[ACK]` responses to complete the handshake.
* **This event could be:** A malicious SYN flood attack intended to saturate server connection queues and disrupt availability for legitimate users.

---

## Section 2: Attack Mechanism & Server Impact

### The TCP Three-Way Handshake

1. **SYN (Synchronize):** The client device sends a `[SYN]` packet to the web server to request connection initialization.
2. **SYN-ACK (Synchronize-Acknowledge):** The web server receives the request, replies with a `[SYN, ACK]` packet, and reserves memory in its backlog queue for the pending session.
3. **ACK (Acknowledge):** The client sends a final `[ACK]` packet back to the server, establishing an active TCP connection.

---

### Impact of Rapid SYN Flooding

When an attacker floods a server with rapid `[SYN]` packets without responding to `[SYN, ACK]` replies, the target server holds open numerous half-open connections. Each half-open state reserves system resources while waiting for timeouts, quickly exhausting the server's connection backlog table.

### Log Findings & System Malfunction

| Observed Event          | Log Evidence                                                        | Technical Consequence                                               |
| :---------------------- | :------------------------------------------------------------------ | :------------------------------------------------------------------ |
| **Malicious SYN Flood** | Continuous `[SYN]` packets from `203.0.113.0` (entries 52 to 214+). | Fills available TCP connection slots on web server `192.0.2.1`.     |
| **Connection Resets**   | Server returning `[RST, ACK]` to `198.51.100.16` (entry 73).        | Server drops incoming employee requests due to resource exhaustion. |
| **Service Timeout**     | `504 Gateway Time-out` returned to `198.51.100.5` (entry 77).       | Legitimate web clients experience complete connection failure.      |

The Wireshark logs confirm that external host `203.0.113.0` overwhelmed web server `192.0.2.1` with incomplete handshake requests. As a result, legitimate internal employees (`198.51.100.0/24`) were refused service, resulting in connection resets and timeout errors.
