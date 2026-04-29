# ENV_SETUP.md

This file contains instructions for configuring the development and production environment. **All credentials must be stored securely (e.g.: environment variables, vaults); never in files.** Reference: GSD-RULES.md 7.5.

## 1. Prerequisites
- **Operating System:** [E.g.: Windows/Linux/Mac]
- **Tools:** [Install list, e.g.: JDK 21, Python 3.12, Node.js]
- **Hardware:** [Requirements, e.g.: Multi-core CPU for ML]

## 2. Stack Installation
- **Backend (Java/Spring):** [Steps: Download JDK, Maven/Gradle]
- **Intelligence (Python):** [Steps: Install Python, pip, virtualenv]
- **Frontend (Angular):** [Steps: Install Node.js, npm, Angular CLI]
- **Database (PostgreSQL):** [Steps: Install PostgreSQL, create DB]
- **Container (Docker):** [Steps: Install Docker, Docker Compose]
- **Others:** [E.g.: Redis, Kafka - see PROJECT.md]

## 3. Environment Variables
Configure the following variables (do not commit real values):
- `DB_URL`: [E.g.: jdbc:postgresql://localhost:5432/dbname]
- `DB_USER`: [Placeholder]
- `DB_PASSWORD`: [Placeholder - store in vault]
- `JWT_SECRET`: [Placeholder - secure key]
- `API_KEY_EXTERNAL`: [E.g.: For market APIs - store in vault]
- `REDIS_URL`: [If applicable]
- `LOG_LEVEL`: [E.g.: INFO]

## 3.1 AI Agents Configuration
Configure the API keys and models for the specific agent roles:
- `CEO_AGENT_MODEL`: [E.g.: gpt-4-turbo / claude-3-opus]
- `CTO_AGENT_MODEL`: [E.g.: gpt-4-turbo / claude-3-opus]
- `DEV_FRONT_AGENT_MODEL`: [E.g.: claude-3-sonnet / gpt-4o]
- `DEV_BACK_AGENT_MODEL`: [E.g.: claude-3-sonnet / gpt-4o]
- `QA_AGENT_MODEL`: [E.g.: claude-3-haiku / gpt-3.5]
- `AI_API_KEY`: [Placeholder - secure key for LLM access]

**How to Configure:** Use local `.env` (do not commit) or system env vars. For production, use secrets managers.

## 4. Keys and Credentials
- **Secure Storage:** Use vaults (e.g.: AWS Secrets, HashiCorp Vault) or encrypted env vars.
- **Developer Instructions:** [E.g.: Request keys from the security responsible; register in QUESTIONS.md if questions.]
- **Validation:** Test connections without exposing logs (see GSD-RULES.md 7.6).

## 5. Local Environment Configuration
1. Clone the repo.
2. Run `docker-compose up` to bring up DB and services.
3. Configure env vars as per section 3.
4. Run builds: [E.g.: `./mvnw clean install` for Java, `npm install` for Angular]
5. Validate: [E.g.: Test DB connection, run basic tests]

## 6. Production Configuration
- **Deploy:** [E.g.: Use Docker images, CI/CD]
- **Secrets:** Configure via platform (e.g.: Kubernetes secrets)
- **Monitoring:** Integrate Prometheus/Grafana as per ARCHITECTURE.md

## 7. Validations
- Functional environment: [Steps to test]
- Security: [Verify JWT, sanitization]
- Performance: [E.g.: Test with ML data]
- Record results in TESTS.md.

## 8. Troubleshooting
- **Common Error 1:** [Description and solution]
- Register questions in QUESTIONS.md.

---
*Reminder: Update this file according to changes in PROJECT.md or ARCHITECTURE.md.*

## 9. Obsidian — Project Maintenance Wiki

The project uses **Obsidian** as a local wiki tool for maintenance documentation. Notes live in the `wiki/` (maintained pages) and `raw/` (immutable sources) directories at the project root. See `DOC/WIKI.md` for the full protocol.

### 9.1 Installation

1. Go to [https://obsidian.md](https://obsidian.md) and download the installer for your OS.
2. Install normally (no account required — Obsidian works 100% locally).

### 9.2 Opening the Vault

1. Open Obsidian.
2. Click **"Open folder as vault"**.
3. Select the **project root** (the directory containing `wiki/`, `raw/`, `DOC/`, etc.).
   - This ensures `[[wiki-link]]` links between pages work correctly.
4. Obsidian will automatically create the `.obsidian/` folder at the root (local settings).

### 9.3 Recommended .gitignore Entries

Add to the project's `.gitignore` to avoid committing personal Obsidian settings:
```
.obsidian/workspace
.obsidian/workspace.json
.obsidian/plugins/
```
> **Do not ignore** `.obsidian/app.json` and `.obsidian/appearance.json` if you want to share basic settings with the team.

### 9.4 Recommended Plugins (Community Plugins)

| Plugin | Purpose |
| :--- | :--- |
| **Dataview** | Dynamic queries in wiki pages (e.g.: list all known bugs). |
| **Templater** | Automatic templates for new wiki documents (GSD format). |
| **Git** | Automatic commit of notes directly from Obsidian. |
| **Tag Wrangler** | Tag management to categorize wiki pages. |

> To install: `Settings → Community Plugins → Browse`.

### 9.5 Usage Workflow

1. Open the vault in Obsidian pointing to the project root.
2. Navigate the wiki at `wiki/index.md`.
3. To add maintenance documentation, create pages in `wiki/`.
4. To ingest external sources (PDFs, reports), place them in `raw/` and ask the Agent.
5. Always update `wiki/log.md` with a timestamp after changes (GSD immutability standard).

