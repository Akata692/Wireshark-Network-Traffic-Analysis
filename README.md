# 🔍 Wireshark Network Traffic Analysis & Investigation

<p align="center">
  <img src="https://img.shields.io/badge/Tool-Wireshark-blue?style=for-the-badge&logo=wireshark" />
  <img src="https://img.shields.io/badge/Domain-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-Network%20Forensics-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" />
</p>

<p align="center">
  <b>Hands-on Network Traffic Analysis, Packet Inspection, Threat Detection and Digital Forensics Using Wireshark.</b>
</p>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Project Objectives](#-project-objectives)
- [Tools and Technologies](#-tools-and-technologies)
- [Repository Structure](#-repository-structure)
- [Practical Exercises](#-practical-exercises)
  - [01. Identifying the Attacker's IP Address](#01-identifying-the-attackers-ip-address)
  - [02. Following TCP Stream](#02-following-tcp-stream)
  - [03. Following TCP Stream – Part 2](#03-following-tcp-stream--part-2)
  - [04. HTTP Plaintext Credentials](#04-http-plaintext-credentials)
  - [05. Brute Force Attack Detection](#05-brute-force-attack-detection)
  - [06. VoIP Call Replay](#06-voip-call-replay)
- [Challenges and Troubleshooting](#-challenges-and-troubleshooting)
- [Key Lessons Learned](#-key-lessons-learned)
- [Security Recommendations](#-security-recommendations)
- [Skills Gained](#-skills-gained)
- [Conclusion](#-conclusion)
- [Disclaimer](#-disclaimer)

---

## 📖 Project Overview

Network traffic analysis is an essential component of cybersecurity, digital forensics, and incident response. Understanding how devices communicate across a network makes it possible to investigate suspicious activities, identify potential security threats, and detect information that may be exposed during transmission.

As part of my continuous journey into Cybersecurity with, I undertook a practical network traffic analysis exercise using **Wireshark**, an open-source network protocol analyser.

The exercise focused on capturing, filtering, inspecting, and analysing network packets to understand how different network activities can reveal valuable information during a security investigation.

Throughout this project, I explored six practical areas:

1. Identifying an attacker's IP address.
2. Following and reconstructing TCP streams.
3. Analysing additional TCP stream communications.
4. Investigating HTTP plaintext credentials.
5. Detecting suspicious brute-force authentication attempts.
6. Analysing and replaying VoIP calls.

This project provided an opportunity to apply theoretical networking and cybersecurity concepts to practical network forensic investigations.

## 🎯 Project Objectives

The primary objectives of this project were to:

- Understand how to capture network traffic using Wireshark.
- Identify suspicious IP addresses through packet analysis.
- Understand TCP communication and session reconstruction.
- Investigate unencrypted HTTP communication.
- Recognise potential credential exposure during transmission.
- Detect suspicious authentication patterns associated with brute-force attacks.
- Analyse SIP signalling and RTP media streams.
- Understand how captured network traffic can support digital forensic investigations.
- Develop practical troubleshooting and network investigation skills.

## 🧰 Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| Wireshark | Network packet capture and analysis |
| TCP/IP | Network communication analysis |
| HTTP | Inspection of web traffic |
| TCP Stream | Reconstruction of network conversations |
| SIP | VoIP signalling analysis |
| RTP | Real-time audio stream analysis |
| IP Addressing | Identification of communicating endpoints |
| Display Filters | Filtering and isolating relevant packets |

## 📂 Repository Structure

The project is organised into six practical exercises, with separate folders for screenshots and investigation findings.

```text
Wireshark-Network-Traffic-Analysis/
│
├── README.md
│
├── 01-Attacker-IP-Identification/
│   ├── screenshots/
│   └── findings.md
│
├── 02-Follow-TCP-Stream/
│   ├── screenshots/
│   └── findings.md
│
├── 03-Follow-TCP-Stream-Part-2/
│   ├── screenshots/
│   └── findings.md
│
├── 04-HTTP-Plaintext-Credentials/
│   ├── screenshots/
│   └── findings.md
│
├── 05-Brute-Force-Detection/
│   ├── screenshots/
│   └── findings.md
│
├── 06-VoIP-Call-Replay/
│   ├── screenshots/
│   └── findings.md
│
└── lessons-learned.md
```

---

# 🔬 Practical Exercises

## 01. Identifying the Attacker's IP Address

**Objective:** Investigate captured network traffic to identify the source IP address associated with suspicious communication.

### Work Performed

- Captured network traffic using Wireshark.
- Examined source and destination IP addresses.
- Applied display filters to isolate relevant communications.
- Analysed packet conversations and communication patterns.
- Used the Statistics → Endpoints and Statistics → Conversations features.
- Investigated unusual connections and identified potential sources of suspicious activity.

### Useful Wireshark Filters

```wireshark
ip
```

Displays IPv4 traffic.

```wireshark
ip.addr == 192.168.10.10
```

Filters traffic involving a particular IP address.

```wireshark
ip.src == 192.168.10.66<img width="2736" height="1824" alt="tcp00" src="https://github.com/user-attachments/assets/1496f738-112d-4b03-984c-85ec09b6020f" />

```

Displays packets originating from a particular IP address.

### Challenges Encountered

- Identifying suspicious traffic among numerous legitimate packets.
- Distinguishing the original source of suspicious traffic from intermediate network devices.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Large volumes of packets made identifying suspicious connections difficult. | Applied IP-related display filters and used the Conversations feature to narrow down the investigation. |
| Multiple devices communicated with the target system, making attribution difficult. | Examined source and destination addresses, ports, timestamps, and communication patterns to identify the likely source of suspicious activity. |

### Key Lesson Learnt

Identifying a potential attacker's IP address requires analysing communication patterns and correlating multiple packet details rather than relying on a single packet.

An IP address alone does not conclusively establish an attacker's identity.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="tcp0" src="https://github.com/user-attachments/assets/9e0aef60-4058-405a-a8ad-87c6ca55bc49" />

`01-Attacker-IP-Identification/screenshots/`

Suggested evidence:
- Captured network traffic.
- IP address filtering.
- Conversations analysis.
- Identified suspicious source IP.

---

## 02. Following TCP Stream

**Objective:** Reconstruct and analyse TCP communication between two endpoints to understand the data exchanged during a network session.

### Work Performed

- Captured TCP traffic using Wireshark.
- Identified relevant TCP packets.
- Selected a packet and used Follow → TCP Stream.
- Reconstructed the communication between the client and server.
- Examined transmitted information and the sequence of communication.
- Investigated how TCP streams provide context during network forensic investigations.

### Useful Wireshark Filters

```wireshark
tcp
```

Displays TCP traffic.

```wireshark
tcp.stream eq 0
```

Displays packets belonging to TCP stream 0.

```wireshark
tcp.port == 80
```

Displays TCP traffic involving port 80.

### Challenges Encountered

- Understanding how individual TCP packets contribute to a complete communication session.
- Distinguishing between client requests and server responses.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Individual packets contained fragmented pieces of communication. | Used Follow TCP Stream to reconstruct the conversation into a readable sequence. |
| Difficulty distinguishing the two communicating endpoints. | Examined stream direction and colour-coded client/server data to understand the communication flow. |

### Key Lesson Learnt

TCP stream reconstruction is an important network forensic technique because it provides communication context that individual packets may not reveal.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="tcp0" src="https://github.com/user-attachments/assets/1ed098b5-8b17-4ab5-a73c-fe6a4e214a56" />


`02-Follow-TCP-Stream/screenshots/`

Suggested evidence:
- TCP packet selection.
- Follow TCP Stream option.
- Reconstructed TCP conversation.

---

## 03. Following TCP Stream – Part 2

**Objective:** Extend TCP stream analysis by investigating additional network conversations and understanding the relationship between different communication sessions.

### Work Performed

- Continued analysing captured TCP sessions.
- Investigated multiple TCP streams.
- Examined transmitted content and communication exchanges.
- Compared different client-server conversations.
- Investigated how encrypted and unencrypted traffic affects packet visibility.
- Used stream identifiers and packet filters to isolate relevant sessions.

### Useful Wireshark Filters

```wireshark

tcp.stream eq 1
```

Displays packets belonging to TCP stream 1.

```wireshark
tcp.flags.syn == 1
```

Identifies TCP packets with the SYN flag set.

```wireshark
tcp.flags.fin == 1
```

Identifies TCP packets with the FIN flag set.

### Challenges Encountered

- Analysing multiple TCP streams without confusing their respective sessions.
- Understanding the limitations of inspecting encrypted communication.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Difficulty locating the specific conversation of interest among multiple TCP streams. | Used stream identifiers, packet filters, and endpoint information to isolate the relevant session. |
| Some reconstructed conversations contained unreadable or encrypted data. | Examined protocol information and identified the limitations of analysing encrypted sessions without appropriate decryption material. |

### Key Lesson Learnt

Understanding TCP sessions requires more than reconstructing conversations. Investigators must understand network protocols, encryption, and the limitations of packet inspection.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="tcp01" src="https://github.com/user-attachments/assets/851da836-53b1-4e91-b465-5a62c360a1b9" />


`03-Follow-TCP-Stream-Part-2/screenshots/`

Suggested evidence:
- Additional TCP stream analysis.
- Stream identification.
- Comparison of different conversations.
- Encrypted versus readable traffic.

---

## 04. HTTP Plaintext Credentials

**Objective:** Investigate how sensitive authentication information can be exposed when transmitted over unencrypted HTTP connections.

### Work Performed

- Captured HTTP traffic in an authorised lab environment.
- Applied HTTP display filters.
- Identified HTTP POST requests.
- Inspected packet details and transmitted request data.
- Used Follow TCP Stream to examine HTTP communication.
- Investigated how credentials can appear in plaintext during unencrypted transmission.

### Useful Wireshark Filters

```wireshark
http
```

Displays HTTP traffic.

```wireshark
http.request.method == "POST"
```

Identifies HTTP POST requests.

```wireshark
http.request.method == "GET"
```

Identifies HTTP GET requests.

### Challenges Encountered

- Locating authentication requests among other HTTP traffic.
- Understanding how plaintext credentials appear within packet data.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Difficulty identifying packets containing authentication information. | Applied the HTTP POST filter and inspected relevant request fields. |
| Authentication information was not immediately visible in the packet overview. | Examined packet details and followed the corresponding TCP stream to inspect the HTTP request body. |

### Key Lesson Learnt

Transmitting sensitive credentials over HTTP creates a serious security risk because information may be intercepted and exposed.

HTTPS, TLS encryption, secure authentication practices, and proper session management are essential for protecting user information.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="21" src="https://github.com/user-attachments/assets/e49aafd7-afe4-4986-99db-f19108d2f835" />


`04-HTTP-Plaintext-Credentials/screenshots/`

Suggested evidence:
- HTTP traffic capture.
- HTTP POST request.
- Packet details.
- Follow TCP Stream analysis.

**Security Note:** Never publish actual usernames, passwords, session tokens, or other confidential information in screenshots or repository files.

---

## 05. Brute Force Attack Detection

**Objective:** Investigate captured network traffic for suspicious authentication patterns that may indicate brute-force password-guessing activity.

### Work Performed

- Analysed captured network traffic for repeated authentication attempts.
- Examined source IP addresses and destination ports.
- Investigated timestamps and request frequency.
- Identified repeated authentication requests.
- Compared communication patterns to identify potential automated password-guessing activity.
- Used packet filtering and traffic analysis to investigate suspicious behaviour.

### Useful Wireshark Filters

```wireshark
tcp
```

Displays TCP traffic.

```wireshark
ip.src == 192.168.1.100
```

Isolates traffic originating from a particular source IP.

```wireshark
tcp.flags.syn == 1
```

Helps identify TCP connection initiation attempts.

For HTTP-based authentication:

```wireshark
http.request.method == "POST"
```

Filters HTTP POST requests for further authentication analysis.

### Challenges Encountered

- Distinguishing legitimate failed login attempts from automated brute-force activity.
- Identifying repeated authentication attempts occurring across different TCP connections.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Repeated authentication requests were difficult to distinguish from normal user activity. | Compared request frequency, timestamps, source addresses, and authentication response patterns to identify suspicious repetition. |
| Authentication attempts used different TCP connections, making the activity appear unrelated. | Correlated packets using source and destination addresses, service ports, timestamps, and protocol-specific authentication indicators. |

### Key Lesson Learnt

Brute-force detection depends on identifying suspicious patterns and correlating events. Network traffic analysis can provide valuable evidence for detecting unusual authentication behaviour.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="23" src="https://github.com/user-attachments/assets/8449856e-5903-448c-b0fe-56a44e0d8ca1" />

`05-Brute-Force-Detection/screenshots/`

Suggested evidence:
- Repeated authentication requests.
- Source IP analysis.
- Relevant packet timestamps.
- Suspicious authentication patterns.

---

## 06. VoIP Call Replay

**Objective:** Investigate captured Voice over Internet Protocol (VoIP) traffic and understand how SIP signalling and RTP media streams can be analysed and reconstructed.

### Work Performed

- Captured VoIP traffic in an authorised lab environment.
- Investigated SIP signalling packets.
- Identified associated RTP media streams.
- Used Wireshark's Telephony → VoIP Calls feature.
- Examined call information and associated packet streams.
- Explored how captured RTP traffic can be reconstructed and replayed using Wireshark's VoIP analysis capabilities.

### Useful Wireshark Filters

```wireshark
sip
```

Displays SIP signalling traffic.

```wireshark
rtp
```

Displays RTP traffic when the packets are recognised or decoded as RTP.

```wireshark
udp
```

Displays UDP traffic, which is commonly used for RTP media transmission.

### Challenges Encountered

- Identifying SIP signalling packets and their associated RTP streams.
- Understanding the relationship between call setup information and actual audio transmission.

### Problems Encountered and Solutions

| Problem | Solution |
|---|---|
| Difficulty identifying RTP packets associated with a particular VoIP call. | Used Telephony → VoIP Calls and RTP stream analysis to identify and isolate the relevant call traffic. |
| Audio replay was affected by missing packets, incomplete captures, or incorrect stream selection. | Verified the selected RTP stream, checked packet completeness, and used the appropriate VoIP playback functionality. |

### Key Lesson Learnt

VoIP traffic contains valuable forensic information. Understanding SIP signalling and RTP media streams makes it possible to investigate communication patterns and analyse captured calls.

### 📸 Screenshots / Evidence

<img width="2736" height="1824" alt="labonwireshartVoip" src="https://github.com/user-attachments/assets/bd5cf2b9-950c-4446-93f9-09ded67b7b47" />


`06-VoIP-Call-Replay/screenshots/`

Suggested evidence:
- SIP signalling packets.
- VoIP Calls analysis window.
- RTP stream identification.
- Audio reconstruction or playback interface.

**Privacy Note:** VoIP recordings may contain private conversations. Only analyse and replay recordings obtained with appropriate authorisation.

---

# ⚠️ Challenges and Troubleshooting

Throughout the practical exercises, several challenges highlighted the importance of understanding network protocols and using the appropriate Wireshark analysis features.

| Challenge | Troubleshooting Approach |
|---|---|
| Large volumes of network traffic | Applied targeted display filters. |
| Difficulty identifying relevant communication | Used Conversations, Endpoints, and packet details. |
| Fragmented TCP communication | Used Follow TCP Stream. |
| Encrypted traffic | Identified protocol encryption and its visibility limitations. |
| Exposed HTTP authentication data | Inspected HTTP requests and TCP streams. |
| Repeated authentication attempts | Correlated source IPs, timestamps, and authentication patterns. |
| VoIP stream identification | Used Telephony → VoIP Calls and RTP analysis. |

# 📚 Key Lessons Learnt

This practical exercise strengthened my understanding of network forensics and the importance of packet-level analysis in cybersecurity investigations.

My major takeaways include:

**1. Network Visibility Matters**

Captured network traffic can reveal suspicious communication patterns that may otherwise go unnoticed.

**2. Protocol Knowledge Is Essential**

Understanding TCP, HTTP, SIP, RTP, and other protocols makes network traffic analysis more effective.

**3. Encryption Protects Sensitive Information**

Unencrypted communication can expose credentials and other confidential information.

**4. Correlation Is Critical**

Effective investigations require connecting IP addresses, ports, timestamps, protocols, and packet contents.

**5. Evidence Must Be Handled Carefully**

Network captures can contain sensitive information and should be securely stored, handled, and analysed.

**6. Practical Skills Complement Theoretical Knowledge**

Working with Wireshark provided a better understanding of how network communication operates and how suspicious activities can be investigated.

---

# 🛡️ Security Recommendations

Based on the areas explored in this project, the following security practices are recommended:

- Enforce HTTPS and TLS encryption for web applications.
- Avoid transmitting sensitive information over unencrypted protocols.
- Implement account lockout policies and authentication rate limiting.
- Deploy intrusion detection and prevention systems.
- Monitor unusual authentication patterns.
- Maintain network logs for incident investigation.
- Implement network segmentation and access controls.
- Secure VoIP infrastructure and protect captured communication data.
- Regularly review network traffic for suspicious activity.

---

# 🚀 Skills Gained

Through this hands-on exercise, I developed and strengthened the following technical skills:

| Skill | Practical Application |
|---|---|
| Network Packet Analysis | Capturing and examining network traffic |
| IP Address Investigation | Identifying suspicious communication sources |
| TCP Stream Analysis | Reconstructing client-server conversations |
| HTTP Analysis | Investigating unencrypted web traffic |
| Credential Exposure Investigation | Understanding plaintext authentication risks |
| Brute Force Detection | Analysing suspicious authentication patterns |
| VoIP Forensics | Investigating SIP and RTP communication |
| Wireshark Display Filters | Isolating relevant network packets |
| Incident Investigation | Correlating network evidence |

---

# 📝 Conclusion

This Wireshark practical exercise was a valuable opportunity to move beyond theoretical cybersecurity knowledge and gain hands-on experience in network traffic analysis.

By completing the six exercises, I gained practical exposure to identifying suspicious IP addresses, reconstructing TCP conversations, investigating plaintext HTTP credentials, detecting potential brute-force activity, and analysing VoIP communication.

The exercise reinforced the importance of network visibility, protocol knowledge, encryption, and evidence correlation in cybersecurity investigations.

It also strengthened my interest in **Network Security, Digital Forensics, Threat Detection, and Incident Response**.

I look forward to building on these skills through additional practical cybersecurity labs and real-world security investigation scenarios.

---

## 🔗 Connect and Follow My Learning Journey

I am continuously developing my technical skills in Cybersecurity, Digital Forensics, Network Security, and IT Infrastructure.

If you find this project useful, feel free to ⭐ star the repository, explore the practical exercises, and share your feedback.

**Tools:** Wireshark | TCP/IP | HTTP | SIP | RTP

**Areas of Interest:** Cybersecurity | Network Forensics | Digital Forensics | Incident Response | Threat Detection

---

## ⚖️ Disclaimer

This project was created strictly for educational purposes and authorised cybersecurity lab practice.

All packet captures, traffic inspections, credential analysis, brute-force investigations, and VoIP replay activities should only be performed on networks and systems for which appropriate permission has been obtained.

Do not use these techniques to intercept, access, or disclose private communications or credentials without authorisation.

---

# Author
Nicholas Gyemfi 

Cybersecurity Entusiast

LinkedIn: [https://www.linkedin.com/in/nic-gyim/](https://www.linkedin.com/in/nic-gyim/)


<p align="center">
  <b>Learn. Practise. Analyse. Secure.</b>
  <br>
  <i>Building practical cybersecurity skills, one packet at a time.</i>
</p>

#Wireshark #Cybersecurity #NetworkForensics #DigitalForensics #PacketAnalysis #EthicalHacking #IncidentResponse #ThreatDetection #InformationSecurity
