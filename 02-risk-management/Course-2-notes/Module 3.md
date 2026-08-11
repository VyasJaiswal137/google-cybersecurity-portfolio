# Course 2 - Module 3: Security Tools, Playbooks, and SIEM Dashboards

## The Evolution of SIEM & Automation

### Current vs. Future SIEM Solutions
* **Current SIEM Tools:** Collect and analyze log data to offer real-time tracking, risk identification, and customizable monitoring dashboards. Currently, they rely heavily on manual human interaction to perform detailed analysis of security events.
* **Cloud Solutions:** Modern SIEM systems are increasingly cloud-based:
  * **Cloud-Hosted:** Operated and maintained by external vendors on their infrastructure; accessed over the internet. Ideal for organizations seeking to avoid internal infrastructure maintenance.
  * **Cloud-Native:** Built specifically to leverage cloud computing scalability, flexibility, and high availability.
* **Emerging Enhancements:** As the Internet of Things (IoT) expands the corporate attack surface and data volume, SIEM platforms are integrating Artificial Intelligence (AI) and Machine Learning (ML). These capabilities improve threat terminology recognition, log data storage, and dashboard visualizations.

### SOAR & Integration
* **Security Orchestration, Automation, and Response (SOAR):** A suite of tools and workflows designed to automate repetitive security responses flagged by SIEM or Managed Detection and Response (MDR) services.
* **Operational Impact:** Automating routine tasks (e.g., auto-locking accounts after multiple failed login attempts) reduces manual intervention, allowing security analysts to focus on complex, non-automatable incidents.
* **Interoperability:** Platforms continue moving toward seamless cross-system communication and data sharing across interconnected security tools.

---

## Open-Source vs. Proprietary Tools

| Feature | Open-Source Tools | Proprietary Tools |
| :--- | :--- | :--- |
| **Development** | Built collaboratively by the public community; source code is freely available to view, modify, and distribute. | Developed and owned exclusively by a single vendor or enterprise. Source code is closed and protected. |
| **Cost & Training** | Generally free to use, with open documentation, community guides, and training resources. | Usage licensing, maintenance updates, and formal training typically require paid fees. |
| **Flexibility** | Highly customizable; allows teams to build new extensions or tailored services. | Customization options are generally restricted to standard features exposed by the vendor. |
| **Security Misconceptions** | Widely scrutinized source code allows global security professionals to identify and patch bugs rapidly, resisting malicious manipulation. | Code modifications depend on the software vendor's patch release schedules. |
| **Examples** | **Linux:** Open-source operating system providing command-line system controls.<br>**Suricata:** Open-source network analysis and threat detection engine developed by OISF. | **Splunk®:** Enterprise and Cloud SIEM solution.<br>**Chronicle:** Cloud-native SIEM developed by Google. |

---

## Playbooks (Runbooks)

* **Definition:** Detailed incident response procedures providing step-by-step instructions (often structured via flowcharts or tables) to guide standardized response actions.
* **Role with SIEM:** Guides analysts through specific steps when a SIEM dashboard triggers an alert (e.g., handling flagged unusual user activity).
* **Role with SOAR:** Complements automated workflows by directing analyst actions once automated triggers execute (e.g., resolving account lockouts after SOAR automatically blocks a user).

---

## SIEM Tools & Dashboard Functions

### Splunk Dashboards

* **Security Posture Dashboard:** Designed for Security Operations Center (SOC) teams to monitor notable security events, trends, and real-time infrastructure performance over the past 24 hours.
* **Executive Summary Dashboard:** Tracks high-level organizational health and long-term security metrics to report trends to executive stakeholders.
* **Incident Review Dashboard:** Visualizes incident timelines and highlights high-risk events requiring immediate analyst investigation.
* **Risk Analysis Dashboard:** Monitors individual risk objects (e.g., users, workstations, IP addresses) to identify anomalous behaviors, such as off-hours logins or unexpected spikes in network traffic.

### Google Chronicle Dashboards

* **Enterprise Insights Dashboard:** Highlights recent security alerts and identifies Indicators of Compromise (IOCs), tagging events with severity levels and threat confidence scores.
* **Data Ingestion and Health Dashboard:** Tracks log processing rates, success metrics, and active log source configurations to ensure data flows reliably into the SIEM.
* **IOC Matches Dashboard:** Tracks domain name, IP address, and device threat indicators over time to help security teams prioritize high-impact risks.
* **Main Dashboard:** Displays high-level summaries of ingested log volume, triggering alerts, and historical event activity timelines across all systems.
* **Rule Detections Dashboard:** Tracks event metrics for triggered detection rules (e.g., opening malicious attachments) to identify high-frequency threat trends.
* **User Sign In Overview Dashboard:** Monitors global user access patterns and authentication logs to flag multi-location sign-ins or unauthorized access attempts.