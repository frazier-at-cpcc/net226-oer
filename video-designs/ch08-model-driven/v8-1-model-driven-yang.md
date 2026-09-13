---
video_id: V8.1
chapter: 8
title: "Why CLI Scraping Fails: The Power of Model-Driven Programmability & YANG"
composition_id: net226-v8-1-model-driven-yang
duration_target: "5:00"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss, lucide-icons]
blocks: [cpcc-open, model-driven-stack-anim, yang-tree-interactive]
objectives:
  - Contrast human-oriented CLI scraping with machine-oriented model-driven programmability.
  - Deconstruct YANG schemas into containers, lists, and leaves.
  - Distinguish configuration data (`config true`) from operational telemetry (`config false`).
opens_with: cpcc-open
source_section: ch08 §8.1 & 8.2
---

# Video Design: V8.1 Model-Driven Programmability & YANG

---

## Scene 1 — The Brittle CLI Ceiling (0:00–1:15)
**Visual:** Animation of a developer building a house of cards labeled "Regex Scrapers". A gentle breeze labeled "IOS XE 17.3 Update" blows the cards down.
**Narration:**
> Throughout this course, we've seen why the traditional command line fails when automation scales. The CLI was created for human eyes.
>
> When firmware updates change output formatting, screen-scraping breaks.
>
> What if network devices had an explicit, unambiguous software contract—a schema that strictly defines every configuration setting, every interface, and every telemetry counter?
>
> That schema exists. It is called YANG.

---

## Scene 2 — The Model-Driven Stack (1:15–2:30)
**Visual:** 4-layer animated protocol stack:
- Top: **Encoding** (JSON, XML)
- Layer 2: **Data Model** (YANG RFC 6020/7950)
- Layer 3: **Protocols** (NETCONF RFC 6241, RESTCONF RFC 8040)
- Bottom: **Transport** (SSH Port 830, HTTPS Port 443)
**Block:** `model-driven-stack-anim`
**Narration:**
> Model-Driven Programmability decouples four distinct layers:
>
> At the foundation: secure transport using SSH or HTTPS.
>
> Above transport: management protocols—NETCONF and RESTCONF.
>
> In the center: the data model—**YANG**. YANG models the data, independent of how it is sent or formatted.
>
> And at the top: serialization encoding using XML or JSON.

---

## Scene 3 — Inside a YANG Model (2:30–4:00)
**Visual:** Interactive YANG tree diagram based on `ietf-interfaces`:
- Root container: `interfaces`
- List: `interface` [key: `name`]
- Leaves: `name (string)`, `description (string)`, `enabled (boolean)`
- Red badge: `rw` (Read-Write Config) vs Blue badge: `ro` (Read-Only Operational Telemetry like packet counters).
**Block:** `yang-tree-interactive`
**Narration:**
> Look at the structure of a YANG model. It organizes device state as a hierarchical tree:
>
> A **container** groups related elements.
>
> A **list** represents repeatable records—like multiple switch interfaces—each indexed by a unique key.
>
> A **leaf** holds a single typed value, like an integer, IP address, or boolean.
>
> Crucially, YANG distinguishes between two types of data:
> `config true` nodes are read-write configurations you can change.
> `config false` nodes are read-only operational telemetry—like input octets, error counters, and link status.

---

## Scene 4 — Takeaway (4:00–5:00)
**Visual:** Summary card leading into NETCONF and RESTCONF protocols.
**Narration:**
> Because YANG models are mathematically defined schemas, both your script and the router agree on the data structure before a single packet is sent.
>
> In our next video, we will use Python and NETCONF to interact with YANG models over SSH.
