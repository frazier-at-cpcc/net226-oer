---
video_id: V2.2
chapter: 2
title: "Sandboxes Demystified: Always-On vs. Reservable VPN Topologies"
composition_id: net226-v2-2-sandboxes-demystified
duration_target: "5:00"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, threejs, tailwindcss]
blocks: [cpcc-open, 3d-topology-anim, comparison-matrix-card]
objectives:
  - Contrast Always-On and Reservable DevNet sandboxes.
  - Explain the AnyConnect VPN connection workflow to private sandbox pods.
  - Choose the appropriate sandbox type based on automation tasks.
opens_with: cpcc-open
source_section: ch02 §2.3
---

# Video Design: V2.2 Sandboxes Demystified

---

## Scene 1 — The Problem of Production Testing (0:00–1:00)
**Visual:** An animated server rack with flashing warning LEDs. A developer pushes code and an alert pops up: "502 Gateway Error: BGP adjacency dropped".
**Narration:**
> In software development, you never test new code directly on the production database. The same rule applies to network engineering: you never run untested automation scripts against production core switches.
>
> But physical enterprise hardware is expensive. How do you practice without breaking the live network? DevNet Sandboxes solve this by providing free, cloud-hosted lab environments.

---

## Scene 2 — Always-On: The Instant Sandbox (1:00–2:15)
**Visual:** 3D cloud globe showing public HTTPS endpoints accessible globally. An icon of a developer laptop sends GET requests directly to `sandboxdnac.cisco.com`.
**Block:** `3d-topology-anim`
**Narration:**
> DevNet provides two distinct sandbox types. The first is the **Always-On Sandbox**.
>
> Always-On sandboxes are multi-tenant environments available 24 hours a day, seven days a week, with zero scheduling required.
>
> They are accessible over the public internet via HTTPS. They are ideal for quick REST API queries: retrieving device inventories, testing authentication headers, or exploring API structure. However, because they are shared by thousands of developers, write operations are restricted or automatically scrubbed.

---

## Scene 3 — Reservable Sandboxes & VPN Topologies (2:15–3:45)
**Visual:** A dedicated virtual pod animates into view. An encrypted VPN tunnel (AnyConnect) extends from the laptop across the internet into the private subnet `10.10.20.0/24`. We see a Cisco CSR1000v virtual router at `10.10.20.48`.
**Block:** `vpn-tunnel-topology`
**Narration:**
> When you need to test configuration changes—like pushing new VLANs, deploying Ansible playbooks, or modifying NETCONF interfaces—you need a **Reservable Sandbox**.
>
> A reservable sandbox is a private, dedicated virtual network pod reserved exclusively for you for hours or days at a time.
>
> Once your reservation starts, DevNet emails you credentials and VPN connection instructions. You launch Cisco AnyConnect, connect to the sandbox gateway, and receive a private IP address. You now have full privilege-15 enable access to real virtual routers.

---

## Scene 4 — Comparison & Decision Matrix (3:45–5:00)
**Visual:** Animated comparison table highlighting:
- Availability: Instant vs Scheduled
- Access: Public HTTPS vs AnyConnect VPN
- Permissions: Read-Only vs Full Admin
- Use Case: API GET queries vs Configuration Pushes & Ansible
**Narration:**
> Use Always-On when you need to prototype a quick GET script in five minutes. Use Reservable when your automation needs to write configurations, test rollbacks, or validate pyATS test suites.
>
> Next, let's look at how to evaluate third-party automation code before incorporating it into your project.
