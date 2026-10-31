# Network Traffic Analysis — Findings

## 1. Objective

Capture and analyze DNS traffic with Wireshark to understand how domain names are resolved to IP addresses.

## 2. Environment

- Operating system: Windows 10
- Packet analyzer: Wireshark 4.6.9
- Command-line tool: PowerShell
- Test domain: `tryhackme.com`
- Network interface: Wi-Fi

## 3. Methodology

1. Started a packet capture on the Wi-Fi interface in Wireshark.
2. Ran `nslookup tryhackme.com` in PowerShell.
3. Stopped the capture.
4. Applied the Wireshark display filter `dns`.
5. Inspected the DNS response and expanded the Answers section.

## 4. Findings

The DNS response for `tryhackme.com` contained two IPv4 A records:

- `64.239.123.129`
- `64.239.109.129`

The response packet showed:

- Source IP: `192.168.1.1`
- Destination IP: `10.121.10.25`
- DNS response TTL: 50 seconds

The source IP is the DNS server shown in the captured response. The destination IP is the laptop's Wi-Fi IPv4 address.

An A record maps a domain name to an IPv4 address. The TTL indicates how long the DNS record may be cached, subject to the remaining TTL value in the response.

## 5. What I Learned

- DNS translates domain names into IP address records.
- DNS queries and responses travel between a client and a DNS resolver.
- Source and destination IP addresses help identify the endpoints in a packet exchange.
- Wireshark display filters help isolate relevant traffic without deleting other captured packets.
- Packet details can reveal DNS questions, answers, record types, and TTL values.

## 6. Evidence

- `screenshots/dns_filter.png` — DNS packets displayed using the `dns` filter.
- `screenshots/dns_answers.png` — DNS answer records for `tryhackme.com`.

## 7. Security Considerations

Packet captures may contain sensitive information about network activity. Review captures before sharing them. The raw `.pcapng` file is retained locally and should not be published in a public repository without a careful privacy review.
