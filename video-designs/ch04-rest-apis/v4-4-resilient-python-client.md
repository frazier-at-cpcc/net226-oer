---
video_id: V4.4
chapter: 4
title: "Building Resilient Python API Clients: Auth, Pagination, Backoff"
composition_id: net226-v4-4-resilient-python-client
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [editor-live-typing, backoff-timeline]
objectives:
  - Construct authenticated Python API clients using the `requests` library.
  - Ingest credentials safely from environment variables.
  - Implement exponential backoff to handle HTTP 429 rate limits gracefully.
opens_with: cpcc-open
source_section: ch04 §4.6
---

# Video Design: V4.4 Building Resilient Python API Clients

---

## Scene 1 — The Anatomy of a Production Client (0:00–1:15)
**Visual:** VS Code opens `meraki_client.py`. Live typing setup:
```python
import os
import time
import requests

API_KEY = os.environ.get("MERAKI_DASHBOARD_API_KEY")
if not API_KEY:
    raise ValueError("Missing MERAKI_DASHBOARD_API_KEY environment variable")

BASE_URL = "https://api.meraki.com/api/v1"
HEADERS = {
    "X-Cisco-Meraki-API-Key": API_KEY,
    "Accept": "application/json",
    "Content-Type": "application/json"
}
```
**Narration:**
> In this video, we will translate our Postman requests into a production-grade Python client using the `requests` library.
>
> Notice line five: we load the API key from `os.environ`. If the variable is missing, we raise an explicit ValueError immediately, preventing unauthenticated calls.
>
> We establish our base URL and define reusable request headers.

---

## Scene 2 — Handling HTTP 429 & Exponential Backoff (1:15–3:30)
**Visual:** Typing the resilient request loop:
```python
def fetch_devices(network_id: str, retries: int = 3) -> list:
    url = f"{BASE_URL}/networks/{network_id}/devices"
    for attempt in range(retries):
        try:
            resp = requests.get(url, headers=HEADERS, timeout=10)
            if resp.status_code == 200:
                return resp.json()
            elif resp.status_code == 429:
                wait = int(resp.headers.get("Retry-After", 2 ** attempt))
                print(f"Rate limited (429). Retrying in {wait}s...")
                time.sleep(wait)
                continue
            resp.raise_for_status()
        except requests.exceptions.RequestException as err:
            if attempt == retries - 1:
                raise RuntimeError(f"API request failed: {err}") from err
            time.sleep(2 ** attempt)
    return []
```
**Narration:**
> Cloud controllers enforce strict rate limits. If your script queries 100 switches too quickly, the server returns HTTP 429: Too Many Requests.
>
> A naive script crashes immediately. Our resilient client inspects the response. If it sees status 429, it checks the `Retry-After` header to see how long the server wants us to wait, pauses execution with `time.sleep()`, and retries automatically.
>
> We implement exponential backoff: doubling our wait time on successive attempts to protect the controller.

---

## Scene 3 — Testing Against Live Mock (3:30–5:30)
**Visual:** Running the script in terminal:
```bash
developer@devasc:~/workspace$ python3 meraki_client.py
Fetched 14 network devices successfully.
First device: Meraki MS220-8P Switch (Serial: Q2XX-XXXX-XXXX)
```
Reviewing Milestone 3 expectations.
**Narration:**
> We run our client, and within 400 milliseconds, fourteen network devices are parsed into clean Python dictionaries.
>
> For Project Milestone 3 due this week, you will author your own API client module with secure credential ingestion and error handling. Head to Section 4.7 to begin!
