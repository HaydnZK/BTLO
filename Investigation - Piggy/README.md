# BTLO: Piggy – Network Investigation

This investigation involved analyzing network activity using Wireshark, performing OSINT checks, and mapping observed activity to the 
MITRE ATT&CK framework. The exercise helped build skills in packet analysis, threat intelligence, and understanding malicious infrastructure.

## PCAP One
### Question One: What remote IP address was used to transfer data over SSH? (Format: X.X.X.X)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
35.221.33.16
</details>

Opened the first PCAP file in Wireshark and filtered by protocol to isolate SSH traffic. After reviewing the packets, only two IP addresses 
were communicating within the SSH stream. The destination address consistently shown in these packets was identified as the remote system 
involved in the data transfer.

### Question Two: How much data was transferred in total? (Format: XXXX M)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
1131 M
</details>

Used Wireshark’s Conversations statistics to analyze communication between hosts. The connection between the malicious IP (35.221.33.16) and 
the internal host (10.0.9.171) was located, and the data statistics for this connection revealed the total amount of information transferred.

## PCAP Two

### Question Three: Review the IPs the infected system has communicated with. Perform OSINT searches to identify the malware family tied to this 
infrastructure. (Format: MalwareName)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
Trickbot
</details>

Examined network conversations in the second PCAP, focusing on the IP address that had communicated with the malicious host from the previous 
capture. External IPs were collected and checked using VirusTotal. Multiple addresses were flagged as malicious and consistently linked to the 
Trickbot malware family.

### Question Four: What are the ASN numbers for the two IPs communicating on unusual ports? (Format: ASN, ASN)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
14061, 63949
</details>

Filtered the PCAP by unusual ports (8000 and 8080) and identified the two communicating IPs: 104.236.57.24 and 194.233.171.171. OSINT lookup on 
VirusTotal revealed their associated ASN numbers, providing the answer.

## PCAP Three

### Question Five: Perform OSINT checks. What malware category have these IPs been attributed to historically? (Format: MalwareType)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
Miner
</details>

Using VirusTotal, both IPs communicating on unusual ports were flagged for malicious activity. Details consistently identified them as associated 
with cryptocurrency mining operations.

### Question Six: What ATT&CK technique is most closely related to this activity? (Format: TXXXX)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
T1496
</details>

After linking the IPs to mining malware, the MITRE ATT&CK framework was consulted. The activity matched T1496 – Resource Hijacking, describing 
malware that uses system resources for unauthorized purposes.

## PCAP Four

### Question Seven: How long into the capture was the first TXT record query made? (Format: X.xxxxxx)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
8.527712
</details>

Set Wireshark’s time display format to seconds since the beginning of the capture. DNS packets were filtered and examined to locate the first 
TXT record query, which occurred 8.527712 seconds into the capture.

### Question Eight: What is the date and timestamp of the first TXT record query? (Format: YYYY-MM-DD HH:MM:SS)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
2024-05-24 10:08:50
</details>

Changed the time display format to UTC Date and Time of Day. The timestamp for the first TXT record query appeared directly in the packet list.

### Question Nine: What is the ATT&CK subtechnique relating to this activity? (Format: TXXXX.xxx)
<details>
<summary><b>Answer:</b> Click to reveal</summary>
T1071.004
</details>

The ATT&CK framework was searched for techniques related to DNS TXT queries used for command-and-control and data exchange. The observed DNS-based, 
application-layer tunneling behavior matched T1071.004. This subtechnique describes using DNS as an application-layer protocol to blend malicious 
communications with normal traffic and avoid network filtering.
