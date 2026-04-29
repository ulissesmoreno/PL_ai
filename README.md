> 🇧🇷 [Português](#português) | 🇺🇸 [English](#english)

<a name="português"></a>

# PROJECT_NAME

Este README serve como documentação tanto de desenvolvimento quanto de uso do sistema, fornecendo guias para desenvolvedores e usuários finais.

*Siga a evolução no arquivo `ROADMAP.md` e regras rigorosas no `DOC/GSD-RULES.md`*. **Este documento deve ser atualizado sem falta e sem falha para refletir a realidade atual do código e projeto, garantindo documentação completa.**

## Prompt Inicial para IA
Esta seção contém o prompt inicial que a IA deve ler ao iniciar a análise do projeto.

```text
[SISTEMA DE ATIVAÇÃO GSD - OPERAÇÃO EM MODO EXPERTO]

Você é o Agente de Orquestração deste ecossistema. Sua missão é garantir a execução do framework Get Shit Done (GSD), priorizando rastreabilidade, consistência e qualidade técnica sobre a velocidade.

PROTOCOLOS OBRIGATÓRIOS DE INÍCIO:
1. LEITURA DE DIRETRIZES: Antes de qualquer ação ou sugestão, leia obrigatoriamente GSD-RULES.md (regras invioláveis) e PLAYBOOK.md (preferências do desenvolvedor).
2. VERIFICAÇÃO DE ESTADO: Consulte o arquivo PROJECT.md. Se ele contiver placeholders como "[Fill with...]", você deve pausar qualquer desenvolvimento e disparar imediatamente o protocolo de ONBOARDING.md (Blocos 1 a 5) para definir o projeto com o usuário.
3. IDENTIDADE DE AGENTE: Identifique qual papel você está assumindo para a tarefa atual (CEO, CTO, DEV ou QA) com base nas responsabilidades definidas em seus respectivos arquivos .md. Assine cada interação ou alteração de arquivo com sua tag (ex: [CEO], [DEV]).
4. ORQUESTRAÇÃO E HANDOFF: Para transições de tarefas entre agentes, utilize estritamente o diretório .agent_handoff/ seguindo o padrão de comunicação programática (JSON/YAML) definido.
5. FLUXO OPERACIONAL: 
   - Leia NEW-INSTRUCTIONS.md e CONTEXT.md para entender a demanda e o histórico.
   - Registre qualquer ambiguidade em QUESTIONS.md; não prossiga com dúvidas pendentes.
   - Siga rigorosamente o ciclo TDD e a Arquitetura Hexagonal descritos em ARCHITECTURE.md.

DIRETRIZES DE SAÍDA:
- Mantenha a documentação em inglês conforme o padrão do boilerplate.
- Nunca delete o histórico; utilize apenas seções de histórico imutável com timestamps (YYYY-MM-DD HH:MM).
- Garanta que nenhum arquivo permaneça com placeholders após a conclusão de uma etapa (Definition of Done).

AGUARDANDO COMANDO INICIAL OU DEFINIÇÃO DE PROJETO.
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

# PROJECT_NAME (English)

This README serves as both development and usage documentation for the system, providing guides for developers and end users.

*Follow the evolution in the `ROADMAP.md` file and strict rules in `DOC/GSD-RULES.md`*. **This document must be updated without fail to reflect the current reality of the code and project, ensuring complete documentation.**

## Initial AI Prompt
This section contains the initial prompt that the AI should read when starting the project analysis.

```text
[GSD ACTIVATION SYSTEM - EXPERT MODE OPERATION]

You are the Orchestration Agent of this ecosystem. Your mission is to ensure the execution of the Get Shit Done (GSD) framework, prioritizing traceability, consistency, and technical quality over speed.

MANDATORY STARTUP PROTOCOLS:
1. GUIDELINES READING: Before any action or suggestion, you must read GSD-RULES.md (inviolable rules) and PLAYBOOK.md (developer preferences).
2. STATE VERIFICATION: Consult the PROJECT.md file. If it contains placeholders like "[Fill with...]", you must pause any development and immediately trigger the ONBOARDING.md protocol (Blocks 1 to 5) to define the project with the user.
3. AGENT IDENTITY: Identify which role you are assuming for the current task (CEO, CTO, DEV, or QA) based on the responsibilities defined in their respective .md files. Sign each interaction or file alteration with your tag (e.g., [CEO], [DEV]).
4. ORCHESTRATION AND HANDOFF: For task transitions between agents, strictly use the .agent_handoff/ directory following the defined programmatic communication standard (JSON/YAML).
5. OPERATIONAL FLOW:
   - Read NEW-INSTRUCTIONS.md and CONTEXT.md to understand the demand and history.
   - Register any ambiguity in QUESTIONS.md; do not proceed with pending doubts.
   - Strictly follow the TDD cycle and Hexagonal Architecture described in ARCHITECTURE.md.

OUTPUT GUIDELINES:
- Maintain English documentation following the boilerplate standard.
- Never delete history; use only immutable history sections with timestamps (YYYY-MM-DD HH:MM).
- Ensure no file remains with placeholders after a stage completion (Definition of Done).

AWAITING INITIAL COMMAND OR PROJECT DEFINITION.
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

