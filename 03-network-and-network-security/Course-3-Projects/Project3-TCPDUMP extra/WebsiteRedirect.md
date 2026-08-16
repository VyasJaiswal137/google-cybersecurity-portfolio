# How to Read a tcpdump Traffic Log

This guide explains how to read a `tcpdump` traffic log and use it to analyze network activity related to a security incident.

## 1. DNS Resolution

The first section of the log shows the computer performing a DNS lookup for `yummyrecipesforme.com`:

```text
14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A?
yummyrecipesforme.com. (24)

14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084
1/0/0 A 203.0.113.22 (40)
```

The first entry shows the source computer, `your.machine`, using port `52444` to send a DNS query to the DNS server, `dns.google.domain`. The query asks for the IPv4 address (`A` record) associated with `yummyrecipesforme.com`.

The DNS server then responds to the same source port and provides the IP address `203.0.113.22` for the requested domain.

In simple terms:

**Computer → DNS server:** “What is the IP address of `yummyrecipesforme.com`?”

**DNS server → Computer:** “The IP address is `203.0.113.22`.”

---

## 2. Establishing a TCP Connection

The next section shows the computer establishing a TCP connection with `yummyrecipesforme.com`:

```text
14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http:
Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS
val 3302576859 ecr 0,nop,wscale 7], length 0

14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086:
Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss
65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0
```

The source computer uses the temporary port `36086` to initiate a TCP connection with `yummyrecipesforme.com` on the HTTP service.

The `.http` suffix indicates the destination service is associated with HTTP, which normally uses **TCP port 80**.

The first packet contains:

* `Flags [S]` — a **SYN** packet, which starts the TCP connection.
* `seq` — the initial sequence number used for the connection.

The destination responds with:

* `Flags [S.]` — **SYN + ACK**, meaning it received the connection request and is acknowledging it.
* `ack` — the acknowledgment number for the received SYN.

Together, these packets are part of the **TCP three-way handshake**, which establishes the connection before data is exchanged.

### Common TCP Flags

| Flag  | Meaning                               |
| ----- | ------------------------------------- |
| `[S]` | SYN — starts a TCP connection         |
| `[.]` | ACK — acknowledges received data      |
| `[P]` | PSH — pushes data to the application  |
| `[F]` | FIN — begins closing a TCP connection |
| `[R]` | RST — resets/aborts a TCP connection  |

---

## 3. HTTP GET Request

The following packet shows the computer sending an HTTP request:

```text
14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http:
Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val
3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1
```

The important part is:

```text
HTTP: GET / HTTP/1.1
```

This indicates that the computer is requesting the root page (`/`) from `yummyrecipesforme.com` using the HTTP `GET` method and HTTP version `1.1`.

Because this traffic occurs during the security incident, this request is significant. It could represent the browser requesting a webpage or potentially downloading content associated with the incident.

The `[P.]` flag indicates that the packet contains application data and that the data should be pushed to the receiving application. The `.` represents the ACK flag.

---

## 4. A New DNS Lookup

Approximately two minutes later, the computer performs another DNS lookup:

```text
14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A?
greatrecipesforme.com. (24)

14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899
1/0/0 A 192.0.2.172 (40)
```

This time, the computer asks the DNS server for the IP address of a different domain:

`greatrecipesforme.com`

The DNS server responds with:

`192.0.2.172`

This change in the requested domain is important because it indicates that the computer is now attempting to communicate with a different destination.

---

## 5. Connection to the New Website

The log then shows a new TCP connection:

```text
14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http:
Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS
val 3302989649 ecr 0,nop,wscale 7], length 0

14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378:
Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss
65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0
```

The computer establishes a new TCP connection with `greatrecipesforme.com`.

Notice that the source port has changed from `36086` to `56378`. This is normal: client applications generally use temporary (ephemeral) source ports for separate TCP connections.

The traffic flow is now:

**Computer → `greatrecipesforme.com`**

and

**`greatrecipesforme.com` → Computer**

The important observation is that the computer has moved from communicating with `yummyrecipesforme.com` to communicating with `greatrecipesforme.com`.

---

## 6. What the Traffic Shows

When these entries are viewed together, the sequence of events is:

1. The computer performs a DNS lookup for `yummyrecipesforme.com`.
2. DNS returns `203.0.113.22`.
3. The computer establishes a TCP connection to the HTTP service.
4. The computer sends an HTTP `GET` request.
5. About two minutes later, the computer performs a DNS lookup for `greatrecipesforme.com`.
6. DNS returns `192.0.2.172`.
7. The computer establishes a new TCP connection to `greatrecipesforme.com`.

This sequence is important when investigating a security incident because it shows a **change in the destination domain** and a subsequent connection to that new destination.

The `tcpdump` log therefore provides evidence of the network communication that occurred during the incident, including DNS lookups, TCP connection establishment, and HTTP requests.

> **Key takeaway:** When reading a `tcpdump` log, focus on the **timestamps, source and destination addresses/ports, DNS lookups, TCP flags, and application-layer requests**. Looking at these elements together helps reconstruct what the computer was communicating with and when.
