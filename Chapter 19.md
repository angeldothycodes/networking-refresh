# Chapter 19: Network Software Tools and Commands

## Exam Objectives Covered

- **5.5:** Given a scenario, use the appropriate tool or protocol to solve networking issues.

---

## Software Tools

### Protocol Analyzer / Packet Capture

- **Purpose:** Captures network packets to analyze traffic.
- **Examples:** Wireshark, Omnipeek, tcpdump.
- **Use cases:** See what’s happening on the wire, troubleshoot DHCP, DNS, and connectivity issues, spot suspicious traffic.
- **Note:** Commercial analyzers can put the NIC in *promiscuous mode* (captures all packets, not just those for your system).

**DHCP Process Example:**  
If you use a packet sniffer and run `ipconfig /release` then `ipconfig /renew`, you’ll see:
- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP ACK

If you see Discover packets but no Offer, the DHCP server might not be working or reachable.

---

### Bandwidth Speed Testers

- **Purpose:** Measure network throughput (real or perceived speed).
- **Examples:** IPerf, TamoSoft, speedtest.net.
- **Use cases:** Baseline normal performance, troubleshoot “slow network” complaints, classify traffic types (TCP vs UDP).

**Tip:** Always create a baseline when the network is healthy.

---

### Port Scanners

- **Purpose:** Scan hosts for open ports/services.
- **Examples:** Nmap, Advanced IP Scanner.
- **Use cases:** Security audits, checking for unnecessary/unsafe open ports, verifying service availability.

**Note:** *Port sweep* = scan many hosts for one port. *Port scan* = scan one host for many ports.

---

### NetFlow Analyzers

- **Purpose:** Analyze traffic flows for volume and type.
- **How:** Devices export flow summaries (not packets) to a collector for analysis.
- **Use cases:** Deep traffic analysis, detect top talkers, diagnose bandwidth hogs.

---

### TFTP Server

- **Purpose:** Transfer firmware/config files to network devices.
- **How:** Lightweight protocol, simple to run, commonly used for router/switch upgrades.

---

### Connectivity Software

- **Purpose:** Remote access to devices for support or administration.
- **Examples:** Microsoft Remote Desktop, Quick Assist, LogMeIn, GoToMyPC.
- **Command-line access:** **SSH** (preferred), **Telnet** (not secure), **PuTTY** (popular SSH/Telnet tool).

---

### IP Scanner

- **Purpose:** Discover active hosts and open ports on the network.
- **Caution:** Excessive scanning may trigger security alerts.

---

## Command-Line Networking Tools

### traceroute / tracert

- **Purpose:** Shows each router (hop) between you and a destination, measuring latency at each.
- **Syntax:** `tracert <hostname or IP>` (Windows), `traceroute <host>` (Linux/Mac)
- **Use case:** Find where connectivity fails; spot routing loops or bottlenecks.

> If you see `*` in output, that hop is slow, busy, or blocking ICMP.

---

### ipconfig / ifconfig / ip

- **ipconfig (Windows):** Shows IP, subnet mask, gateway, DNS, MAC, lease info.
- **ifconfig (Linux/Unix):** Shows and configures interfaces (older).
- **ip (Linux/Unix):** Modern replacement for ifconfig; used for showing and configuring interfaces, addresses, routes.

**Common commands:**

ipconfig /all # Detailed config
ipconfig /release # Release DHCP lease
ipconfig /renew # Renew DHCP lease
ifconfig # Show interfaces (Linux/Unix)
ip addr show # Show interfaces (Linux/Unix)


---

### ping

- **Purpose:** Check if a host is reachable, measure latency, detect packet loss.
- **Syntax:** `ping <hostname or IP>`
- **Options (Windows):**
  - `-t`  : Ping until stopped (Ctrl+C)
  - `-n <count>`: Number of packets to send
  - `-w <timeout>`: Wait time in ms per reply
  - `-4`, `-6`: Force IPv4/IPv6

- **Special:** `ping 127.0.0.1` or `ping localhost` = local loopback test.

---

### arp

- **Purpose:** Shows or modifies the IP-to-MAC address mapping table (ARP cache).
- **Syntax:** `arp -a` (show current ARP table), `arp -d <IP>` (delete), `arp -s <IP> <MAC>` (add static)
- **Use case:** Diagnose duplicate IP addresses, see what MAC address is linked to which IP.

---

### nslookup / dig

- **nslookup (Windows):** Query DNS servers for hostname → IP (and vice versa).
- **dig (Linux/Unix):** More advanced DNS lookups.
- **Syntax:**
  - `nslookup <hostname>` (simple)
  - `nslookup -type=MX <domain>` (find mail servers)
  - `dig <hostname>`

**Use case:** Check if DNS is resolving correctly.

---

### mtr / pathping

- **mtr (Linux/Unix):** Combines traceroute and ping; shows route and latency/loss at each hop.
- **pathping (Windows):** Similar functionality.

---

### Nmap

- **Purpose:** The most widely used port scanner for open ports, live hosts, and service detection.
- **Use cases:** Map the network, spot open services, test firewall rules.

---

## Specialized Hardware Tools

- **Cable tester:** Check physical cable continuity and wiring.
- **Toner probe:** Trace cables in walls.
- **Taps:** Capture network traffic at the hardware level.
- **Wi-Fi analyzer:** Scan for wireless networks, channel overlap, signal strength.
- **Visual fault locator:** Laser device to find fiber breaks.

---

## Device-Specific Commands

- `show mac-address-table`   — See MAC addresses learned by a switch.
- `show route`               — Display routing table.
- `show interface`           — Status, errors, and statistics for interfaces.
- `show config`              — View device configuration.
- `show arp`                 — Show device’s ARP table.
- `show vlan`                — See VLAN configuration on switches.
- `show power`               — See power/PoE status.

---

## Key Study Points

- Know what each tool does, what problems it helps solve, and sample output.
- Practice with both Windows and Linux tools: many exam questions show command output and ask you to interpret it.
- Know common options/switches, especially for `ping`, `ipconfig`, `nslookup`, and `tracert`.

---

**Practice:**
- Run `ipconfig /all` and identify DHCP, DNS, MAC, gateway.
- Use `tracert google.com` and see the path.
- Use `arp -a` and explain an entry.
- Try `nslookup -type=MX gmail.com`.
- Use Wireshark or tcpdump to capture traffic and filter for `DHCP`.
- Run Nmap on your test network (never on production without permission).

---

> **Tip:** Always get a baseline of what “normal” looks like for your network. That way, you’ll know when something’s wrong and which tool will help you confirm and diagnose the issue.


## Manipulating the Routing Table in Windows

- **View routing table:**
- route print

- 
- **Add route:**  
route add [destination] mask [netmask] [gateway]

- Example:  
  `route add 10.1.1.0 mask 255.255.255.0 10.2.2.2`

- **Add persistent route:**  
route -p add 10.100.0.0 mask 255.255.0.0 10.2.0.1



- **Delete route:**  
route delete 10.100.0.0 mask 255.255.0.0


- **Change route:**  
route change 10.100.0.0 mask 255.255.0.0 10.7.0.5


- **Options:**
- `-f`: Clears non-host, non-loopback, and non-multicast routes
- `-p`: Persistent (remains after reboot)
- `/?`: Help

---

## Using netstat

- **Basic usage:**  
netstat

- Shows all active connections

- **Switches:**
- `-a`: All connections and listening ports
- `-b`: Executable behind connection
- `-e`: Ethernet stats (packets, errors, discards)
- `-n`: Numeric IP/port instead of names
- `-o`: Process ID
- `-p [proto]`: Protocol-specific (TCP, UDP, etc.)
- `-r`: Routing table
- `-s`: Per-protocol stats
- Combine switches as needed (`netstat -an`)

**Example:**  
View all TCP connections in numeric format:  
netstat -an


**Example:**  
View ICMP statistics:  
netstat -s -p ICMP


---

## Using tcpdump (Linux/macOS)

- **Capture all traffic:**  
tcpdump -i any



- **Capture on specific interface:**  
tcpdump -i eth0


- **Filter by host:**  
tcpdump host 192.168.5.5


---

## Basic Cisco Router/Switch Commands

- **View current config (RAM):**  
show running-config


- **View saved config (NVRAM):**  
show startup-config


- **Save running config to NVRAM:**  
copy running-config startup-config


- **Erase startup config:**  
erase startup-config


- **Reload device:**  
reload



- **Show hardware/software info:**  
show version


- **Show inventory:**  
show inventory


---

## Device Discovery Protocols

- **Cisco Discovery Protocol (CDP):**
- `show cdp neighbors`
- `show cdp neighbors detail`

- **Link Layer Discovery Protocol (LLDP):**
- Vendor-neutral alternative to CDP
- `show lldp neighbors`

---

## Common Show Commands (Switches/Routers)

- **Show MAC address table:**  
show mac address-table


- **Show interfaces:**  
show interfaces
show interface [type/number]



- **Show brief IP info:**  
show ip interface brief


- **Show routing table:**  
show ip route



- **Show ARP table:**  
show arp


- **Show VLANs:**  
show vlan


- **Show power/PoE status:**  
show power
show power inline


- **Show switch stack info:**  
show switch


---

## Hardware Tools

- **Toner Probe (Tone Generator):**  
Trace wires through walls and identify cables in bundles.

- **Cable Tester:**  
Test cable continuity, identify straight-through/crossover, and spot wiring faults.

- **Tap:**  
Hardware device to passively monitor network traffic between two devices.

- **Wi-Fi Analyzer:**  
Measure signal, SSID, noise, and optimize wireless coverage.

- **Visual Fault Locator (Fiber):**  
Tool to visually identify fiber breaks, bends, and polarity issues.

---

## Exam Essentials (Summary Points)

- Know and practice core CLI tools: `route`, `netstat`, `ping`, `tracert`, `ipconfig`, `arp`, `nslookup`, `tcpdump`, `nmap`
- Understand Cisco show commands for config, status, and troubleshooting
- Be familiar with GUI tools: protocol analyzers, throughput testers, RDP clients
- Know what each utility does and when to use it
- Recognize the role of hardware tools (toner, testers, taps, analyzers) in network troubleshooting

---

