---
video_id: V7.2
chapter: 7
title: "Ansible Architecture: Control Nodes, Dynamic Inventories, and SSH CLI"
composition_id: net226-v7-2-ansible-architecture
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [inventory-yaml-editor, terminal-adhoc-run]
objectives:
  - Contrast agentless Ansible architecture with agent-based tools (Puppet/Chef).
  - Configure Ansible inventories (`hosts.yml`) and connection variables.
  - Execute ad-hoc network commands across fleet inventories.
opens_with: cpcc-open
source_section: ch07 §7.3 & 7.4
---

# Video Design: V7.2 Ansible Architecture

---

## Scene 1 — The Agentless Advantage (0:00–1:15)
**Visual:** Diagram comparing agent-based tools requiring third-party software daemons installed on switches vs. Ansible connecting directly over native SSH.
**Narration:**
> Why did Ansible become the undisputed king of network automation?
>
> Because Ansible is completely **agentless**. Tools like Puppet and Chef traditionally require a software agent running inside the device's operating system. On locked network switches where you cannot install custom daemons, agent-based tools hit a wall.
>
> Ansible requires zero software installed on managed network devices. It executes from an Ansible Control Node, communicating over native SSH or HTTPS APIs.

---

## Scene 2 — Configuring the Inventory (1:15–3:15)
**Visual:** VS Code opens `inventory/hosts.yml`. Live typing:
```yaml
all:
  children:
    campus_routers:
      hosts:
        rtr-core-01:
          ansible_host: 10.10.20.48
      vars:
        ansible_network_os: cisco.ios.ios
        ansible_connection: network_cli
        ansible_user: developer
```
**Narration:**
> The foundation of Ansible is the **inventory file**.
>
> We group devices logically into children groups like `campus_routers`.
>
> Notice the critical variables on lines seven and eight:
> `ansible_network_os: cisco.ios.ios` tells Ansible which command parser to use.
> `ansible_connection: network_cli` tells Ansible to maintain an interactive, persistent SSH terminal session rather than expecting a standard Linux bash shell.

---

## Scene 3 — Running Ad-Hoc Commands (3:15–4:45)
**Visual:** Terminal executes an ad-hoc Ansible command against the inventory:
```bash
developer@devasc:~/workspace$ ansible campus_routers -m cisco.ios.ios_command -a "commands='show version'"
rtr-core-01 | SUCCESS => {
    "changed": false,
    "stdout": [
        "Cisco IOS XE Software, Version 16.09.03..."
    ]
}
```
**Narration:**
> Before writing complex playbooks, test connectivity with an ad-hoc command.
>
> We tell Ansible: target the `campus_routers` group, invoke the `cisco.ios.ios_command` module, and execute `show version`.
>
> Ansible connects over SSH, runs the command, captures the output, and returns structured JSON in seconds.

---

## Scene 4 — Wrap-Up (4:45–5:30)
**Visual:** Summary card leading into playbook authoring.
**Narration:**
> With inventory in place, you are ready to write automated playbooks. In our next video, we will author an idempotent playbook to enforce VLAN and interface state.
