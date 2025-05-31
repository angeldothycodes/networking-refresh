# Chapter 15: Organizational Documents and Policies

> **CompTIA Network+ Objectives Covered**
> - **2.4:** Explain important factors of physical installations (MDF, IDF, racks, panels, security, etc.)
> - **3.1:** Explain the purpose of organizational processes and procedures (documentation, SLAs, asset management, change management, security policies, etc.)

---

## Why Do Organizations Need Policies and Documentation?

Networks don’t just run on cables and routers—they run on rules, structure, and written plans. If you don’t define _how_ your network should be built, managed, and secured, chaos (and security gaps) are inevitable.

**Policies** are the “what and why” (rules and expectations).  
**Procedures** are the “how” (step-by-step instructions).

Without strong policies and procedures—supported by upper management—security, reliability, and troubleshooting will all suffer.

---

## Plans and Procedures

Policies tell you the rules; procedures tell you exactly what to do when a situation comes up (like onboarding a new user, responding to an attack, or installing software).

- **Change Management:**  
  Change is risky. Every change to the network or systems should be logged, reviewed, and approved before implementation. The process includes documenting why the change is needed, what will be changed, how to roll back if it fails, who approves it, and notifying all affected teams.  
  A **maintenance window** is a planned period for making changes, usually during low-traffic times.

- **Incident Response Plan:**  
  When something bad happens (a hack, a virus, data leak), you need a playbook. The incident response plan says how to contain, investigate, and recover from the event, and how to preserve evidence.

- **Disaster Recovery Plan (DRP):**  
  When a major event disrupts operations (fire, flood, hardware failure), the DRP guides you to restore systems and resume business quickly, minimizing loss.

- **Business Continuity Plan (BCP):**  
  The BCP is about keeping critical business functions running even while you recover from disaster. This includes alternative work sites, backup communications, and priorities for restoring services.  
  A **Business Impact Analysis (BIA)** ranks which functions are most critical.

- **System Life Cycle:**  
  Every asset (hardware or software) goes through purchase, deployment, management, and retirement.  
  - **End-of-Life (EOL):** Vendor stops selling.
  - **End-of-Support (EOS):** Vendor stops supporting.
  - Before disposal, securely wipe data and follow environmental regulations.

---

## Security and Acceptable Use Policies

- **Hardening:**  
  Reduce attack surface by disabling unnecessary services, removing unused apps, blocking ports, restricting device access, and updating firmware.

- **Acceptable Use Policy (AUP):**  
  Defines what users can and can’t do on company systems. Covers device usage, internet access, software installation, and consequences for violations.

- **Password Policy:**  
  Sets requirements for password length, complexity, expiration, history, and lockout.

- **BYOD Policy (Bring Your Own Device):**  
  Rules for using personal devices at work, including security controls, PIN requirements, remote wipe, and MDM enforcement.

- **Remote Access Policy:**  
  Defines requirements for VPN and remote connections (authentication, allowed methods, etc.).

- **Onboarding/Offboarding Policy:**  
  Steps for granting/revoking accounts and access, collecting devices, and training on policies.

- **Patch and Firmware Management:**  
  Always keep OS, drivers, and firmware up to date. Test patches first, and always back up configs before upgrading firmware.

- **Clean-Desk Policy:**  
  Users must keep confidential materials (notes, passwords, files) locked away when not present.

- **Other Security Policies:**  
  Rules for equipment access (lock doors, disable unused ports), wiring security, badges, visitor control, background checks, firewalls, IDS/IPS, camera monitoring, backup storage, and more.

---

## Common Documentation Types

**Why document?** Good documentation is your network’s memory. It makes onboarding new staff easy, troubleshooting faster, and audits possible.

- **Physical Network Diagram:** Shows actual devices, wiring, racks, panels—how everything is physically connected. Should be detailed enough to rebuild the network from scratch.

- **Logical Network Diagram:** Shows how data flows, subnets, VLANs, firewalls, protocols, and routing. Logical diagrams are crucial for understanding the "invisible" connections.

- **Rack Diagrams:** Show equipment placement in each rack (by rack unit, or “U”)—critical for dense data centers.

- **Floor Plan:** Map of where assets are in a building, often using ANSI/TIA-606-B naming for quadrants.

- **IDF/MDF Documentation:**  
  - **MDF (Main Distribution Frame):** Main wiring point—connects internal systems to outside lines.
  - **IDF (Intermediate Distribution Frame):** Satellite wiring hubs branching out from the MDF.

- **Wiring Diagrams & Cable Maps:** Detailed maps of how and where cables run, essential for troubleshooting.

- **Wireless Survey / Heat Map:** Documents wireless coverage (signal strength, interference, etc.) before and after deployment.

- **Asset Inventory:**  
  - **Hardware:** Serial numbers, asset tags, warranty info.
  - **Software:** Licenses, versions, install locations.
  - **IPAM (IP Address Management):** Who has what IPs, static assignments, subnets.

- **Baselines and Golden Configurations:**  
  - **Baseline:** The “normal” performance profile for devices/networks.
  - **Golden Config:** The official, working configuration—save this after deployment!

---

## Standard Operating Procedures (SOPs)

SOPs are clear instructions for routine tasks—installing software, reporting incidents, changing a user’s permissions, etc. They make your organization efficient and prevent mistakes.

---

## Common Agreements

- **Nondisclosure Agreement (NDA):**  
  Legal contract preventing parties from sharing confidential info.

- **Service Level Agreement (SLA):**  
  Contract with a provider for uptime, response times, penalties for downtime, etc. (“the nines”—e.g., 99.99% = 52.56 minutes downtime/year).

- **Memorandum of Understanding (MOU):**  
  Formal but non-binding agreement between parties, often as a precursor to a contract.

---

## When Policy Is Broken

Policies must be enforced consistently, with consequences for violations. Users need to know what’s expected and what happens if they break the rules (up to and including termination).

---

## Data Loss Prevention (DLP)

DLP policies and tools prevent unauthorized data leaving the organization, using filters, controls, and monitoring at network egress points or on endpoints.

---

## Summary

- **Plans and policies** (change management, incident response, DRP, BCP, lifecycle) are critical for IT stability.
- **Security policies** (AUP, password, BYOD, remote access, onboarding/offboarding) reduce risk and define acceptable behavior.
- **Documentation** (physical, logical, rack, cabling, IDF/MDF, wireless, asset inventory) is essential for efficient operation and compliance.
- **Business agreements** (NDA, SLA, MOU) protect the organization and set expectations.

---

> This meets Network+ objectives 2.4 and 3.1—covering install implications, key diagrams, asset/inventory management, SLAs, change/incident/disaster/business continuity, system lifecycle, SOPs, and all relevant security policy types.

