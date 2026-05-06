# Fraud Detection Engine

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source fraud detection engine providing real-time transaction scoring and chargeback management across multiple payment rails.

Fraud Detection Engine is a real-time, multi-rail transaction scoring platform designed for banks, payment processors, fintechs, and e-commerce operators. It combines rule engines, supervised machine learning, and graph neural networks to detect fraudulent transactions, fraud rings, and coordinated account-takeover patterns. The project targets the gap between expensive enterprise incumbents and narrowly-scoped SaaS entrants by offering an open, extensible alternative.

---

## Why Fraud Detection Engine?

- Enterprise incumbents (FICO Falcon, SAS Fraud Management) require multi-year licences negotiated per transaction volume and consulting-heavy implementations, putting them out of reach for smaller institutions.
- Newer SaaS entrants (Hawk AI, Flagright, SEON) deliver fast onboarding but typically operate as black boxes with limited transparency, smaller ecosystems, or shallow historical analytic depth.
- Most platforms still rely on single-transaction models or manual rule tuning; coordinated fraud rings and cross-rail "hop-over" patterns regularly slip through.
- Federated learning across institutions and natural-language explainability remain theoretical in practice; no major vendor offers either as a first-class feature.
- Chargeback recovery is largely reactive and merchant-focused, leaving issuers and fintechs to stitch together preventive scoring and dispute automation themselves.

---

## Key Features

### Real-Time Scoring and Decisioning

- Real-time transaction scoring API targeting sub-500ms latency
- Rules-based decision engine with accept / review / decline actions
- Supervised ML model for transaction-level risk scoring
- Multi-channel support across cards, ACH, P2P, with expansion to SEPA and Wire
- Threshold-based decisioning with configurable risk appetite

### Advanced Detection

- Graph neural networks for detecting fraud rings and coordinated multi-transaction patterns
- Cross-rail pattern detection identifying coordination across payment channels
- Behavioural device fingerprinting and multi-signal scoring (IP, device ID, velocity)
- Custom ML model training on organisation-specific fraud data
- 24-hour lookback analytics and pattern analysis

### Analyst Tooling and Workflow

- No-code rule builder for non-technical fraud analysts
- Automated rule and threshold recommendation
- Alert and case management workflow with thresholds and escalation
- Dashboard for monitoring fraud rates and model performance
- Regulatory compliance workflow including AML, sanctions screening, and reporting

### Chargeback and Dispute Management

- Automated evidence compilation aligned with Visa Compelling Evidence 3.0
- ROI prediction per dispute (win probability, value, fees)
- Fight-vs-accept dispute recommendation engine
- Outcome feedback loop for continuous improvement

### Explainability and Future Capabilities

- Natural-language reasoning for fraud scores
- Federated learning enabling cross-institution training without data sharing
- Generative synthesis of rare fraud scenarios to address class imbalance
- Continuous adversarial testing of detection models
- Outcome-driven autonomous rule refinement

---

## AI-Native Advantage

Real-time graph neural network scoring detects fraud rings and account-takeover patterns that single-transaction models and rule engines miss. LLM-based natural-language rule authoring lets analysts express detection logic without code, shortening time-to-detection for emerging fraud types. Generative AI synthesises rare fraud scenarios to address persistent class imbalance in labelled datasets, while federated learning architectures allow shared model training across institutions without centralising sensitive transaction records. AI agents can automate the full chargeback dispute lifecycle, compressing per-case analyst effort from hours to minutes.

---

## Tech Stack & Deployment

The engine is designed around a REST API for transaction submission and decision delivery, with webhook callbacks for asynchronous alerts and case-management integration. It targets ISO 20022 rich-data messaging (mandatory migration deadline November 2025) for higher-precision scoring, and aligns with PCI DSS v4.0, PSD2 / Strong Customer Authentication, FATF guidance, and ISO 37003:2025 fraud control management. Visa VAMP and Compelling Evidence 3.0 are first-class targets for chargeback workflows. Deployment is intended to support both self-hosted and managed modes so institutions with strict data-residency or AML requirements can keep transaction data in-house.

---

## Market Context

The global fraud detection and prevention market is estimated at USD 67–70 billion in 2026, projected to reach USD 243–270 billion by 2034 at a CAGR of approximately 17–20%. Enterprise incumbents (FICO, SAS) charge multi-year licences per transaction volume, while SaaS entrants (SEON from ~$599/month, Flagright usage-based) scale with event volume; chargeback specialists (Justt, Chargebacks911) take a percentage of recovered disputes. Primary buyers are fraud operations managers at banks and payment processors, chief risk officers at fintechs, e-commerce fraud teams managing chargeback ratios, and AML compliance officers at financial institutions.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
