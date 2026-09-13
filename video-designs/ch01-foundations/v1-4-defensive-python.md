---
video_id: V1.4
chapter: 1
title: "Writing Defensive Python: Control Flow, Collections, Error Handling"
composition_id: net226-v1-4-defensive-python
duration_target: "5:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [editor-live-typing, exception-highlighter]
objectives:
  - Model network inventories using Python dictionaries and lists.
  - Implement defensive exception handling with `try...except` to prevent automation crashes.
  - Structure modular functions with type annotations and validation.
opens_with: cpcc-open
source_section: ch01 §1.5
---

# Video Design: V1.4 Writing Defensive Python

---

## Scene 1 — The Fragile Script (0:00–1:00)
**Visual:** Live typing in VS Code. A fragile script that attempts to extract an IP address from a raw dictionary:
```python
device = {"hostname": "rtr-campus-01", "platform": "cisco_ios"}
ip = device["ip_address"]  # Raises KeyError!
```
Running script produces a traceback: `KeyError: 'ip_address'`. Script terminates.
**Narration:**
> In software development, writing code that works when everything is perfect is easy. In network engineering, things are rarely perfect. Devices reboot, interfaces drop, and API responses return unexpected schemas.
>
> Notice what happened here: our script assumed every device dictionary contained an `ip_address` key. When the key was missing, Python threw an unhandled KeyError and crashed the entire workflow. Let's make this code resilient.

---

## Scene 2 — Safe Dictionary Extraction (1:00–2:15)
**Visual:** Refactoring to use `.get()` and defensive dictionary patterns:
```python
# Safe extraction with fallback default
ip = device.get("ip_address", "UNCONFIGURED")
print(f"Device {device.get('hostname')} IP: {ip}")
```
Running script outputs: `Device rtr-campus-01 IP: UNCONFIGURED`.
**Narration:**
> Instead of using square brackets, use the `.get()` method. `.get()` allows you to provide a sensible fallback default when a key is absent, allowing your automation to log the discrepancy and keep running.

---

## Scene 3 — Defensive Try-Except Blocks (2:15–3:45)
**Visual:** Writing a complete defensive connection function:
```python
import ipaddress

def validate_device(device_info: dict) -> dict:
    hostname = device_info.get("hostname", "unknown-host")
    raw_ip = device_info.get("ip")
    
    if not raw_ip:
        return {"host": hostname, "status": "FAIL", "reason": "Missing IP"}
    
    try:
        validated_ip = ipaddress.IPv4Address(raw_ip)
        return {"host": hostname, "status": "PASS", "ip": str(validated_ip)}
    except ValueError as err:
        return {"host": hostname, "status": "FAIL", "reason": f"Invalid IPv4: {err}"}
```
**Narration:**
> When validating IP addresses or making network connections, wrap the operation in an explicit `try...except` block.
>
> We pass the raw IP to Python's built-in `ipaddress` module. If the string contains an invalid address—like `192.168.1.999`—the `ValueError` is caught, a structured failure dictionary is returned, and execution continues smoothly. Never use a bare `except:`; catch the specific exceptions you anticipate.

---

## Scene 4 — Structuring for the Project (3:45–5:00)
**Visual:** Calling the function against a list of 3 test devices: one valid, one missing IP, one malformed IP. Terminal displays clean structured output.
**Narration:**
> When you test this function against a list of devices, every item is audited without a single crash.
>
> This defensive programming structure will form the core of your Network Change Automation project in upcoming weeks. Head over to Section 1.6 to begin your NETLAB+ workstation validation lab!
