---
video_id: V2.4
chapter: 2
title: "Scoping the Automation Project: User Stories, Acceptance Criteria, and Backlogs"
composition_id: net226-v2-4-project-scoping
duration_target: "4:30"
aspect: "16:9"
engine: hyperframes
libraries: [gsap, tailwindcss]
blocks: [cpcc-open, agile-board-animated, user-story-card, kanban-swimlanes]
objectives:
  - Translate an enterprise business problem into Agile user stories.
  - Author testable acceptance criteria using the "Given-When-Then" formula.
  - Structure the 5 milestones of the Network Change Automation capstone project.
opens_with: cpcc-open
source_section: ch02 §2.5
---

# Video Design: V2.4 Scoping the Automation Project

---

## Scene 1 — The Customer Problem: Campus-A (0:00–1:00)
**Visual:** An animated enterprise campus map titled 'Campus-A Regional Network'. Callouts highlight manual configuration bottlenecks, missing audit logs, and inconsistent VLAN assignments across distribution switches.
**Narration:**
> Meet your customer for this semester: Campus-A.
>
> Campus-A is expanding its regional facilities. Their network operations team is overwhelmed by repetitive manual tasks: provisioning standardized VLANs, auditing switch interfaces, and verifying device health during emergency changes.
>
> Your mission across the next seven weeks is to design, build, test, and demonstrate an authentic **Network Change Automation Service**.

---

## Scene 2 — Crafting Precise User Stories (1:00–2:15)
**Visual:** An animated User Story card flips onto the screen:
"As a [Role] / I want [Capability] / So that [Business Benefit]"
Fills in:
"As a Network Operations Engineer / I want an automated Python audit script / So that manual errors are eliminated and VLAN compliance is verified across distribution switches."
**Block:** `user-story-card`
**Narration:**
> Software engineering begins with clear requirements. We express requirements as user stories.
>
> A user story answers three fundamental questions: Who wants this? What do they want to do? And why does it matter to the business?
>
> Writing user stories prevents you from getting lost in technical weeds and keeps your focus on delivering measurable operational value.

---

## Scene 3 — Defining Acceptance Criteria: Given-When-Then (2:15–3:30)
**Visual:** Acceptance criteria breakdown card appears:
- **GIVEN:** A target switch inventory in YAML format.
- **WHEN:** The automation script runs against the target device.
- **THEN:** It asserts that VLANs 10, 20, and 99 exist, and outputs a structured JSON report.
Green checkmarks land beside each condition.
**Narration:**
> How do you know when a user story is finished? By defining unequivocal acceptance criteria using the 'Given-When-Then' formula:
>
> GIVEN the initial system context—such as our target router inventory file.
>
> WHEN the specific action occurs—such as running our Python audit tool.
>
> THEN the observable outcome must match our expectation—such as verifying VLAN state and producing a structured audit report.
>
> If a requirement cannot be tested objectively, it is not ready for development.

---

## Scene 4 — The 5 Milestone Roadmap (3:30–4:30)
**Visual:** A modern Kanban board displays the 5 milestone columns advancing through the course weeks, highlighting Milestone 1 for submission this week.
**Block:** `kanban-swimlanes`
**Narration:**
> For Project Milestone 1 due this week, you will formulate your project charter, write three core user stories with acceptance criteria, and establish your project backlog.
>
> In Chapter 3, you'll open your personal Git repository and write your first tested Python module. Let's get building!
