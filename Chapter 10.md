# Chapter 10: Routing Protocols

Routing protocols are what make it possible for networks to talk to each other. They're how routers figure out the best path for your data to travel. Instead of manually telling every router what path to use (static routing), we use *dynamic routing protocols* so the routers can do the hard work themselves.

---

## Why Routing Protocols Matter

When you connect networks together, you need routers to direct packets from one network to another. But how do routers know where to send packets? That’s where routing protocols come in: they build and update the routers’ maps of the network, called routing tables.

There are two types of routing protocols:
- **IGP (Interior Gateway Protocols):** Used within one organization or administrative domain (called an Autonomous System, or AS).
- **EGP (Exterior Gateway Protocols):** Used to connect different organizations/ASes. The main EGP is **BGP**.

---

## Administrative Distance (AD)

*Administrative Distance* is how a router rates the trustworthiness of a route—think of it as "which info should I believe?" Lower AD is more trusted (0 = best, 255 = never used). If a router learns about the same network from two sources, it chooses the route with the lowest AD.

**Default ADs (memorize for exams):**

| Source            | AD   |
|-------------------|------|
| Connected         | 0    |
| Static            | 1    |
| BGP (external)    | 20   |
| EIGRP (internal)  | 90   |
| OSPF              | 110  |
| IS-IS             | 115  |
| RIP (v1/v2)       | 120  |
| EIGRP (external)  | 170  |
| BGP (internal)    | 200  |
| Unknown           | 255  |

---

## Types (Classes) of Routing Protocols

There are three classes:

### 1. Distance-Vector

- Focuses on "distance" (number of hops) to the destination.
- Routers share their *whole* routing table with their neighbors.
- Example protocols: **RIP**, **IGRP**.
- Hop count is the main metric.
- Simple but slow to converge, prone to loops.

### 2. Link-State

- Routers know the *full* network topology, not just neighbors.
- Share only updates, not the full table.
- Each router builds its own map.
- Example protocols: **OSPF**, **IS-IS**.
- Fast convergence, scalable, supports modern features like VLSM.

### 3. Hybrid

- Combines distance-vector and link-state features.
- Example: **EIGRP** (Cisco), **BGP** (sometimes called hybrid).
- Efficient, fast convergence, can scale to large networks.

---

## Core Routing Protocols You Need to Know

### **RIP (Routing Information Protocol)**

- Distance-vector, sends full table every 30s.
- Only uses hop count (max 15 hops; 16 = unreachable).
- RIP v1: Classful (no subnet info), broadcasts, no authentication.
- RIP v2: Classless (carries subnet mask), multicasts (224.0.0.9), supports VLSM, allows authentication.

**Summary Table:**

| Feature               | RIPv1           | RIPv2        |
|-----------------------|-----------------|--------------|
| Classful/Classless    | Classful        | Classless    |
| Transport             | Broadcast       | Multicast    |
| Subnet Mask Info      | No              | Yes          |
| Authentication        | No              | Yes (MD5)    |
| Max Hop Count         | 15              | 15           |

#### Why not use RIP today?  
Slow, limited, not scalable. Used for legacy/small networks only.

---

### **EIGRP (Enhanced Interior Gateway Routing Protocol)**

- Hybrid protocol (distance-vector + link-state features).
- Cisco proprietary (but modern versions support open standard).
- Supports VLSM, CIDR, IPv4, IPv6.
- Uses bandwidth and delay as primary metrics (default).
- Maintains neighbor table, topology table, and routing table for fast, loop-free convergence.
- Uses *DUAL* algorithm for best path and quick backup.

**Why use EIGRP?**  
It’s fast, efficient, and great for large or changing networks (if you use Cisco devices).

---

### **BGP (Border Gateway Protocol)**

- Path-vector, used for routing between organizations/ISPs (across the Internet).
- Exterior Gateway Protocol (EGP), but also used internally in big networks (iBGP).
- Core protocol of the Internet.
- Makes decisions based on paths, network policies, and rules.
- Scalable and highly configurable.
- Does *not* flood the network with updates—shares path vectors.

---

### **OSPF (Open Shortest Path First)**

- Open standard, link-state.
- Fast convergence, supports VLSM and CIDR.
- Hierarchical—networks divided into *areas* (area 0 is the backbone).
- Uses Dijkstra algorithm (shortest path first).
- Multivendor support.
- Great for complex and large environments.

---

### **IS-IS (Intermediate System-to-Intermediate System)**

- Link-state, like OSPF.
- Often used by ISPs because it handles both IPv4 and IPv6 efficiently.
- Not as common as OSPF in enterprise, but widely used in carrier networks.

---

## Advanced Routing Concepts

### VLSM (Variable Length Subnet Masking)

- Lets you use different subnet masks within the same network.
- More efficient use of IP address space.
- Requires classless routing protocols (RIPv2, EIGRP, OSPF, IS-IS).

### Discontiguous Networks

- Same major network, separated by a different network in the middle.
- RIPv1 can’t handle these. OSPF can.

### Route Summarization (Aggregation)

- Combines multiple routes into one to keep routing tables small (aka supernetting).
- OSPF, EIGRP, and BGP support this.

---

## High Availability and FHRP

- If your default gateway goes down, hosts lose external connectivity.
- First Hop Redundancy Protocols (FHRP) provide a *virtual* default gateway:
  - **VRRP** (open standard)
  - **HSRP** (Cisco proprietary)
- Routers share a *virtual IP* and *virtual MAC* so if one fails, another takes over without end users noticing.

---

## IPv6 Routing: New Concepts

### Router Advertisement (RA) and NDP

- Routers in IPv6 send out *router advertisements* (RA) to let hosts know what prefix/network to use.
- Hosts can auto-configure their IPv6 address using this info (stateless autoconfig).
- NDP (Neighbor Discovery Protocol): Replaces ARP, used for discovering neighbors and gateways.

### Tunneling

- Used for IPv6 migration: carry IPv6 traffic over IPv4 networks.
- Types: GRE, 6to4, ISATAP, Teredo.
- Tunnels wrap IPv6 packets in IPv4 so you can connect IPv6 islands.

### Dual Stack

- Routers and hosts run both IPv4 and IPv6 at the same time.
- Easiest way to migrate: support both protocols until IPv6-only is possible.

---

## IPv6 Routing Protocols

- **RIPng:** Next-Gen RIP for IPv6, still 15 hops max, uses multicast (FF02::9).
- **EIGRPv6:** EIGRP for IPv6, works like EIGRP for IPv4.
- **OSPFv3:** OSPF for IPv6. Similar to OSPFv2 but supports IPv6 natively.

---

## Summary Table: Protocols and Characteristics

| Protocol | Type           | Metric       | Supports VLSM | Classless | Multicast | Max Hops | Notes                      |
|----------|----------------|-------------|---------------|-----------|-----------|----------|----------------------------|
| RIP v1   | Distance-Vector| Hop count   | No            | No        | No        | 15       | Legacy only                |
| RIP v2   | Distance-Vector| Hop count   | Yes           | Yes       | Yes       | 15       | Basic, not for big nets    |
| EIGRP    | Hybrid         | Bandwidth+  | Yes           | Yes       | Yes       | 255      | Fast, Cisco-focused        |
| OSPF     | Link-State     | Bandwidth   | Yes           | Yes       | Yes       | None     | Open, fast, scalable       |
| IS-IS    | Link-State     | Cost        | Yes           | Yes       | Yes       | None     | ISP/career use, multi-proto|
| BGP      | Path-Vector    | Policy/Path | Yes           | Yes       | No        | None     | Internet core, scalable    |

---

## Exam Tips

- **Know AD values.** Lower AD wins.
- **Distance-vector vs. link-state vs. hybrid.**
- **RIP vs. OSPF:** RIP is hop-count, OSPF is link-state and uses bandwidth.
- **FHRP:** VRRP (open), HSRP (Cisco), virtual gateways for redundancy.
- **IPv6:** RAs, NDP, tunneling, dual stack.
- **Routing loops:** Occur when routes send packets in circles. RIP is especially prone.
- **VLSM/classless:** Modern protocols support it; legacy classful ones don’t.

---

# End of Chapter 10

You now know what each routing protocol does, when to use which, how they interact, and how modern networks transition from IPv4 to IPv6. Ready to move on to switching!

