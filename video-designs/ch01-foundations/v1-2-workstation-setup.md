---
video_id: V1.2
chapter: 1
title: "Configuring Your Workstation: VS Code, Extensions, and Virtual Envs"
composition_id: net226-v1-2-workstation-setup
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator, xterm]
blocks: [vscode-ui, terminal-capture, callout-box]
objectives:
  - Launch and configure Visual Studio Code in the NETLAB+ DEVASC workstation environment.
  - Install and verify essential extensions: Python, GitLens, and YAML.
  - Create, activate, and configure a dedicated Python 3.10+ virtual environment (`.venv`).
  - Set up interactive breakpoints and execute a script using the integrated debugger.
opens_with: cpcc-open
source_section: ch01 §1.3
---

# Video Design: V1.2 Configuring Your Workstation

> **Output verification:** All terminal commands and paths match the NETLAB+ VE 25 DEVASC workstation image running Linux Cinnamon.

---

## Scene 0 — CPCC Open (0:00–0:02.5)
Standard institutional open with video title card.

---

## Scene 1 — Touring the DEVASC Desktop (0:02.5–1:00)
**Visual:** Crisp screen capture of the NETLAB+ DEVASC workstation desktop. Mouse cursor navigates to the application menu and launches Visual Studio Code. The Welcome screen appears.
**Narration:**
> Welcome to your network automation workspace. Throughout NET-226, you will work inside the NETLAB+ DEVASC workstation image—a purpose-built Linux environment pre-loaded with the DevNet toolchain.
>
> Let's launch Visual Studio Code. VS Code is more than a text editor; it's a modular development platform that unites code authoring, Git version tracking, terminal execution, and interactive debugging into a single unified window.

---

## Scene 2 — Installing Extensions (1:00–2:15)
**Visual:** Mouse clicks the Extensions icon on the Activity Bar. Cursor types `Python` in the search bar. We see Microsoft Python extension installed. Then types `GitLens` and installs it, followed by `YAML` from Red Hat.
**Narration:**
> Out of the box, VS Code is lightweight. Its real power comes from extensions.
>
> First, install the official Microsoft Python extension. This equips your editor with Pylance for intelligent code completion, type signature inspections, and automatic syntax error highlighting.
>
> Next, search for and install GitLens. When you collaborate on automation scripts, GitLens shows you line-by-line git blame annotations directly inside your editor.
>
> Finally, install the YAML extension from Red Hat. You'll spend weeks authoring Ansible playbooks and Docker files; this extension ensures indentation errors are caught before execution.

---

## Scene 3 — Virtual Environments Demystified (2:15–4:00)
**Visual:** VS Code integrated terminal opens with shortcut `Ctrl+~`.
Typing commands character-by-character:
```bash
developer@devasc:~/workspace$ mkdir -p net226-labs && cd net226-labs
developer@devasc:~/workspace/net226-labs$ python3 -m venv .venv
developer@devasc:~/workspace/net226-labs$ source .venv/bin/activate
(.venv) developer@devasc:~/workspace/net226-labs$ which python3
/home/developer/workspace/net226-labs/.venv/bin/python3
```
**Narration:**
> Now open the integrated terminal. Here is a rule you must follow on every Python project: never install third-party automation packages directly into your global system Python environment.
>
> If one project needs `requests` version 2.25 and another needs 2.31, a global install causes breaking conflicts. Instead, we create a virtual environment.
>
> We run `python3 -m venv .venv`. This creates an isolated directory containing its own Python interpreter and independent site-packages directory.
>
> Activate it with `source .venv/bin/activate`. Notice how your terminal prompt changes, prepending `(.venv)`. When we run `which python3`, it points inside our local `.venv` folder. Any package installed now is completely isolated.

---

## Scene 4 — The Integrated Debugger in Action (4:00–5:30)
**Visual:** Creating a test file `test_env.py`. Typing code:
```python
import sys
devices = ["csr1000v", "nexus9k", "catalyst9300"]
for dev in devices:
    print(f"Validating target: {dev}")
print(f"Running Python version: {sys.version.split()[0]}")
```
Placing a red breakpoint on line 4. Pressing `F5`. The execution pauses on line 4. Yellow highlight on line. Hovering over `dev` shows `"csr1000v"`. Step-Over button is pressed twice. Terminal outputs lines.
**Narration:**
> Let's test our setup with an interactive debugging session. In `test_env.py`, we loop through three router targets.
>
> Instead of using messy print statements to figure out where code fails, click just to the left of line four to drop a red breakpoint.
>
> Press F5 to launch the debugger. Execution pauses instantly on line four. Look at the Variables pane on the left: you can inspect the exact memory state of `devices` and `dev`. Step forward one iteration at a time, watch values change, and catch bugs before they cause problems.
>
> Your developer workstation is configured. Next, let's master the Linux command line.
