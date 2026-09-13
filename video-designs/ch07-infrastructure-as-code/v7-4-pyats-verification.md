---
video_id: V7.4
chapter: 7
title: "Automated State Verification: Snapshot Testing and Diffs with pyATS and Genie"
composition_id: net226-v7-4-pyats-verification
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [pyats-cli-walkthrough, genie-diff-viewer]
objectives:
  - Explain why CLI regex screen-scraping fails in enterprise test harnesses.
  - Parse operational Cisco show commands into structured JSON using Genie.
  - Execute pre/post snapshot diffs to verify routing and interface health automatically.
opens_with: cpcc-open
source_section: ch07 §7.6
---

# Video Design: V7.4 Automated State Verification with pyATS

---

## Scene 1 — Why Screen-Scraping Fails (0:00–1:15)
**Visual:** Terminal showing a brittle Python regex attempting to parse `show ip route`. When a firmware update changes output spacing by two spaces, the regex fails to match.
**Narration:**
> Network engineers have spent decades writing brittle regular expressions to parse `show ip route` and `show interfaces`.
>
> But the moment Cisco updates the firmware and changes a single column width, your regex breaks.
>
> Cisco pyATS and Genie solve this by treating device operational state as structured data.

---

## Scene 2 — Genie Parsing in Action (1:15–3:00)
**Visual:** Running Genie parser from the terminal:
```bash
developer@devasc:~$ pyats parse "show ip interface brief" --testbed-file testbed.yml --devices csr1
{
  "interface": {
    "GigabitEthernet1": {
      "ip_address": "10.10.20.48",
      "status": "up",
      "protocol": "up"
    },
    "GigabitEthernet2": {
      "ip_address": "10.100.1.1",
      "status": "up",
      "protocol": "up"
    }
  }
}
```
**Narration:**
> Look at what Genie does: you execute a standard CLI command, and Genie converts the raw text into clean, structured JSON dictionaries.
>
> You can now access `interface["GigabitEthernet1"]["status"]` directly in Python without writing a single line of regular expressions.

---

## Scene 3 — Automated Snapshot Diffs (3:00–4:30)
**Visual:** Taking snapshots before and after a change:
```bash
pyats learn routing --testbed-file testbed.yml --output pre_change
# (Automation change deploys new route)
pyats learn routing --testbed-file testbed.yml --output post_change
pyats diff pre_change post_change
```
Terminal displays colored diff:
`+ route 192.168.100.0/24 next-hop 10.10.20.1`
**Block:** `genie-diff-viewer`
**Narration:**
> Here is the ultimate automated change verification workflow:
>
> Step one: take a pre-change snapshot of routing state using `pyats learn routing`.
>
> Step two: execute your Ansible automation playbook.
>
> Step three: take a post-change snapshot.
>
> Step four: run `pyats diff`. Genie mathematically compares the two snapshots and highlights exactly what changed: new routes added in green, unexpected drops in red. Zero human guesswork.

---

## Scene 4 — Takeaway (4:30–5:30)
**Visual:** Summary card linking pyATS verification to enterprise change tickets.
**Narration:**
> Incorporating pyATS snapshots into your CI/CD pipeline guarantees that unexpected routing drops are caught before tickets close.
>
> In Chapter 8, we reach the capstone of our course: Model-Driven Programmability with YANG, NETCONF, and RESTCONF.
