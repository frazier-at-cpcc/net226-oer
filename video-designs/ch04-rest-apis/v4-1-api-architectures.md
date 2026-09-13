---
video_id: V4.1
chapter: 4
title: "REST vs. RPC vs. Webhooks: Choosing the Right API Architecture"
composition_id: net226-v4-1-api-architectures
duration_target: "4:30"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss, lucide-icons]
blocks: [cpcc-open, api-style-comparison, webhook-push-anim]
objectives:
  - Compare REST, RPC, and Webhook architectural communication models.
  - Explain Roy Fielding's REST constraints (statelessness, resource URIs).
  - Contrast request-response polling with event-driven webhook notifications.
opens_with: cpcc-open
source_section: ch04 §4.2
---

# Video Design: V4.1 API Architectures

---

## Scene 1 — The World Beyond the Web Page (0:00–1:00)
**Visual:** An animated web browser sends an HTTP request and receives an HTML web page rendered for human reading. Beside it, an automated network script sends an HTTP request and receives a lean, machine-readable JSON payload.
**Narration:**
> When you use a web browser, servers send you HTML, CSS, and images formatted for human eyeballs.
>
> But when network devices and automation scripts communicate, they don't need formatting—they need pure data.
>
> Application Programming Interfaces, or APIs, are the contracts that allow programs to talk to programs. But not all APIs operate the same way.

---

## Scene 2 — The REST Architectural Pattern (1:00–2:15)
**Visual:** 3D animated cards illustrate REST constraints:
- **Resources as Nouns:** `/api/v1/devices`, `/api/v1/networks/12/vlans`
- **Standard HTTP Verbs:** GET, POST, PUT, PATCH, DELETE
- **Statelessness:** Server stores zero client session context; each request contains full authentication.
**Block:** `api-style-comparison`
**Narration:**
> The dominant architectural style across modern networking is REST: Representational State Transfer.
>
> In a REST API, everything is modeled as a **resource** identified by a clean URL noun. You don't have endpoints called `/getAllSwitches` or `/deletePort`.
>
> Instead, you use standard HTTP verbs against resource nouns: `GET /devices` to read, `POST /devices` to create, and `DELETE /devices/101` to remove. REST is strictly stateless: every single request must carry its own authentication credentials.

---

## Scene 3 — The Inverted Power of Webhooks (2:15–3:30)
**Visual:** Animated comparison:
Top: Continuous Polling. Script asks router every 5 seconds: "Is link down? Is link down? Is link down?" (Wasted bandwidth, server load).
Bottom: Event-Driven Webhook. Router detects link down event, immediately fires an HTTP POST containing event JSON directly to the automation listener.
**Block:** `webhook-push-anim`
**Narration:**
> Traditional monitoring uses polling: your script asks the controller every ten seconds if anything changed. Ninety-nine percent of the time, the answer is no, wasting bandwidth and compute.
>
> Webhooks invert that relationship. Instead of polling, you register a listener URL. When a network link drops or a rogue AP is detected, the controller immediately fires an HTTP POST containing the event details directly to your server. Fast, lightweight, and event-driven.

---

## Scene 4 — Architecture Selection Guide (3:30–4:30)
**Visual:** Summary decision chart matching network tasks to API styles.
**Narration:**
> Use REST for standard device provisioning and inventory audits. Use Webhooks for real-time alerting and incident response.
>
> In our next video, we will dissect the exact anatomy of an HTTP transaction.
