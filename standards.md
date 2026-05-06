# Standards & API Reference

> Project: Fraud Detection Engine · Generated: 2026-05-03

## Industry Standards & Specifications

### ISO Standards

**ISO 37003:2025 — Fraud Control Management Systems**
- URL: https://www.iso.org/standard/37003
- Relevance: Published May 2025, ISO 37003 is the first globally recognised standard providing guidance for building a Fraud Control Management System (FCMS). It covers internal, external, collusive, and third-party fraud across a four-pillar model: prevention, detection, response, and continual improvement. Applicable to all organisations regardless of type or size. A fraud detection engine implementing ISO 37003 principles demonstrates regulatory alignment when tendering to enterprise financial institutions and helps organisations pass audits under fraud risk management frameworks.

**ISO 20022 — Financial Messaging Standard**
- URL: https://www.iso20022.org/iso-20022
- Relevance: ISO 20022 replaced legacy SWIFT MT formats with rich MX message formats; SWIFT's coexistence period ended November 2025, making MX formats mandatory for cross-border payments. ISO 20022 expands fraud-relevant data fields from 5–7 in legacy formats to 20+ structured elements — including debtor/creditor names, addresses, account IDs, remittance references, and payment purpose codes. Fraud detection engines that parse ISO 20022 MX fields can apply significantly more precise scoring logic, as highlighted by the Federal Reserve's guidance on using ISO 20022 for fraud mitigation. Mandatory reading for any engine targeting SWIFT-connected financial institutions.

**ISO/IEC 27001 — Information Security Management Systems**
- URL: https://www.iso.org/standard/27001
- Relevance: De facto certification requirement for SaaS platforms handling sensitive financial transaction data. Fraud detection engines process highly sensitive data (transaction records, device fingerprints, behavioural profiles) that financial institution clients will require to be protected under ISO 27001 environments. SOC 2 Type II is the US-market equivalent.

**ISO 31000:2018 — Risk Management Guidelines**
- URL: https://www.iso.org/standard/65694.html
- Relevance: The international framework for risk management principles and guidelines. ISO 31000 provides the conceptual underpinning for risk-based fraud scoring — scoring thresholds, risk appetite calibration, and escalation workflows should align with ISO 31000 principles. Often referenced alongside ISO 37003 for fraud control programme design.

### W3C & IETF Standards

**RFC 6749 — OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- Relevance: The authentication standard for fraud detection API integrations with payment processors, core banking systems, and e-commerce platforms. Fraud engines that expose APIs must implement OAuth 2.0 to enable secure, scoped access by integration partners without sharing master credentials. Particularly relevant for Stripe Radar-style platform integrations where per-merchant scoring is required.

**RFC 6750 — OAuth 2.0 Bearer Token Usage**
- URL: https://datatracker.ietf.org/doc/html/rfc6750
- Relevance: Defines how OAuth access tokens are transmitted in API requests. Required for all fraud engine API integrations with payment and banking platforms.

**RFC 7231 — HTTP/1.1 Semantics and Content**
- URL: https://datatracker.ietf.org/doc/html/rfc7231
- Relevance: Defines HTTP method semantics, status codes, and caching for REST APIs. Critical for correct idempotency in fraud scoring endpoints — a transaction submitted twice due to a network retry must not be scored twice or create duplicate case records. Status codes for timeout, rate-limit, and service-unavailable responses must be correctly handled to prevent false decisioning.

**RFC 7807 — Problem Details for HTTP APIs**
- URL: https://datatracker.ietf.org/doc/html/rfc7807
- Relevance: Standardises structured error payloads from REST APIs. Fraud engines must return machine-parseable errors distinguishing between invalid transaction format, scoring engine timeout, insufficient data, and policy violation — enabling calling systems to implement deterministic retry and fallback logic.

### Data Model & API Specifications

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://spec.openapis.org/oas/v3.1.0.html ; https://swagger.io/specification/
- Relevance: The industry standard for REST API documentation. Flagright, SEON, Sardine, and Stripe Radar all provide OpenAPI-documented APIs. A fraud detection engine must publish a well-structured OAS 3.1 specification covering scoring endpoints, case management events, rule configuration APIs, and webhook schemas — enabling integration partners to auto-generate SDKs and write contract tests before production deployment.

**JSON Schema 2020-12**
- URL: https://json-schema.org/specification
- Relevance: Standard for validating JSON payloads. Fraud detection engines ingest transaction events from many different source systems with varying data quality. JSON Schema validation of inbound transaction payloads (before scoring) prevents malformed data from corrupting model inputs, causing incorrect scores, or creating compliance audit gaps.

**CloudEvents Specification (CNCF)**
- URL: https://cloudevents.io ; https://github.com/cloudevents/spec
- Relevance: CNCF-graduated standard for event schema and delivery. Fraud engines emit high-value events (transaction.flagged, case.opened, rule.triggered, model.alert) to downstream SIEM, case management, and compliance systems. Adopting CloudEvents provides a consistent, interoperable event envelope — allowing integration partners (Splunk, IBM QRadar, ServiceNow) to consume fraud events without bespoke parsing logic.

**Protocol Buffers (Protobuf) — Google**
- URL: https://protobuf.dev/
- Relevance: High-throughput fraud detection engines (targeting >10K transactions/second as SAS achieves) require binary serialisation formats for internal message queues. Protobuf is the de facto standard for high-performance inter-service communication and is used in Apache Kafka-based scoring pipelines. Relevant for the internal architecture of the scoring engine, not the external-facing API.

### Regulatory & Compliance Standards

**PCI DSS v4.0 — Payment Card Industry Data Security Standard**
- URL: https://www.pcisecuritystandards.org/document_library/
- Relevance: Fraud detection engines that receive raw cardholder data (PANs, CVVs) as part of transaction scoring are directly in PCI scope. PCI DSS v4.0 requires MFA for all access to cardholder data environments (effective March 2025), continuous monitoring and automated anomaly detection, and encryption of cardholder data both at rest and in use. Fraud engines must either be PCI-certified or handle only tokenised transaction data to minimise PCI scope. PCI DSS v4.0.1 clarifications also address audit logging requirements relevant to fraud investigation workflows.

**PSD2 / Strong Customer Authentication (SCA) — EU Regulation**
- URL: https://www.eba.europa.eu/regulation-and-policy/payment-services-and-electronic-money/regulatory-technical-standards-on-strong-customer-authentication-and-secure-communication-under-psd2
- Relevance: EU regulation requiring two-factor authentication on electronic payments via 3D Secure 2 (3DS2). Fraud engines must be SCA-aware: they must model Transaction Risk Analysis (TRA) exemptions (transactions below €30 or assessed as low-risk by the fraud engine can bypass SCA), and must correctly handle authentication failure events in their scoring model. SCA-authenticated transactions show card fraud rates 10× lower than non-SCA transactions (ECB/EBA data). The fraud engine is the entity that produces the TRA score that determines whether SCA is required.

**FATF 40 Recommendations — Anti-Money Laundering**
- URL: https://www.fatf-gafi.org/en/publications/Fatfrecommendations/Fatf-recommendations.html
- Relevance: The Financial Action Task Force's 40 Recommendations are the international AML/CFT standard implemented through national law in 200+ jurisdictions. FATF Recommendation 10 (Customer Due Diligence), Recommendation 20 (Suspicious Transaction Reporting), and Recommendation 21 (Tipping-Off Prohibition) directly govern how fraud detection engines must handle AML transaction monitoring, case escalation, and Suspicious Activity Report (SAR) filing workflows. Rule engines used for AML transaction monitoring must be designed to address FATF-compliant risk scenarios.

**Visa VAMP — Visa Acquirer Monitoring Program**
- URL: https://corporate.visa.com/en/sites/visa-perspectives/security-trust/visa-vamp-program-update-fraud-disputes.html
- Relevance: Effective April 2025, VAMP consolidates Visa Dispute Monitoring Program (VDMP) and Visa Fraud Monitoring Program (VFMP) into a single ratio. As of April 2026, the Excessive threshold is 1.5% VAMP ratio (TC40 fraud reports + TC15 chargebacks combined), with $8-per-transaction enforcement fees and no warning tier. Fraud detection engines for merchants and acquirers must be calibrated against VAMP thresholds. Compelling Evidence 3.0 (CE3.0) representments for Visa reason code 10.4 chargebacks are excluded from VAMP numerator — fraud engines should surface CE3.0-eligible transactions to enable efficient dispute workflow.

**GDPR — General Data Protection Regulation (EU 2016/679)**
- URL: https://gdpr.eu/
- Relevance: Fraud detection engines processing EU transaction data must handle personal data lawfully. GDPR Article 22 specifically addresses automated individual decision-making — where a fraud score leads to an automatic decline without human review, this triggers the right to human review and explanation. Fraud engines must implement explainability mechanisms and provide a human review workflow for automated adverse decisions. Device fingerprinting (used by SEON-style engines) requires explicit consent under GDPR's ePrivacy Directive in EU markets. Data minimisation, purpose limitation, and retention limits apply to all transaction and behavioural data processed.

**OWASP API Security Top 10 (2023)**
- URL: https://owasp.org/API-Security/editions/2023/en/0x11-t10/
- Relevance: Fraud detection APIs are high-value targets — adversaries who can manipulate scoring API responses or bypass authentication can evade detection at scale. Critical risks for fraud engines: Broken Object Level Authorization (a merchant must not be able to query another merchant's fraud scores); Broken Authentication (scoring API access must use tightly scoped credentials); Unrestricted Access to Sensitive Business Flows (scoring endpoints can be probed to reverse-engineer detection thresholds, requiring rate limiting and obfuscation); and Unsafe Consumption of Third-Party APIs (enrichment data from IP reputation and device fingerprint providers must be validated before use in scoring).

**NIST Cybersecurity Framework 2.0 (CSF 2.0)**
- URL: https://www.nist.gov/cyberframework ; https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf
- Relevance: CSF 2.0 (published 2024) added a sixth "Govern" function to the original five (Identify, Protect, Detect, Respond, Recover). Financial institutions using NIST CSF 2.0 as their primary cybersecurity self-assessment framework expect fraud detection products to demonstrate alignment with the Detect and Respond functions. The Financial Services Sector-Specific CSF Profile provides sector-tailored guidance that fraud engine integrations should address.

### MCP Server Specifications

**Model Context Protocol (MCP) — Agentic Fraud Investigation**
- URL: https://modelcontextprotocol.io/ ; https://www.businesswire.com/news/home/20260316016511/en/Fingerprint-Launches-Industry-First-MCP-Server-for-Fraud-Prevention
- Relevance: Fingerprint launched the first open-source MCP server for fraud prevention in March 2026, and IBM Safer Payments introduced an MCP server for agentic AI-enabled fraud detection. MCP enables AI agents to query fraud engine APIs directly — accessing transaction history, customer behavioural patterns, and related account activity in real time — reducing fraud investigation time from 8 hours to under 45 minutes according to IBM's data. Fraud detection engines should plan MCP server exposure to enable AI-assisted investigation workflows, where agents can autonomously gather evidence, cross-reference entity relationships, and draft SAR narratives. Gartner predicts 75% of gateway vendors will have MCP features by end of 2026.

---

## Similar Products — Developer Documentation & APIs

### Stripe Radar

- **Description:** Stripe's built-in ML fraud detection trained on $1 trillion+ in annual payment volume. Provides risk scores, custom rules (including AI-generated Radar Assistant rules from natural language), 3DS2 integration, and feedback-loop improvement via Stripe Sigma. Radar for Fraud Teams adds custom rule authoring, backtesting, and manual review queues.
- **API Documentation:** https://docs.stripe.com/radar
- **Rules Reference:** https://docs.stripe.com/radar/rules
- **Developer Guide:** https://docs.stripe.com/radar/integration
- **SDKs/Libraries:** Stripe official SDKs for JavaScript, Python, Ruby, PHP, Java, Go, .NET — https://stripe.com/docs/libraries
- **Standards:** REST/JSON; OpenAPI specification published; webhook events for payment lifecycle
- **Authentication:** API Key (publishable + secret keys); OAuth 2.0 for Stripe Connect

### SEON Fraud API

- **Description:** API-first fraud prevention combining device fingerprinting (900+ signals), email/phone/IP intelligence, network graph analysis, and behavioural signals across web and mobile. Provides a unified fraud score with transparent signal attribution. Used by fintechs, neobanks, and e-commerce platforms.
- **API Documentation:** https://docs.seon.io/api-reference
- **Fraud API Reference:** https://docs.seon.io/api-reference/fraud-api
- **Device Intelligence Guide:** https://docs.seon.io/integration/device-intelligence
- **SDKs/Libraries:** JavaScript SDK (web) — https://github.com/seontechnologies/seon-web-sdk-public ; Android SDK — https://github.com/seontechnologies/seon-android-sdk-public
- **Standards:** REST/JSON; OpenAPI-documented endpoints
- **Authentication:** API Key (secret key in Authorization header)

### Flagright FRAML API

- **Description:** Real-time transaction monitoring SaaS with no-code rule builder, AI-driven threshold recommendations, and sub-500ms scoring latency. Covers consumer and business user journeys, card payments, wires, and crypto transactions. Targets fintechs and payment companies needing rapid AML/fraud compliance deployment.
- **API Documentation:** https://docs.flagright.com/framl-api/api-reference/introduction/getting-started
- **Integration Overview:** https://docs.flagright.com/framl-api/guides/overview/introduction
- **GitHub:** https://github.com/flagright
- **SDKs/Libraries:** Python and Node.js/TypeScript (official); Java (available)
- **Standards:** REST/JSON; API organized around resource-oriented URLs; JSON request/response bodies; standard HTTP status codes
- **Authentication:** API Key (retrieved from Flagright console developer settings)

### Sardine AI Platform

- **Description:** Agentic financial crime platform for banks and fintechs covering fraud prevention, BSA/AML compliance, and sanctions screening. Scores transactions against 12,000+ real-time features across device, behaviour, network, identity, and transaction data. Includes SardineX, a real-time fraud data consortium for cross-institution intelligence sharing. Built by PayPal, Uber, and Coinbase fraud alumni.
- **API Documentation:** https://docs.sardine.ai/home
- **Standards:** REST/JSON; no-code rule editor alongside API-configurable rules
- **Authentication:** API credentials per integration (contact Sardine for developer access)

### Hawk AI Fraud & AML Platform

- **Description:** Rail-agnostic fraud detection and AML transaction monitoring with a single unified API supporting ACH, SEPA, Wire, Card, P2P, Check, and Real-Time Payments. 150ms average response time. Provides cross-rail pattern detection, out-of-the-box rule libraries, and self-serve rule management. Every decision is fully explainable for regulatory transparency.
- **API Documentation:** https://hawk.ai/ (contact vendor for developer portal access; full API documentation behind partner agreement)
- **Standards:** REST/JSON; webhook callbacks for asynchronous decision delivery
- **Authentication:** API credentials per partner integration

### NICE Actimize (IFM-X / AML Essentials)

- **Description:** Enterprise financial crime platform providing integrated fraud management (IFM-X) and AML transaction monitoring. Covers cross-channel payment fraud, cybercrime, sanctions monitoring, market abuse, and customer due diligence. Used by major banks globally. AI/ML-driven with case management and regulatory reporting.
- **API Documentation:** Contact NICE Actimize for developer documentation (enterprise sales process)
- **Standards:** REST/JSON; enterprise integration via middleware connectors; supports messaging protocols used by core banking systems
- **Authentication:** Enterprise SSO and API credentials (Actimize-specific authentication)

### Fingerprint Pro (Device Intelligence MCP)

- **Description:** Device identity and fingerprinting platform providing highly accurate visitor identification across web and mobile. Fingerprint launched the industry's first open-source MCP server for fraud prevention in March 2026, enabling AI agents to query device intelligence in real time for fraud analysis workflows.
- **API Documentation:** https://dev.fingerprint.com/docs/introduction
- **MCP Server:** Open-source MCP server for fraud prevention (announced March 2026 — check Fingerprint GitHub for repository)
- **SDKs/Libraries:** JavaScript, TypeScript, Python, Go, Java, PHP, .NET — https://github.com/fingerprintjs
- **Standards:** REST/JSON; OpenAPI specification; JavaScript agent for browser fingerprinting
- **Authentication:** API Key (public key for browser agent, secret key for server-side API)

### IBM Safer Payments (MCP-enabled)

- **Description:** IBM's enterprise real-time payment fraud prevention platform introduced MCP server support for agentic AI-enabled fraud detection. AI agents can query IBM Safer Payments APIs via MCP to assess transactions, alerts, and emerging threat patterns, reducing investigation time from 8 hours to under 45 minutes.
- **API Documentation:** https://www.ibm.com/products/safer-payments (enterprise sales process for developer documentation)
- **Standards:** REST/JSON; MCP server integration (2026); enterprise messaging protocols
- **Authentication:** IBM IAM; enterprise credentials per deployment

### FICO Falcon Fraud Manager

- **Description:** FICO's industry-leading fraud detection platform covering all payment channels with 120+ patented ML techniques. Provides authorization-time scoring with adaptive self-calibration. Used by major issuers and processors globally as the de facto standard for card fraud detection.
- **API Documentation:** Contact FICO for developer documentation (enterprise partner programme)
- **Standards:** REST/JSON for API integration; supports legacy messaging protocols for direct authorization system integration
- **Authentication:** Enterprise credentials; direct authorization system integration via proprietary protocol

---

## Notes

**MCP as the Emerging Standard for Fraud Investigation Automation:** The March 2026 launches by Fingerprint and IBM of MCP servers for fraud prevention represent a significant architectural shift — fraud investigation workflows that previously required manual analyst work across 5–8 systems can now be orchestrated by AI agents via MCP tool calls. Fraud detection engines built after mid-2026 should include MCP server exposure as a first-class integration concern rather than a future roadmap item.

**ISO 37003 as a Sales Enabler:** ISO 37003:2025 is new enough that few vendors have explicitly aligned their products to it. A fraud detection engine that explicitly maps its features to the ISO 37003 four-pillar model (prevention, detection, response, improvement) gains a competitive advantage in enterprise procurement, particularly with risk and compliance teams who are familiar with ISO standards.

**Federated Learning Gap:** All surveyed vendors provide centralised scoring models. Federated learning for cross-institution model training without data centralisation is referenced in academic literature (see research.md) but not yet implemented by any commercial vendor. This represents a significant open-source opportunity — a fraud detection engine that implements federated learning for cross-institution model improvement could attract financial institution consortia that cannot share raw transaction data.

**VAMP Thresholds Drive Urgency:** Visa's VAMP enforcement (April 2026) has created immediate commercial urgency for merchants whose chargeback/fraud ratios approach the 1.5% Excessive threshold. Fraud detection engines that provide VAMP-specific dashboards and Compelling Evidence 3.0 automation will find a ready buyer in any merchant or acquirer currently above-threshold.
