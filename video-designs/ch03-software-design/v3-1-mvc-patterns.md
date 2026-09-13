---
video_id: V3.1
chapter: 3
title: "Software Design Patterns in Network Automation: The MVC Architecture"
composition_id: net226-v3-1-mvc-patterns
duration_target: "4:30"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss, lucide-icons]
blocks: [cpcc-open, mvc-animated-diagram, data-flow-particles]
objectives:
  - Explain why monolithic scripts fail in enterprise environments.
  - Apply the Model-View-Controller (MVC) architectural pattern to network scripts.
  - Decouple device communication logic from data presentation formatters.
opens_with: cpcc-open
source_section: ch03 §3.2
---

# Video Design: V3.1 Software Design Patterns: MVC

---

## Scene 1 — The 1,200-Line Spaghetti Monster (0:00–1:00)
**Visual:** An endless scroll of monolithic Python code fills the screen. Red error badges pop up everywhere: hardcoded print statements, API queries, and formatting logic all tangled together in a single loop.
**Narration:**
> We have all seen it—and many of us have written it: the 1,200-line monolithic script.
>
> It fetches data from a router, processes it inside a nested loop, and prints text directly to the console all at once.
>
> But what happens when your manager asks to send those alerts to a Webex room instead of the console? Or store them in a database? You have to rewrite the entire script. Let's fix this using a software design pattern: Model-View-Controller.

---

## Scene 2 — Deconstructing MVC for Networks (1:00–2:30)
**Visual:** Three clean, modular containers animate onto a dark canvas:
1. **Model:** Illustrated as a structured database/object container holding device state (`interfaces`, `ip_addresses`, `vlan_list`).
2. **View:** Illustrated as modular display lenses (Terminal Table, HTML Dashboard, Webex Card).
3. **Controller:** Illustrated as a central orchestration engine processing CLI arguments.
Light particles travel between Controller, Model, and Views.
**Block:** `mvc-animated-diagram`
**Narration:**
> Model-View-Controller, or MVC, separates an application into three distinct responsibilities:
>
> The **Model** represents your network data and device state. It knows nothing about the terminal or how things look. It only cares about data integrity: device hostnames, interface statuses, and IP allocations.
>
> The **View** handles presentation. It takes data from the Model and formats it. One view formats a clean terminal table; another formats an HTML email; another formats a Webex Adaptive Card.
>
> The **Controller** is the brain. It takes user input—like a command-line flag—instructs the Model to fetch or update data, and tells the View which format to render.

---

## Scene 3 — Swapping Views Seamlessly (2:30–3:45)
**Visual:** The Controller triggers a data refresh. The Model updates with new interface state. With a single click, the View switches from a terminal ASCII table to a rich Webex alert card without altering a single line of the Model code.
**Narration:**
> Look at the architectural power this gives you. When you decouple device interaction from presentation, adding a new notification channel takes five minutes.
>
> You write a new View formatter. You don't touch the Model, and you don't touch your router communication code. Clean, modular, and maintainable.

---

## Scene 4 — Takeaway (3:45–4:30)
**Visual:** Summary card showing how Chapter 3 code modules align to MVC.
**Narration:**
> As you build Milestone 2 this week, organize your repository into models, views, and controllers. In our next video, we'll master the tool that tracks every line of that code: Git.
