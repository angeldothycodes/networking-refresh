# CCNA Chapter 12 – Wireless Networking (Technical, Information-Rich Summary)

## Wireless Technologies & Standards

- WLANs = Half-duplex RF communication, subject to interference, lower robustness vs wired.
- Key agencies: IEEE (standards), FCC (US regulation), ETSi (Europe), Wi-Fi Alliance (interoperability).
- Unlicensed RF bands: 900MHz, 2.4GHz (ISM), 5GHz (U-NII).

### IEEE 802.11 Standards (Summary Table)
- 802.11b: 2.4GHz, DSSS, 11Mbps, 3 non-overlapping channels (1, 6, 11 US).
- 802.11g: 2.4GHz, OFDM, 54Mbps, backward compatible w/ b.
- 802.11a: 5GHz, OFDM, 54Mbps, 12 non-overlapping channels (US), immune to 2.4GHz interference.
- 802.11n: 2.4/5GHz, MIMO, 20/40MHz channels, up to 600Mbps, both bands supported, channel bonding.
- 802.11ac (Wi-Fi 5): 5GHz, wider channels (up to 160MHz), up to 1Gbps, MU-MIMO, QAM-256.
- 802.11ax (Wi-Fi 6/6E): 2.4/5/6GHz, OFDMA, 1024-QAM, higher density, better efficiency, up to 3.5+Gbps, TWT, supports more users.

### Modulation
- DSSS: Used by 802.11b, lower speeds, longer range.
- OFDM: Used by 802.11a/g/n/ac/ax, higher speeds, better spectral efficiency.

## Wireless Channels & Regulatory

- 2.4GHz: 11 channels (US), 3 non-overlapping (1, 6, 11).
- 5GHz: More non-overlapping channels; less crowded; DFS/TPC (802.11h) for radar avoidance.
- 6GHz: Added in Wi-Fi 6E for more spectrum.

## Wireless Network Types

- Ad hoc/IBSS: Peer-to-peer, no AP, poor scalability/security.
- Infrastructure/BSS: Clients connect via AP; AP bridges to wired LAN.
- ESS/ESSID: Multiple APs with same SSID allow roaming; signals overlap 10%+.

## Components

- Wireless NIC: Usually integrated, antenna for RF comms.
- AP (WAP): Bridges wireless <-> wired; can operate as repeater/bridge/router.
- Wireless Controller: Manages APs centrally (enterprise), split MAC (LWAPP/CAPWAP).

## Antennas

- Omni: 360-degree coverage (point-to-multipoint).
- Directional (Yagi): Focused, longer range (point-to-point).
- dBi/dBd: Signal gain reference. dBd = dBi - 2.2.

## Cellular Technologies

- GSM: SIM-based, global standard, subject to SIM cloning.
- FDMA/TDMA/CDMA: Channelization/multiplexing techniques.
- 3G: Up to 2Mbps, WCDMA, start of smartphone era.
- 4G/LTE: 100Mbps-1Gbps, "true" 4G was rare, LTE accepted.
- 5G: Millimeter wave, very high speed (1-10Gbps), shorter range, denser APs.

## Wireless Installation

- Site survey: **Pre- and post-deployment** to plan/verify coverage & performance.
- Coverage planning: Use non-overlapping channels, adjust AP power for density/fault tolerance.
- Multi-floor: Stagger channels between floors, patch antennas to minimize bleed.
- Site survey tools: Ekahau, AirMagnet, heat maps.

## Wireless Security

- Major threats: Rogue APs, ad hoc networks, DoS (jamming/deauth), sniffing/passive attack.
- Mitigation: WLCs for rogue detection, disable ad hoc, enable MFP for management frames, use IDS/IPS.
- Open Access: Default config, never leave in production.
- SSID: Unique network name; hiding ≠ security.
- MAC filtering: Weak, easily spoofed.
- WEP: Deprecated, easily cracked, static keys.
- WPA/WPA2-PSK: PSK = passphrase-based, stronger than WEP but can be brute-forced.
- WPA2-Enterprise: EAP, 802.1X, RADIUS; strongest, uses AAA.
- WPA3: Latest, strongest (not universally supported yet).

### Encryption & Auth

- WPA/WPA2: TKIP (legacy), AES-CCMP (modern/required for WPA2).
- WPA2-Enterprise: Uses 802.1X (RADIUS), EAP, certificates/PKI.
- EAP methods: PEAP (server cert only), EAP-TLS (client/server certs), EAP-FAST (PAC key).

## IoT Wireless Technologies

- Z-Wave: Home automation, mesh, sub-GHz, appliances/sensors.
- ANT+: Sensors, low-power, sports/health.
- Bluetooth/BLE: PAN, devices, up to 100m, BLE for low power.
- NFC: <10cm, payments, low power.
- IR: Line of sight, legacy, slow.
- RFID: Asset tracking, passive tags.
- 802.11: Standard Wi-Fi, used for IoT.

## WLAN Config & Optimization

- AP: Change default IP, set SSID, enable security, choose channels, adjust power, update firmware.
- NIC: Join SSID, enter PSK or use EAP.
- Roaming: Use same SSID for all APs, overlapping coverage, different channels.

## Guest Networking

- Guest VLANs: Segregate guests, restrict access to internal LAN.
- Captive portal: Web auth for guests (airports, cafes).
- Mobile hotspots: Tethering, LTE/5G for on-the-go Wi-Fi.

## Troubleshooting

- Signal issues: Check antenna, obstacles, AP placement, interference.
- Channel overlap: Use spectrum analyzer, stagger channels.
- Connectivity: Confirm SSID/security settings, client drivers.
- Slow speeds: RF interference, excessive clients, low SNR, distance to AP.
- Security: Ensure WPA2/AES, strong PSK, disable unused SSIDs, check for rogue APs.

## Key Exam Points

- Memorize: 802.11 standards, frequencies, speeds, channels.
- Know security protocols: WEP, WPA, WPA2, WPA3, EAP, 802.1X, RADIUS.
- Antenna types: Omni vs directional, dBi/dBd.
- Cellular evolution: 3G/4G/5G, GSM/CDMA.
- WLAN install: Site survey, channel plan, AP config.
- Wireless threats: Rogue APs, ad hoc, DoS, sniffing; mitigations.
- IoT protocols: Z-Wave, ANT+, Bluetooth, NFC, IR, RFID.

# End of Chapter 12 Summary
