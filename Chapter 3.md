# Chapter 3: Networking Connectors and Wiring Standards

#### **CompTIA Network+ Exam Objectives Covered**
- Domain 1.0 Networking Concepts
    - Compare and contrast transmission media and transceivers.
    - Wired: Single-mode vs. multimode fiber, DAC, twinax, coaxial, cable speeds, plenum vs. non-plenum.
    - Transceivers, protocols, form factors, connector types (SC, LC, ST, MPO, RJ-11, RJ-45, F-type, BNC).
- Domain 5.0: Troubleshoot common cabling and physical interface issues.
    - Cable types, shielded/unshielded, cable issues.

---

#### **Physical Media**
- **Coaxial Cable:** Center copper conductor, plastic jacket, braided shield, plenum/non-plenum (fire code).
- **Twisted-pair Cable:** Multiple pairs of insulated wires (UTP = Unshielded, STP = Shielded).
- **Twinaxial (Twinax):** Short distance, high-speed copper cable for data center, DAC is direct attach copper.
- **Fiber Optic:** Uses light over glass or plastic, immune to EMI/RFI, single-mode for long, multimode for shorter distances.

---

#### **Ethernet Cable Categories**
- **Cat 1:** Voice (POTS).
- **Cat 2–4:** Obsolete, for low-speed data.
- **Cat 5:** 100 Mbps, now obsolete.
- **Cat 5e:** Enhanced, for Gigabit (1000BaseT).
- **Cat 6/6A:** Higher speed/frequency, 10GBaseT.
- **Cat 7/8:** For future/high-density data centers.

---

#### **Connectors**
- **BNC:** For coax (RG-58, RG-8).
- **RJ-45:** For UTP (Ethernet); 8 wires, 4 pairs.
- **RJ-11:** For phone; 4 wires, 2 pairs.
- **SC, LC, ST, MT-RJ, MPO:** Fiber optic connectors.  
  - **ST:** Bayonet, "twist and lock"
  - **SC:** Square, "push-pull"
  - **LC:** Small form factor, looks like RJ
  - **MPO:** High-density, for multiple fibers

---

#### **Transceivers and Media Converters**
- **SFP/SFP+:** Small form-factor pluggable, up to 16Gbps.
- **QSFP/QSFP+:** Quad SFP, up to 100Gbps.
- **Media converters:** Fiber to Ethernet, fiber to coaxial, single-mode to multimode.

---

#### **Wiring Standards**
- **T568A/B:** Wiring color codes for RJ-45.
    - T568A: Green on 1/2, Orange on 3/6.
    - T568B: Orange on 1/2, Green on 3/6.
- **Straight-through cable:** Same standard both ends (A–A or B–B).
- **Crossover cable:** T568A on one end, T568B on the other (A–B).

---

#### **Cable Types and Usage**
- **Straight-through:** Host to switch/hub, router to switch/hub.
- **Crossover:** Switch to switch, host to host, router to host.
- **Rolled/Rollover:** Host to router console.
- **T1 crossover:** For T1 WAN/CSU/DSU devices.

---

#### **Fiber Optic Details**
- **Single-mode (SMF):** Long distance, single ray of light.
- **Multimode (MMF):** Shorter distance, multiple rays/paths.
- **APC vs UPC:** Connector polish type (APC = angled, green; UPC = flat, blue).

---

#### **Distribution Frames & Blocks**
- **MDF/IDF:** Main/intermediate distribution frame for cabling.
- **66 block:** Old analog phone, voice only.
- **110 block:** Modern, for phone/network, punch-down style.
- **BIX block:** Alternative to 110.
- **Demarc:** Service provider's last point of responsibility.
- **Smart jack (NID/NIU):** Network interface, sometimes loopable for testing.

---

#### **Other Cables**
- **RS-232/DB-9/DB-25:** Serial connections (mostly obsolete, replaced by USB).
- **USB:** Universal, 127 devices max, for peripherals.

---

#### **Key Cable Properties**
- **Transmission speed**: Mbps/Gbps
- **Distance**: Max segment length (e.g., UTP = 100m)
- **Duplex**: Half (one-way at a time), Full (simultaneous)
- **Noise immunity**: EMI/RFI resistance (fiber = best)
- **Frequency**: Max MHz supported (Cat 5e = 100MHz, Cat 6 = 250MHz)

---

#### **Exam Essentials**
- Know cable types (coaxial, UTP, fiber).
- Recognize connector types and their uses.
- Understand media converters and wiring standards (T568A/B, crossover, straight-through, rolled).
- Know transceiver types (SFP, QSFP, etc).
- Difference between SMF/MMF, APC/UPC.

---

#### **Wiring Pinouts for Reference**

```text
T568A      T568B
1 Green/W  1 Orange/W
2 Green    2 Orange
3 Orange/W 3 Green/W
4 Blue     4 Blue
5 Blue/W   5 Blue/W
6 Orange   6 Green
7 Brown/W  7 Brown/W
8 Brown    8 Brown



### **Quick Cable Reference**

| Cable Type        | Use Case                    | Pinout             |
|-------------------|----------------------------|--------------------|
| Straight-through  | Host–Switch, Router–Switch  | A–A or B–B         |
| Crossover         | Switch–Switch, Host–Host    | A–B or B–A         |
| Rolled            | Console (PC–Router/Switch)  | All pins reversed  |
| T1 Crossover      | CSU/DSU–CSU/DSU             | 1/2–4/5 swapped    |
