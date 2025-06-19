# Chapter 9: Introduction to IP Routing

IP routing is the way routers move packets between different networks. If you want computers in one network to talk to computers in another, you need routers, and you need to understand how they make forwarding decisions. This chapter will give you that solid foundation—covering both how packets get routed and how routers figure out the best path.

## What Is Routing? Routed Protocols vs. Routing Protocols

Routing is about moving packets from one network to another using routers. When a packet leaves its local network, the router must know where to send it. Routers work at Layer 3 (the network layer), so they use logical addresses (IP addresses), not MAC addresses, to make decisions.

There are two types of protocols involved here. A routed protocol (like IP or IPv6) is what actually carries user data through a routed network. A routing protocol (like OSPF, EIGRP, BGP, RIP) is used by routers to share information about available networks with each other. The routing protocol helps routers build and update their routing tables, which tell them the best way to reach each network.

## Routing Basics: How Routers Move Packets

Imagine a network with two routers, each connected to a couple of different networks. When a host wants to send data outside its own subnet, it sends the packet to its default gateway (usually the router's IP on that subnet). Routers decide where to forward the packet based on their routing tables. These tables can have entries that are:

- Directly connected networks (the router has an interface in that subnet)
- Learned from a static route (manually added by an admin)
- Learned dynamically (from a routing protocol)

If the router doesn't know where to send the packet (no entry for that network), it drops the packet and may send an ICMP "destination unreachable" message back to the source.

When a router receives a packet, it does not care about the destination host's MAC address. Instead, it checks the destination **IP address** and looks up the network portion in its routing table. It then forwards the packet out the correct interface. The **frame** (which has a MAC address) is rebuilt at every hop—so the MAC address is always local for each link, but the **packet's IP addresses** stay the same end-to-end.

## Example: What Happens When Host_A Sends a Packet to Host_B

Suppose Host_A with IP 172.16.10.2 wants to ping Host_B at 172.16.20.2. Host_A realizes that Host_B is not in its local network, so it sends the packet to its default gateway (say, 172.16.10.1). Host_A needs the MAC address of the gateway, so it checks its ARP cache or sends an ARP request if needed. The frame goes to the router's Ethernet interface.

The router receives the frame, checks the FCS for errors, and then checks the destination MAC address. If it matches its own interface, it strips the frame and looks at the packet. The router examines the destination IP. If the network 172.16.20.0 is directly connected, it forwards the packet out the right interface. If not, it looks for a route (static or dynamic). The router then uses ARP to find the MAC address of Host_B (if it's not already in the ARP cache), rebuilds the frame with the appropriate source and destination MAC addresses, and sends it out.

This process continues at each hop: at every router, the frame is rebuilt for the next link, but the packet IP stays the same. The only time the IP packet gets changed is at the destination (or if it is dropped en route).

## Static Routing and Dynamic Routing

**Static routing** is when an admin enters all the route information manually. This works fine for small, simple networks but doesn't scale. Any changes (like a new subnet) must be updated everywhere by hand.

**Dynamic routing** uses protocols like RIP, OSPF, EIGRP, or BGP to let routers exchange information automatically. When a new route appears, routers advertise it to their neighbors. Dynamic routing is essential for larger, changing networks. Most networks use a mix: static routes for simple, stable paths; dynamic routing for everything else.

## Types of Routing Protocols: IGP, EGP, DV, LS, Hybrid

Routing protocols are divided into categories:

- **Interior Gateway Protocols (IGP):** Used within a single organization’s network (an autonomous system or AS).
- **Exterior Gateway Protocols (EGP):** Used between different organizations or ASes. The main EGP is BGP, which runs the Internet.

IGPs break down further:

- **Distance-vector (DV):** Each router tells its neighbors what networks it knows about and how far away they are (in “hops” or other metrics). Examples: RIP, IGRP.
- **Link-state (LS):** Each router shares information about its directly connected links with all routers in the AS. Routers then build a complete map of the network. Example: OSPF, IS-IS.
- **Hybrid:** Combines aspects of both. Example: EIGRP.

## How Routers Choose the Best Path

When a router has more than one possible path to a destination, it chooses the “best” route using these factors:

- **Administrative Distance:** This is a trust ranking. If a route to the same destination is learned from different sources (say, static vs OSPF), the one with the lowest administrative distance wins. For example, static routes have a lower administrative distance than dynamic ones.
- **Metric:** Each protocol has its own metric for the “cost” of a path (like hop count, bandwidth, delay). The route with the best (lowest) metric is chosen.
- **Prefix Length:** If there are multiple matches for a destination IP, the router picks the one with the longest prefix match (the most specific route).

## BGP, OSPF, and EIGRP

BGP is used by ISPs and huge companies to connect different autonomous systems. BGP is a path-vector protocol, and is the core routing protocol of the Internet. You probably won’t use it in a small/medium network, but you need to recognize its name and purpose.

OSPF is a widely used link-state IGP for enterprise networks. It quickly shares topology information and recalculates the best paths when there are changes.

EIGRP is a Cisco protocol that is hybrid, using both DV and LS features. It’s efficient and scalable, but mainly used on Cisco networks.

## The IP Routing Process, Step by Step

1. Host builds a packet with destination IP, hands it to its default gateway.
2. Host uses ARP to get the gateway's MAC and sends the frame to the router.
3. Router strips the frame, examines the IP packet, looks up the destination network in its routing table.
4. Router forwards the packet out the interface toward the destination network, building a new frame for each hop.
5. At the last router, it uses ARP to get the MAC of the destination host, frames the packet, and sends it.
6. Destination host receives the frame, verifies the FCS, strips the frame, and processes the IP packet.

The packet’s IP addresses (source and destination) do **not** change along the route; only the frame’s MAC addresses change at each hop. MAC addresses are only valid on a local network segment.

## Common Routing Table Output (Cisco Example)

```text
Gateway of last resort is not set
C      10.10.10.0/24 is directly connected, FastEthernet0/0
C      10.10.20.0/24 is directly connected, FastEthernet0/1
C      10.10.30.0/24 is directly connected, FastEthernet0/2
C      10.10.40.0/24 is directly connected, Serial0/0



The “C” means “directly connected.” Static routes show as “S,” OSPF as “O,” EIGRP as “D,” BGP as “B.”

## Why Routing Tables Matter

If a router has no route to a network, it will drop the packet and (usually) send an ICMP “destination unreachable” message to the sender. For routing to work across your organization, every router must have a complete map of the networks it needs to reach—either by static configuration, or by using dynamic routing protocols.

If you see “convergence,” that means all routers have up-to-date, consistent routing tables.

## Lab: Viewing the ARP Cache

You can see which IP addresses your host has resolved to MAC addresses by opening a command prompt and typing:
arp -a


The ARP cache maps IP addresses to MAC addresses—but only for devices on your local network. You’ll always see your default gateway’s MAC address in this list, because every packet to another network needs to use it.

## Key Exam Points

The MAC address is always local and changes at every hop. The IP addresses in a packet stay the same from source to destination. Static routing is manual, good for small or simple networks. Dynamic routing protocols share network info automatically, which is crucial for larger networks.

Remember, the frame only takes the packet as far as the next device (another host or the router); then the router rebuilds the frame for the next leg. The packet itself isn’t changed until it hits the final destination.

BGP is the protocol used between ISPs; OSPF and EIGRP are common inside organizations. The router chooses the route with the best administrative distance and the best metric for a destination. If there’s no specific match, it may use a default route, if one is configured.

When troubleshooting, if a packet doesn’t make it to its destination and there’s no route, the router drops it. If there’s a routing loop or a broken link, you may get a timeout or unreachable message.

---

This is everything you need to understand the IP routing process, static and dynamic routing, how routers use routing tables, and how they choose the best path. Review the tables, understand how the MAC and IP addresses interact at each step, and you’ll be ready for both the exam and the real world.



