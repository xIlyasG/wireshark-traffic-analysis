# Network Traffic Analysis with Wireshark

## Overview

This beginner cybersecurity project explores how Domain Name System (DNS) traffic works. Wireshark was used to capture network packets, filter DNS traffic, and inspect DNS responses.

## Objectives

- Capture network traffic on a Wi-Fi interface.
- Generate a DNS lookup using PowerShell.
- Filter packets using Wireshark's `dns` display filter.
- Inspect DNS response records and understand source and destination IP addresses.
- Document findings and retain screenshots as evidence.

## Tools and Environment

- Windows 10
- Wireshark 4.6.9
- PowerShell
- `nslookup`

## Methodology

1. Started a capture on the Wi-Fi interface in Wireshark.
2. Executed `nslookup tryhackme.com` in PowerShell.
3. Stopped the capture.
4. Applied the `dns` display filter.
5. Inspected the response for `tryhackme.com`.
6. Recorded the observed DNS answer records and packet endpoints.

## Key Findings

The captured DNS response for `tryhackme.com` contained these IPv4 A records:

- `64.239.123.129`
- `64.239.109.129`

The response packet showed:

- **Source IP:** `192.168.1.1`
- **Destination IP:** `10.121.10.25`
- **Displayed TTL:** 50 seconds

An A record maps a domain name to an IPv4 address. The TTL indicates how long the record may remain cached, according to its remaining lifetime.

## Evidence

See the `screenshots/` directory:

- `dns_filter.png` — filtered DNS packets.
- `dns_answers.png` — DNS answer records for `tryhackme.com`.

## Skills Practiced

- Basic packet capture and analysis.
- DNS troubleshooting fundamentals.
- IPv4 source and destination identification.
- Wireshark display filters.
- PowerShell file and directory management.
- Technical documentation.

## Security Note

Packet captures may contain sensitive network information. The raw `.pcapng` capture is retained locally and should be reviewed before any public sharing. This repository should contain sanitized screenshots and documentation, not the raw capture.

## Project Status

Initial DNS capture and analysis completed. Further analysis may be added in future iterations.
