# threat-ledger

First-party threat intelligence from an SSH honeypot: IP addresses that repeatedly hit the honeypot,
passively enriched and scored — refreshed automatically every 15 minutes.

## Contents

| File | What it is |
|------|-----------|
| `ssh-blocklist.txt` | Source IPs with more than 3 login attempts — drop-in for a firewall URL table |
| `reputation.json` / `reputation.csv` | Per-IP enrichment: ASN, country, org, forward-confirmed rDNS, hosting/cloud classification, a 0–100 reputation score, and activity **counts** (login attempts, credentials attempted, commands run) |
| `REPUTATION.md` | Human-readable summary (top source countries + networks) |

## Method

- **Passive only** — sources are observed hitting the honeypot; **no IP is ever scanned or probed back.**
- Enrichment uses public data (rDNS/FCrDNS, DNSBL-over-DNS, ip-api, Team Cymru whois).
- Raw session forensics (attacker commands and credentials) are retained privately and are **not**
  published — only aggregate counts appear here.

## Use

Firewall URL-table / blocklist feed:

```
https://raw.githubusercontent.com/AndrewGoloida/threat-ledger/main/ssh-blocklist.txt
```

_All data derives from unsolicited traffic to a honeypot. No warranty — verify before blocking in production._
