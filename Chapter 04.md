Chapter 4: The Current Ethernet Specifications (Summary)
This chapter covers the essential concepts and standards behind Ethernet, which is the foundation of most local area networks (LANs) today.

Ethernet Basics and LAN Communication
Ethernet is the main protocol used for connecting computers within a LAN.

Devices communicate using MAC addresses (hardware addresses burned into NICs), not hostnames or IP addresses at the Ethernet level.

If a device knows only another device’s name or IP, it uses protocols like DNS and ARP to discover the MAC address.

On a hub, all devices share the same collision domain and broadcast domain. A switch creates a separate collision domain for each port, reducing collisions and improving network efficiency.

Collision Domains, Broadcast Domains, and CSMA/CD
Collision domain: Where data collisions can happen. Hubs extend the collision domain; switches separate them.

Broadcast domain: All devices that receive broadcast frames. Routers separate broadcast domains.

CSMA/CD (Carrier Sense Multiple Access with Collision Detection):

Prevents two devices from transmitting at the same time.

If a collision occurs, all devices stop, wait a random period (backoff), then try again.

Duplex Modes
Half-duplex: Data can only travel one direction at a time (uses CSMA/CD). Common on old hubs.

Full-duplex: Data can travel both ways simultaneously. No collisions. Common with switches and modern NICs. Requires a dedicated switch port for each host.

Bit Rate vs. Baud Rate
Bit rate: Number of bits sent per second (bps). Modern term.

Baud rate: Number of signal changes per second. Was common with old modems.

Binary, Decimal, and Hexadecimal
Networking uses all three number systems, especially for addressing (e.g., subnet masks, MAC addresses).

You should know how to convert between binary, decimal, and hexadecimal (important for subnetting and MAC address understanding).

Ethernet Addressing and Frames
MAC address: 48 bits (6 bytes) in hexadecimal. Format: AA:BB:CC:DD:EE:FF.

First 24 bits: OUI (vendor).

Last 24 bits: Unique value for the device.

MAC addresses indicate unicast (single device), multicast, or broadcast (all devices).

Ethernet frame: Structure includes preamble, destination MAC, source MAC, type/length, data, and CRC (FCS) for error checking (not correction).

Ethernet_II frames: Most common in modern networks; includes protocol type field (e.g., 0x0800 for IPv4, 0x86DD for IPv6).

Ethernet Physical Layer and Cabling Standards
Ethernet was originally standardized by DIX (Digital, Intel, Xerox) and later by IEEE as 802.3.

Media types and speeds:

10Base2 (Thinnet): 10 Mbps, coaxial, 185m.

10Base5 (Thicknet): 10 Mbps, coaxial, 500m.

10BaseT: 10 Mbps, Cat 3 UTP, 100m, star topology.

100BaseTX (Fast Ethernet): 100 Mbps, Cat 5/5e/6 UTP, 100m.

100BaseFX: 100 Mbps, multimode fiber, up to 2,000m.

1000BaseT (Gigabit Ethernet): 1 Gbps, Cat 5/5e/6 UTP, 100m.

1000BaseSX/LX: 1 Gbps, multimode/singlemode fiber, various lengths.

10GBaseT: 10 Gbps, Cat 6a/7 UTP, 100m.

40GBaseT: 40 Gbps, Cat 8, 30m, mainly for data centers.

Fiber vs. Copper: Fiber-optic is immune to EMI and supports longer distances; copper (UTP/STP) is easier and cheaper for shorter runs.

Other Ethernet Media
Ethernet over Power Line: Uses electrical wiring for data transfer (IEEE 1901).

Ethernet over HDMI: Sends network traffic along with video/audio through HDMI cables.

IEEE 1905.1: A standard for converged digital home networks, combining Ethernet, Wi-Fi, powerline, and coax.

Key Takeaways
Understand how Ethernet devices communicate using MAC addresses.

Know the difference between collision domains and broadcast domains.

Know basic duplex concepts and why full-duplex is better.

Be familiar with major cabling types and IEEE 802.3 standards.

Practice binary, decimal, and hex conversion for subnetting and MAC addresses.

