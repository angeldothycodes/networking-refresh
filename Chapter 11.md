# CCNA Chapter 11: Switching and Virtual LANs

## 1. The World Before Switching
- Old networks used **hubs** and **routers** to connect PCs, servers, and mainframes.
- Hubs = all devices share one big collision domain, lots of collisions, slow performance as more devices are added.
- Growth made these networks too slow; needed better segmentation.

## 2. Why Layer 2 Switching Changed Everything
- **Switches** replaced hubs, making each port a separate collision domain (every device gets its own bandwidth).
- Switches use **ASICs** (hardware) for fast forwarding.
- Large networks now possible without as many slowdowns.

## 3. Bridges vs. Switches (Compare)
- **Bridges:** Software-based, fewer ports, slower.
- **Switches:** Hardware-based (ASICs), many ports, very fast.
- Both use MAC addresses (Layer 2), but switches can scale for big modern LANs.

## 4. What Does a Switch Actually Do?
- **Three main jobs:**
    1. **Address Learning:** Learns source MAC addresses and maps them to switch ports (MAC address table).
    2. **Forward/Filter:** Forwards frames to correct port if MAC is known, floods if not.
    3. **Loop Avoidance:** Uses **Spanning Tree Protocol (STP)** to avoid network loops (broadcast storms).

### Example:
- When a frame is sent, switch saves sender’s MAC/port, checks if destination MAC is in table:
    - If yes → forwards only to correct port.
    - If no → floods to all ports except source.

## 5. MAC Address Table (CAM Table)
- Use command `show mac address-table` on Cisco switches.
- Entries age out if inactive (default 5 minutes).
- If table is full (attack or misconfig), switch acts like a hub (not good).

## 6. Looping and STP: Why You Care
- Redundant links (for reliability) = risk of network loops.
- **Problems from loops:**
    - Broadcast storms (frame never dies, multiplied).
    - Multiple frame copies.
    - MAC address table instability.

### Spanning Tree Protocol (STP) Basics
- Elects one **Root Bridge** (lowest Bridge ID, usually lowest MAC).
- Each switch picks shortest path to root bridge.
- Non-best paths get **blocked**.
- STP sends **BPDUs** (Bridge Protocol Data Units) to communicate topology info.

#### Port States (classic 802.1D STP)
- **Blocking:** Listens for BPDUs, doesn’t forward data.
- **Listening:** Prepares to forward, checks for loops, doesn’t learn MACs.
- **Learning:** Learns MAC addresses, doesn’t forward frames.
- **Forwarding:** Sends and receives data frames.
- **Disabled:** Not part of STP.

#### STP Timers
- Default convergence time: up to 50 seconds (slow!).
- **Rapid STP (RSTP, 802.1w):** Converges in a few seconds.

#### STP Troubleshooting
- If devices can’t talk after a topology change, STP may be converging.
- Use `show spanning-tree` to check root bridge, port states, topology.

## 7. Distributed Switching (Virtualization)
- Virtual switches inside hypervisors connect VMs just like physical switches.
- **Distributed switch:** One virtual switch spans multiple hosts (VMware).

## 8. VLANs (Virtual LANs): What, Why, and How
- **VLAN = Virtual LAN:** Logically segments a switch so devices in one VLAN can’t see devices in another (unless routed).
- By default, all switch ports are in VLAN 1.
- Each VLAN is its own broadcast domain (cuts down noise, improves security).

### Why Use VLANs?
- Separate departments, projects, or user types—even if they are on different physical locations.
- Improve security by keeping sensitive devices isolated.
- Limit broadcast storms to one VLAN.

#### Example Use Case:
- Sales and HR are on the same floor. Assign Sales to VLAN 10, HR to VLAN 20. They are logically separated even if plugged into the same switch.

### Physical LAN vs. VLAN
- Old: Physical cabling decided broadcast/collision domains.
- Now: Any port on any switch can be in any VLAN.

## 9. VLAN Membership: Static vs. Dynamic
- **Static VLAN:** Admin assigns ports to VLANs manually (most common, more secure).
- **Dynamic VLAN:** VLAN assigned based on device’s MAC address using a server (VMPS).

## 10. Access Ports, Trunk Ports, Voice VLANs

### Access Port:
- Assigned to a single VLAN.
- Used by end devices (PCs, printers).
- No VLAN tag on frames as they leave the port.

### Voice VLAN:
- Allows both a phone and a PC to share one switch port, with separate VLANs for data and voice.

### Trunk Port:
- Carries traffic for **multiple VLANs**.
- Used between switches or switch-router connections.
- Frames are tagged to show which VLAN they belong to.
- Default native VLAN = VLAN 1 (untagged traffic).

## 11. VLAN Tagging: ISL vs. 802.1Q

- **ISL:** Cisco proprietary, tags the frame with VLAN info (older, not widely used now).
- **802.1Q:** Industry standard, inserts VLAN tag inside the Ethernet frame (most common).
    - Allows up to 4094 VLANs.
    - Native VLAN traffic is untagged (by default VLAN 1).
    - You must use 802.1Q to trunk between Cisco and other vendors.

## 12. Routing Between VLANs

- **Inter-VLAN Routing:** Needed if devices in different VLANs need to communicate.
    - **Router-on-a-stick:** One router interface (trunk) with subinterfaces for each VLAN.
    - **Layer 3 switch (SVI):** Switch has a virtual interface for each VLAN. Routing is done in hardware (much faster).

#### Example:  
- Router subinterfaces: `int g0/0.10` for VLAN 10, `int g0/0.20` for VLAN 20.

## 13. VLAN Trunking Protocol (VTP)

- **Purpose:** Automatically propagates VLAN info across multiple switches.
- **Modes:**
    - **Server:** Can add/change/delete VLANs, advertises changes.
    - **Client:** Receives and uses VLAN info, can’t make changes.
    - **Transparent:** Forwards VTP messages, but doesn’t use them; VLANs configured locally.
- **VTP domain:** All switches in same domain share VLAN info.
- **Caution:** VTP misconfiguration can wipe out all VLANs!

## 14. Switch Management (IP address, remote access)

- Switches don’t need IP addresses to switch traffic, only for management (SSH, Telnet, SNMP).
- IP address assigned to a VLAN interface (typically VLAN 1, but best practice is a dedicated management VLAN).

## 15. Switch Security Features

### Port Security:
- Restrict which MAC addresses can connect to each port.
- Can shut down port if violation occurs (protects against rogue devices).

### DHCP Snooping:
- Blocks rogue DHCP servers by allowing DHCP responses only on trusted ports.
- Maintains binding table for IP/MAC mapping.

### Dynamic ARP Inspection (DAI):
- Prevents ARP spoofing/poisoning using DHCP snooping table to verify ARP responses.

### Flood Guard:
- Protects against MAC table overflow attacks.
- Unknown Unicast Flood Blocking (UUFB) & Rate-Limiting.

### BPDU Guard:
- Shuts down a port if BPDU is received where it shouldn’t be (protects STP topology).

### Root Guard:
- Prevents a new switch from becoming root bridge.

## 16. EtherChannel / Link Aggregation (Port Bonding)

- **Purpose:** Combine multiple physical links into one logical bundle for more bandwidth and redundancy.
- **Cisco EtherChannel:** Up to 8 active ports bundled together.
- All links must match (speed, duplex, VLAN).
- Appears as a single link to STP (no blocking, all links used).
- **Negotiation Protocols:**
    - **PAgP (Port Aggregation Protocol):** Cisco proprietary.
    - **LACP (Link Aggregation Control Protocol, 802.3ad):** Industry standard.
- **Static EtherChannel:** Can be configured with no protocol, but not recommended.
- **Config Example:**
    - On Cisco:  
      ```
      interface range f0/1 - 2
        channel-group 1 mode active
      ```
- **Troubleshooting:**  
    - Ports not bundling? Check speed/duplex, allowed VLANs, mode (active/passive), and protocol (must match).

## 17. Advanced Features

### Power over Ethernet (PoE, PoE+)
- Supplies power (in addition to data) over Ethernet cables.
- Used for APs, VoIP phones, cameras.
- **PoE (802.3af):** Up to 15.4W per port.
- **PoE+ (802.3at):** Up to 25.5W per port.

### Port Mirroring (SPAN, RSPAN)
- Copies traffic from one port (or VLAN) to another port for monitoring/troubleshooting (e.g., connect a sniffer or IDS).
- Use sparingly—can overload switch if overused.

### Jumbo Frames
- Increases MTU up to 9000 bytes (vs. 1500 bytes default).
- Used in storage or high-performance networks.
- **All devices along the path must support jumbo frames,** or you’ll get fragmentation, high latency.

## 18. Troubleshooting Layer 2 Issues

- **Common Issues:**
    - VLAN misconfiguration: Check port VLAN assignment.
    - STP problems: Loops, wrong root bridge, mis-set priorities.
    - EtherChannel not forming: Check settings (speed, duplex, VLANs must match).
    - No connectivity: Port security violation, shutdown ports, wrong trunking config.

- **Useful Commands (Cisco):**
    - `show interfaces status`
    - `show mac address-table`
    - `show vlan brief`
    - `show interfaces trunk`
    - `show spanning-tree`
    - `show etherchannel summary`
    - `show port-security`

---

# Quick Interview Reference / Cheat Sheet

- **Switch functions:** Address learning, filtering/forwarding, loop avoidance (STP).
- **STP states:** Blocking, Listening, Learning, Forwarding, Disabled.
- **EtherChannel protocols:** PAgP (Cisco), LACP (standard).
- **Access vs trunk port:** Access = 1 VLAN, trunk = many VLANs.
- **VLAN tags:** ISL (Cisco), 802.1Q (standard).
- **VTP modes:** Server, Client, Transparent.
- **Inter-VLAN routing:** Needs router (router-on-a-stick) or SVI on L3 switch.
- **Security:** Use port security, DHCP snooping, DAI, BPDU guard, root guard.
- **PoE:** Power and data on one cable; PoE+ for higher wattage devices.
- **Jumbo frames:** High-performance networks; all hardware must support.

---

# End of Chapter 11 Summary
