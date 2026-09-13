---
video_id: V7.3
chapter: 7
title: "Authoring Idempotent Network Playbooks with the cisco.ios Collection"
composition_id: net226-v7-3-cisco-ios-playbooks
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [playbook-yaml-editor, terminal-playbook-exec]
objectives:
  - Author structured Ansible playbooks using plays, tasks, and modules.
  - Utilize `cisco.ios.ios_config` to manage parent/child configuration blocks.
  - Execute a playbook twice to demonstrate live idempotency (`changed: 0`).
opens_with: cpcc-open
source_section: ch07 §7.5
---

# Video Design: V7.3 Authoring Idempotent Playbooks

---

## Scene 1 — Anatomy of an Ansible Playbook (0:00–1:45)
**Visual:** VS Code opens `deploy_vlans.yml`. Live typing:
```yaml
---
- name: Enforce VLAN Compliance on Campus Switches
  hosts: campus_routers
  gather_facts: no

  tasks:
    - name: Ensure VLAN 100 Exists
      cisco.ios.ios_config:
        lines:
          - name CORPORATE_DATA
        parents: vlan 100

    - name: Configure GigabitEthernet2
      cisco.ios.ios_config:
        lines:
          - description Workstation Access Port
          - ip address 10.100.1.1 255.255.255.0
          - no shutdown
        parents: interface GigabitEthernet2
```
**Narration:**
> An Ansible playbook is a YAML document describing a sequence of automation tasks.
>
> At the top: the play header specifies the target host group and disables standard Linux fact gathering.
>
> In our tasks, we use the `cisco.ios.ios_config` module. Notice the `parents:` parameter: this instructs Ansible to enter sub-configuration modes—like `vlan 100` or `interface GigabitEthernet2`—before applying child lines.

---

## Scene 2 — First Execution: Applying Changes (1:45–3:30)
**Visual:** Terminal executes `ansible-playbook -i inventory/hosts.yml deploy_vlans.yml`:
```bash
PLAY [Enforce VLAN Compliance on Campus Switches] *************************************
TASK [Ensure VLAN 100 Exists] *********************************************************
changed: [rtr-core-01]
TASK [Configure GigabitEthernet2] *****************************************************
changed: [rtr-core-01]
PLAY RECAP ****************************************************************************
rtr-core-01 : ok=2    changed=2    unreachable=0    failed=0
```
**Narration:**
> We execute our playbook. Ansible connects to our router, inspects running configuration, discovers that VLAN 100 and the interface description are missing, and pushes the commands.
>
> In the play recap, look at the result: `changed=2`. The device was successfully updated.

---

## Scene 3 — Second Execution: Proving Idempotency (3:30–4:45)
**Visual:** Pressing Up arrow in terminal to run the exact same playbook again immediately:
```bash
PLAY [Enforce VLAN Compliance on Campus Switches] *************************************
TASK [Ensure VLAN 100 Exists] *********************************************************
ok: [rtr-core-01]
TASK [Configure GigabitEthernet2] *****************************************************
ok: [rtr-core-01]
PLAY RECAP ****************************************************************************
rtr-core-01 : ok=2    changed=0    unreachable=0    failed=0
```
A green highlight illuminates `changed=0`.
**Narration:**
> Now, without touching anything, we run the exact same command a second time.
>
> Look at the play recap: `ok=2, changed=0`.
>
> Ansible queried the device, determined that VLAN 100 and the interface IP already matched our desired state, and pushed zero changes. That is idempotency in action.

---

## Scene 4 — Milestone 5 Guidance (4:45–6:00)
**Visual:** Reviewing Milestone 5 deliverable expectations: playbook, assertions, and verification log.
**Narration:**
> For Project Milestone 5, you will author an idempotent playbook applying changes to your reservation router.
>
> In our next video, we will learn how to verify device state scientifically using pyATS and Genie.
