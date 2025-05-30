Chapter 1: Introduction to Networks
1. What Is a Network?
Network: Two or more computers/devices connected to share resources (data, printers, internet, etc.).

Communication: Occurs using binary (1s and 0s).

2. Types of Networks
LAN (Local Area Network): Small geographic area (office, building). Devices access each other’s resources directly.

Workgroups: Logical groups inside LANs, often by department.

Router: Connects separate LANs so devices on different LANs can communicate.

3. Key Network Components
Workstations: Powerful user computers, sometimes called clients.

Servers: High-performance machines for specific tasks (file, mail, print, web, etc.).

Hosts: Any device with an IP address (workstations, servers, printers).

4. Other Network Types
Type	Description
MAN	Metropolitan Area Network; covers a city, connects buildings.
WAN	Wide Area Network; spans large distances (e.g., Internet). Uses routers.
PAN	Personal Area Network; very small, close range (Bluetooth, etc.).
CAN	Campus Area Network; covers a campus, connects building LANs.
SAN	Storage Area Network; dedicated to storage traffic.
SDWAN	Software-defined WAN, managed by software.
MPLS	WAN protocol using labels for data routing.
mGRE	Protocol for dynamic VPN connections (often in DMVPN).

5. Network Architectures
Peer-to-Peer:
No central authority; each device can be both client and server. Simple, not very scalable or secure.

Client-Server:
Central server manages resources, access, and security. Most business networks use this for scalability, security, and central management.

6. Physical Network Topologies
Topology	Description	Pros	Cons
Bus	All devices share a single cable.	Cheap, simple	Not fault-tolerant, hard to troubleshoot
Star	Devices connect to a central hub/switch.	Easy to manage, scalable, fault-tolerant	Central device is single point of failure
Ring	Devices form a closed loop.	Simple traffic management	Not fault-tolerant, not used much
Mesh	Every device connects to every other.	Redundant, robust	Complex, expensive
Hybrid	Mix of topologies (common in real life).	Flexible	Can be complex
Point-to-Point	Direct link between two devices.	Simple, secure	Not scalable
Point-to-Multipoint	One device connects to several others.	Efficient for some WANs	Central device is single point of failure

7. Selecting a Topology
Consider:

Cost

Scalability

Fault tolerance

Ease of installation/maintenance

Security

Star is most common for LANs. Mesh/Partial Mesh for high fault tolerance (WANs/Internet backbone).

8. Backbone and Segments
Backbone: Main high-speed path connecting different parts of a network.

Segments: Smaller subnetworks connected to the backbone.

9. Service Entry Points
Demarc (Demarcation Point): Handoff point between your network and ISP/service provider.

10. Virtual Networking
Term	What Is It?
vSwitch	Virtual switch that connects VMs on a hypervisor.
vNIC	Virtual network interface card for VMs.
NFV	Network Function Virtualization (routers, firewalls, etc. as software).

11. Three-Tier Network Model
Layer	Role
Core	Backbone; fast switching/routing.
Distribution	Connects access layers to core; filtering, VLANs, routing.
Access	Connects end-user devices (switches, PoE, QoS).

Collapsed-Core: Combines core and distribution layers for cost/complexity savings.

12. Spine and Leaf (Data Center Topology)
Spine: High-speed backbone switches, connect only to leaf switches.

Leaf: Connects to servers/hosts, never to other leafs or the spine.

Purpose: Low-latency, redundant switching for data centers/virtualization.

13. Network Traffic Flows
Type	Description
North-South	Traffic between internal network and Internet (in/out). Focus for perimeter security.
East-West	Traffic inside the network/data center (lateral movement). Focus for internal security.

14. Quick Terms Table
Term	What Is It?
LAN	Local Area Network
WAN	Wide Area Network
MAN	Metropolitan Area Network
CAN	Campus Area Network
PAN	Personal Area Network
SAN	Storage Area Network
SDWAN	Software-Defined WAN
MPLS	Label-based WAN protocol
Demarc	ISP/service provider handoff point
vSwitch	Virtual switch (hypervisor)
vNIC	Virtual network interface card
NFV	Network Function Virtualization

15. Exam/Interview Essentials
Know your topologies (star, mesh, bus, etc.) and their pros/cons.

LAN vs. WAN: LAN = local, WAN = wide area (multiple LANs).

Three-tier model: Core, Distribution, Access.

North-south vs. east-west traffic: North-south = in/out; east-west = within network/data center.

Virtual networking concepts: vSwitch, vNIC, NFV.

16. Sample Interview Q&A
Q: What’s the difference between LAN and WAN?
A: LAN = local network; WAN = connects LANs over wide areas.

Q: Why is star topology popular?
A: Easy to troubleshoot/expand, only one device goes down if cable fails; single point of failure is the hub/switch.

Q: What’s north-south vs. east-west traffic?
A: North-south = between internal network and internet; east-west = within the same network or data center.

Tip:
When asked to design a network, always clarify:

How many users/devices?

Fault tolerance required?

Security requirements?

Budget?

Scalability?

