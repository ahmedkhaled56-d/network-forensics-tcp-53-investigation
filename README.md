# Project 03 — Network Forensics Case Study

**Title:** Remote Shell Communication Observed over TCP Port 53  
**Case ID:** SOC-NF-003  
**Project Type:** Independent Training / Portfolio Case Study  
**Tools:** Wireshark, TCP Stream Analysis, Packet-Level Investigation

> This is an independent training and portfolio project. It does not represent paid client work or professional incident-response employment.

## 1. Executive Summary

The supplied 131-packet PCAP contains an interactive Windows command-shell exchange between `192.168.1.3:1396` and `192.168.1.2:53`.

The responder sends a Windows XP command-prompt banner and directory-listing output. The initiator sends the `dir` and `exit` commands.

The responder subsequently sends TCP RST/ACK packets.

Separate UDP/53 DNS transactions are also present between `192.168.1.3` and `192.168.1.1`. The reviewed transactions do not establish DNS tunneling.

## 2. Key Technical Findings

| Frame | Observation |
|---|---|
| 2 | DNS PTR query for 192.168.1.1 |
| 4 | PTR response: SpeedTouch.lan |
| 7–8 | DNS query for www.www.com.lan; zero answer records |
| 9–10 | www.www.com resolves to 63.215.91.200 |
| 22 | Windows XP command-shell banner evidence |
| 25 | `dir` command |
| 28, 32 | Directory-listing output |
| 35 | `exit` command |
| 37–38 | TCP RST/ACK packets |

### Important Payload Evidence

- `dir\n`: `64 69 72 0a`
- `exit\n`: `65 78 69 74 0a`

## 3. Network Indicators

| Indicator | Observation |
|---|---|
| Initiator | 192.168.1.3 |
| Initiator Port | 1396 |
| Responder | 192.168.1.2 |
| Responder Port | 53 |
| Protocol | TCP |
| Additional Traffic | UDP/53 DNS |

These are observed network indicators, not independently verified malicious indicators.

## 4. Investigation Methodology

1. Examined PCAP metadata and capture integrity.
2. Reviewed TCP and UDP conversations.
3. Filtered traffic using Wireshark display filters.
4. Reconstructed the TCP conversation using Follow TCP Stream.
5. Examined command and response payloads.
6. Reviewed DNS queries and responses.
7. Identified session termination behavior.
8. Documented findings and evidence references.

## 5. Evidence and Integrity

**SHA-256:**

`8c89c0d2d5b91695a03d05a451897f583a99d2379afac0822af0d8f390163d95`

The original PCAP is intentionally excluded from the public repository.

The public evidence gallery contains selected Wireshark screenshots. The original PCAP and unredacted evidence are retained privately.

## 6. Limitations

The reviewed evidence does not independently establish:

- Attacker identity.
- Whether the communication was authorized.
- Successful compromise.
- Malware execution.
- Data exfiltration.
- DNS tunneling.

Internal IP addresses and DNS responses should not be classified as malicious without independent validation.

## 7. Investigation Recommendations

- Validate whether TCP/53 communication is authorized.
- Review firewall and DNS server policies.
- Correlate the observed endpoints with endpoint and network logs.
- Investigate the originating system if unauthorized activity is suspected.
- Preserve the original PCAP and supporting evidence.

## 8. Repository Files

- [Detailed Investigation Report](reports/Investigation_Report.pdf)
- [Evidence Register](evidence/Evidence_Register.csv)
- [Wireshark Evidence Gallery](evidence/screenshots/)
- [PCAP Validation](docs/PCAP_Validation.txt)

## 9. Portfolio Summary

Performed passive PCAP analysis using Wireshark, reconstructed an interactive Windows command-shell exchange over TCP/53, validated command and response payloads, reviewed DNS transactions, and documented technical findings, network indicators, evidence, and investigation limitations.

## Disclaimer

This is an independent educational investigation conducted for technical development and portfolio demonstration. It is not paid client work and does not represent professional employment.
