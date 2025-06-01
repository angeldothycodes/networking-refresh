# Chapter 21: Common Types of Attacks

## Objectives

- **Explain the importance of basic network security concepts**  
  (Physical security, deception technologies, honeypots, segmentation, IoT/IIoT, SCADA/ICS/OT, guest/BYOD)
- **Summarize various types of attacks and their impact to the network**
- **Apply network security features, defense techniques, and solutions**

---

## Introduction

No matter how secure you think your network is, there are always threats that could breach security and cripple your infrastructure. Understanding attack types is the first step toward defense. This chapter teaches you common network attacks and basic mitigation strategies.

---

## Technology-Based Attacks

### Denial of Service (DoS) & Distributed DoS (DDoS)

- **DoS:** Overwhelms a service/server with fake requests so real requests can’t be fulfilled.
- **Reflective DoS:** Attack traffic is bounced off a third-party server back to the victim.
- **Amplified DoS:** Small attacker request triggers a much larger response to the victim (commonly using DNS/NTP).
- **Distributed DoS (DDoS):** Many compromised hosts (botnet) flood the victim; source is distributed and harder to block.

**Unintentional DoS:** Sudden spikes in legitimate traffic (“friendly fire”) can have the same effect.

**Physical DoS:** Physical damage or unplugging cables, or PDoS (“phlashing”) attacks that destroy device firmware.

---

### On-Path Attack (Man-in-the-Middle, MitM)

- Attacker secretly intercepts and possibly alters communications between two parties.
- Can be used with evil twin, ARP spoofing, and DNS poisoning.

---

### DNS Poisoning/Spoofing

- **Poisoning:** Attacker tricks DNS cache to return the wrong IP for a domain.
- **Spoofing:** Attacker forges DNS responses, redirecting victims to malicious sites.

---

### VLAN Hopping

- Allows traffic from one VLAN to reach another, typically by “double tagging” frames to trick switches.

---

### ARP Spoofing/Poisoning

- Attacker sends fake ARP messages to associate their MAC with the IP of another host, allowing interception.

---

### Rogue Devices and Services

- **Rogue DHCP:** Fake DHCP server gives out malicious IP settings (wrong gateway/DNS), enabling attacks.
- **Rogue Access Point:** Unauthorized AP connected to your wired LAN; can be set up by attackers or employees.
- **Evil Twin:** Malicious AP using your network’s SSID to hijack clients and perform attacks.

---

### Password Attacks

- **Dictionary Attack:** Uses a list of common passwords.
- **Brute-force Attack:** Tries every possible combination.
- **Rainbow Tables:** Precomputed hashes for fast lookup.

---

### Spoofing Attacks

- **MAC Spoofing:** Attacker fakes their MAC address.
- **IP Spoofing:** Attacker fakes their IP address to bypass access controls.

---

### MAC Flooding

- Overloads a switch’s MAC table so that it floods all ports, exposing traffic.

---

### Malware

- **Virus:** Self-replicates by attaching to files.
- **Worm:** Self-replicates but spreads independently.
- **Ransomware:** Encrypts user data, demands payment.
- **Trojan:** Disguised as a legit app; may install backdoors.
- **Keylogger:** Captures keystrokes.
- **Rootkit:** Hides malware presence at OS level.
- **Spyware:** Collects user info, may show ads (adware).
- **Cryptominer:** Hijacks system resources for cryptocurrency mining.

---

## Human & Environmental Attacks

### Social Engineering

- Attacker manipulates people to reveal confidential info (ex: phishing).
- **Phishing:** Fake emails/websites tricking users for credentials.
- **Spear phishing:** Targeted phishing at specific users.

### Environmental

- **Tailgating:** Attacker follows authorized person through a secure door.
- **Piggybacking:** Authorized person knowingly lets someone in.
- **Dumpster Diving:** Searching trash for sensitive info.
- **Shoulder Surfing:** Observing someone entering sensitive data.

---

## Hardening Security

- **Device Hardening:** Change default credentials, use strong passwords, patch devices.
- **Disable Unused Services/Ports:** Reduces attack surface.
- **Use Secure Protocols:** Prefer SSH/SCP/HTTPS over Telnet/TFTP/HTTP.
- **Access Control Lists (ACLs):** Restrict network traffic to/from critical resources.
- **Content/URL Filtering:** Restrict access to malicious or non-work sites.
- **Network Segmentation:** Isolate sensitive assets with VLANs, ACLs, or firewalls.
- **Screened Subnet (DMZ):** Hosts serving Internet clients are isolated between firewalls.
- **802.1X:** Port-based network access control, often uses RADIUS.
- **NAC:** Network Access Control; enforces health checks before granting access.
- **MAC Filtering/Port Security:** Restricts device access based on MAC address.

---

## IoT, IIoT, SCADA/ICS/OT

- **IoT:** Consumer smart devices (fridges, speakers, thermostats, doorbells) create new attack surfaces.
- **IIoT:** Industrial sensors/actuators in factories, fields.
- **SCADA/ICS/OT:** Industrial systems (plants, utilities). Highly latency-sensitive, must be separated from IT networks for safety.

---

## Segmentation & Guest/BYOD

- **Network Segmentation:** Physical or logical (VLANs, ACLs) separation for security.
- **Honeypot/Honeynet:** Fake assets to lure and study attackers.
- **BYOD:** User-owned devices increase risk; segment them from core network.
- **Guest Network Isolation:** Separate guest wireless from production network.
- **Captive Portal:** Forces guests to accept usage policy before network access.

---

## Physical Security

- **Cameras:** Fixed (for recording) or PTZ (for wide area/intervention).
- **Locks:** Doors, server racks, USB ports, laptops (cable locks).
- **CCTV:** Coax or IP/Ethernet-based. NVR for storage.
- **Ethernet Surveillance:** Allows VLAN isolation, PoE.
- **Combination/cipher locks:** No key to lose, reprogrammable.
- **Server Locks:** Latch/padlock or rackmount enclosure.

---

## Summary

- **Common attacks:** DoS/DDoS, on-path/MitM, DNS poisoning, VLAN hopping, ARP spoofing, rogue DHCP/AP, evil twin, ransomware, password attacks.
- **Human attacks:** Social engineering, phishing, tailgating, piggybacking, shoulder surfing, dumpster diving.
- **Hardening:** Change default credentials, disable unused services/ports, use ACLs, content filtering, segment networks.
- **Segmentation:** VLANs, ACLs, DMZ/screened subnet, NAC, port security, guest/BYOD isolation.
- **Physical security:** Surveillance and locks are foundational to prevent unauthorized access.

---

## **Exam Essentials**

- **Tech attacks:** DoS/DDoS, on-path, DNS poisoning, VLAN hopping, ARP spoofing, rogue DHCP/AP, evil twin, ransomware, password attacks.
- **Human/environmental:** Social engineering, phishing, tailgating, piggybacking, shoulder surfing.
- **Hardening:** Device hardening, key management, disabling services, ACLs, content filtering.
- **Segmentation:** Screened subnet (DMZ), 802.1X, NAC, port security.
- **Physical security:** Cameras, locks, CCTV, equipment and USB security.

---

## **Quick Table: Attack Terms**

| Description | Attack Name |
|-------------|-------------|
| Disruption of service by an attacker | DoS |
| Indirect DoS attack | Reflective DoS |
| Small request, large third-party response | Amplified DoS |
| Many attackers disrupt service | DDoS |
| Disruption via stolen equipment | Physical DoS |
| Device bricked by firmware attack | Permanent DoS (PDoS, phlashing) |
| Attacker eavesdrops & manipulates | On-path (MitM) |
| Malicious reply for DNS query | DNS Poisoning |
| VLAN access via double tag | VLAN Hopping |
| Client gets malicious DNS/gateway via DHCP | Rogue DHCP |
| Duplicate SSID to intercept wireless | Evil Twin |

---

## **Sample Review Questions**

(Answers are in your book’s appendix, but here’s the format)

1. Which of the following is **not** a technology-based attack?  
    a) DoS  
    b) Rogue DHCP  
    c) Shoulder surfing  
    d) Malware

2. A command-and-control server is a part of which attack?  
    a) DDoS

3. Which attack involves impersonating both sides of a conversation?  
    a) On-path attack

...

(continue as needed)

