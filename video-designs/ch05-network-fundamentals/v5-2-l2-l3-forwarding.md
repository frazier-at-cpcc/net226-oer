---
video_id: V5.2
chapter: 5
title: "Layer 2 vs. Layer 3 Forwarding: MAC Learning, VLANs, and Route Lookups"
composition_id: net226-v5-2-l2-l3-forwarding
duration_target: "5:30"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss]
blocks: [cpcc-open, mac-learning-anim, longest-prefix-tree]
objectives:
  - Explain how switches populate MAC address tables and handle unknown unicast flooding.
  - Trace 802.1Q VLAN trunk tagging across switch fabrics.
  - Apply the longest-prefix match routing algorithm to determine packet next-hops.
opens_with: cpcc-open
source_section: ch05 §5.2 & 5.3
---

# Video Design: V5.2 Layer 2 vs. Layer 3 Forwarding

---

## Scene 1 — The Two Forwarding Worlds (0:00–1:15)
**Visual:** Split animated graphic: Layer 2 Data Link (MAC frames within a broadcast domain) vs. Layer 3 Network (IP packets routed between subnets).
**Narration:**
> In computer networking, devices forward data at two distinct boundaries: Layer 2 switching and Layer 3 routing.
>
> Switches forward Ethernet frames based on 48-bit physical MAC addresses within a local broadcast domain.
>
> Routers forward IP packets across network boundaries based on logical 32-bit IPv4 or 128-bit IPv6 addresses. Let's look under the hood of both forwarding decisions.

---

## Scene 2 — How Switches Learn and Forward (1:15–3:00)
**Visual:** An animated 4-port switch. A host on Port 1 sends a frame with source MAC `AAAA.AAAA.AAAA` destined for `BBBB.BBBB.BBBB`.
The switch adds `AAAA.AAAA.AAAA -> Port 1` to its MAC table.
Because `BBBB` is not in the table, the switch floods the frame out Ports 2, 3, and 4 (Unknown Unicast Flooding).
When host on Port 3 replies, switch learns `BBBB -> Port 3` and subsequent frames are unicast forwarded directly.
**Block:** `mac-learning-anim`
**Narration:**
> A switch begins life with an empty MAC address table. When a frame arrives on Port 1, the switch inspects the *Source MAC* address and writes it into its table, mapping that MAC to Port 1.
>
> Next, it inspects the *Destination MAC*. If that address is not yet in its table, the switch floods the frame out every port in the same VLAN.
>
> As soon as the destination host replies, the switch learns its port mapping. From that moment forward, frames between those hosts are unicast forwarded with zero flooding.

---

## Scene 3 — The Router's Decision: Longest-Prefix Match (3:00–4:30)
**Visual:** A routing table visualizer displaying three routes:
1. `10.0.0.0/8` via `172.16.1.1`
2. `10.1.0.0/16` via `172.16.2.1`
3. `10.1.20.0/24` via `172.16.3.1`
A packet arrives destined for `10.1.20.55`. All three routes match, but an animated highlight crowns `10.1.20.0/24` as the winner because `/24` has the longest prefix (24 matching bits).
**Block:** `longest-prefix-tree`
**Narration:**
> When an IP packet arrives at a router, the router decrements TTL and searches its routing table using **longest-prefix match**.
>
> Look at this packet destined for `10.1.20.55`. All three routes technically cover that address. But the `/24` route is the most specific.
>
> The router selects the longest matching prefix, decrements the TTL, encapsulates the packet in a new Layer 2 frame with the next-hop MAC, and transmits it out the matching interface.

---

## Scene 4 — Takeaway (4:30–5:30)
**Visual:** Summary takeaway card linking L2/L3 concepts to Packet Tracer Lab 5.2.8.
**Narration:**
> In this week's Packet Tracer lab, you will trace frames and routing decisions step by step in simulation mode. Next, let's look at how edge firewalls and load balancers impact your automation.
