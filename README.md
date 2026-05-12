# Wireshark-Traffic-Anaysis-Lab-
This project documents a beginner Wireshark traffic analysis lab focused on capturing, filtering, and analyzing real network traffic.
The goal of the lab was to build foundational packet analysis skills commonly used in:

Network troubleshooting
Security Operations Center (SOC) workflows
Threat hunting
Incident response
Network visibility and monitoring

The lab focused on understanding how devices communicate across a network and how different protocols appear in packet captures.

Objectives
Install and configure Wireshark
Capture live network traffic
Analyze TCP and TLS traffic
Observe encrypted HTTPS communications
Filter traffic using Wireshark display filters
Inspect DNS requests and responses
Generate and analyze ICMPv6 traffic
Explore TCP streams and protocol hierarchy statistics
Practice interpreting packet metadata and communication flows
Tools Used
Wireshark
Windows 11
Command Prompt (ping utility)


Lab Environment

The lab was performed on a Windows laptop connected to a home Wi-Fi network.

Traffic was captured from the active wireless interface and analyzed locally using Wireshark.

Sensitive information such as internal IP addresses and MAC addresses has been intentionally omitted or redacted from screenshots for operational security and privacy purposes.

Traffic Captured

The following traffic types were observed during analysis:

Protocol	Purpose
TCP	Reliable transport protocol
TLS	Encrypted HTTPS communications
DNS	Domain name resolution
ICMPv6	IPv6 ping and network messaging
Step 1 — Installing Wireshark

Wireshark was installed along with Npcap to allow packet capture functionality on Windows.

After installation, active network interfaces were identified from the Wireshark home screen.

<img width="971" height="658" alt="Screenshot 2026-05-12 134043" src="https://github.com/user-attachments/assets/7a31d6ad-aea7-4395-b73b-fecf61bbd1c8" />


Step 2 — Capturing Live Traffic

The active Wi-Fi interface was selected and live traffic capture was started.

Initial packet captures included:

TCP traffic
TLS encrypted traffic
Background network communications
Browser-related HTTPS traffic


<img width="788" height="314" alt="Screenshot 2026-05-12 141548" src="https://github.com/user-attachments/assets/44ebcf7f-ecd1-445a-a87e-8006edbfaf19" />


Step 3 — TCP Traffic Filtering

The following display filter was used:

tcp

This isolated TCP traffic from other protocols and allowed inspection of:

Source IPs
Destination IPs
Ports
Packet lengths
TCP acknowledgements and sequence information
Screenshot Placeholder

<img width="517" height="360" alt="Screenshot 2026-05-12 141654" src="https://github.com/user-attachments/assets/e0779890-81ca-4bb9-aa64-08360d6d2867" />


Step 4 — TLS / HTTPS Traffic Analysis

The following display filter was used:

tls

This revealed encrypted HTTPS communications occurring on the network.

Observed TLS activity included:

Client Hello
Server Hello
Certificate exchanges
Encrypted application data

This demonstrated how modern internet traffic is predominantly encrypted.

<img width="512" height="610" alt="Screenshot 2026-05-12 141738" src="https://github.com/user-attachments/assets/1f44cbca-11f2-4434-a3e9-bd24211a6392" />



Step 5 — Packet Inspection

Individual packets were inspected using Wireshark’s three-pane layout:

Packet List Pane
Packet Details Pane
Packet Bytes Pane

TLS packet details were expanded to observe:

TLS versions
Handshake information
Encryption metadata

Step 6 — Following TCP Streams

The “Follow TCP Stream” feature was used to analyze conversations between hosts.

This demonstrated how Wireshark can reconstruct communication sessions between systems.

<img width="1364" height="720" alt="Screenshot 2026-05-12 135731" src="https://github.com/user-attachments/assets/74b9328e-6f1b-403a-84f0-f7333e5a8730" />


Step 7 — DNS Analysis

The following filter was used:

dns

DNS traffic was analyzed to observe:

Domain name lookups
DNS requests
DNS responses
Name resolution behavior

This demonstrated how systems discover the IP addresses of external services and websites.

<img width="512" height="617" alt="Screenshot 2026-05-12 142012" src="https://github.com/user-attachments/assets/a1893dbe-c439-4e08-b330-5a5f1b0dd683" />


Step 8 — HTTP vs HTTPS Observation

An HTTP filter was tested:

http

Very little or no HTTP traffic was observed.

This highlighted an important modern networking concept:

Most modern web traffic now uses encrypted HTTPS/TLS communications instead of plaintext HTTP.

This limits visibility into packet contents while still allowing analysis of metadata such as:

IP addresses
Ports
Timing
Session behavior
Step 9 — ICMPv6 Traffic Generation

ICMP traffic was intentionally generated using the Windows ping command:

ping google.com

The initial ICMP filter showed no results because the traffic was using IPv6.

The following filter successfully identified the traffic:

icmpv6

This demonstrated the distinction between:

ICMP (IPv4)
ICMPv6 (IPv6)

Observed traffic included:

Echo Requests
Echo Replies
Neighbor Solicitation messages
Neighbor Advertisement messages

<img width="515" height="412" alt="Screenshot 2026-05-12 142141" src="https://github.com/user-attachments/assets/bd1e82d0-fbe9-4c03-b165-ddd4edd33d68" />


Step 10 — Protocol Hierarchy Statistics

Wireshark’s Protocol Hierarchy statistics feature was used to observe protocol distribution across the packet capture.

This provided insight into:

Which protocols dominated the capture
Traffic composition
Relative protocol usage


<img width="1364" height="720" alt="Screenshot 2026-05-12 140511" src="https://github.com/user-attachments/assets/db52b36c-b4cc-47c8-ad85-4b7838f0b502" />


Key Findings

Most observed traffic was encrypted using TLS/HTTPS
DNS traffic revealed domain resolution behavior
TCP filtering simplified packet analysis workflows
ICMPv6 traffic demonstrated active IPv6 communications
Wireshark provides strong visibility into network metadata even when payloads are encrypted
Skills Demonstrated
Packet capture
Network traffic filtering
Protocol analysis
TCP/IP fundamentals
TLS inspection
DNS analysis
ICMPv6 analysis
Traffic interpretation
Basic network troubleshooting
Lessons Learned

This lab reinforced the importance of:

Understanding network protocols
Recognizing encrypted traffic patterns
Using filters effectively
Interpreting packet metadata
Understanding IPv4 vs IPv6 behavior

The project also demonstrated how defenders and analysts can investigate network activity even when packet contents are encrypted.

Future Improvements

Potential future expansions:

Malware traffic analysis
Suspicious DNS query investigation
Packet export analysis
Wireshark color rule customization
HTTP authentication capture in a controlled lab
PCAP analysis from public malware datasets
SIEM integration workflows
Detection engineering exercises
