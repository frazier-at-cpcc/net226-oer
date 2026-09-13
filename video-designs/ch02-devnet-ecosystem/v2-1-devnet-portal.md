---
video_id: V2.1
chapter: 2
title: "Navigating Cisco DevNet: Learning Labs, Code Exchange, and API Docs"
composition_id: net226-v2-1-devnet-portal
duration_target: "4:30"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss, lucide-icons]
blocks: [cpcc-open, devnet-portal-quadrant, browser-interactive-frame, callout-box]
objectives:
  - Identify the four foundational pillars of the Cisco DevNet portal.
  - Locate official REST API specifications and data models for Catalyst Center and Meraki.
  - Search and vet community automation scripts on Cisco DevNet Code Exchange.
opens_with: cpcc-open
source_section: ch02 §2.2
---

# Video Design: V2.1 Navigating Cisco DevNet

---

## Scene 0 — CPCC Open (0:00–0:02.5)
Central Piedmont Open with chapter and video title.

---

## Scene 1 — The Developer Portal Hub (0:02.5–1:15)
**Visual:** Smooth zoom-in on `developer.cisco.com`. The homepage layout is simplified into a clean 3D isometric representation. Four quadrants light up sequentially: Learning Labs, Sandboxes, Code Exchange, and Community.
**Block:** `devnet-portal-quadrant`
**Narration:**
> In chapter one, you configured your local workstation. But where do you find authoritative documentation, code examples, and practice hardware?
>
> The answer is Cisco DevNet: Cisco's official developer program. Whether you are automating enterprise campus networks, data centers, or collaboration systems, DevNet is your starting point.
>
> It is organized around four core pillars: Learning Labs for self-paced skill building, Sandboxes for free cloud-hosted practice environments, Code Exchange for verified open-source automation scripts, and Community for developer support.

---

## Scene 2 — Finding Authoritative API Documentation (1:15–2:30)
**Visual:** Browser frame navigates through the API Documentation directory. Clicks into 'Cisco Catalyst Center (DNA Center) Intent API'. Shows the interactive documentation layout: endpoints grouped by tag (`Devices`, `Site Management`), required HTTP methods, query parameters, request headers, and expandable JSON response models.
**Block:** `browser-interactive-frame`
**Narration:**
> Let's look at the API documentation. When you search for Cisco APIs, avoid third-party tutorials that may be years out of date.
>
> In the official DevNet API reference, every endpoint is documented with its exact HTTP method, base path, required authentication headers, and JSON response schema.
>
> Notice how each endpoint displays its API version lifecycle. When an endpoint is superseded, Cisco marks it with a clear deprecation banner and links you directly to the modern alternative.

---

## Scene 3 — DevNet Code Exchange (2:30–3:45)
**Visual:** Browser navigates to DevNet Code Exchange (`developer.cisco.com/codeexchange`). Search bar types `meraki python vlan`. A curated card appears: verified badge, GitHub stars, MIT license, author listed as Cisco Systems.
**Block:** `code-exchange-card-anim`
**Narration:**
> Don't reinvent the wheel. Before writing an automation tool from scratch, check DevNet Code Exchange.
>
> Code Exchange is a curated directory of open-source automation repositories. Cisco engineers test and review these repositories before they're published.
>
> Look for the 'Cisco Verified' badge. Inspect the repository's README, verify its license, and check recent commit dates to ensure the project is actively maintained.

---

## Scene 4 — Takeaway & Action (3:45–4:30)
**Visual:** Clean summary graphic with actionable links for students to register a free DevNet account.
**Narration:**
> Registering for Cisco DevNet is completely free. If you haven't already, sign up today using your student email. In our next video, we'll dive into DevNet Sandboxes: how to reserve dedicated hardware and connect securely via VPN.
