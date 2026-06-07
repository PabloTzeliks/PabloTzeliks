# Pablo Tzeliks

Backend developer — Java, Spring, distributed systems. Jaraguá do Sul, Brazil.

I build deliberately complex systems to understand them from the inside — eventual consistency, distributed sagas, decentralized authorization, domain design. I don't reach for the simplest solution; I reach for the one that forces the real engineering problem.

[Portfolio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)

---

## Where I am now

Finishing WEG's CentroWEG / SENAI Industrial Apprenticeship in Systems Development (Aug 2024 – Jul 2026).

On **Portal Conecta**, I'm Frontend Tech Lead — a role I was placed in deliberately, outside my backend specialty. The project is in active development; I coordinate the frontend squad (Next.js, Tailwind v4, shadcn/ui, pnpm monorepo) and own the design-system and delivery decisions.

Outside the program I'm in active development on **BlinkLink v4** and returning to **Time Trial** to remodel it around Kafka Streams. I'm reading *Fundamentals of Software Architecture* and learning the way I always have — by building the harder version of the problem.

---

## Stack

**Languages**  
Java · SQL · TypeScript · JavaScript · Python

**Backend**  
Spring Boot · Spring Security · Spring Modulith · JPA/Hibernate · REST APIs · JWT · JDBC · OpenAPI/Swagger

**Data & messaging**  
PostgreSQL · Redis · Kafka · Cassandra · Neo4j · MySQL · MQTT

**Observability**  
Micrometer · Prometheus · Grafana

**Infra, testing & build**  
AWS · Docker · Flyway · GitHub Actions · Linux · JUnit 5 · Mockito · Testcontainers · JaCoCo · Maven

---

## Focus
 
- Distributed systems and event-driven architecture
- Domain-Driven Design and explicit domain modeling
- Eventual consistency, sagas, and partial-failure handling
- Data ownership, derived state, and polyglot persistence
- Backend reliability — testing, observability, evolvability

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

Each one is a deliberate choice of problem — the decisions matter more than the features.

### [BlinkLink](https://github.com/PabloTzeliks/blink-link)
*v3 delivered · v4 in active development*

**A trivial domain, re-engineered four times to surface the hard problems.**

A URL shortener rebuilt across four iterations, each a vehicle for a specific engineering problem. The simplicity of the domain is the point — the focus is the rigor of the solution.

- Stateless IAM — JWT in HttpOnly cookies, OAuth2 (Google, GitHub), RBAC by roles and tiers.
- Async garbage collection with `SELECT ... FOR UPDATE SKIP LOCKED` — concurrent workers, no lock contention.
- Tested with Testcontainers against real PostgreSQL; CI/CD on every push.
- *v4 in progress:* Redis cache-aside, rate limiting, Spring Modulith boundaries, Kafka-fed analytics, first AWS deployment.

---

### [Time Trial](https://github.com/PabloTzeliks/time-trial-api)
*v1 delivered · remodeling in progress*

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

## Looking ahead
 
I'm starting a Software Engineering degree in mid-2026 and want to keep deepening the fundamentals beneath the systems I build — distributed architecture, data, the trade-offs that decide them.
Near term, I'm after backend or full-stack roles on hard problems — distributed systems, event-driven platforms, payments — with teams that document decisions and take trade-offs seriously. Available full-time from August 2026.

[Portfolio](https://pablotzeliks.github.io) · [LinkedIn](https://linkedin.com/in/pablo-ruan-tzeliks) · [devpablotzeliks@gmail.com](mailto:devpablotzeliks@gmail.com)
