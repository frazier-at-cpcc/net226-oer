---
video_id: V6.2
chapter: 6
title: "Containerizing Network Automation: Authoring Clean Multi-Stage Dockerfiles"
composition_id: net226-v6-2-containerizing-automation
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [dockerfile-editor, terminal-docker-build]
objectives:
  - Author an optimized, production-ready `Dockerfile` for a Python automation service.
  - Utilize layer caching techniques to achieve rapid sub-second build times.
  - Build, execute, and verify container port redirection (`-p 8080:5000`).
opens_with: cpcc-open
source_section: ch06 §6.3
---

# Video Design: V6.2 Containerizing Network Automation

---

## Scene 1 — The Anatomy of a Dockerfile (0:00–1:30)
**Visual:** VS Code opens an empty `Dockerfile`. Live typing instructions:
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY src/ ./src/
EXPOSE 5000
CMD ["python", "src/main.py"]
```
**Narration:**
> A `Dockerfile` is an automated recipe that builds a container image. Let's dissect the essential instructions:
>
> `FROM python:3.11-slim`: Always use lean official base images rather than bloated full OS distributions.
>
> `WORKDIR /app`: Establishes our working directory inside the container.
>
> Notice the order on lines three and four: we copy `requirements.txt` and install dependencies *before* copying our source code. Why? Docker caches image layers. If you only edit Python code, Docker reuses the cached dependency layer, building your image in half a second!

---

## Scene 2 — Building the Container Image (1:30–3:00)
**Visual:** Terminal executes `docker build`:
```bash
developer@devasc:~/workspace$ docker build -t net-automation:v1 .
[+] Building 4.2s (10/10) FINISHED
 => [internal] load build definition from Dockerfile
 => => naming to docker.io/library/net-automation:v1
developer@devasc:~/workspace$ docker images
REPOSITORY        TAG       IMAGE ID       SIZE
net-automation    v1        3a9b1c4e7f20   142MB
```
**Narration:**
> We run `docker build -t net-automation:v1 .`. Docker executes each instruction, creating an immutable, cryptographically hashed image layer.
>
> When the build finishes, `docker images` shows our complete application packaged into a 142-megabyte self-contained image.

---

## Scene 3 — Running with Port Redirection (3:00–4:30)
**Visual:** Executing `docker run` with port mapping:
```bash
developer@devasc:~$ docker run -d -p 8080:5000 --name audit-service net-automation:v1
8f4b2c1d9e...
developer@devasc:~$ docker ps
CONTAINER ID   IMAGE                COMMAND                  STATUS          PORTS
8f4b2c1d9e     net-automation:v1   "python src/main.py"     Up 5 seconds    0.0.0.0:8080->5000/tcp
developer@devasc:~$ curl http://localhost:8080/health
{"status": "healthy", "service": "network-change-automation"}
```
**Narration:**
> By default, containers run in an isolated network namespace. To access our Python API service from outside, we use the `-p` flag: `8080:5000`.
>
> This tells Docker: forward traffic arriving on host port 8080 through NAT to container port 5000.
>
> We test with `curl http://localhost:8080/health`, and the containerized microservice responds instantly.

---

## Scene 4 — Hardening & Best Practices (4:30–6:00)
**Visual:** Adding `USER appuser` to avoid running as root inside the container.
**Narration:**
> In enterprise environments, never run containers as root. Add a non-privileged system user to your Dockerfile to ensure that if the application is compromised, the attacker cannot escape to the host kernel.
>
> In our next video, we'll automate the testing and building of this container in a continuous integration pipeline.
