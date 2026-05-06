# Fraud Detection Engine — Feature & Functionality Survey

> Candidate #145 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| FICO Falcon Fraud Manager | Commercial SaaS | Proprietary (enterprise licence) | https://www.fico.com/en/products/fico-falcon-fraud-manager |
| SAS Fraud Management | Commercial SaaS | Proprietary (enterprise licence) | https://www.sas.com/en_us/software/fraud-management.html |
| Hawk AI | Commercial SaaS | Proprietary (usage-based subscription) | https://hawk.ai/ |
| SEON | Commercial SaaS | Proprietary (from ~$599/month) | https://seon.io/ |
| Flagright | Commercial SaaS | Proprietary (usage-based subscription) | https://www.flagright.com/ |
| Fraud.net | Commercial SaaS | Proprietary (enterprise contract) | https://www.fraud.net/ |
| Alessa | Commercial SaaS | Proprietary (subscription) | https://alessa.com/ |
| Justt (formerly Chargebacks911) | Commercial SaaS | Proprietary (revenue-share model) | https://justt.ai/ |

## Feature Analysis by Solution

### FICO Falcon Fraud Manager

**Core features**
- Real-time transaction scoring across all payment channels (card, ACH, P2P, digital, real-time payments)
- 100% transaction scoring with adaptive self-calibrating analytics
- Portfolio of 120+ patented machine learning techniques
- Cross-channel behavioral profiling
- Support for authorization-time fraud prevention at point-of-sale
- Integration with global financial consortium data
- 50% better fraud detection than rule-based systems

**Differentiating features**
- Patented portfolio of 120+ ML techniques built over decades of domain expertise
- Seamless authorization-time scoring for first-dollar fraud prevention
- Global consortium data informing model development
- Adaptive self-calibration reducing manual tuning

**UX patterns**
- Enterprise integration with authorization systems
- Configurable scoring thresholds per risk appetite
- Decision API with latency optimized for real-time authorization

**Integration points**
- Direct authorization system integration for pre-approval scoring
- Real-time data feeds from financial consortium
- Webhook and API-based decision delivery
- Support for multiple payment processor ecosystems

**Known gaps**
- Very high enterprise costs limit accessibility to smaller institutions
- Complex implementation and customization requires consulting services
- Limited transparency into which of 120+ techniques are applied per transaction

**Licence / IP notes**
- Proprietary SaaS; 120+ patented ML techniques represent significant IP; no licensing conflicts but advanced ranking/profiling methods may be patent-protected

---

### SAS Fraud Management

**Core features**
- Real-time in-memory processing scoring 100% of transactions
- Industry-leading throughput (>10,000 transactions per second)
- Industry-leading latency (<50 milliseconds)
- Smart middleware for scaling and throttling under load
- Support for all messaging protocols (AMQP, sockets, file-based, JMS, JSON, REST)
- High-volume environment optimization
- Multi-channel fraud detection

**Differentiating features**
- Highest throughput benchmark in industry
- Lowest latency response times
- In-memory processing architecture for sustained high-volume performance
- Enterprise-grade infrastructure management built-in

**UX patterns**
- Enterprise system administration interface
- Configuration of protocol stacks and messaging middleware
- Performance monitoring and tuning dashboards
- Batch and real-time processing modes

**Integration points**
- Messaging middleware support (AMQP, JMS, MQTT)
- REST, JSON, and socket-based APIs
- File-based batch processing
- Deep integration with enterprise data systems

**Known gaps**
- Requires significant infrastructure footprint and DevOps expertise
- Steep learning curve for system configuration
- Pricing and deployment complexity
- Limited transparency on algorithmic approach

**Licence / IP notes**
- Proprietary SaaS; in-memory processing architecture may incorporate patented techniques in parallel query execution; no identified patent encumbrances but advanced algorithmic IP likely

---

### Hawk AI

**Core features**
- Rail-agnostic API supporting ACH, SEPA, Wire, Card, P2P, Check, Real-Time Payments
- 150 ms average response time for decision delivery
- Real-time fraud detection across all payment rails
- Cross-rail analysis detecting hop-over patterns and coordinated fraud
- Payment interdiction (block, hold, release) capabilities
- Out-of-the-box rule guidance for ACH/wire fraud, card fraud, check fraud, merchant fraud
- ATM fraud detection

**Differentiating features**
- Native multi-rail support with single unified API vs. siloed detection per channel
- Cross-rail pattern detection identifying fraud across payment types
- Rapid 150 ms response time enabling real-time interdiction
- Emerging/newer vendor with modern API-first architecture

**UX patterns**
- RESTful API for rule-based configuration
- Real-time decision delivery with clear accept/decline/review signals
- Dashboard for rule management and monitoring
- Payment interdiction control panel

**Integration points**
- REST API for all payment rails
- Webhook callbacks for asynchronous decision delivery
- Integration with core banking and payment systems
- API for custom rule definition

**Known gaps**
- Smaller vendor ecosystem compared to established players
- Limited documentation on advanced multi-rail correlations
- Less extensive domain knowledge vs. FICO/SAS
- Newer entrant may lack long-term historical performance data

**Licence / IP notes**
- Proprietary SaaS; modern API architecture but no identified patent encumbrances; cross-rail detection logic may incorporate proprietary techniques

---

### SEON

**Core features**
- Device fingerprinting with 900+ first-party digital footprint signals
- Email, phone, and IP intelligence APIs with historical data and breach detection
- Network intelligence graph mapping relationships across devices, IPs, and emails
- Device security checks (jailbreak/root detection, emulator detection, private browsing)
- Behavioral device data analysis (typing speed, battery, orientation, hardware/software config)
- Real-time fraud decisions across customer journey (synthetic identity, bot, promo abuse, ATO, payment fraud)
- Multi-platform web and mobile support

**Differentiating features**
- Breadth of digital identity signals (900+) from 300+ platforms
- Network graph revealing fraud and money laundering rings without manual searching
- Comprehensive journey-based fraud detection vs. point solution
- Device behavioral signals (typing speed, battery) add biometric-like discrimination

**UX patterns**
- API-first integration for device fingerprinting
- Dashboard for customer risk assessment
- Network graph visualization for ring detection
- Real-time scoring with explainable signal contribution

**Integration points**
- REST API for device fingerprinting on web and mobile
- Email, phone, IP intelligence APIs
- Webhook callbacks for risk scoring
- Data enrichment via third-party breach and reputation databases
- Network graph API for relationship analysis

**Known gaps**
- GDPR/privacy concerns with extensive device fingerprinting and profile linking
- Requires user consent for device signal collection
- Network graph analysis creates privacy risks requiring careful compliance review

**Licence / IP notes**
- Proprietary SaaS; extensive device fingerprinting and behavioral signal techniques are proprietary; GDPR compliance note: device fingerprinting requires explicit consent and transparent privacy policy, flagged for legal review

---

### Flagright

**Core features**
- Real-time transaction monitoring with sub-500ms decision latency
- No-code rule builder for unlimited monitoring rules
- Dynamic risk scoring updating in real time based on transaction and behavioral patterns
- Rule recommendation and threshold recommendation AI
- 93% fewer false positives reported by users
- 80% lower compliance costs compared to fragmented tools
- Support for rule nesting, aggregation variables, and complex logic
- Integration with automated investigation (AIF) templates

**Differentiating features**
- True no-code rule builder enabling non-technical analysts to create rules
- AI-driven rule and threshold recommendation reducing tuning overhead
- False positive reduction claim (93%) notably competitive
- Rapid deployment and onboarding vs. enterprise platforms

**UX patterns**
- Drag-and-drop no-code rule interface
- Rule recommendation engine guiding best practices
- Risk-based thresholds with visual editors
- Real-time performance monitoring dashboard

**Integration points**
- REST API for transaction submission
- Webhook callbacks for alerts and decisions
- Integration with case management systems
- API for rule import/export and bulk configuration

**Known gaps**
- Limited historical analytic depth for mature compliance programs
- Smaller vendor ecosystem
- Less integration with advanced AML/sanctions screening tools
- May lack scale for very-high-volume environments

**Licence / IP notes**
- Proprietary SaaS; rule recommendation and threshold optimization techniques are proprietary; no identified patent encumbrances

---

### Fraud.net

**Core features**
- Custom machine learning models trained on organization-specific data
- Graph neural networks for detecting fraud rings and coordinated activity
- Multi-layered ML approach (supervised models, anomaly detection, GNNs)
- Real-time, adaptive risk scoring
- 30% reduction in review time reported by users
- Up to 92% false positive reduction
- Global Anti-Fraud Network for cross-industry threat intelligence mesh
- Advanced anomaly detection for novel fraud schemes

**Differentiating features**
- Graph neural networks for complex relationship detection vs. traditional single-transaction models
- Custom ML models tailored to organization's fraud patterns and business rules
- Cross-industry intelligence sharing network (with data-sharing agreement)
- Multi-layered ML combining supervised, unsupervised, and graph-based approaches

**UX patterns**
- Model training interface for organization-specific customization
- Dashboard for monitoring and analyzing fraud patterns
- Alert prioritization based on risk scoring
- Graph visualization for relationship analysis

**Integration points**
- Data import/export for model training
- REST API for real-time scoring
- Webhook callbacks for alerts
- Integration with SIEM and case management systems
- Global Anti-Fraud Network API for threat intelligence

**Known gaps**
- Requires data-sharing agreement to participate in threat intelligence mesh
- Custom model training requires historical fraud data and domain expertise
- Competitive pressure from cross-industry sharing may limit participating institutions
- Smaller vendor footprint vs. FICO/SAS

**Licence / IP notes**
- Proprietary SaaS; graph neural networks represent significant algorithmic IP; GNN techniques in financial fraud detection may be subject to existing patents—recommend independent legal review before deep architectural adoption of GNN ranking systems

---

### Alessa

**Core features**
- Real-time sanctions screening against infraction lists
- Automated risk scoring for customer due diligence
- Drag-and-drop workflow designer for AML/compliance processes
- Support for multiple transaction types (wires, SWIFT, ACH, CHAPS, Interac)
- Entity screening across all payment transaction parties
- Real-time decision communication to integrated systems
- Periodic and on-demand screening modes
- Automated case and report generation

**Differentiating features**
- Integrated AML compliance suite (not fraud-only)
- User-friendly workflow designer reducing analyst burden
- Real-time interdiction with immediate system communication
- Automated regulatory report filing

**UX patterns**
- Drag-and-drop workflow configuration
- Visual case management dashboard
- Risk scoring with automated alerts
- Report generation and filing UI

**Integration points**
- Integration with transaction processing systems
- Direct connectivity to regulatory filing systems
- REST API for screening and decision queries
- Webhook callbacks for alerts
- Integration with core banking platforms

**Known gaps**
- UI design more dated than newer competitors
- Less sophisticated ML/AI vs. pure fraud detection platforms
- Better suited to regulatory compliance than fraud prevention
- Limited advanced analytics for pattern detection

**Licence / IP notes**
- Proprietary SaaS; no identified IP encumbrances; compliance-focused architecture is standard industry practice

---

### Justt (formerly Chargebacks911)

**Core features**
- Automated chargeback dispute representment
- Customized compelling evidence 3.0 package compilation per dispute
- Machine learning-driven evidence selection per argument type
- ROI prediction per dispute (win probability + chargeback value - fees)
- Dispute recommendation engine (fight vs. accept decision)
- Dynamic argument tuning based on industry and merchant learnings
- Visa Compelling Evidence 3.0 standardized framework support
- Real-time information sharing for dispute substantiation

**Differentiating features**
- Per-dispute/per-argument evidence customization vs. one-size-fits-all templates
- ROI prediction enabling rational dispute selection
- Continuous improvement of win rates through machine learning
- Compelling Evidence 3.0 integration for next-gen dispute framework

**UX patterns**
- Dispute dashboard with ROI indicators
- One-click evidence package generation
- Recommendation engine showing fight/accept decision with rationale
- Learning feedback loop from dispute outcomes

**Integration points**
- REST API for dispute intake
- Integration with payment processor dispute APIs
- Webhook callbacks for dispute status
- Integration with merchant reporting systems

**Known gaps**
- Reactive approach to fraud (post-transaction) vs. preventive
- Primarily merchant-focused rather than issuer-focused
- Limited to chargeback disputes vs. broader fraud prevention
- Competitive fit only for merchants with significant chargeback volume

**Licence / IP notes**
- Proprietary SaaS; revenue-share model on recovered amounts; no identified IP encumbrances; Compelling Evidence 3.0 is Visa standard (patent unclear but public specification)

---

## Cross-Cutting Feature Themes

### Table-Stakes Features

- **Real-time transaction scoring** — All competitors offer sub-second to 150ms decision latency enabling contemporaneous fraud prevention at authorization time
- **Multi-channel support** — All support at least cards and ACH; modern platforms support 5+ payment rails (SEPA, Wire, P2P, etc.)
- **Rules or ML-based ranking** — All use either rule engines (Flagright, Alessa) or machine learning (FICO, SAS, Hawk, Fraud.net) or both for scoring
- **Risk scoring with thresholds** — All enable threshold-based decisions (accept/review/decline)
- **API integration** — REST/webhook APIs for system integration standard across all
- **Compliance workflow** — All support escalation, case routing, and regulatory reporting
- **False positive reduction** — All claim substantial FPR reduction (70–93%)

### Differentiating Features

- **Graph neural networks** — Fraud.net's GNN for detecting fraud rings and coordinated activity across multiple transactions/entities (vs. single-transaction models in competitors)
- **Cross-rail pattern detection** — Hawk AI's unique ability to detect patterns across different payment rails (hop-overs) in unified system
- **Real-time behavioral device signals** — SEON's 900+ device fingerprint and behavioral signals (typing speed, battery, orientation) vs. transaction-only scoring
- **No-code rule building** — Flagright's (and Alessa's) drag-and-drop rule builder for non-technical analysts vs. API-only or consulting-heavy competitors
- **Custom ML models** — Fraud.net's organization-specific training vs. pre-trained generic models
- **Authorization-time fraud prevention** — FICO's integration directly into payment authorization vs. post-transaction detection
- **Chargeback automation** — Justt's specialized approach to evidence compilation and ROI prediction for dispute management
- **Enterprise throughput** — SAS's >10K transactions/second benchmark for core banking scenarios

### Underserved Areas / Opportunities

- **Reinforcement learning for dynamic rule optimization** — No solutions mentioned autonomous rule adjustment based on outcome feedback loops; rule tuning remains manual or requires consulting
- **Synthetic identity fraud at scale** — While SEON addresses synthetic ID detection, no solution highlighted advanced matching of structural/behavioral patterns unique to synthetic fraud
- **Federated learning across institutions** — Research indicates federated learning enables cross-institution training without data centralization, but no vendor mentioned this (privacy-preserving model sharing remains theoretical in practice)
- **Explainability and transparency** — While Flagright mentions risk scoring, none highlighted natural-language explanations of why a transaction was flagged or scoring rationale (black-box scoring remains common)
- **Coordinated attack detection (MADS)** — Fraud rings operating across multiple merchants/accounts simultaneously; no vendor mentioned explicit multi-merchant coordinated attack detection
- **Regulatory scenario automation** — FATF guidance and AML rules are static; no vendor mentioned AI-driven scenario generation for emerging regulatory requirements
- **Real-time inventory integration** — Digital goods fraud (gifting, account stuffing) requires inventory state; no solution highlighted inventory depletion as fraud signal
- **Bias detection and fairness** — No vendor mentioned bias auditing or fairness testing of ML models despite regulatory interest in non-discrimination

### AI-Augmentation Candidates

- **Natural-language rule authoring** — Convert fraud analyst intent ("detect rapid account changes combined with velocity spike") into rules automatically via LLM
- **Generative synthesis of rare fraud scenarios** — Address class imbalance by synthesizing minority-class examples (synthetic fraud, rare patterns) for model training
- **Multi-modal anomaly detection** — Combine transaction, device, network, and time-series signals into a unified anomaly detection model vs. siloed scoring
- **Counterfactual explanation** — Generate "what-if" explanations showing which factors could have changed a decision (interpretability)
- **Continuous adversarial testing** — AI-generated adversarial fraud examples to identify weaknesses in detection models before attacks materialize
- **Cross-institution federated learning** — Collaboratively train shared models across institutions without centralizing transaction data
- **Outcome-driven rule refinement** — Observe dispute outcomes and automatically adjust rule thresholds/weights to improve accuracy without manual tuning

---

## Legal & IP Summary

All solutions analysed are proprietary, closed-source SaaS offerings. No open-source components or licence conflicts identified. FICO and SAS hold extensive patent portfolios in machine learning and fraud detection (120+ patented techniques claimed by FICO; SAS's in-memory processing architecture may be patent-protected). Graph neural networks (employed by Fraud.net) represent an area of active patent development in machine learning—Fraud.net's specific GNN implementations may be patent-subject; independent legal review recommended before adopting GNN-based ranking as core architecture. Flagright's rule recommendation and threshold optimization techniques are proprietary. SEON's extensive device fingerprinting and behavioral signal collection raises GDPR/privacy concerns; device fingerprinting requires explicit user consent and transparent privacy policy. No solutions identified copyright, content reproduction, or trademark concerns. Visa's Compelling Evidence 3.0 framework (referenced by Justt/Chargebacks911) is a public standard; patent status unclear but is published specification. No materials were omitted due to uncertainty, but recommend legal review before adopting GNN-based detection or extensive device-signal-based scoring in high-regulation jurisdictions (GDPR, PCI DSS).

---

## Recommended Feature Scope

Based on the feature survey above, the project should prioritise the following scope to compete in fraud detection:

**Must-have (MVP)**
- Real-time transaction scoring API with sub-500ms latency supporting cards and ACH at minimum
- Rules-based decision engine (boost, bury, block actions) with API configuration
- Basic ML model for transaction-level risk scoring (supervised learning on historical fraud/non-fraud)
- Multi-channel support (cards, ACH, P2P minimum; expandable to SEPA, Wire)
- Alert and case management workflow with thresholds and escalation
- Dashboard for monitoring fraud rates and model performance
- Integration with core payment/banking systems via REST API

**Should-have (v1.1)**
- Graph neural networks for detecting fraud rings and coordinated multi-transaction patterns
- No-code rule builder for non-technical fraud analysts
- Behavioral device fingerprinting and multi-signal scoring (IP, device ID, velocity)
- Cross-rail pattern detection identifying coordination across payment channels
- Automated rule and threshold recommendation via AI
- Custom ML model training on organization-specific fraud data
- Regulatory compliance workflow (AML, sanctions screening, reporting)
- 24-hour lookback analytics and pattern analysis

**Nice-to-have (backlog)**
- Explainability layer providing natural-language reasoning for fraud scores
- Federated learning enabling cross-institution model training without data sharing
- Generative synthesis of rare fraud scenarios for improving model training
- Chargeback dispute automation (evidence compilation, ROI prediction)
- Real-time entity risk scoring and network relationship mapping
- Continuous adversarial testing to identify and patch model weaknesses
- Outcome-driven autonomous rule refinement based on dispute/appeal results
