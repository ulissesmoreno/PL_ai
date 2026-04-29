# VERSIONS.md

This file documents project versioning and commit control. It must be updated with each release, delivery, or significant change, ensuring traceability of versions and changes.

## 1. Objective
- Register project versions and their main artifacts.
- Control the history of relevant commits/deliveries.
- Facilitate auditing and rollback of changes.

## 2. Versioning Convention
- Use [SemVer](https://semver.org/) whenever possible:
  - `MAJOR.MINOR.PATCH`
  - `MAJOR`: incompatible changes, large refactors, contract breaks.
  - `MINOR`: backward-compatible new features, architecture improvements.
  - `PATCH`: bug fixes, small adjustments, and quality improvements.
- For pre-releases, add a suffix: `1.0.0-alpha.1`, `1.0.0-beta.1`, etc.

## 3. Commit Control
- Use clear and structured commit messages.
- Suggested commit format:
  - `type(scope): short description`
  - Example: `feat(api): add data ingestion endpoint`
- Recommended types:
  - `feat`: new feature.
  - `fix`: bug fix.
  - `docs`: documentation.
  - `refactor`: refactoring without behavior change.
  - `test`: tests added or corrected.
  - `chore`: maintenance and infrastructure tasks.
- Always reference the plan or task file when applicable.
  - Example: `fix(api): fix JWT validation (PLAN.md Phase 1)`

## 4. Version Registry Structure
### [Version] - YYYY-MM-DD
- **Main Commit:** `hash` or reference message.
- **Description:** Summary of changes.
- **Main Files Changed:** [README.md, PLAN.md, etc.]
- **Tests / Validation:** Reference to `TESTS.md` and status.
- **Deploy / Environment Notes:** Required environment variables, release instructions.

## 5. Release History

### 1.1.0 - 2026-04-29
- **Main Commit:** boilerplate-finalization
- **Description:** Finalization of the GSD Boilerplate structure. Mapping and closure of all pending items from the initial TODO. Introduction of `ONBOARDING.md`, stabilization of `GSD-RULES.md`, wiki structure via Obsidian, and detailed frontend architecture.
- **Main Files Changed:** `TODO.md`, `GSD-RULES.md`, `ARCHITECTURE.md`, `ENV_SETUP.md`, `PLAYBOOK.md`, `ONBOARDING.md`, `WIKI.md`, `DESIGN.md`
- **Tests / Validation:** Structure validated through technical review sessions.
- **Deploy / Environment Notes:** The Boilerplate is consolidated for new projects.

### 1.0.0 - YYYY-MM-DD
- **Main Commit:** [hash or reference]
- **Description:** Initial boilerplate release with architecture structure and base documentation.
- **Main Files Changed:** `README.md`, `GSD-RULES.md`, `PROJECT.md`, `ROADMAP.md`, `TESTS.md`, `STATE.md`, `ENV_SETUP.md`
- **Tests / Validation:** [Reference to `TESTS.md`]
- **Deploy / Environment Notes:** [Specific release instructions]

## 6. Update Process
1. Update `VERSIONS.md` whenever a new version is published or when a significant delivery occurs.
2. Include the date, main commit, and change summary.
3. Keep history immutable: add new entries, do not delete old ones.
4. Align versioning with `ROADMAP.md`, `PLAN.md`, and `STATE.md`.

## 7. Additional Notes
- Use `VERSIONS.md` as the single source of truth for releases and significant changes.
- Do not register trivial text editing or formatting changes here unless they impact the project's behavior or flow.
- For smaller intermediate commits, maintain control in normal Git; use `VERSIONS.md` for milestones and deliveries.
