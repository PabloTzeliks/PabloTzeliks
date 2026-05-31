# Pablo Tzeliks

Desenvolvedor de software Back-End. Java, Spring, sistemas distribuídos. Jaraguá do Sul, Brasil.

Construo sistemas deliberadamente complexos para entendê-los por dentro — consistência eventual, saga distribuída, autorização descentralizada, design de domínio. Não busco a solução mais simples — busco a que force o problema de engenharia real.

**Disponível a partir de agosto de 2026.**

[Portfólio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)

---

## Projetos Pessoais

### [Ciphernance](https://github.com/PabloTzeliks/Ciphernance) · em desenvolvimento ativo

Motor de core banking construído para entender sistemas distribuídos por dentro — um domínio onde saga, autorização descentralizada e event sourcing têm que coexistir por requisito, não por escolha.

Seis microsserviços. Quinze ADRs antes de qualquer código.

**Decisões centrais:**

- **Choreography sobre Orchestration.** Sem orquestrador central como ponto único de falha; rastreabilidade mais complexa mitigada pelo Audit Service imutável que captura a cadeia de eventos completa.
- **ABAC com Policy Agents distribuídos.** Cache em duas camadas (Caffeine L1 + Redis L2), sincronizado via Kafka — consistência eventual aceita e documentada como trade-off deliberado.
- **Event Sourcing escopado ao Transaction Service.** Saldo derivado do histórico de transações, não armazenado como coluna — aplicado onde o domínio exige, não onde seria conveniente.

**Em andamento:** Identity Service — estrutura de políticas ABAC com DSL YAML, agentes em cada serviço sincronizados via Kafka.

`Java 21 · Spring Boot 4 · Kafka · PostgreSQL · Redis · Neo4j · Prometheus · Grafana · Testcontainers · Maven`

[Repositório](https://github.com/PabloTzeliks/Ciphernance) — código, ADRs e roadmap públicos.

---

### [BlinkLink](https://github.com/PabloTzeliks/blink-link) · v3 disponível · v4 em desenvolvimento

URL shortener reconstruído quatro vezes — cada iteração foi o veículo para um problema específico de engenharia. A simplicidade do domínio é proposital: o foco está no rigor da solução, não na complexidade do negócio.

**v3 — entregue:**

- IAM stateless: JWT em cookies HttpOnly, OAuth2 com Google e GitHub, RBAC por Roles e Tiers de usuário.
- Garbage collection assíncrono com `SELECT ... FOR UPDATE SKIP LOCKED` — workers concorrentes sem contenção de lock.
- Testcontainers contra PostgreSQL real — não H2, não mocks. CI/CD com GitHub Actions a cada push.

**v4 — em construção:**

- Cache Redis com estratégia cache-aside e alinhamento de TTL entre cache e banco.
- Rate limiting por usuário e por endpoint.
- Refatoração com Spring Modulith — modularização explícita sem migrar para microsserviços.
- Banco colunar para o módulo de Analytics com ingestão via Kafka.
- Primeiro deploy real na AWS.

`Java 21 · Spring Boot 4 · Spring Security · Spring Modulith · PostgreSQL · Redis · Kafka · Flyway · Docker · Testcontainers · GitHub Actions`

---

## Aprendizado — CentroWEG/SENAI

Programa industrial de 3.200 horas dentro da WEG, agosto de 2024 a julho de 2026. O currículo oferece amplitude; a profundidade construo nos projetos, levando cada problema além do que o escopo do curso exige.

**InfoWEG** · Product Owner e Tech Lead

Plataforma de comunicação interna com entrega segmentada por perfil — originei o conceito, defini a arquitetura inicial e coordenei o time de classe com Scrum.

`Java · Spring Boot · MySQL`

<br>

**SynapseRH** · Tech Lead e Lead Backend Developer

Sistema de recrutamento com matchmaking por habilidades — capstone da unidade de Técnicas de Programação, equipe de cinco pessoas, ~80 issues gerenciadas.

- Arquitetura em quatro camadas com DDD explícito e Value Objects no domínio (Email, CPF, Endereço, Senha)
- Algoritmo de matchmaking com pontuação ponderada contra requisitos da vaga
- Strategy Pattern no CLI, MapStruct entre camadas de aplicação e apresentação
- Apresentado a painel externo de RH

`Java 21 · PostgreSQL · JDBC · MapStruct`

<br>

**Time Trial System** · Tech Lead e Arquiteto

Plataforma de telemetria IoT em tempo real com hardware físico (ESP32 + RFID) — o time saiu do stack esperado pelo curso e reconstruiu o problema do zero com arquitetura orientada a eventos.

- Ingestão assíncrona via MQTT, Cassandra em cluster de 3 nós com consistência QUORUM
- Distribuição de resultados em tempo real via WebSocket sem polling
- Módulo de análise em Python com K-Means e Streamlit
- Demo ao vivo para Professores e Supervisores de diferentes áreas do CentroWEG

`Java 21 · Spring Boot 3 · Apache Cassandra · Docker`

<br>

**Payment Gateway Core** · Co-desenvolvedor

Duas implementações paralelas do mesmo gateway — uma deliberadamente caótica, uma deliberadamente rigorosa — para estudar por contraste o valor de arquitetura disciplinada.

- Transaction manager ACID customizado via `ThreadLocal` + JDBC sem Spring
- Execute Around Pattern para centralizar o ciclo de vida das conexões JDBC
- Event Sourcing para derivar saldo do histórico imutável de transações
- ~80% de cobertura entre testes unitários, de integração e end-to-end

`Java 21 · PostgreSQL · Maven`

---

## Atualmente

- Praticando CQRS, Event Sourcing e sagas coreografadas
- Estudando ABAC, caching com Redis e bancos colunares
- Lendo *Fundamentals of Software Architecture: An Engineering Approach*

---

## Stack

- **Runtime:** Java 21 · Spring Boot
- **Dados:** PostgreSQL · Redis · Apache Kafka · Neo4j · MySQL · Apache Cassandra
- **Infra:** Docker · AWS · GitHub Actions · Linux
- **Observabilidade:** Micrometer · Prometheus · Grafana
- **Testes:** JUnit 5 · Mockito · Testcontainers
- **Build:** Maven

Trabalho com TypeScript/Node.js quando o projeto demanda. Tenho base muito sólida em frontend — meu foco de aprofundamento é backend.

---

## Certificações

**AWS Cloud Practitioner Essentials** — Amazon Web Services, janeiro de 2026. Preparando para a certificação CLF-C02.

**Confluent Apache Kafka Fundamentals Accreditation** — Confluent, maio de 2026. Fundamentos de Apache Kafka, Kafka Streams, Kraft, Apache Flink, Confluent Cloud e Platform

**Cisco Academy Networking Basics** — Cisco Networking Academy, dezembro de 2025. Fundamentos de redes IP, IPv4 e protocolos de rede.

---

## O que busco

Concluindo o CentroWEG, com disponibilidade plena a partir de **agosto de 2026**. Busco oportunidades de engenharia backend ou full-stack em problemas complexos — sistemas distribuídos, plataformas orientadas a eventos, sistemas financeiros e de pagamento. Valorizo equipes que documentam decisões, encaram trade-offs com seriedade e tratam código como meio de design, não apenas entrega.

---

[Portfólio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)
