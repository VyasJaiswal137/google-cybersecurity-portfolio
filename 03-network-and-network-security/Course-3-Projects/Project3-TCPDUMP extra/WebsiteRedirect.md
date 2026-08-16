# Cybersecurity Incident Report: Website Compromise & Malware Redirection

## How to Read the tcpdump Traffic Log

This reading explains how to use tcpdump to analyze the network traffic related to the security incident.

```text
14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A?
yummyrecipesforme.com. (24)

14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084
1/0/0 A 203.0.113.22 (40)
```

The first section of the DNS and HTTP traffic log shows the source computer (`your.machine.52444`) using port `52444` to send a DNS resolution request to the DNS server (`dns.google.domain`) for `yummyrecipesforme.com`. The DNS server then responds with the IP address of the destination URL, `203.0.113.22`.

```text
14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http:
Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS
val 3302576859 ecr 0,nop,wscale 7], length 0

14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086:
Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss
65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0
```

The next section shows the source computer sending a TCP connection request (`Flags [S]`) from port `36086` to `yummyrecipesforme.com.http`. The `.http` suffix identifies HTTP traffic, which commonly uses port `80`. The server replies with `Flags [S.]`, acknowledging the connection request. This is part of the TCP three-way handshake.

TCP flag codes include:

* `Flags [S]` — Connection Start
* `Flags [.]` — Acknowledgment
* `Flags [F]` — Connection Finish
* `Flags [P]` — Data Push
* `Flags [R]` — Connection Reset

```text
14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http:
Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val
3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1
```

The log entry `HTTP: GET / HTTP/1.1` shows that the browser is requesting the webpage from `yummyrecipesforme.com` using the HTTP `GET` method and HTTP version 1.1. According to the incident investigation, the website then prompts the victim to download a malicious executable.

```text
14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A?
greatrecipesforme.com. (24)

14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899
1/0/0 A 192.0.2.172 (40)

14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http:
Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS
val 3302989649 ecr 0,nop,wscale 7], length 0

14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378:
Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss
65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0
```

A sudden change then appears in the logs. The source computer sends another DNS resolution request, this time for `greatrecipesforme.com`. The DNS server responds with the IP address `192.0.2.172`. The traffic then changes to a new HTTP connection between the source computer (`your.machine.56378`) and `greatrecipesforme.com.http`.

This indicates that the browser was redirected from the legitimate website to the spoofed or malicious website. The source port also changes from `36086` to `56378` for the new connection.

---

## Section 1: Identify the Network Protocols Involved

* **DNS (Domain Name System):** Resolves `yummyrecipesforme.com` and `greatrecipesforme.com` into their corresponding IP addresses.
* **TCP (Transmission Control Protocol):** Establishes the connection between the user's computer and the web server using the TCP handshake.
* **HTTP (Hypertext Transfer Protocol):** Used by the browser to request and receive the webpage over port `80`.

---

## Section 2: Documenting the Incident

The website was compromised after the attacker gained access to the administrative account through a **brute force attack**. The password was still set to the default password, and no controls were in place to prevent repeated login attempts.

After gaining access, the attacker modified the website's source code and inserted malicious JavaScript that prompted visitors to download an executable file disguised as a browser update.

The downloaded file contained a script that redirected the browser to `greatrecipesforme.com`. The tcpdump traffic confirms this behavior by showing a DNS request for the new domain followed by a TCP connection to its web server.

The attacker also changed the administrator password after modifying the website, preventing the legitimate owner from accessing the admin panel.

### Attack Flow

```text
Brute Force Attack
        ↓
Default Password Compromised
        ↓
Admin Panel Access
        ↓
Malicious JavaScript Added
        ↓
Victim Visits Website
        ↓
Malicious File Downloaded
        ↓
Browser Redirect
        ↓
greatrecipesforme.com
        ↓
Malware Infection
```

---

## Section 3: Recommending One Remediation for Brute Force Attacks

The recommended remediation is to implement **account lockout and login rate limiting**.

After a defined number of failed login attempts, the account should be temporarily locked or further attempts should be delayed. This prevents an attacker from repeatedly guessing passwords.

The organization should also remove all default passwords and use strong, unique administrator passwords.

---

## Conclusion

The tcpdump evidence shows the normal DNS, TCP, and HTTP communication with `yummyrecipesforme.com`, followed by a new DNS lookup and HTTP connection to `greatrecipesforme.com`.

This supports the conclusion that the compromised website redirected visitors to a malicious website after the attacker gained administrative access through a brute force attack.
