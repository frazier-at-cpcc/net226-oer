---
video_id: V2.3
chapter: 2
title: "Evaluating Third-Party Code: Currency, Security, and Deprecation Audits"
composition_id: net226-v2-3-resource-evaluation
duration_target: "4:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [code-audit-diff, security-scanner-ui]
objectives:
  - Audit open-source network automation scripts for security flaws and hardcoded secrets.
  - Identify deprecated API paths and verify semantic version compatibility.
  - Review open-source license compliance (MIT, Apache 2.0).
opens_with: cpcc-open
source_section: ch02 §2.4
---

# Video Design: V2.3 Evaluating Third-Party Code

---

## Scene 1 — The Trap of the Stale Gist (0:00–1:00)
**Visual:** VS Code opens a downloaded third-party script named `cisco_backup.py` found on a 2017 blog. Red highlights flag multiple problematic lines.
**Narration:**
> Searching for network automation scripts will lead you to countless blogs and GitHub gists. But copying and pasting unverified scripts into your enterprise environment is an immense security and operational risk.
>
> Let's perform a professional 4-point audit on this script before running it.

---

## Scene 2 — Point 1 & 2: Currency and API Deprecation (1:00–2:15)
**Visual:** Code inspection zooms in on an API call:
`url = "https://api.meraki.com/api/v0/organizations"`
A callout highlights `/api/v0/` with a yellow warning tag.
**Narration:**
> Check the API version path. Notice this script calls `/api/v0/`. Meraki deprecated version 0 years ago. Running this script today returns a 404 or 410 Gone error.
>
> Check the repository's commit history. If the last commit was five years ago, treat the code as an unmaintained artifact that must be refactored to current API standards.

---

## Scene 3 — Point 3: Credential Hygiene & Insecure SSL (2:15–3:15)
**Visual:** Red boxes highlight two critical security vulnerabilities:
`API_KEY = "6c95...88f1"` (Hardcoded secret)
`response = requests.get(url, verify=False)` (Disabled TLS check)
**Narration:**
> Point three: security hygiene. Look at line twelve: the developer hardcoded their production API token directly in plain text. If this file is committed to Git, that token is compromised.
>
> Look at line eighteen: `verify=False`. Disabling SSL verification suppresses warning messages, but it disables TLS certificate validation and exposes your network traffic to man-in-the-middle interception. Never disable TLS verification in production.

---

## Scene 4 — Point 4: Licensing & Safe Refactoring (3:15–4:00)
**Visual:** Refactoring the script in VS Code to load from `os.environ` and enable TLS. Inspecting the `LICENSE` file for MIT or Apache 2.0 terms.
**Narration:**
> Finally, verify the license. Permissive licenses like MIT and Apache 2.0 allow commercial modification and integration.
>
> Always refactor third-party code: remove hardcoded tokens, use environment variables, and re-enable TLS verification. With an audited foundation, you're ready to scope your own project.
