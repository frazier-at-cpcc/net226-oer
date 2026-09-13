---
video_id: V8.2
chapter: 8
title: "NETCONF in Action: Executing XML RPCs with Python and ncclient"
composition_id: net226-v8-2-netconf-ncclient
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [ncclient-editor, xml-filter-highlighter]
objectives:
  - Connect to Cisco IOS-XE devices using NETCONF over SSH port 830.
  - Formulate XML subtree filters to retrieve specific interface configurations.
  - Execute atomic configuration changes using `<edit-config>`.
opens_with: cpcc-open
source_section: ch08 §8.3
---

# Video Design: V8.2 NETCONF with ncclient

---

## Scene 1 — What is NETCONF? (0:00–1:15)
**Visual:** Protocol diagram illustrating SSH port 830, Remote Procedure Calls (`<rpc>`), and XML payloads conforming to YANG schemas.
**Narration:**
> NETCONF is an IETF standard protocol designed to replace command-line configuration management.
>
> It operates over SSH on standard TCP port 830. Everything in NETCONF is an explicit Remote Procedure Call, or RPC, exchanging XML payloads that conform to YANG models.
>
> In Python, we use the `ncclient` library to automate NETCONF transactions.

---

## Scene 2 — Establishing the Session & The Hello Exchange (1:15–2:30)
**Visual:** VS Code opens `netconf_demo.py`. Live typing:
```python
from ncclient import manager

router = {
    "host": "10.10.20.48",
    "port": 830,
    "username": "developer",
    "password": "CiscoPassword123!",
    "hostkey_verify": False
}

with manager.connect(**router) as m:
    print(f"Connected! Session ID: {m.session_id}")
    for cap in m.server_capabilities:
        if "ietf-interfaces" in cap:
            print(f"Server supports: {cap}")
```
Terminal runs script: prints `Connected! Session ID: 42` and supported YANG capabilities.
**Narration:**
> When `manager.connect()` establishes an SSH connection on port 830, both devices exchange a `<hello>` message.
>
> This capabilities exchange tells your script exactly which YANG models the router supports.

---

## Scene 3 — Subtree Filtering with `<get-config>` (2:30–4:15)
**Visual:** Constructing an XML subtree filter:
```python
filter_xml = """
<filter xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <interfaces xmlns="urn:ietf:params:xml:ns:yang:ietf-interfaces">
    <interface>
      <name>GigabitEthernet1</name>
    </interface>
  </interfaces>
</filter>
"""
reply = m.get_config(source="running", filter=filter_xml)
print(reply.xml)
```
Terminal outputs lean XML showing only GigabitEthernet1 configuration.
**Narration:**
> Never dump 5,000 lines of configuration. With NETCONF, use a subtree filter.
>
> We define a small XML snippet specifying that we only want data inside the `interfaces` container for `GigabitEthernet1`.
>
> The router parses our filter against its YANG model and returns precisely the requested XML subtree.

---

## Scene 4 — Modifying State with `<edit-config>` (4:15–6:00)
**Visual:** Executing an edit-config to update interface description:
```python
config_xml = """
<config xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <interfaces xmlns="urn:ietf:params:xml:ns:yang:ietf-interfaces">
    <interface>
      <name>GigabitEthernet1</name>
      <description>Automated by NET-226 Capstone</description>
    </interface>
  </interfaces>
</config>
"""
m.edit_config(target="running", config=config_xml)
```
Terminal runs script and receives `<rpc-reply><ok/></rpc-reply>`.
**Narration:**
> To change configuration, we call `m.edit_config()` targeting the running datastore.
>
> The router validates the change against its YANG schema. If valid, it applies the change atomically and returns `<ok/>`.
>
> In our next video, we will explore RESTCONF: managing YANG data over HTTPS.
