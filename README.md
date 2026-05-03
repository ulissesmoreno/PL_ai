> 🇧🇷 [Português](#português) | 🇺🇸 [English](#english)

<a name="português"></a>
## 📝 Visão Geral do Projeto
O **PF_ai** é um ecossistema de desenvolvimento assistido por inteligência artificial fundamentado no framework **GSD (Get Shit Done)**. Diferente de repositórios convencionais, este projeto utiliza uma arquitetura de múltiplos agentes (**CEO, CTO, DEV, QA**) para garantir que a construção de software seja realizada com rastreabilidade total, consistência arquitetural e qualidade técnica rigorosa.

### ⚠️ Aviso de Boilerplate
**Este documento e todos os arquivos deste repositório representam uma estrutura base (Boilerplate) no estado `v1.1.0`.** 
Todas as informações, tecnologias, descrições e objetivos listados são modelos genéricos. **Tudo será alterado e personalizado** assim que o projeto for formalmente iniciado através do protocolo de **Onboarding**. O estado real do sistema será definido pela interação inicial entre o usuário e o Agente de Orquestração.

---

## 🤖 Prompt Inicial para IA (Ignition Protocol)
*Esta seção contém as instruções mestre que a IA deve ler para assumir o controle dos agentes e iniciar qualquer atividade.*

```text
[SISTEMA DE ATIVAÇÃO GSD - OPERAÇÃO MODO EXPERT]
Você é o Agente de Orquestração do PF_ai. Sua missão é garantir a execução do framework Get Shit Done (GSD), priorizando rastreabilidade, consistência e qualidade técnica em detrimento da velocidade.
PROTOCOLOS OBRIGATÓRIOS DE INÍCIO:

    1. LEITURA DE DIRETRIZES: Você deve ler o GSD-RULES.md e o PLAYBOOK.md antes de qualquer ação para se alinhar aos padrões técnicos e preferências do desenvolvedor.
    2. PRECEDÊNCIA DO CEO E GATILHO: Cada novo ciclo ou sessão de trabalho começa exclusivamente após o usuário humano enviar o sinal [USER_DONE] no chat. O Agente CEO deve ser o primeiro a agir, realizando a leitura obrigatória de NEW-INSTRUCTIONS.md e PLAN.md para resolver ambiguidades de negócio antes de qualquer delegação.
    3. VERIFICAÇÃO DE ESTADO: Se o PROJECT.md contiver placeholders (campos não preenchidos), acione imediatamente o protocolo ONBOARDING.md. Nenhum desenvolvimento começa sem uma visão de projeto 100% populada.

IDENTIDADES DOS AGENTES E HIERARQUIA: Assuma o papel específico exigido pela tarefa atual e assine cada ação com sua tag (ex: [CEO], [CTO]). Siga o fluxo hierárquico estabelecido: CEO → BA → CTO → Agentes Técnicos:

    - [CEO]: Orquestração de alto nível, gestão do roadmap e processamento inicial das instruções do usuário.
    - [BA]: Detalhamento de regras de negócio (PLAN.md §5), critérios de aceitação e manutenção de manuais na WIKI.
    - [CTO]: Guardião arquitetural, análise de skills (ambiente Antigravity) e distribuição de tarefas técnicas.
    - [DEV] / [DBA] / [DS/ML] / [SECURITY]: Execução técnica, implementação TDD e otimização de infraestrutura.
    - [QA] / [REVISOR]: Porta de qualidade, validação de testes (TESTS.md) e aprovação do fechamento de estágio (Stage Closure Gate).

ORQUESTRAÇÃO E HANDOFF:

    - Handoff Programático: Todas as transições entre agentes DEVEM usar arquivos JSON/YAML estruturados salvos no diretório .agent_handoff/ (ignorado pelo git).
    - Matriz de Cobertura de Contexto: Antes de concluir um estágio, o agente responsável deve validar a leitura de seus arquivos atribuídos (ex: CEO lê docs estratégicos, CTO lê docs arquiteturais) conforme definido no STATE.md.

FLUXO OPERACIONAL:

    - Leia NEW-INSTRUCTIONS.md e CONTEXT.md.
    - Resolva ambiguidades em QUESTIONS.md (A execução é bloqueada por perguntas pendentes).
    - Siga o ciclo TDD (Red-Green-Refactor) e o isolamento da Arquitetura Hexagonal.
    - Atualize o "cérebro" do projeto no STATE.md após cada entrega.

DIRETRIZES DE SAÍDA:

    - Estritamente Inglês: Toda a documentação e comentários de código devem ser feitos apenas em Inglês e/ou outro idioma a pedido do usuário.
    - Histórico Imutável: Nunca delete informações; adicione novas entradas com timestamps (YYYY-MM-DD HH:MM).
    - Definição de "Pronto" (DoD): Sem placeholders, 100% de testes validados no TESTS.md e aprovação do Checklist de Fechamento de Estágio pelo usuário.
```

## Descrição do Projeto
- **Nome do Projeto:** `PROJECT_NAME`
- **Descrição:** [Descrição concisa do projeto, baseada no PROJECT.md. Ex.: Plataforma de análise de dados financeiros com machine learning para previsão e visualização de sinais.]
- **Objetivo:** [Resumo do propósito, ex.: validar hipóteses de negócio com MVP antes de avançar para expansão.]
- **Público-Alvo:** [Quem usa o sistema, ex.: analistas financeiros, traders, equipe interna.]

## Instalação
1. **Pré-requisitos:**
   - Java 21
   - Python 3.12
   - Angular 18 / Node.js
   - PostgreSQL 16
   - Docker / Docker Compose
2. **Clone o Repositório:**
   - `git clone [url]`
   - `cd [nome-do-projeto]`
3. **Configure o Ambiente:**
   - Consulte [ENV_SETUP.md](ENV_SETUP.md) para variáveis de ambiente e credenciais seguras.
   - Siga as instruções em [NEW_PROJECT_PROMPT.md](NEW_PROJECT_PROMPT.md) para ajustar tecnologias ao projeto.
4. **Execute:**
   - `docker-compose up`
   - [Comandos adicionais de build, ex.: `./mvnw clean install`, `npm install`, `npm start`]

## Uso do Sistema
- **Acesso ao Frontend:** [Ex.: http://localhost:4200]
- **APIs:** [Ex.: `POST /api/v1/analyze`, `GET /api/v1/status`]
- **Principais Funcionalidades:**
  - Ingestão de dados de mercado
  - Processamento e análise via ML
  - Visualização de resultados e sinais
  - Segurança via JWT

## Desenvolvimento
- **Arquitetura:** Consulte [ARCHITECTURE.md](ARCHITECTURE.md) para a arquitetura hexagonal, camadas, e componentes sugeridos.
- **Processo GSD:** Siga [GSD-RULES.md](DOC/GSD-RULES.md). Planeje o MVP no início, escreva testes antes de qualquer implementação e use `NEW-INSTRUCTIONS.md` para ajustes posteriores.
- **Estrutura de Diretórios:** Antes de criar diretórios backend/frontend/microservices, valide a estrutura e os nomes. Para soluções web, o frontend deve ser nomeado como `<nome-abreviado>-web`; para apps use lógica apropriada ao projeto; múltiplos microserviços devem usar `<nome>-service`; monólitos podem usar apenas o nome abreviado.
- **Registro de Dúvidas:** Todas as questões devem ser registradas em [QUESTIONS.md](QUESTIONS.md). Não inicie ações com dúvidas pendentes.
- **Configurações Sensíveis:** Não armazene senhas ou chaves em arquivos. Use [ENV_SETUP.md](ENV_SETUP.md) para orientação de ambiente seguro.
- **Skills & Ferramentas:** O ambiente Antigravity possui skills instaladas e ferramentas sugeridas. Consulte a seção 9 de [GSD-RULES.md](DOC/GSD-RULES.md) para o catálogo completo de skills por domínio e recomendações de ferramentas externas (linting, SAST, performance, observabilidade, etc.).
- **Preferências do Desenvolvedor:** Consulte [PLAYBOOK.md](PLAYBOOK.md) para preferências, decisões recorrentes e estilo de trabalho do desenvolvedor responsável. Este arquivo é agnóstico de projeto e viaja entre projetos.

## Testes
- **Obrigatórios:** Testes de funcionalidade e de segurança antes de cada etapa.
- **Documentação de testes:** Use [TESTS.md](TESTS.md) para registrar resultados, passos e validações.
- **Execução:**
  - Java: `./mvnw test` ou `mvn test`
  - Python: `pytest`
  - Frontend: `npm test`
- **Log de atividades:** Toda ação da solução deve possuir logs para rastreabilidade de atividades e erros (ver [DOC/GSD-RULES.md](DOC/GSD-RULES.md)).

## Roadmap e Estado
- **Acompanhamento:** Use [ROADMAP.md](ROADMAP.md) para acompanhar o desenvolvimento.
- **Progresso:** Consulte [STATE.md](STATE.md) para o estado atual e próximos passos.
- **Validação:** O `PLAN.md` valida o plano da etapa; o `ROADMAP.md` acompanha o progresso de execução.

## Contribuição
1. Leia [DOC/GSD-RULES.md](DOC/GSD-RULES.md) e [NEW_PROJECT_PROMPT.md](NEW_PROJECT_PROMPT.md).
2. Preencha `PROJECT.md` antes de iniciar a implementação.
3. Registre dúvidas em [QUESTIONS.md](QUESTIONS.md).
4. Siga TDD e atualize `TESTS.md`, `STATE.md`, `ROADMAP.md` e `README.md` após cada entrega.

## Licença
[Placeholder para licença]

## Contato
[Placeholder para contato]

---

<a name="english"></a>

# PF_ai (English)

Project Overview
PF_ai is an AI-assisted development ecosystem based on the GSD (Get Shit Done) framework. Unlike conventional repositories, this project utilizes a multi-agent architecture (CEO, CTO, DEV, QA) to ensure that software construction is performed with total traceability, architectural consistency, and rigorous technical quality.
⚠️ Boilerplate Notice
This document and all files in this repository represent a base structure (Boilerplate) in version v1.1.0. All information, technologies, descriptions, and objectives listed below are generic templates. Everything will be changed and customized once the project is formally started through the Onboarding protocol.

--------------------------------------------------------------------------------
## 🤖 Initial AI Prompt (Ignition Protocol)
This section contains the master instructions for the AI agents.
```text
[GSD ACTIVATION SYSTEM - EXPERT MODE OPERATION]
You are the Orchestration Agent of PF_ai. Your mission is to ensure the execution of the Get Shit Done (GSD) framework, prioritizing traceability, consistency, and technical quality over speed.
MANDATORY START PROTOCOLS:

    1. GUIDELINE READING: You must read GSD-RULES.md and PLAYBOOK.md before any action to align with technical standards and developer preferences.
    2. CEO PRECEDENCE & TRIGGER: Every new cycle or work session starts exclusively after the human user sends the [USER_DONE] signal in the chat. The CEO Agent must be the first to act, performing a mandatory reading of NEW-INSTRUCTIONS.md and PLAN.md to resolve business ambiguities before delegation [43, 50, Histórico].
    3. STATE CHECK: If PROJECT.md contains placeholders, immediately trigger the ONBOARDING.md protocol. No development starts without a 100% populated project vision.

AGENT IDENTITIES & HIERARCHY: Assume the specific role required by the current task and sign every action with your tag (e.g., [CEO], [CTO]). Follow the established Hierarchical Flow: CEO → BA → CTO → Technical Agents [10, 16, 33, 90, Histórico]:

    - [CEO]: High-level orchestration, roadmap management, and initial user instruction processing.
    - [BA]: Business rules detailing (PLAN.md §5), acceptance criteria, and user manual maintenance in the WIKI [69, 70, Histórico].
    - [CTO]: Architectural guardian, skill analysis (Antigravity environment), and technical task distribution.
    - [DEV] / [DBA] / [DS/ML] / [SECURITY]: Technical execution, TDD implementation, and infrastructure optimization [33, 48, Histórico].
    - [QA] / [REVISOR]: Quality gate, test validation (TESTS.md), and Stage Closure approval.

ORCHESTRATION & HANDOFF:

    - Programmatic Handoff: All transitions between agents MUST use structured JSON/YAML files saved in the .agent_handoff/ directory (ignored by git).
    - Context Coverage Matrix: Before completing a stage, the responsible agent must validate the reading of their assigned files (e.g., CEO reads Strategic docs, CTO reads Architectural docs) as defined in STATE.md [119, Histórico].

OPERATIONAL FLOW:

    - Read NEW-INSTRUCTIONS.md and CONTEXT.md.
    - Resolve ambiguities in QUESTIONS.md (Execution is blocked by pending questions).
    - Follow the TDD cycle (Red-Green-Refactor) and Hexagonal Architecture isolation.
    - Update the project "brain" in STATE.md after every delivery.

EXIT GUIDELINES:

    - Strictly English: All documentation and code comments must be written only in English and/or another language at the user's request..
    - Immutable History: Never delete information; append with timestamps (YYYY-MM-DD HH:MM).
    - Definition of "Done" (DoD): No remaining placeholders, 100% validated tests in TESTS.md, and user approval of the Stage Closure Checklist.
```

## Project Description
- **Project Name:** `PROJECT_NAME`
- **Description:** [Concise project description, based on PROJECT.md. E.g.: Financial data analysis platform with machine learning for signal prediction and visualization.]
- **Objective:** [Purpose summary, e.g.: validate business hypotheses with MVP before advancing to expansion.]
- **Target Audience:** [Who uses the system, e.g.: financial analysts, traders, internal team.]

## Installation
1. **Prerequisites:**
   - Java 21
   - Python 3.12
   - Angular 18 / Node.js
   - PostgreSQL 16
   - Docker / Docker Compose
2. **Clone the Repository:**
   - `git clone [url]`
   - `cd [project-name]`
3. **Configure the Environment:**
   - Refer to [ENV_SETUP.md](DOC/ENV_SETUP.md) for environment variables and secure credentials.
   - Follow the instructions in [NEW_PROJECT_PROMPT.md](NEW_PROJECT_PROMPT.md) to adjust technologies to the project.
4. **Run:**
   - `docker-compose up`
   - [Additional build commands, e.g.: `./mvnw clean install`, `npm install`, `npm start`]

## System Usage
- **Frontend Access:** [E.g.: http://localhost:4200]
- **APIs:** [E.g.: `POST /api/v1/analyze`, `GET /api/v1/status`]
- **Main Features:**
  - Market data ingestion
  - Processing and analysis via ML
  - Results and signals visualization
  - Security via JWT

## Development
- **Architecture:** Refer to [ARCHITECTURE.md](DOC/ARCHITECTURE.md) for hexagonal architecture, layers, and suggested components.
- **GSD Process:** Follow [GSD-RULES.md](DOC/GSD-RULES.md). Plan the MVP at the beginning, write tests before any implementation, and use `NEW-INSTRUCTIONS.md` for later adjustments.
- **Directory Structure:** Before creating backend/frontend/microservices directories, validate the structure and names. For web solutions, the frontend should be named `<abbreviated-name>-web`; for apps use appropriate project logic; multiple microservices should use `<name>-service`; monoliths can use just the abbreviated name.
- **Issue Tracking:** All questions must be registered in [QUESTIONS.md](DOC/QUESTIONS.md). Do not start actions with pending questions.
- **Sensitive Configurations:** Do not store passwords or keys in files. Use [ENV_SETUP.md](DOC/ENV_SETUP.md) for secure environment guidance.
- **Skills & Tools:** The Antigravity environment has installed skills and suggested tools. Refer to section 9 of [GSD-RULES.md](DOC/GSD-RULES.md) for the complete skills catalog by domain and external tool recommendations (linting, SAST, performance, observability, etc.).
- **Developer Preferences:** See [PLAYBOOK.md](PLAYBOOK.md) for the responsible developer's preferences, recurring decisions, and working style. This file is project-agnostic and travels across projects.

## Testing
- **Mandatory:** Functionality and security tests before each stage.
- **Test Documentation:** Use [TESTS.md](DOC/TESTS.md) to record results, steps, and validations.
- **Execution:**
  - Java: `./mvnw test` or `mvn test`
  - Python: `pytest`
  - Frontend: `npm test`
- **Activity Logging:** Every system action must have logs for activity and error traceability (see [GSD-RULES.md](DOC/GSD-RULES.md)).

## Roadmap and State
- **Tracking:** Use [ROADMAP.md](DOC/ROADMAP.md) to track development.
- **Progress:** Refer to [STATE.md](DOC/STATE.md) for the current state and next steps.
- **Validation:** `PLAN.md` validates the stage plan; `ROADMAP.md` tracks execution progress.

## Contributing
1. Read [GSD-RULES.md](DOC/GSD-RULES.md) and [NEW_PROJECT_PROMPT.md](NEW_PROJECT_PROMPT.md).
2. Fill in `PROJECT.md` before starting implementation.
3. Register questions in [QUESTIONS.md](DOC/QUESTIONS.md).
4. Follow TDD and update `TESTS.md`, `STATE.md`, `ROADMAP.md`, and `README.md` after each delivery.

## License
[License placeholder]

## Contact
[Contact placeholder]

