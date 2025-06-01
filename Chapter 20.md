# Chapter 20: Network Security Concepts

## Network+ Exam Objectives Covered
- Logical security
- Encryption (data in transit, at rest)
- Certificates & PKI
- Self-signed certs
- IAM (Authentication, MFA, SSO)
- RADIUS, LDAP, SAML, TACACS+
- Time-based authentication
- Authorization, Least Privilege, RBAC
- Risk, Vulnerability, Exploit, Threat
- CIA triad (Confidentiality, Integrity, Availability)
- Audits & regulatory compliance (PCI DSS, GDPR)
- Data locality

---

## Why Network Security Matters

Modern networks are exposed to the Internet and a wider threat landscape. Admins must secure data against both external and internal threats, and understand core security terms and concepts. Many organizations must meet strict security and privacy regulations.

---

## Common Security Terminology

### Threats and Risk

- **Threat:** A potential danger (malware, theft, outage, etc).
- **Risk:** The likelihood a threat will actually impact you.

**Types:**
- *External threats*: Attackers, Internet risks, DoS, malware. Mitigate with firewalls, backups, antimalware.
- *Internal threats*: Insiders, disgruntled staff, accidental leaks. Harder to defend—mitigate with policy, access controls, training.
- *Unintentional threats*: Mistakes, misconfigurations, leaked passwords.

### Vulnerability

- A weakness that can be exploited (unpatched software, unlocked doors, misconfigured services).
- **CVE** (Common Vulnerabilities and Exposures): A global ID system for public vulnerabilities (e.g., CVE-2020-17084).
- **Zero-day:** A vulnerability not yet patched or even known; extremely dangerous.

### Exploit

- A method or code that takes advantage of a vulnerability.
- *Zero-day exploit*: Attack launched before a patch exists.

---

## CIA Triad

Security is built on three pillars:

- **Confidentiality:** Only authorized users can access data.
  - Examples: Encryption, authentication, access control.
- **Integrity:** Data is accurate and unaltered.
  - Examples: Hashes, digital signatures, checksums.
- **Availability:** Data/systems are up and accessible when needed.
  - Examples: Backups, redundancy, high-availability systems.

---

## Encryption

**Purpose:** Protect data confidentiality and integrity, both "in transit" and "at rest."

- **Data in Transit:** Data moving across a network (HTTPS, VPNs). *Always encrypt!*
- **Data at Rest:** Data stored on disk (databases, backups, laptops).
- **Data in Use:** Data in RAM or temporary files (less commonly regulated).

### Types of Encryption

- **Symmetrical:** Same key encrypts and decrypts. Fast, but risky if key is leaked.
- **Asymmetrical:** Public/private key pairs (RSA). More secure for sharing, used in PKI.

---

## Certificates and Public Key Infrastructure (PKI)

**Certificates** authenticate users, servers, and encrypt communications (HTTPS, email, etc).

### PKI Components

- **Certificate Authority (CA):** Issues/validates certs, manages keys.
- **AIA:** Where public keys are published (URL/file share).
- **Enrollment Policy:** What users/devices must do to get a cert.
- **Key Pair:** Public/private keys used for encryption or signing.
- **Root CA:** The main trust anchor (trusted by OS/browser).
- **Issuing CA:** Actually hands out certs, can be delegated.
- **CRL (Certificate Revocation List):** List of revoked certs.
- **Expiration:** Certs have a lifetime and must be renewed.

#### Two Main PKI Functions

- **Encryption:** Sender uses recipient’s public key to encrypt, recipient uses private key to decrypt.
- **Signing:** Sender uses their own private key to sign, recipient verifies with sender’s public key.

### Public vs Private CA

- **Public CA:** (e.g., DigiCert) Trusted by most browsers/OS by default.
- **Private CA:** Set up and managed by your organization for internal use (trust must be manually distributed).

### Self-Signed Certificates

- Used when you don’t want or need a full CA (e.g., encrypting local device traffic).
- *Less trusted by default*; must manually trust these certs.

#### Example: Windows EFS (Encrypting File System) generates self-signed certs to protect file encryption keys.

---

## Key Takeaways (so far)

- Understand risk, threats, vulnerabilities, and exploits.
- Know the CIA triad and how it applies to IT security.
- Be able to explain and recognize encryption in transit and at rest.
- Understand the basics of certificates, PKI, and when to use self-signed vs. CA-signed certificates.

---


## AAA Model (Authentication, Authorization, Accounting)

The AAA model is a security framework central to network security. It covers:

- **Authentication:** Verifying user identity (username/password, smart card, biometrics, etc).
- **Authorization:** Granting user access to resources after authentication.
- **Accounting:** Recording what users do (logins, changes, access attempts).

### Authentication

Ways to prove identity (factors):
- **Something you know:** Password, PIN.
- **Something you have:** Key fob, smart card, ID badge, OTP.
- **Something you are:** Biometrics (fingerprint, face, voice).
- **Somewhere you are:** GPS location or trusted IP.
- **Something you do:** Unique actions, signatures, typing rhythm.

### Multifactor Authentication (MFA)

Combining two or more factors. Examples:
- ATM: Card (have) + PIN (know).
- App: Password (know) + OTP from phone (have).

**MFA methods:**
- Email (least secure)
- SMS text code
- Voice call code
- Time-based tokens (hardware or software, e.g., Google Authenticator)

---

## Single Sign-On (SSO) and SAML

- **Single Sign-On (SSO):** Authenticate once, access many systems without re-entering credentials.
- **SAML (Security Assertion Markup Language):** XML-based protocol for claims-based authentication between Identity Provider (IdP) and Service Provider (SP).
- Used in many cloud services and federated identity systems.

---

## Authentication Protocols

### RADIUS

- **Remote Authentication Dial-In User Service**
- Centralized AAA (auth/authz/accounting) for VPNs, Wi-Fi, network devices.
- Uses UDP 1812 (auth), 1813 (accounting).
- Microsoft implementation: Network Policy Server (NPS).
- Common in enterprise wireless and remote access.

### TACACS+

- **Terminal Access Controller Access-Control System Plus**
- Cisco proprietary, but widely used.
- Separates authentication, authorization, and accounting.
- Uses TCP port 49 (more reliable than UDP).
- More granular than RADIUS; used for device admin access.

### LDAP

- **Lightweight Directory Access Protocol**
- For querying directory services like Microsoft Active Directory.
- Standard port TCP 389 (LDAP), TCP 636 (LDAPS).
- Used for user lookups, not authentication (Active Directory uses Kerberos for authentication).

---

## Authorization

### IAM (Identity and Access Management)

- Framework to manage user identities and define who can access what.
- Includes username/password, certs, SSO, MFA.

### Principle of Least Privilege

- Give users only the minimum permissions needed to do their job.
- Reduces risk and simplifies compliance.

### Role-Based Access Control (RBAC)

- Permissions assigned to roles, roles assigned to users.
- Easier management, less error-prone.
- Example: Marketing staff get 'Marketing' role; Teams meeting roles (attendee, presenter, organizer).

### Geofencing

- Access control based on physical location (GPS, RFID).

---

## Accounting

- Audit trails/logs: Tracks access, actions, denied attempts.
- Important for investigations, compliance, billing (in some services).

---

## Regulatory Compliance

Many organizations must comply with various laws, standards, and frameworks:

- **ISO/IEC 27002:** Code of practice for information security controls.
- **Data Locality:** Laws requiring data to stay within country borders.
- **FERPA:** US law for student record privacy.
- **GLBA:** Financial privacy.
- **GDPR:** EU data privacy law, strict consent and breach reporting.
- **HIPAA:** US health info privacy.
- **PCI DSS:** Payment card data standard (credit cards).
- **SOX:** US law for financial records in public companies.

### Policies, Processes, and Procedures

- **Policy:** High-level rules (ex: password policy).
- **Process:** Step-by-step to achieve policy (ex: user onboarding).
- **Procedure:** Specific instructions for each process.

### Audit

- Internal/external audits check compliance with policies and regulations.
- Logs, processes, and access control are reviewed.
- Regular audits reduce risk of penalties or breaches.

---

## **Summary & Exam Essentials**

- **CIA Triad:** Confidentiality, Integrity, Availability—core to security.
- **Threat:** Potential for harm (internal/external).
- **Risk:** Likelihood of threat impacting the organization.
- **Vulnerability:** Weakness that can be exploited.
- **CVE:** Standardized list of public vulnerabilities.
- **Exploit:** Actual code/attack that abuses a vulnerability.
- **Symmetric encryption:** Same key for encrypt/decrypt.
- **Asymmetric encryption:** Public/private key pairs.
- **PKI:** Uses asymmetric encryption for encryption and signing.
- **Authentication methods:** MFA, TACACS+, SSO, RADIUS, LDAP.
- **Authorization:** IAM, least privilege, RBAC.
- **Regulations:** Know major standards/laws (PCI, GDPR, HIPAA, SOX).

