---
video_id: V6.4
chapter: 6
title: "Securing Network Applications: Secrets Management and OWASP Top 10"
composition_id: net226-v6-4-secrets-and-owasp
duration_target: "5:00"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss, lucide-icons]
blocks: [cpcc-open, owasp-threat-radar, injection-exploit-demo]
objectives:
  - Demonstrate command injection vulnerabilities in network tools and design mitigations.
  - Implement zero-trust secrets management across development, CI, and production.
  - Identify the OWASP Top 10 web vulnerabilities relevant to network APIs.
opens_with: cpcc-open
source_section: ch06 §6.5 & 6.6
---

# Video Design: V6.4 Securing Network Applications

---

## Scene 1 — The Exposed Secret Disaster (0:00–1:15)
**Visual:** A simulated GitHub search showing automated bot scanners discovering an API key in a public commit within 20 seconds. An alert flashes: "Cisco Catalyst Center admin token leaked."
**Narration:**
> Automated bot scanners crawl public repositories every second of every day. If you commit an API token, an enable secret, or an SSH private key to GitHub, that secret is scraped within seconds.
>
> Even if you delete the file in a subsequent commit, Git's immutable history preserves the secret forever.
>
> In this video, we master secrets management hygiene and defend our automation against the OWASP Top 10.

---

## Scene 2 — The Secrets Management Pipeline (1:15–2:30)
**Visual:** A 3-stage animated secrets pipeline:
1. **Local Development:** `.env` file containing local tokens, explicitly listed inside `.gitignore`.
2. **CI/CD Testing:** GitHub Actions Encrypted Secrets (`secrets.CISCO_API_TOKEN`) injected into runner memory at execution time.
3. **Production Containers:** Injected as environment variables via container orchestrators, never baked into Docker image layers.
**Narration:**
> Follow the three-tier secrets pipeline:
>
> In local development, store secrets in a `.env` file and verify that `.env` is listed inside your `.gitignore`.
>
> In your CI pipeline, store tokens in GitHub Encrypted Secrets, injecting them into runner memory as environment variables.
>
> And in production containers, inject secrets at runtime. Never, under any circumstances, use `ENV` in a Dockerfile to store credentials—anyone who downloads your image can extract them with `docker history`.

---

## Scene 3 — Command Injection in Action (2:30–4:00)
**Visual:** Animated code walkthrough demonstrating a naive Python network diagnostics script:
```python
# VULNERABLE:
user_input = "10.10.20.48; cat /etc/shadow"
os.system("ping -c 1 " + user_input)
```
The shell executes the ping, followed by the malicious appended command, dumping system credentials.
Refactoring to secure parameter lists:
```python
# SECURE:
subprocess.run(["ping", "-c", "1", user_ip], shell=False, check=True)
```
**Block:** `injection-exploit-demo`
**Narration:**
> The most critical OWASP vulnerability in network automation is Command Injection.
>
> Look at this naive ping utility. If you concatenate user input directly into `os.system()`, an attacker can append a semicolon and execute arbitrary shell commands on your server.
>
> To defend against injection, never invoke the shell. Use Python's `subprocess.run()` with `shell=False`, passing arguments as a strict list of tokens.

---

## Scene 4 — Takeaway (4:00–5:00)
**Visual:** Summary checklist: TLS 1.3, `.gitignore`, parameterized commands, non-root containers.
**Narration:**
> Security is not something you add at the end of a project; it must be designed into every line of code.
>
> In Chapter 7, we will scale our automation across the entire enterprise using Ansible.
