# Pablo Tzeliks

Desenvolvedor de software Back-End. Java, Spring, sistemas distribuídos. Jaraguá do Sul, Brasil.

Construo sistemas deliberadamente complexos para entendê-los por dentro — consistência eventual, saga distribuída, autorização descentralizada, design de domínio. Não busco a solução mais simples. Busco a que force o problema de engenharia real.

**Disponível a partir de agosto de 2026.**

[pablotzeliks.github.io](https://pablotzeliks.github.io/pablotzeliks-portfolio) · [linkedin.com/in/pablo-ruan-tzeliks](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)

---

## Projetos Pessoais

### [Ciphernance](https://github.com/PabloTzeliks/Ciphernance) · em desenvolvimento ativo

Motor de core banking construído para entender sistemas distribuídos por dentro. O domínio bancário não foi escolhido arbitrariamente — é um dos poucos domínios onde saga, autorização descentralizada e event sourcing têm que coexistir porque consistência, rastreabilidade e segurança são requisitos do negócio, não opções arquiteturais. Nenhum desses padrões foi adicionado por interesse acadêmico; todos foram forçados pelo domínio.

Seis microsserviços coordenados por choreography-based saga. Quinze ADRs documentam cada decisão antes do código ser escrito.

**Decisões que definem o sistema:**

— **Choreography sobre Orchestration (ADR 01).** Um orquestrador central cria acoplamento e ponto único de falha. A coreografia aceita rastreabilidade mais complexa como custo — mitigado pelo Audit Service imutável que captura a cadeia de eventos completa.

— **ABAC eventualmente consistente com Policy Agents distribuídos (ADR 02).** Cada serviço hospeda um agente com cache em duas camadas (Caffeine L1 local + Redis L2 compartilhado). Atualizações de política partem do Identity Service via Kafka. O trade-off — uma janela de inconsistência na avaliação de políticas — está documentado e aceito deliberadamente.

— **Event Sourcing escopado ao Transaction Service (ADR 03).** Aplicado onde o histórico imutável de transações é requisito do domínio — saldo derivado do histórico, não armazenado como coluna. Não como padrão genérico aplicado ao sistema todo.

**Status atual:** Identity Service em desenvolvimento. Domínio modelado além dos agregados User e Account; trabalho em andamento na estrutura de políticas ABAC — DSL YAML como fonte única da verdade para autorização, com agentes em cada serviço recebendo atualizações via Kafka.

**Stack:** Java 21, Spring Boot 4, Apache Kafka, PostgreSQL, Redis, Neo4j, Micrometer + Prometheus + Grafana, JUnit 5 + Testcontainers, Maven (monorepo).

[Repositório](https://github.com/PabloTzeliks/Ciphernance) — código, ADRs e roadmap públicos.

---

### [BlinkLink](https://github.com/PabloTzeliks/blink-link) · v3 disponível · v4 em desenvolvimento

URL shortener reconstruído quatro vezes — não por insatisfação com a versão anterior, mas porque cada iteração foi o veículo para um problema específico de engenharia. A simplicidade do domínio é proposital: o foco está no rigor da solução, não na complexidade do negócio.

**v3 — o que foi construído:**

— IAM stateless com JWT em cookies HttpOnly (mitigando XSS), OAuth2 com Google e GitHub, controle de acesso por Roles (RBAC) combinado com Tiers de usuário.

— Garbage collection assíncrono para URLs expiradas com `SELECT ... FOR UPDATE SKIP LOCKED` — múltiplos workers concorrentes sem contenção de lock.

— Testes de integração com Testcontainers rodando contra PostgreSQL real — não H2, não mocks. CI/CD via GitHub Actions executando a suíte completa a cada push.

**v4 — em construção:**

— Camada de cache Redis com estratégia cache-aside e alinhamento de TTL entre cache e banco.

— Rate limiting por usuário e por endpoint.

— Refatoração da base com Spring Modulith — modularização explícita sem migração para microsserviços.

— Banco colunar para o módulo de Analytics, com ingestão via Kafka.

— Primeiro deploy real na AWS.

**Stack:** Java 21, Spring Boot 4, Spring Security, Spring Modulith, PostgreSQL, Redis, Apache Kafka, Flyway, Docker, Testcontainers, GitHub Actions.

---

## Aprendizado — CentroWEG/SENAI

Programa industrial de 3.200 horas dentro da WEG, agosto de 2024 a julho de 2026. O currículo oferece amplitude; a profundidade construo nos projetos, levando cada problema além do que o escopo do curso exige.

Ao longo do programa, liderei ou co-liderei quatro projetos com decisões de engenharia reais:

**InfoWEG** · Plataforma de comunicação interna com entrega segmentada por perfil de usuário. Product Owner e Tech Lead do projeto de classe. Java, Spring Boot, MySQL.

**SynapseRH** · Sistema de recrutamento com motor de matchmaking por habilidades. Tech Lead e Lead Backend Developer em equipe de cinco pessoas — cerca de 80 issues gerenciadas. Arquitetura em quatro camadas com DDD explícito, Value Objects no domínio (Email, CPF, Endereço, Senha), Strategy Pattern na camada de apresentação, algoritmo de matchmaking com pontuação ponderada. Apresentado a painel externo de RH. Java 21, PostgreSQL, JDBC, MapStruct.

**Time Trial System** · Plataforma de telemetria IoT em tempo real com hardware físico (ESP32 + RFID). Tech Lead e Arquiteto. Saímos do stack esperado pelo curso — Node-RED com MySQL — e reconstruímos o problema com arquitetura orientada a eventos. Ingestão via MQTT, Cassandra em cluster de 3 nós com consistência QUORUM, resultados em tempo real via WebSocket, análise em Python com K-Means. Demo ao vivo para Professores e Supervisores de diferentes áreas do CentroWEG. Java 21, Spring Boot 3, Docker.

**Payment Gateway Core** · Estudo comparativo entre duas implementações paralelas do mesmo gateway — uma deliberadamente caótica, uma deliberadamente rigorosa. Co-desenvolvedor. Na implementação limpa: transaction manager ACID customizado via `ThreadLocal` + JDBC sem Spring, Execute Around Pattern para centralizar o ciclo de vida das conexões, Event Sourcing para derivar saldo do histórico imutável de transações, ~80% de cobertura entre testes unitários, de integração e end-to-end. Java 21.

---

## Atualmente

Concluindo o aprendizado na WEG. Nos últimos meses:

- Praticando CQRS, Event Sourcing, Sagas Coreografadas, Caching e Rate Limiting
- Lendo *Fundamentals of Software Architecture: An Engineering Approach*
- Estudando Kafka, autorização baseada em atributos (ABAC), Sistemas Distribuídos, Aplicações com Redis e Bancos Colunares

**Escrevendo**
- Publicações técnicas ocasionais no LinkedIn sobre decisões arquiteturais dos projetos

---

## Stack

| | |
|---|---|
| **Runtime** | Java 21 · Spring Boot |
| **Dados** | PostgreSQL · Redis · Apache Kafka · MySQL · Apache Cassandra |
| **Infra** | Docker · AWS · GitHub Actions · Linux |
| **Observabilidade** | Micrometer · Prometheus · Grafana |
| **Testes** | JUnit 5 · Mockito · Testcontainers |
| **Build** | Maven |

Trabalho com TypeScript/Node.js e Python quando o projeto demanda. Tenho base sólida em frontend — meu foco de aprofundamento é backend.

---

## Certificações

**AWS Cloud Practitioner Essentials** — Amazon Web Services, janeiro de 2026. Preparando para a certificação CLF-C02.

**Cisco Academy Networking Basics** — Cisco Networking Academy, dezembro de 2025. Fundamentos de redes IP, IPv4 e protocolos de rede.

Estudo autodirigido contínuo em arquitetura de sistemas distribuídos e infraestrutura em nuvem — incluindo trilha Java/Spring Boot pela Rocketseat.

---

## O que busco

Concluindo o CentroWEG, com disponibilidade plena a partir de **agosto de 2026**. Busco oportunidades de engenharia backend ou full-stack em problemas complexos — sistemas distribuídos, plataformas orientadas a eventos, sistemas financeiros e de pagamento. Valorizo equipes que documentam decisões, encaram trade-offs com seriedade e tratam código como meio de design, não apenas entrega.

---

[pablotzeliks.github.io](https://pablotzeliks.github.io/pablotzeliks-portfolio) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)
