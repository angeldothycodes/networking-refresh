# Chapter 8: IP Subnetting, Troubleshooting IP, and Introduction to NAT

This chapter is a core foundation for IP addressing, subnetting, troubleshooting, and address translation. You will master all the following CompTIA Network+ objectives:

---

## Domain 1.0 Networking Concepts

### 1.4 Common Networking Ports, Protocols, Services, and Traffic Types

#### **Traffic Types**

- **Unicast:**  
  Data is sent from one device directly to one other device.  
  _Example: Browsing a website sends traffic from your PC to a single server._

- **Broadcast:**  
  Data is sent from one device to all devices in the broadcast domain.  
  _Example: ARP requests (Who has this IP?)._

- **Multicast:**  
  Data is sent from one device to a selected group of devices, using special addresses (224.0.0.0–239.255.255.255).  
  _Example: Video streaming to a group of subscribers._

- **Anycast:**  
  Data is sent from one device to the *nearest* member of a group, typically in IPv6.  
  _Example: DNS requests routed to the nearest available DNS server._

---

### 1.7 IPv4 Network Addressing

#### **Public vs. Private IP Addresses**

- **Public IP Addresses:**  
  Routable on the internet. Must be unique globally. Assigned by IANA/Regional Internet Registries.
- **Private IP Addresses:**  
  Not routable on the internet. Used inside LANs. Defined by **RFC1918**:
    - **Class A:** 10.0.0.0 – 10.255.255.255
    - **Class B:** 172.16.0.0 – 172.31.255.255
    - **Class C:** 192.168.0.0 – 192.168.255.255

#### **Automatic Private IP Addressing (APIPA)**
- Range: **169.254.0.1 – 169.254.255.254**
- If a device can’t reach a DHCP server, it assigns itself an APIPA address. Only works for local communication (not internet).

#### **Loopback / Localhost**
- **127.0.0.1** is the loopback address (localhost). Used to test the local TCP/IP stack.

#### **Subnetting**
Subnetting is the process of dividing a large network into smaller, more manageable sub-networks.

- **Why Subnet?**  
  - Reduce broadcast domains (and network congestion)
  - Increase network security and organization
  - Make networks easier to manage and scale

#### **Subnet Masks and CIDR**
- Subnet masks define which portion of the IP address is the network and which is the host.
- **CIDR (Classless Inter-Domain Routing)** uses a “slash” notation (e.g., `/24`) to define the number of network bits.

##### **Common CIDR and Subnet Mask Table**

| CIDR | Subnet Mask       | Hosts/Subnet | # Subnets (/24) |
|------|-------------------|--------------|-----------------|
| /24  | 255.255.255.0     | 254          | 1               |
| /25  | 255.255.255.128   | 126          | 2               |
| /26  | 255.255.255.192   | 62           | 4               |
| /27  | 255.255.255.224   | 30           | 8               |
| /28  | 255.255.255.240   | 14           | 16              |
| /29  | 255.255.255.248   | 6            | 32              |
| /30  | 255.255.255.252   | 2            | 64              |

- **Subnetting Math:**  
  - Hosts per subnet: `2^h - 2` (h = host bits, subtract network and broadcast addresses)
  - Subnets: `2^s` (s = subnet bits)

#### **Variable Length Subnet Mask (VLSM)**
- VLSM allows different subnets to have different sizes within the same network.  
- Useful for efficiently allocating IPs (big subnets for large departments, small for WAN links).

#### **IPv4 Address Classes**

| Class | First Octet | Default Mask      | Typical Use               |
|-------|-------------|-------------------|---------------------------|
| A     | 1 – 126     | 255.0.0.0 (/8)    | Huge orgs/ISPs            |
| B     | 128 – 191   | 255.255.0.0 (/16) | Midsize companies/universities |
| C     | 192 – 223   | 255.255.255.0 (/24)| Small businesses/homes     |
| D     | 224 – 239   | (N/A)             | Multicast groups           |
| E     | 240 – 255   | (N/A)             | Experimental/research      |

- **Class D:** Reserved for multicast.
- **Class E:** Reserved for experimental use.

---

## Domain 2.0 Network Implementation

### 2.1 Routing Technologies

#### **Address Translation: NAT and PAT**

**NAT (Network Address Translation):**
- Allows private IP addresses to communicate on the public internet by translating them to public IPs.
- **Types:**
  - **Static NAT:** One-to-one mapping (rarely used).
  - **Dynamic NAT:** Many-to-many mapping using a pool of public IPs.
  - **PAT (Port Address Translation):** Many-to-one. Many private IPs share a single public IP, differentiated by port numbers.  
    - **Also known as NAT Overload.**  
    - _Example: All users in an office access the internet via one public IP._

**Key NAT Terminology Table**

| Name            | Description                                               |
|-----------------|----------------------------------------------------------|
| Inside Local    | Private (internal) IP before translation                 |
| Inside Global   | Public (external) IP representing internal host          |
| Outside Local   | IP address of outside destination before translation     |
| Outside Global  | Public IP of destination host after translation          |

---

## **Troubleshooting IP Addressing**

1. **Ping Loopback (127.0.0.1):** Checks the TCP/IP stack.
2. **Ping Local IP:** Verifies NIC and IP stack.
3. **Ping Default Gateway:** Checks local network connectivity.
4. **Ping Remote Device:** Verifies routing and remote network access.

**Common IP Troubleshooting Tools**
- `ping`: Test connectivity
- `tracert` (Windows) / `traceroute` (Linux): Shows path to destination
- `ipconfig /all` (Windows): Display IP configuration
- `arp -a`: Show ARP cache

**Typical Problems:**
- Wrong subnet mask, gateway, or IP
- Misconfigured NAT
- Host using broadcast address or wrong subnet

---

## **Practice Subnetting Example**

Suppose you have `192.168.1.0/24` and need 4 equal subnets.

1. 4 subnets → 2 subnet bits needed (`2^2 = 4`)
2. New mask: `/26` (255.255.255.192)
3. Subnet increments: 256-192 = 64

| Subnet # | Network Address    | Host Range           | Broadcast Address  |
|----------|--------------------|----------------------|--------------------|
| 1        | 192.168.1.0/26     | .1 – .62             | 192.168.1.63       |
| 2        | 192.168.1.64/26    | .65 – .126           | 192.168.1.127      |
| 3        | 192.168.1.128/26   | .129 – .190          | 192.168.1.191      |
| 4        | 192.168.1.192/26   | .193 – .254          | 192.168.1.255      |

---

## **Summary Table: IPv4 Classes and Private Ranges**

| Class | First Octet | Private Range                     | Default Mask      |
|-------|-------------|-----------------------------------|-------------------|
| A     | 1-126       | 10.0.0.0 – 10.255.255.255         | 255.0.0.0         |
| B     | 128-191     | 172.16.0.0 – 172.31.255.255       | 255.255.0.0       |
| C     | 192-223     | 192.168.0.0 – 192.168.255.255     | 255.255.255.0     |

---

## **Key Points for the Exam**

- Memorize the ranges for unicast, broadcast, multicast, and anycast.
- Be able to calculate and apply subnet masks (CIDR/VLSM).
- Know which address classes and private ranges are used where.
- Understand NAT, PAT, and their terms and use-cases.
- Be able to troubleshoot IP addressing issues step by step.

---
