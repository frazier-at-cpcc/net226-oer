# Applied Network Programmability: Automating Cisco Infrastructure with Python, APIs, and NetDevOps

An open educational resource (OER) textbook for **NET-226 — Network Programmability** at Central Piedmont Community College.

**Author:** Dr. Frazier A. Smith  
**Target Certification:** Cisco Certified DevNet Associate (200-901 DEVASC)  
**Format:** Written in AsciiDoc and structured for Antora documentation site generation.

## About This Textbook

This textbook supports an 8-week asynchronous online course aligned to the Cisco DevNet Associate certification and Quality Matters 7th Edition Higher Education standards. Each chapter maps 1:1 to a course instructional week, combining theoretical foundations, hands-on NETLAB+ and Packet Tracer lab bridges, custom embedded instructional videos, and weekly milestones for an authentic individual Network Change Automation project.

| Chapter | Topic | Key Technologies & Concepts |
|---|---|---|
| 1. Foundations: Environment, Linux & Python | Workspace setup, Linux shell, Python control flow | VS Code, Linux POSIX, Python 3.10+, Virtual Envs |
| 2. The DevNet Ecosystem & Project Scoping | Cisco DevNet portal, sandboxes, agile requirements | DevNet Sandboxes, API Docs, Code Exchange, Backlogs |
| 3. Software Design, Git, Formats & TDD | Software design patterns, Git workflows, JSON/YAML/XML, unit testing | MVC, Git PRs, PyYAML, json, xmltodict, unittest |
| 4. REST APIs & Secure Network Integration | REST constraints, HTTP methods, authentication, Postman, Python clients | REST, Postman, Bearer Tokens, OAuth, requests, Meraki API |
| 5. Network Fundamentals & App Diagnostics | L2/L3 forwarding, L4 TCP/UDP, IP services, planes, network constraints | VLANs, Routing, TCP Handshake, DNS/DHCP/NTP, Latency/Jitter |
| 6. Container Deployment, CI/CD & Security | Deployment models, Docker, automated CI pipelines, OWASP threats | Dockerfiles, GitHub Actions, Secrets Vaults, OWASP Top 10 |
| 7. Infrastructure as Code with Ansible | IaC, agentless automation, playbooks, automated validation | Ansible, cisco.ios, Jinja2, pyATS/Genie, Idempotency |
| 8. Model-Driven Programmability & Capstone | YANG modeling, NETCONF, RESTCONF, controller APIs, ChatOps | YANG, NETCONF (ncclient), RESTCONF, DNA Center, Webex |

## Architecture & Production Assets

* [`graphics-manifest.md`](graphics-manifest.md): Complete specifications and generative prompts for all 51 textbook diagrams and architecture illustrations.
* [`video-manifest.md`](video-manifest.md): Complete curriculum specification for the 32 bespoke instructional videos embedded across the 8 chapters.
* [`video-designs/`](video-designs/): State-of-the-art production design documents for all 32 videos, utilizing HyperFrames and CodeVideo engines with scene-by-scene timing, animations, and verbatim scripts.

## License

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).
