# Wireshark Evidence Gallery

This folder contains selected Wireshark screenshots supplied during the investigation of `dns-remoteshell.pcap`.

## Evidence index

| File | What it documents |
|---|---|
| `01-pcap-metadata-redacted.png` | Capture metadata, packet count, duration, and SHA-256. The local Windows file path has been redacted. |
| `02-tcp-conversations.png` | Wireshark Conversations view showing the observed endpoint conversations. |
| `03-tcp-handshake.png` | TCP SYN/SYN-ACK handshake-related packets for the shell conversation. |
| `04-windows-xp-shell-banner-frame22.png` | Packet payload associated with the Windows XP command-shell banner. |
| `05-follow-tcp-stream-windows-shell.png` | Follow TCP Stream view showing the Windows command prompt, `dir`, directory output, and `exit`. |
| `06-dir-command-frame25.png` | Frame 25 payload bytes for the `dir` command. |
| `07-directory-listing-response-frame32.png` | Server-to-client directory-listing response payload. |
| `08-tcp-and-dns-traffic-overview.png` | Combined view of TCP/53 and UDP/53 traffic in the capture. |
| `09-dns-ptr-query-frame2.png` | DNS PTR query for `1.1.168.192.in-addr.arpa`. |
| `10-dns-ptr-response-frame4.png` | PTR response identifying `SpeedTouch.lan`. |
| `11-dns-a-response-no-answer-frame8.png` | DNS A response for `www.www.com.lan` with zero answer records. |
| `12-dns-a-query-frame9.png` | DNS A query for `www.www.com`. |
| `13-exit-command-frame35.png` | Frame 35 payload bytes `65 78 69 74 0a` (`exit` followed by line feed). |
| `14-tcp-reset-frames37-38.png` | TCP RST/ACK packets observed at Frames 37 and 38. |

## Privacy and handling

- The local Windows path visible in the original PCAP properties screenshot was redacted in the public copy.
- The original PCAP is intentionally not included.
- These are screenshots of packet-analysis evidence, not proof by themselves of attacker identity, authorization status, compromise, or data exfiltration.
- Keep the original unredacted screenshots and original PCAP privately.
