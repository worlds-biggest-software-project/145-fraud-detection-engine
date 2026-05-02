# Fraud Detection Engine

> Candidate #145 · Researched: 2026-05-02

## Existing Products and Software Packages

| Tool | Description | Type | Pricing | Strengths / Weaknesses |
|------|-------------|------|---------|------------------------|
| FICO Falcon Fraud Manager | AI/ML transaction scoring across all payment types and channels in real time | Commercial | Enterprise contract (undisclosed) | Strength: decades of domain data, industry standard in card fraud; Weakness: expensive, slower to customise |
| SAS Fraud Management | In-memory processing scores 100% of transactions in real time at high throughput and low latency | Commercial | Enterprise licence | Strength: highest throughput benchmark; Weakness: heavy infrastructure footprint |
| Hawk AI | Rail-agnostic API with 150 ms average response, supports ACH, SEPA, Wire, Card, P2P | Commercial SaaS | Usage-based (undisclosed) | Strength: speed and multi-rail coverage; Weakness: newer entrant, smaller ecosystem |
| SEON | AI fraud prevention combining device fingerprinting, email/phone intelligence, and graph analysis | Commercial SaaS | From ~$599/month | Strength: transparent scoring, fast onboarding; Weakness: less suited to high-volume core banking |
| Flagright | Real-time transaction monitoring with no-code rule builder and AI risk scoring | Commercial SaaS | Usage-based | Strength: rapid deployment; Weakness: limited historical analytic depth |
| Fraud.net | Custom ML models, graph analytics, and Global Anti-Fraud Network cross-industry intelligence mesh | Commercial SaaS | Enterprise contract | Strength: shared threat intelligence network; Weakness: requires data-sharing agreement |
| Alessa | Real-time screening with risk scores and AML workflow integration | Commercial SaaS | Subscription (undisclosed) | Strength: built-in AML/compliance modules; Weakness: UI dated compared with newer entrants |
| Chargebacks911 / Justt | Automated chargeback dispute management and Visa Compelling Evidence 3.0 filing | Commercial SaaS | % of recovered revenue | Strength: dispute workflow automation; Weakness: reactive rather than preventive |

## Relevant Industry Standards or Protocols

- **ISO 37003:2025** — International standard for fraud control management systems, published May 2025, providing organisation-level guidance on managing internal and external fraud risk
- **ISO 20022** — Rich financial messaging standard replacing legacy SWIFT MT formats; structured data enables more precise fraud pattern detection; mandatory migration deadline November 2025
- **Visa VAMP (Visa Acquirer Monitoring Program)** — Enforcement began October 2025; second-tier acquirer fees added January 2026; Compelling Evidence 3.0 data-sharing framework reduces dispute counts
- **PCI DSS v4.0** — Payment card data security requirements that shape fraud-control architecture, including transaction authentication and audit logging
- **PSD2 / Strong Customer Authentication (SCA)** — EU regulatory requirement for multi-factor authentication on electronic payments, directly influencing fraud engine integration points
- **FATF Recommendations** — Financial Action Task Force anti-money-laundering guidance underpinning transaction monitoring rule design

## Available Research Materials

1. Multiple authors (2024). *Graph Neural Networks for Financial Fraud Detection: A Review*. Frontiers of Computer Science / arXiv:2411.05815. https://arxiv.org/abs/2411.05815 — peer-reviewed
2. Various authors (2024). *CaT-GNN: Enhancing Credit Card Fraud Detection via Causal Temporal Graph Neural Networks*. arXiv preprint, February 2024. https://arxiv.org/abs/2402.xxxxx — not peer-reviewed (preprint)
3. Various authors (2024). *Enhancing Fraud Detection in Banking With Deep Learning: Graph Neural Networks and Autoencoders for Real-Time Credit Card Fraud Prevention*. IEEE Xplore. https://ieeexplore.ieee.org/document/10689393/ — peer-reviewed
4. Various authors (2024). *Real-Time Financial Fraud Detection Using Adaptive Graph Neural Networks and Federated Learning*. International Journal of Management and Data Analytics (IJMADA). https://ijmada.com/index.php/ijmada/article/view/77 — peer-reviewed
5. Jacobs et al. (2023). *Enhancing Vulnerability Prioritization: Data-Driven Exploit Predictions*. WEIS 2023. https://weis2023.econinfosec.org/wp-content/uploads/sites/11/2023/06/weis23-jacobs.pdf — peer-reviewed (related: quantitative risk prioritisation methodology applicable to fraud scoring)
6. Federal Reserve Financial Services (2025). *Using the ISO 20022 Standard to Help Fraud Mitigation*. Fed360 newsletter. https://www.frbservices.org/news/fed360/issues/041526/risk-management-power-of-iso-20022 — practitioner report

## Market Research

**Market Size:** The global fraud detection and prevention market is estimated at USD 67–70 billion in 2026, growing to USD 243–270 billion by 2034 at a CAGR of approximately 17–20%.

**Funding:** Venture investment has shifted toward AI-native startups; Hawk AI raised Series B funding; Justt raised $70 M+ for automated chargeback recovery. Established players (FICO, SAS) remain publicly traded or private-equity-backed with large R&D budgets.

**Pricing Landscape:** Enterprise platforms (FICO, SAS) charge multi-year licences negotiated per transaction volume. SaaS entrants (SEON, Flagright) start from a few hundred dollars per month, scaling with event volume. Chargeback recovery specialists typically take a percentage of successfully recovered disputes.

**Key Buyer Personas:** Fraud operations managers at banks and payment processors; chief risk officers at fintechs; e-commerce fraud teams managing chargeback ratios; AML compliance officers at financial institutions.

**Notable Trends:** Generative-AI-driven synthetic identity fraud is accelerating, forcing real-time graph-based detection. ISO 20022 rich data fields are being exploited to improve scoring precision. Visa's VAMP enforcement is pushing merchants to adopt proactive fraud tools. Federated learning approaches are emerging to allow cross-institution intelligence sharing without exposing raw data.

## AI-Native Opportunity

- Real-time graph neural network scoring can detect fraud rings and coordinated account takeover patterns that rule engines and single-transaction models miss entirely
- LLM-based natural-language rule authoring allows fraud analysts to express detection logic without writing code, dramatically reducing time-to-detection for new fraud types
- Generative AI can synthesise rare fraud scenarios for model training, addressing the persistent class-imbalance problem in labelled fraud datasets
- Federated learning architectures enable a platform to train shared fraud models across many client institutions without centralising sensitive transaction records, providing a legal and competitive advantage
- AI agents can automate the full chargeback dispute lifecycle — evidence gathering, Compelling Evidence 3.0 package assembly, and filing — reducing manual analyst hours per case from hours to minutes
