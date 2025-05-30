#### OSI Model Layers & Data Encapsulation

---

**OSI Model Layers and Their Protocol Data Units (PDU):**

| **Layer**          | **PDU Name** | **Function**                                 |
|--------------------|:------------:|-----------------------------------------------|
| **Application**    | Datagrams    | User interface, file transfers, email, etc.   |
| **Presentation**   | Datagrams    | Data encryption, compression, translation     |
| **Session**        | Datagrams    | Dialog control, session management            |
| **Transport**      | Segments     | End-to-end connection, TCP/UDP, reliability   |
| **Network**        | Packets      | Routing, logical addressing (IP)              |
| **Data Link**      | Frames       | Framing, MAC addressing, error detection      |
| **Physical**       | Bits         | Transmission of bits (1s and 0s) over media   |

---

#### **Encapsulation Process**

As data moves down the OSI model:

1. **Application, Presentation, Session Layers**
   - **PDU:** Datagrams
   - **Function:** Generates data for communication.
   - **Example:** Web browser sending HTTP data, file transfer, email.

2. **Transport Layer**
   - **PDU:** Segments
   - **Function:** Breaks data into segments, adds TCP or UDP header (port numbers, sequencing, etc.)
   - **Example:** TCP Header is added for reliable communication.

3. **Network Layer**
   - **PDU:** Packets
   - **Function:** Adds IP header (source and destination IP addresses) for logical addressing and routing.
   - **Example:** Each segment becomes a packet with an IP header.

4. **Data Link Layer**
   - **PDU:** Frames
   - **Function:** Adds MAC header (source and destination MAC addresses), encapsulates each packet into a frame, includes Frame Check Sequence (FCS) for error checking.
   - **Example:** Frame = MAC header + IP packet + FCS.

5. **Physical Layer**
   - **PDU:** Bits
   - **Function:** Converts frames to bits for transmission as electrical/optical signals across the physical medium (cables, Wi-Fi, etc.).
   - **Example:** Transmitted bits of 1s and 0s.

---

#### **Example of Encapsulation (Based on Diagram):**

- **Step 1:** Application generates data (datagram).
- **Step 2:** Transport layer adds TCP header:  
  `TCP Header | Data`
- **Step 3:** Network layer adds IP header:  
  `IP Header | TCP Header | Data`
- **Step 4:** Data Link layer adds Frame header (LLC, MAC addresses), and FCS (Frame Check Sequence):  
  `Frame Header (LLC) | IP Header | TCP Header | Data | FCS`
- **Step 5:** Physical layer transmits as bits:  
  `Transmitted bits of 1s and 0s`

---

#### **OSI Layer to PDU Mapping Summary**

| **Layer**         | **Encapsulation Term** |
|-------------------|-----------------------|
| Application       | Data / Datagram       |
| Presentation      | Data / Datagram       |
| Session           | Data / Datagram       |
| Transport         | Segment               |
| Network           | Packet                |
| Data Link         | Frame                 |
| Physical          | Bits                  |

---

#### **Key Points:**
- Each OSI layer adds its own header (and sometimes trailer) to the data as it passes downward.
- At each layer, the data is known by a different name (PDU).
- This process is called **encapsulation**.
- When data is received, the process is reversed (decapsulation).

---

**(Paste this block into your .md file for a clean, formatted reference on GitHub!)**


+--------------+-----------------------------------------------+
| Application  | File, print, message, database, application   |
+--------------+-----------------------------------------------+
| Presentation | Data encryption, compression, translation     |
+--------------+-----------------------------------------------+
| Session      | Dialog control                                |
+--------------+-----------------------------------------------+
| Transport    | End-to-end connection                         |
+--------------+-----------------------------------------------+
| Network      | Routing                                       |
+--------------+-----------------------------------------------+
| Data Link    | Framing                                       |
+--------------+-----------------------------------------------+
| Physical     | Physical topology                             |
+--------------+-----------------------------------------------+



+--------------+---------------------------+
| Application  | Provides a user interface |
+--------------+-------------------------- +
| Presentation | Presents data             |
|              | Handles encryption        |
+--------------+-------------------------- +
| Session      | Data separation           |
+--------------+-------------------------- +



+------------+---------------------------------------------+
| Transport  | Reliable/unreliable delivery                |
|            | Error correction                            |
+------------+---------------------------------------------+
| Network    | Logical addressing, path determination      |
+------------+---------------------------------------------+
| Data Link  | Framing, MAC addressing, error detection    |
+------------+---------------------------------------------+
| Physical   | Moves bits, wiring, voltage, cabling        |
+------------+---------------------------------------------+


Sender              Receiver
  |---- SYN ------->|
  |<--- SYN/ACK ----|
  |---- ACK ------->|
Connection Established
Data Transfer (Segments)
  |---- FIN ------->|



Sender              Receiver
 |----->|           Buffer full
 |----->|           Segments processed
 |----->|  STOP!   (Red arrow)
             GO!   (Green arrow)
 |----->|
 |----->|



Sender               Receiver
Send 1 -------------->|
Send 2 -------------->|
Send 3 -------------->|
           <--- Ack 4 |
Send 4 -------------->|
Send 5 -------------->|
Send 6 -------------->|
           <--- Ack 7 |
Send 7 -------------->|



Send 1 -------------->|
Send 2 -------------->|
Send 3 -------------->|
           <--- Ack 4 |
Send 4 -------------->|
Send 5 ---X Lost in transit
Send 6 -------------->|
           <--- Ack 5 |
Send 5 (Retransmit) -->|
Send 7 -------------->|
           <--- Ack 7 |



192.168.1.0/24 -- RouterA -- 192.168.2.0/24 -- RouterB -- 192.168.3.0/24

|---Routing Table---|
|Dest.Net | Interface | Metric|
|192.168.1.0 | Fa0/1 | 0     |
|192.168.2.0 | S0/0  | 0     |
|192.168.3.0 | S0/0  | 1     |



[Router]--- FastEthernet 0/0
     |
     +--- FastEthernet 0/1
     |
     +--- Serial0 --- (WAN) --- [Internet]



+-------------------+
|   Data Link Layer |
+-------------------+----------+
| LLC Layer 802.2              |
| MAC Layer 802.3 & 802.11     |
+------------------------------+




PDU      OSI Layer      Example Data Structure
Datagram Application    [Application Data]
Segment  Transport      [TCP Header][Data]
Packet   Network        [IP Header][Data]
Frame    Data Link      [Frame][LLC][Data][FCS]
Bits     Physical       [Transmitted 1s and 0s]

