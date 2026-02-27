# LLM Rules & Development Standards

A consolidated repository of structured, sane software development processes designed for LLM-driven engineering. This repo serves as the central source of truth for all LLM agents (Claude, Cursor, Gemini) working across my projects.

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
