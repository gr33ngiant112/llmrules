# Git Flow & GitHub Standards

## 1. Strict Git Flow
- **Main:** Production-ready code only.
- **Develop:** Main integration branch for local development.
- **Feature Branches:** `feature/<name>` cut from `develop`.
- **Release Branches:** `release/<version>` for stabilization.
- **Hotfix Branches:** `hotfix/<name>` for urgent production fixes.

## 2. GitHub CLI (`gh`) Integration
- Use `gh` CLI for all pull requests and GitHub-related interactions.
- `gh pr create` for all completed features.
- Auto-merge is authorized ONLY IF all automated tests and schema validations pass.

## 3. Commit & PR Quality
- Use descriptive commit messages following project conventions.
- Provide a high-level summary of changes at each step.
- Ensure all PRs are linked to relevant issues or features.

## 4. Versioning & Changelog
- Use Semantic Versioning (SemVer) strictly.
- Maintain a `CHANGELOG.md` at the root.
- Log all features, bug fixes, and breaking changes with version tags.

## 5. Documentation
- Use GitFlow tags for releases (e.g., `v1.0.0`).
- Ensure `main` and `develop` are kept in sync via proper release/hotfix merge-backs.
