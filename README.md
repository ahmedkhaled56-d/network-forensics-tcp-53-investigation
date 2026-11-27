# Project 03 — Network Forensics Case Study

**Title:** Remote Shell Communication Observed over TCP Port 53  
**Case ID:** SOC-NF-003  
**Type:** Independent training / portfolio case study — not paid client work.

## Summary
The supplied 131-packet PCAP contains an interactive Windows command-shell exchange between `192.168.1.3:1396` and `192.168.1.2:53`. The responder sends a Windows XP command prompt banner and directory-listing output. The initiator sends `dir` and later `exit`. The responder then sends TCP RST/ACK.

Separate UDP/53 DNS transactions are present between `192.168.1.3` and `192.168.1.1`. The reviewed transactions do not establish DNS tunneling.

## Main evidence
- Frame 25: `dir\n` (`64 69 72 0a`)
- Frames 28 and 32: directory-listing output
- Frame 35: `exit\n` (`65 78 69 74 0a`)
- Frame 38: TCP RST/ACK from `192.168.1.2:53` to `192.168.1.3:1396`
- Frames 2 and 4: PTR lookup for `192.168.1.1`, response `SpeedTouch.lan`
- Frames 7 and 8: `www.www.com.lan`, zero answer records
- Frames 9 and 10: `www.www.com` resolves to `63.215.91.200`

## Integrity
SHA-256:
`8c89c0d2d5b91695a03d05a451897f583a99d2379afac0822af0d8f390163d95`

## Important limitations
This evidence does not establish attacker identity, authorization status, compromise, data exfiltration, malware, or DNS tunneling. Do not label the internal IPs or DNS answer malicious without independent validation.

## Files
- `Project_03_Network_Forensics_Report.pdf` — detailed report
- `Evidence_Register.csv` — packet/evidence register
- `PCAP_Validation.txt` — integrity and metadata
- Original PCAP is intentionally not bundled for redistribution. Preserve it privately and check the source's reuse terms before publishing or redistributing the sample.
- Conversation screenshots were reviewed, but were not separately uploaded as image files for embedding. Add your original screenshots to a private evidence folder before publication.

## Portfolio wording
"Performed passive PCAP analysis in Wireshark, reconstructed an interactive Windows command-shell exchange over TCP/53, validated command and response payloads, reviewed DNS transactions, and documented findings, indicators, timeline, MITRE mapping, and limitations."
## Investigation Evidence

### Main Report
[Download Network Forensics Report](reports/Investigation_Report.pdf)

### Evidence Files
- [Evidence Register](evidence/Evidence_Register.csv)
- [Wireshark Screenshots](evidence/screenshots/)
- [PCAP Validation](PCAP_Validation.txt)

### Investigation Highlights
- TCP/53 remote shell analysis
- Windows XP command-shell identification
- Directory enumeration
- DNS traffic analysis
- TCP session termination
  
## Investigation Evidence

### Main Report
[Download Network Forensics Report](reports/Investigation_Report.pdf)

### Evidence Files
- [Evidence Register](evidence/Evidence_Register.csv)
- [Wireshark Screenshots](evidence/screenshots/)
- [PCAP Validation](PCAP_Validation.txt)

### Investigation Highlights
- TCP/53 remote shell analysis
- Windows XP command-shell identification
- Directory enumeration
- DNS traffic analysis
- TCP session termination

## Disclaimer
This is an independent training and portfolio case study.
It does not represent paid client work or professional incident-response employment.

