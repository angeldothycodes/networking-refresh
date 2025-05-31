# Chapter 14: Using Statistics and Sensors to Ensure Network Availability

> **CompTIA Network+ 3.2 Objective**  
> _Given a scenario, use network monitoring technologies (SNMP, syslog, SIEM, metrics, logs, and more)._

## Why Monitor Networks?

Downtime costs money and trust. The only way to stop downtime before it happens is by watching for warning signs from your devices. This means monitoring both the hardware (like temperature, CPU, memory, and NICs) and the network traffic itself. You want to catch issues _before_ they become outages.

## Understanding Key Metrics

Just like a car dashboard shows you speed and temperature, devices and networks show their health through metrics.

**Common device metrics include:**
- **Temperature:** Overheating causes reboots and hardware failures. Keep systems cool and dust-free.
- **CPU usage:** If the processor is above ~85% for long periods, performance suffers.
- **Memory:** If available RAM drops too low or page file use is high, you may have memory leaks or need more memory.
- **Bandwidth/Throughput:** The connection's speed (bandwidth) and how much is actually being used (throughput). If utilization is constantly over 70%, that's a warning sign.

**Key network metrics:**
- **Latency:** The delay for a packet to travel from source to destination (measured as Round-Trip Time or RTT, e.g., with `ping`). High latency causes slow performance.
- **Jitter:** Variation in latency, which can disrupt voice/video.
- **Loss:** Lost packets mean data must be resent or is simply gone (bad for VoIP and real-time apps).

## Baselines and Anomaly Detection

**Baseline:**  
Before you can know something is wrong, you need to know what's "normal." A baseline is a record of regular, healthy network/device behavior. This is your reference. If metrics suddenly go above or below baseline, that’s an anomaly and a potential problem.

**Anomaly detection:**  
Once you have a baseline, set up alerts for anything outside normal ranges. This could be an email/text if bandwidth spikes or CPU suddenly maxes out.

## Monitoring Tools and Technologies

### Performance Monitoring

Tools like Windows Performance Monitor, MRTG, and PRTG collect and graph these metrics over time. They help spot trends, set baselines, and catch issues before users complain.

### Network Discovery

**Network discovery** scans for devices and maps how they connect. Ad hoc discovery is done manually; scheduled scans are automated. Automated discovery can alert you to rogue or misconfigured devices.

### Availability Monitoring

**Availability monitoring** checks if critical systems and services are up. The main goal: maximize uptime and respond fast to outages. Network management systems keep a log of uptime vs. downtime.

### Configuration Monitoring

Configuration drift (unintended changes to device settings) can break things. Use configuration monitoring tools to compare actual configs to the approved baseline and alert if there are differences.

---

## SNMP: Simple Network Management Protocol

**SNMP** is a standard protocol for collecting and organizing information about managed devices.

- **Agent:** A service running on each device to be monitored.
- **NMS (Network Management Station):** Central server that collects metrics from all agents.
- **OID (Object Identifier):** A unique ID for each measurable metric.
- **MIB (Management Information Base):** Database of OIDs. Each vendor/device type has its own MIB.

**How SNMP works:**  
The NMS polls the agent for data (`get` command) or the agent can alert the NMS on events (`trap` command). The NMS stores and analyzes the data, triggering alerts or generating reports as needed.

### SNMP Versions

- **SNMPv2c:** Adds support for bulk requests but is not secure. Auth is done via a plaintext "community string" (default: `public` for read-only, `private` for write).
- **SNMPv3:** Adds authentication and encryption, with user-based security models. Much more secure—use SNMPv3 in modern networks.

### SNMP Security

- SNMPv1/v2c are **not** secure; only protected by community strings.
- SNMPv3 supports MD5/SHA auth and DES/AES encryption.
- Always restrict SNMP with ACLs/firewalls, and never expose SNMP to the internet.

---

## Logs and Aggregation

### Syslog

Syslog is a standard protocol to send logs from devices to a central server (Syslog collector) over UDP/514. Log types include:

- **Traffic logs:** Who's using the network and how.
- **Audit logs:** Who did what on which device.
- **System logs:** Events like service restarts or hardware failures.

Syslog messages have severity levels from 0 (emergency) to 7 (debug). Collecting logs in one place makes troubleshooting and security monitoring much easier.

### Log Aggregation and SIEM

**Log aggregation** is gathering logs from many devices into a central place (Syslog collector, SIEM).

**SIEM (Security Information and Event Management):**
- Combines log collection, analysis, and alerting for security events.
- Gives real-time dashboards, historical analysis, and compliance reports.
- Can trigger alerts for security anomalies (intrusions, failed logins, etc).

---

## Packet Capture and Traffic Analysis

**Packet sniffers/protocol analyzers** (e.g., Wireshark) capture and decode network traffic for analysis. NICs must be in "promiscuous mode" to see all packets. **Port mirroring** (SPAN on Cisco) is used to send a copy of switch traffic to a monitoring port.

**Traffic analysis tools** (like NetFlow) measure "who is talking to whom," which helps identify top users, heavy traffic sources, or security issues.

---

## Modern Monitoring

**API Integration:**  
Modern devices may expose APIs for monitoring/automation, making it possible to script or automate much of what SNMP or syslog used to handle.

**Flow Data:**  
NetFlow and similar protocols record metadata about flows between systems (source/dest IP/port, protocol, etc). Useful for both troubleshooting and security.

---

## Summary

- **Monitor key metrics** (CPU, memory, temp, bandwidth, latency, jitter, loss) to prevent outages.
- **Use SNMP, logs (syslog), and flow data** to gather statistics and alerts.
- **Know SNMP versions and security best practices.**
- **Aggregate logs centrally, use SIEM for advanced security monitoring.**
- **Capture packets for deep troubleshooting, use port mirroring as needed.**
- **Always establish baselines and set up alerts for anomalies.**

---

## Key Terms for Review

- **SNMP agent / NMS / OID / MIB**
- **Syslog & severity levels**
- **SIEM**
- **Packet capture / protocol analyzer / port mirroring (SPAN)**
- **Baseline / anomaly alerting**
- **NetFlow / flow data**
- **API integration**

---

> _This covers Network+ 3.2 objectives: monitoring technologies, SNMP (traps, OIDs, MIB, v2c/v3, auth), log aggregation, syslog/SIEM, API/port mirroring, and all key metrics and techniques for ensuring network availability._
