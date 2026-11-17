# Projects & Technical Initiatives Portfolio

A structured record of engineering projects, architectural initiatives, and system implementations, with domain context and technology stacks.

## Index

- [1. Digital Health, Medical Devices & Regulated Systems](#1-digital-health-medical-devices--regulated-systems)
  - [Recovery Cat · EU MDR Certified Class I Medical Device Platform](#recovery-cat--eu-mdr-certified-class-i-medical-device-platform)
  - [Recovery Cat Architecture & Automated Threat Modeling (`rcc-architecture`)](#recovery-cat-architecture--automated-threat-modeling-rcc-architecture)
  - [Recovery Cat Keycloak Extensions & Custom IAM Plugins (`keycloak-plugins`)](#recovery-cat-keycloak-extensions--custom-iam-plugins-keycloak-plugins)
  - [Recovery Cat User Data Storage API (`rcc-user-data-storage-api`)](#recovery-cat-user-data-storage-api-rcc-user-data-storage-api)
  - [German COVID-19 Digital Vaccination Certificate (`CovPass` / `EU DCC`)](#german-covid-19-digital-vaccination-certificate-covpass--eu-dcc)
- [2. Distributed Systems, Blockchain & Data Integrity Platforms](#2-distributed-systems-blockchain--data-integrity-platforms)
  - [Ubirch Attestation Platform](#ubirch-attestation-platform)
  - [Ubirch Identity Service (`ubirch-id-service`)](#ubirch-identity-service-ubirch-id-service)
  - [Ubirch Token Manager (`ubirch-token-manager`)](#ubirch-token-manager-ubirch-token-manager)
  - [Ubirch Blockchain Service (`ubirch-blockchain-service`)](#ubirch-blockchain-service-ubirch-blockchain-service)
  - [Ubirch Accounting & Metering Service (`ubirch-accounting-service`)](#ubirch-accounting--metering-service-ubirch-accounting-service)
  - [Ubirch Key Service Migration Pipeline (`ubirch-key-service-migration`)](#ubirch-key-service-migration-pipeline-ubirch-key-service-migration)
  - [Ubirch Point of Certification Agent (`ubirch-poc-agent`)](#ubirch-point-of-certification-agent-ubirch-poc-agent)
  - [Ubirch Kafka Express · High-Throughput Streaming & Microservice Abstraction Framework](#ubirch-kafka-express--high-throughput-streaming--microservice-abstraction-framework)
  - [KYCT (Know Your Customer Token) · Decentralized Identity Protocol](#kyct-know-your-customer-token--decentralized-identity-protocol)
  - [Catalina · Ubirch Trust Platform Client & Verification Suite](#catalina--ubirch-trust-platform-client--verification-suite)
  - [Catalina Slack App · Verifiable Message Timestamping](#catalina-slack-app--verifiable-message-timestamping)
  - [Engineering Technical Debt & Quality Governance Framework](#engineering-technical-debt--quality-governance-framework)
- [3. E-Commerce, SaaS & Marketing Automation Platforms](#3-e-commerce-saas--marketing-automation-platforms)
  - [pluriME Multi-Tenant Website-Builder Platform](#plurime-multi-tenant-website-builder-platform)
  - [pluriWow E-Commerce & Checkout Suite](#pluriwow-e-commerce--checkout-suite)
  - [Instream Multi-Channel Marketing Automation](#instream-multi-channel-marketing-automation)
- [4. Enterprise ERP, Open-Source & Integration Solutions](#4-enterprise-erp-open-source--integration-solutions)
  - [Simple S.A. Invoicing & Data Integration Solution](#simple-sa-invoicing--data-integration-solution)
  - [Aminco Legacy ERP Modernization & Migration](#aminco-legacy-erp-modernization--migration)
  - [Ecuadorian University ERP & Official Localization of Ecuador (`LEC`)](#ecuadorian-university-erp--official-localization-of-ecuador-lec)
  - [iDempiere Core Contributions & Regional Localizations](#idempiere-core-contributions--regional-localizations)
- [5. Applied AI, Deep Learning & Security Intelligence](#5-applied-ai-deep-learning--security-intelligence)
  - [Session Behavioral Anomaly Detection System](#session-behavioral-anomaly-detection-system)
  - [Interpretable Portfolio Management Workflow (`portafolio-workflow`)](#interpretable-portfolio-management-workflow-portafolio-workflow)
- [6. Developer Tooling, CI/CD & Deployment Management](#6-developer-tooling-cicd--deployment-management)
  - [Cherry Change · Deployment Lifecycle & Release Management Platform](#cherry-change--deployment-lifecycle--release-management-platform)
  - [Ubirch Scala Client SDK (`ubirch-client-scala`)](#ubirch-scala-client-sdk-ubirch-client-scala)
  - [Ubirch Kafka Service Template (`ubirch-kafka-service-template`)](#ubirch-kafka-service-template-ubirch-kafka-service-template)
  - [ZooKeeper Service Discovery & Leader Election Framework (`zookeeper-service-discovery`)](#zookeeper-service-discovery--leader-election-framework-zookeeper-service-discovery)
  - [Distributed Attestation Load Testing & Simulation Engine (`load-tests-sim`)](#distributed-attestation-load-testing--simulation-engine-load-tests-sim)

## 1. Digital Health, Medical Devices & Regulated Systems

### Recovery Cat · EU MDR Certified Class I Medical Device Platform
- **Role & Organization**: Head of Development · Recovery Cat GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Digital Mental Health, Measurement-Based Care (MBC), Remote Patient Monitoring (RPM), Charité – Universitätsmedizin Berlin spin-off, Berlin Institute of Health (BIH) Digital Health Accelerator, Techniker Krankenkasse (TK) statutory reimbursement contract (later acquired by Resilience Care).
- **Technologies**: EU MDR 2017/745 (Class I SaMD), WebRTC, Keycloak (OIDC/OAuth2), Progressive Web Apps (PWA), Docker, GitLab CI/CD, Threagile (Threat Modeling), Trivy (Vulnerability Scanning), Cross-Browser E2E Testing, Scrum.
- **Key Deliverables & Practical Impact**:
  - **SaMD Architecture & Regulatory Threat Modeling**: Owned the end-to-end software architecture and regulatory security posture for an EU MDR 2017/745 certified Class I Medical Device, protecting psychiatric patient data across inpatient and outpatient care pathways deployed in ~20 German hospital networks and psychiatric clinics.
  - **WebRTC Signaling Rebuild**: Rebuilt the real-time WebRTC signaling architecture from the ground up, eliminating peer connection dropouts and 100% of communication support incidents between Healthcare Professionals (HCPs) and patients.
  - **Zero-Loss Patient Data Migration**: Eliminated critical data loss vulnerabilities inherent to client-side PWA browser caches by building an automated, encrypted backend migration pipeline that preserved full longitudinal clinical histories.
  - **IAM Integration (Keycloak)**: Designed and deployed a multi-tenant, custom-branded Keycloak Identity & Access Management (OIDC/OAuth2) infrastructure, migrating unauthenticated PWA endpoints to role-based access control (RBAC) with per-role session policies.
  - **Automated DevSecOps Pipeline**: Embedded Threagile automated threat modeling and Trivy container scanning directly into GitLab CI/CD pipelines, so every build was threat-checked and scanned for vulnerabilities.
  - **Cross-Browser E2E Testing in CI**: Added end-to-end test runs across multiple browsers to the GitLab CI pipeline, so every change to the patient and clinician PWAs was checked in each supported browser before release.
  - **Unit Test Coverage**: Raised unit test coverage from 10% to between 71% and 90%, depending on the project.
  - **Release Frequency**: Increased production deployments from 3 to 10 or more per year.

### Recovery Cat Architecture & Automated Threat Modeling (`rcc-architecture`)
- **Role & Organization**: Head of Development & Software Architect · Recovery Cat GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Medical Device Security Architecture, STRIDE Threat Modeling, EU MDR 2017/745 & ISO 27001 Compliance, Multi-Cloud Topology.
- **Technologies**: Threagile (Code-as-Threat-Model, Go/YAML), Docker, GitLab CI/CD, Scaleway Kapsule (Kubernetes), Hetzner Bare Metal & Cloud, Traefik, Keycloak (OIDC), PostgreSQL, WebRTC/STUN, Python.
- **Key Deliverables & Practical Impact**:
  - **Executable Threat Model & Architecture-as-Code**: Wrote and maintained the code-driven architecture specification and threat model, mapping 34 technical assets, 16 data assets, 13 trust boundaries, and 44 communication links, with risk reports and data flow diagrams generated automatically for compliance.
  - **Infrastructure-Based Risk Modeling in CI/CD**: Modeled 300 STRIDE/ASVS security risks against the infrastructure actually built, and ran containerized Threagile in the GitLab CI pipelines. This gave the team an organized process to assess, prioritize, and track each risk, and caught security regressions during continuous delivery.
  - **Multi-Cloud Medical Infrastructure Architecture**: Designed and built the operational deployment topology spanning Scaleway Kapsule Kubernetes (production apps, monitoring, and Flux GitOps), dedicated managed PostgreSQL clusters, Hetzner VM infrastructure (STUN signaling, GitLab CI runners), and Jointech Bare Metal hosts (Zammad, Matomo).
  - **Zero-Knowledge Privacy & Real-Time Signaling Topology**: Designed and built the client-side data isolation model featuring browser-local patient storage, QR-code AES cryptographic negotiation, and hybrid WebRTC DataChannel transmission with WebSocket fallback, which together prevent unauthorized access to psychiatric records.

### Recovery Cat Keycloak Extensions & Custom IAM Plugins (`keycloak-plugins`)
- **Role & Organization**: Head of Development · Recovery Cat GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Medical IAM & Identity Federation, Custom Keycloak SPI Extensions, Multi-Realm Healthcare Architecture, German Statutory Health Insurance Integration (§ 290 SGB V).
- **Technologies**: Java 17, Keycloak 26.5 (Quarkus runtime), Keycloak Server SPIs (Authenticator, Event Listener, Validator, custom Provider SPI), Jakarta RESTful Web Services 3.1, JBoss Logging, Lombok, Maven (Shade, Enforcer, Spotless, PMD), JUnit 5, Mockito, Docker, GitLab CI/CD.
- **Key Deliverables & Practical Impact**:
  - **Client-Driven Role & Group Assignment Authenticator**: Built custom Keycloak authentication flow interceptors that map and validate user groups and role privileges based on the calling OIDC client (clinician app or patient app).
  - **German Health Insurance Number (KVN) Checksum Validator**: Implemented strict server-side validation of German statutory health insurance numbers (§ 290 SGB V 10-digit checksum algorithm), preventing invalid medical reimbursement registrations.
  - **Cross-Realm Organization Federation & User Profile Sync**: Built custom Event Listeners and cross-realm validators that synchronize healthcare clinic organizations and update user profile metadata, attributes, and i18n localizations dynamically between administrative and clinical realms.
  - **Insurance Catalog Provider SPI & Cache**: Designed and built a custom Keycloak Provider SPI that fetches, caches (with time-to-live eviction), and synchronizes statutory and private health insurance catalogs, with automated User Profile attribute schema enrichment.
  - **Regulated Date of Birth & Age Gate Validation**: Created configurable minimum/maximum age validators embedded into Keycloak User Profile registration flows for clinical trial and psychiatric SaMD eligibility compliance.

### Recovery Cat User Data Storage API (`rcc-user-data-storage-api`)
- **Role & Organization**: Head of Development · Recovery Cat GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Regulated Medical Device Backend, Encrypted Client-Side Data Storage & Backup, Multi-Tenant OIDC RBAC, SOUP Regulatory BOM Compliance (IEC 62304 & EU MDR).
- **Technologies**: Java 21, Quarkus (REST Jackson, Hibernate ORM Panache, OIDC Multi-Tenant, SmallRye Fault Tolerance, SmallRye Health, Micrometer Prometheus, Scheduler), PostgreSQL 17 (JSONB), Liquibase, MapStruct, Hypersistence Utils, JSON Schema Validation, Lombok, Spotless, PMD, JaCoCo, REST-Assured, Docker Jib & Harbor Registry, GitLab CI/CD.
- **Key Deliverables & Practical Impact**:
  - **Zero-Knowledge Medical Data Persistence & JSONB Schema Enforcement**: Designed and built a compliant REST backend for storing and synchronizing encrypted clinical client state across 12 distinct health data types, using PostgreSQL JSONB storage with time-sorted identifiers and JSON Schema validation.
  - **Multi-Tenant JWT Issuer Resolution**: Implemented custom Quarkus OIDC tenant resolution that inspects the JWT issuer across the clinical and patient Keycloak realms, establishing unified security contexts with fine-grained RBAC policies for patients, clinicians, and administrators.
  - **API-Key Protected Insurance Gateway & Cross-Service Federation**: Built API-key protected internal integration endpoints serving active German health insurance catalogs directly to the Keycloak IAM plugins.
  - **Automated SOUP/SBOM Regulatory Compliance Generator**: Wrote tooling that extracts Software of Unknown Provenance (SOUP) lists from Gradle dependency trees for IEC 62304 & EU MDR Class I medical device technical file audits and post-market surveillance.
  - **Fault-Tolerant Transaction Processing & Real-Time Telemetry**: Integrated SmallRye retry handling for optimistic concurrency and constraint collisions, alongside scheduled Prometheus gauges tracking active patient and clinician counts.

### German COVID-19 Digital Vaccination Certificate (`CovPass` / `EU DCC`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: National Public Health Infrastructure, EU Digital COVID Certificate (EU DCC), German Federal Ministry of Health (BMG) consortium partnership with IBM and Bechtle/GovOS.
- **Technologies**: Scala, Akka (Actors, HTTP, Streams), Apache Kafka, Apache Cassandra, PostgreSQL, Cryptographic Signing (ECDSA/Ed25519), High-Throughput REST APIs.
- **Key Deliverables & Practical Impact**:
  - **National Vaccination Certificate Backend**: Delivered core backend streaming and signing components for the official German Vaccination Proof (*Digitales Impfzertifikat*), integrating thousands of pharmacies (DAV), vaccination centers, and medical practices into the EU DCC trust gateway. More than 250 million certificates were issued.

## 2. Distributed Systems, Blockchain & Data Integrity Platforms

### Ubirch Attestation Platform
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Cryptographic Data Integrity, IoT & Sensor Attestation, Distributed Ledger Anchoring.
- **Technologies**: Scala, Java, Apache Kafka, Apache Cassandra, PostgreSQL, Redis, JanusGraph, Merkle Tree Aggregations, Blockchain Anchoring (IOTA, Ethereum, Polygon).
- **Key Deliverables & Practical Impact**:
  - **Event-Driven Ingestion Pipeline**: Co-developed and maintained the message ingestion microservices (decoding, signature verification, device certificate validation, and high-throughput serialization) handling continuous streams of cryptographic data packets.
  - **Merkle Tree Event Log & Multi-Chain Anchoring**: Built the event log service that aggregates cryptographic hashes into linked Merkle trees and periodically anchors root hashes into public ledgers (Ethereum, IOTA), generating tamper-proof timestamps and verifiable proofs of existence.
  - **Certificate Storage**: Designed a multi-tier storage layer using Cassandra, JanusGraph, and Redis for sub-second verification and cryptographic lineage tracing across thousands of connected devices.

### Ubirch Identity Service (`ubirch-id-service`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Public Key Infrastructure (PKI), Decentralized Identity (DID), Cryptographic Key Lifecycle & Device Attestation.
- **Technologies**: Scala, Monix, Scalatra, Apache Cassandra (Quill), Apache Kafka (Ubirch Kafka Express), Ed25519, ECDSA, X.509 Certificates, Docker, Prometheus.
- **Key Deliverables & Practical Impact**:
  - **Asynchronous High-Throughput PKI Core**: Designed and developed the central identity management microservice handling public key registration, verification, and cryptographic lifecycle management for thousands of IoT devices and identity anchors using Monix and Scalatra.
  - **Multi-Algorithm Cryptographic Key Storage**: Built persistence and retrieval pipelines on Apache Cassandra, supporting Ed25519 and ECDSA public key algorithms, certificate chains, and key revocation lists.
  - **Event-Driven Identity Event Streaming**: Integrated bidirectional Apache Kafka event streaming for instant pub/sub notification of key lifecycle transitions (activation, expiration, and invalidation) across all downstream verification services.
  - **Signature Verification API**: Designed RESTful and streaming verification endpoints enforcing cryptographic signature validation against registered public keys with sub-50ms latency.

### Ubirch Token Manager (`ubirch-token-manager`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Multi-Tenant Access Control, Scoped Token Delegation, API Security & Authorization Infrastructure.
- **Technologies**: Scala, Monix, Scalatra, Apache Cassandra (Quill), JWT, SHA-256 Token Hashing, Keycloak OIDC, Docker, Prometheus.
- **Key Deliverables & Practical Impact**:
  - **Fine-Grained Scoped Token Architecture**: Designed and implemented a multi-tenant token management service issuing cryptographically signed JWTs with fine-grained, per-capability scopes.
  - **Hierarchical Token Delegation & Sub-Token Trees**: Built hierarchical sub-token generation workflows allowing master accounts and enterprise tenants to delegate restricted access rights and expiration policies to downstream devices and automated services.
  - **Cassandra Persistence & SHA-256 Token Verification**: Built a high-throughput validation and persistence pipeline using Apache Cassandra alongside SHA-256 token hashing for sub-millisecond token lookup and authorization checks.
  - **Keycloak & Gateway Interoperability**: Integrated with the Keycloak IAM, translating user identity contexts and bearer tokens into short-lived service tokens for secure inter-service communication.

### Ubirch Blockchain Service (`ubirch-blockchain-service`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Distributed Ledger Technology (DLT), Multi-Chain Anchoring, Public Consensus Validation & Proof of Existence.
- **Technologies**: Scala, Java, IOTA (Native C/JNI & Rust Client), Ethereum/EVM (Web3j), Bloxberg, GovDigital, Apache Kafka, Prometheus.
- **Key Deliverables & Practical Impact**:
  - **Multi-Chain Anchoring Service**: Developed a multi-chain ledger dispatching microservice that consumes aggregated Merkle tree root hashes from Kafka and asynchronously commits cryptographic anchors across public and consortium networks (Ethereum, IOTA, Bloxberg, GovDigital).
  - **High-Throughput IOTA JNI Integration**: Built native JVM-to-C/Rust JNI bindings for the IOTA client library, optimizing transaction payload serialization, tip selection, and proof-of-work delegation under high message volume.
  - **Dynamic Gas Management & Balance Telemetry**: Implemented automated gas price estimation, wallet balance monitors, and Prometheus alerting to guarantee continuous, zero-failure transaction broadcast during network congestion.
  - **Verifiable Transaction Receipt Pipeline**: Built asynchronous receipt generation and validation pipelines returning immutable blockchain transaction hashes and block numbers to the Ubirch attestation lineage.

### Ubirch Accounting & Metering Service (`ubirch-accounting-service`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Usage Metering, Multi-Tenant Billing Telemetry, High-Volume Event Accounting & Auditability.
- **Technologies**: Scala, Monix, Scalatra, Apache Cassandra, PostgreSQL (Flyway), Apache Kafka, Keycloak JWT, Prometheus, Docker.
- **Key Deliverables & Practical Impact**:
  - **High-Volume Event Accounting Service**: Designed and built an event-driven accounting platform tracking, partitioning, and aggregating billable cryptographic operations (anchoring and verification requests) with zero event loss.
  - **Dual-Channel Ingestion & Cassandra Partitioning**: Designed dual Kafka streaming and RESTful HTTP batch ingestion endpoints persisting time-partitioned accounting records into Apache Cassandra for high-write scalability.
  - **Asynchronous Enrichment & Aggregation Jobs**: Built dedicated background enrichment workers using PostgreSQL and Flyway to aggregate raw transaction volumes into monthly tenant usage reports with tag-based filtering.
  - **Secured Multi-Tenant Metering APIs**: Implemented Keycloak OIDC/JWT-authenticated query endpoints allowing enterprise customers to audit, monitor, and export real-time consumption and quota analytics.

### Ubirch Key Service Migration Pipeline (`ubirch-key-service-migration`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Database Migration, Graph-to-Columnar Schema Translation, Zero-Downtime Data Modernization.
- **Technologies**: Scala, Neo4j, Apache HttpClient, JSON4S, CSV Audit Reporting, Docker.
- **Key Deliverables & Practical Impact**:
  - **Graph-to-Distributed Migration Architecture**: Built an automated data migration pipeline extracting historical cryptographic public keys from legacy Neo4j graph databases and translating them into the modern Identity Service Cassandra store.
  - **REST Dispatching & Zero-Downtime Batch ETL**: Implemented batch extraction with cursor pagination, payload normalization, and REST dispatching to Identity Service endpoints with cryptographic verification and retry handling.
  - **Dual-Format Audit & Executive Reporting**: Integrated automated dual-stream reconciliation generating detailed CSV transaction logs and summary reports tracking migrated, updated, and failed key records for regulatory verification.

### Ubirch Point of Certification Agent (`ubirch-poc-agent`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Edge Certification, Hybrid Cloud/On-Premise Gateway, EU Digital Health Interoperability.
- **Technologies**: Scala, Monix, Scalatra, STTP, Ubirch Protocol (UPP), EU Digital COVID Certificate (EU DCC / Base45), Bouncy Castle, Prometheus, Docker.
- **Key Deliverables & Practical Impact**:
  - **Edge Certification Gateway Architecture**: Developed an on-premise and hybrid-cloud certification agent using Scalatra and Monix, acting as a facade that coordinates cryptographic UPP signing and EU DCC health certificate generation.
  - **Dual-Target Dispatching & Coordination**: Built request distribution pipelines using STTP, multiplexing certification workloads across local UPP signers and remote certification APIs with automated fallback and error buffering.
  - **High-Availability Local Ingestion**: Designed lightweight, containerized edge deployment profiles ensuring reliable Base45 payload encoding and certificate issuance in low-connectivity or security-restricted hospital/testing center environments.

### Ubirch Kafka Express · High-Throughput Streaming & Microservice Abstraction Framework
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Event-Driven Architecture, High-Throughput Stream Processing, JVM Microservices, Developer Experience & Framework Tooling.
- **Technologies**: Scala, Apache Kafka, Prometheus, JVM Concurrency (Futures/Actors), Maven/SBT.
- **Key Deliverables & Practical Impact**:
  - **Standardized Streaming Microservice Framework**: Designed and implemented a generic component abstraction simplifying Kafka consumer and producer initialization across microservices, with unified configuration, deserialization/serialization pipelines, and multi-topic routing.
  - **Consumer Runner with Back-Pressure**: Built a consumer runner with back-pressure, partition rebalance handling, configurable commit and retry policies, and ready-made consumers for common message formats.
  - **Two-Tier Exception Escalation & Fault Isolation**: Implemented two-tier error handling that separates transient failures on single records from fatal partition or broker errors that need escalation.
  - **Embedded Prometheus Telemetry & Graceful Lifecycle Hooks**: Integrated real-time Prometheus throughput and lag monitoring, alongside automated JVM shutdown hooks for consumers and producers ensuring zero-data-loss draining during redeployments.

### KYCT (Know Your Customer Token) · Decentralized Identity Protocol
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Web3, Self-Sovereign Identity, Privacy-Preserving Compliance, Deutsche Telekom & T-Mobile US Innovation Ecosystem.
- **Technologies**: Solidity, ERC-721 Smart Contracts, Ethereum, Polygon, Zero-Knowledge / Non-PII Verification Patterns.
- **Key Deliverables & Practical Impact**:
  - **"Best Solution" Award**: Won **"Best Solution"** at the international T-Challenge 2022/2023 (*Human-Centered Web3 & 5G Innovation*), run by Deutsche Telekom, T-Mobile US, and T-Labs, chosen from 282 teams across 53 countries for privacy-preserving decentralized tokenization.
  - **On-Chain Compliance Tokenization**: Designed and built KYCT, an on-chain identity verification mechanism using ERC-721 non-fungible tokens on Ethereum and Polygon.
  - **Zero-PII Regulatory Proofs**: Enabled decentralized finance (DeFi) protocols and Web3 dApps to cryptographically verify user KYC compliance and accreditation without exposing underlying Personally Identifiable Information (PII).

### Catalina · Ubirch Trust Platform Client & Verification Suite
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Cryptographic Data Integrity, Verifiable Data Auditing, Trust-as-a-Service Cloud APIs.
- **Technologies**: Java, Scala, REST APIs, Cryptographic Micro-Certificates, Merkle Tree Anchoring, Public Ledgers.
- **Key Deliverables & Practical Impact**:
  - **Multi-Source Micro-Certificate Dispatch**: Built client interface modules enabling automated generation and dispatch of cryptographic micro-certificates from diverse data sources (local files, arbitrary text payloads, user inputs, and static strings) to the Ubirch Trust Service.
  - **Trust-as-a-Service Verification Tooling**: Built verification tooling that checks micro-certificates against their public ledger anchors, proving when the data existed and that it has not changed.
  - **Client Integration & Workflow Automation**: Simplified integration pipelines for third-party systems to embed cryptographic attestation and lineage tracking directly into upstream data ingestion workflows.

### Catalina Slack App · Verifiable Message Timestamping
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: ChatOps, Communication Integrity, Immutable Audit Trails.
- **Technologies**: Slack API & Bot Framework, Webhooks, RESTful Integrations, Cryptographic Hashing, Ubirch Trust Service.
- **Key Deliverables & Practical Impact**:
  - **Chat-Native Timestamping & Attestation**: Developed a Slack integration enabling teams to generate tamper-proof, verifiable timestamps and cryptographic snapshots of messages directly inside communication channels.
  - **Zero-Friction Audit Trails**: Automated the conversion of critical chat decisions, operational incidents, and contractual exchanges into immutable proofs anchored via the Ubirch Trust Service.
  - **Instant Verification Workflow**: Added slash commands and message actions that let any channel participant audit and verify message integrity without leaving the Slack client.

### Engineering Technical Debt & Quality Governance Framework
- **Role & Organization**: Lead Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Software Architecture, Engineering Governance, Radar Metrics, CI/CD Quality Gates.
- **Technologies**: Architectural Decision Records (ADRs), Automated CI Testing Suites.
- **Key Deliverables & Practical Impact**:
  - **6-Dimension Evaluation Framework**: Designed and put into practice a structured technical debt assessment matrix across Security, Compliance, Performance, Modifiability, Testability, and Usability/DX.
  - **Sustainable Codebase Modernization**: Guided multi-year codebase refactoring programs, maintaining an 80/20 delivery-to-refactoring balance that continuously reduced vulnerability surface area while feature work continued.

## 3. E-Commerce, SaaS & Marketing Automation Platforms

### pluriME Multi-Tenant Website-Builder Platform
- **Role & Organization**: Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
- **Domain & Ecosystem**: Multi-Tenant SaaS, SMB Digital Enablement, Cloud Content Management.
- **Technologies**: RESTful APIs, Throttling & Rate-Limiting Systems, Java/JVM, Relational Databases, Modular Cloud Services.
- **Key Deliverables & Practical Impact**:
  - **Site Builder**: Developed core platform modules enabling non-technical users to build, customize, and publish digital storefronts, portfolios, and custom domains in minutes.
  - **Commercial Transaction Subsystems**: Built full-lifecycle business modules including dynamic product catalogs, inventory management, automated invoicing, and shopping cart checkouts.
  - **API Tier & Rate Limiting**: Built scalable REST APIs and rate-limiting/throttling subsystems to keep the backend stable during traffic spikes.

### pluriWow E-Commerce & Checkout Suite
- **Role & Organization**: Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
- **Domain & Ecosystem**: E-Commerce, Payment Integration, Automated Sales Funnels.
- **Technologies**: Stripe API, Payment Gateway Integrations, Sales Automation, Java.
- **Key Deliverables & Practical Impact**:
  - **Payment Processing**: Built the pluriWow checkout flow, integrating Stripe for automated credit card handling, recurring billing, and multi-currency transactions.
  - **Order Fulfillment Automation**: Implemented backend sales automation pipelines reducing merchant operational overhead across fulfillment, notifications, and invoicing.

### Instream Multi-Channel Marketing Automation
- **Role & Organization**: Senior Software Engineer · pluriME International Inc. (Bogotá, Colombia)
- **Domain & Ecosystem**: Marketing Automation, Omnichannel Campaign Management, Conversion Analytics.
- **Technologies**: Social Media APIs (Facebook, Twitter/X, LinkedIn), Email/SMS Gateways, CTA Tracking Analytics, REST APIs.
- **Key Deliverables & Practical Impact**:
  - **Multi-Channel Campaign Broadcasting**: Built a marketing automation suite (HubSpot alternative) allowing cross-channel composition, scheduling, and multi-network broadcasting across social platforms, email, and SMS.
  - **Real-Time Conversion Analytics**: Developed real-time Call-To-Action (CTA) tracking and conversion telemetry, giving marketers conversion metrics per campaign.

## 4. Enterprise ERP, Open-Source & Integration Solutions

### Simple S.A. Invoicing & Data Integration Solution
- **Role & Organization**: Senior Software Engineer Contractor · Iteria (Bogotá, Colombia)
- **Domain & Ecosystem**: Billing, Electronic Invoicing, Data ETL.
- **Technologies**: iDempiere, OSGi, Java, SQL, High-Volume Batch ETL.
- **Key Deliverables & Practical Impact**:
  - **Invoicing Plugin**: Developed a decoupled OSGi plugin on iDempiere to automate high-throughput electronic invoicing and financial data synchronization for Simple S.A.

### Aminco Legacy ERP Modernization & Migration
- **Role & Organization**: Software Engineer, later Senior Software Engineer · Global QSS (Bogotá, Colombia)
- **Domain & Ecosystem**: ERP Modernization, Database Migration, Legacy Refactoring.
- **Technologies**: Compiere 2.5b, iDempiere 1.0, OSGi Plugin Architecture, Database Schema Migration, Java.
- **Key Deliverables & Practical Impact**:
  - **Zero-Downtime Legacy Migration**: Led the full-cycle migration of Aminco's core ERP from legacy Compiere 2.5b to iDempiere 1.0.
  - **OSGi Modularization**: Refactored complex proprietary customizations into isolated OSGi bundles, so later iDempiere upgrades no longer broke client customizations.

### Ecuadorian University ERP & Official Localization of Ecuador (`LEC`)
- **Role & Organization**: Software Engineer · Global QSS (Bogotá, Colombia)
- **Domain & Ecosystem**: Higher Education ERP, Statutory Tax & Regulatory Compliance.
- **Technologies**: iDempiere, OSGi, Open-Source Development, Ecuadorian Tax Engine.
- **Key Deliverables & Practical Impact**:
  - **Higher Education Implementation**: Designed customized ERP modules for university administration, academic fees, and billing workflows.
  - **Official Open-Source Localization (LEC)**: Promoted statutory compliance modules into the official open-source Localization of Ecuador (LEC) for iDempiere, giving the regional community shared tax compliance tooling.

### iDempiere Core Contributions & Regional Localizations
- **Role & Organization**: Software Engineer · Global QSS & Open Source Community
- **Domain & Ecosystem**: Global Open-Source ERP (iDempiere Project), International Financial Systems.
- **Technologies**: iDempiere Core, Localization of Colombia (LCO), Financial Reporting Engines, Java, i18n.
- **Key Deliverables & Practical Impact**:
  - **Core Engine Contributions**: Submitted upstream patches, bug fixes, and performance improvements to the central iDempiere codebase.
  - **Internationalization & LCO**: Contributed to the official Localization of Colombia (LCO) and translated the complete iDempiere Setup Wizard into Spanish.
  - **Accounting & Reconciliation Modules**: Built customized accounting, reconciliation, and financial reporting modules for clients in Colombia and the USA (including TrekGlobal client ecosystems).

## 5. Applied AI, Deep Learning & Security Intelligence

### Session Behavioral Anomaly Detection System
- **Role & Organization**: Independent Engineer · Applied AI Research (Berlin, Germany)
- **Domain & Ecosystem**: Anomaly Detection, Session Behavioral Analytics, IAM & API Gateway Security, Zero-Trust Architecture.
- **Technologies**: Python, PyTorch, ONNX, Autoencoders, Cyclic Feature Encoding, Dynamic Thresholding, MDR/Explainability Telemetry.
- **Key Deliverables & Practical Impact**:
  - **Unsupervised Deep Learning Autoencoder**: Built an unsupervised deep learning anomaly detection architecture trained exclusively on normal behavioral sessions, eliminating dependency on labeled attack datasets.
  - **Symmetric Deep Architecture & Linear Output**: Designed a 5-layer symmetric network (11 input features compressed to a 6-dimensional latent space) with unbounded linear output to maximize reconstruction error penalties on extreme behavioral outliers.
  - **Feature Preprocessing & Model Segregation**: Implemented sine/cosine cyclic encodings for temporal signals (hour, day of week), logarithmic compression for geolocation distance, and segregated models for standard vs. privileged user workloads.
  - **Explainability & Low-Latency Deployment**: Integrated per-feature reconstruction error attribution ranking root-cause anomaly signals for incident review; exported artifacts to ONNX for sub-100ms inference in JVM microservice pipelines.

### Interpretable Portfolio Management Workflow (`portafolio-workflow`)
- **Role & Organization**: Independent Software Architect & Developer · Personal Project
- **Domain & Ecosystem**: Personal Wealth Management, Interpretable Context Methodology, Multi-Stage Analytical Pipelines, Financial Auditing & Rebalancing.
- **Technologies**: Python 3.9+ (standard library only), Yahoo Finance API, CoinGecko API, YAML, Vector SVG Graphics, Markdown Reporting, unittest.
- **Key Deliverables & Practical Impact**:
  - **Interpretable Multi-Stage Workflow Architecture**: Designed and implemented a decoupled 6-stage data pipeline based on the *Interpretable Context Methodology* (arXiv:2603.16021), where intermediate YAML artifacts act as verifiable, human-in-the-loop audit and correction surfaces.
  - **Multi-Asset Price Retrieval**: Built zero-dependency price retrieval modules querying live quotes and historical spot data for equities, ETFs, and cryptocurrencies with built-in rate-limit handling and YAML schema normalization.
  - **Valuation & Asset Allocation**: Developed aggregation scripts computing aggregate holdings value, liquid cash reserves, total portfolio net worth, and granular percentage allocations across asset classes and individual instruments.
  - **Zero-Dependency SVG Visualizations & Markdown Reporting**: Implemented vector charting that generates multi-tier SVG distribution visualizations (overall asset classes vs. ETF breakdowns) and consolidated Markdown summaries.
  - **Longitudinal Historical Run Analytics & Backfilling**: Created historical analysis and backfill tooling to aggregate archived run snapshots, compute temporal deltas and asset drift, and generate trend comparisons across customizable date ranges and offsets.
  - **Automated Test Suite & Character Sanitization**: Built a comprehensive unittest test suite covering valuation mathematics, distribution logic, and schema integrity, accompanied by encoding sanitization tooling to enforce repository-wide character and formatting hygiene.

## 6. Developer Tooling, CI/CD & Deployment Management

### Cherry Change · Deployment Lifecycle & Release Management Platform
- **Role & Organization**: Software Architect & Lead Developer
- **Domain & Ecosystem**: DevOps Tooling, Release Governance, Deployment Lifecycle Tracking & Team Management.
- **Technologies**: Ruby on Rails, Sidekiq, Redis, PostgreSQL, Docker, Docker Compose, Background Job Processing, Charting & Analytics Dashboards.
- **Key Deliverables & Practical Impact**:
  - **Multi-Stage Deployment Lifecycle Tracking**: Built an automated release governance platform to coordinate and track software deployments across progressive environments (Development, Staging, and Production).
  - **Team Coordination & Access Management**: Implemented granular team and resource management capabilities, organizing engineers and system resources with role-specific visibility and execution controls.
  - **Statistical Cadence Dashboards & Analytics**: Designed visualization dashboards providing telemetry on deployment frequency, status distributions (daily, weekly), and release health metrics to optimize team delivery cadence.
  - **Asynchronous Jobs & Automated Snapshotting**: Integrated Sidekiq and Redis to run background processing for automated system state snapshots, scheduled maintenance tasks, and transactional email alerts.
  - **Containerized Environment Portability**: Built comprehensive Docker and Docker Compose configurations ensuring reproducible, isolated development, staging, and deployment workflows.

### Ubirch Scala Client SDK (`ubirch-client-scala`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: JVM SDK, Cryptographic Protocol Implementation, Client-Side Data Integrity & Key Resolution.
- **Technologies**: Scala, Ubirch Protocol Packet (UPP), Ed25519/ECDSA, Skinny HTTP Client, JSON4S, Maven/SBT.
- **Key Deliverables & Practical Impact**:
  - **Idiomatic Scala Cryptographic SDK**: Developed the official JVM client library implementing the binary Ubirch Protocol Packet (UPP) specification for client-side data hashing, signing, and verification.
  - **Extensible Protocol Signers & Verifiers**: Implemented composable signing and verification components supporting pluggable keystores and multi-key verification.
  - **Dynamic Public Key Resolution**: Built public key provider abstractions with local caching and automated remote key fetching from the Ubirch Identity Service.

### Ubirch Kafka Service Template (`ubirch-kafka-service-template`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Microservice Architecture, Event-Driven Streaming Boilerplate, Developer Experience & Accelerators.
- **Technologies**: Scala, Apache Kafka, Ubirch Kafka Express, Typesafe Config, Prometheus Metrics, Docker, Maven.
- **Key Deliverables & Practical Impact**:
  - **Standardized Event-Driven Service Boilerplate**: Created the reference microservice archetype and starter template using Ubirch Kafka Express to speed up new backend streaming service bootstrap across the engineering organization.
  - **Pre-Configured Ingestion & Transformation Pipeline**: Embedded opinionated configuration structures, JSON serialization/deserialization abstractions, and sample stream processors demonstrating end-to-end data pipelines with zero boilerplate.
  - **Operational Readiness Out of the Box**: Included Docker build specs, JVM graceful shutdown handlers, and Prometheus telemetry endpoints, so every new service started production-ready.

### ZooKeeper Service Discovery & Leader Election Framework (`zookeeper-service-discovery`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Distributed Coordination, High Availability, Dynamic Cluster Topology & Leader Election.
- **Technologies**: Java, Scala, Apache ZooKeeper, Apache Curator, Akka HTTP, Monix, Distributed Locks, Maven.
- **Key Deliverables & Practical Impact**:
  - **Distributed Coordination & Service Discovery**: Designed and built a modular service discovery framework using Apache ZooKeeper and Apache Curator enabling dynamic microservice registration, heartbeat monitoring, and automatic consumer routing.
  - **Distributed Leader Election**: Implemented leader election recipes enabling distributed worker clusters to dynamically elect leader instances for singleton job coordination and to hand over leadership automatically upon node failure.
  - **Decoupled Provider & Consumer Libraries**: Split the framework so services could register as providers or discover dependencies independently, pulling in only the side they needed.

### Distributed Attestation Load Testing & Simulation Engine (`load-tests-sim`)
- **Role & Organization**: Lead & Senior Software Engineer · Ubirch GmbH (Berlin, Germany)
- **Domain & Ecosystem**: Performance Engineering, High-Throughput Stress Simulation, Distributed Load Generation.
- **Technologies**: Scala, Gatling, Apache Kafka, Async HTTP, Cryptographic Key Generation, Docker.
- **Key Deliverables & Practical Impact**:
  - **Large-Scale Distributed Simulation Harness**: Built a high-throughput load testing and benchmarking suite using Gatling and Scala to simulate real-world IoT sensor fleets transmitting thousands of cryptographic payloads.
  - **Automated Device & Key Generation Suite**: Built synthetic dataset generators creating thousands of devices, cryptographic identities, public keys, and signed hash payloads for stress simulations.
  - **Continuous Rate & Peak Benchmark Scenarios**: Developed Gatling simulation models (continuous-rate sending and verification stress tests) benchmarking latency degradation, Kafka ingestion back-pressure, and microservice recovery thresholds under sustained multi-thousand TPS load.
