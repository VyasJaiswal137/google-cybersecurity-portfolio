# NIST Cybersecurity Framework 2.0 — DoS Incident Analysis

## Summary

This report analyzes a **Denial-of-Service (DoS) attack** against a multimedia company providing web design, graphic design, and social media marketing services.

The attack caused internal network services to become unavailable for approximately **two hours** after the network was overwhelmed by a flood of ICMP packets. Investigation determined that the attacker exploited an **unconfigured firewall**, allowing excessive ICMP traffic to enter the network and consume network resources.

The incident response team initially:

* Blocked incoming ICMP traffic.
* Took non-critical services offline.
* Restored critical services.

Following the incident, the security team implemented:

* ICMP rate limiting.
* Source IP verification and anti-spoofing controls.
* Network traffic monitoring.
* IDS/IPS filtering for suspicious ICMP traffic.

This report applies **NIST Cybersecurity Framework (CSF) 2.0** to identify additional improvements across its six Functions: **Govern, Identify, Protect, Detect, Respond, and Recover**.

---

# Govern

The **Govern** Function establishes cybersecurity policies, responsibilities, risk tolerance, and organizational oversight.

The incident revealed governance weaknesses around firewall configuration, security validation, and network availability.

### Key Risks

* Inadequate firewall configuration standards.
* Lack of formal firewall change management.
* Insufficient security auditing.
* Undefined network availability requirements.
* Limited ownership of network security risks.

### Recommended Improvements

* Establish formal firewall and network security policies.
* Add DoS/DDoS risks to the organizational risk register.
* Assign clear ownership for firewall security and monitoring.
* Require security approval for firewall changes.
* Conduct regular firewall and network configuration audits.
* Define acceptable downtime and recovery requirements.
* Track metrics such as detection time, response time, and service availability.

**Objective:** Align cybersecurity controls with business requirements and establish accountability for network security.

---

# Identify

The **Identify** Function provides visibility into assets, business processes, people, and cybersecurity risks.

## Technology and Assets

The organization should maintain an inventory of:

* Firewalls, routers, and switches.
* Servers and workstations.
* Operating systems and applications.
* IDS/IPS and monitoring systems.
* Cloud and Internet-facing services.
* Network segments and critical infrastructure.

The attack path was:

**External attacker → Internet → Firewall → Internal Network → Network Services → Legitimate Users**

The firewall was the primary security control that failed to adequately restrict the attack traffic.

## Business Impact

The outage potentially affected:

* Web design operations.
* Graphic design workflows.
* Social media marketing.
* Internal communication.
* File and application access.
* Customer support.

Network availability should therefore be considered a **business-critical security requirement**.

## People

Administrative access should be limited to authorized personnel such as:

* Network administrators.
* Security analysts.
* IT administrators.
* Incident response personnel.

Access should follow **least privilege**, strong authentication, and centralized logging.

### Primary Risk

> An improperly configured network perimeter can allow malicious traffic to consume network resources and disrupt critical business services.

---

# Protect

The **Protect** Function establishes safeguards to reduce the likelihood and impact of attacks.

## Access and Firewall Controls

The organization should:

* Use a default-deny approach for unnecessary inbound traffic.
* Permit only required services.
* Rate-limit incoming ICMP traffic.
* Validate source addresses and implement anti-spoofing.
* Restrict administrative access.
* Use MFA for privileged accounts where supported.
* Log firewall and administrative activity.
* Regularly review and remove obsolete firewall rules.

## Network Segmentation

Critical systems should be separated from general user networks.

Recommended segments include:

* User networks.
* Server networks.
* Management networks.
* Security infrastructure.
* Guest networks.
* Public-facing services.

Segmentation limits the potential impact of future attacks.

## Training and Maintenance

Security and IT personnel should receive training on:

* Firewall configuration.
* DoS/DDoS attacks.
* IP spoofing.
* IDS/IPS.
* Network monitoring.
* Incident response.

Network devices, firewalls, operating systems, and security tools should also follow a formal **patch and maintenance process**.

## Protective Technology

A layered architecture should include:

* Next-generation firewall.
* IDS/IPS.
* Network monitoring.
* SIEM.
* Endpoint security.
* Network segmentation.
* DDoS protection where appropriate.
* Centralized logging.

---

# Detect

The **Detect** Function improves the organization's ability to identify attacks quickly.

## Monitoring

The organization should establish normal network traffic baselines and monitor for:

* Sudden ICMP spikes.
* Unusual packet rates.
* Large volumes from individual sources.
* Spoofed or suspicious addresses.
* Unexpected inbound traffic.
* Network bandwidth saturation.
* Increased firewall-deny events.
* IDS/IPS alerts.
* Service availability problems.

## SIEM

Firewall, IDS/IPS, authentication, server, and network logs should be centralized in a **SIEM**.

Example detection rule:

> **High ICMP volume + multiple external sources + reduced service availability = potential DoS/DDoS incident**

## Detection Workflow

1. Alert is generated.
2. Analyst validates the event.
3. Traffic sources and destinations are investigated.
4. Attack volume and patterns are analyzed.
5. Severity is determined.
6. Incident response procedures are initiated if necessary.

The goal is to improve both **detection speed and accuracy**.

---

# Respond

The **Respond** Function defines how the organization contains, analyzes, and communicates during an incident.

## Response Planning

Create a dedicated **DoS/DDoS Incident Response Playbook** covering:

* Detection criteria.
* Severity classification.
* Escalation procedures.
* Firewall response actions.
* Traffic-blocking procedures.
* Evidence preservation.
* Service prioritization.
* Communication.
* Recovery.
* Post-incident review.

## Analysis

Analysts should determine:

* Attack start and end times.
* Source IP addresses and networks.
* Packet volume and characteristics.
* Affected systems and services.
* Firewall and IDS/IPS activity.
* Whether source addresses were spoofed.
* Business impact.

Relevant logs should be preserved for investigation.

## Mitigation

Potential actions include:

1. Confirm the attack.
2. Identify affected systems.
3. Apply ICMP rate limiting.
4. Block malicious traffic where appropriate.
5. Enable anti-spoofing and IDS/IPS controls.
6. Contact the ISP for upstream filtering if required.
7. Isolate non-critical services.
8. Prioritize critical services.
9. Continue monitoring.

## Improvements

Conduct a **lessons-learned review** after significant incidents.

Questions should include:

* What happened?
* Why did it happen?
* Which controls failed?
* Which controls worked?
* How quickly was the incident detected?
* How quickly was it contained?
* What services were affected?
* What should change?

Findings should be added to the risk register and security improvement plan.

---

# Recover

The **Recover** Function ensures affected systems and services are restored safely and efficiently.

## Recovery Process

1. Confirm malicious traffic has been contained.
2. Verify firewall and IDS/IPS configurations.
3. Confirm network stability.
4. Restore critical services.
5. Validate system functionality.
6. Restore non-critical services according to priority.
7. Monitor for recurring attacks.
8. Confirm normal operations.
9. Close the incident after validation.

## Recovery Planning

The organization should establish:

* **Recovery Time Objectives (RTOs)**.
* **Recovery Point Objectives (RPOs)**.
* Service restoration priorities.
* System dependencies.
* Recovery responsibilities.
* Communication procedures.

## Resilience Improvements

Recommended improvements include:

* Network configuration backups.
* Redundant infrastructure where appropriate.
* Tested recovery procedures.
* Alternative communication channels.
* Service redundancy.
* ISP/DDoS mitigation options.
* Regular disaster recovery exercises.
* Periodic restoration testing.

---

# Security Improvement Priorities

| Priority | Improvement                                   | CSF Function       |
| -------- | --------------------------------------------- | ------------------ |
| Critical | Audit firewall configurations                 | Identify / Protect |
| Critical | Maintain ICMP rate limiting and anti-spoofing | Protect            |
| Critical | Implement centralized security monitoring     | Detect             |
| Critical | Create DoS/DDoS response playbook             | Respond            |
| High     | Integrate firewall and IDS/IPS with SIEM      | Detect             |
| High     | Implement network segmentation                | Protect            |
| High     | Establish firewall change management          | Govern / Protect   |
| High     | Define RTOs and recovery priorities           | Govern / Recover   |
| Medium   | Conduct regular network security audits       | Identify           |
| Medium   | Perform incident response exercises           | Respond / Recover  |
| Medium   | Review ISP/DDoS mitigation capabilities       | Govern / Protect   |

---

# Risk Prioritization

| Risk                          | Likelihood | Impact | Priority | Treatment                           |
| ----------------------------- | ---------- | ------ | -------- | ----------------------------------- |
| Firewall misconfiguration     | Medium     | High   | High     | Audits and change control           |
| ICMP/DoS attack               | High       | High   | Critical | Rate limiting, IDS/IPS, monitoring  |
| IP spoofing                   | Medium     | High   | High     | Source validation and anti-spoofing |
| Monitoring gaps               | Medium     | High   | High     | SIEM and continuous monitoring      |
| Network segmentation weakness | Medium     | High   | High     | Network segmentation                |
| Slow incident response        | Medium     | High   | High     | Tested response playbook            |
| Inadequate recovery planning  | Medium     | High   | High     | RTO/RPO and recovery exercises      |

---

# Reflections / Notes

This incident demonstrates that cybersecurity requires more than deploying individual security technologies. An improperly configured firewall can become a significant vulnerability even when other security controls exist.

The key lesson is the importance of **defense in depth**. Firewall rules should be supported by IDS/IPS, network monitoring, SIEM, segmentation, incident response procedures, and recovery planning.

The incident also demonstrates that cybersecurity is directly connected to **business continuity**. The two-hour outage prevented employees from reliably accessing resources needed for normal operations, making network availability an important business risk.

Security configurations should therefore be continuously reviewed, tested, and audited. The organization should use this incident to improve both its technical controls and its processes.

---

# Conclusion

The ICMP flood exposed a weakness in the organization's network perimeter and demonstrated how a network-based attack can disrupt business operations when preventive and detective controls are insufficient.

Applying **NIST CSF 2.0** provides a structured approach for addressing the issue:

* **Govern** establishes accountability and cybersecurity risk management.
* **Identify** provides visibility into assets, processes, and vulnerabilities.
* **Protect** implements safeguards such as firewall controls, segmentation, and anti-spoofing.
* **Detect** improves visibility through monitoring, IDS/IPS, and SIEM.
* **Respond** provides structured procedures for containment and analysis.
* **Recover** ensures critical services can be restored efficiently.

The organization's long-term objective should be to move from **reactive incident handling toward continuous risk management and resilience**.

Regular audits, security testing, monitoring, incident response exercises, and recovery testing should be used to continuously improve the organization's security posture.

---

# References

1. National Institute of Standards and Technology. **The NIST Cybersecurity Framework (CSF) 2.0**. 2024.
   https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20

2. National Institute of Standards and Technology. **Cybersecurity Framework 2.0 FAQs**.
   https://www.nist.gov/cyberframework/faqs

3. National Institute of Standards and Technology. **NIST Cybersecurity Framework Resource Center**.
   https://www.nist.gov/cyberframework

4. National Institute of Standards and Technology. **NIST Releases Version 2.0 of Landmark Cybersecurity Framework**. 2024.
   https://www.nist.gov/news-events/news/2024/02/nist-releases-version-20-landmark-cybersecurity-framework
