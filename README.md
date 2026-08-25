# Falcon Freight Solutions – GRC Audit & Compliance Programme

A comprehensive Governance, Risk & Compliance (GRC) case study conducted for Falcon Freight Solutions, a mid-sized logistics company operating across Southern and East Africa. The project delivers an ISO/IEC 27001:2022 ISMS gap analysis, a third-party vendor risk assessment, and a full suite of corporate security policies to close identified governance gaps.

## Table of Contents

- [Project Overview](#project-overview)
- [Network Topology](#network-topology)
- [Tools and Technologies](#tools-and-technologies)
- [Configuration Steps](#configuration-steps)
- [Results and Findings](#results-and-findings)
- [Author](#author)

## Project Overview

Falcon Freight Solutions is a logistics and supply chain company that scaled its regional operations and vendor relationships faster than its governance and compliance processes, leaving it unable to demonstrate ISO/IEC 27001 conformance. As GRC Analyst Consultant, the objective of this project was to:

- Conduct a comprehensive risk assessment across the organization's hybrid infrastructure and vendor network
- Identify governance and compliance gaps against **ISO/IEC 27001:2022**, **ISO 31000**, and the **NIST Cybersecurity Framework (CSF)**
- Assess third-party and vendor risk, using **Microsoft Azure** (the cloud shipment tracking provider) as a case example
- Recommend and draft a standardized GRC framework and supporting policy suite
- Deliver an audit-ready compliance report with a prioritized remediation roadmap

## Network Topology

Falcon Freight operates a hybrid IT infrastructure spanning head office, regional offices, and a distributed third-party network:

- **Cloud-based shipment tracking platform** — hosted on Microsoft Azure, primary region Azure South Africa North (Johannesburg), with disaster recovery in Azure West Europe (Netherlands)
- **On-premise Warehouse Management System (WMS)** — hosted and fully secured within Falcon Freight's own infrastructure, network-segmented from corporate and guest networks
- **Corporate IT systems** — head office in Johannesburg, South Africa, with regional offices across Southern and East Africa connected via site-to-site VPNs / encrypted tunnels
- **Mobile/field devices** — used by delivery contractors and customs brokers, enrolled in a Mobile Device Management (MDM) solution
- **Third-party access points** — customs brokers, subcontracted delivery contractors, and technology vendors provisioned with scoped, least-privilege access into the tracking platform and WMS

## Tools and Technologies

- **ISO27k ISMS Gap Analysis Questionnaire v1 (2024)** — 161-question assessment across Clauses 4–10 and all 93 Annex A controls
- **Third-Party & Vendor Risk Questionnaire** — 76-question, 12-domain vendor risk scoring instrument
- **Microsoft Azure** (cloud hosting, Entra ID / Azure AD, Purview DLP, Azure Key Vault)
- **Enterprise Risk Register** (Excel-based risk and vendor tracking)
- **ISO/IEC 27001:2022** and **ISO 31000** frameworks
- **NIST Cybersecurity Framework (CSF)**
- **GDPR** and **POPIA** (South African Protection of Personal Information Act) compliance requirements
- **Microsoft Excel** and **Word** (risk register, questionnaires, and report authoring)

## Configuration Steps

1. Conducted discovery and scoping to understand Falcon Freight's business operations, hybrid infrastructure, and third-party vendor relationships.
2. Issued and completed the Third-Party & Vendor Risk Questionnaire for Microsoft Azure (Vendor ID `TPV-001`) across 12 weighted risk domains.
3. Scored vendor responses (Yes = 2, Partial/Compensating Control = 1, No = 0, Not Applicable excluded) and calculated a weighted overall risk rating.
4. Conducted the ISO/IEC 27001:2022 ISMS Gap Analysis, evaluating all 10 mandatory management-system Clauses and all Annex A controls across the Organizational, People, Physical, and Technological domains.
5. Logged all findings, non-conformances, and risk ratings in the Enterprise Risk Register.
6. Drafted the core policy suite required to close identified gaps:
   - Information Security Policy
   - Password & Access Control Policy
   - Third-Party Vendor Management Policy
7. Compiled the Vendor Risk Assessment Report – Microsoft Azure, documenting methodology, scoring, key risks (R1–R7), and mitigation actions with owners and timeframes.
8. Compiled the ISO/IEC 27001 Gap Analysis Findings Report, summarizing critical non-conformances and a phased remediation roadmap (Phase 1: Foundational, Phase 2: Core Controls, Phase 3: Assurance & Maturity).
9. Mapped all findings back to ISO/IEC 27001, ISO 31000, and NIST CSF to ensure framework alignment.
10. Delivered final audit-ready reports and a prioritized compliance roadmap to leadership.

## Results and Findings

- **Vendor Risk Assessment (Microsoft Azure)**: Achieved an overall weighted score of **89.2%**, rated **Low Risk**. Lowest-scoring domains were Incident Management & Breach Notification (78.6%), Data Privacy & Regulatory Compliance (87.5%), and Business Continuity & Disaster Recovery (83.3%).
- Key vendor risks identified: unconfirmed MFA enforcement on admin accounts, DLP/data masking not yet enabled, no bespoke DPIA completed, breach notification lacking a firm SLA, and no formal API key rotation schedule — each assigned an owner, priority, and remediation timeframe.
- **ISO/IEC 27001:2022 Gap Analysis**: Of 161 questions assessed, only 16 (10%) were fully conformant (Yes), 100 (62%) were non-conformant (No), 36 (22%) were partial/informal practices, and 9 (6%) were not applicable.
- **Critical finding**: None of the 10 mandatory ISMS Clauses were satisfied, meaning certification could not currently be achieved; gaps were concentrated in supplier/vendor risk management, incident management, privacy/PII protection, and technical monitoring.
- **Outcome**: A phased 12-month remediation roadmap was produced, alongside three foundational corporate policies (Information Security Policy, Password & Access Control Policy, Third-Party Vendor Management Policy) to close the identified governance gaps and move Falcon Freight Solutions toward a certifiable ISMS.

## Author

**Tapiwa Muyengwa**

- LinkedIn: [linkedin.com/in/tapiwa-muyengwa-64a9a3320](https://linkedin.com/in/tapiwa-muyengwa-64a9a3320)
- Email: `Muyengwataps@gmail.com`
