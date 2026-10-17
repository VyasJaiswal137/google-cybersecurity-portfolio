# Data Leak Worksheet — Completed Analysis

---

## Incident Summary

An educational technology company suffered a leak of internal business plans after an employee accidentally shared a confidential folder with an external business partner. The folder had been created for a sales meeting and contained unannounced product files, customer analytics, and promotional materials. Access was granted to the sales team during the meeting but was never revoked afterward. A sales representative later intended to share only the promotional materials with a business partner, but shared a link to the entire internal folder instead. The partner assumed the link contained promotional content and posted it on the company’s social media page.

---

## Control: Least Privilege

Least privilege means granting users only the access necessary to complete their assigned tasks, for only as long as it is needed. In this incident, access was broader and longer-lasting than the task required.

---

## Issue(s): What factors contributed to the information leak?

- The manager shared access to the internal folder with the entire sales team instead of limiting access to individuals with a specific need.
- Access was not revoked after the meeting, so permissions remained active after the business need had passed.
- The warning to wait for approval was verbal only and was not enforced through technical controls.
- The folder mixed internal-only product files, customer analytics, and promotional materials, increasing the impact of a single mistaken link.
- The sales representative was able to share an internal folder link externally without an approval step or link restriction.
- The external partner was able to post the link publicly, and no monitoring or data loss prevention control detected or blocked the exposure.

---

## Review: What does NIST SP 800-53: AC-6 address?

NIST SP 800-53: AC-6 addresses the principle of least privilege. It calls for organizations to allow only authorized access that is necessary for assigned tasks, restrict access to privileged functions, review privileges regularly, and enforce need-to-know access. The control is intended to reduce both accidental exposure and malicious misuse by keeping permissions as limited as possible.

---

## Recommendation(s): How might the principle of least privilege be improved at the company?

- Separate internal-only documents, customer analytics, and promotional materials into distinct folders with different access rules.
- Grant folder access by role or project, using just-in-time access that expires automatically after a meeting or task.
- Revoke meeting-based access immediately after the meeting and require a new request for future access.
- Default to denying external sharing, and require approval before any internal link can be shared outside the company.
- Use expiring, restricted links for external partners and disable public posting or forwarding where possible.
- Apply data loss prevention alerts for internal-only files shared externally.
- Conduct periodic access reviews and require managers to confirm that permissions are still necessary.
- Provide scenario-based training on safe link sharing and require confirmation before external sharing.

---

## Justification: How might these improvements address the issues?

Separating folders by sensitivity reduces the chance that a promotional link and an internal folder link are confused, and it limits the damage if a mistake occurs. Expiring and just-in-time access prevents permissions from lingering after a meeting. External-sharing approvals and restricted links stop internal folders from being posted publicly. Data loss prevention alerts and access reviews provide detection and accountability. Together, these measures enforce need-to-know access, reduce the blast radius of accidental sharing, and support the NIST CSF outcome for protections against data leaks.

---

## Security Plan Snapshot

| Function | Category | Subcategory | Reference(s) |
| --- | --- | --- | --- |
| Protect | PR.DS: Data security | PR.DS-5: Protections against data leaks | NIST SP 800-53: AC-6 |

Note: References are commonly hyperlinked to the guidelines or regulations they relate to, making it easier to understand how a control should be implemented. Multiple sources may appear in the references column.