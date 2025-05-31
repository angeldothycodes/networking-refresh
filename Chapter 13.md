# Chapter 13: Remote Network Access

_Remote access is how people and devices connect to a network from far away—like working from home, supporting remote sites, or fixing servers without being physically there. In modern IT, this means using **secure** methods to keep company data safe while providing the flexibility workers need._

---

## Why Remote Access?

Remote access lets employees, admins, and devices reach a company’s internal resources from anywhere. This is great for working from home or connecting multiple offices, but it can also be a security risk if not managed properly. So, companies use tools and protocols to keep those connections secure.

---

## VPN Architectures: Making Remote Access Secure

### Site-to-Site VPN

Think of this as a **secure tunnel** between two office buildings. A site-to-site VPN connects two or more entire networks (like branch offices and headquarters) over the public Internet. All traffic between these sites is automatically encrypted and routed through this tunnel.  
- **No action needed by users:** Devices just work as if they're on the same LAN.
- **Typical use:** Permanent links between offices.

### Client-to-Site VPN (Remote Access VPN)

Here, the VPN tunnel is set up by a remote user (like someone working from home). The user runs a VPN client app, which securely connects them to the company network.  
- **Typical use:** Telecommuters, traveling staff.
- **Common problem:** Users can’t connect if they don’t have the right VPN address or password.

### Clientless VPN

Sometimes, you don’t even need to install a client. With a **clientless VPN**, you log in via a secure web browser (using SSL/TLS encryption).  
- **Just use a browser:** No VPN software needed.
- **Common use:** Quick, occasional access to company apps or files from any computer.

---

## Split Tunnel vs. Full Tunnel

When using a VPN, you can set how traffic is handled:

- **Split Tunnel:** Only traffic meant for the company goes through the VPN. Everything else (like YouTube, Facebook) goes straight to the Internet.  
  - **Pros:** Less bandwidth used on the company network, faster Internet for the user.
  - **Cons:** Security risk—device is on two networks at once.

- **Full Tunnel:** **All** the user’s traffic (even regular web browsing) goes through the VPN, and then out to the Internet via the company.  
  - **Pros:** Everything is inspected and secured by the company firewall.
  - **Cons:** Slower Internet, heavier company bandwidth use.

---

## Remote Desktop Solutions

When you need to control a machine as if you’re sitting at it (for support, troubleshooting, or running apps):

### RDP (Remote Desktop Protocol)

- Developed by Microsoft.
- Lets you see and control the full graphical desktop of a remote Windows machine.
- Runs on TCP port **3389**.
- Most Windows and even macOS systems have an RDP client preinstalled.
- Used for full desktop access or delivering single applications (RemoteApp).

**Remote Desktop Gateway:**  
- A server role that brokers RDP connections securely over the Internet, often using SSL/TLS (port **443**).
- Controls which users can access which resources, provides encryption, and handles authentication.

### VNC (Virtual Network Computing)

- Open-source protocol for remote desktop control.
- Works on any operating system.
- Uses TCP port **5900** by default.
- Sends raw pixel data—works anywhere, but usually less efficient and secure than RDP (unless add-on encryption is used).

### Virtual Desktop Infrastructure (VDI)

- The desktop itself is not on your computer, but runs as a virtual machine in the cloud or a datacenter.
- User connects and gets the same desktop experience, but all resources and apps are handled remotely.

---

## Connection Methods

### SSH (Secure Shell)

- A secure way to get command-line (terminal) access to remote devices and servers.
- **Always use SSH instead of Telnet** (Telnet sends everything unencrypted!).
- Runs on TCP port **22**.
- Uses public/private key cryptography for authentication.

### Graphical User Interface (GUI)

- RDP and VNC are examples of GUI-based remote management.
- You see the desktop and can use the mouse/keyboard just as if local.

### API (Application Programming Interface)

- Used for automating or programmatically managing systems (like routers, cloud services).
- Common style is **REST API**, which is stateless and uses URLs for resources (returns data in JSON or XML).
- Great for scripts, apps, or integrations.

### Console / Serial (Out-of-Band)

- Old school but still essential! Used when the device can’t be reached over the network.
- Use a **console cable** (often a rolled RJ45-to-serial cable, or USB now) to connect directly.
- Typical settings: **9600 baud**, 8 data bits, no parity, 1 stop bit, no flow control.

---

## Jump Box / Jump Host

- A **jump box** is a special, highly secured machine that sits between a secure network (like your office) and a less-secure zone (like the DMZ or Internet).
- Admins first connect to the jump box, then to internal resources. This provides an audit trail and an extra layer of security.

---

## In-Band vs. Out-of-Band Management

- **In-Band Management:** Accessing devices over the production network (using SSH, RDP, or API over the same network as user/data traffic).
- **Out-of-Band Management:** Accessing devices via a separate channel, such as a console cable or a dedicated management Ethernet port. Used for emergencies when the main network is down or unavailable.

---

## Summary

- **Remote network access** is essential for modern businesses, allowing secure connections for offices, remote users, and admins.
- **VPNs** are the main way to secure these connections, with site-to-site for permanent office links, client-to-site for users, and clientless for web-based access.
- **Split/full tunneling** decides if all or just some traffic goes through the VPN.
- **Remote desktop solutions** like RDP and VNC let you control remote computers graphically.
- **SSH** provides secure command-line access.
- **Jump boxes** and proper management (in-band and out-of-band) add extra layers of security and reliability.

---

## Quick Reference Table

| Term/Tech         | Purpose/Description                                      | Typical Port |
|-------------------|---------------------------------------------------------|--------------|
| Site-to-site VPN  | Securely connects two networks (offices)                | Various      |
| Client-to-site VPN| User connects securely to office from remote location    | Various      |
| Clientless VPN    | Secure access via browser (SSL/TLS)                     | 443 (HTTPS)  |
| RDP               | Full desktop access, Windows                            | 3389/TCP     |
| RDP Gateway       | Brokers secure RDP over Internet                        | 443/TCP      |
| VNC               | Remote desktop, open source                             | 5900/TCP     |
| SSH               | Secure command-line remote management                   | 22/TCP       |
| Console           | Serial out-of-band management                           | n/a          |
| Jump box/host     | Secured, audited relay point for admin access           | n/a          |

---

> **Pro Tip:** Always use the most secure, least-privilege method for remote access. Disable unused services like Telnet, use VPNs, enforce strong authentication, and audit access!

