# Original Instructional Video Curriculum: Applied Network Programmability (NET-226)

**Author & Course Director:** Dr. Frazier A. Smith  
**Institution:** Central Piedmont Community College (CPCC)  
**Target Text:** *Applied Network Programmability: Automating Cisco Infrastructure with Python, APIs, and NetDevOps*  
**Format:** Bespoke, CC-BY-NC 4.0 compliant, high-retention instructional videos embedded directly in Antora AsciiDoc chapter content.  
**Policy Compliance:** **Zero third-party proprietary dependencies** (fully replacing CBT Nuggets video clips with original, institutional-grade media).  

---

## 1. Video Curriculum Design Principles

1. **Cognitive Load Optimization (Micro-Learning):** Every video is tightly scoped between **3 and 6 minutes** (averaging 4.5 minutes), focusing on a single high-impact concept or demonstration.
2. **Pedagogical Modality Mix:** Each chapter features a balanced four-part video suite:
   * **Modality A: Animated Concept Explainer (HyperFrames):** High-design motion graphics illustrating abstract architectural paradigms, protocol layers, and comparison matrices.
   * **Modality B: Terminal & Code Screencast (CodeVideo/CLI):** Live, annotated terminal sessions demonstrating command execution, code syntax, and debugging techniques.
   * **Modality C: Deep Dive & Topology Trace:** Dynamic interactive walkthroughs of packet captures, network topology states, and API explorer tools.
   * **Modality D: Lab & Milestone Coaching:** Direct practical guidance for that week's hands-on lab in NETLAB+ and the individual project milestone deliverable.
3. **Universal Accessibility (Quality Matters Standard 8.4):** Every video is produced with professional-grade synchronized captions (`.vtt`/`.srt`) and an accompanying verbatim markdown transcript.

---

## 2. Master Video Inventory (32 Original Videos | ~2.5 Hours Total Runtime)

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                            ORIGINAL VIDEO PRODUCTION CURRICULUM                             │
├─────────┬─────────────────────────────────────────────────┬───────────┬─────────────────────┤
│ Chapter │ Video Titles & IDs                              │ Count     │ Total Video Runtime │
├─────────┼─────────────────────────────────────────────────┼───────────┼─────────────────────┤
│ Ch. 1   │ V1.1 NetDevOps Mindset, V1.2 Workstation Setup, │ 4 videos  │ 20m 30s             │
│         │ V1.3 Linux CLI, V1.4 Defensive Python           │           │                     │
│ Ch. 2   │ V2.1 DevNet Portal, V2.2 Sandboxes Demystified, │ 4 videos  │ 18m 00s             │
│         │ V2.3 Resource Audit, V2.4 Agile Project Scoping │           │                     │
│ Ch. 3   │ V3.1 MVC Pattern, V3.2 Git Branching & PRs,     │ 4 videos  │ 21m 00s             │
│         │ V3.3 Data Formats Rosetta, V3.4 TDD & unittest  │           │                     │
│ Ch. 4   │ V4.1 API Architectures, V4.2 HTTP Anatomy,      │ 4 videos  │ 21m 00s             │
│         │ V4.3 Postman Testing, V4.4 Resilient Python API │           │                     │
│ Ch. 5   │ V5.1 App Flow Trace, V5.2 L2/L3 Forwarding,     │ 4 videos  │ 22m 00s             │
│         │ V5.3 Edge Devices, V5.4 Network Constraints     │           │                     │
│ Ch. 6   │ V6.1 Deployment Models, V6.2 Dockerfiles,       │ 4 videos  │ 21m 00s             │
│         │ V6.3 GitHub Actions CI, V6.4 Secrets & OWASP    │           │                     │
│ Ch. 7   │ V7.1 IaC & Idempotency, V7.2 Ansible Control,   │ 4 videos  │ 21m 00s             │
│         │ V7.3 IOS Playbooks, V7.4 pyATS State Diffs      │           │                     │
│ Ch. 8   │ V8.1 Model-Driven & YANG, V8.2 NETCONF ncclient,│ 4 videos  │ 22m 00s             │
│         │ V8.3 RESTCONF & JSON, V8.4 Webex ChatOps Bot    │           │                     │
├─────────┴─────────────────────────────────────────────────┴───────────┴─────────────────────┤
│ Total Course Production: 32 Bespoke Instructional Videos | 2 Hours, 47 Minutes Total Media  │
└─────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Chapter-by-Chapter Video Production Specifications

### Chapter 1: Foundations: Development Environment, Linux Systems, and Python

#### V1.1: The NetDevOps Mindset: Why the Network CLI Stopped Scaling
* **Embedded Location:** Chapter 1, Section 1.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 4m 00s
* **Aligned Objective:** CLO 1 | Explain the cultural and operational shift from manual CLI to software-driven programmability.
* **On-Screen Assets:** Split-screen animation showing manual SSH terminal pasting vs. automated pipeline push; timeline showing evolution of network management from serial cables to APIs; kinetic text highlighting "Idempotency", "Auditability", "Velocity".
* **Narration Script Beats:**
  1. *Hook (0:00–0:45):* "Imagine managing 500 edge routers by hand during a midnight maintenance window. One typo, one misplaced subnet mask, and half your branches go dark."
  2. *The CLI Ceiling (0:45–1:45):* Why terminal screens were designed for human eyes in the 1980s, not automation algorithms. Explaining the cost of configuration drift and lack of audit trails.
  3. *The NetDevOps Triad (1:45–3:15):* Introducing the combination of software practices (Git, CI/CD), structured data (JSON/YAML), and programmatic execution (Python/Ansible).
  4. *Takeaway (3:15–4:00):* "Network programmability is not about replacing network engineers with programmers—it’s about giving network engineers superpowers."

#### V1.2: Configuring Your Workstation: VS Code, Extensions, and Python Virtual Environments
* **Embedded Location:** Chapter 1, Section 1.3
* **Format:** Terminal Screencast / CodeVideo Walkthrough
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 1 | Configure and validate a local VS Code and Python workspace.
* **On-Screen Assets:** Full-screen recording of the NETLAB+ DEVASC Cinnamon desktop; opening VS Code; installing the Python, GitLens, and YAML extensions; opening the integrated terminal; creating `.venv` via `python3 -m venv .venv`; activating and selecting interpreter.
* **Narration Script Beats:**
  1. *Introduction (0:00–0:30):* Touring the approved DEVASC workstation environment.
  2. *VS Code Settings (0:30–2:00):* Configuring workspace settings, auto-formatting with Black, and enabling linting.
  3. *Virtual Environments Demystified (2:00–3:45):* Demonstrating why `pip install` on system Python causes package collision disasters; creating and activating isolated virtual environments.
  4. *Interactive Debugging (3:45–5:00):* Setting a breakpoint on a sample script, stepping through variable execution, and inspecting watch values.
  5. *Wrap-Up (5:00–5:30):* Running the verification test command.

#### V1.3: Linux Essentials for Network Engineers: Permissions, Navigation, and Sockets
* **Embedded Location:** Chapter 1, Section 1.4
* **Format:** Terminal Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 1 | Execute Linux commands for navigation, permissions, and network verification.
* **On-Screen Assets:** Linux terminal executing commands with high-contrast text and graphic callouts; diagram of file permission bits (`rwx`); output of `ss -tulpn` highlighting open network ports.
* **Narration Script Beats:**
  1. *Why Linux Matters (0:00–1:00):* Explaining that modern Cisco operating systems (IOS XE, XR, NX-OS) run on Linux kernels.
  2. *Filesystem Navigation (1:00–2:30):* Moving through `/etc/network`, `/var/log`, and project directories with `pwd`, `cd`, and `ls -la`.
  3. *Permissions & Octal Math (2:30–4:15):* Demystifying `chmod 755` vs `chmod 600` (for SSH keys); demonstrating user/group/other ownership via `chown`.
  4. *Inspecting Network Sockets (4:15–5:30):* Using `ss -tulpn` and `ip addr` to verify active network listeners and IP bindings.
  5. *Summary (5:30–6:00):* The core command cheat sheet for subsequent labs.

#### V1.4: Writing Defensive Python: Control Flow, Collections, and Error Handling
* **Embedded Location:** Chapter 1, Section 1.5
* **Format:** Code Walkthrough
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 1 | Construct and debug Python scripts utilizing control flow, collections, and exception handling.
* **On-Screen Assets:** Split-screen with VS Code editor on left and terminal output on right; typing and refactoring a network inventory script; triggering a `KeyError` and catching it gracefully.
* **Narration Script Beats:**
  1. *The Fragile Script Problem (0:00–0:45):* Showing how unhandled network connection timeouts crash scripts mid-execution.
  2. *Structuring Data (0:45–2:00):* Lists of dictionaries representing network devices; extracting nested values cleanly using `.get()`.
  3. *Defensive Try-Except Blocks (2:00–3:45):* Implementing `try...except (ConnectionError, TimeoutError)` blocks with meaningful logging.
  4. *Modularizing into Functions (3:45–4:30):* Encapsulating logic into single-responsibility functions with type hints.
  5. *Challenge (4:30–5:00):* Prompting the student to complete the Week 1 Python practice lab.

---

### Chapter 2: The DevNet Ecosystem: Developer Resources, Sandboxes, and Project Scoping

#### V2.1: Navigating Cisco DevNet: Learning Labs, Code Exchange, and API Docs
* **Embedded Location:** Chapter 2, Section 2.2
* **Format:** Guided Portal Tour & Screencast
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 2 | Navigate `developer.cisco.com` to locate authoritative API documentation and code samples.
* **On-Screen Assets:** Screen capture of `developer.cisco.com` highlighting navigation bars, API documentation search, DevNet Learning Labs tracks, and searching DevNet Code Exchange for verified repositories.
* **Narration Script Beats:**
  1. *The DevNet Landscape (0:00–0:45):* Overview of the Cisco developer ecosystem.
  2. *Finding Authoritative API Specs (0:45–2:15):* Navigating to Catalyst Center and Meraki REST API references; locating HTTP verbs, request schemas, and response samples.
  3. *Leveraging Code Exchange (2:15–3:45):* How to evaluate verified Cisco GitHub repositories, inspect license files, and test sample code safely.
  4. *Takeaway (3:45–4:30):* Bookmarking essential documentation resources for the course.

#### V2.2: Sandboxes Demystified: Always-On vs. Reservable VPN Topologies
* **Embedded Location:** Chapter 2, Section 2.3
* **Format:** Architecture & Demo Screencast
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 2 | Differentiate Always-On and Reservable DevNet Sandboxes.
* **On-Screen Assets:** Side-by-side architectural diagram; live screen recording reserving an IOS XE sandbox; establishing AnyConnect VPN connection; pinging the sandbox gateway router at `10.10.20.48`.
* **Narration Script Beats:**
  1. *Why Sandboxes Exist (0:00–0:45):* Providing free, safe enterprise hardware topologies without risking production gear.
  2. *Always-On: The Fast Track (0:45–2:00):* Shared multi-tenant environments; ideal for read-only GET requests; zero VPN required.
  3. *Reservable: Dedicated Infrastructure (2:00–3:45):* Private virtual pods; scheduling calendar; connecting via AnyConnect; root/enable privileges; persistent changes.
  4. *Common Pitfalls (3:45–4:30):* Forgetting to disconnect VPN, subnet conflicts, and handling reservation timeouts.
  5. *Wrap-Up (4:30–5:00):* When to choose each sandbox type for course labs.

#### V2.3: Evaluating Third-Party Code: Currency, Security, and Deprecation Audits
* **Embedded Location:** Chapter 2, Section 2.4
* **Format:** Code Review Screencast
* **Target Runtime:** 4m 00s
* **Aligned Objective:** CLO 2 | Audit developer resources for authority, currency, and credential security.
* **On-Screen Assets:** Reviewing a sample GitHub repository; spotting hardcoded API keys; inspecting `git log` for exposed secrets; checking commit timestamps and API version paths (`/v1/` vs `/v2/`).
* **Narration Script Beats:**
  1. *The Danger of Copy-Paste (0:00–0:45):* Why blindly executing Stack Overflow network scripts can compromise enterprise infrastructure.
  2. *Checking Provenance & Currency (0:45–1:45):* Verifying repository authors, recent commit activity, and supported firmware versions.
  3. *Security Red Flags (1:45–3:15):* Identifying hardcoded passwords, disabled SSL verification (`verify=False`), and unvetted dependencies.
  4. *Audit Checklist (3:15–4:00):* A 4-step checklist to run before importing any third-party script.

#### V2.4: Scoping the Automation Project: User Stories, Acceptance Criteria, and Backlogs
* **Embedded Location:** Chapter 2, Section 2.5
* **Format:** Project Coaching & Whiteboard Breakdown
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 2 | Translate an enterprise automation problem into measurable requirements and a product backlog.
* **On-Screen Assets:** Digital whiteboard mapping the "Campus-A" customer problem; writing an Agile user story; breaking down acceptance criteria using "Given-When-Then" format; populating a Trello/GitHub Project Kanban board.
* **Narration Script Beats:**
  1. *The Project Challenge (0:00–0:45):* Introducing the *Network Change Automation* semester project.
  2. *Writing Precise User Stories (0:45–2:00):* Framing requirements from the perspective of Network Operations.
  3. *Defining "Done" (2:00–3:30):* Setting objective, testable acceptance criteria so there is zero ambiguity on project success.
  4. *Milestone 1 Deliverable Guidance (3:30–4:30):* Rubric review and submission expectations for Week 2.

---

### Chapter 3: Modern Software Practices: Design Patterns, Version Control, Data Formats, and TDD

#### V3.1: Software Design Patterns in Network Automation: The MVC Architecture
* **Embedded Location:** Chapter 3, Section 3.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 3 | Apply software architectural patterns (MVC, Observer) to network scripts.
* **On-Screen Assets:** Animated breakdown of the Model-View-Controller pattern; diagrams showing how raw router state (Model) is decoupled from formatting (View) and execution logic (Controller).
* **Narration Script Beats:**
  1. *The Monolith Trap (0:00–0:45):* Why 1,000-line "spaghetti" scripts break when output formats change.
  2. *Deconstructing MVC for Networks (0:45–2:30):* What constitutes a Model (inventory/state), a View (CLI tables, Webex cards, HTML), and a Controller (orchestration logic).
  3. *The Power of Decoupling (2:30–3:45):* Swapping output views without touching a single line of device communication code.
  4. *Summary (3:45–4:30):* Applying clean architecture to the course project.

#### V3.2: Git for Network Engineers: Branching, Commits, and Merge Conflict Resolution
* **Embedded Location:** Chapter 3, Section 3.3 & 3.4
* **Format:** Terminal Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 3 | Execute local and collaborative Git workflows, pull requests, and conflict resolution.
* **On-Screen Assets:** Split terminal showing Git commands and live Git graph visualization; executing `git checkout -b feature/vlan`, editing code, staging, committing; intentionally creating a merge conflict on `main` and resolving conflict markers in VS Code.
* **Narration Script Beats:**
  1. *Why Git is the Network Source of Truth (0:00–1:00):* Version history as an immutable audit trail.
  2. *The Golden Rule: Never Commit to Main (1:00–2:15):* Creating isolated feature branches for every change.
  3. *Reading Unified Diffs (2:15–3:30):* Understanding `git diff`, hunk headers, insertions, and deletions.
  4. *Demystifying Merge Conflicts (3:30–5:15):* Reading `<<<<<<< HEAD`, `=======`, `>>>>>>>`; resolving conflicts calmly in VS Code.
  5. *Wrap-Up (5:15–6:00):* Pushing branches and opening clean Pull Requests.

#### V3.3: The Data Serialization Rosetta Stone: XML, JSON, and YAML Demystified
* **Embedded Location:** Chapter 3, Section 3.5 & 3.6
* **Format:** Code Inspection & Visual Comparison
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 3 | Parse and serialize JSON, YAML, and XML documents into Python data structures.
* **On-Screen Assets:** Side-by-side code editor displaying the identical network configuration across JSON, YAML, and XML; highlighting syntax traps (YAML indentation, JSON trailing commas, XML namespaces); live Python REPL parsing each format via `json.loads()`, `yaml.safe_load()`, and `xmltodict.parse()`.
* **Narration Script Beats:**
  1. *Moving Beyond Screen Scraping (0:00–0:45):* Why regex parsing `show ip interface brief` is obsolete.
  2. *Format Comparison (0:45–2:45):* The strengths and syntax rules of JSON (web APIs), YAML (Ansible/configs), and XML (NETCONF).
  3. *Python Parsing in Action (2:45–4:30):* Converting structured text into native Python lists and dictionaries with two lines of code.
  4. *Common Traps (4:30–5:00):* White space errors in YAML and unquoted strings.
  5. *Takeaway (5:00–5:30):* Choosing the right format for the right network protocol.

#### V3.4: Test-Driven Development (TDD) for Network Scripts with Python `unittest`
* **Embedded Location:** Chapter 3, Section 3.7
* **Format:** Code Walkthrough
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 3 | Construct automated unit tests with `unittest` validating normal, boundary, and error conditions.
* **On-Screen Assets:** VS Code editor showing the TDD cycle; writing a failing test in `test_parser.py` (Red); running `python -m unittest` in terminal; implementing parsing code in `parser.py` until the test passes (Green); refactoring with type hints.
* **Narration Script Beats:**
  1. *The Philosophy of Testing (0:00–0:45):* Testing code locally before letting it touch a million-dollar router.
  2. *The Red-Green-Refactor Loop (0:45–2:00):* Writing the expectation before writing the implementation.
  3. *Testing the Edge Cases (2:00–3:30):* Asserting exceptions with `assertRaises()`; testing missing keys and malformed IPs.
  4. *Running Automated Test Discovery (3:30–4:30):* Structuring `tests/` directories for continuous execution.
  5. *Milestone 2 Prep (4:30–5:00):* What instructors look for in your unit test submission.

---

### Chapter 4: REST APIs and Secure Network Integration

#### V4.1: REST vs. RPC vs. Webhooks: Choosing the Right API Architecture
* **Embedded Location:** Chapter 4, Section 4.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 4 | Differentiate REST, RPC, SOAP, and Webhook architectural communication models.
* **On-Screen Assets:** Dynamic animation contrasting client-server polling with event-driven push webhooks; resource-based URL mapping (`/devices/12`) vs action-based RPC calls (`/rebootDevice`).
* **Narration Script Beats:**
  1. *The API Landscape (0:00–0:45):* Why not all APIs operate the same way.
  2. *The REST Architectural Model (0:45–2:00):* Resources, statelessness, standard HTTP methods, and uniform interfaces.
  3. *When RPC Makes Sense (2:00–2:45):* Direct action verbs vs noun resources.
  4. *The Power of Webhooks (2:45–3:45):* Stopping the polling madness; push notifications on link failure.
  5. *Summary (3:45–4:30):* Selecting the right model for enterprise automation tasks.

#### V4.2: Deconstructing the HTTP Transaction: Methods, Headers, and Status Code Diagnostics
* **Embedded Location:** Chapter 4, Section 4.3
* **Format:** Visual Breakdown & Packet Inspection
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 4 | Structure HTTP requests and interpret status codes for error diagnosis.
* **On-Screen Assets:** Dissected graphic of an HTTP request and response packet; highlighting Method, Path, Headers (`Authorization`, `Content-Type`), and JSON Payload; interactive status code diagnostic flowchart.
* **Narration Script Beats:**
  1. *Anatomy of a Call (0:00–1:00):* Dissecting an HTTP transaction down to its protocol elements.
  2. *Verbs and Idempotency (1:00–2:15):* GET vs POST vs PUT vs PATCH vs DELETE; what idempotency means in practice.
  3. *Headers That Matter (2:15–3:15):* Authentication headers, content negotiation, and User-Agent.
  4. *Diagnosing Status Codes (3:15–4:30):* 2xx triumphs, 401 vs 403 authorization failures, 404 missing routes, and 429 rate limit backoff.
  5. *Takeaway (4:30–5:00):* Reading error bodies to debug failing requests instantly.

#### V4.3: API Testing with Postman: Collections, Environments, and Automated Test Scripts
* **Embedded Location:** Chapter 4, Section 4.5
* **Format:** Application Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 4 | Test REST APIs interactively using Postman collections and environment variables.
* **On-Screen Assets:** Live Postman interface; importing an API collection; configuring `{{base_url}}` and `{{auth_token}}` in an Environment; executing an authentication request; extracting token via test script; executing subsequent requests seamlessly.
* **Narration Script Beats:**
  1. *Why Test in Postman First (0:00–0:45):* Separating API protocol understanding from Python syntax debugging.
  2. *Managing Collections & Environments (0:45–2:15):* Creating modular request suites and switching between dev, test, and sandbox variables.
  3. *Chaining Authentication Tokens (2:15–4:00):* Writing a Postman test script to automatically save dynamic tokens to environment variables.
  4. *Writing Automated Test Assertions (4:00–5:15):* Checking status codes and verifying JSON payload keys in JavaScript.
  5. *Wrap-Up (5:15–6:00):* Exporting collections for portfolio submissions.

#### V4.4: Building Resilient Python API Clients: Authentication, Pagination, and Exponential Backoff
* **Embedded Location:** Chapter 4, Section 4.6
* **Format:** Code Walkthrough
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 4 | Construct a Python REST API client with credential security, pagination, and error handling.
* **On-Screen Assets:** VS Code screencast building a Meraki/Cisco REST API client using Python `requests`; using `os.environ` for secrets; implementing a pagination loop; catching `HTTPError` and handling status code 429 with `time.sleep()`.
* **Narration Script Beats:**
  1. *The Script that Fails in Production (0:00–0:45):* Hardcoded tokens, uncaught timeouts, and silent rate-limiting drops.
  2. *Secure Secrets Ingestion (0:45–1:45):* Loading API keys from environment variables using `os.environ.get()`.
  3. *Handling API Pagination (1:45–3:15):* Traversing multi-page inventories without missing devices.
  4. *Surviving Rate Limits (3:15–4:45):* Detecting HTTP 429, reading the `Retry-After` header, and implementing exponential backoff.
  5. *Milestone 3 Guidance (4:45–5:30):* Expectations for the Week 4 project client deliverable.

---

### Chapter 5: Network Fundamentals and Application Flow Troubleshooting

#### V5.1: Anatomy of an Application Flow: Tracing Packet Travel from Client to API Gateway
* **Embedded Location:** Chapter 5, Section 5.1
* **Format:** Packet & Topology Walkthrough (Wireshark & Animated Trace)
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 5 | Trace an application flow across addressing, routing, DNS, DHCP, NAT, and transport evidence.
* **On-Screen Assets:** Animated enterprise topology diagram synchronized with live Wireshark packet captures; highlighting packet traversal from laptop through switch, router, NAT gateway, firewall, to cloud API server.
* **Narration Script Beats:**
  1. *The Mystery Outage (0:00–0:45):* "My Python script timed out—is it a script bug, or did the packet die in transit?"
  2. *Step 1: The Name Resolution (0:45–1:45):* Tracing the DNS query on UDP port 53.
  3. *Step 2: Layer 2 & 3 Hop-by-Hop (1:45–3:15):* ARP lookup, MAC header rewrite, default gateway routing, and TTL decrement.
  4. *Step 3: Traversing NAT & Firewalls (3:15–4:30):* Port Address Translation (PAT) and stateful inspection tables.
  5. *Step 4: Transport Handshake (4:30–5:30):* Establishing TCP port 443 connection and TLS negotiation.
  6. *Takeaway (5:30–6:00):* The mental model required to troubleshoot distributed automation systems.

#### V5.2: Layer 2 vs. Layer 3 Forwarding: MAC Learning, VLANs, and Routing Table Lookups
* **Embedded Location:** Chapter 5, Section 5.2 & 5.3
* **Format:** Packet Tracer Interactive Simulation
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 5 | Trace Layer 2 switching frames and Layer 3 packet forwarding paths.
* **On-Screen Assets:** Cisco Packet Tracer in Simulation Mode; visualizing frames moving across switchports; inspecting switch MAC address table; stepping into router forwarding decision and examining `show ip route`.
* **Narration Script Beats:**
  1. *The Two Forwarding Worlds (0:00–0:45):* Frame forwarding within a LAN vs. packet routing between networks.
  2. *How Switches Learn (0:45–2:15):* Source MAC learning, CAM table aging, and unknown unicast flooding.
  3. *VLAN Tagging (2:15–3:15):* Broadcast domains, 802.1Q trunk headers, and access port enforcement.
  4. *The Router's Decision (3:15–4:45):* Longest-prefix match in the routing table, ARP cache resolution, and Layer 2 re-encapsulation.
  5. *Summary (4:45–5:30):* How L2/L3 misconfigurations manifest as script timeouts.

#### V5.3: The Impact of Edge Services: Firewalls, NAT, and Load Balancers on API Traffic
* **Embedded Location:** Chapter 5, Section 5.5
* **Format:** Network Architecture Explainer (Diagram & Terminal)
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 5 | Evaluate the operational impact of firewalls, NAT, and load balancers on application traffic.
* **On-Screen Assets:** Animated diagrams of stateful firewalls dropping unauthorized TCP SYN packets; PAT translation tables; load balancer reverse proxy distributing traffic across backend pools.
* **Narration Script Beats:**
  1. *The Middlebox Gauntlet (0:00–0:45):* Why network infrastructure scripts frequently clash with security edge devices.
  2. *Stateful Firewalls (0:45–2:00):* Connection tracking tables; why outbound API calls succeed but inbound webhooks fail without explicit rules.
  3. *NAT and PAT (2:00–3:15):* Private-to-public port multiplexing; implications for direct device management.
  4. *Reverse Proxies & Load Balancers (3:15–4:30):* TLS termination, session affinity, and health probe failures.
  5. *Takeaway (4:30–5:00):* Designing scripts that survive enterprise network boundaries.

#### V5.4: Network Constraints in Practice: How Latency, Jitter, and Packet Loss Break Scripts
* **Embedded Location:** Chapter 5, Section 5.7
* **Format:** Diagnostic Screencast & Lab Simulation
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 5 | Quantify the impact of network constraints (bandwidth, latency, jitter, loss) on software execution.
* **On-Screen Assets:** Terminal executing a Python network automation loop; injecting artificial network delay (`tc netem delay 250ms`) and packet loss; observing HTTP timeouts, TCP retransmissions, and script crashes.
* **Narration Script Beats:**
  1. *The Happy Path Illusion (0:00–0:45):* Scripts tested on zero-latency localhost vs. real WAN realities.
  2. *Latency & the TCP Window (0:45–2:00):* Why chatty REST API requests suffer exponential slowdown over high RTT links.
  3. *Packet Loss & Retransmissions (2:00–3:15):* Demonstrating socket drops and connection pool exhaustion.
  4. *Defensive Script Tuning (3:15–4:30):* Setting realistic socket timeouts, implementing connection pooling, and payload chunking.
  5. *Incident Report Guidance (4:30–5:00):* How to formulate your Week 5 failure-mode checkpoint deliverable.

---

### Chapter 6: Application Deployment, Continuous Integration, and Security

#### V6.1: Deployment Evolution: Bare Metal to Virtual Machines to Docker Containers
* **Embedded Location:** Chapter 6, Section 6.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 6 | Compare application deployment architectures across compute models.
* **On-Screen Assets:** 3D animated architectural comparison stacking hardware, hypervisors, guest operating systems, container engines, and microservices; visual meters showing boot time, memory overhead, and density.
* **Narration Script Beats:**
  1. *The Deployment Dilemma (0:00–0:45):* The historical pain of running dedicated physical servers for single utilities.
  2. *The Hypervisor Revolution (0:45–1:45):* VMs, hardware virtualization, resource isolation, and the cost of duplicating OS kernels.
  3. *The Container Breakthrough (1:45–3:15):* Linux namespaces, cgroups, sharing the host kernel, and sub-second container instantiation.
  4. *Edge & Cloud Considerations (3:15–4:00):* Running containers on branch routers and IoT gateways.
  5. *Summary (4:00–4:30):* Why containers are the universal packaging format for NetDevOps.

#### V6.2: Containerizing Network Automation: Authoring Clean, Multi-Stage Dockerfiles
* **Embedded Location:** Chapter 6, Section 6.3
* **Format:** Terminal Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 6 | Build and run a containerized network application with documented port exposure.
* **On-Screen Assets:** Writing a `Dockerfile` in VS Code; running `docker build -t net-audit:v1 .`; inspecting layer caching; executing `docker run -d -p 8080:5000 --name audit-app net-audit:v1`; verifying logs with `docker logs -f audit-app`.
* **Narration Script Beats:**
  1. *Writing Your First Dockerfile (0:00–1:15):* Dissecting `FROM python:slim`, `WORKDIR`, `COPY`, `RUN`, `EXPOSE`, and `CMD`.
  2. *Layer Caching Best Practices (1:15–2:45):* Ordering `COPY requirements.txt` before application source to avoid rebuilding dependencies.
  3. *Port Mapping & Networking (2:45–4:15):* Explaining `-p 8080:5000` mapping host sockets to container namespaces.
  4. *Running as Non-Root (4:15–5:15):* Security hardening via `USER appuser`.
  5. *Wrap-Up (5:15–6:00):* Testing containerized API execution against the target sandbox.

#### V6.3: Automating Quality: Building a Continuous Integration (CI) Pipeline with GitHub Actions
* **Embedded Location:** Chapter 6, Section 6.4
* **Format:** Screencast & Pipeline Execution Walkthrough
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 6 | Configure a continuous-integration workflow that runs automated tests on repository changes.
* **On-Screen Assets:** Authoring `.github/workflows/ci.yml` in VS Code; pushing commit to GitHub; watching GitHub Actions pipeline trigger; viewing live console logs as runner spins up Ubuntu, installs Python, runs `unittest`, and builds Docker container.
* **Narration Script Beats:**
  1. *What is CI/CD in Infrastructure (0:00–0:45):* Ensuring zero broken scripts enter production.
  2. *The Anatomy of a Workflow (0:45–2:15):* Triggers (`on: [push]`), jobs, runner environments, and sequential steps.
  3. *Automating Test Execution (2:15–3:45):* Running test suites in an isolated cloud runner; failing the pipeline if any test breaks.
  4. *Automated Container Builds (3:45–4:45):* Compiling the container image only after test passes.
  5. *Milestone 4 Guidance (4:45–5:30):* Submitting passing pipeline logs for project credit.

#### V6.4: Securing Network Applications: Secrets Management and Defending the OWASP Top 10
* **Embedded Location:** Chapter 6, Section 6.5 & 6.6
* **Format:** Security Explainer & Code Defense
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 6 | Apply credential protection and mitigate OWASP vulnerabilities in network tools.
* **On-Screen Assets:** Demonstrating command injection in a vulnerable network ping utility; refactoring code to sanitize input; configuring GitHub Secrets; ensuring `.env` is tracked in `.gitignore`.
* **Narration Script Beats:**
  1. *The Exposed Credential Catastrophe (0:00–1:00):* Scanning public GitHub repositories for leaked Cisco API tokens and private keys.
  2. *Proper Secrets Hygiene (1:00–2:15):* Using `.gitignore`, environment variables, and encrypted secrets vaults.
  3. *OWASP Command Injection (2:15–3:45):* Why `os.system("ping " + user_input)` is a critical vulnerability; refactoring to safe parameter lists.
  4. *Defensive Coding Principles (3:45–4:30):* Principle of least privilege, TLS enforcement, and secure logging.
  5. *Summary (4:30–5:00):* Security checklist for enterprise automation scripts.

---

### Chapter 7: Infrastructure as Code: Ansible Automation and Device Validation

#### V7.1: Infrastructure as Code: Idempotency, Desired State, and Configuration Drift
* **Embedded Location:** Chapter 7, Section 7.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 4m 30s
* **Aligned Objective:** CLO 7 | Explain the principles of Infrastructure as Code, idempotency, and declarative configuration.
* **On-Screen Assets:** Dynamic animation illustrating configuration drift across router fleets; visual timeline demonstrating the difference between running an imperative script twice (causing duplicate lines and errors) vs. an idempotent playbook twice (reporting `changed: false`).
* **Narration Script Beats:**
  1. *The Configuration Drift Epidemic (0:00–0:45):* How manual changes turn clean networks into undocumented snowflake systems.
  2. *Defining Desired State (0:45–2:00):* Specifying *what* the network should look like rather than *how* to configure it.
  3. *The Power of Idempotency (2:00–3:30):* Executing changes with 100% confidence; zero side-effects when state already matches.
  4. *Summary (3:30–4:30):* Transitioning from ad-hoc scripts to enterprise configuration management.

#### V7.2: Ansible Architecture: Control Nodes, Dynamic Inventories, and SSH Network CLI
* **Embedded Location:** Chapter 7, Section 7.3 & 7.4
* **Format:** Terminal Screencast
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 7 | Install and configure an Ansible control node with structured inventory.
* **On-Screen Assets:** DEVASC terminal configuring `ansible.cfg` and `inventory/hosts.yml`; defining device groups (`[routers]`, `[switches]`); setting connection parameters (`ansible_connection: network_cli`); running an ad-hoc ping and `ios_command` test across the inventory.
* **Narration Script Beats:**
  1. *Why Ansible Dominates Networking (0:00–1:00):* The agentless advantage; managing devices over native SSH without custom OS software.
  2. *Structuring Your Inventory (1:00–2:30):* Host grouping, parent-child relationships, and variable scoping in YAML.
  3. *Connection Plugins Demystified (2:30–3:45):* Why `network_cli` is required instead of standard Linux SSH shells.
  4. *Running Ad-Hoc Commands (3:45–5:00):* Executing fleet-wide state checks in 10 seconds.
  5. *Wrap-Up (5:00–5:30):* Prepping for playbook development.

#### V7.3: Authoring Idempotent Network Playbooks with the `cisco.ios` Collection
* **Embedded Location:** Chapter 7, Section 7.5
* **Format:** Code & Execution Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 7 | Create an idempotent Ansible playbook enforcing Cisco IOS configuration state.
* **On-Screen Assets:** Authoring `configure_campus.yml` in VS Code; utilizing `cisco.ios.ios_config` to enforce VLANs, access ports, and descriptions; executing `ansible-playbook configure_campus.yml -v` in terminal; observing `changed: 1`; executing a second time and observing `ok: 1, changed: 0`.
* **Narration Script Beats:**
  1. *Playbook Anatomy (0:00–1:15):* Plays, hosts, tasks, and modules.
  2. *The `cisco.ios` Collection (1:15–2:45):* Managing parents and child configuration lines; handling sub-interface modes.
  3. *Proving Idempotency Live (2:45–4:15):* Running the playbook twice and analyzing the terminal execution summary.
  4. *Capturing Output with Register (4:15–5:15):* Registering command results and asserting state.
  5. *Milestone 5 Guidance (5:15–6:00):* Packaging your playbook and evidence.

#### V7.4: Automated State Verification: Snapshot Testing and Diffs with pyATS and Genie
* **Embedded Location:** Chapter 7, Section 7.6
* **Format:** Terminal Screencast
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 7 | Use an automated test framework (pyATS/Genie) to collect and evaluate device state.
* **On-Screen Assets:** Terminal session running `pyats` and `genie`; capturing a baseline network snapshot (`genie parse "show ip route"`); pushing an automated change; capturing post-snapshot; executing `genie diff pre post` and highlighting added/removed routes in color.
* **Narration Script Beats:**
  1. *Beyond Grep (0:00–0:45):* Why parsing raw CLI text strings is a maintenance nightmare.
  2. *Introducing pyATS and Genie (0:45–2:00):* Cisco's official test harness; transforming operational show commands into structured JSON dictionaries.
  3. *Snapshot-Driven Change Verification (2:00–3:45):* Taking pre-change baselines, applying changes, taking post-change snapshots.
  4. *The Power of `genie diff` (3:45–4:45):* Automatically identifying routing drops and interface changes with mathematical precision.
  5. *Takeaway (4:45–5:30):* Incorporating automated verification into your change management workflow.

---

### Chapter 8: Model-Driven Programmability, Controller APIs, and Capstone Demonstration

#### V8.1: Why CLI Scraping Fails: The Power of Model-Driven Programmability and YANG
* **Embedded Location:** Chapter 8, Section 8.1 & 8.2
* **Format:** Animated Concept Explainer (HyperFrames Motion Graphics)
* **Target Runtime:** 5m 00s
* **Aligned Objective:** CLO 8 | Interpret YANG models differentiating configuration from operational data.
* **On-Screen Assets:** Visualizing how firmware updates break human CLI text scrapers; animated tree diagram of YANG models (`ietf-interfaces`); highlighting root modules, containers, lists, leaves, and `config true` vs `config false`.
* **Narration Script Beats:**
  1. *The Brittle CLI (0:00–1:00):* The fundamental flaw of building enterprise automation on human-facing console output.
  2. *The Model-Driven Architecture (1:00–2:30):* Decoupling the data schema from the transport protocol.
  3. *YANG: The Universal Network Schema (2:30–3:45):* Trees, containers, lists, and types; why YANG guarantees type safety.
  4. *Config vs State Data (3:45–4:30):* Desired configuration vs real-time operational telemetry (counters, status).
  5. *Summary (4:30–5:00):* How YANG powers both NETCONF and RESTCONF.

#### V8.2: NETCONF in Action: Executing XML RPCs with Python and `ncclient`
* **Embedded Location:** Chapter 8, Section 8.3
* **Format:** Terminal & Code Screencast
* **Target Runtime:** 6m 00s
* **Aligned Objective:** CLO 8 | Construct and execute NETCONF RPC operations using Python `ncclient` over SSH.
* **On-Screen Assets:** VS Code script using `ncclient.manager.connect()`; connecting over SSH port 830 to a live Cisco CSR1000v router; passing an XML subtree filter for `<interfaces>`; sending `<edit-config>` to update an interface description; inspecting raw `<rpc-reply>` XML.
* **Narration Script Beats:**
  1. *NETCONF Protocol Fundamentals (0:00–1:15):* SSH transport on port 830, XML encoding, and RPC messaging.
  2. *The Capabilities Exchange (1:15–2:15):* How routers and scripts negotiate supported YANG schemas during `<hello>`.
  3. *Filtering Configuration Subtrees (2:15–3:45):* Querying exactly the interface configuration you need without dumping 5,000 lines of config.
  4. *Atomic Edits with `<edit-config>` (3:45–5:15):* Submitting compliant XML changes to the running datastore.
  5. *Wrap-Up (5:15–6:00):* Verifying changes and closing NETCONF sessions cleanly.

#### V8.3: RESTCONF in Practice: Managing IOS-XE Devices with HTTP and `yang-data+json`
* **Embedded Location:** Chapter 8, Section 8.4
* **Format:** Application & Code Screencast (Postman & Python)
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 8 | Formulate and execute RESTCONF HTTP requests using Python `requests`.
* **On-Screen Assets:** Postman submitting RESTCONF requests to `https://10.10.20.48/restconf/data/ietf-interfaces:interfaces`; setting `Content-Type: application/yang-data+json`; executing GET and PATCH operations; converting Postman request into Python `requests` code.
* **Narration Script Beats:**
  1. *REST Meets YANG (0:00–1:00):* When to use RESTCONF over NETCONF; HTTPS port 443 and JSON formatting.
  2. *Deconstructing RESTCONF URIs (1:00–2:30):* Root `/restconf/data/`, module namespace prefix, container paths, and key selectors.
  3. *PATCH vs PUT Operations (2:30–3:45):* Updating single leaves without blowing away adjacent interface configs.
  4. *Writing the Python RESTCONF Client (3:45–4:45):* Handling self-signed certificates and parsing YANG-JSON payloads.
  5. *Takeaway (4:45–5:30):* The easiest pathway for web developers to program network gear.

#### V8.4: ChatOps and Controller APIs: Building a Webex Bot for Network Alerting
* **Embedded Location:** Chapter 8, Section 8.5 & 8.6
* **Format:** Screencast & Bot Integration Demo
* **Target Runtime:** 5m 30s
* **Aligned Objective:** CLO 8 & Synthesis | Integrate controller and collaboration APIs for end-to-end event notification.
* **On-Screen Assets:** Creating a Bot on `developer.webex.com`; capturing the bot access token; writing a Python script that detects an interface down event via RESTCONF and posts an interactive Markdown alert card to an operations Webex room.
* **Narration Script Beats:**
  1. *The Power of ChatOps (0:00–0:45):* Bringing automated infrastructure alerts directly into operational chat channels.
  2. *Creating a Cisco Webex Bot (0:45–1:45):* Bot tokens, permissions, and security.
  3. *Posting Rich Messages (1:45–3:15):* Structuring markdown and adaptive cards via `POST https://webexapis.com/v1/messages`.
  4. *Connecting the Circuit (3:15–4:30):* Triggering alerts from router state changes.
  5. *Capstone & Skills Assessment Coaching (4:30–5:30):* Final walkthrough expectations and demonstration packet submission tips.

---

## 4. Production Pipeline & Embedding Specifications

### Embedding Syntax in Antora AsciiDoc
Each video will be hosted on an institutional streaming endpoint (or YouTube / Vimeo unlisted embed) and embedded in the chapter `.adoc` files using responsive HTML5 video containers:

```asciidoc
.Video 1.2: Configuring Your Workstation — VS Code and Virtual Environments
[video, width=800, height=450]
video::v1-2-workstation-setup.mp4[poster=v1-2-poster.png, captions=v1-2-captions.vtt]

TIP: You can download the link:https://frazier-at-cpcc.github.io/net226-oer/transcripts/v1-2-transcript.txt[Plain Text Transcript] or follow along in your NETLAB+ DEVASC workstation.
```
