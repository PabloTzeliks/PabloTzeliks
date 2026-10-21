# Pablo Tzeliks

Full stack developer on WEG's industrial software engineering team. I work end to end, from critical data scattered across the company to the tools people use every day. Jaraguá do Sul, Brazil.

[Portfolio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)

---
 
## Now
 
Full stack developer at WEG since August 2026, in the Integrated Manufacturing Systems section. Day to day developing end to end solutions for industrial digitalization.

## Education
 
**Bachelor's in Software Engineering**, Instituto Infnet  
*2026 to 2030 · in progress*
 
**Industrial Apprenticeship in Systems Development**, CentroWEG / SENAI  
*2024 to 2026 · 3,200 hours*  

Graduated as the outstanding student of my class, with a final average of 9.61.

---

## Stack

**Languages**  
Java · TypeScript · SQL · Python · JavaScript · Go *(learning)*

**Backend**  
Spring Boot · Spring Security · Spring Modulith · JPA/Hibernate · REST APIs · JWT · JDBC · OpenAPI/Swagger

**Frontend:**
Next.js · React · Micro-frontends · Tailwind · Storybook · Vitest · Chromatic

**Data & messaging**  
PostgreSQL · MySQL · Redis · Cassandra · Kafka · MQTT · Airflow · Dremio

**Observability**  
Prometheus · Grafana · Micrometer · OpenTelemetry · Loki · Tempo

**Infra, testing & build**  
AWS · Kubernetes · Docker · Flyway · GitHub Actions · GitLab CI/CD · Linux · JUnit 5 · Mockito · Testcontainers · JaCoCo · Maven

---

## Certifications & Coursework

Certifications, accreditations, and training badges:

- **Confluent Apache Kafka Fundamentals Accreditation** — May 2026
- **AWS Cloud Practitioner Essentials** — Jan 2026 *(preparing for CLF-C02)*
- **AWS Academy Graduate — Cloud Foundations** — Jun 2026
- **Networking Basics** — Cisco Networking Academy, Dec 2025

Relevant coursework at WEG CentroWEG / SENAI: System Architecture, API Programming, Front-End programming, Database Implementation, Cloud Computing, and Information Security.

---

## Systems

Each one is a deliberate choice of problem, the decisions matter more than the features.

### [Portal Conecta](https://github.com/Portal-Conecta)
*Delivered · apprenticeship final project*
 
A hub platform for WEG and SENAI, built by 28 people across 5 squads. I was the Frontend Tech Lead, which meant a backend developer leading the frontend. I studied frontend after hours so I could make the calls while the project was moving.
 
- Modular frontend in a pnpm monorepo (Next.js, Tailwind v4), split into core, ui and shared layers with enforced module boundaries.
- Design system with 44 components, kept in Figma and Storybook. Tokens flow from Figma variables straight into Tailwind.
- A BFF inside the Next.js server keeps business logic out of the UI.
- Around 700 logic tests with Vitest, plus Chromatic visual regression and boundary checks.

### [BlinkLink](https://github.com/PabloTzeliks/blink-link)
*v4.1 delivered*

**A trivial domain, re-engineered four times to surface the hard problems.**

A URL shortener rebuilt across four iterations, each a vehicle for a specific engineering problem. The simplicity of the domain is the point — the focus is the rigor of the solution.

- Redis hot path — cache-aside redirects, distributed ID sequence (`INCR`), and per-plan rate limiting with a sliding-window counter. Redis as the speed layer, PostgreSQL as the source of truth.
- Stateless IAM — JWT in HttpOnly cookies, OAuth2 (Google, GitHub), RBAC by roles and tiers.
- Async garbage collection with `SELECT ... FOR UPDATE SKIP LOCKED` — concurrent workers, no lock contention.
- Tested with Testcontainers against real PostgreSQL and Redis; CI/CD on every push.
- *v4.2 next:* Spring Modulith boundaries, Redis Streams analytics pipeline, ClickHouse storage, first AWS deployment.

---

### [Time Trial](https://github.com/PabloTzeliks/time-trial-api)
*v1 delivered*

**Physical race sensors to a live leaderboard, event-driven end to end.**

A real-time IoT lap-timing platform on physical hardware (ESP32 + RFID). The team left the course's expected stack (Node-RED + MySQL) and rebuilt the problem around event-driven architecture. Demoed live to instructors and WEG IT leadership, with physical ESP32 hardware on stage.

- Edge devices kept deliberately "dumb" — they emit only `{rfid, timestamp}`; all validation lives in the backend, so sensors scale horizontally.
- Async MQTT ingestion into a running 3-node Cassandra cluster with QUORUM reads/writes; real-time output over WebSocket, history over REST.
- Python analytics — K-Means clustering, Streamlit dashboard.
- *Remodeling toward:* Kafka Streams for lap aggregation, first-class `Pista` and `Sessão` entities, durable lap-time storage.

---

### [Ciphernance](https://github.com/PabloTzeliks/Ciphernance)
*architecture study · paused*

**Distributed core banking as an architecture study — fifteen ADRs before the first line of code.**

A design-first exploration of the problems a banking core forces on you: choreographed sagas, eventually consistent authorization, event sourcing where the domain demands it. The repository is the reasoning — fifteen ADRs documenting the trade-offs.

**Designed, not yet implemented** — this captures how I reason about hard distributed problems before writing code, not a system I've validated by running it.

- Choreography over orchestration — no central orchestrator as a single point of failure; an immutable Audit Service captures the full event chain.
- ABAC with distributed policy agents — Caffeine (L1) + Redis (L2) synced over Kafka; eventual consistency as a documented trade-off.
- Event sourcing scoped to the Transaction Service — balance derived from history, applied only where the domain requires it.

---

### [SynapseRH](https://github.com/equipe-javagle/mvp-recruitment-system)
*delivered*

**Skill-based recruitment matching — DDD, a five-person team, presented to an external HR panel.**

A CLI recruitment system that matches candidates to openings through a weighted skill-scoring algorithm, built as a course capstone. ~80 issues managed across the team.

- Four-layer architecture with explicit DDD and domain Value Objects (Email, CPF, Address, Password).
- Weighted-score matchmaking against vacancy requirements.
- Strategy Pattern in the CLI; MapStruct between layers.

---

### [Payment Gateway Core](https://github.com/PabloTzeliks/system-architecture-challenge)
*delivered*

**The same gateway built twice — disciplined vs. chaotic — to study architecture by contrast.**

Two parallel implementations of one payment gateway, one deliberately rigorous and one deliberately chaotic, to study the value of disciplined architecture by contrast.

- Custom ACID transaction manager via `ThreadLocal` + JDBC — `@Transactional` by hand, no Spring.
- Execute-Around Pattern centralizing the JDBC connection lifecycle.
- Event sourcing to derive balance from immutable transaction history.

---

## Know me better

[Portfolio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)
