---
video_id: V8.3
chapter: 8
title: "RESTCONF in Practice: Managing IOS-XE Devices with HTTP and JSON"
composition_id: net226-v8-3-restconf-practice
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [restconf-postman-ui, python-restconf-code]
objectives:
  - Deconstruct RESTCONF URI structures (RFC 8040).
  - Use `application/yang-data+json` media types to query and update IOS XE devices.
  - Construct authenticated Python scripts managing interfaces via RESTCONF.
opens_with: cpcc-open
source_section: ch08 §8.4
---

# Video Design: V8.3 RESTCONF in Practice

---

## Scene 1 — Why RESTCONF? (0:00–1:15)
**Visual:** Side-by-side comparison: NETCONF (SSH, Port 830, XML) vs. RESTCONF (HTTPS, Port 443, JSON).
**Narration:**
> NETCONF is powerful, but many web developers and automation tools prefer REST APIs and JSON payloads over SSH and XML.
>
> RESTCONF (RFC 8040) gives you the best of both worlds: it maps standardized YANG data models directly to standard HTTP operations over port 443.

---

## Scene 2 — Deconstructing the RESTCONF URI (1:15–2:45)
**Visual:** Dissection of a RESTCONF URI:
`https://10.10.20.48/restconf/data/ietf-interfaces:interfaces/interface=GigabitEthernet1`
Breakdown:
- Root: `/restconf/`
- Datastore: `/data/`
- Module Prefix: `ietf-interfaces:`
- Container: `interfaces/`
- List Key: `interface=GigabitEthernet1`
**Narration:**
> Look at the structure of a RESTCONF URL:
>
> It begins with `/restconf/data/`.
>
> Next comes the YANG module name and container: `ietf-interfaces:interfaces`.
>
> And when addressing a specific list entry, the key is appended: `interface=GigabitEthernet1`.
>
> The HTTP headers are critical: you must specify `Accept: application/yang-data+json`.

---

## Scene 3 — RESTCONF in Python (2:45–4:30)
**Visual:** VS Code opens `restconf_client.py`:
```python
import requests

url = "https://10.10.20.48/restconf/data/ietf-interfaces:interfaces/interface=GigabitEthernet1"
headers = {
    "Accept": "application/yang-data+json",
    "Content-Type": "application/yang-data+json"
}
auth = ("developer", "CiscoPassword123!")

# Read interface configuration
resp = requests.get(url, headers=headers, auth=auth, verify=False)
print(resp.json())

# Update description with PATCH
payload = {
    "ietf-interfaces:interface": {
        "description": "Updated via RESTCONF"
    }
}
patch_resp = requests.patch(url, headers=headers, json=payload, auth=auth, verify=False)
print(f"Status Code: {patch_resp.status_code}")  # 204 No Content
```
Terminal runs script: prints clean JSON interface data, followed by status 204.
**Narration:**
> In Python, interacting with RESTCONF is as simple as using `requests.get()` and `requests.patch()`.
>
> We query the interface, receive clean JSON conforming to the YANG model, and submit a `PATCH` request to update the description.
>
> The router returns HTTP 204 No Content, confirming the change was applied successfully.

---

## Scene 4 — Wrap-Up (4:30–5:30)
**Visual:** Summary takeaway card comparing when to use NETCONF vs RESTCONF.
**Narration:**
> In our final video, we will integrate ChatOps: connecting device alerts to a Cisco Webex Teams bot for our capstone demonstration!
