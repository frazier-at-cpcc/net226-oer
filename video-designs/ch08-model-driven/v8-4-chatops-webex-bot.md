---
video_id: V8.4
chapter: 8
title: "ChatOps and Controller APIs: Building a Webex Bot for Network Alerting"
composition_id: net226-v8-4-chatops-webex-bot
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [webex-portal-tour, bot-code-editor, live-chatops-alert]
objectives:
  - Register a Bot Account on `developer.webex.com` and capture access tokens securely.
  - Post formatted Markdown and Adaptive Cards to Webex spaces via REST APIs.
  - Complete the requirements for the Individual Skills Assessment and Capstone Demonstration.
opens_with: cpcc-open
source_section: ch08 §8.5 & 8.6
---

# Video Design: V8.4 ChatOps with Webex Teams Bots

---

## Scene 1 — The Power of ChatOps (0:00–1:15)
**Visual:** A modern network operations team collaborating in a Webex room. An automated bot posts a card: "CRITICAL: Interface GigabitEthernet2 down on rtr-core-01", complete with before/after state diff and interactive acknowledge button.
**Narration:**
> Sending automated emails during an outage is slow and easily buried in inboxes.
>
> ChatOps brings people, tools, and infrastructure events into a transparent, shared chat channel.
>
> In this video, we build a Cisco Webex bot that alerts network operations teams automatically when interface state changes.

---

## Scene 2 — Registering the Bot (1:15–2:30)
**Visual:** Screen recording of `developer.webex.com`. Clicking 'Start Building' -> 'Create a Bot'.
Entering Bot Name (`Campus-A NetOps Bot`), username, and avatar.
Copying the Bot Access Token. Storing it in an environment variable `WEBEX_TEAMS_TOKEN`.
**Block:** `webex-portal-tour`
**Narration:**
> Navigate to `developer.webex.com` and create a Bot.
>
> Webex provides you with a permanent Bot Access Token. Store this token securely in your environment variables.
>
> Add your bot to an operations space using its email address. The bot is now authorized to post messages.

---

## Scene 3 — Posting Alert Cards via Python (2:30–4:15)
**Visual:** VS Code opens `webex_alert.py`:
```python
import os
import requests

WEBEX_TOKEN = os.environ.get("WEBEX_TEAMS_TOKEN")
ROOM_ID = os.environ.get("WEBEX_ROOM_ID")

headers = {
    "Authorization": f"Bearer {WEBEX_TOKEN}",
    "Content-Type": "application/json"
}

markdown_alert = """
### 🚨 Network Audit Alert: Interface State Change
* **Device:** `rtr-core-01 (10.10.20.48)`
* **Interface:** `GigabitEthernet2`
* **Status:** `DOWN`
* **Action:** Automated verification failed. Rollback initiated.
"""

payload = {
    "roomId": ROOM_ID,
    "markdown": markdown_alert
}

resp = requests.post("https://webexapis.com/v1/messages", headers=headers, json=payload)
print(f"Message sent! ID: {resp.json().get('id')}")
```
Terminal runs script. Webex desktop app immediately dings, and the rich alert card appears in the room.
**Block:** `live-chatops-alert`
**Narration:**
> Look at how clean this API is. We formulate an HTTP `POST` request to `https://webexapis.com/v1/messages`.
>
> We supply our room ID and a rich Markdown payload detailing the device name, interface, and status.
>
> When our script runs, the message lands in the operations channel in milliseconds.

---

## Scene 4 — Capstone Demonstration Guidance (4:15–5:30)
**Visual:** Reviewing the Capstone Demonstration Packet rubric: Git history, CI/CD pipeline, Docker container, idempotent Ansible change, and Webex alert.
**Narration:**
> This Webex bot forms the final piece of your Individual Skills Assessment and Capstone Demonstration.
>
> You have mastered the entire network programmability toolchain: from Python and Linux to REST APIs, Docker, CI/CD, Ansible, YANG, and ChatOps.
>
> Congratulations on completing the course material for NET-226. Head to Section 8.7 to package your final capstone demonstration!
