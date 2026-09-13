---
video_id: V5.4
chapter: 5
title: "Network Constraints in Practice: How Latency and Packet Loss Break Scripts"
composition_id: net226-v5-4-network-constraints
duration_target: "5:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [terminal-tc-inject, script-crash-debugger]
objectives:
  - Inject artificial latency and packet loss using Linux `tc` (Traffic Control).
  - Observe how TCP retransmissions and window throttling trigger script timeouts.
  - Implement defensive connection pooling and socket timeouts in Python.
opens_with: cpcc-open
source_section: ch05 §5.7
---

# Video Design: V5.4 Network Constraints in Practice

---

## Scene 1 — The Zero-Latency Fallacy (0:00–1:00)
**Visual:** Terminal runs a Python automation script locally on `localhost`. Execution takes 80 milliseconds.
**Narration:**
> One of the classic fallacies of distributed computing is assuming the network is reliable and latency is zero.
>
> When you test your scripts in a local VM, everything responds in milliseconds. But when your code runs across a congested WAN or satellite link, physical constraints take over. Let's inject real-world network degradation and watch what happens.

---

## Scene 2 — Injecting WAN Latency with Linux `tc` (1:00–2:30)
**Visual:** Executing Linux Traffic Control commands in the terminal:
```bash
developer@devasc:~$ sudo tc qdisc add dev eth0 root netem delay 250ms loss 5%
developer@devasc:~$ ping -c 3 10.10.20.48
64 bytes from 10.10.20.48: icmp_seq=1 ttl=255 time=502 ms
```
Terminal runs naive Python script. Script hangs for 60 seconds and throws `requests.exceptions.ConnectionError: HTTPSConnectionPool: Max retries exceeded`.
**Narration:**
> Using the Linux `tc` netem utility, we inject 250 milliseconds of round-trip latency and 5 percent random packet loss on our interface.
>
> When we run our naive script, disaster strikes. Each TCP handshake requires multiple round trips. With packet loss, TCP enters congestion avoidance, cutting transmission rates in half. The script hangs for a minute before crashing with a ConnectionError.

---

## Scene 3 — Tuning Timeouts and Connection Pooling (2:30–4:15)
**Visual:** VS Code refactors the script to use `requests.Session()` with HTTPAdapter and explicit granular timeouts:
```python
from requests.adapters import HTTPAdapter
from urllib3.util import Retry

session = requests.Session()
retries = Retry(total=3, backoff_factor=1, status_forcelist=[500, 502, 503, 504])
session.mount("https://", HTTPAdapter(max_retries=retries))

# Explicit connect and read timeout (5s connect, 30s read)
response = session.get(url, timeout=(5.0, 30.0))
```
Running script under degraded network conditions. Script survives retransmissions and completes successfully.
**Narration:**
> To survive real-world networks, tune your client:
>
> First, use `requests.Session()` with an HTTPAdapter to reuse established TCP connections rather than initiating a new handshake for every call.
>
> Second, provide an explicit tuple for timeouts: `timeout=(5.0, 30.0)`. Five seconds to establish the socket, and thirty seconds to read data.
>
> Third, configure automatic urllib3 retries with backoff factors. Now your automation survives network hiccups without crashing.

---

## Scene 4 — Project Checkpoint Guidance (4:15–5:00)
**Visual:** Reviewing the Week 5 Network Dependency and Failure-Mode deliverable rubric.
**Narration:**
> For your Week 5 project checkpoint, document your automation service's network dependencies and explain how your code handles latency and packet loss.
>
> In Chapter 6, we will package our tested scripts into Docker containers and automate validation with CI/CD.
