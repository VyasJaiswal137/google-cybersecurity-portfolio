# Access Controls Worksheet — Incident Analysis

---

## Scenario Overview

A growing business experienced a security incident in which a deposit was nearly made to an unknown bank account. The finance manager confirmed the transaction was not a mistake, and the payment was fortunately stopped. The investigation focuses on reviewing the access log, identifying the possible threat actor, assessing the exploited access controls, and recommending mitigations to prevent future occurrences.

---

## Authorization / Authentication

| Note(s) | Issue(s) | Recommendation(s) |
| --- | --- | --- |
| **Objective:** List 1-2 pieces of information that can help identify the threat:<br><br>• **Who caused this incident?** The activity originated from the `Legal\Administrator` account, which is associated with the contractor Robert Taylor Jr.<br>• **When did it occur?** October 3, 2023, at 8:29:57 AM.<br>• **What device was used?** The event was logged on the computer named `Up2-NoGud` from the IP address `152.207.255.255`. | **Objective:** Based on the notes, list 1-2 authorization issues:<br><br>• **What level of access did the user have?** The user held `Admin` authorization. For a contractor in a legal role, this violates the principle of least privilege.<br>• **Should their account be active?** No. The employee directory lists an end date of December 27, 2019. The account should have been disabled long before the 2023 incident, indicating a severe failure in the offboarding process. | **Objective:** Make at least 1 recommendation that could prevent this kind of incident:<br><br>• **Technical/Managerial Controls:** Implement a rigid offboarding procedure that automatically revokes access and disables accounts on an employee's designated end date.<br>• **Operational Controls:** Enforce the principle of least privilege by regularly auditing user roles and removing `Admin` rights from contractors and employees who do not require them for their daily tasks. |

---

## Security Plan Snapshot

The following table illustrates how the recommended security controls align with the NIST Cybersecurity Framework (CSF).

| Function | Category | Subcategory | Reference(s) |
| --- | --- | --- | --- |
| Protect | PR.AC: Identity Management and Access Control | PR.AC-4: Access permissions and authorizations are managed, incorporating the principles of least privilege and separation of duties. | NIST SP 800-53: AC-6 |
| Protect | PR.AC: Identity Management and Access Control | PR.AC-1: Identities and credentials are issued, managed, verified, revoked, and audited for authorized devices, users, and processes. | NIST SP 800-53: AC-2 |