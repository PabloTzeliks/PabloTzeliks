<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=143478&height=120&section=header"/>

### Pablo Tzeliks

Desenvolvedor Back-End focado em Java e no ecossistema Spring, com interesse em sistemas distribuídos, arquitetura orientada a eventos e design de APIs. Construo projetos que me forçam a resolver problemas reais de engenharia — concorrência, consistência, tolerância a falhas — em vez de exercícios didáticos.

Atualmente sou aprendiz na **WEG**, cursando Desenvolvimento de Sistemas no CentroWEG. Acredito em *build in public*: os projetos abaixo estão todos com código, ADRs e issues visíveis.

💬 Sempre aberto a colaborar em projetos open-source e a conversar com a comunidade.

---

### 💻 Stack Principal

<p align="left">
  <a href="https://skillicons.dev">
    <img src="https://go-skill-icons.vercel.app/api/icons?i=java,spring,postgres,mysql,cassandra,redis" alt="Java, Spring, Postgres, MySQL, Cassandra, Redis e "/>
  </a>
</p>

<p align="left">
  <a href="https://skillicons.dev">
    <img src="https://go-skill-icons.vercel.app/api/icons?i=kafka,docker,aws,githubactions,git,linux" alt="Kafka, Docker, AWS, GitHub Actions, Git, Linux"/>
  </a>
</p>

Também trabalho com MySQL, TypeScript/Node.js e Python quando o projeto pede, tenho conhecimento sólido em Front-End também — mas meu foco de evolução em Back-End.

---

### 🚀 Projetos em Destaque

#### [Ciphernance — Core banking engine distribuído](https://github.com/PabloTzeliks/Ciphernance) &nbsp;·&nbsp; 🚧 em desenvolvimento ativo

Motor de core banking construído deliberadamente como exercício de engenharia distribuída de ponta a ponta. É onde saio da aplicação monolítica bem estruturada e começo a lidar com os problemas reais de topologia — consistência eventual, saga distribuída, cache em múltiplas camadas, autorização descentralizada.

**Arquitetura decidida (documentada em ADRs públicos):**
- **Seis microsserviços** com responsabilidades separadas por domínio: Identity, Account/Wallet, Transaction, Fraud, Audit e API Gateway.
- **Saga coreografada** em vez de orquestrada — escolhida para evitar um orquestrador central como ponto de acoplamento e falha, ao custo de rastreabilidade mais complexa (trade-off mitigado via Audit Service imutável).
- **Autorização eventualmente consistente via Policy Agents** distribuídos em cada serviço, com cache de duas camadas (Caffeine L1 local + Redis L2 compartilhado), sincronizados a partir do Identity Service via Kafka. Inspirado em XACML (PAP/PIP/PDP/PEP) mas com DSL ABAC própria em YAML.
- **Event Sourcing escopado ao Transaction Service** — aplicado onde o histórico imutável de eventos é requisito de domínio, não como padrão arquitetural genérico aplicado a tudo.
- **Modelagem de domínio** com User → Account(s) → Wallet(s) → Balance, com separação explícita entre estado de identidade (Identity Service) e estado financeiro (Wallet Service).

**Em execução agora:** Modelando Identity Service, com Clean e Hexagonal arch, aplicando CQRS, aprendendo sobre Eventos com Kafka e Agent Policy para o ABAC real com autorização por contexto, a real fonte da verdade do Sistema.

**Planejado:** implementação incremental dos serviços seguindo a ordem Identity → Wallet → Transaction → Fraud → Audit → Gateway, com Testcontainers cobrindo os contratos de integração entre eles.

**Stack:** Java 21, Spring Boot 4, Spring Cloud Gateway, Spring Authorization Server, Apache Kafka, PostgreSQL, Redis, Neo4j, Micrometer + Prometheus + Grafana, JUnit 5 + Testcontainers, Maven (monorepo).

📋 [GitHub Project público](https://github.com/PabloTzeliks/Ciphernance) com issues e ADRs acompanhando cada decisão.

---

#### [Time Trial System — Cronometragem distribuída em tempo real](https://github.com/PabloTzeliks/time-trial-api)

Sistema de telemetria e cronometragem de alta precisão para corridas, processando eventos vindos de hardware real (ESP32 + RFID) em tempo real. MVP funcional apresentado à supervisão da WEG.

**Decisões de engenharia:**
- **Arquitetura orientada a eventos.** Ingestão via broker MQTT desacopla o hardware do processamento — o cronômetro não cai se o back-end reiniciar.
- **Cluster Cassandra com 3 nodes e consistência Quorum.** Escolhido sobre um relacional por dois motivos: padrão de escrita dominante (eventos imutáveis de passagem) e necessidade de tolerar a queda de um nó sem perder leituras consistentes.
- **Distribuição instantânea de pódio via WebSockets**, permitindo que o front-end reaja a cada volta sem polling.
- **Saída RESTful** expondo os dados para análise posterior em Python (Machine Learning).
- Observabilidade com Prometheus + Grafana.

**Stack:** Java 21, Spring Boot 3, Apache Cassandra, MQTT, WebSockets, Docker, Prometheus, Grafana.

---

#### [BlinkLink — URL Shortener v3](https://github.com/PabloTzeliks/blink-link)

API REST para encurtamento de URLs, evoluída de um MVP simples até uma aplicação com IAM completo e garbage collection assíncrono. É o projeto onde exercito rigor de engenharia: testes, CI/CD, segurança e design de domínio.

**Decisões de engenharia:**
- **Organizado segundo Clean Architecture e DDD tático** — camadas de domínio, aplicação e infraestrutura bem separadas, com dependências apontando para dentro.
- **IAM stateless** com JWT em cookies HttpOnly (mitigando XSS), onboarding via OAuth2 com Google e GitHub, e controle de acesso por Roles (RBAC) combinado com Tiers de usuário.
- **Garbage Collection assíncrono** para URLs expiradas usando `SELECT ... FOR UPDATE SKIP LOCKED` do PostgreSQL, permitindo múltiplos workers concorrentes sem contenção.
- **Testes de integração com Testcontainers** rodando contra PostgreSQL real — não H2, não mocks — cobrindo os fluxos críticos de autenticação e o pipeline de expiração.
- **CI/CD** via GitHub Actions executando a suíte completa a cada push.

**Stack:** Java 21, Spring Boot 4, Spring Security, PostgreSQL, Flyway, Docker, Testcontainers, GitHub Actions.

---

### 📊 GitHub

<div align="center">
  <img height="180em" src="https://github-readme-stats-fast.vercel.app/api?username=PabloTzeliks&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide=commits"/>
  <img height="180em" src="https://github-readme-stats-fast.vercel.app/api/top-langs/?username=PabloTzeliks&layout=compact&theme=tokyonight"/>
</div>

<div align="center">
  <img src="https://github-readme-stats-fast.vercel.app/api/streak?username=PabloTzeliks&theme=tokyonight" alt="GitHub Streak" />
</div>

---

<h2 align="center">Conecte-se Comigo</h2>

<p align="center">
  <a href="https://www.linkedin.com/in/pablo-ruan-tzeliks" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="mailto:arq.pabloo@gmail.com" target="_blank">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
  </a>
</p>

  <h4 align="center">Sinta se a vontade a ver meus repositórios e projetos! Caso goste de algum, considere favorita-lo!</h4>
</p>

---

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=PabloTzeliks&style=flat-square&color=0077B5" alt="Contador de Visitas"/>
</p>
