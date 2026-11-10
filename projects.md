# Projects & Technical Initiatives Portfolio

A structured record of engineering projects, architectural initiatives, and system implementations, enriched with industry context, domain specifications, and technology stacks.

---

## 1. Digital Health, Medical Devices & Regulated Systems

### Recovery Cat - EU MDR Certified Class I Medical Device Platform
* **Role & Organization:** Head of Development · Recovery Cat GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Digital Mental Health, Measurement-Based Care (MBC), Remote Patient Monitoring (RPM), Charité – Universitätsmedizin Berlin spin-off, Berlin Institute of Health (BIH) Digital Health Accelerator, Techniker Krankenkasse (TK) statutory reimbursement contract (later acquired by Resilience Care).
* **Technologies:** EU MDR 2017/745 (Class I SaMD), WebRTC, Keycloak (OIDC/OAuth2), Progressive Web Apps (PWA), Docker, GitLab CI/CD, Threagile (Threat Modeling), Trivy (Vulnerability Scanning), Scrum.
* **Key Deliverables & Practical Impact:**
  * **SaMD Architecture & Regulatory Threat Modeling:** Owned the end-to-end software architecture and regulatory security posture for an EU MDR 2017/745 certified Class I Medical Device, safeguarding highly sensitive psychiatric patient data across inpatient and outpatient care pathways deployed in ~20 German hospital networks and psychiatric clinics.
  * **WebRTC Signaling Engine Overhaul:** Rebuilt the real-time WebRTC signaling architecture from the ground up, eliminating peer connection dropouts and 100% of communication support incidents between Healthcare Professionals (HCPs) and patients.
  * **Zero-Loss Patient Data Migration:** Eliminated critical data loss vulnerabilities inherent to client-side PWA browser caches by engineering an automated, encrypted backend migration pipeline preserving full longitudinal clinical histories.
  * **Enterprise IAM Integration (Keycloak):** Architected and deployed a multi-tenant, custom-branded `Keycloak` Identity & Access Management (OIDC/OAuth2) infrastructure, migrating unauthenticated PWA endpoints to role-based access control (RBAC) with granular session governance.
  * **Automated DevSecOps Pipeline:** Embedded `Threagile` automated threat modeling and `Trivy` container scanning directly into GitLab CI/CD pipelines to ensure continuous regulatory compliance and risk mitigation across every build artifact.

### Recovery Cat Architecture & Automated Threat Modeling (`rcc-architecture`)
* **Role & Organization:** Head of Development / Software Architect · Recovery Cat GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Medical Device Security Architecture, STRIDE Threat Modeling, EU MDR 2017/745 & ISO 27001 Compliance, Multi-Cloud Topology.
* **Technologies:** Threagile (Code-as-Threat-Model, Go/YAML), Docker, GitLab CI/CD, Scaleway Kapsule (Kubernetes), Hetzner Bare Metal / Cloud, Traefik, Keycloak (OIDC), PostgreSQL, WebRTC / STUN, Python (`validate_yaml.py`).
* **Key Deliverables & Practical Impact:**
  * **Executable Threat Model & Architecture-as-Code:** Formulated and maintained the comprehensive, code-driven architecture specification and threat model (`threagile-rcc-model.yaml`), mapping 34 technical assets, 16 data assets, 13 trust boundaries, and 44 communication links into automated compliance artifacts (`report.pdf`, `risks.json`, `data-flow-diagram.png`).
  * **Automated CI/CD Risk Quantification:** Integrated containerized `Threagile` execution into `.gitlab-ci.yml` pipelines, automatically quantifying 300 STRIDE/ASVS security risks to prevent security regressions during continuous delivery.
  * **Multi-Cloud Medical Infrastructure Architecture:** Engineered the operational deployment topology spanning Scaleway Kapsule Kubernetes (`prod-apps`, `monitoring`, `flux-system` namespaces), dedicated managed PostgreSQL clusters, Hetzner VM infrastructure (STUN signaling, GitLab CI runners), and Jointech Bare Metal hosts (Zammad, Matomo).
  * **Zero-Knowledge Privacy & Real-Time Signaling Topology:** Architected the client-side data isolation model featuring browser-local patient storage, QR-code AES cryptographic negotiation, and hybrid WebRTC DataChannel / WebSocket fallback transmission preventing unauthorized access to psychiatric records.

### Recovery Cat Keycloak Extensions & Custom IAM Plugins (`keycloak-plugins`)
* **Role & Organization:** Head of Development · Recovery Cat GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Medical IAM & Identity Federation, Custom Keycloak SPI Extensions, Multi-Realm Healthcare Architecture, German Statutory Health Insurance Integration (§ 290 SGB V).
* **Technologies:** Java 17, Keycloak 26.5 (Quarkus runtime), Keycloak Server SPIs (`AuthenticatorFactory`, `EventListenerProviderFactory`, `ValidatorFactory`, custom `InsuranceProvider` SPI), Jakarta RESTful Web Services 3.1, JBoss Logging, `vbu-krankenversichertennummer`, Lombok, Maven (Shade, Enforcer, Spotless, PMD), JUnit 5, Mockito, Docker (BusyBox init container), GitLab CI/CD.
* **Key Deliverables & Practical Impact:**
  * **Client-Driven Role & Group Assignment Authenticator (`GroupAssignmentAuthenticator`):** Engineered custom Keycloak authentication flow interceptors dynamically mapping and validating authenticated user groups and role privileges based on calling OIDC client context (`rcc-hcp` vs `rcc-pat`).
  * **German Health Insurance Number (KVN) Checksum Validator (`KrankenversichertennummerValidator`):** Implemented strict server-side validation against official German statutory health insurance number formatting rules (§ 290 SGB V 10-digit modulo-10 checksum algorithm) via `vbu-krankenversichertennummer`, preventing invalid medical reimbursement registrations.
  * **Cross-Realm Organization Federation & User Profile Sync (`OrganizationValidator`, `OrganizationEventListener`):** Built custom Event Listeners and cross-realm validators that synchronize healthcare clinic organizations and update user profile metadata, attributes, and i18n localizations dynamically between administrative and clinical realms.
  * **Dynamic Insurance Provider SPI & Cache Engine (`InsuranceProvider`, `InsuranceEventListener`, `TimedCache`):** Architected a custom Keycloak Provider SPI fetching, caching, and synchronizing statutory and private health insurance catalog endpoints with automated User Profile attribute schema enrichment and time-to-live (`TimedCache`) eviction.
  * **Regulated Date of Birth & Age Gate Validation (`DateOfBirthValidator`):** Created configurable minimum/maximum age validators embedded into Keycloak User Profile registration flows for clinical trial and psychiatric SaMD eligibility compliance.

### Recovery Cat User Data Storage API (`rcc-user-data-storage-api`)
* **Role & Organization:** Head of Development · Recovery Cat GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Regulated Medical Device Backend, Encrypted Client-Side Data Storage & Backup, Multi-Tenant OIDC RBAC, SOUP Regulatory BOM Compliance (IEC 62304 / EU MDR).
* **Technologies:** Java 21, Quarkus (REST Jackson, Hibernate ORM Panache, OIDC Multi-Tenant, SmallRye Fault Tolerance, SmallRye Health, Micrometer Prometheus, Scheduler), PostgreSQL 17 / JSONB, Liquibase, MapStruct, Hypersistence Utils (TSID, JSONB), NetworkNT JSON Schema Validator, Lombok, Spotless, PMD, JaCoCo, REST-Assured, Docker Jib / Harbor Registry, GitLab CI/CD.
* **Key Deliverables & Practical Impact:**
  * **Zero-Knowledge Medical Data Persistence & JSONB Schema Enforcement:** Architected a high-performance, compliant REST backend for storing and synchronizing encrypted clinical client state across 12 distinct health data types (`rcc-settings`, `rcc-journal`, `rcc-custom-symptom-checks`, `rcc-custom-questions`, `rcc-hcp-backup`, `rcc-pat-backup`, `metadata`) using PostgreSQL `jsonb` with Hypersistence TSID (Time-Sorted Unique Identifier) primary keys and NetworkNT JSON Schema pre-validation.
  * **Multi-Tenant JWT Issuer Resolution (`MultiTenantMergerTenantResolver`):** Implemented custom Quarkus OIDC tenant resolution interceptors inspecting JWT issuer payloads across multi-realm Keycloak topologies (`rcc-hcp` clinical realm and `rcc-pat` patient realm), establishing unified security contexts with fine-grained HTTP RBAC policies (`pat-read`, `pat-create`, `pat-destroy`, `hcp-read`, `hcp-create`, `hcp-destroy`, `super-admin`).
  * **API-Key Protected Insurance Gateway & Cross-Service Federation:** Engineered high-security internal integration endpoints (`/v1/insurances`) with custom JAX-RS `ApiKeyRequestFilter` authentication, serving active German health insurance catalogs directly to the Keycloak IAM SPI plugin ecosystem.
  * **Automated SOUP / SBOM Regulatory Compliance Generator (`generate-soup.sh`):** Formulated automated Software of Unknown Provenance (SOUP) extraction tooling parsing Gradle dependency trees for IEC 62304 / EU MDR Class I medical device technical file audits and post-market surveillance.
  * **Resilient Fault-Tolerant Transaction Processing & Real-Time Telemetry:** Integrated SmallRye `@Retry` handling for optimistic concurrency and constraint collisions, alongside scheduled Prometheus gauges (`UserStatsScheduler`) tracking active patient and clinician cohort telemetry (`app.users.total`, `app.users.hcp.total`, `app.users.pat.total`).

### German COVID-19 Digital Vaccination Certificate (`CovPass` / `EU DCC`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** National Public Health Infrastructure, EU Digital COVID Certificate (`EU DCC`), German Federal Ministry of Health (BMG) consortium partnership with IBM and Bechtle/GovOS.
* **Technologies:** Scala, Akka (Actors, HTTP, Streams), Apache Kafka, Apache Cassandra, PostgreSQL, Cryptographic Signing (ECDSA / Ed25519), High-Throughput REST APIs.
* **Key Deliverables & Practical Impact:**
  * **Nationwide Public Health Backbone:** Delivered core backend streaming and signing components for the official German Vaccination Proof (*Digitales Impfzertifikat*), integrating thousands of pharmacies (DAV), vaccination centres, and medical practices into the EU DCC trust gateway.
  * **High-Throughput Cryptographic Scalability:** Engineered high-availability event-driven streaming pipelines using `Scala`, `Akka Streams`, and `Kafka` capable of processing, signing, and mathematically validating millions of verifiable health certificates daily under peak national load.

---

## 2. Distributed Systems, Blockchain & Data Integrity Platforms

### Ubirch Attestation Platform
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Cryptographic Data Integrity, IoT & Sensor Attestation, Distributed Ledger Anchoring.
* **Technologies:** Scala, Java, Apache Kafka, Apache Cassandra, PostgreSQL, Redis, JanusGraph, Merkle Tree Aggregations, Blockchain Anchoring (IOTA, Ethereum, Polygon).
* **Key Deliverables & Practical Impact:**
  * **Niomon Event-Driven Ingestion Pipeline:** Co-developed and maintained the `Niomon` message ingestion microservices (decoding, signature verification, device certificate validation, and high-throughput serialization) handling continuous streams of cryptographic data packets.
  * **Merkle Tree Event Log & Multi-Chain Anchoring:** Engineered the `Event Log System` that aggregates cryptographic hashes into linked Merkle trees and periodically anchors root hashes into public ledgers (Ethereum, IOTA), generating tamper-proof timestamps and verifiable proofs of existence.
  * **Intelligent Certificate Storage:** Designed a multi-tier storage engine leveraging `Cassandra`, `JanusGraph`, and `Redis` for sub-second verification and cryptographic lineage tracing across millions of connected devices.

### Ubirch Identity Service (`ubirch-id-service`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Public Key Infrastructure (PKI), Decentralized Identity (DID), Cryptographic Key Lifecycle & Device Attestation.
* **Technologies:** Scala, Monix (`Task`), Scalatra, Apache Cassandra (`quill-cassandra-monix`), Apache Kafka (`ubirch-kafka-express`), Ed25519, ECDSA, X.509 Certificates, Docker, Prometheus.
* **Key Deliverables & Practical Impact:**
  * **Asynchronous High-Throughput PKI Core:** Architected and developed the central identity management microservice handling public key registration, verification, and cryptographic lifecycle management for millions of IoT devices and identity anchors using `Monix Task` and `Scalatra`.
  * **Multi-Algorithm Cryptographic Key Storage:** Engineered high-performance persistence and retrieval pipelines on `Apache Cassandra` via `Quill Cassandra Monix`, supporting Ed25519 and ECDSA public key algorithms, certificate chains, and key revocation lists.
  * **Event-Driven Identity Event Streaming:** Integrated bidirectional `Apache Kafka` event streaming using `ubirch-kafka-express` for instant pub/sub notification of key lifecycle transitions (activation, expiration, and invalidation) across all downstream verification services.
  * **Zero-Trust Identity Verification API:** Designed RESTful and streaming verification endpoints enforcing cryptographic signature validation against registered public keys with sub-50ms latency.

### Ubirch Token Manager (`ubirch-token-manager`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Multi-Tenant Access Control, Scoped Token Delegation, API Security & Authorization Infrastructure.
* **Technologies:** Scala, Monix (`Task`), Scalatra, Apache Cassandra (`quill-cassandra-monix`), JWT (`jose4j`, `jwt-core`), SHA-256 Token Hashing, Keycloak OIDC, Docker, Prometheus.
* **Key Deliverables & Practical Impact:**
  * **Fine-Grained Scoped Token Architecture:** Designed and implemented a multi-tenant token management engine issuing cryptographically signed fine-grained scoped JWT tokens with granular capabilities (e.g., `upp:anchor`, `upp:verify`, `thing:*`, `user:getinfo`).
  * **Hierarchical Token Delegation & Sub-Token Trees:** Built hierarchical sub-token generation workflows allowing master accounts and enterprise tenants to delegate restricted access rights and expiration policies to downstream devices and automated services.
  * **Cassandra Persistence & SHA-256 Token Verification:** Engineered a high-throughput validation and persistence pipeline leveraging `Apache Cassandra` via `Quill Cassandra Monix` alongside `SHA-256` token hashing for sub-millisecond token lookup and authorization checks.
  * **Keycloak & Gateway Interoperability:** Embedded seamless integration with enterprise `Keycloak` IAM, translating user identity contexts and bearer tokens into ephemeral service tokens for secure inter-service communication.

### Ubirch Blockchain Service (`ubirch-blockchain-service`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Distributed Ledger Technology (DLT), Multi-Chain Anchoring, Public Consensus Validation & Proof of Existence.
* **Technologies:** Scala, Java, IOTA (Native C/JNI & Rust Client), Ethereum / EVM (`Web3j`), Bloxberg, GovDigital, Apache Kafka (`ubirch-kafka-express`), Prometheus.
* **Key Deliverables & Practical Impact:**
  * **Multi-Chain Distributed Anchoring Engine:** Developed a multi-chain ledger dispatching microservice that consumes aggregated Merkle tree root hashes from `Kafka` and asynchronously commits cryptographic anchors across public and consortium networks (`Ethereum`, `IOTA`, `Bloxberg`, `GovDigital`).
  * **High-Throughput IOTA JNI Integration:** Engineered native JVM-to-C/Rust JNI bindings for the `IOTA` client library, optimizing transaction payload serialization, tip selection, and proof-of-work delegation under high message volume.
  * **Dynamic Gas Management & Balance Telemetry:** Implemented automated gas price estimation, wallet balance monitors, and Prometheus alerting to guarantee continuous, zero-failure transaction broadcast during network congestion.
  * **Verifiable Transaction Receipt Pipeline:** Built asynchronous receipt generation and validation pipelines returning immutable blockchain transaction hashes and block numbers to the Ubirch attestation lineage.

### Ubirch Accounting & Metering Service (`ubirch-accounting-service`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Usage Metering, Multi-Tenant Billing Telemetry, High-Volume Event Accounting & Auditability.
* **Technologies:** Scala, Monix, Scalatra, Apache Cassandra (`quill-cassandra`), PostgreSQL (`quill-jdbc`, Flyway), Apache Kafka (`ubirch-kafka-express`), Keycloak JWT, Prometheus, Docker.
* **Key Deliverables & Practical Impact:**
  * **High-Volume Event Accounting Engine:** Architected an event-driven accounting platform tracking, partitioning, and aggregating billable cryptographic operations (`anchoring`, `upp_verification`, `uvs_verification`) with zero event loss.
  * **Dual-Channel Ingestion & Cassandra Partitioning:** Designed dual `Kafka` streaming and RESTful HTTP batch ingestion endpoints persisting time-partitioned accounting records into `Apache Cassandra` for high-write scalability.
  * **Asynchronous Enrichment & Aggregation Jobs:** Built dedicated background enrichment workers (`acct-enricher-job`, `acct-enricher-job-http`) using `PostgreSQL` and `Flyway` to aggregate raw transaction volumes into monthly tenant usage reports with tag-based filtering.
  * **Secured Multi-Tenant Metering APIs:** Implemented Keycloak OIDC/JWT-authenticated query endpoints allowing enterprise customers to audit, monitor, and export real-time consumption and quota analytics.

### Ubirch Key Service Migration Pipeline (`ubirch-key-service-migration`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Database Migration, Graph-to-Columnar Schema Translation, Zero-Downtime Data Modernization.
* **Technologies:** Scala, Neo4j (`neo4j-java-driver`), Identity Service REST APIs, Apache HttpClient, JSON4S, CSV Audit Reporting, Docker.
* **Key Deliverables & Practical Impact:**
  * **Graph-to-Distributed Migration Architecture:** Engineered an automated data migration pipeline extracting historical cryptographic public keys from legacy `Neo4j` graph databases and translating them into the modern `ubirch-id-service` Cassandra store.
  * **REST Dispatching & Zero-Downtime Batch ETL:** Implemented batch extraction with cursor pagination, payload normalization, and REST dispatching to Identity Service endpoints with cryptographic verification and retry handling.
  * **Dual-Format Audit & Executive Reporting:** Integrated automated dual-stream reconciliation generating detailed CSV transaction logs and executive summary reports tracking migrated, updated, and failed key records for regulatory verification.

### Ubirch Point of Certification Agent (`ubirch-poc-agent`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Edge Certification, Hybrid Cloud/On-Premise Gateway, EU Digital Health Interoperability.
* **Technologies:** Scala, Monix (`Task`), Scalatra, STTP (`async-http-client`), Ubirch Protocol (UPP), EU Digital COVID Certificate (`EU DCC` / Base45), Bouncy Castle, Prometheus, Docker.
* **Key Deliverables & Practical Impact:**
  * **Edge Certification Gateway Architecture:** Developed an on-premise and hybrid-cloud certification agent using `Scalatra` and `Monix Task`, acting as an intelligent facade coordinating cryptographic UPP signing and EU DCC health certificate generation.
  * **Dual-Target Dispatching & Orchestration:** Built resilient request distribution pipelines using `STTP` and `AsyncHttpClient` multiplexing certification workloads across local UPP Signers and remote Certify-APIs with automated fallback and error buffering.
  * **High-Availability Local Ingestion:** Designed lightweight, containerized edge deployment profiles ensuring reliable Base45 payload encoding and certificate issuance in low-connectivity or security-restricted hospital/testing center environments.

### Ubirch Kafka Express - High-Throughput Streaming & Microservice Abstraction Framework
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Event-Driven Architecture, High-Throughput Stream Processing, JVM Microservices, Developer Experience & Framework Tooling.
* **Technologies:** Scala, Apache Kafka, Prometheus Metrics (`WithMetrics`), JVM Concurrency (Futures / Actors), Maven/SBT (`com.ubirch:ubirch-kafka-express`), Graceful Shutdown Hooks.
* **Key Deliverables & Practical Impact:**
  * **Standardized Streaming Microservice Framework (`ExpressKafkaApp`):** Designed and implemented `ExpressKafkaApp[K, V]`, a generic component abstraction streamlining Kafka consumer and producer initialization across microservices with unified configuration, deserialization/serialization pipelines, and multi-topic routing (`send`/`process`).
  * **Resilient Consumer Runner with Adaptive Back-Pressure:** Built `ConsumerRunner` featuring amortized pause/unpause back-pressure mechanisms, partition rebalance listeners, configurable auto-commit and manual commit retry policies, and out-of-the-box String and Bytes consumer implementations.
  * **Two-Tier Exception Escalation & Fault Isolation:** Implemented a two-floor exception management architecture allowing fine-grained isolation between transient record-level processing failures and fatal partition/broker errors requiring escalation.
  * **Embedded Prometheus Telemetry & Graceful Lifecycle Hooks:** Integrated `WithMetrics` trait for real-time Prometheus throughput and lag monitoring, alongside automated JVM shutdown hooks (`WithConsumerShutdownHook`, `WithProducerShutdownHook`) ensuring zero-data-loss draining during redeployments.

### `KYCT` (Know Your Customer Token) - Decentralized Identity Protocol
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Web3, Self-Sovereign Identity, Privacy-Preserving Compliance, Deutsche Telekom & T-Mobile US Innovation Ecosystem.
* **Technologies:** Solidity, `ERC-721` Smart Contracts, Ethereum, Polygon, Zero-Knowledge / Non-PII Verification Patterns.
* **Key Deliverables & Practical Impact:**
  * **Global Innovation Recognition ("Best Solution" Award):** Awarded **"Best Solution"** at the international **T-Challenge 2022/2023** (*Human-Centered Web3 & 5G Innovation*) organized jointly by **Deutsche Telekom**, **T-Mobile US**, and **T-Labs**, selected from 282 competing teams across 53 countries for excellence in privacy-preserving decentralized tokenization.
  * **On-Chain Compliance Tokenization:** Conceptualized and built `KYCT`, an on-chain identity verification mechanism utilizing `ERC-721` non-fungible tokens on Ethereum and Polygon.
  * **Zero-PII Regulatory Proofs:** Enabled decentralized finance (DeFi) protocols and Web3 dApps to cryptographically verify user KYC compliance and accreditation without exposing underlying Personally Identifiable Information (PII).

### Catalina - Ubirch Trust Platform Client & Verification Suite
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Cryptographic Data Integrity, Verifiable Data Auditing, Trust-as-a-Service Cloud APIs.
* **Technologies:** Java, Scala, REST APIs, Cryptographic Micro-Certificates, Merkle Tree Anchoring, Public Ledgers.
* **Key Deliverables & Practical Impact:**
  * **Multi-Source Micro-Certificate Dispatch:** Engineered client interface modules enabling automated generation and dispatch of cryptographic micro-certificates from diverse data sources (local files, arbitrary text payloads, user inputs, and static strings) to the Ubirch Trust Service.
  * **Trust-as-a-Service Verification Engine:** Built verification tooling that queries public ledger anchors to mathematically validate micro-certificate integrity, guaranteeing tamper-proof, immutable timestamps and provable existence.
  * **Client Integration & Workflow Automation:** Streamlined integration pipelines for third-party systems to embed cryptographic attestation and lineage tracking directly into upstream data ingestion workflows.

### Catalina Slack App - Verifiable Message Timestamping
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** ChatOps, Enterprise Communication Integrity, Immutable Audit Trails.
* **Technologies:** Slack API / Bot Framework, Webhooks, RESTful Integrations, Cryptographic Hashing, Ubirch Trust Service.
* **Key Deliverables & Practical Impact:**
  * **Chat-Native Timestamping & Attestation:** Developed a Slack integration enabling enterprise teams to generate tamper-proof, verifiable timestamps and cryptographic snapshots of messages directly inside communication channels.
  * **Zero-Friction Audit Trails:** Automated the conversion of critical chat decisions, operational incidents, and contractual exchanges into immutable proofs anchored via the Ubirch Trust Service.
  * **Instant Verification Workflow:** Provided seamless slash commands and message actions allowing any channel participant to instantly audit and verify message integrity without leaving the Slack client.

### Engineering Technical Debt & Quality Governance Framework
* **Role & Organization:** Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Software Architecture, Engineering Governance, Radar Metrics, CI/CD Quality Gates.
* **Technologies:** Architectural Decision Records (ADRs), 6-Dimension Radar Evaluation, Automated CI Testing Suites.
* **Key Deliverables & Practical Impact:**
  * **6-Dimension Evaluation Framework:** Designed and operationalized a structured technical debt assessment matrix across Security, Compliance, Performance, Modifiability, Testability, and Usability/DX.
  * **Sustainable Codebase Modernization:** Guided multi-year codebase refactoring programs, maintaining an 80/20 delivery-to-refactoring balance that continuously reduced vulnerability surface area without compromising product velocity.

---

## 3. E-Commerce, SaaS & Marketing Automation Platforms

### pluriME Multi-Tenant Website-Builder Platform
* **Role & Organization:** Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
* **Domain & Ecosystem:** Multi-Tenant SaaS, SMB Digital Enablement, Cloud Content Management.
* **Technologies:** RESTful APIs, Throttling & Rate-Limiting Systems, Java/JVM, Relational Databases, Modular Cloud Services.
* **Key Deliverables & Practical Impact:**
  * **High-Velocity Site Generation Engine:** Developed core platform modules enabling non-technical users to build, customize, and publish digital storefronts, portfolios, and custom domains in minutes.
  * **Commercial Transaction Subsystems:** Built full-lifecycle business modules including dynamic product catalogs, inventory management, automated invoicing, and shopping cart checkouts.
  * **Resilient API Tier:** Engineered scalable REST APIs and intelligent rate-limiting/throttling subsystems to safeguard backend stability against traffic spikes.

### pluriWow E-Commerce & Checkout Suite
* **Role & Organization:** Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
* **Domain & Ecosystem:** E-Commerce, Payment Orchestration, Automated Sales Funnels.
* **Technologies:** Stripe API, Payment Gateway Integrations, Sales Automation, Java.
* **Key Deliverables & Practical Impact:**
  * **Frictionless Payment Processing:** Built the pluriWow checkout flow, integrating `Stripe` for automated credit card handling, recurring billing, and multi-currency transactions.
  * **Order Fulfillment Automation:** Implemented backend sales automation pipelines reducing merchant operational overhead across fulfillment, notifications, and invoicing.

### Instream Multi-Channel Marketing Automation
* **Role & Organization:** Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
* **Domain & Ecosystem:** Marketing Automation, Omnichannel Campaign Management, Conversion Analytics.
* **Technologies:** Social Media APIs (Facebook, Twitter/X, LinkedIn), Email/SMS Gateways, CTA Tracking Analytics, REST APIs.
* **Key Deliverables & Practical Impact:**
  * **Unified Omnichannel Broadcast Engine:** Engineered a marketing automation suite (HubSpot alternative) allowing cross-channel composition, scheduling, and multi-network broadcasting across social platforms, email, and SMS.
  * **Real-Time Conversion Analytics:** Developed real-time Call-To-Action (`CTA`) tracking engines and conversion telemetry to provide actionable ROI metrics for marketing campaigns.

---

## 4. Enterprise ERP, Open-Source & Integration Solutions

### Simple S.A. Enterprise Invoicing & Data Integration Solution
* **Role & Organization:** Senior Software Engineer Contractor · Iteria (Bogotá, Colombia)
* **Domain & Ecosystem:** Enterprise Billing, Electronic Invoicing, Data ETL.
* **Technologies:** `iDempiere`, `OSGi`, Java, SQL, High-Volume Batch ETL.
* **Key Deliverables & Practical Impact:**
  * **Enterprise Invoicing Engine:** Developed a decoupled `OSGi` plugin on `iDempiere` to automate high-throughput electronic invoicing and financial data synchronization for Simple S.A.

### Aminco Legacy ERP Modernization & Migration
* **Role & Organization:** Software Engineer → Senior Software Engineer · Global QSS (Bogotá, Colombia)
* **Domain & Ecosystem:** Enterprise ERP Modernization, Database Migration, Legacy Refactoring.
* **Technologies:** `Compiere 2.5b`, `iDempiere 1.0`, `OSGi` Plugin Architecture, Database Schema Migration, Java.
* **Key Deliverables & Practical Impact:**
  * **Zero-Downtime Legacy Migration:** Led the full-cycle migration of Aminco’s core enterprise ERP from legacy `Compiere 2.5b` to `iDempiere 1.0`.
  * **OSGi Modularization:** Refactored complex proprietary customizations into isolated `OSGi` bundles, eliminating regression risks and securing future upgradability.

### Ecuadorian University ERP & Official Localization of Ecuador (`LEC`)
* **Role & Organization:** Software Engineer · Global QSS (Bogotá, Colombia)
* **Domain & Ecosystem:** Higher Education ERP, Statutory Tax & Regulatory Compliance.
* **Technologies:** `iDempiere`, `OSGi`, Open-Source Development, Ecuadorian Tax Engine.
* **Key Deliverables & Practical Impact:**
  * **Higher Education Implementation:** Designed customized ERP modules for university administration, academic fees, and billing workflows.
  * **Official Open-Source Localization (LEC):** Promoted statutory compliance modules into the official open-source Localization of Ecuador (`LEC`) for iDempiere, establishing standard tax compliance tooling for the regional community.

### `iDempiere` Core Contributions & Regional Localizations
* **Role & Organization:** Software Engineer · Global QSS & Open Source Community
* **Domain & Ecosystem:** Global Open-Source ERP (iDempiere Project), International Financial Systems.
* **Technologies:** `iDempiere` Core, Localization of Colombia (`LCO`), Financial Reporting Engines, Java, i18n.
* **Key Deliverables & Practical Impact:**
  * **Core Engine Contributions:** Submitted upstream patches, bug fixes, and performance improvements to the central `iDempiere` codebase.
  * **Internationalization & LCO:** Contributed to the official Localization of Colombia (`LCO`) and translated the complete `iDempiere` Setup Wizard into Spanish.
  * **Global Financial Reconciliations:** Engineered customized accounting, reconciliation, and financial reporting modules for international enterprises across Colombia and the USA (including `TrekGlobal` client ecosystems).

---

## 5. Applied AI, Deep Learning & Security Intelligence

### Session Behavioral Anomaly Detection System
* **Role & Organization:** Independent Applied AI Research & Engineering (Berlin, Germany)
* **Domain & Ecosystem:** Anomaly Detection, Session Behavioral Analytics, IAM & API Gateway Security, Zero-Trust Architecture.
* **Technologies:** Python, PyTorch, ONNX, Autoencoders, Cyclic Feature Encoding, Dynamic Thresholding, MDR/Explainability Telemetry.
* **Key Deliverables & Practical Impact:**
  * **Unsupervised Deep Learning Autoencoder:** Engineered an unsupervised deep learning anomaly detection architecture trained exclusively on normal behavioral sessions, eliminating dependency on labeled attack datasets.
  * **Symmetric Deep Architecture & Linear Output:** Designed a 5-layer symmetric network (`Input 11 -> 32 -> 16 -> Latent 6 -> 16 -> 32 -> Output 11`) with unbounded linear output to maximize reconstruction error penalties on extreme behavioral outliers.
  * **Feature Preprocessing & Model Segregation:** Implemented sine/cosine cyclic encodings for temporal signals (`Hour`, `Day of Week`), `log(1+x)` compression for geolocation distance, and segregated models for standard vs. privileged user workloads.
  * **Explainability & Low-Latency Deployment:** Integrated per-feature reconstruction error attribution ranking root-cause anomaly signals for incident review; exported artifacts to ONNX for sub-100ms inference in JVM microservice pipelines.

---

## 6. Developer Tooling, CI/CD & Deployment Management

### Cherry Change - Deployment Lifecycle & Release Management Platform
* **Role & Organization:** Software Architect & Lead Developer
* **Domain & Ecosystem:** DevOps Tooling, Release Governance, Deployment Lifecycle Tracking & Team Management.
* **Technologies:** Ruby on Rails, Sidekiq, Redis, PostgreSQL, Docker, Docker Compose, Background Job Processing, Charting & Analytics Dashboards.
* **Key Deliverables & Practical Impact:**
  * **Multi-Stage Deployment Lifecycle Tracking:** Engineered an automated release governance platform to orchestrate and track software deployments across progressive environments (Development, Staging, and Production).
  * **Team Orchestration & Access Management:** Implemented granular team and resource management capabilities, organizing engineers and system resources with role-specific visibility and execution controls.
  * **Statistical Cadence Dashboards & Analytics:** Designed visualization dashboards providing telemetry on deployment frequency, status distributions (daily, weekly), and release health metrics to optimize team delivery cadence.
  * **Asynchronous Jobs & Automated Snapshotting:** Integrated `Sidekiq` and `Redis` to drive resilient background processing for automated system state snapshots, scheduled maintenance tasks, and transactional email alerts.
  * **Containerized Environment Portability:** Built comprehensive `Docker` and `Docker Compose` configurations ensuring reproducible, isolated development, staging, and deployment workflows.

### Ubirch Scala Client SDK (`ubirch-client-scala`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** JVM SDK, Cryptographic Protocol Implementation, Client-Side Data Integrity & Key Resolution.
* **Technologies:** Scala, Ubirch Protocol Packet (`UPP` / `ubirch-protocol-java`), Ed25519 / ECDSA (`ubirch-crypto`), Skinny HTTP Client, JSON4S, Maven/SBT.
* **Key Deliverables & Practical Impact:**
  * **Idiomatic Scala Cryptographic SDK:** Developed the official JVM client library implementing the binary `Ubirch Protocol Packet (UPP)` specification for seamless client-side data hashing, signing, and verification.
  * **Extensible Protocol Signers & Verifiers:** Implemented composable signer and verifier traits (`DefaultProtocolSigner`, `DefaultProtocolVerifier`, `MultiKeyProtocolVerifier`) supporting pluggable keystores and multi-key verification routines.
  * **Dynamic Public Key Resolution:** Built integrated public key provider abstractions (`UbirchKeyService`, `UnencryptedFileKeyProvider`) with local caching and automated remote key fetching from Ubirch Identity Services.

### Ubirch Kafka Service Template (`ubirch-kafka-service-template`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Microservice Architecture, Event-Driven Streaming Boilerplate, Developer Experience & Accelerators.
* **Technologies:** Scala, Apache Kafka, `ubirch-kafka-express` (`event-log-kafka`), Typesafe Config, Prometheus Metrics, Docker, Maven.
* **Key Deliverables & Practical Impact:**
  * **Standardized Event-Driven Service Boilerplate:** Created the reference microservice archetype and starter template leveraging `ubirch-kafka-express` to accelerate new backend streaming service bootstrap across the engineering organization.
  * **Pre-Configured Ingestion & Transformation Pipeline:** Embedded opinionated configuration structures, JSON serialization/deserialization abstractions, and sample stream processors demonstrating end-to-end data pipelines with zero boilerplate.
  * **Operational Readiness Out of the Box:** Integrated containerized Docker build specs, JVM graceful shutdown handlers, and Prometheus telemetry endpoints out-of-the-box, enforcing standard production readiness across engineering squads.

### ZooKeeper Service Discovery & Leadership Election Framework (`zookeeper-service-discovery`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Distributed Coordination, High Availability, Dynamic Cluster Topology & Leader Election.
* **Technologies:** Java, Scala, Apache ZooKeeper, Apache Curator (`curator-x-discovery`), Akka HTTP, Monix, Distributed Locks, Maven.
* **Key Deliverables & Practical Impact:**
  * **Distributed Coordination & Service Discovery:** Architected a modular service discovery framework using `Apache ZooKeeper` and `Apache Curator` enabling dynamic microservice registration, heartbeat monitoring, and automatic consumer routing.
  * **Resilient Distributed Leader Election:** Implemented leader election recipes enabling distributed worker clusters to dynamically elect leader instances for singleton job coordination and seamlessly transfer leadership upon node failure.
  * **Decoupled Multi-Module Architecture:** Designed a clean three-tier structure (`common`, `service`, `discovery`) encapsulating Curator client lifecycles, provider registration hooks, and consumer discovery listeners.

### Distributed Attestation Load Testing & Simulation Engine (`load-tests-sim`)
* **Role & Organization:** Lead / Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
* **Domain & Ecosystem:** Performance Engineering, High-Throughput Stress Simulation, Distributed Load Generation.
* **Technologies:** Scala, Gatling, Apache Kafka, Async HTTP, Cryptographic Key Generation (`ubirch-crypto`, `ubirch-protocol-java`), Docker.
* **Key Deliverables & Practical Impact:**
  * **Large-Scale Distributed Simulation Harness:** Engineered a high-throughput load testing and benchmarking suite using `Gatling` and `Scala` to simulate real-world IoT sensor fleets transmitting millions of cryptographic payloads.
  * **Automated Device & Key Generation Suite:** Built high-velocity synthetic dataset generators (`DeviceGenerator`, `KeyRegistration`, `DataGenerator`) creating thousands of cryptographic identities, public keys, and signed hash payloads for stress simulations.
  * **Continuous Rate & Peak Benchmark Scenarios:** Developed specialized Gatling simulation models (`SendHashApproxRateSecondsSimulationContinuous`, verification stress tests) benchmarking latency degradation, Kafka ingestion back-pressure, and microservice recovery thresholds under sustained multi-thousand TPS load.
