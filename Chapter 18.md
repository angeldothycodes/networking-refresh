# Chapter 18: Network Troubleshooting Methodology (CompTIA Network+)

## 5.1 Explain the Troubleshooting Methodology

**1. Identify the Problem**
- Gather info: Interview users, check error messages, logs, LEDs.
- Identify symptoms: What *exactly* is not working? One user, or many?
- Duplicate the problem if possible.
- Has anything changed recently (software, hardware, cabling)?
- Approach multiple problems individually.

**2. Establish a Theory of Probable Cause**
- Start simple (cables, power, config)
- Question the obvious (is it plugged in? Caps Lock?)
- Use OSI model (top-down or bottom-up) if needed.
- Consider multiple possible causes.

**3. Test the Theory**
- Test and confirm your theory (swap cables, try a new port, different PC).
- If confirmed: Proceed.
- If not: Formulate a new theory or escalate.

**4. Establish a Plan of Action**
- Plan fix, considering risks and business impact.

**5. Implement the Solution**
- Execute the fix. Communicate with users.

**6. Verify Full System Functionality**
- Confirm the fix works.
- Test with the user.
- Implement preventive measures.

**7. Document Findings, Actions, and Outcomes**
- Write down what happened, how you fixed it, and any lessons learned.

---

## 5.2 Troubleshoot Common Cabling & Physical Interface Issues

**Cable Problems:**
- Incorrect cable (straight/crossover, single/multimode, STP/UTP)
- Signal degradation, crosstalk, attenuation, EMI/RFI
- Improper termination or damaged connectors
- TX/RX reversed
- Split pairs, bent pins, open/shorts

**Interface Issues:**
- Check interface counters (CRC errors, runts, giants, drops)
- Port status: error-disabled, administratively down

**Hardware:**
- Power over Ethernet (PoE) issues
- Transceiver mismatch (duplex/speed, SFP/GBIC)
- Bad port or SFP

---

## 5.3 Troubleshoot Common Network Service Issues

- Incorrect VLAN assignment
- ACL blocking traffic
- Routing table/default gateway/IP address/subnet mask errors
- Duplicate IPs

---

## 5.4 Troubleshoot Common Performance Issues

- Bottlenecking (congestion, bandwidth, throughput)
- Latency, jitter, packet loss
- Wireless: interference, channel overlap, coverage holes, SSID/passphrase mismatch, roaming issues

---

## Pro Tips

- Always check the **super simple stuff (SSS)** first: power, cables, user error, link lights.
- Isolate: is it one device or many?
- Work from the physical layer up.
- Document everything!

---


## The 7-Step Troubleshooting Model

1. **Identify the problem**
    - Gather info (question users, duplicate problem, check what changed)
    - Check basics (SSS: power, cables, link lights, login)
    - Isolate: one user, group, or whole network?

2. **Establish a theory of probable cause**
    - List likely causes (cabling, config, hardware, software)
    - OSI model: Bottom-up, Top-down, or Divide & Conquer

3. **Test the theory to determine the cause**
    - Test your hypothesis (change, check result)
    - If wrong, try another theory or escalate

4. **Establish a plan of action and identify potential effects**
    - Plan fix, consider impact

5. **Implement the solution or escalate as necessary**
    - Make the fix or escalate to expert

6. **Verify full system functionality and implement preventative measures**
    - Test all related systems, prevent recurrence

7. **Document findings, actions, outcomes, lessons learned**
    - Write up problem, solution, and takeaways

---

## Common Issues & Examples

- **Cabling**: wrong cable, bad termination, EMI, attenuation, split pairs
- **Physical Layer**: port down, bad NIC, no link light, bent pins
- **Interface errors**: runts, giants, CRC errors, drops (check with `show interface`)
- **Config mistakes**: wrong IP, subnet, VLAN, gateway, DNS, port speed/duplex
- **Wireless**: interference, wrong passphrase, AP placement, roaming config
- **DHCP**: pool exhaustion, rogue DHCP, expired lease
- **Security**: firewall/ACL blocks, untrusted SSL, MAC spoofing
- **Service issues**: dependency failures, unresponsive services

---

## Troubleshooting Tools

- `ipconfig /all` (Windows)
- `ping`, `tracert`
- `netstat`
- Cable tester/loopback plug
- Event viewer/logs

---

## Tips

- Always check the simple stuff first
- Prioritize by impact (network-wide > small group > single user)
- Change one thing at a time
- Always document

---

## Exam Essentials

- Memorize the **7 steps** in order
- Know what a link light is
- Know how to tell if it’s a hardware or user/training problem
- Be able to narrow down the problem
- Know how to spot and test for cabling-related problems

