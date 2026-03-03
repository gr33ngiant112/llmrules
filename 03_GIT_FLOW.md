# Git Flow & GitHub Standards

## 1. Strict Git Flow
- **Main:** Production-ready code only. Receives merges ONLY from `release/*` and `hotfix/*` branches.
- **Develop:** Main integration branch. `develop` MUST be set as the GitHub default branch so that PRs target it by default. After creating a repo, always run `gh repo edit --default-branch develop`.
- **Feature Branches:** `feature/<name>` cut from `develop`, merged back to `develop`.
- **Release Branches:** `release/<version>` cut from `develop` for stabilization, merged to both `main` and `develop`.
- **Hotfix Branches:** `hotfix/<name>` cut from `main` for urgent production fixes, merged to both `main` and `develop`.

## 2. GitHub CLI (`gh`) Integration
- Use `gh` CLI for all pull requests and GitHub-related interactions.
- `gh pr create` for all completed features.
- Auto-merge is authorized ONLY IF all automated tests and schema validations pass.

## 3. Commit & PR Quality
- Use descriptive commit messages following project conventions.
- Provide a high-level summary of changes at each step.
- Ensure all PRs are linked to relevant issues or features.

**Conventional commit prefixes:**
- `feat:` — New feature (triggers MINOR version bump)
- `fix:` — Bug fix (triggers PATCH version bump)
- `refactor:` — Code restructure, no behavior change (PATCH or no bump)
- `docs:` — Documentation only (no version bump unless standalone release)
- `chore:` — Build, CI, tooling changes (no version bump unless standalone release)
- `test:` — Adding/updating tests (no version bump unless standalone release)
- `BREAKING CHANGE:` in commit body or `!` after type (e.g., `feat!:`) — triggers MAJOR bump

## 4. Semantic Versioning (SemVer 2.0.0)

All releases MUST follow [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html). Format: **`MAJOR.MINOR.PATCH`** (e.g., `1.2.3`).

**When to bump:**
- **MAJOR** — Incompatible API changes, breaking schema migrations, removed endpoints, changed response shapes that break consumers
- **MINOR** — New features, new API endpoints, new UI pages/sections, new database migrations that are additive (backwards compatible)
- **PATCH** — Bug fixes, typo corrections, performance improvements, dependency updates — all backwards compatible

**Reset rules:**
- Bumping MAJOR resets MINOR and PATCH to 0 (e.g., `1.9.3` → `2.0.0`)
- Bumping MINOR resets PATCH to 0 (e.g., `1.2.5` → `1.3.0`)

**Pre-release versions** (optional, for release candidates):
- Append with hyphen: `1.0.0-alpha`, `1.0.0-beta.1`, `1.0.0-rc.1`
- Pre-release versions have lower precedence than the release (`1.0.0-alpha` < `1.0.0`)

**Build metadata** (optional):
- Append with plus sign: `1.0.0+20260303`, `1.0.0-alpha+001`
- Build metadata is ignored when determining version precedence

**Immutability rule:**
- Once a version is tagged and released, its contents MUST NOT be modified — any fix requires a new version

**GitFlow integration:**
- Every merge to `main` MUST be tagged `v{MAJOR}.{MINOR}.{PATCH}` (e.g., `v1.1.0`)
- `release/<version>` branches carry the target version; only PATCH-level fixes allowed after branch cut
- `hotfix/<name>` branches from `main` always produce a PATCH bump, merged back to both `main` and `develop`
- `feature/*` branches merge to `develop`; version is determined when cutting the release branch
- Tags MUST use `v` prefix: `v1.0.0`, not `1.0.0`

**CHANGELOG.md:**
- Every version tag MUST have a corresponding entry in `CHANGELOG.md`
- Use [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) format: Added, Changed, Fixed, Removed
- Unreleased changes go under `## [Unreleased]` until the release branch is cut
- Maintain a `CHANGELOG.md` at the root of the project

## 5. Documentation
- Use GitFlow tags for releases (e.g., `v1.0.0`).
- Ensure `main` and `develop` are kept in sync via proper release/hotfix merge-backs.
