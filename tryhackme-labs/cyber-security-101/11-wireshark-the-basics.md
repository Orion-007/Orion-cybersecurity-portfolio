# Wireshark: The Basics

The **Wireshark: The Basics** room introduced me to one of the most important tools used for network traffic analysis.

After completing the networking section of **TryHackMe Cyber Security 101**, this room gave me the opportunity to apply those networking concepts practically by inspecting real packets and PCAP files.

I learned how to navigate Wireshark, capture and inspect network traffic, dissect packets across different TCP/IP/OSI layers, search and navigate packet captures, follow network conversations, and use display filters to isolate traffic during an investigation. :contentReference[oaicite:0]{index=0}

---

## 🧠 What I Learned

### 🦈 What is Wireshark?

**Wireshark** is an open-source, cross-platform network packet analyzer.

It can be used to:

- Capture live network traffic
- Inspect existing packet captures (**PCAPs**)
- Troubleshoot network problems
- Investigate suspicious network activity
- Identify unusual ports and hosts
- Analyze network protocols
- Examine response codes and payload data

An important distinction I learned is that **Wireshark is not an Intrusion Detection System (IDS)**.

It does not automatically determine whether traffic is malicious and does not modify packets. Instead, it gives analysts visibility into network traffic so they can investigate what happened.

This means the effectiveness of Wireshark depends heavily on the analyst's networking knowledge and investigation skills. :contentReference[oaicite:1]{index=1}

---

# 🖥️ Understanding the Wireshark Interface

The Wireshark GUI provides several areas for capturing, filtering, and analyzing network traffic.

Some of the main components include:

- **Toolbar** – Provides shortcuts for capturing, filtering, sorting, exporting, merging, and processing packets.
- **Display Filter Bar** – Used to filter displayed traffic.
- **Recent Files** – Displays recently analyzed capture files.
- **Capture Filters & Interfaces** – Allows the selection of network interfaces and capture filters.
- **Status Bar** – Displays information about Wireshark, the active profile, and packet statistics.

Understanding the interface makes navigating large packet captures much easier. :contentReference[oaicite:2]{index=2}

---

# 📂 Loading PCAP Files

Wireshark can analyze previously captured network traffic stored in files such as:

```text
.pcap
.pcapng
```

A capture can be loaded by:

```text
File → Open
```

or by dragging and dropping the capture into Wireshark.

Once loaded, Wireshark processes the packets and presents the traffic for analysis. :contentReference[oaicite:3]{index=3}

---

# 🔎 The Three Packet Panes

One of the most important things I learned was how Wireshark organizes packet information into three panes.

### 1. Packet List Pane

Provides a summary of captured packets, including information such as:

```text
Packet Number
Time
Source
Destination
Protocol
Length
Information
```

Selecting a packet displays additional information in the other panes.

### 2. Packet Details Pane

Provides a detailed breakdown of the protocols and fields contained inside the selected packet.

### 3. Packet Bytes Pane

Displays the raw packet data using:

```text
Hexadecimal
+
Decoded ASCII
```

Selecting information from the packet details pane highlights the corresponding bytes in the packet bytes pane. :contentReference[oaicite:4]{index=4}

---

# 🎨 Packet Colouring

Wireshark uses colors to make different types of traffic easier to identify.

This helps analysts quickly recognize protocols and potentially interesting traffic within large packet captures.

I learned that Wireshark supports two types of colouring rules:

```text
Temporary Colouring Rules
Permanent Colouring Rules
```

Temporary rules only remain during the current session, while permanent rules are stored in the Wireshark profile.

Permanent rules can be managed through:

```text
View → Coloring Rules
```

:contentReference[oaicite:5]{index=5}

---

# 📡 Capturing Network Traffic

Wireshark can capture live traffic directly from network interfaces.

The interface provides controls to:

```text
Start Capture
Stop Capture
Restart Capture
```

The status bar also displays information such as the interface being used and the number of captured packets.

This allows Wireshark to observe network communication as it occurs. :contentReference[oaicite:6]{index=6}

---

# 🔗 Merging PCAP Files

Multiple capture files can be combined into a single PCAP.

This can be done using:

```text
File → Merge
```

Wireshark combines the selected capture with the currently opened capture, after which the merged file needs to be saved.

This can be useful when traffic from multiple captures needs to be analyzed together. :contentReference[oaicite:7]{index=7}

---

# 📋 Capture File Properties

Wireshark can also display information about the capture file itself.

This includes:

```text
File Hash
Capture Time
Comments
Network Interface
Statistics
```

These details can help identify, classify, and prioritize capture files during an investigation.

They can be accessed through:

```text
Statistics → Capture File Properties
```

:contentReference[oaicite:8]{index=8}

---

# 🧩 Packet Dissection

One of the most useful concepts in this room was **packet dissection**, also known as **protocol dissection**.

Wireshark decodes protocols and their fields so analysts can examine the structure of individual packets.

This connects directly with the OSI model I learned earlier in Cyber Security 101. :contentReference[oaicite:9]{index=9}

---

## Layer 1 – Frame

The Frame section provides information about the captured packet and details associated with the physical layer.

```text
Frame
↓
Capture information
Packet length
Arrival time
Interface information
```

---

## Layer 2 – MAC Addresses

The Ethernet section provides the:

```text
Source MAC Address
Destination MAC Address
```

These correspond to the **Data Link Layer**. :contentReference[oaicite:10]{index=10}

---

## Layer 3 – IP Addresses

The IP section can reveal:

```text
Source IP
Destination IP
TTL
Protocol
Other IP header information
```

This corresponds to the **Network Layer**. :contentReference[oaicite:11]{index=11}

---

## Layer 4 – TCP/UDP

The Transport Layer contains information about protocols such as:

```text
TCP
UDP
```

Wireshark can display information including:

```text
Source Port
Destination Port
Sequence Numbers
Acknowledgement Numbers
TCP Flags
Payload Information
```

It can also identify situations where TCP segments need to be reassembled. :contentReference[oaicite:12]{index=12}

---

## Application Protocol

Wireshark can identify application-level protocols such as:

```text
HTTP
FTP
SMB
```

Depending on the protocol and whether the traffic is encrypted, it may also reveal application-specific data contained inside the packet. :contentReference[oaicite:13]{index=13}

---

# 🧭 Packet Navigation

Large PCAP files can contain thousands of packets, so efficient navigation is important.

Wireshark assigns each packet a unique packet number.

This makes it easier to return to specific packets during an investigation. :contentReference[oaicite:14]{index=14}

---

# 🔍 Finding Packets

Wireshark allows analysts to search packet captures for specific information.

The feature can be accessed through:

```text
Edit → Find Packet
```

Packets can be searched using:

```text
Display Filter
Hex
String
Regex
```

Searches can also target different locations:

```text
Packet List
Packet Details
Packet Bytes
```

Choosing the correct search location is important because Wireshark only searches the selected pane for the information. :contentReference[oaicite:15]{index=15}

---

# 🚩 Marking Packets

Interesting packets can be marked for further investigation.

Packets can be marked through:

```text
Edit
```

or the:

```text
Right-Click Menu
```

Marked packets appear black regardless of their original colouring.

One important detail is that packet markings are temporary and disappear when the capture file is closed. :contentReference[oaicite:16]{index=16}

---

# 📝 Packet Comments

Comments can also be added to packets.

Unlike packet markings, comments can remain stored within the capture file.

This can be useful for:

- Documenting findings
- Highlighting suspicious packets
- Recording observations
- Sharing investigation notes with other analysts

:contentReference[oaicite:17]{index=17}

---

# 📤 Exporting Packets

Instead of sharing an entire PCAP containing thousands of packets, Wireshark allows analysts to export only the packets relevant to an investigation.

This can help reduce unnecessary information and keep the investigation focused on suspicious activity.

Packets can be exported using the:

```text
File Menu
```

:contentReference[oaicite:18]{index=18}

---

# 📁 Exporting Objects

Wireshark can also extract certain files transferred across network traffic.

Supported streams covered in the room include:

```text
DICOM
HTTP
IMF
SMB
TFTP
```

For security analysts, this can be useful when investigating files transferred across a network and saving them for further analysis. :contentReference[oaicite:19]{index=19}

---

# ⏰ Time Display Format

By default, Wireshark can display packet times as:

```text
Seconds Since Beginning of Capture
```

However, the time format can be changed through:

```text
View → Time Display Format
```

The room highlighted using **UTC** as a useful format when analyzing packet timelines. :contentReference[oaicite:20]{index=20}

---

# ⚠️ Expert Information

Wireshark includes **Expert Information**, which helps identify notable protocol states and possible problems.

Examples include:

```text
Chat  → Normal workflow information
Note  → Notable events
Warn  → Warnings or unusual conditions
Error → Problems such as malformed packets
```

However, these should not automatically be treated as evidence of malicious activity.

Wireshark can produce false positives and false negatives, so the analyst still needs to investigate and interpret the traffic.

Expert Information can be accessed through:

```text
Analyse → Expert Information
```

:contentReference[oaicite:21]{index=21}

---

# 🔬 Packet Filtering

Packet captures can contain huge amounts of traffic.

Wireshark's filtering capabilities allow analysts to remove unnecessary traffic and focus on events of interest.

I learned that Wireshark has two main types of filters:

```text
Capture Filters
Display Filters
```

### Capture Filters

Determine which packets are captured.

### Display Filters

Determine which already-captured packets are displayed.

A useful rule from the room was:

> **If you can click on it, you can filter and copy it.**

:contentReference[oaicite:22]{index=22}

---

# 🎯 Apply as Filter

A value inside a packet can be selected and immediately used as a filter.

This can be done through:

```text
Right Click → Apply as Filter
```

or:

```text
Analyse → Apply as Filter
```

This is a quick way to isolate traffic related to a specific value.

---

# 💬 Conversation Filter

Sometimes I may want to investigate an entire network conversation instead of a single value.

The **Conversation Filter** isolates related packets based on information such as:

```text
IP Addresses
Port Numbers
```

It can be accessed using:

```text
Right Click → Conversation Filter
```

or:

```text
Analyse → Conversation Filter
```

:contentReference[oaicite:23]{index=23}

---

# 🎨 Colourise Conversation

Instead of hiding unrelated packets, Wireshark can highlight packets belonging to a specific conversation.

This can be done using:

```text
View → Colourise Conversation
```

Unlike a Conversation Filter, the packets remain visible while the relevant conversation is visually highlighted. :contentReference[oaicite:24]{index=24}

---

# 🧪 Prepare as Filter

**Prepare as Filter** works similarly to Apply as Filter, but it does not immediately execute the filter.

Instead, Wireshark places the query into the filter bar.

This allows additional conditions to be added using:

```text
AND
OR
```

before applying the final filter. :contentReference[oaicite:25]{index=25}

---

# 📊 Apply as Column

Wireshark allows packet fields to be added as columns in the Packet List Pane.

This can be done using:

```text
Analyse → Apply as Column
```

This makes it easier to compare a specific field across multiple packets in a capture. :contentReference[oaicite:26]{index=26}

---

# 🔄 Follow Stream

Packets normally appear individually, but sometimes an analyst needs to understand the complete communication between systems.

Wireshark can reconstruct network streams using:

```text
Follow TCP Stream
Follow UDP Stream
Follow HTTP Stream
```

This allows the communication to be viewed closer to how it appeared at the application level.

For unencrypted protocols, this may expose transmitted information such as usernames, passwords, and other data.

When a stream is followed, Wireshark automatically creates a filter showing the packets belonging to that stream. :contentReference[oaicite:27]{index=27} :contentReference[oaicite:28]{index=28}

---

# 🔎 Basic Display Filters

I also practiced some simple Wireshark display filters.

## Filter by Protocol

To display HTTP traffic:

```text
http
```

Other examples include:

```text
arp
dhcp
ftp
smtp
pop
imap
```

---

## Filter by TCP Port

Syntax:

```text
tcp.port == <port>
```

Example:

```text
tcp.port == 80
```

This displays TCP traffic associated with port 80.

---

## Filter by UDP Port

Syntax:

```text
udp.port == <port>
```

---

## Filter by IP Address

Syntax:

```text
ip.addr == <IP address>
```

Example:

```text
ip.addr == 192.168.1.2
```

This allows me to isolate traffic associated with a specific IP address. :contentReference[oaicite:29]{index=29}

---

# 🧠 Key Takeaways

- Learned what Wireshark is and how it is used for packet analysis.
- Understood the difference between packet analysis and an IDS.
- Learned how to navigate the Wireshark interface.
- Loaded and analyzed PCAP files.
- Understood the Packet List, Packet Details, and Packet Bytes panes.
- Learned how Wireshark dissects packets across network layers.
- Identified MAC addresses, IP addresses, ports, protocols, and application data.
- Learned how to capture live network traffic.
- Practiced navigating and searching large packet captures.
- Learned how to mark, comment on, and export interesting packets.
- Learned how Wireshark can extract transferred objects.
- Used Expert Information to identify potential network issues.
- Understood the difference between capture and display filters.
- Practiced filtering traffic by protocol, port, and IP address.
- Learned how to isolate and highlight network conversations.
- Learned how to reconstruct TCP, UDP, and HTTP streams.

---

## 🎯 Why This Matters for Cybersecurity

This room helped connect the networking theory I learned earlier with practical traffic analysis.

Instead of only knowing that systems communicate using:

```text
MAC Addresses
IP Addresses
TCP/UDP
Ports
Protocols
```

I can now open a packet capture and begin identifying these components directly inside real network traffic.

Wireshark is especially relevant for areas such as:

```text
SOC Analysis
Network Security
Incident Response
Threat Hunting
Digital Forensics
Network Troubleshooting
```

This is an important step toward learning how security analysts investigate what is actually happening across a network.

---

## 📸 Proof of Completion

![Wireshark: The Basics](../../assets/11-wireshark-the-basics.jpg)
