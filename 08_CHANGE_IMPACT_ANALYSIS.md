# Change Impact Analysis

Every change exists in a dependency graph. A regression is what happens when you modify a node without updating its dependents. The fix is not "be more careful" — it's a repeatable process that makes regressions structurally difficult to introduce.

## 1. The Dependency Principle

No change is isolated. A file, function, config value, schema column, or API endpoint exists because other things reference it. Moving, renaming, deleting, or altering its behavior without tracing those references is the single most common source of regressions.

**Before touching anything, answer: "What depends on this?"**

## 2. Blast Radius Mapping

Before executing a change, map its blast radius — the set of all things that could break.

**Process:**
1. Identify the artifact being changed (file, path, function, config key, schema, endpoint, etc.).
2. Search the entire codebase for references to that artifact. Use grep, LSP find-references, or AST search — not memory.
3. Search configuration and build files separately (these are often missed): `Dockerfile`, `docker-compose.yml`, `.dockerignore`, `Makefile`, CI configs, `package.json` scripts, `pyproject.toml`, `setup.py`, `.env`, nginx configs.
4. Document the dependency list: "Artifact X is referenced by A, B, C."
5. Plan updates to every dependent in the same change.

**The search is not optional.** Skipping it because a change "seems isolated" is exactly how regressions happen.

## 3. Common Dependency Types

These are the categories of references that silently break when their target changes:

| Change Type | What Typically Depends On It |
|---|---|
| **File move/rename** | Imports, `COPY` in Dockerfile, docker-compose paths, CI configs, README references, scripts, `.dockerignore` patterns |
| **Config key change** | Application code reading that key, `.env.example`, documentation, deployment scripts, docker-compose `environment:` blocks |
| **API endpoint change** | Frontend fetch calls, integration tests, API docs, reverse proxy configs (nginx), external consumers |
| **Database schema change** | ORM models, raw queries, migration scripts, seed data, backup/restore scripts, API serializers |
| **Dependency add/remove** | `requirements.txt`, `package.json`, lock files, Dockerfile install steps, CI caching, `setup.py`/`pyproject.toml` |
| **Port change** | docker-compose port mappings, nginx upstream, healthchecks, firewall rules, documentation, env vars |
| **Build artifact change** | `.dockerignore`, `.gitignore`, CI artifacts, deployment scripts, volume mounts |
| **Environment variable change** | `.env`, `.env.example`, docker-compose, CI secrets, documentation, application defaults |

## 4. The Exclusion Inversion Check

Build systems that use exclusion lists (`.dockerignore`, `.gitignore`, `.npmignore`) are especially dangerous because they fail silently — the file just isn't there at runtime.

**Rule: After any change to an exclusion file, cross-check every source that gets copied, published, or deployed against the exclusion list.** For Docker specifically:
- List every `COPY` source in the Dockerfile.
- Verify none are matched by `.dockerignore` patterns.
- Remember that patterns like `*.md` or `lib/` match at any directory depth unless root-anchored with `/`.

## 5. The Atomic Commit Rule

All dependents must be updated in the same commit as the change that affects them. If you move a file in one commit and update its references in the next, you've created a window where the codebase is broken. Anyone who pulls, builds, or deploys between those commits gets a regression.

**One logical change = one commit, including all dependent updates.**

## 6. The Pre-Change Checklist

Execute this before every non-trivial change:

```
1. IDENTIFY: What artifact am I changing? (file, path, config, schema, endpoint)
2. SEARCH:   What references this artifact? (grep the entire project — code, configs, docs, CI, Docker)
3. SEARCH:   What exclusion lists affect this artifact? (.dockerignore, .gitignore, .npmignore)
4. LIST:     Write down every dependent found.
5. PLAN:     For each dependent, what update is needed?
6. VERIFY:   After making all changes, re-search to confirm zero remaining stale references.
7. TEST:     Build/run/test to confirm nothing is missing at runtime.
```

## 7. Why "Be More Careful" Doesn't Work

"Be more careful" is not a process — it's a hope. Regressions don't happen because of carelessness; they happen because of invisible dependencies. The human (or agent) making the change doesn't know what they don't know.

The fix is mechanical: **search before you change, verify after you change.** No amount of experience substitutes for actually grepping the codebase. The dependency graph is the source of truth, not your mental model of it.
