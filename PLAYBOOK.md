# PLAYBOOK.md — Developer Preferences & Working Style

> **Location:** By default this file lives at the project root alongside `README.md`.
> It is **project-agnostic** and belongs to the developer, not to any single project.
>
> **Shared setup (recommended):** Instead of copying this file to every project, you can place it
> in a **parent directory shared by all your projects** (e.g. `~/Projects/PLAYBOOK.md`).
> In that case, update the `README.md` reference from `PLAYBOOK.md` to `../PLAYBOOK.md`
> (or the appropriate relative path). This way a single file reflects your current preferences
> across all codebases simultaneously.
>
> **Immutability Rule:** This document is **append-only**.
> - Never delete or overwrite existing entries.
> - When a preference changes, add a new entry with a timestamp that supersedes the previous one.
> - The most recent entry for any topic is the active preference.
> - Format: `[YYYY-MM-DD HH:MM] — Entry`
>
> **When to Update (mandatory triggers):**
> 1. **After every answer in `QUESTIONS.md`** — if the answer reveals a preference, decision pattern, or working style.
> 2. **After every new entry in `NEW-INSTRUCTIONS.md`** — if new instructions reflect how the developer likes to work.
> 3. **After `PROJECT.md` is defined** — review and append any stack, architecture, or process choices that differ from or confirm existing entries.
>
> The agent must check this file at each of these triggers and append entries with timestamp *before* the Atomic Commit.

---


## 1. Working Philosophy

> *Core values that guide every project, regardless of stack or domain.*

| Timestamp | Principle | Notes |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **GSD (Get Shit Done)** — delivery over perfection, but quality by design. | Functional code ships. Untested code doesn't. |
| [2026-04-25 21:25] | **Traceability above speed.** Every decision, every question, every context must be documented. | Nothing lost. Nothing assumed. |
| [2026-04-25 21:25] | **Documentation is not optional.** If it's not documented, it doesn't exist. | All `.md` files must be complete before a stage is "Done". |
| [2026-04-25 21:25] | **Immutability of history.** Files are append-only. History is never erased. | Timestamps on all entries. |
| [2026-04-25 21:25] | **User controls the roadmap.** The AI agent proposes; the user approves before advancing. | No stage starts without explicit user OK. |

---

## 2. Architecture Defaults

> *Recurring architecture decisions I make when starting a new project.*

| Timestamp | Decision | Rationale |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Hexagonal Architecture (Ports & Adapters)** as default for any non-trivial system. | Testability, isolation, and independence from frameworks. |
| [2026-04-25 21:25] | **Domain layer has zero external dependencies.** No Spring, no Pandas, no ORMs in domain. | Pure business logic, maximally testable. |
| [2026-04-25 21:25] | **API routes born deny-all.** Security is not opt-in — every route requires explicit JWT release. | Security-first by default. |
| [2026-04-25 21:25] | **MVP planned before any implementation.** Even fully mapped projects need an MVP to validate hypotheses. | Avoids building the wrong thing. |
| [2026-04-25 21:25] | **Directory naming convention:** frontend → `<name>-web`, mobile → `<name>-app`, desktop → `<name>-desktop`, microservices → `<name>-service`. | Consistency across all projects. |

---

## 3. Tech Stack Defaults

> *My go-to technologies. New entries supersede old ones when preferences change.*

### 3.1 Backend
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Java 21 + Spring Boot 3** | Primary backend for rule orchestration, API gateway, and security. |
| [2026-04-29 20:35] | **C# / .NET** | Primary backend replacing Java for full CRUD and business rules in this project. |
| [2026-04-25 21:25] | **Python 3.12** | Data processing, ML pipelines, automation scripts. |

### 3.2 Frontend
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Angular 18 / TypeScript** | Default web frontend — dashboards, admin panels, complex forms. |
| [2026-04-25 21:25] | **React Native + Expo** | Preferred for mobile MVP (hybrid, iOS + Android). |
| [2026-04-29 20:35] | **React Native (Web e Mobile)** | Utilizado como frontend único (web e mobile) substituindo Angular. |

### 3.3 Database
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **PostgreSQL 16** | Default relational database. Central repository for all structured data. |

### 3.4 Infrastructure
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Docker + Docker Compose** | All dev environments containerized. No "works on my machine". |
| [2026-04-25 21:25] | **GitHub Actions** | Default CI/CD pipeline. |
| [2026-04-25 21:25] | **Apache Kafka** | Messaging and async decoupling when needed. |
| [2026-04-25 21:25] | **Redis** | Cache and volatile data acceleration. |

### 3.5 Observability
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Prometheus + Grafana** | Metrics collection, alerting, and dashboards. |

### 3.6 Security
| Timestamp | Choice | Context |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Spring Security + JWT** | Stateless auth. Default for all Java backends. |
| [2026-04-25 21:25] | **HashiCorp Vault / env vars** | Secrets never in files. Never committed. |

---

## 4. Development Process

> *How I like to work, step by step.*

| Timestamp | Rule | Detail |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **TDD — strict mode.** No production code without a prior failing test. | RED → GREEN → REFACTOR → SECURITY. |
| [2026-04-25 21:25] | **SOLID + Clean Code** applied in every refactor. | Semantic names. Single responsibility. No magic numbers. |
| [2026-04-25 21:25] | **Structured logs always.** INFO / WARN / ERROR. No sensitive data in logs. | Logs are auditable, not a security liability. |
| [2026-04-25 21:25] | **Stage Closure Gate** before advancing any roadmap phase. | Checklist of 8 files must be verified and confirmed by user. |
| [2026-04-25 21:25] | **`.env` is never committed.** All credentials in vault or local env vars. | ENV_SETUP.md guides configuration without exposing values. |
| [2026-04-25 21:25] | **Atomic commits.** One concern per commit. Conventional Commits format. | `feat`, `fix`, `docs`, `refactor`, `test`, `chore`. |
| [2026-04-29 20:35] | **Developer as Manager.** O desenvolvedor atua apenas como gerente do projeto. | Delegação integral da escrita de código, QA e arquitetura para os IAs. |
| [2026-04-29 21:07] | **Branching por ROADMAP Phase.** Cada fase rodará em uma branch isolada. | A Fase 0 é a única desenvolvida diretamente na `main`. As próximas criam PRs. |
| [2026-04-30 16:03] | **Git & Branching Strategy:** | Para cada nova fase do projeto, criar branch dedicada e realizar commits atômicos de estado. |

---

## 5. AI Agent Preferences

> *How I want the AI agent to behave when working with me.*

| Timestamp | Preference | Detail |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Read all docs before acting.** README, GSD-RULES, CONTEXT, NEW-INSTRUCTIONS — all before any code. | No assumptions. No undocumented actions. |
| [2026-04-25 21:25] | **Register all ambiguities in QUESTIONS.md.** Stop and ask instead of assuming. | Pending questions block execution. |
| [2026-04-25 21:25] | **Bilingual documentation by default** — PT as primary language, EN as mirror. | Both DOC/ and DOC/ must stay in sync. |
| [2026-04-25 21:25] | **Never skip the Stage Closure Checklist** before starting a new roadmap stage. | User approval is mandatory; verbal "go ahead" is not sufficient. |
| [2026-04-25 21:25] | **Skills first.** Check Antigravity environment skills before writing generic code. | Skills take precedence over generic knowledge. |
| [2026-04-25 21:25] | **Present options before creating.** For naming, structure, or ambiguous choices — suggest, don't decide alone. | Respects user's decision-making authority. |
| [2026-04-25 21:25] | **Concise responses.** Summary after completion; no repetition of what the user already knows. | Quality over verbosity. |
| [2026-04-29 20:59] | **No autonomous execution before approval.** | Preencher documentação de planejamento e aguardar autorização humana *explícita* antes de rodar qualquer comando no terminal ou alterar código fonte. |
| [2026-04-29 20:59] | **Native files over artifacts.** | Planejamentos devem ser preenchidos diretamente nos arquivos do projeto (ex: `PLAN.md`). Nunca gerar "Implementation_Plan.md" ou arquivos efêmeros via ferramenta da IDE. |
| [2026-04-30 16:03] | **Check for existing files.** | Não recriar arquivos que já existem; sempre procurar no diretório completo primeiro. |
| [2026-04-30 16:03] | **Correct file placement.** | Mover o conteúdo de arquivos gerados incorretamente para o local correto. |
| [2026-04-30 16:03] | **Agent & Target identification.** | Ao ler arquivos de documentação, identificar qual agente executará cada tarefa e os arquivos modificados. |
| [2026-04-30 16:03] | **Sync STATE and TASKS.** | Sempre atualizar `STATE.md` e `TASKS.md` para refletir mudanças decorrentes de novas instruções. |

---

## 6. Documentation Style

> *How I want documentation structured across all projects.*

| Timestamp | Preference | Detail |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | **Markdown everywhere.** All project documentation in `.md` files. | Versionable, portable, readable without tools. |
| [2026-04-25 21:25] | **Obsidian for maintenance wiki.** Vault opens at project root; `wiki/` and `raw/` directories. | See WIKI.md and ENV_SETUP.md §9 for setup. |
| [2026-04-25 21:25] | **Immutable history in all files.** Append-only. Timestamps on every entry. | Nothing is ever deleted — only superseded by newer entries. |
| [2026-04-25 21:25] | **DESIGN.md for visual decisions only.** No inspiration references in DESIGN.md — only the final aesthetic decisions. | Inspiration sources go to PROJECT.md if needed. |

---

## 7. Code Quality Gates

> *Non-negotiable quality thresholds.*

| Timestamp | Gate | Threshold |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | Unit test coverage — domain layer | ≥ 80% |
| [2026-04-25 21:25] | Integration tests | 100% passing before stage closure |
| [2026-04-25 21:25] | Routes without JWT return 401 | 100% |
| [2026-04-25 21:25] | Logs free of sensitive data | 100% |
| [2026-04-25 21:25] | Regressions on previous stages | 0 new failures |

---

## 8. Entry Log (Immutable)

> *Record of every addition to this PLAYBOOK. Never delete entries.*

| Timestamp | Author | Change |
| :--- | :--- | :--- |
| [2026-04-25 21:25] | Developer | Initial PLAYBOOK created. Sections 1–7 populated with baseline preferences from boilerplate project. |
| [2026-04-30 16:03] | Agente de IA | Adicionadas preferências de branching, verificação de arquivos e identificação de tarefas/agentes baseadas no NEW-INSTRUCTIONS.md. |

---

*To add new preferences: append a new row to the relevant section table with the current timestamp. Never edit or remove existing rows.*
