# What is an IP Address? Why Does It Matter?

Imagine every device on the Internet is like a house in a massive city. Just as every house needs a unique postal address to receive mail, every device—your phone, your laptop, your smart fridge—needs a unique address so that it can send and receive information across the network.  
That unique “postal code” is the **IP address**.

But an IP address isn’t stuck to your device like a serial number; it’s assigned logically, and it can change. Think of it as the address your device uses to communicate with other devices.

---

## IP Addressing Basics: Bits, Bytes, and Octets

- **Bit**: Think of a bit as a single light switch—on (1) or off (0).
- **Byte**: A group of 8 bits—a tiny bundle that can represent numbers from 0 to 255.
- **Octet**: Just another word for a group of 8 bits (or a byte).

When you see an IP address like `192.168.1.5`, each of those four numbers is an **octet**.  
The entire address, written in this way, is called **dotted decimal notation**.

---

## How Do We Organize All These Addresses? (Hierarchical Addressing)

If every device in the world just picked a random address, it would be chaos! Routers wouldn’t know where to send anything.  
Instead, we organize IP addresses into networks—like having cities, neighborhoods, and house numbers.

- **Network address**: Identifies a group of devices (like a city or a street).
- **Host address**: Identifies the specific device (like a house number).

**Example:**  
In `172.16.30.56`  
- `172.16` = the network  
- `30.56` = the host

---

## IP Address Classes (A, B, C, D, E): How the World Divides Address Space

When the Internet was invented, engineers grouped addresses into classes—like making small, medium, and large neighborhoods.

### Class A
- **First number (octet):** 1-126
- **For HUGE networks** (like mega corporations or ISPs)
- **Example:** `10.34.12.3`
- Can support millions of hosts in one network!

### Class B
- **First number (octet):** 128-191
- **Medium-sized networks** (like universities, big companies)
- **Example:** `172.16.5.4`
- Supports tens of thousands of hosts.

### Class C
- **First number (octet):** 192-223
- **Small networks** (like homes, small offices)
- **Example:** `192.168.1.1`
- Supports up to 254 hosts per network.

> **Fun Fact:**  
> Addresses starting with 127 are reserved for something special: loopback testing (`127.0.0.1` is “this computer”).

### Class D and E
- **Class D (224–239):** For sending messages to many devices at once (multicast).
- **Class E (240–255):** Reserved for experiments, not used in normal networks.

---

## Public vs. Private IP Addresses (RFC 1918)

Not all IP addresses are allowed to be used on the public Internet!  
Private IP addresses are like house numbers on a private road—not visible from outside your gated community. They’re used inside your home or business so you don’t “waste” valuable public addresses.

**Here are the private ranges you must memorize:**

- **Class A:** `10.0.0.0 – 10.255.255.255`
- **Class B:** `172.16.0.0 – 172.31.255.255`
- **Class C:** `192.168.0.0 – 192.168.255.255`

**Why do we use private IPs?**  
Because there aren’t enough public addresses for everyone in the world, especially as we connect more and more devices.

**How do we connect private devices to the Internet?**  
We use a system called **NAT** (Network Address Translation), like a receptionist in your company’s front office. When you send mail (data) to the Internet, NAT swaps your private return address for a public one. When mail comes back, NAT knows which device it should deliver it to.

---

## APIPA (Automatic Private IP Addressing)

What if your device tries to get an address automatically (via DHCP), but can’t find the “address assigner”?  
Windows and other systems will just assign themselves an address in the range **169.254.0.1 – 169.254.255.254**.  
This is called **APIPA**.

- You’ll see this if there’s a network problem: your computer can talk to other local computers (on the same switch), but NOT out to the Internet.

---

## Types of IPv4 Communication

- **Unicast**: One-to-one (like sending a letter to a specific house).
- **Broadcast**: One-to-all (like shouting so everyone in the neighborhood hears).
- **Multicast**: One-to-many (like sending an invite only to friends who subscribed to your party).

---

## Subnetting, VLSM, and CIDR (Not-Too-Scary Version!)

Early networks used classes (A, B, C), but that wasted address space.  
**Subnetting** allows you to divide a network into smaller groups, making it easier to manage and not waste addresses.  
**VLSM** (Variable Length Subnet Mask) and **CIDR** (Classless Inter-Domain Routing) are advanced ways to slice networks up exactly as needed—no more waste!

> **Example:** Instead of giving a small office a huge Class A block, you just give them a “slice” with enough addresses.

---

## Special Addresses

- `0.0.0.0` = “any network” (used for default routes)
- `255.255.255.255` = “all hosts” (broadcast)
- `127.0.0.1` = loopback (your own computer)
- Last address in a subnet = broadcast address for that subnet

---

## Why Did We Invent IPv6?

Let’s face it—we ran out of addresses. With only about 4.3 billion possible IPv4 addresses, and with every person (and their phone, TV, fridge, etc.) needing one, it’s not enough!

- **IPv6** is the “next generation” of IP addressing.
- Uses 128 bits instead of 32 bits
- That’s enough addresses for every grain of sand on Earth (seriously—3.4 x 10³⁸ addresses)

---

## IPv6: What’s Different?

- Looks different: Eight groups of four hex digits, separated by colons.  
  Example: `2001:0db8:3c4d:0012:0000:0000:1234:56ab`
- Can be shortened: Drop leading zeros or groups of zeros:  
  `2001:db8:3c4d:12::1234:56ab`
- No broadcasts: Uses multicast and unicast (and a new one: anycast)

### Special addresses:
- `::1` = loopback (like 127.0.0.1 in IPv4)
- `FE80::/10` = link-local (like APIPA, not routed)
- `FC00::/7` = unique local (like IPv4 private)

### IPv6 Address Types
- **Unicast:** Sent to a single device
- **Multicast:** Sent to many devices
- **Anycast:** Sent to any one of a group (like “nearest server wins”)

---

## How Does IPv6 Assign Addresses?

There are two ways:

**1. Stateless Address Autoconfiguration (SLAAC):**  
Devices make up their own address based on the network prefix and their MAC address. It’s automatic!

**2. DHCPv6:**  
Like DHCP in IPv4, but works with IPv6 addresses and can provide more settings.

**EUI-64:**  
When using SLAAC, your device creates a unique address by splitting its MAC address and sticking “FF:FE” in the middle, then flipping the 7th bit (don’t worry, the computer does it for you).

---

## How Do We Migrate to IPv6?

You can’t just flip a switch! Most real networks run both IPv4 and IPv6 for years:

- **Dual Stack:** Devices run both IPv4 and IPv6. They can talk to old and new networks.
- **Tunneling (6to4, Teredo, Miredo):** IPv6 traffic is wrapped inside IPv4 packets to travel across parts of the Internet that don’t understand IPv6 yet.

---

## Summary Table: Key Things to Remember

| Class | First Octet | Networks Possible | Hosts per Network | Private Range                     |
|-------|-------------|-------------------|-------------------|-----------------------------------|
| A     | 1-126       | 126               | 16,777,214        | 10.0.0.0 – 10.255.255.255         |
| B     | 128-191     | 16,384            | 65,534            | 172.16.0.0 – 172.31.255.255       |
| C     | 192-223     | 2,097,152         | 254               | 192.168.0.0 – 192.168.255.255     |

Other key addresses:
- **APIPA:** `169.254.0.1 – 169.254.255.254`
- **Loopback:** `127.0.0.1`
- **Broadcast:** `255.255.255.255`

---

## Exam Pointers and Real-World Tips

- Remember your class ranges (A: 1–126, B: 128–191, C: 192–223)
- Private IPs: `10.x.x.x`, `172.16–31.x.x`, `192.168.x.x`
- APIPA is `169.254.x.x`—means network or DHCP problem!
- IPv6 is coming—get familiar with its notation and concepts

---

## TL;DR / “If You Only Remember Three Things…”

1. IP addresses are how devices find and talk to each other, like house addresses.
2. IPv4 addresses are running out, so we invented IPv6 (with way more space).
3. You must know your address classes and private ranges for the exam and for troubleshooting.

---

# What is Subnetting? (And Why Do We Need It?)

Imagine you’re managing a big office building. If you gave every single person a key to every single room, things would get chaotic. Instead, you give out keys that only open the rooms people need.

**Subnetting works the same way.**

- You start with one big network (like a building).
- You divide it into smaller groups (subnets), so only people in each group have access to their section.

**Why do this?**
- **Organization:** Makes the network easier to manage.
- **Security:** Keeps traffic separate (HR can’t see IT’s traffic).
- **Efficiency:** Reduces wasted IP addresses.
- **Performance:** Local traffic stays local—less congestion.

---

## How Are IP Addresses Divided?

Every IPv4 address has two parts:
- **Network part:** Tells routers which “building” the address is in.
- **Host part:** Tells devices inside the building which room you want.

The dividing line is called the **subnet mask**.

**Example:**  
`192.168.1.15` with subnet mask `255.255.255.0`

**Subnet mask in binary:**
255.255.255.0 = 11111111.11111111.11111111.00000000


- The 1’s (left side) = network
- The 0’s (right side) = host

---

## What Does a Subnet Mask Look Like?

The subnet mask tells devices which part of the IP is the network and which part is the host.

- `/24` (read as “slash twenty-four”) means the first 24 bits are the network (`255.255.255.0`)
- `/16` means the first 16 bits are the network (`255.255.0.0`)

**CIDR notation** uses the “slash” to show how many bits are network bits.

---

## Subnetting Example: Making Smaller Networks

Suppose your company gets `192.168.1.0/24`  
That’s 256 addresses: `192.168.1.0` to `192.168.1.255`  
Usable for hosts: `192.168.1.1` to `192.168.1.254` (the first is the network address, the last is the broadcast address)

But you have 4 departments, and you want each to have their own network.

**Step 1:** Decide How Many Subnets You Need  
4 departments = 4 subnets

**Step 2:** Find the Right Subnet Mask  
- `/24` = `255.255.255.0` (1 subnet, 254 hosts)
- `/26` = `255.255.255.192` (4 subnets, 62 hosts each)
  - Why `/26`? 2 bits for subnetting (because 2² = 4)
  - 192 in binary = `11000000`

**Step 3:** List Your Subnets

| Subnet # | Network Address    | Usable Hosts     | Broadcast Address   |
|----------|--------------------|------------------|---------------------|
| 1        | 192.168.1.0/26     | .1 – .62         | 192.168.1.63        |
| 2        | 192.168.1.64/26    | .65 – .126       | 192.168.1.127       |
| 3        | 192.168.1.128/26   | .129 – .190      | 192.168.1.191       |
| 4        | 192.168.1.192/26   | .193 – .254      | 192.168.1.255       |

Each subnet can have up to 62 devices.

---

## How Do You Know Which Subnet Mask to Use?

Use the formula:
- **Number of subnets = 2ⁿ** (n = number of subnet bits)
- **Number of hosts per subnet = 2ʰ – 2** (h = number of host bits, subtract 2 for network and broadcast)

**Example:** Want 8 subnets from a /24 block?
- 2³ = 8 (so, use 3 bits for subnets)
- Subnet mask: `255.255.255.224` (/27)
- Each subnet: 2⁵ – 2 = 30 hosts

---

## Variable Length Subnet Mask (VLSM): Slicing More Precisely

**VLSM** means you don’t have to cut every piece the same size.

- Big departments get big subnets, small ones get small subnets.

**Example:**
- One department needs 100 hosts: give them a `/25` (128 addresses)
- Another needs 10 hosts: give them a `/28` (16 addresses)

---

## Real-World Reasons for Subnetting

- **Security:** Sales can’t see HR’s files
- **Performance:** Broadcasts don’t swamp the whole network
- **Scalability:** Easily add new departments (subnets) as you grow
- **Troubleshooting:** Easier to find and fix network problems

---

## Subnetting in CIDR (Classless Inter-Domain Routing)

Before CIDR, addresses were always handed out in big blocks (Class A, B, C).  
With CIDR, ISPs and organizations can give you just the number of addresses you actually need (no more waste).

> **Example:** Instead of giving a small company all of `192.168.1.0/24`, give them just `192.168.1.32/28` (16 addresses).

---

## Practice: Identify Subnet, Network, Host

If you see an address like `172.16.5.130/20`:
- `/20` = `255.255.240.0` (16 class C networks combined)
- Network address: `172.16.0.0`
- Broadcast address: `172.16.15.255`
- Host range: `172.16.0.1` to `172.16.15.254`

---

## Summary Table: Common Subnet Masks

| CIDR | Subnet Mask       | # Subnets (from /24) | # Hosts/Subnet |
|------|-------------------|---------------------|----------------|
| /24  | 255.255.255.0     | 1                   | 254            |
| /25  | 255.255.255.128   | 2                   | 126            |
| /26  | 255.255.255.192   | 4                   | 62             |
| /27  | 255.255.255.224   | 8                   | 30             |
| /28  | 255.255.255.240   | 16                  | 14             |
| /29  | 255.255.255.248   | 32                  | 6              |
| /30  | 255.255.255.252   | 64                  | 2              |

---

## Final Tips

- Always subtract 2 from your host count: 1 for the network address, 1 for the broadcast address.
- Subnetting lets you be efficient and secure.
- CIDR and VLSM allow flexible, no-waste networks.




# Subnetting Examples

Subnetting is the process of dividing a single network into smaller, more manageable pieces.

---

## Example 1: Divide a /24 Network into 4 Subnets

Suppose you have the network `192.168.10.0/24` and need to split it into **4 equal subnets**.

### Step-by-Step

1. **Determine subnet bits:**  
   Need 4 subnets → 2 bits (2² = 4)
2. **New subnet mask:**  
   `/26` or `255.255.255.192`
3. **Hosts per subnet:**  
   2⁶ − 2 = **62**

**Subnets Table:**

| Subnet # | Network Address     | Usable Hosts            | Broadcast Address   |
|----------|---------------------|-------------------------|--------------------|
| 1        | 192.168.10.0/26     | 192.168.10.1 – .62      | 192.168.10.63      |
| 2        | 192.168.10.64/26    | 192.168.10.65 – .126    | 192.168.10.127     |
| 3        | 192.168.10.128/26   | 192.168.10.129 – .190   | 192.168.10.191     |
| 4        | 192.168.10.192/26   | 192.168.10.193 – .254   | 192.168.10.255     |

---

## Example 2: Subnetting a /24 into 8 Subnets

- **Network:** `10.0.0.0/24`
- **Borrowed bits:** 3 (2³ = 8)
- **New subnet mask:** `/27` (`255.255.255.224`)
- **Hosts/subnet:** 2⁵ − 2 = **30**

| Subnet # | Network Address   | Usable Hosts              | Broadcast Address   |
|----------|-------------------|---------------------------|--------------------|
| 1        | 10.0.0.0/27       | 10.0.0.1 – 10.0.0.30      | 10.0.0.31          |
| 2        | 10.0.0.32/27      | 10.0.0.33 – 10.0.0.62     | 10.0.0.63          |
| 3        | 10.0.0.64/27      | 10.0.0.65 – 10.0.0.94     | 10.0.0.95          |
| 4        | 10.0.0.96/27      | 10.0.0.97 – 10.0.0.126    | 10.0.0.127         |
| 5        | 10.0.0.128/27     | 10.0.0.129 – 10.0.0.158   | 10.0.0.159         |
| 6        | 10.0.0.160/27     | 10.0.0.161 – 10.0.0.190   | 10.0.0.191         |
| 7        | 10.0.0.192/27     | 10.0.0.193 – 10.0.0.222   | 10.0.0.223         |
| 8        | 10.0.0.224/27     | 10.0.0.225 – 10.0.0.254   | 10.0.0.255         |

---

## Example 3: VLSM (Variable Length Subnet Mask)

Suppose you have `172.16.20.0/24` and three departments with different host needs:

- Dept A: **100 hosts** (`/25`)
- Dept B: **50 hosts** (`/26`)
- Dept C: **10 hosts** (`/28`)

**Subnet Assignments:**


Dept A: 172.16.20.0/25 Hosts: 172.16.20.1 – 172.16.20.126 Broadcast: 172.16.20.127


Dept B: 172.16.20.128/26 Hosts: 172.16.20.129 – 172.16.20.190 Broadcast: 172.16.20.191


Dept C: 172.16.20.192/28 Hosts: 172.16.20.193 – 172.16.20.206 Broadcast: 172.16.20.207


---

## Example 4: CIDR Practice – Identify Subnet, Network, Host

**Given:**  
IP Address: `172.16.5.130/20`  
Subnet Mask: `255.255.240.0`

- **Network address:** `172.16.0.0`
- **Broadcast address:** `172.16.15.255`
- **Usable hosts:** `172.16.0.1` – `172.16.15.254`

---

## Subnet Mask and Host Reference Table

| CIDR | Subnet Mask       | # Subnets (from /24) | # Hosts/Subnet |
|------|-------------------|----------------------|----------------|
| /24  | 255.255.255.0     | 1                    | 254            |
| /25  | 255.255.255.128   | 2                    | 126            |
| /26  | 255.255.255.192   | 4                    | 62             |
| /27  | 255.255.255.224   | 8                    | 30             |
| /28  | 255.255.255.240   | 16                   | 14             |
| /29  | 255.255.255.248   | 32                   | 6              |
| /30  | 255.255.255.252   | 64                   | 2              |

---

## **Subnetting Quick Tips**

- **Always subtract 2** from your host count (1 for the network address, 1 for the broadcast address).
- **Formula:**  
  - Number of subnets = `2^n` (n = subnet bits)  
  - Hosts per subnet = `2^h – 2` (h = host bits)
- **CIDR notation:** `/24` = `255.255.255.0`, `/26` = `255.255.255.192`, etc.
