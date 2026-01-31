# OBP Legal Framework Conclusion

## Content

1. [Executive Summary](#executive-summary)
2. [Swiss Financial Market Context and Regulatory Starting Position](#swiss-financial-market-context-and-regulatory-starting-position)
3. [Identified Key Legal Questions and Expert Opinions](#identified-key-legal-questions-and-expert-opinions)
4. [Open Questions](#open-questions)
5. [Proposal Compliance Framework for API Design](#proposal-compliance-framework-for-api-design)
6. [Risk Management and Liability](#risk-management-and-liability)
7. [Conclusion and Recommendations](#conclusion-and-recommendations)

---
**Terminology:** Throughout this documentation, the terms "Data Producer" and "Data Integrator" are used. The "Data Producer" provides the customer data, while the "Data Integrator" uses this data to establish a new customer relationship (or banking relationship in our examples).

## Executive Summary

The legal framework conditions for the Open API Customer Relationship are characterized by a complex interplay of Swiss financial market regulation, data protection law, and international law. The analysis identifies critical legal areas and offers practice-oriented compliance frameworks (rule-compliant structures) for API implementation.

**Key Findings:**
- From a legal and regulatory perspective, there are no insurmountable hurdles
- FINMA statement identified as a critical success factor for market acceptance
- The distribution of liability between data producers and data integrators requires clear contractual regulation
- As a rule, liability for data usage lies with the data integrator – unless the data producer has breached their duty of care in a particularly serious manner, which must be proven in the event of an occurrence
- Compliant processing of data in the interest of the customer requires robust consent mechanisms

**Important Disclaimer:** *The information and recommendations contained in this document do not constitute legal advice. We are not specialists in the legal field. For specific legal questions, qualified legal advice must be obtained.*

---

## Swiss Financial Market Context and Regulatory Starting Position

### Legal Framework Matrix

The Open API Customer Relationship operates in the area of tension between various legal fields:

| Legal Area | Primary Source | FINMA Guidance | Application to APIs |
|------------|----------------|----------------|---------------------|
| **Banking Secrecy** | BankG Art. 47 | RS 2008/7 | Consent-based data release required |
| **Money Laundering Law** | GwG Art. 3, 4 | RS 2016/7 | Identification standards and KYC processes |
| **Data Protection** | FADP, GDPR Equivalence | FAQ FADP/GDPR | Consent Management, Data Minimization |
| **Outsourcing** | BankV Art. 25 | RS 2008/7 | Third-party service integration |
| **Operational Risk** | Basel III/IV | FINMA Guidance | API reliability, security requirements |

### Compliance Starting Position

**Regulatory Complexity:**
- Existing laws must be interpreted for new technologies
- International standards as orientation aid
- FINMA position not yet fully established

**Legal Uncertainties:**
- Liability distribution in API-based data transmissions
- Minimum requirements for data validation
- Cross-Border Data Sharing Compliance
- Minimum requirements for cross-industry data usage

---

## Identified Key Legal Questions
Based on the workshops conducted and the exchange with subject matter experts, over 15 critical legal questions were identified that require qualified legal clarification. The clarification of these questions took place within the workshop format together with internal legal experts of the project participants and was initially answered in Phase 1. Below is an excerpt of the discussed questions as well as the answers to four specific key questions.

| Category | Topic | Question |
|----------|-------|----------|
| **Legal** | Dataset | What are the minimum requirements for data verification and for the released datasets? |
| **Legal** | Federated System | How should the federated system be designed and operationalized? |
| **Legal** | Governance | How is the developing network legally secured between the actors? |
| **Legal** | Liability (Delegation) | Regulation of delegation (Example: HBL passes an onboarding from Intrum to a third-party bank. Who has what role and liability?) |
| **Legal** | Liability (Online Ident.) | Liability for Online Ident. in connection with initial deposits: Who is liable for what (since identification consists of components from third-party provider and bank)? |
| **Legal** | Identification & Outsourcing | How must reused identifications be treated in connection with the assessment of outsourcing? (FINMA) |
| **Regulatory** | Authorized Customer Groups | Definition of "out of scope" customer groups (e.g., Workout/Recovery positions, customers with MROS reports, etc.) before data transfer, or afterwards by new bank? |
| **Regulatory** | Governance | How is the ongoing further development of regulatory requirements ensured in the federated system? |
| **Regulatory** | Identification (Stock) | Is the principle of "identification on stock" generally allowed? (e.g., if ID stolen, name change upon marriage, etc.) Definition of the duration how long an identification can be reused? |
| **Regulatory** | Identification (Types) | Which types of identification should be transferable (e.g., only Online / Video Ident.)? |
| **Regulatory** | Identification & ID Document | Handling of foreigners / foreigner ID card necessary? |

**Important Disclaimer:** *The answers to the following key questions refer specifically to the opening of a customer relationship in banking.*

## What minimum requirements apply to the release of datasets regarding timeliness, quality, and handling of risk profiles such as PEP, sanctions lists, and high-risk customers?

Existing market solutions and initiatives in the Swiss market show that data is generally accepted, unless the risk and compliance departments see reason for further clarifications.

This seems plausible, as it concerns data that the data producer keeps, uses, and assumes to be correct. If the timeliness of the data changes, this would also not be immediately known to the data producer.

The data integrator receives the data based on an identification as well as further data processing, which takes place in compliance with FINMA. It remains essential that the customer must confirm their data again – as would be the case with a regular account opening.

If banks express doubts as to whether the received data can be relied upon, the question arises as to what else should be relied upon, since even with conventional onboarding, the information ultimately comes from the customer.

In this constellation, there is additionally a pre-recording by the previous bank, which has already maintained the customer relationship over a certain period of time. The data integrator could alternatively carry out an identification through an external provider. The difference to the described constellation would then essentially only be that the identification was not carried out by the provider, but by the data producer at an earlier point in time.

The mere passage of time does not result in any problems regarding identity: The customer remains the same customer.
It remains to be ensured that the data integrator and data producer are dealing with the same person who is appearing.

This is ensured by the process (information from the customer to the data integrator regarding the existing customer relationship, confirmation with the data producer that the relevant data should be transferred to the data integrator).

For handling special cases (e.g., PEP, AML issues), it is advisable for the participating banks to define criteria in which cases data is not passed on. In a specific individual case, the data producer can then communicate that such a case exists without having to disclose further details.

## How is liability regulated if incorrect datasets are adopted and further processed (e.g., between a Bank A and a Bank B), and is there a duty to verify the content of the adopted data?

The responsibility regarding the use of data lies with the data integrator (e.g., bank) that uses it. This also applies in the case of a delegated customer identification.

The situation is fundamentally no different whether a provider is used for identification or whether data from a pre-existing banking relationship is used. This applies to the responsibility of the bank using the data and can also be handled this way regarding the liability of third parties (be it a provider or a data producer).

Liability is likely only considered in the event of a breach of duty by the third party, i.e., the bank will be able to assume that the third party has observed the duties incumbent upon it. Since the responsibility lies with the bank using the data, the data producer will hardly be willing to accept substantial liability risks, and any breaches of duty by the third party will generally be difficult for the bank to determine and prove, a limitation to gross negligence and intent or possibly, insofar as such can be effectively formulated in a contract, to specific, clearly defined contractual breaches is recommended here.

## How is liability regulated if incorrect datasets are adopted and further processed, and is there a duty to verify the content of the adopted data?

If the data integrator uses the data of the data producer regarding identity, which the latter has created within the scope of its customer relationship, the data producer is not commissioned by the data integrator to carry out an identification for it. Rather, the data producer carried out the identification long ago for its customer relationship. The data producer only hands over certain data to the data integrator with the effect that an actual identification no longer has to be carried out, but instead an earlier identification can be used in the defined process. This process is not outsourcing, but a pure transfer of data.

## How is liability regulated in delegated onboarding, if for example a bank transfers the onboarding of a third party to another bank? Who bears what responsibility?

Strictly speaking, "identification on stock" does not exist: The identification was made at the data producer for the purpose of maintaining the banking relationship between the customer and the data producer.

When transmitting the data to the data integrator, a change in the purpose of the relevant data only takes place insofar as this data at the data integrator serves not the original, but the new banking relationship. This is obviously unproblematic because the customer wants exactly that and consequently agrees to this change of purpose.

It makes sense to keep the various steps separate: The actual identification took place at the data producer. Its data is transferred to the data integrator. It remains to be ensured that it is the same person, which is 1. guaranteed and 2. must always be ensured, even if the identification took place recently. The note that identification and account opening never take place simultaneously is conclusive in this respect. The temporal discrepancy between these steps does not per se result in a problem.

Thus, it also does not appear relevant whether the ID used for identification at the data producer is still valid or whether certain characteristics of the customer have changed (e.g., name through marriage). The identity as such still stands, and that it concerns the person identified at that time is, as mentioned, ensured by the process.

## Conclusion and Recommendations

### Legal Recommendations for Action

The legal implementation takes place parallel to the technical implementation with a specific focus on Compliance-by-Design and proactive FINMA engagement across all project phases.

**Complete Implementation Timeline:** → [See Master ROADMAP.md](../../ROADMAP.md)

#### **Legal-Specific Phase Overview:**
**Phase 1 (Months 1-6):** Qualified legal advice, FINMA strategy, Legal Framework Design, Compliance-by-Design
**Phase 2 (Months 6-18):** Pilot Legal Testing, Regulatory Engagement, Industry Coordination, Legal Precedent Building
**Phase 3 (Months 18-36):** Regulatory Advocacy, International Coordination, Legal Innovation

#### **Detailed Legal Measures:**
**Short-term measures (0-6 months):** Legal Foundation and Compliance Framework
**Medium-term measures (6-18 months):** Pilot Validation and Industry Coordination
**Long-term strategies (18+ months):** Regulatory Innovation and International Coordination

### Critical Success Factors

**1. Early legal involvement:** Involve legal experts from the start of the project
**2. FINMA relationship:** Proactive and transparent communication with FINMA
**3. Industry cooperation:** Common legal positions with other market participants
**4. Regulatory monitoring:** Continuous monitoring of regulatory developments
**5. Adaptive compliance:** Flexible legal architecture for rapid regulatory adjustments

### Closing Remark

The legal complexity of the Open API Customer Relationship requires a systematic and proactive approach. The identified key questions and expert opinions provide a solid basis for further legal design, but cannot replace qualified legal advice for specific implementation decisions.

Close cooperation between technical and legal experts as well as proactive dialogue with FINMA are identified as critical success factors for the compliant and marketable implementation of the Open API Customer Relationship.

---

**Version:** 1.0  
**Date:** August 2025  
**Status:** Final Draft for Legal Review  
**Important Note:** *This document does not contain legal advice. Qualified legal advice is required for binding legal assessments.*

---

[Sources and References](./sources-and-references.md) 
