---
video_id: V6.3
chapter: 6
title: "Automating Quality: Building a CI Pipeline with GitHub Actions"
composition_id: net226-v6-3-ci-pipeline-actions
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [actions-yaml-editor, live-pipeline-run]
objectives:
  - Author a GitHub Actions Continuous Integration workflow in YAML.
  - Automate Python unit test execution upon code commits and pull requests.
  - Configure the pipeline to build a Docker container image only after tests pass.
opens_with: cpcc-open
source_section: ch06 §6.4
---

# Video Design: V6.3 Automating Quality with CI

---

## Scene 1 — Why Continuous Integration? (0:00–1:00)
**Visual:** Diagram of broken code slipping into production without automated tests vs. a CI pipeline stopping bad commits at the gate.
**Narration:**
> What happens when an engineer pushes an untested change to a shared repository at 5:00 PM on a Friday? Production breaks.
>
> Continuous Integration, or CI, solves this by automatically spinning up an isolated virtual runner on every Git push, installing dependencies, and running all unit tests. If a single test fails, the build turns red and the pull request cannot be merged.

---

## Scene 2 — Authoring the Workflow YAML (1:00–2:45)
**Visual:** VS Code opens `.github/workflows/ci.yml`. Typing instructions:
```yaml
name: Network Automation CI

on:
  push:
    branches: [ main, feature/* ]
  pull_request:
    branches: [ main ]

jobs:
  test-and-build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v3

      - name: Set up Python 3.11
        uses: actions/setup-python@v4
        with:
          python-version: "3.11"

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Run unit tests
        run: python -m unittest discover -s tests

      - name: Build Docker image
        run: docker build -t net-service:${{ github.sha }} .
```
**Narration:**
> GitHub Actions workflows live inside `.github/workflows/`.
>
> We define triggers: run on pushes to `main` or feature branches, and on pull requests.
>
> In our job steps: we checkout the code, provision Python 3.11, install dependencies, and run `unittest discover`.
>
> Notice that the Docker build step appears at the very end. If a unit test fails, the pipeline halts immediately—zero broken containers are ever compiled.

---

## Scene 3 — Watching the Pipeline Execute Live (2:45–4:30)
**Visual:** Committing the workflow and pushing to GitHub:
```bash
git add .github/workflows/ci.yml
git commit -m "ci: add automated unit testing and container build workflow"
git push origin feature/ci-setup
```
Browser opens GitHub Actions tab. The workflow triggers automatically. Live logs stream in: spinning up Ubuntu runner, installing packages, running unit tests (all green checkmarks), building Docker container.
**Block:** `live-pipeline-run`
**Narration:**
> We push our commit, and within three seconds, GitHub Actions triggers our workflow.
>
> Watch the live console logs: GitHub allocates a clean virtual machine in the cloud, executes our test suite, and builds our container. All steps pass with green checkmarks.
>
> You now have automated quality gates protecting your network code.

---

## Scene 4 — Milestone 4 Guidance (4:30–5:30)
**Visual:** Reviewing the Milestone 4 submission requirements.
**Narration:**
> For Milestone 4 this week, submit your working Dockerfile, your GitHub Actions workflow, and a screenshot of your passing pipeline run.
>
> Next, let's look at how to secure your network applications and defend against the OWASP Top 10.
