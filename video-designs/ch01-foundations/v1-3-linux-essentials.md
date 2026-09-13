---
video_id: V1.3
chapter: 1
title: "Linux Essentials for Network Engineers: Permissions, Navigation, Sockets"
composition_id: net226-v1-3-linux-essentials
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [terminal-split, permission-annotator]
objectives:
  - Navigate the Linux Filesystem Hierarchy Standard (FHS) relevant to network configs.
  - Calculate and enforce POSIX file permissions using octal notation (`chmod 600`, `chmod 755`).
  - Inspect active network socket listeners and interface bindings using `ss` and `ip`.
opens_with: cpcc-open
source_section: ch01 §1.4
---

# Video Design: V1.3 Linux Essentials for Network Engineers

---

## Scene 1 — Why Linux is the Network OS (0:00–1:00)
**Visual:** Clean terminal session. Typing `uname -a` to show the Linux kernel.
**Narration:**
> If you've worked in networking, you might think Linux is just for server administrators. But open up the hood of Cisco IOS XE, IOS XR, or Cisco NX-OS, and what do you find? A hardened Linux kernel.
>
> In fact, modern network automation scripts, Docker containers, and CI/CD pipelines all run natively in Linux. If you can't navigate the Linux filesystem or manage permissions, your automation will grind to a halt. Let's master the essential command line skills.

---

## Scene 2 — Directory Navigation & File Management (1:00–2:30)
**Visual:** Terminal demonstrates `pwd`, `ls -la /etc`, locating network configurations.
```bash
developer@devasc:~$ pwd
/home/developer
developer@devasc:~$ ls -ld /etc/network /var/log
drwxr-xr-x 2 root root 4096 Sep 10 14:02 /etc/network
drwxrwxr-x 8 root syslog 4096 Sep 12 18:00 /var/log
```
**Narration:**
> The Linux filesystem is a single hierarchical tree starting at root, denoted by a forward slash.
>
> Key directories you'll interact with: `/etc` holds system and network configurations. `/var/log` stores syslog and automation execution logs. Your user directory, `/home/developer`, is where all your repositories and code reside.

---

## Scene 3 — POSIX Permissions & Octal Calculations (2:30–4:30)
**Visual:** An annotated callout box breaks down a permission string:
`-rwxr-xr-- 1 developer netops 4096 audit.py`
Highlights:
- User: `rwx` = 4 + 2 + 1 = 7
- Group: `r-x` = 4 + 0 + 1 = 5
- Others: `r--` = 4 + 0 + 0 = 4
Terminal runs:
```bash
developer@devasc:~$ touch id_rsa_router && chmod 600 id_rsa_router
developer@devasc:~$ ls -l id_rsa_router
-rw------- 1 developer developer 0 Sep 12 19:40 id_rsa_router
```
**Narration:**
> File permissions protect automation credentials from unauthorized access. Every file has permissions for User, Group, and Others.
>
> Read has a numeric weight of four. Write is two. Execute is one.
>
> When you save an SSH private key for router access, SSH will reject the key if permissions are too loose. Running `chmod 600 id_rsa_router` grants read and write to you alone, and completely revokes access for everyone else. For automation scripts that need to be run by team members, `chmod 755` grants read and execute rights across the board.

---

## Scene 4 — Sockets, Processes, and Ports (4:30–6:00)
**Visual:** Executing socket and network inspection:
```bash
developer@devasc:~$ ss -tulpn
Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:Port Process
tcp   LISTEN 0      128    0.0.0.0:22          0.0.0.0:*         users:(("sshd",pid=912,fd=3))
tcp   LISTEN 0      10     127.0.0.1:5000      0.0.0.0:*         users:(("python3",pid=4102,fd=4))
developer@devasc:~$ ip -br addr
lo               UNKNOWN        127.0.0.1/8 ::1/128 
eth0             UP             192.168.1.105/24 fe80::a00:27ff:fe4e:66a1/64 
```
**Narration:**
> Before troubleshooting why an API script or web service isn't responding, check the local socket state.
>
> The `ss -tulpn` command lists all active TCP and UDP listening sockets along with their process IDs. Here, we confirm that our Python API service is listening on port 5000 bound to localhost, while OpenSSH listens on port 22.
>
> The `ip -br addr` command gives you an immediate, clean overview of your network interfaces and IP assignments. With these tools in hand, you're ready to inspect real network systems.
