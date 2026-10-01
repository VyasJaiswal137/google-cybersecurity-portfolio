# Activity 2 — Risk Register: Commercial Bank Risk Assessment

## Overview

This activity focuses on performing a risk assessment for a commercial bank by evaluating vulnerabilities that commonly threaten business operations. A risk register is created to record each asset, the risk it faces, the vulnerability that enables the risk, and a calculated priority score.

The purpose of the risk register is to help a security team decide where to focus limited resources. Risks are scored using two factors: likelihood of occurrence and severity of impact. The two scores are multiplied to produce a priority value. Higher priority values indicate risks that require attention sooner.

This assessment follows the risk assessment principles outlined in the NIST Cybersecurity Framework (CSF), which treats risk identification as a foundational step before protective controls can be selected.

---

## Operational Environment

The bank operates under the following conditions:

- Located in a **coastal area with low crime rates**
- **100 on-premises employees** and **20 remote employees**
- Customer base includes **2,000 individual accounts** and **200 commercial accounts**
- Services are marketed by a **professional sports team** and **ten local businesses**
- Strict financial regulations apply, including requirements to maintain sufficient daily cash reserves for Federal Reserve compliance

These environmental details influence both the likelihood and severity of each risk. For example, the low crime rate reduces the likelihood of physical theft, while the coastal location increases exposure to natural disasters. The large customer base and regulatory obligations raise the severity of any data exposure.

---

## Risk Register

| Asset | Risk(s) | Description | Likelihood | Severity | Priority |
|---|---|---|---|---|---|
| Funds | Business email compromise | An employee is tricked into sharing confidential information. | 2 | 3 | 6 |
| Compromised user database | Customer data is poorly encrypted | Weak encryption exposes customer records if the database is accessed. | 3 | 3 | 9 |
| Financial records leak | Publicly accessible backup server | A database server of backed-up data is reachable from the public internet. | 3 | 3 | 9 |
| Theft | Safe left unlocked | Physical cash and valuables are exposed to insider or outsider theft. | 1 | 3 | 3 |
| Supply chain disruption | Delivery delays due to natural disasters | Coastal storms interrupt the delivery of cash, equipment, or supplies. | 2 | 2 | 4 |

### Scoring Scale

- **Likelihood:** 1 = Rare, 2 = Likely, 3 = Certain
- **Severity:** 1 = Low, 2 = Moderate, 3 = Catastrophic
- **Priority:** Likelihood × Severity

### Priority Bands

| Score | Priority Band |
|---|---|
| 1–2 | Low |
| 3–4 | Moderate |
| 6 | High |
| 9 | Critical |

---

## Scoring Rationale

### 1. Business Email Compromise (Likelihood 2 × Severity 3 = 6)

- **Likelihood: 2 (Likely).** Social engineering is one of the most common attack methods against financial institutions. With 120 total employees, several of whom work remotely, there are many entry points. However, banks typically provide awareness training and email filtering, which keeps the likelihood from reaching the highest level.
- **Severity: 3 (Catastrophic).** A successful compromise can lead to direct financial loss, unauthorized transfers, and regulatory penalties. Because the bank must maintain daily cash reserves, any loss of funds has immediate operational consequences.

### 2. Compromised User Database — Poor Encryption (Likelihood 3 × Severity 3 = 9)

- **Likelihood: 3 (Certain).** Poor encryption is an existing weakness, not a hypothetical one. Once an attacker gains any level of access, the data is effectively readable. This makes exploitation highly probable.
- **Severity: 3 (Catastrophic).** The database holds records for 2,200 accounts. Exposure would violate financial regulations, trigger notification requirements, and damage customer trust. The regulatory and reputational impact is severe.

### 3. Financial Records Leak — Publicly Accessible Backup Server (Likelihood 3 × Severity 3 = 9)

- **Likelihood: 3 (Certain).** A publicly accessible server is continuously exposed to internet-wide scanning. Automated tools can detect and attempt to access it without any targeted effort.
- **Severity: 3 (Catastrophic).** Backup data often contains complete copies of financial records. A leak would expose sensitive information, breach regulatory requirements, and create legal liability.

### 4. Theft — Safe Left Unlocked (Likelihood 1 × Severity 3 = 3)

- **Likelihood: 1 (Rare).** The bank is in a low-crime area. Physical access controls and staffing further reduce the chance of theft. The unlocked safe is a weakness, but the surrounding environment lowers the probability of exploitation.
- **Severity: 3 (Catastrophic).** If theft occurs, the loss of cash directly conflicts with Federal Reserve reserve requirements. The financial and compliance impact is high.

### 5. Supply Chain Disruption — Natural Disasters (Likelihood 2 × Severity 2 = 4)

- **Likelihood: 2 (Likely).** The coastal location increases exposure to storms and flooding. Such events are not constant, but they are plausible within a normal operating year.
- **Severity: 2 (Moderate).** Delivery delays disrupt operations but do not directly compromise customer data or funds. The impact is operational rather than catastrophic.

---

## Priority Ranking

| Rank | Asset | Priority Score | Band |
|---|---|---|---|
| 1 (tie) | Compromised user database | 9 | Critical |
| 1 (tie) | Financial records leak | 9 | Critical |
| 3 | Funds (business email compromise) | 6 | High |
| 4 | Supply chain disruption | 4 | Moderate |
| 5 | Theft  | 3 | Moderate |

### Recommended Focus

- **Immediate action:** The two critical risks share a common theme — exposed data. Encryption must be strengthened, and the publicly accessible backup server must be moved behind proper access controls.
- **Short-term action:** Business email compromise should be addressed through continued awareness training, multi-factor authentication, and email gateway filtering.
- **Ongoing monitoring:** Supply chain disruption is best handled through contingency planning and vendor diversification.
- **Lower priority:** The unlocked safe is a policy issue that can be corrected through procedural enforcement rather than technical investment.

---

## Notes: How Security Events Are Possible in This Environment

The bank's operating environment creates conditions where security events can occur despite the low crime rate:

1. **Remote workforce expands the attack surface.** Twenty remote employees connect from outside the on-premises network. Credentials can be phished, devices can be lost, and home networks may lack the protections of the bank's internal environment.
2. **Customer data is a high-value target.** With 2,200 accounts and strict regulatory requirements, the bank holds information that attackers find valuable. The presence of poorly encrypted data turns a potential breach into a likely one.
3. **Public exposure of backup infrastructure.** A publicly accessible backup server removes the need for an attacker to breach the perimeter. Automated scanning finds such systems quickly.
4. **Human error remains the weakest link.** Business email compromise depends on an employee being tricked. No amount of perimeter security prevents a user from voluntarily sharing information.
5. **Physical and environmental risks persist.** Even with low crime, an unlocked safe and a coastal location create opportunities for loss. Physical security and disaster planning are part of the same risk picture as cyber threats.
6. **Third-party dependencies add indirect risk.** Marketing relationships with a sports team and ten local businesses mean the bank's reputation and operations are connected to partners who may not follow the same security standards.

---

## Key Takeaways

- A risk register converts a list of concerns into a prioritized action plan by scoring likelihood and severity.
- Risks that combine high likelihood with high severity (such as poor encryption and public exposure) demand immediate attention.
- Environmental context matters. A low crime rate lowers the likelihood of theft but does not eliminate it. A coastal location raises the likelihood of supply chain disruption.
- Regulatory obligations increase severity for any risk involving customer data or cash reserves.
- Risk assessment is a judgment exercise. Different analysts may assign different scores, but the reasoning behind each score must be defensible and tied to the scenario.

