# Subject Area 2: Requirements

## Content

1. [Executive Summary](#executive-summary)
2. [Target Image Framework](#target-image-framework)
3. [Use Case Analysis and Prioritization](#use-case-analysis-and-prioritization)
4. [Requirements in the Context of the Reference Process](#requirements-in-the-context-of-the-reference-process)
5. [Technical Requirements](#technical-requirements)
6. [Business Case and Monetization](#business-case-and-monetization)
7. [E-ID Integration and Delimitation](#e-id-integration-and-delimitation)
8. [Strategic Approach: "From Small to Large"](#strategic-approach-from-small-to-large)
9. [Conclusion and Roadmap](#conclusion-and-roadmap)

## Executive Summary

The requirements analysis defines a structured framework for the implementation of the Open API Customer Relationship based on five target images of digital customer proximity. The focus is on solutions that can be implemented in the short term (Target Images 1 & 2) with a strategic perspective for extended scenarios. Use Case 1 "Customer Relationship Opening" was identified as a priority implementation candidate, with the "Identification" module defined as the MVP entry point.

**Key Findings:**
- Clear prioritization on Target Images 1 & 2 for MVP phase
- 4 prioritized Use Cases with quantitative evaluation
- Modular API architecture for scalable implementation
- Business Case challenges identified and addressed

## Target Image Framework

### Methodology of Target Image Development

The development of the target images was carried out through a structured workshop-based approach with all relevant stakeholders. The framework considers both technical feasibility and strategic market positions.

**Evaluation Criteria:**
- Short-term feasibility (6-12 months)
- Strategic potential (24+ months)
- Technical complexity
- Regulatory requirements
- Market acceptance

### The 5 Target Images of Digital Customer Proximity

![Target Images Overview](./resources/graphics/02-anforderungen/Zielbilder%20Übersicht%20Grafik.png)

#### **Target Image 1: Direct (Classic)**

![Detail Target Image Direct](./resources/graphics/02-anforderungen/Detail%20Zielbild%20Direkt.png)

**Conceptual Structure:** Direct customer relationship between customer and financial service provider without intermediaries.

**Central Characteristics:**
- Direct customer relationship without mediating instances
- Classic business models with API enhancement for efficiency improvement
- Low technical complexity due to proven structures
- High control over the entire customer journey

**Structure:** Customer ↔ Individualist

**Characteristics:**
- Direct customer relationship without intermediaries
- Classic business models with API enhancement
- Low technical complexity
- High control over customer journey

**Use Cases:**
- Opening a bank account
- Concluding insurance
- Direct credit application

**Evaluation:**
- **Feasibility:** Very high (implementable immediately)
- **Innovation Potential:** Medium
- **Market Relevance:** High (optimizing existing processes)

#### **Target Image 2: Indirect**

![Detail Target Image Indirect](./resources/graphics/02-anforderungen/Detail%20Zielbild%20Indirekt.png)

**Conceptual Structure:** Mediated customer relationship via service aggregators acting as integrators between customers and service producers.

**API Integration:** Dual API structure with Customer API for end-customer interaction and Provider API for backend integration.

**Central Characteristics:**
- Intermediaries as service aggregators allow extended service offerings
- API-based integration creates flexible, scalable connections
- Partner networks increase reach and service spectrum
- Shared customer journey through coordinated service experience

**Structure:** Customer ↔ Integrator ↔ Producer

**Characteristics:**
- Intermediaries as service aggregators
- API-based service integration
- Increased reach through partner networks
- Shared Customer Journey Management

**Use Cases:**
- Embedding of financial products
- Account Information Services (AIS)
- Payment Initiation Services (PIS)
- Robo-Advisory with Multi-Provider Backend

**Evaluation:**
- **Feasibility:** High (6-12 months)
- **Innovation Potential:** High
- **Market Relevance:** Very high (PSD2 compliance)

#### **Target Image 3: Intermediary**

![Detail Target Image Intermediary](./resources/graphics/02-anforderungen/Detail%20Zielbild%20Intermediär.png)

**Conceptual Structure:** Extended multi-player constellation with specialized intermediaries mediating between integrators and producers.

**Multi-API Architecture:** Four-layer API structure with Integration API, Production API, Specialist API, and Cross-Service API for comprehensive service orchestration.

**Central Characteristics:**
- Multi-player constellations enable complex service compositions
- Specialized intermediaries offer professional expertise for complex requirements
- Increased coordination requirements due to multi-layered architecture
- Innovation potential through new service combinations and cross-industry integration

**Structure:** Customer ↔ Integrator ↔ Producer + Intermediary

**Characteristics:**
- Multi-player constellations
- Specialized intermediaries for complex services
- Increased coordination requirements
- Potential for innovative service combinations

**Use Cases:**
- Embedding of financial products (extended)
- Multi Banking Platforms (SIX bLink integration)
- Cross-industry service bundling
- Wealth Management Ecosystems

**Evaluation:**
- **Feasibility:** Medium (12-18 months)
- **Innovation Potential:** Very high
- **Market Relevance:** High (future market development)

#### **Target Image 4: Platform**

![Detail Target Image Platform](./resources/graphics/02-anforderungen/Detail%20Zielbild%20Plattform.png)

**Conceptual Structure:** Hub-based platform architecture with a central platform as a service hub for all connected providers.

**Central Platform Hub:** Integrated platform with Service Engine for service processing, Analytics Layer for data analysis, and Governance Layer for rules and compliance.

**Connected Providers:** Comprehensive provider ecosystem with banks, fintechs, insurance companies, investment and payment providers, all centrally connected via the hub.

**Platform APIs:** Four specialized API layers - Consumer API for end customers, Provider API for provider integration, Marketplace API for service discovery, and Analytics API for data insights.

**Central Characteristics:**
- Central platform as service hub enables uniform customer experience
- Network effects through ecosystem approach create exponential added value
- High technical complexity due to comprehensive integration of all services
- Potential for disruptive business models through platform economy

**Structure:** Hub-based architecture

**Characteristics:**
- Central platform as service hub
- Network effects through ecosystem approach
- High technical complexity
- Potential for disruptive business models

**Use Cases:**
- Marketplace for trading VC & PE investments
- Comprehensive Financial Services Platform
- Cross-border Payment Hubs
- Digital Asset Trading Platforms

**Evaluation:**
- **Feasibility:** Low-Medium (18-24 months)
- **Innovation Potential:** Very high
- **Market Relevance:** Medium-High (strategic future perspective)

#### **Target Image 5: Decentralized**
**Out of Scope:** Not relevant for the implementation of the Open API Customer Relationship

### Target Image Comparison and Evolution

**Target Images Evolution and Evaluation:**

**Feasibility and Innovation Evaluation:**
- **Target Image 1 (Direct):** Highest feasibility, moderate innovation, minimal complexity
- **Target Image 2 (Indirect):** High feasibility, high innovation, moderate complexity
- **Target Image 3 (Intermediary):** Medium feasibility, highest innovation, medium complexity
- **Target Image 4 (Platform):** Low feasibility, highest innovation, highest complexity
- **Target Image 5 (Decentralized):** Out of scope - Blockchain-based solutions are not relevant for the Swiss financial market

**Implementation Timeline:**
- **Phase 1 (0-6 months):** Focus on Target Images 1 & 2 for rapid market launch
- **Phase 2 (6-12 months):** Expansion to Target Image 2 & 3 with extended services
- **Phase 3 (12-24 months):** Strategic development to Target Images 3 & 4

**Strategic Focus:**
- **Primary Focus:** Target Images 1 & 2 due to high short-term feasibility
- **Secondary Focus:** Target Images 3 & 4 as strategic expansion options

## Use Case Analysis and Prioritization

### Use Case Collection and Evaluation Methodology

**Collection:** 9 Use Cases identified (every ecosystem from the Ecosystem Wheel represented)

**Evaluation Methodology:**
- Workshop-based point ranking procedure
- Multi-stakeholder evaluation (Bank, Fintech, Regulator, Consumer)
- Quantitative criteria (see evaluation matrix)

**Evaluation Criteria:**

| Category | Weighting | Description |
|----------|-----------|-------------|
| **Feasibility** | Equal | Customer benefit, Bank added value, Contributor added value, Provider added value, Market volume |
| **Implementability** | Equal | Level of Assurance, API coverage degree, Complexity & Risks, Integration effort, Financial sustainability |
| **Strategic Relevance** | Equal | Differentiation potential, Ecosystem impact, Scalability |
| **Regulatory Conformity** | Equal | Compliance requirements, Governance complexity, Reputation risks |

### Top 4 Prioritized Use Cases

**Quantitative Evaluation Matrix:**

The use cases were evaluated through a structured workshop process with multi-stakeholder assessment (Bank, FinTech, Regulator, Consumer). Each use case received points based on the defined evaluation criteria.

| Use Case | Feasibility | Implementability | Strategic Relevance | Regulatory Conformity | **Total** |
|----------|-------------|------------------|---------------------|-----------------------|-----------|
| **UC1: Customer Relationship Opening** | 4/4 | 3/4 | 3/4 | 3/4 | **13 Points** |
| **UC2: Re-Identification** | 3/4 | 2/4 | 1/4 | 1/4 | **7 Points** |
| **UC3: Age Verification** | 2/4 | 1/4 | 1/4 | 0/4 | **4 Points** |
| **UC4: CLM of EVV End Customers** | 2/4 | 1/4 | 1/4 | 0/4 | **4 Points** |

#### **UC1: Customer Relationship Opening**

**Initial Situation:**
- Opening of a banking relationship of a customer directly at a bank
- Data points are based on standardized building blocks
- Different onboarding processes lead to inefficiencies and media breaks
- Customers must submit personal data again despite previous verification

**Implementation in the context of "Open API Customer Relationship":**
- Harmonization of onboarding journeys through standardized data building blocks
- Reuse of customer data to reduce media breaks
- Seamless integration between different banks when switching banks

**Pain Points (Customer):**
- High administrative effort due to repeated data entry
- Extended waiting times until account activation

**Pain Points (Bank):**
- High costs and complexity due to inconsistent onboarding processes
- Low reusability of customer data leads to duplicate verification processes

**Added Values:**
- Reduction of redundant data entries through automated reuse
- Seamless integration, high security standards, and usability
- Faster and simpler customer relationship opening and bank switching processes
- Leveraging efficiencies in the customer relationship opening process for banks
- Cost saving potential through leaner processes

**Roles in the Network:**
- Bank customers (Data owners)
- Bank (Service Provider)
- Optional Providers (Verification services)

#### **UC2: Re-Identification**

**Initial Situation:**
- Customers have to identify themselves repeatedly at different financial service providers
- AML-compliant identification processes are time-consuming and cost-intensive
- Fragmented identity data across different providers

**Implementation:**
- Standardized identification data building blocks
- Cross-provider identity verification
- AML-compliant data transmission with corresponding Level of Assurance

**Added Values:**
- Reduced identification costs for providers
- Improved Customer Experience through shortened onboarding times
- Increased security through standardized verification processes

#### **UC3: Age Verification**

**Initial Situation:**
- Legal requirements for age verification in various industries
- Inefficient individual solutions without reusability
- Data protection issues with comprehensive identity disclosure

**Implementation:**
- Attribute-based verification (Age ≥ 18) without full identity disclosure
- Privacy-by-Design implementation
- Cross-industry usability

**Added Values:**
- Data protection compliant age verification
- Cost reduction through reusability
- Compliance security for various industries

#### **UC4: CLM of EVV End Customers**

**Initial Situation:**
- Customer Lifecycle Management across various touchpoints
- Fragmented customer data at different providers
- Inefficient data maintenance and synchronization
- Complex onboarding processes at different custodian banks
- Redundant KYC processes for already verified customers

**Implementation:**
- Integrated Customer Lifecycle Management
- Standardized data maintenance processes
- Cross-provider data reconciliation
- Reuse of data building blocks for onboarding end customers at different custodian banks
- Efficient updating of KYC information

**Added Values:**
- Improved data quality through central data maintenance
- Efficiency increase in customer support
- Reduced compliance risks through more current data
- Simplified EVV onboarding processes

### Additional Use Cases

**Ecosystem-Specific Use Cases:**

**Mobility Sector:**
- Vehicle leasing with integrated insurance
- Mobility-as-a-Service subscriptions
- Cross-border vehicle registration

**Retail & E-Commerce:**
- Age-gated product sales (Alcohol, Tobacco)
- Premium account verification
- Cross-platform loyalty programs

**Real Estate:**
- Rental process/rent deposit account (high number of moves annually in Switzerland)
  * Special feature: No complete identification is necessary for a pure rent deposit account
  * Reduced regulatory hurdles and technical complexity
  * Long-term optimization potential for rental processes
- Mortgage comparison and brokerage
- Property investment verification

**Government Services:**
- Government services with pre-filled forms
- Cross-agency data sharing
- Digital identity for public services

**Healthcare:**
- Insurance verification for medical services
- Cross-provider medical record access
- Telemedicine identity verification

## Requirements in the Context of the Reference Process
[Conclusion Reference Process](./03-reference-process.md)

### Ecosystem-specific Requirements

#### **Finance Area**

**Banking:**
- KYC/AML compliance (Level of Assurance QEAA/EAA)
- PSD2 compatibility for Payment Services
- Basel III/IV regulatory capital requirements
- FATCA/CRS reporting obligations

**Insurance:**
- Insurance Distribution Directive (IDD) compliance
- Risk assessment data requirements
- Claims processing automation
- Cross-border insurance portability

**Investments:**
- MiFID II suitability assessment
- Qualified investor verification
- Portfolio reporting standards
- Alternative investment access

#### **Mobility**
- Vehicle registration data standards
- Insurance coverage verification
- Cross-border mobility services
- Environmental impact reporting

#### **Retail**
- Consumer protection compliance
- Age and identity verification
- Payment service integration
- Cross-border e-commerce support

#### **Government**
- Digital identity integration (E-ID readiness)
- Interoperability with public services
- Data protection and privacy compliance
- Audit trail and transparency requirements

### Data Building Blocks Requirements
*TODO: Please verify this chapter and adjust if necessary!*

#### **Basic Data (Basic Kit)**

**Identity Data:**
- Full Name (incl. Aliases)
- Date and place of birth
- Nationality(ies)
- Gender
- Marital status

**Contact Data:**
- Primary and secondary e-mail addresses
- Telephone numbers (Mobile/Landline)
- Preferred communication channels
- Availability times

**Address Data:**
- Residential address (current and previous)
- Registration address (if different)
- Business address (for business customers)
- Delivery addresses for documents

#### **Extended Data (Full Dataset)**

**KYC/AML Data:**
- Profession and employer
- Income and asset circumstances
- Politically Exposed Person (PEP) status
- Beneficial owners
- Source of funds documentation

**Risk Profiling:**
- Investment experience and goals
- Risk tolerance and capacity
- Investment horizon
- ESG preferences
- Tax situation

**Compliance Data:**
- FATCA/CRS classification
- Tax residency information
- Sanctions screening results
- Enhanced due diligence findings
- Ongoing monitoring flags

#### **Metadata**

**Consent Management:**
- Purpose-specific consent status
- Consent granularity (Data field level)
- Consent validity period
- Withdrawal mechanisms
- Audit trail

**Data Quality:**
- Source system identification
- Last update timestamp
- Verification status and method
- Data lineage information
- Quality scores

**Governance:**
- Data classification (Public/Internal/Confidential/Restricted)
- Retention policies
- Cross-border transfer restrictions
- Legal basis for processing

## Technical Requirements
[Market Analysis: Description of Existing Standards and Technologies](./01-market-analysis.md)

### Modular API Architecture

#### **Design Principles**

**RESTful Design:**
- HTTP-method-based operations (GET, POST, PUT, DELETE)
- Resource-oriented URL structures
- Stateless communication
- Idempotent operations where applicable

**JSON Format as Standard:**
- UTF-8 encoding for international characters
- Consistent naming conventions (camelCase)
- Null-value handling
- Schema validation with JSON Schema

**API Versioning:**
- Semantic Versioning (MAJOR.MINOR.PATCH)
- URL-based versioning (/v1/, /v2/)
- Backward compatibility guarantees
- Deprecation policies and timelines

#### **Security Requirements**

**Transport Security:**
- TLS 1.3 minimum requirement
- Certificate pinning for mobile applications
- HTTP Strict Transport Security (HSTS)
- Certificate Transparency monitoring

**API Security:**
- OAuth 2.0 / OpenID Connect implementation
- Financial-grade API (FAPI) compliance
- JWT token-based authentication
- Mutual TLS (mTLS) for critical services

**Data Protection:**
- Field-level encryption for sensitive data
- Tokenization for PII data
- Privacy-preserving technologies (e.g., Differential Privacy)
- GDPR/FADP-compliant data processing

#### **Performance and Scaling**

**Response Time Requirements:**
- Authentication: < 2 seconds (< 500ms optimized)
- Data Retrieval: < 5 seconds (< 2000ms optimized)
- Data Submission: < 3000ms
- Bulk Operations: < 30 seconds (< 10000ms optimized)
- Real-time Notifications: < 1 second

**Throughput Requirements:**
- Minimum 1000 requests/second per API endpoint
- Burst capacity up to 5000 requests/second
- Graceful degradation in case of overload
- Circuit Breaker pattern implementation

**Availability Requirements:**
- Very high uptime SLA with minimal annual downtime
- Maximum 5 minutes unplanned outages
- Planned maintenance windows outside business hours
- Multi-region deployment for disaster recovery

### Federated System Requirements
*TODO: Please verify this chapter and adjust if necessary!*

#### **Interoperability**

**Standards Compliance:**
- OpenAPI 3.0 specifications
- ISO 20022 for financial messaging
- W3C standards for Web APIs
- FIDO Alliance standards for authentication

**Protocol Support:**
- HTTP/2 and HTTP/3 support
- WebSocket for real-time communication
- gRPC for high-performance service-to-service communication
- MQTT for IoT integration

**Data Exchange Formats:**
- JSON as primary format
- XML support for legacy system integration
- Protocol Buffers for efficient serialization
- CSV for bulk data export

#### **Governance and Orchestration**

**Service Discovery:**
- Dynamic service registration
- Health check monitoring
- Load balancing configuration
- Service dependency management

**Configuration Management:**
- Centralized configuration store
- Environment-specific settings
- Feature flag management
- A/B testing support

**Monitoring and Observability:**
- Distributed tracing
- Comprehensive logging
- Metrics collection and alerting
- Performance analytics

### MVP Open API Customer Relationship

The Minimum Viable Product of the Open API Customer Relationship focuses on the essential functionalities for successful market launch. The MVP definition takes place on a conceptual level, while detailed data structures and technical implementation aspects are elaborated in the [Reference Process Conclusion](./03-reference-process.md) and the technical documents [Implementation Alpha Version 1.0](../implementation/implementation-alpha-version-1.0.md).

#### **MVP Scope Definition**
The Minimum Viable Product of the Open API Customer Relationship focuses on the basic functionalities for **Use Case 1: Customer Relationship Opening**.

**MVP Core Functionalities:**
1. Basic Data Transfer: Name, address, contact details
2. Identity Data Transmission: Already verified identity information
3. Consent Management: Customer consent for data transmission
4. Basic Security: FAPI 2.0 compliant security implementation

**MVP Exclusions:**
- Extended Data: Assets, income, profession
- Payment Initiation: Payment triggering
- Cross-Industry: Other ecosystems except Finance
- Advanced Analytics: AI-based data analysis

#### **MVP Data Model**
The MVP data model focuses on the essential data structures for the implementation of the "Identification" module. The structures are fully compatible with the final API specification Version 2.0 from the workshop phase and define the core components for the Open API Customer Relationship.

![System Open API Customer Relationship](./resources/graphics/02-anforderungen/System%20Open%20API%20Kundenbeziehung.png)

**Conceptual Data Structure**

The MVP is based on three core components for the Open API Customer Relationship:

**1. Identity Data Framework:**
Standardized structures for personal data, contact information, and address data with integrated verification status. The data structures enable cross-provider reuse while maintaining data protection and security.
**Customer Identity Structure:**
Conceptual data structure includes customerId as internal reference, sharedCustomerHash for anonymous cross-provider identification, and three main categories:

- **Personal Information:** Basic identity data such as First/Last Name, Date and Place of Birth, Nationality(ies), Gender, and Marital Status
- **Contact Information:** Primary and secondary e-mail addresses, mobile and landline numbers with verification status, preferred communication channels
- **Address Information:** Residential address and differing correspondence address with validity periods, structured address components

Detailed data structures are specified in [Implementation Alpha Version 1.0](../implementation/implementation-alpha-version-1.0.md).

**2. Consent Management System:**
Granular consent management with purpose-bound data use, temporal limitation, and complete traceability. The system supports field-specific permissions and different legal bases for data processing.

- **Consent Identification:** Unique ConsentId and customer assignment
- **Purpose Definition:** Explicit purpose statement for data use (e.g., account opening, KYC check)
- **Data Categories:** Specification of affected data categories (Identity, Contact, Financial)
- **Temporal Management:** Granting, expiration, and withdrawal times
- **Granularity Control:** Field-specific authorization with Read/Write/Delete permissions
- **Legal Framework:** Legal basis for data processing (Consent, Contract, Legal Obligation)
- **Audit Trail:** Complete traceability of all consent changes

**3. Verification and Assurance Level:**
Structured documentation of verification methods and times with corresponding assurance levels according to regulatory standards. This enables trustworthy data transmission between different providers.

- **Verification Identity:** Unique VerificationId with customer assignment
- **Data Field Specification:** Specification of the verified data field (e.g., identity, address)
- **Method Documentation:** Verification method (VideoIdent, E-ID, Document Upload)
- **Assurance Level:** Verification level according to regulatory standards (QEAA, EAA, self-declared)
- **Temporal Tracking:** Verification time, performing instance, validity period
- **Document References:** Secure references to verification documents without direct storage

**Privacy-preserving Identification:**
Implementation of an anonymous customer hash system for cross-provider identification without disclosing personal data, based on standardized cryptographic procedures.

#### **sharedCustomerHash Concept**

**Purpose:**
- Unique but anonymous identification of customers across providers
- Privacy-preserving customer matching
- Fraud prevention through cross-provider analytics

**Implementation:**
- SHA-256 hash of standardized identity data
- Salt-based hashing for additional security
- Reversibility only by authorized key holders
- GDPR-compliant through pseudonymization

**Hash Generation:**
Conceptually, the sharedCustomerHash is generated by normalizing and linking standardized identity data (First Name, Last Name, Date of Birth, Place of Birth, Nationality) with a security salt and hashing via SHA-256.

## E-ID Integration and Delimitation

### Conceptual Differences

#### **E-ID Paradigm**
- **Identity-centric:** Focus on digital identity proofs
- **State-controlled:** Regulatory frameworks and standards
- **Verification-focused:** Primarily identity verification
- **Centralized Trust:** State Certificate Authorities

#### **Open API Customer Relationship Paradigm**
- **Service-centric:** Focus on business process integration
- **Industry-driven:** Market-driven standards and innovation
- **Relationship-focused:** Comprehensive customer lifecycle
- **Federated Trust:** Multi-stakeholder governance

### Integration Scenarios

#### **Complementary Integration**
- E-ID as Identity Provider for Strong Authentication
- Open API as Service Layer for Business Logic
- Shared Trust Framework for Cross-domain Services
- Unified User Experience across both paradigms

### Delimitation and Scope Definition

#### **E-ID Scope (outside Open API Customer Relationship)**
- Digital identity proofs
- State verification services
- Cross-border identity recognition
- Public sector service access

#### **Open API Customer Relationship Scope**
- Commercial customer onboarding
- Financial services integration
- Private sector data sharing
- Business process automation

#### **Overlap Areas**
- Identity verification for commercial services
- Consent management frameworks
- Privacy-preserving technologies
- Cross-sector interoperability

**Interplay between E-ID and Open API**
The integration of the Swiss E-ID with the Open API Customer Relationship represents a strategic advantage. While the data resides with the banks, data sovereignty lies with the customer, especially during the consent process.

**Hybrid Solution Approach:** 
- Ensure E-ID compatibility from the beginning
- Parallel solution during E-ID introduction phase
- Avoidance of "unnecessary verifications" through modular identity data reuse

## Strategic Approach: "From Small to Large"

The strategic approach follows the proven principle of gradual build-up, starting with quickly realizable successes and systematic expansion to more complex use cases.

### Phase 1: Identification and Basic Data

**Focus: Module "Identification"**
- **Rationale:** Reusability across all use cases
- **Technical Scope:** Basic identity verification APIs
- **Business Value:** Immediate return through process improvement
- **Risk Level:** Low (established technologies and processes)

**Concrete Deliverables:**
- Identity Verification API (Level 1-2)
- Basic Consent Management
- Sandbox Environment with 2-3 partner banks
- Developer documentation and SDKs

**Success Metrics:**
- Reduction of verification time
- Number of partner banks onboarded
- Number of successful API calls/month
- Customer Satisfaction Score

#### **Excluded Complex Modules**

**Module "Self-declaration" → Later Phase**
- **Justification:** High variance of data requirements per bank
- **Complexity:** Lack of standardization of question catalogs
- **Integration:** Complex integration into existing bank processes


### Critical Success Factors

For the successful implementation of the Open API Customer Relationship, the following goals and factors are essential.

1. **Technical Excellence:** Robust, secure, scalable platform
2. **Strong Partnerships:** Committed, high-quality partners
3. **Regulatory Compliance:** Proactive regulatory engagement
4. **Customer Value:** Clear, demonstrable customer benefits
5. **Financial Sustainability:** Viable business model from Day 1
6. **Market Timing:** Market launch before competing threats
7. **Team Expertise:** Experienced team with professional competence
8. **Stakeholder Alignment:** Unified vision across all stakeholders

The requirements analysis shows a clear path for the successful implementation of the Open API Customer Relationship with a focused approach on solutions implementable in the short term and strategic perspective for long-term market leadership.


---

**Version:** 1.1
**Date:** November 2025
**Status:** Reviewed for Alpha Version 1.0

---

[Sources and References](./sources-and-references.md)
