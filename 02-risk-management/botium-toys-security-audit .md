# Botium Toys: Security Audit & Risk Assessment Report [ Fictional Company ]

## Executive Summary
A security audit was carried out internally at Botium Toys in order to examine its present security position, to check how well it complies with the relevant regulatory frameworks (PCI DSS, GDPR, SOC 1/SOC 2), and to spot any operational vulnerabilities. 

The evaluation showed an overall Risk Score of 8 out of 10 (High Risk). Although Botium Toys has sufficient physical security and some basic perimeter defences (such as a firewall and antivirus software), the organisation has serious deficiencies in its access controls, lacks data encryption, has no backup procedures in place, and is not compliant with the major data privacy regulations.

---

## Audit Scope & Goals
**Scope:** The entire security infrastructure of Botium Toys, which includes the physical premises (such as the storefront, offices, and warehouse), the employee end-user devices, the internal network, the data storage and retention systems, the legacy software, and the customer data touchpoints.
* **Goals:** 
  1. Assess the current technical, administrative, and physical assets.
  2. Compare the operational vulnerabilities with the NIST Cybersecurity Framework (CSF).
  3. Checklists for full controls and compliance assessments.
  4. Develop a set of remediation strategies that are prioritized in order to enhance the overall security position.

---

## Current State Audit Findings

### 🔐 Access Control & User Rights
**Unrestricted Internal Access:** At present, all employees of Botium Toys are able to access data that is stored internally, this including sensitive customer cardholder data and Personally Identifiable Information / Sensitive PII (PII/SPII).
* **Lack of safeguards:** The principles related to access control, namely **Least Privilege** and **Separation of Duties**, have not been put into effect.
* **Poor password policies:** Although there is a basic password policy in place, the requirements it sets are very modest and do not meet the complexity standards required by modern security practices (for example, a minimum of 8 or more characters, the inclusion of special characters, both uppercase and lowercase letters, and numbers).
**No password management system is in place:** This results in productivity delays whenever employees or vendors ask IT for manual password resets.

### 🛡️ Data Protection & Systems Defense
* No encryption is employed to protect customer credit card data when it is being accepted, when it is being processed, when it is being transmitted, or when it is stored locally in the internal database.
* **Perimeter Defense:** The IT department keeps an active firewall which uses a ruleset that has been appropriately defined.
* **Endpoint Defense:** Antivirus software is installed on all endpoints and is regularly monitored by members of the IT staff.
* There is no Intrusion Detection System (IDS) in place for detecting unusual traffic or unauthorized network intrusions.
* **Legacy Systems:** Although outdated end-of-life legacy systems are monitored and maintained by manual means, they have no set schedule or standard operating procedures for intervention.

### 💾 Continuity, Integrity & Availability
* **Data Integrity and Availability:** The IT department has successfully put in place controls in order to ensure data integrity (i.e. accuracy and consistency) and system availability.
* There is a deficit in regard to Disaster Recovery: the company has no formal Disaster Recovery Plans (DRP) and is currently running without backups of its critical business data.

### 📜 Compliance & Regulatory Status
* **GDPR Notification Plan:** The IT department has set up a procedure so that E.U. customers are informed within 72 hours should there be a security breach.
The IT department has active and enforced privacy policies, processes, and documentation procedures.
* **Non-compliance with PCI DSS:** The failure to encrypt cardholder data and the fact that employees have unrestricted access give rise to substantial risks of not complying with PCI DSS.

### 🏢 Physical & Environmental Security
**Physical Controls:** The main offices, storefronts, and product warehouses are adequately secured by means of physical locks.
**Surveillance:** The use of Closed-Circuit Television (CCTV) is current and is in operation throughout the facilities.
**Environmental Safety:** The fire detection and sprinkler suppression systems in operation on site are fully functional.

---

## Controls Assessment Checklist

| Control Name | Category | In Place? | Risk / Impact |
| :--- | :--- | :---: | :--- |
| Least Privilege | Administrative | No | High — unrestricted data access across all staff. |
| Disaster Recovery Plans | Administrative | No | High — there are no recovery procedures after an incident. |
| Password Policies | Administrative | Yes | Medium — a policy is in place, but the requirements are weak. |
| Separation of Duties | Administrative | No | High — there is an increased risk of an insider threat or abuse of privileges. |
| Firewall | Technical | Yes | Low — since it is properly filtering unwanted traffic. |
| Intrusion Detection System (IDS) | Technical | No | High — fails to detect active network breaches. |
| Data Backups | Technical | No | High — there is a critical risk to operational data during a ransomware attack or outage. |
| Antivirus Software | Technical | Yes | Low — It is regularly monitored on a per-endpoint basis. |
| Legacy Systems Maintenance | Technical | Yes | Medium — Manually monitored, but with no regular schedule. |
| Data Encryption | Technical | No | Critical — Personal identifiable information and credit card data are processed and stored in plain text. |
| Password Management System | Technical | No | Medium, since it leads to delays in IT ticketing and results in weak credentials. |
| Physical Locks | Physical | Yes | Low — the security of offices, storefronts, and warehouses. |
| CCTV Surveillance | Physical | Yes | Low – the facilities are covered by active camera systems. |
| Fire detection and prevention | Physical | Yes | Low — the alarm systems and sprinklers are functioning. |

---

## Compliance Assessment Checklist

### The Payment Card Industry Data Security Standard (PCI DSS)
[ ] **Authorized Access Only:** ❌ *Failed* — At present, all employees have access to cardholder data.
[ ] **Secure Storage/Processing Environment:** ❌ *Failed* — The data is stored locally within an unencrypted internal network.
[ ] **Data Encryption:** ❌ *Failed* — There are no encryption protocols in operation at any of the points where the data is processed.
[ ] **Secure Password Policies:** ❌ *Failed* — the requirements for passwords are weak and there is no central management.

### 2. The General Data Protection Regulation (GDPR)
[ ] **EU customer data privacy:** ❌ *Failed* — unencrypted PII/SPII is accessible throughout the workforce.
[x] **72-Hour Breach Notification:** ✅ The response protocol has been activated for notifications to E.U. customers.
[ ] **Data Classification and Inventory:** ❌ *Failed* — the asset management is incomplete and the risk impact has not been mapped.
[x] **Privacy Policies Enforced:** ✅ *Passed* — The internal privacy procedures have been put into effect by IT.

### 3. System and organizational controls (SOC 1 / SOC 2)
[ ] The user access policies have not been established ❌ (failure) – the principles of least privilege and separation of duties are absent.
[ ] **Sensitive Data Confidentiality:** ❌ *Failed* — there is no encryption of PII/SPII and there is no role access control.
* [x] **Data Integrity Ensured:** *Passed.* Integrated controls keep data correct and checked.
[x] **Data Availability Guaranteed:** ✅ *Completed* — The system's uptime and the availability of its resources are actively managed.

---

## Strategic Recommendations

1. **Immediately enforce access controls (high priority):** Introduce Role-Based Access Control (RBAC) in order to ensure the principle of least privilege and separation of duties. Access to cardholder data and personal identifiable information should be strictly limited to authorized roles.
2. **Implement end-to-end encryption (high priority):** Encrypt data at rest using AES-256 and use TLS 1.3 to encrypt the data in transit at all points involved in credit card transaction processing.
3. **Set up data backups and a Disaster Recovery Plan (a high priority):** Arrange for automated daily off-site backups and prepare a formal Disaster Recovery Plan in order to ensure business continuity.
4. **Deploy a centralised password management system and a network intrusion detection system (medium priority):** Introduce an enterprise password manager to enforce strict requirements for passphrases and install a network intrusion detection system to detect malicious traffic.
5. **Schedule legacy maintenance (low priority):** Set up a structured maintenance period for legacy end-of-life systems once a week or monthly.
