# Chapter 16: High Availability and Disaster Recovery

> **CompTIA Network+ Objectives Covered**
> - **2.4:** Explain important factors of physical installations (power, environment, fire, etc.)
> - **3.3:** Explain disaster recovery (DR) concepts (RPO, RTO, MTTR, MTBF, DR sites, high availability, testing)

---

## What Is High Availability and Fault Tolerance?

High availability (HA) means your systems and network are up and running as much as possible—even in the face of hardware failures or disasters. You want users to always have access to critical resources, so downtime must be minimized.  
This is achieved by **redundancy**: using duplicate systems, power sources, connections, and paths.

**Fault tolerance** is when the system keeps working even if a part fails. A simple example: two power supplies in a server—if one fails, the other takes over. In networking, this might mean multiple switches, links, or even full server clusters so a single failure doesn’t bring everything down.

---

## Load Balancing, Multipathing, and NIC Teaming

**Load balancing** spreads work across multiple servers, network links, or devices. This keeps things fast and responsive, and prevents any one device from being overwhelmed.  
You can have **active/passive** clusters (one active, the rest on standby), or **active/active** (all share the load).

**Multipathing** is having more than one connection between a server and its storage—so if one path fails, another takes over.

**NIC Teaming** allows you to group multiple network interface cards (NICs) together for more bandwidth or failover. If one NIC or its path fails, traffic continues on the other NIC(s). You can use active/active or active/passive configurations, and this can also be done across switches for more resilience.

---

## Redundant Hardware and Clustering

**Switches:** Use multiple switches, sometimes managed as a stack (all act as one logical switch with a master and backup) or a cluster (using a management protocol so one switch manages others). This reduces downtime from switch failures.

**Routers:** Use First-Hop Redundancy Protocols (FHRPs) so that multiple routers can act as a single gateway. The network sees a virtual router with one IP/MAC address; if one router fails, another takes over instantly.

**Firewalls:** Can also be clustered—multiple firewalls act as one logical device. This provides both redundancy and the ability to handle more traffic (scalability).

**Servers:** Clusters of servers provide redundancy, allowing workloads to continue even if a server goes down. Applications may failover automatically.

**Power Supplies:** Most enterprise hardware has dual power supplies (active/passive or active/active/load-sharing). If one fails, the other keeps things running.

**Storage:** Use RAID (Redundant Array of Independent Disks) for drive redundancy.
- **RAID-1:** Mirroring (identical copy, can lose 1 drive)
- **RAID-5:** Striping with parity (can lose 1 drive)
- **RAID-6:** Striping with dual parity (can lose 2 drives)

---

## Facilities Redundancy and Environmental Controls

**Power:**  
- **Uninterruptible Power Supply (UPS):** Provides temporary battery power to keep systems running during short outages or until generators start.  
- **Power Distribution Unit (PDU):** Distributes electricity to racks/servers; some can be monitored or remotely managed.  
- **Generators:** Provide long-term power during outages. Often fueled by diesel, gas, or natural gas.

**HVAC:**  
Keep temperatures and humidity in the recommended range. Too hot causes shutdowns; too humid causes corrosion; too dry leads to static. Data centers use specialized air conditioning, sometimes backed up by UPS/generators.

**Fire Suppression:**  
Standard water sprinklers will destroy electronics. Data centers often use **clean agent** fire suppression systems (gas that starves fire of oxygen but won’t harm equipment), or pre-action systems to prevent accidental discharges. Wet, dry, preaction, deluge, and clean agent are common types.

---

## Disaster Recovery (DR) Concepts

When disaster strikes, **disaster recovery** (DR) is about restoring critical systems and data as quickly as possible. You need to know two main metrics:

- **Recovery Point Objective (RPO):** How much data loss is acceptable? (E.g., if backups are nightly, RPO is 24 hours; you could lose a day’s data.)
- **Recovery Time Objective (RTO):** How quickly must you be up and running again after a failure? (E.g., 4 hours)

Other important metrics:
- **Mean Time To Repair (MTTR):** Average time to fix a failed component.
- **Mean Time Between Failures (MTBF):** Average time between one failure and the next for a component.

---

## Types of Disaster Recovery Sites

- **Cold Site:** Just a building and utilities—no hardware installed. Cheapest but slowest to restore.
- **Warm Site:** Has network equipment and utilities, but you still need to bring software/data. Middle ground.
- **Hot Site:** Fully equipped with hardware, network, and software—ready for instant use. Fastest, but most expensive.
- **Cloud Site:** Virtual DR solution—your network can be recreated in the cloud when needed.

---

## Backups and Restores

Backups aren’t just for disaster recovery. They’re also for accidental deletions, failed upgrades, or configuration mistakes.

- **Disk-to-tape:** Traditional method; large capacity but slow to restore.
- **Disk-to-disk:** Faster; easier for quick recovery.
- **Disk-to-cloud:** Off-site; good for archiving but can be slow and costly for large restores.

Don’t forget to back up **network device configs**—restoring a switch/router is a nightmare if you have to rebuild configs from scratch.

A common backup rotation is **grandfather-father-son (GFS)**:  
- Daily backups rotate; one becomes the weekly, one weekly becomes the monthly, etc.

---

## Testing Your DR Plan

A plan is worthless if it isn’t tested.  
**Tabletop exercises** are simulated walk-throughs where team members discuss what they would do in various disaster scenarios.  
**Validation tests** verify that the procedures work and everyone knows their role.

Regularly review and update your plans based on feedback and test results.

---

## Key Protocols and Approaches

- **First-Hop Redundancy Protocols (FHRP):** Allow multiple routers to share a virtual IP/MAC for the default gateway.  
  - **HSRP (Hot Standby Router Protocol):** Cisco-proprietary. One router is active, others standby; uses special virtual MAC.
  - **VRRP (Virtual Router Redundancy Protocol):** Open standard; similar idea.

- **Active/Active vs. Active/Passive:**  
  - **Active/Active:** All nodes are working and sharing the load.
  - **Active/Passive:** One or more nodes on standby; only take over if an active node fails.

---

## Summary

High availability and disaster recovery are about minimizing downtime and preventing data loss.  
This means using redundant hardware (servers, switches, routers, firewalls), redundant power (UPS, PDU, generators), environmental controls (HVAC, fire suppression), and planning for backup and rapid recovery (RPO, RTO, MTTR, MTBF).  
DR sites—hot, warm, cold, or cloud—let you restore operations after a disaster.  
Test your plans regularly with tabletop and validation exercises, and always keep backup copies of data and configurations.

---

> This chapter covers Network+ objectives 2.4 and 3.3, focusing on high availability, fault tolerance, redundancy, disaster recovery concepts (metrics, sites, backups), facility/environmental controls, and the testing/validation of DR plans.
