# LLM Rules & Development Standards

A consolidated repository of structured, sane software development processes designed for LLM-driven engineering. This repo serves as the central source of truth for all LLM agents (Claude, Cursor, Gemini) working across my projects.

## 🎯 Desired Agent Outcomes

Agents adhering to these rules should consistently deliver:
- **High-Autonomy Progress:** Completing complex, multi-step tasks with minimal human intervention.
- **Surgical Code Changes:** Implementing precise, elegant solutions that solve root causes without side effects.
- **Empirical Reliability:** Every change is backed by passing tests, verified logs, and documented proof of correctness.
- **Structural Integrity:** Adherence to established patterns (GitFlow, containerization, architectural layers) without deviation.
- **Compound Learning:** A decreasing error rate over time as the agent captures and integrates "lessons learned" into its workflow.

## 🔍 What These Rules Include

These rules represent a synthesis of industry-standard best practices and project-specific successful patterns:
- **Architectural Guidance:** Instructions for domain-driven design, multi-agent collaboration, and strict service isolation.
- **Operational Protocols:** Step-by-step workflows for planning, executing, and validating software changes.
- **Git & GitHub Standards:** Mandatory use of GitFlow and `gh` CLI for professional-grade repository management.
- **Quality Gates:** Hard requirements for testing, linting, and security (zero-secret commitment policy).
- **Communication Standards:** Rules for high-signal, professional communication that focuses on technical rationale.
- **Anti-Failure Patterns:** Explicit blocks against common AI pitfalls like dummy data, hallucination, and "lazy" band-aid fixes.

## 📋 Table of Contents

1. [Core Principles](./01_CORE_PRINCIPLES.md) - Senior mindset and autonomous execution.
2. [Workflow](./02_WORKFLOW.md) - Plan-first strategies and task management.
3. [Git Flow](./03_GIT_FLOW.md) - Branching models and GitHub CLI integration.
4. [Development Standards](./04_DEVELOPMENT_STANDARDS.md) - Personas, containerization, and security.
5. [Testing & Validation](./05_TESTING_AND_VALIDATION.md) - Mandatory verification and bug-fixing protocols.
6. [Self-Improvement](./06_SELF_IMPROVEMENT.md) - Continuous learning and lessons-learned loops.
7. [Documentation](./07_DOCUMENTATION.md) - Minimalist, high-signal documentation standards.

## 🚀 How to Use These Rules

### For New Projects
1. Copy the `PROJECT_TEMPLATE.md` to the root of your new project as `CLAUDE.md`.
2. Reference this repository in the "Rules" section of the project's `CLAUDE.md`.
3. Ensure the project includes a `tasks/` directory for `todo.md` and `lessons.md`.

### For Existing Projects
Add the following directive to your project's `.clauderules` or `CLAUDE.md`:
> "Follow the engineering standards and workflows defined in [gr33ngiant112/llmrules](https://github.com/gr33ngiant112/llmrules)."

## 🛠 Core Tooling
These rules assume the availability and expert use of:
- **Git & GitHub CLI (`gh`)**: For all source control and PR management.
- **Docker & Docker Compose**: For consistent local environments.
- **Modern Test Runners**: (Pytest, Go Test, Vitest, etc.) for mandatory validation.

## 🔄 The Lessons Loop
One of the most critical aspects of these rules is the **Lessons Learned Loop** defined in [06_SELF_IMPROVEMENT.md](./06_SELF_IMPROVEMENT.md). Whenever an agent receives a correction, it must update `tasks/lessons.md` to prevent the mistake from recurring.
