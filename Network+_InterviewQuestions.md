# Chapter 1: Introduction to Networks


### 1. Explain the difference between a LAN and a WAN. In what situation would you use each?

**LAN** is connecting devices in a particular location such as an office building, a single department within an office.
**WAN** is connecting LANs and to connect LANs, they will need routers.

LAN is best used for small networks like small office, SOHO.

WAN is best used for connecting to devices using internet


### 2. Your company is expanding. What network topology would you recommend for scalability and ease of troubleshooting — star, mesh, or hybrid? Why?

If my company is expanding and ease of toubleshooting is a priority, I need to use the star topology because each devices has its own separate cable that connects them to the central device like a switch

### 3. Describe the three-tier hierarchical network model. What role does each layer play in a corporate environment?

Core layer
Distribution layer
Access layer


### 4. A small business has a limited budget but needs network reliability. Would you recommend a collapsed-core architecture or a full three-tier model? Justify your answer.

### 5. What are the key differences between physical and logical network topologies? Can you give examples of each?

### 6. A company uses a spine-leaf topology in its data center. What kind of traffic flow does this topology optimize, and why is it important?

### 7. What are north-south and east-west traffic flows in a network? Why should a network engineer be aware of both?

### 8. How would you connect two remote LANs together? What technologies or methods are typically used?

### 9. During a site evaluation, how would you determine the most appropriate topology to use for a client's network? What factors would influence your decision?

### 10. What is the function of a virtual NIC (vNIC), and how is it used in virtualized environments?



# Chapter 2: The Open Systems Interconnection (OSI) Reference Model

### 1. Can you describe the purpose of the OSI model and explain why it's still important today even if real-world networking often uses the TCP/IP model?

### 2. You’re troubleshooting a network application that is having trouble encrypting data before transmission. Which OSI layer would you investigate, and why?

### 3. If a user reports that their device receives data but cannot respond back, which OSI layer(s) would you suspect and what would you look for?

### 4. Give an example of how the Session layer operates in real-world networking applications. How is this layer different from the Transport layer?

### 5. An engineer says their device uses logical addressing and makes routing decisions. Which OSI layer is this, and what are the practical responsibilities of this layer?

### 6. What’s the role of encapsulation in the OSI model? Can you describe the steps that occur as data moves from Layer 7 down to Layer 1?

### 7. Your task is to implement flow control and ensure reliable delivery of data. Which OSI layer and protocol should you focus on?

### 8. In the Data Link layer, what is the difference between the MAC and LLC sublayers, and what role do they each play?

### 9. Why is it beneficial to divide network communication into layered models like OSI? Name at least two advantages this design offers.

### 10. A wireless device is failing to transmit any data. Assuming physical connections are working, which OSI layer would you troubleshoot first, and what would you check?


# Chapter 3: Networking Connectors and Wiring Standards

### 1. You're tasked with connecting two network switches. Which cable type would you use, and why? How would this choice change if the switches support auto-MDI/MDI-X?

### 2. Explain the difference between plenum-rated and non-plenum-rated cables. In what environments is each type used, and why does it matter?

### 3. A client wants to run 10 Gbps Ethernet across 100 meters. What category of twisted-pair cable would you recommend and why?

### 4. During a fiber-optic installation, what considerations help you decide between single-mode and multimode fiber? Provide real-world scenarios where each would be used.

### 5. Describe the difference between T568A and T568B wiring standards. How would mixing these standards at opposite cable ends impact a network?

### 6. What connector types are commonly used with fiber-optic cables, and how do they differ in terms of usage and physical characteristics?

### 7. A technician reports signal interference on a copper cable installation near industrial machinery. What type of cabling would you suggest as a solution, and why?

### 8. What role does a media converter play in network design, and when is it typically required?

### 9. Can you explain what an MDF and IDF are in a network installation? How do they relate to cable organization?

### 10. You're inspecting a site with various cabling standards and equipment. What steps would you take to verify that the cabling infrastructure is compliant and reliable?



# Chapter 4: The Current Ethernet Specifications

### 1. How does CSMA/CD work in an Ethernet network, and why is it primarily used in half-duplex environments?

### 2. A technician is reviewing Ethernet frame data. What does the Frame Check Sequence (FCS) do, and how does it ensure data integrity?

### 3. Compare the purpose of the Ethernet frame's preamble and the Start of Frame Delimiter (SFD). Why are both necessary?

### 4. Where is the destination MAC address found in a Layer 2 Ethernet frame, and why is it placed there?

### 5. What is the Organizationally Unique Identifier (OUI) in a MAC address, and how is it used?

### 6. In what situation would the I/G (Individual/Group) bit in a MAC address be set to 1, and what does this indicate?

### 7. Explain the difference between 10Base2, 10Base5, and 10BaseT. Which, if any, are still seen in use today?

### 8. What is attenuation in the context of Ethernet cabling, and how can it be minimized when designing a network?

### 9. Describe the key differences between the Media Independent Interface (MII) and the Gigabit Media Independent Interface (GMII). What role do they serve?

### 10. What Ethernet standard would you use for a high-performance backbone connection between core switches in a modern data center?

### 11. What is Ethernet over HDMI, and how is it typically used in home or entertainment networks?

### 12. Explain how MAC addresses facilitate communication on a LAN, and why they are essential even when using IP addresses.

### 13. What are the advantages and limitations of using coaxial cable for Ethernet communication today?

### 14. Describe how duplex mismatches can cause performance issues in Ethernet networks. How would you detect and resolve such a problem?

### 15. A user reports extremely slow network speeds. How would you determine whether the issue is related to the Ethernet standard or cable quality?


# Chapter 5: Networking Devices

### 1. How does a switch differ from a hub in terms of collision and broadcast domains?

### 2. You're designing a network for a small office. Would you choose a Layer 2 switch or a Layer 3 switch for basic segmentation and why?

### 3. Describe the role of a router in a corporate environment. How does it manage traffic between different networks?

### 4. What is the main advantage of using a firewall in a network? How do stateful and stateless firewalls differ?

### 5. How does a wireless access point (WAP) differ from a wireless range extender in both function and placement?

### 6. You are asked to deploy a DHCP server. What key elements must you configure to ensure clients receive proper IP configurations?

### 7. Compare and contrast autonomous vs. lightweight access points. When would you use each type?

### 8. In a network with high traffic demand, how would you implement load balancing? What type of device or service would you use?

### 9. What function does a proxy server serve in a business network, and how does it improve security?

### 10. How does a media converter work, and in what scenario would you implement one?

### 11. You are connecting legacy phone systems to a modern VoIP infrastructure. What device do you need, and what protocols should it support?

### 12. Explain the difference between a cable modem and a DSL modem. What media and technology do they each rely on?

### 13. What role do Internet of Things (IoT) devices play in a modern network, and what are the security considerations?

### 14. You’re reviewing a network layout that includes an IDS/IPS system. How do IDS and IPS differ in terms of threat response?

### 15. How would you segment a SOHO network to separate guest devices from internal business devices? What tools or devices would help you accomplish this?


# Chapter 6: Introduction to the Internet Protocol

### 1. What is the purpose of the TCP/IP protocol suite, and how does it relate to the OSI model?

### 2. Explain the process of data encapsulation in the context of TCP/IP and the OSI model.

### 3. Compare and contrast TCP and UDP. In which scenarios would you choose one over the other?

### 4. What role does the Internet Protocol (IP) play within the TCP/IP stack?

### 5. A user is experiencing dropped packets. What Transport layer mechanism can help ensure reliable delivery?

### 6. What are well-known ports, and why is it important for network professionals to understand them?

### 7. How does the concept of virtual circuits apply to connection-oriented protocols like TCP?

### 8. Describe the purpose and function of the Address Resolution Protocol (ARP) in a TCP/IP network.

### 9. What are the differences between the Authentication Header (AH) and Encapsulating Security Payload (ESP) in IPSec?

### 10. Explain how IP fragmentation occurs and how the reassembly process works on the receiving host.

### 11. A user accesses a secure website via HTTPS. Which ports and protocols are involved in this transaction?

### 12. Why would an organization choose to implement GRE tunneling, and what are its limitations?

### 13. How does a DHCP server assign IP addresses, and what steps occur during the lease process?

### 14. What are the roles of the three-way handshake and acknowledgments in TCP connections?

### 15. Explain the significance of port numbers in identifying network services and managing multiple sessions.

### 16. Which protocol is used to synchronize time across network devices, and why is this important?

### 17. What diagnostic functions are provided by the Internet Control Message Protocol (ICMP)?

### 18. You need to transfer a large file across a network with minimal configuration. Would you use FTP or TFTP? Why?

### 19. Describe the concept of socket pairs (IP address and port number) in TCP connections.

### 20. What is the role of the Session layer in the context of TCP/IP communication?

### 21. How does DNS use port 53 differently for TCP and UDP communications?

### 22. A user receives an IP in the 169.254.x.x range. What does this indicate, and how should you respond?

### 23. What protocols operate at the Application layer of the TCP/IP model? Give examples.

### 24. How does NAT interact with TCP/IP packet headers when routing to the Internet?

### 25. Explain how IPSec secures IP communications and the role of IKE in this process.


# Chapter 7: IP Addressing

### 1. What is the purpose of an IP address, and how does it differ from a MAC address?

### 2. Explain the hierarchical nature of IP addressing. Why is this structure important?

### 3. How many hosts can be assigned in a default Class C network? How about Class B?

### 4. What is the difference between a network address and a broadcast address?

### 5. Describe the structure of an IPv4 address in dotted decimal format.

### 6. What are the ranges of IP addresses in Class A, B, and C?

### 7. Why can’t the first and last IP addresses in a subnet be assigned to hosts?

### 8. What are the key differences between public and private IP address ranges?

### 9. What is RFC1918, and why is it significant for IP addressing?

### 10. What is APIPA, and under what conditions is it used?

### 11. A host receives an IP in the 169.254.x.x range. What does this indicate, and how would you troubleshoot it?

### 12. What are unicast, multicast, broadcast, and anycast addresses? Give examples of each.

### 13. What is the loopback IP address and what is it commonly used for?

### 14. When would a network administrator use CIDR notation?

### 15. How does VLSM (Variable Length Subnet Mask) improve IP addressing efficiency?

### 16. What is the purpose of subnetting? Give a real-world example.

### 17. Define the term "default gateway" and explain its role in networking.

### 18. Compare IPv4 and IPv6 in terms of address length and structure.

### 19. What are some of the advantages of IPv6 over IPv4?

### 20. Describe how IPv6 addresses are written and shortened using rules.

### 21. What is SLAAC, and how does it differ from DHCP in IPv6 networks?

### 22. Explain what a link-local IPv6 address is and when it is used.

### 23. What is the function of the EUI-64 format in IPv6?

### 24. What is a unique local address in IPv6 and how is it different from a global unicast?

### 25. How does dual-stack implementation work in transitioning to IPv6?

### 26. What is NAT64 and in what situation would you use it?

### 27. You see a host using the address `FE80::/10`. What does this indicate?

### 28. What is a multicast address in IPv6 and how does it differ from IPv4 multicast?

### 29. What are the reserved address ranges for loopback and documentation purposes in IPv6?

### 30. What happens when a host sends a packet to 255.255.255.255 in IPv4?


# Chapter 8: IP Subnetting, Troubleshooting IP, and Introduction to NAT

### 1. What is subnetting, and why is it essential in modern IP networks?

### 2. Explain how borrowing bits from the host portion of an IP address allows subnetting.

### 3. How do you calculate the number of subnets and hosts in a given subnet mask?

### 4. What is the block size in subnetting, and how do you determine it?

### 5. A network uses a /26 mask. How many valid hosts per subnet does this allow?

### 6. Why is the formula 2^n - 2 used when calculating host addresses?

### 7. What is CIDR, and how does it differ from traditional classful addressing?

### 8. How does VLSM contribute to more efficient use of IP address space?

### 9. Explain how to identify valid host ranges within a subnet.

### 10. How can you determine the broadcast address of a subnet?

### 11. What are some real-world benefits of subnetting large networks?

### 12. What four diagnostic steps are recommended when troubleshooting IP addressing issues?

### 13. How would you troubleshoot a host that cannot access the internet but can ping internal resources?

### 14. What is the purpose of the loopback address, and how is it used in troubleshooting?

### 15. When would a ping to the default gateway fail, and what would that indicate?

### 16. Describe a situation where a subnetting misconfiguration could cause a network outage.

### 17. What is the difference between inside local and inside global addresses in NAT?

### 18. How does static NAT differ from dynamic NAT?

### 19. What is PAT (Port Address Translation), and how does it conserve public IP addresses?

### 20. What is a NAT table, and what role does it play in packet forwarding?

### 21. In what situations would you use port forwarding?

### 22. How does NAT improve network security?

### 23. Why might a network use both public and private IP addresses, and how is NAT involved?

### 24. What is the difference between SNAT and DNAT?

### 25. What are the limitations of NAT in peer-to-peer and real-time communication applications?

### 26. What tools or commands can help verify correct NAT operation?

### 27. When troubleshooting NAT issues, what specific configuration details should you check?

### 28. Describe the role of a default gateway in relation to NAT.

### 29. What is a virtual IP (VIP), and how does it relate to NAT?

### 30. How can subnetting and NAT work together to support large enterprise networks?


# Chapter 9: Introduction to IP Routing

### 1. What is the primary role of a router in a network, and how does it make forwarding decisions?

### 2. How do routed protocols differ from routing protocols? Give an example of each.

### 3. Describe the end-to-end process of IP routing when Host A sends a packet to Host B on a different subnet.

### 4. What happens to a data packet as it passes through multiple routers in terms of frames and packets?

### 5. Why is it important to understand that MAC addresses are only used on local LANs during routing?

### 6. What is the difference between a static route and a dynamic route, and when would you use each?

### 7. Describe the function of the routing table on a router. What key pieces of information does it contain?

### 8. How does a router determine the best path to a destination network?

### 9. What is the administrative distance (AD), and how is it used in the routing decision process?

### 10. What is meant by the term “convergence” in the context of routing?

### 11. A network has multiple paths to a destination. What factors influence which path a router chooses?

### 12. What are the benefits and drawbacks of manually configuring static routes in a large network?

### 13. How would you test whether a router has learned a specific route successfully?

### 14. What tools or commands can you use to verify and troubleshoot routing issues on a network?

### 15. Describe how hybrid routing protocols like EIGRP combine characteristics of both distance-vector and link-state protocols.


# Chapter 10: Routing Protocols

### 1. What is the primary purpose of a dynamic routing protocol compared to static routing?

### 2. Define the difference between an IGP (Interior Gateway Protocol) and an EGP (Exterior Gateway Protocol). Provide examples of each.

### 3. How does a router use administrative distance (AD) to make routing decisions?

### 4. What is a metric in routing protocols, and how is it used in route selection?

### 5. What is the significance of routing convergence, and how does it affect network performance?

### 6. Compare distance-vector, link-state, and hybrid routing protocols with examples.

### 7. What is “routing by rumor,” and which class of routing protocols use this approach?

### 8. How does RIP determine the best path to a destination network?

### 9. What limitations does RIP have, and why might it not be ideal for large networks?

### 10. How does RIPv2 improve upon RIPv1?

### 11. What multicast address does RIPv2 use for route advertisements?

### 12. Explain the role of the DUAL algorithm in EIGRP.

### 13. How does EIGRP combine features of distance-vector and link-state protocols?

### 14. What is the difference between internal and external EIGRP?

### 15. What is the default administrative distance for RIP, EIGRP, OSPF, and BGP?

### 16. How does OSPF use link-state advertisements (LSAs) to build a routing table?

### 17. What is the purpose of OSPF areas, and how do they help scale large networks?

### 18. What multicast addresses does OSPF use to communicate with routers?

### 19. Describe the difference between a designated router (DR) and a backup designated router (BDR) in OSPF.

### 20. What makes BGP a hybrid routing protocol, and when is it typically used?

### 21. What is the difference between iBGP and eBGP?

### 22. Why is BGP considered a path vector protocol?

### 23. What risks are associated with enabling multiple routing protocols on the same router?

### 24. What is a First Hop Redundancy Protocol (FHRP), and how does it support gateway availability?

### 25. How does IPv6 routing differ from IPv4 routing in terms of protocol use and address handling?


# Chapter 11: Switching and Virtual LANs

### 1. What are the three primary functions of a switch, and how does each support network efficiency?

### 2. How do switches learn the location of hosts on the network?

### 3. What is a collision domain, and how does switching help reduce it?

### 4. Explain how a broadcast domain differs from a collision domain.

### 5. What problem does the Spanning Tree Protocol (STP) solve in switched networks?

### 6. Describe how STP prevents switching loops. What are port states?

### 7. What are the key differences between STP and RSTP?

### 8. What is a root bridge in STP, and how is it elected?

### 9. What happens in a network if no loop prevention mechanism like STP is in place?

### 10. Define VLAN. What are its advantages in a corporate network?

### 11. What is the difference between an access port and a trunk port?

### 12. How does 802.1Q tagging work, and what information is included in the tag?

### 13. Explain the concept of a native VLAN and its default behavior.

### 14. What is inter-VLAN routing, and how can it be implemented?

### 15. What is “router-on-a-stick,” and when would you use this configuration?

### 16. How do Switch Virtual Interfaces (SVIs) enable communication between VLANs?

### 17. What is the function of VTP (VLAN Trunking Protocol), and what modes does it support?

### 18. Describe the role of port security in a switched network.

### 19. How can enabling jumbo frames benefit a storage or data-heavy environment?

### 20. What are the risks associated with jumbo frames if all switches don’t support the same MTU?

### 21. Explain the use of link aggregation and its benefits.

### 22. What is the purpose of Power over Ethernet (PoE), and where is it commonly used?

### 23. Describe the difference between a managed and unmanaged switch.

### 24. What is port mirroring (SPAN), and how is it useful in network analysis?

### 25. How does Remote SPAN (RSPAN) differ from local SPAN?

### 26. How do voice VLANs differ from data VLANs, and why are they important?

### 27. What tools or techniques can you use to troubleshoot VLAN misconfigurations?

### 28. How does flooding differ from forwarding on a switch?

### 29. Why is VLAN membership important when plugging a host into a switch port?

### 30. What is the impact of enabling trunking on links between switches without proper VLAN alignment?

### 31. What is EtherChannel and how does it improve bandwidth and redundancy between switches?

### 32. How does port channeling reduce the risk of STP blocking redundant links between switches?

### 33. Describe how LACP (Link Aggregation Control Protocol) functions and how it differs from static EtherChannel configuration.

### 34. What happens if one of the physical links in an EtherChannel bundle fails? How is traffic affected?

### 35. Why is it important to match configuration settings (speed, duplex, VLANs) on all interfaces in a port channel?


# Chapter 12: Wireless Networking

### 1. What is the purpose of the IEEE 802.11 family of standards?

### 2. Compare the characteristics of the 2.4 GHz, 5 GHz, and 6 GHz frequency bands.

### 3. How does CSMA/CA work in wireless networks, and why is it necessary?

### 4. What are non-overlapping channels, and how are they applied in the 2.4 GHz spectrum?

### 5. Describe the main differences between 802.11n, 802.11ac, and 802.11ax.

### 6. What are the common causes of wireless interference, and how can they be mitigated?

### 7. Explain the difference between omnidirectional and directional antennas.

### 8. What are SSID, BSSID, and ESSID? How do they relate to wireless network identification?

### 9. What are the key differences between infrastructure mode and ad hoc mode in wireless networking?

### 10. What is band steering, and how does it improve wireless network performance?

### 11. Describe the purpose and use of mesh networks.

### 12. How do guest networks and captive portals enhance network security and user management?

### 13. Compare WPA2 and WPA3 in terms of encryption and authentication.

### 14. What is the role of a RADIUS server in enterprise wireless networks?

### 15. How does PSK (Pre-Shared Key) authentication differ from enterprise-level authentication?

### 16. When would you use a wireless range extender, and what are its limitations?

### 17. What is the function of a wireless LAN controller (WLC) in large deployments?

### 18. Compare autonomous and lightweight access points in terms of management and deployment.

### 19. What is the significance of channel bonding in 802.11n?

### 20. What is site surveying in wireless networking, and why is it important before deployment?

### 21. How does antenna placement affect wireless coverage and performance?

### 22. What are some common best practices for securing a wireless network?

### 23. How does beamforming improve wireless performance?

### 24. What wireless standards are best suited for high-density environments?

### 25. What are regulatory considerations for deploying wireless networks in different countries?

### 26. Describe the differences between personal and enterprise wireless security models.

### 27. What steps would you take to troubleshoot a weak wireless signal in a corporate building?

### 28. What is the purpose of 802.11h and how does it relate to radar avoidance?

### 29. What is a heat map in wireless design, and how is it created?

### 30. How would you secure a wireless network in a public area like a coffee shop?


# Chapter 13: Remote Network Access

### 1. What is the difference between site-to-site VPN and client-to-site VPN?

### 2. When would a clientless VPN be a preferred solution?

### 3. What are the main differences between a split tunnel and a full tunnel VPN?

### 4. What are the pros and cons of using Remote Desktop Protocol (RDP) for remote access?

### 5. How does SSH enhance the security of remote access over Telnet?

### 6. What is a jump box or jump host, and where is it typically placed in a network architecture?

### 7. What distinguishes in-band management from out-of-band management?

### 8. What role does SSL/TLS play in securing remote access solutions?

### 9. How do VNC and RDP differ in how they transmit desktop sessions?

### 10. In what situation would you use a virtual desktop over a remote desktop?

### 11. What are the typical port numbers used by SSH, RDP, and VNC?

### 12. How does a RESTful API support remote access and device management?

### 13. Why is Telnet considered insecure, and what are secure alternatives?

### 14. What type of access does a clientless VPN typically allow?

### 15. What are the risks of exposing remote management interfaces to the public internet without proper security controls?


# Chapter 14: Using Statistics and Sensors to Ensure Network Availability

### 1. What is SNMP, and how does it help in network monitoring?

### 2. What is the purpose of a Management Information Base (MIB) in SNMP?

### 3. Compare the differences between SNMPv2c and SNMPv3.

### 4. What is an SNMP trap, and when is it triggered?

### 5. How is a baseline metric used in network performance monitoring?

### 6. What role does a Syslog server play in network monitoring?

### 7. What is a SIEM system and how does it improve security event management?

### 8. How does flow data like NetFlow help in understanding network traffic?

### 9. What are packet captures used for in troubleshooting?

### 10. How can anomaly detection help prevent downtime?

### 11. What metrics would you monitor on a network switch or router chassis?

### 12. What is the difference between latency, jitter, and packet loss?

### 13. How does configuration monitoring contribute to network compliance?

### 14. What is the benefit of using a network monitoring system (NMS)?

### 15. What are OIDs in SNMP, and how are they structured?

### 16. How do API integrations assist in modern network monitoring?

### 17. What are the key metrics you would monitor on a server to ensure performance?

### 18. How is bandwidth utilization calculated and interpreted?

### 19. What is the difference between scheduled and ad hoc network discovery?

### 20. What is port mirroring, and when would you use it?

### 21. Describe a use case for a log aggregator in a network environment.

### 22. How can monitoring tools help identify a rogue device or unauthorized configuration?

### 23. What kind of data can a protocol analyzer provide that other tools may miss?

### 24. What are CRC errors and how do they affect network reliability?

### 25. How does a performance baseline support effective troubleshooting?


# Chapter 15: Organizational Documents and Policies

### 1. What is the difference between a policy and a procedure in an organizational context?

### 2. What are some examples of documentation that support a network's physical layout?

### 3. Why is it important to maintain accurate rack diagrams and cable maps?

### 4. What are IDF and MDF, and how do they relate to network infrastructure?

### 5. How does IP Address Management (IPAM) assist with network scalability?

### 6. What is the purpose of a baseline or golden configuration?

### 7. What is configuration management, and why is it critical in large environments?

### 8. Describe the function and importance of a service-level agreement (SLA).

### 9. How do NDAs and MOUs differ in their use and legal enforceability?

### 10. What types of plans should be documented to support system lifecycle management?

### 11. What is change management, and what are its key components?

### 12. When implementing patches and updates, what documentation should be updated?

### 13. Why is lifecycle documentation (EOL/EOS) necessary for network components?

### 14. What are some common elements of a password policy?

### 15. What topics should a Bring Your Own Device (BYOD) policy address?

### 16. How does a remote access policy contribute to network security?

### 17. What documents are typically completed during user onboarding and offboarding?

### 18. What is an acceptable use policy (AUP), and what should it cover?

### 19. What’s the purpose of documenting warranty and licensing information?

### 20. Why is high-level management support essential for enforcing organizational policies?

### 21. How does a business continuity plan differ from a disaster recovery plan?

### 22. Why is a system life cycle plan important for IT infrastructure?

### 23. What kind of events would trigger an incident response plan?

### 24. Why is documentation review and regular updating necessary?

### 25. How do organizational policies help ensure regulatory compliance?


# Chapter 16: High Availability and Disaster Recovery

### 1. What is high availability and how does it differ from fault tolerance?

### 2. How do load balancing and NIC teaming contribute to system uptime?

### 3. What is multipathing and how is it used in storage or network design?

### 4. Describe the roles of UPS and PDU in maintaining physical infrastructure reliability.

### 5. What environmental controls are important for a data center?

### 6. Compare MTBF, MTTR, RTO, and RPO in the context of disaster recovery planning.

### 7. What are the key differences between a hot site, warm site, and cold site?

### 8. What is a cloud recovery site, and when might it be preferred?

### 9. Explain the difference between active-active and active-passive configurations.

### 10. How does redundancy in internet service providers (ISPs) improve availability?

### 11. What is the purpose of conducting tabletop exercises?

### 12. Describe the process and importance of validation testing in disaster recovery.

### 13. How does clustering help provide high availability?

### 14. What are the risks of not having a disaster recovery site?

### 15. How should organizations approach cost-benefit analysis when selecting a DR site?

### 16. What’s the role of configuration and system state backups in disaster recovery?

### 17. How can organizations prepare for both hardware failure and natural disasters?

### 18. Describe the failover process in an active/passive cluster.

### 19. What types of fire suppression systems are suitable for data centers?

### 20. What are some EPA-approved clean agent alternatives to halon?

### 21. What are key factors to consider in designing redundant paths to ISPs?

### 22. How does VRRP differ from HSRP in first-hop redundancy?

### 23. What are the typical objectives of a tabletop disaster recovery test?

### 24. When validating a DR plan, what metrics should be reviewed?

### 25. How can documentation support effective disaster recovery response?


# Chapter 17: Data Center Architecture and Cloud Concepts

### 1. What are the key characteristics of public, private, and hybrid cloud models?

### 2. How does virtualization improve the efficiency of data center operations?

### 3. What is the role of a hypervisor in cloud computing?

### 4. Compare Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS).

### 5. What does “elasticity” mean in cloud computing, and how does it benefit organizations?

### 6. How does multitenancy work in a cloud environment?

### 7. Explain the concept of network functions virtualization (NFV).

### 8. What is a virtual private cloud (VPC), and how does it differ from a traditional private cloud?

### 9. What security functions are provided by network security groups and security lists?

### 10. Compare the roles of an internet gateway and a NAT gateway in cloud connectivity.

### 11. What is Direct Connect in cloud computing, and when should it be used?

### 12. How does zero trust architecture (ZTA) enhance cloud security?

### 13. Explain the principles behind software-defined networking (SDN).

### 14. What is SD-WAN and how does it support modern enterprise networking?

### 15. What benefits does Secure Access Secure Edge (SASE) offer?

### 16. Describe the spine-and-leaf architecture and its use in modern data centers.

### 17. What is the purpose of a Virtual Extensible LAN (VXLAN)?

### 18. How does infrastructure as code (IaC) change network provisioning?

### 19. What is the importance of automation and orchestration tools like Ansible or Puppet?

### 20. Explain dynamic inventories in the context of IaC.

### 21. What is configuration drift and how can it be managed?

### 22. How does policy-based authentication support secure access in cloud systems?

### 23. What is the significance of central policy management in SDN?

### 24. How does application-awareness improve cloud network performance?

### 25. What are some examples of cloud-based disaster recovery use cases?


# Chapter 18: Network Troubleshooting Methodology


### 1. What are the seven steps of the CompTIA Network+ troubleshooting methodology?

### 2. Why is it important to identify and isolate multiple problems individually?

### 3. How would you gather relevant information when identifying a network issue?

### 4. Why should you always question the obvious when forming a theory?

### 5. Compare the top-down and bottom-up approaches in the OSI model for troubleshooting.

### 6. What is the divide-and-conquer approach, and how does it differ from other OSI-based strategies?

### 7. What should you do if your theory is not confirmed during testing?

### 8. After confirming the cause of a problem, what should your next step be?

### 9. What should be included in a good plan of action before implementing a solution?

### 10. When should a technician escalate an issue?

### 11. What are some preventive measures you can implement after resolving a problem?

### 12. Why is documentation critical in the troubleshooting process?

### 13. How does identifying symptoms help narrow down network issues?

### 14. What is the significance of checking for recent changes in a network?

### 15. How can duplicating the problem help validate its root cause?

### 16. Why should you verify full system functionality after applying a fix?

### 17. How would you differentiate between a hardware failure and a configuration issue?

### 18. What are some common causes of intermittent connectivity problems?

### 19. Describe how to troubleshoot a scenario where only one workstation cannot access the network.

### 20. What should you check first if users report slow performance over Wi-Fi?

### 21. How would you determine if a performance issue is caused by congestion or bandwidth limits?

### 22. What are some ways to troubleshoot packet loss or jitter?

### 23. Why is a baseline important in determining abnormal network behavior?

### 24. What tools can help validate the resolution of a network issue?

### 25. How would you determine whether a network issue is isolated to one user or widespread?

### 26. Why should you verify link lights and physical connections early in the troubleshooting process?

### 27. What actions would you take if a user receives a “duplicate IP address” error?

### 28. How would you handle a situation where users can access external sites but not internal servers?

### 29. What are signs that a DNS misconfiguration might be the root of a problem?

### 30. How can questioning users during problem reporting reveal key details for root cause analysis?


# Chapter 19: Network Software Tools and Commands

### 1. What is the primary function of the `ping` utility?

### 2. How does `traceroute` (or `tracert` on Windows) help in diagnosing network issues?

### 3. What does the `ipconfig` command provide in Windows, and how does it differ from `ifconfig` in Linux?

### 4. Why is `ip` gradually replacing `ifconfig` in modern Linux systems?

### 5. What does the `netstat` command show, and how can it be used to identify malware?

### 6. What does the `arp -a` command display?

### 7. How can the `nslookup` and `dig` commands assist in DNS troubleshooting?

### 8. How does `tcpdump` capture and filter traffic?

### 9. What does the `route` command reveal about network connectivity?

### 10. What information can `nmap` provide during a security audit?

### 11. What is LLDP and how is it used for network discovery?

### 12. How does CDP differ from LLDP?

### 13. Describe how a protocol analyzer (packet sniffer) works and what it captures.

### 14. What is promiscuous mode on a NIC?

### 15. What are use cases for a throughput or bandwidth speed tester?

### 16. When would you use a port scanner, and what are the risks?

### 17. Describe the purpose of a hardware loopback plug.

### 18. How is a tone generator and probe used in cable testing?

### 19. What does a visual fault locator do, and what kind of cabling does it support?

### 20. How can a Wi-Fi analyzer improve wireless network performance?

### 21. What basic command would you use to release and renew a DHCP lease in Windows?

### 22. What four DHCP messages can be captured with a protocol analyzer during IP negotiation?

### 23. What’s the purpose of the `show mac-address-table` command?

### 24. How is the `show vlan` command used to verify switch port configurations?

### 25. What would the `show interface` command reveal on a Cisco device?

### 26. What are the advantages of using a GUI-based protocol analyzer over a CLI tool?

### 27. Why is `netstat -n` useful compared to the default output?

### 28. What is the difference between TCP and UDP traffic shown in `tcpdump`?

### 29. When analyzing a slow network, which command or tool should you run first?

### 30. What does the `hostname` command do?

### 31. What tool would you use to confirm if a default gateway is responding?

### 32. How can `iptables` be used to manage firewall rules on a Linux system?

### 33. What is the use of a TFTP server in network equipment upgrades?

### 34. What’s the purpose of using SSH instead of Telnet for device management?

### 35. How does PuTTY facilitate remote CLI management?

### 36. What does `ip a` show in Linux?

### 37. Describe how `pathping` or `mtr` works and why it's useful.

### 38. What does the `route print` command show in Windows?

### 39. What kind of information can a NetFlow analyzer provide?

### 40. When would you use the `show power` command on a switch?


# Chapter 20: Network Security Concepts

### 1. What are the three core principles of the CIA Triad?

### 2. How does encryption differ when protecting data at rest versus data in transit?

### 3. What is the purpose of a digital certificate and how does it relate to PKI?

### 4. Describe how public key infrastructure (PKI) works.

### 5. What are the common use cases for self-signed certificates?

### 6. What is the role of the Certificate Revocation List (CRL) in a PKI system?

### 7. What is the difference between authentication and authorization?

### 8. How does the AAA model improve security in a network?

### 9. Describe how multifactor authentication (MFA) increases access security.

### 10. What is the function of RADIUS and how does it compare to TACACS+?

### 11. How is LDAP used in enterprise environments?

### 12. What does SAML provide in a federated identity system?

### 13. How does single sign-on (SSO) benefit end users and administrators?

### 14. What is time-based authentication and where is it typically applied?

### 15. What is meant by the principle of least privilege?

### 16. Describe how role-based access control (RBAC) is implemented.

### 17. What is a threat, and how is it different from a vulnerability?

### 18. Define the term "exploit" in a security context.

### 19. What is meant by data locality and why is it important in compliance?

### 20. How do regulations like PCI DSS and GDPR affect IT operations?

### 21. Why is regulatory compliance important for network administrators?

### 22. What is the purpose of conducting a security audit?

### 23. What are the main types of authentication factors used in IAM systems?

### 24. What makes Zero Trust different from traditional security models?

### 25. How does the IAM framework support secure identity lifecycle management?


# Chapter 21: Common Types of Attacks

### 1. What is a denial-of-service (DoS) attack, and how does it differ from a distributed denial-of-service (DDoS) attack?

### 2. How does a reflective DoS attack work?

### 3. What is an amplified DoS attack, and what services are commonly exploited in it?

### 4. How does a command-and-control server function in a DDoS botnet?

### 5. What is an evil twin attack, and how does it compromise wireless security?

### 6. Describe the process of a deauthentication attack in a wireless environment.

### 7. How do dictionary and brute-force attacks differ in execution?

### 8. What security practices can help prevent password attacks?

### 9. What is MAC spoofing and why is it a threat?

### 10. Describe how ARP poisoning can be used to intercept network traffic.

### 11. What is VLAN hopping, and how does double-tagging enable this attack?

### 12. How does DNS poisoning differ from DNS spoofing?

### 13. What risks are associated with rogue DHCP servers?

### 14. What is an on-path (man-in-the-middle) attack and what types of data can be compromised?

### 15. What forms of social engineering are discussed in the chapter?

### 16. How does tailgating differ from piggybacking in a physical security context?

### 17. What type of data loss can result from dumpster diving?

### 18. What is the purpose of network segmentation in mitigating threats?

### 19. How does hardening a system reduce its attack surface?

### 20. What physical security methods can help defend against device theft or tampering?

