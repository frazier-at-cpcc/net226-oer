---
video_id: V3.2
chapter: 3
title: "Git for Network Engineers: Branching, Commits, and Conflict Resolution"
composition_id: net226-v3-2-git-for-networks
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator, gitgraph]
blocks: [terminal-git-run, git-graph-live, conflict-diff-resolver]
objectives:
  - Initialize a local Git repository and execute standard commit lifecycles.
  - Create and manage feature branches (`git checkout -b`).
  - Read unified diffs and resolve merge conflicts calmly in VS Code.
opens_with: cpcc-open
source_section: ch03 §3.3 & 3.4
---

# Video Design: V3.2 Git for Network Engineers

---

## Scene 1 — The Three Trees of Git (0:00–1:30)
**Visual:** Terminal demonstrates initializing a repo and tracking status:
```bash
developer@devasc:~/workspace/net226$ git init
Initialized empty Git repository in /home/developer/workspace/net226/.git/
developer@devasc:~/workspace/net226$ git status
On branch main
No commits yet
```
Animated overlay shows the Three Trees: Working Directory -> `git add` -> Staging Area -> `git commit` -> Repository History.
**Narration:**
> Git is the absolute source of truth for modern infrastructure. Every configuration change, every automation script, and every network policy must live in version control.
>
> Git operates across three local zones: your Working Directory where you edit files, the Staging Area where you craft snapshots, and the Repository where commits become permanent history.

---

## Scene 2 — Feature Branching (1:30–3:00)
**Visual:** Creating a feature branch and making a commit:
```bash
developer@devasc:~/workspace/net226$ git checkout -b feature/vlan-audit
Switched to a new branch 'feature/vlan-audit'
developer@devasc:~/workspace/net226$ git add src/vlan_parser.py
developer@devasc:~/workspace/net226$ git commit -m "feat: add initial VLAN parser module"
[feature/vlan-audit 4a8b1c2] feat: add initial VLAN parser module
 1 file changed, 45 insertions(+)
```
Git Graph visualizes the branch diverging from `main`.
**Narration:**
> Memorize this rule: never write code directly on the `main` branch.
>
> The `main` branch represents production-ready code. Whenever you build a new feature or fix a bug, branch off: `git checkout -b feature/vlan-audit`.
>
> Now you can experiment, make mistakes, and commit changes without touching the stable mainline.

---

## Scene 3 — Creating & Resolving a Merge Conflict (3:00–5:15)
**Visual:** Intentionally introducing conflicting edits in `config.py` on both `main` and `feature/vlan-audit`.
Attempting `git merge feature/vlan-audit`:
```bash
Auto-merging config.py
CONFLICT (content): Merge conflict in config.py
Automatic merge failed; fix conflicts and then commit the result.
```
VS Code opens `config.py` showing conflict markers:
- Current Change (`<<<<<<< HEAD`): `TIMEOUT = 10`
- Incoming Change (`>>>>>>> feature/vlan-audit`): `TIMEOUT = 30`
Clicking "Accept Incoming Change". Saving file. Running `git add config.py` and `git commit -m "merge: resolve timeout conflict"`.
**Narration:**
> Merge conflicts terrify beginners, but they are completely normal. A conflict simply means two branches edited the exact same line of code, and Git refuses to guess which one is right.
>
> Look at the conflict markers: `HEAD` shows what exists on your current branch. Below the equals divider is the incoming change from your feature branch.
>
> In VS Code, resolve it with a single click: accept current, accept incoming, or combine both. Save the file, stage it with `git add`, and commit. The conflict is resolved.

---

## Scene 4 — Wrap-Up (5:15–6:00)
**Visual:** Git log graph showing the clean merge commit back into `main`.
**Narration:**
> With Git mastered, you have a safe, auditable trail for all your automation. In our next video, we'll examine the three data formats that travel through our code: JSON, YAML, and XML.
