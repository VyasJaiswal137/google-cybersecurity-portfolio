# Module 2 - Security Controls, Encryption, and Access Management

---

## 1. The Principle of Least Privilege

The principle of least privilege (PoLP) is a foundational security concept where users are granted only the minimum level of access and authorization required to complete their tasks. This control directly supports the confidentiality, integrity, and availability (CIA) triad by limiting access to sensitive information, reducing the chance of accidental data loss, and supporting system monitoring.

### Determining Access and Authorization

To implement least privilege, two questions must be answered: Who is the user, and how much access do they need? Users generally fall into specific account types:
- **Guest accounts:** Provided to external users needing temporary internal network access.
- **User accounts:** Assigned to staff based on job duties.
- **Service accounts:** Granted to applications or software interacting with other systems.
- **Privileged accounts:** Hold elevated permissions or administrative access.

### Auditing Account Privileges

Because access needs change over time, routine auditing is essential to prevent privilege creep. Three common approaches are used:
- **Usage audits:** Review what resources an account is accessing to ensure adherence to policy.
- **Privilege audits:** Assess whether a user's current role aligns with the resources they can access.
- **Account change audits:** Review directory service logs to ensure all account modifications are made by authorized users.

---

## 2. The Data Lifecycle and Governance

Data vulnerabilities are often mapped using the data lifecycle model, which consists of five stages: **Collect, Store, Use, Archive, and Destroy**. Protecting data requires maintaining accessibility and recoverability throughout this flow.

To manage this, organizations implement data governance—a set of processes defining how information is managed. This typically assigns roles:
- **Data owner:** Decides who can access, edit, use, or destroy their information.
- **Data custodian:** Responsible for the safe handling, transport, and storage of information.
- **Data steward:** Maintains and implements the governance policies.

### Legally Protected Information

Regulatory agencies require organizations to protect specific types of data by default:
- **PII (Personally Identifiable Information):** Any information used to infer an individual's identity.
- **PHI (Protected Health Information):** Information relating to a person's physical or mental health.
- **SPII (Sensitive Personally Identifiable Information):** PII requiring stricter handling, such as bank account numbers or login credentials.

---

## 3. Information Privacy and Compliance

While often used interchangeably, information privacy and information security serve distinct functions. Privacy provides people with control over their personal information, while security protects those choices by keeping the data safe from threats.

### Notable Privacy Regulations

Compliance with industry regulations is crucial. Three influential examples include:
- **GDPR (General Data Protection Regulation):** EU regulation giving data owners total control over their personal information, applying to any business handling EU citizens' data.
- **PCI DSS (Payment Card Industry Data Security Standard):** Security standards aimed at securing credit and debit card transactions.
- **HIPAA (Health Insurance Portability and Accountability Act):** U.S. law requiring the protection of sensitive patient health information.

### Audits and Assessments

Compliance is a continual process. **Security audits** review controls and policies against a set of expectations (often annually), while **security assessments** check how resilient current implementations are against threats (typically every three to six months).

---

## 4. Symmetric and Asymmetric Encryption

Encryption converts readable data into an encoded format to prevent unintended access. There are two main types:
- **Symmetric Encryption:** Uses a single secret key for both encryption and decryption. It is faster but requires secure key exchange.
- **Asymmetric Encryption:** Uses a public key to encrypt data and a private key to decrypt it. It is slower but solves the key exchange problem.

```text
Symmetric:  [Plaintext] ──(Secret Key)──► [Ciphertext] ──(Secret Key)──► [Plaintext]

Asymmetric: [Plaintext] ──(Public Key)──► [Ciphertext] ──(Private Key)──► [Plaintext]
```

### Approved Algorithms

Longer key lengths are more secure against brute force attacks but result in slower processing times. 
- **Symmetric:** Triple DES (192-bit) and AES (128, 192, or 256-bit).
- **Asymmetric:** RSA (1,024, 2,048, or 4,096-bit) and DSA (2,048-bit).

According to **Kerckhoff's principle**, a cryptographic system must remain secure even if all details of the algorithm (except the private key) are public knowledge.

---

## 5. The Evolution of Hash Functions

Hash functions are algorithms that convert data into a unique, fixed-size value (a digest) that cannot be decrypted. They are essential for verifying data integrity and secure authentication.

- **MD5 (Message Digest 5):** An early hash function that creates a 128-bit value (32 characters). Because it has a finite output limit, it is vulnerable to **hash collisions** (where different inputs produce the same hash).
- **SHA (Secure Hashing Algorithms):** Developed to avoid collisions, this family includes SHA-1, SHA-224, SHA-256, SHA-384, and SHA-512, with the numbers indicating the bit size.

### Secure Password Storage

If a database is breached, plaintext passwords are compromised. Hashing helps, but attackers can use a **rainbow table** (a file of pre-generated hashes and their plaintext matches) to crack them. 

To prevent this, **salting** is used. A salt is a random string of characters added to data before hashing. This ensures that identical passwords produce entirely different hashes, rendering rainbow tables ineffective.

---

## 6. Authentication and Identity Management

### SSO and MFA

- **Single Sign-On (SSO):** Combines multiple logins into one, improving user experience, lowering costs, and reducing attack vectors. It relies on protocols like LDAP (on-premises) and SAML (cloud) to exchange encrypted access tokens.
- **Multi-Factor Authentication (MFA):** Requires two or more forms of verification to access a system. Factors include something the user *knows* (password), *has* (OTP), or *is* (fingerprint).

### Identity and Access Management (IAM)

IAM is a collection of processes and technologies designed to manage digital identities. It relies on **user provisioning** (creating digital identities) and **deprovisioning** (removing access rights when no longer needed). 

IAM handles authorization through three common frameworks:
- **Mandatory Access Control (MAC):** The strictest framework, based on a need-to-know basis, granting access manually through a central authority (e.g., military).
- **Discretionary Access Control (DAC):** The data owner decides the appropriate levels of access (e.g., sharing a Google Drive file).
- **Role-Based Access Control (RBAC):** Authorization is determined by the user's role within the organization.

Both IAM and the AAA (Authentication, Authorization, and Accounting) framework ensure the right user is granted access to the right resources at the right time for the right reasons.