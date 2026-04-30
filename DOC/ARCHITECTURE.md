# ARCHITECTURE.md -

## 1. System Overview
This system is xxx. It uses **Hexagonal Architecture (Ports & Adapters)** to ensure that the business core is resilient, testable, and fully independent of external technologies (such as market APIs or persistence frameworks).

## 2. Development Pillars (GSD Framework)
* **Get Shit Done (GSD):** Focus on functional delivery and high-impact executable code.
* **TDD (Test Driven Development):** Strict Red -> Green -> Refactor cycle before any commit.
* **Layered Security:** JWT implementation in the Backend and rigorous sanitization in Adapters.
* **SOLID:** Guarantee of extensible code for new ML models and technical indicators.

## 3. Layer Organization (Hexagonal)

### A. Domain (The Heart)
Located in `src/domain`. **Golden Rule:** Zero dependency on external libraries.
- **Entities:** .
- **Value Objects:** .
- **Domain Services:** Complex logic such as .

### B. Application (Use Cases)
Located in `src/application`. Orchestrates data flow between the external world and the domain.
- **Input Ports:** Command interfaces (e.g.: `IProcessMarketData`, `IRegisterTrade`).
- **Output Ports:** Need interfaces (e.g.: `IPriceRepository`, `INotificationService`).

### C. Infrastructure (Adapters)
Located in `src/infrastructure`. Technical implementation details.
- **Driving Adapters:** Spring REST Controllers, Cron Schedulers, CLI.
- **Driven Adapters:** PostgreSQL (JPA/SQL).

## 4. Technology Stack and Responsibilities

| Component | Technology | Responsibility | AI Engine |
| :--- | :--- | :--- | :--- |
| **Backend** | Java 21 / Spring Boot 3 | Rule orchestration, API Gateway and Security. | `[DEV_BACKEND]` |
| **Intelligence** | Python 3.12 / Scikit-Learn | Massive data capture, Technical Analysis and ML Modeling. | `[DEV_BACKEND]` |
| **Frontend Web** | Angular 18 / TypeScript | Reactive visualization and operations management via browser. | `[DEV_FRONTEND]` |
| **Mobile App (Hybrid)** | React Native / Expo *(optional)* | iOS and Android app with camera access, push notifications, and offline-first. | `[DEV_FRONTEND]` |
| **Mobile App (Native)** | Swift (iOS) / Kotlin (Android) *(optional)* | Maximum performance and hardware integration — biometrics, GPS, BLE, etc. | `[DEV_FRONTEND]` |
| **Desktop App** | Electron / Tauri *(optional)* | Cross-platform desktop client (Windows, macOS, Linux) with filesystem access. | `[DEV_FRONTEND]` |
| **Database** | PostgreSQL 16 | Central repository for prices, signals, and history. | `[CTO]` / `[DEV_BACKEND]` |
| **Security** | Spring Security + JWT | Stateless access control and permissions. | `[CTO]` / `[DEV_BACKEND]` |
| **Container** | Docker / Compose | Ecosystem orchestration in the Antigravity environment. | `[CTO]` |
| **Messaging** | Apache Kafka | Queue management for asynchronous processing and data decoupling. | `[DEV_BACKEND]` |
| **Cache** | Redis | Temporary storage and acceleration of volatile data access. | `[DEV_BACKEND]` |
| **Monitoring** | Prometheus + Grafana | Metrics collection, alerts, and dashboards for real-time observability. | `[CTO]` / `[QA]` |
| **CI/CD** | GitHub Actions | Build, test, and deploy automation for continuous delivery. | `[QA]` / `[CTO]` |
| **Skills & Tools** | Antigravity Skills + External | Skills catalog by domain and suggested tools (see GSD-RULES.md §9). | `[CEO]` / `[ALL]` |

## 4.1 Alternative Frontends — Decision Guide

The hexagonal architecture completely decouples the backend from its clients. The **primary** project uses Angular 18 as the web frontend, but the REST (or GraphQL) API layer allows integration with any other type of client without changes to the domain or use cases.

### 🌐 Web (Default)
| Technology | When to Use |
| :--- | :--- |
| **Angular 18 / TypeScript** | Admin dashboards, data panels, complex flows with forms and routing. |
| **React / Next.js** | Landing pages, SSR/SSG, larger component ecosystem. |
| **Vue / Nuxt** | Smaller teams, lower learning curve, medium-scope projects. |

### 📱 Mobile Hybrid *(recommended for mobile MVP)*
| Technology | When to Use |
| :--- | :--- |
| **React Native + Expo** | Share code between iOS and Android; fast launch; push notifications, camera, geolocation. Skills: `expo-dev-client`, `expo-deployment`. |
| **Flutter (Dart)** | High-fidelity custom UI; near-native performance; single team for both platforms. Skills: `flutter-expert`. |

### 📱 Mobile Native *(maximum performance and hardware integration)*
| Technology | When to Use |
| :--- | :--- |
| **Swift / SwiftUI (iOS)** | Biometrics, ARKit, HealthKit, deep integration with Apple ecosystem. Skills: `swiftui-ui-patterns`, `ios-developer`. |
| **Kotlin / Jetpack Compose (Android)** | Biometrics, advanced camera, Google services integration. Skills: `android_ui_verification`. |

### 🖥️ Desktop
| Technology | When to Use |
| :--- | :--- |
| **Electron** | Cross-platform desktop app reusing web code (Node.js + Chromium). |
| **Tauri (Rust)** | Lightweight and secure desktop app; smaller bundle than Electron; Rust backend. |
| **JavaFX / Swing** | Native integration with Java backend; corporate environment without external dependencies. |

> **Naming Rule (GSD-RULES §4.1):** Web frontend → `<name>-web`; mobile app → `<name>-app`; desktop → `<name>-desktop`; multiple microservices → `<name>-service`.

> **Agent Note:** When starting a new client, register the technology choice in `PROJECT.md` and evaluate available skills in the environment (see GSD-RULES §9) before starting implementation.

## 4.2 Agent Communication Schemas (.agent_handoff)
To ensure deterministic and programmatic handoff between specialized agents (CEO, CTO, DEV, QA), all files in the .agent_handoff/ directory must follow these structured schemas.

4.2.1. **General Handoff Header (Mandatory for all files)**
Every handoff file must include these identification and traceability fields:

    timestamp: YYYY-MM-DD HH:MM (GSD standard).
    sender: The tag of the agent initiating the handoff (e.g., [CEO], [DEV]).
    recipient: The tag of the target agent.
    task_ref: ID or link to the specific task in TASKS.md.
    intent: The objective of the communication (e.g., DELEGATION, REVIEW_REQUEST, TEST_VALIDATION, BUG_REPORT).

4.2.2. **Schema: Task Delegation (CEO → DEV)**
Used when the CEO moves a task from the roadmap to implementation.

    {
    "header": {
        "timestamp": "2026-04-30 16:20",
        "sender": "[CEO]",
        "recipient": "[DEV]",
        "task_ref": "TASK-001",
        "intent": "DELEGATION"
    },
    "payload": {
        "stage_ref": "ROADMAP.md#Phase-1",
        "plan_ref": "PLAN.md#Stage-1",
        "constraints": ["TDD mandatory", "Hexagonal isolation"],
        "priority": "High"
    }
    }

4.2.3. **Schema: Feature Validation (DEV → QA)**
Used when the developer finishes an implementation and requests a quality gate check.

    {
    "header": {
        "timestamp": "2026-04-30 18:45",
        "sender": "[DEV]",
        "recipient": "[QA]",
        "task_ref": "TASK-001",
        "intent": "TEST_VALIDATION"
    },
    "payload": {
        "artifacts": ["src/domain/entity/User.java", "src/infrastructure/adapter/UserRepo.java"],
        "test_file": "TESTS.md#Test-1",
        "coverage_report": "target/site/jacoco/index.html",
        "status": "Green"
    }
    }

4.2.4. **Schema: QA Report (QA → CEO/DEV)**
Used to approve a stage closure or report regressions.

    {
    "header": {
        "timestamp": "2026-04-30 20:10",
        "sender": "[QA]",
        "recipient": "[CEO]",
        "task_ref": "TASK-001",
        "intent": "STAGE_APPROVAL"
    },
    "payload": {
        "status": "PASSED",
        "checklist_validated": true,
        "security_scan": "SAST Clean",
        "observations": "Ready for Roadmap Phase 1 closure gate."
    }
    }

## 5. Data Flow (Data Lifecycle)

1. **Ingestion:**
2. **Processing:**
3. **Business:**
4. **Consumption:**

## 6. Machine Learning Optimization (Hardware-Specific Performance)
As the models will run exclusively on local hardware, the following performance premises are mandatory:
- **Parallel Processing:** Mandatory use of `n_jobs=-1` in compatible algorithms to exhaust all available CPU cores.
- **Memory Management:** Use of `Pandas` with optimized data types (e.g.: `float32`) and vectorized operations to avoid slow Python loops.
- **Batch Processing:** Bulk Insert persistence in PostgreSQL to avoid local network I/O bottlenecks.

## 7. Definition of "Done" (DoD)
The task is only considered complete if it meets the 5 requirements:
1. **Tests:** Unit and integration coverage validated.
2. **Security:** Protected routes and masked sensitive data.
3. **Documentation:** `README.md` reflecting the new code reality. **All documents (`PLAN.md`, `CONTEXT.md`, `QUESTIONS.md`, `tests.md`, etc.) must be filled without fail to ensure complete traceability.**
4. **Code:** Clean Code and SOLID patterns applied.
5. **STATE:** The `STATE.md` file must be updated with the current functionality snapshot for progress tracking.

## 8. Development Process
Before starting any roadmap stage, all tests must be written, covering functionality and security (following TDD). At the end of each stage, the developer must have access to a detailed step-by-step guide on how to test what was developed. Only after validating these tests can the next stage be performed, ensuring continuous quality and traceability.
