# OBP API Endpoint Design Conclusion

## Content

1. [Executive Summary](#executive-summary)
2. [API Architecture Overview](#api-architecture-overview)
3. [Main Endpoints](#main-endpoints)
4. [Granular Data Endpoints](#granular-data-endpoints)
5. [Request/Response Structures](#requestresponse-structures)
6. [Implementation Guidelines](#implementation-guidelines)

---

## Executive Summary

The API Endpoint Design for the Open API Customer Relationship follows the OpenAPI 3.0 standards and establishes a clear, RESTful architecture for the secure exchange of customer data. The API specification focuses on conceptual structures, while detailed technical implementations are covered in the separate [API Codebase Documentation](../implementation/).

**Central Design Principles:**
- OpenAPI 3.0 compliant specification for automatic code generation
- RESTful design with resource-oriented URL structures  
- FAPI 2.0 Security Integration for financial services → [See Conclusion Consent and Security Flow](./06-consent-security-flow.md)
- Modular endpoint architecture for flexible use case coverage

---

## API Architecture Overview

### Technical Basics

**API Standard:** RESTful design according to OpenAPI 3.0 Specification
- JSON as primary data format for interoperability
- HTTPS/TLS 1.3 mandatory for Transport Security
- HTTP/2 support for performance optimization
- Semantic Versioning for API evolution

**Design Principles:**
- **Resource-oriented URLs:** Logical data structure mapping
- **HTTP Verbs:** Standard CRUD Operations (GET, POST, PUT, DELETE)
- **Statelessness:** Session-independent Request/Response Cycles
- **Idempotency:** Safe repeatability for critical operations

### Security Architecture

**Authentication & Authorization:** → [Detailed Security Implementation see Conclusion Consent and Security Flow](./06-consent-security-flow.md)
- FAPI 2.0 Security Profile for Financial APIs
- OAuth 2.0/OpenID Connect for standardized authentication
- JWT-based Access Tokens with granular scopes
- Mutual TLS (mTLS) for critical partner integrations

**API Gateway Integration:**
- Rate Limiting with adaptive throttling logic
- Request validation through JSON Schema
- Response caching with ETags for efficiency
- Comprehensive monitoring and audit trails

---

## Main Endpoints

Based on the final API specification Version 2.0 from the workshop phase, the Open API Customer Relationship offers the following core endpoints:

### Customer Check API
#### `POST /customer/check`
**Purpose:** Existence and identification validity check of a customer
**Authentication:** JWT Header with Consent Claims
**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value",
  "lastName": "Doe",
  "firstName": "John", 
  "dateOfBirth": "1990-01-01"
}
```

**Response (In):**
```json
{
  "match": true,
  "identificationDate": "2025-01-15",
  "verificationLevel": "QEAA",
  "lastUpdate": "2025-01-15T10:00:00Z"
}
```

### Full Customer Dataset API
#### `POST /customer/fullRequest`
**Purpose:** Complete customer data set based on defined data building blocks
**Scope:** Includes Identity, Address, Contact, Identification, and KYC data
**Authentication:** JWT Header with Consent Claims

**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value",
  "purpose": "accountOpening",
  "requestedDataCategories": ["identity", "address", "contact", "identification", "kyc"]
}
```

**Response (In):** Complete customer data set based on the defined data building blocks of the reference process:
```json
{
  "personalData": {
    "title": "Mr",
    "firstName": "John",
    "lastName": "Doe",
    "gender": "male",
    "dateOfBirth": "1990-01-01",
    "placeOfBirth": "Zurich",
    "nationality": ["CH"],
    "maritalStatus": "single"
  },
  "addressData": {
    "street": "Main Street",
    "houseNumber": "123",
    "postalCode": "8001",
    "city": "Zurich",
    "country": "CH",
    "canton": "ZH"
  },
  "contactData": {
    "phoneNumber": "+41791234567",
    "emailAddress": "john.doe@example.ch",
    "preferredCommunication": "email"
  },
  "identificationData": {
    "identificationMethod": "VideoIdent",
    "documentType": "passport",
    "documentNumber": "123456789",
    "issuingAuthority": "Switzerland",
    "expiryDate": "2035-01-15",
    "verificationLevel": "QEAA",
    "verificationDate": "2025-01-15T10:00:00Z"
  },
  "kycData": {
    "economicBeneficiary": true,
    "taxDomicile": "CH",
    "usTaxLiability": false,
    "fatcaStatus": "non_us_person",
    "tin": "756.1234.5678.97",
    "amlRiskClass": "low",
    "pepStatus": "no"
  }
}
```

### Customer Identification API
#### `POST /customer/identification`
**Purpose:** Query specific identification data with verification status
**Authentication:** JWT Header with Consent Claims
**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value"
}
```

**Response (In):**
```json
{
  "identificationMethod": "VideoIdent",
  "referenceNumber": "VI_2025_001234",
  "verificationDate": "2025-01-15T10:00:00Z",
  "documentType": "passport",
  "documentNumber": "123456789",
  "issuingAuthority": "Switzerland",
  "expiryDate": "2035-01-15",
  "verificationLevel": "QEAA",
  "biometricVerification": {
    "livenessScore": 0.98,
    "faceMatchScore": 0.95,
    "documentAuthenticityScore": 0.97
  },
  "auditTrail": {
    "videoReference": "secure-storage.example.ch/audit/video_123.mp4",
    "documentScanReference": "secure-storage.example.ch/docs/passport_scan_123.pdf"
  }
}
```

### Process Flow APIs
**Based on the 10-step reference process** → [Complete process details in Conclusion 03 Reference Process](./03-reference-process.md)

The following endpoints implement the technical interfaces for the structured onboarding flow:

- `POST /process/initialize` - Initialization of the onboarding process
- `POST /process/self-declaration` - Self-declaration for compliance
- `POST /process/background-checks` - Background checks and KYC verifications
- `POST /process/contract-signature` - Digital contract signing

#### `POST /process/initialize`
**Purpose:** Step 1 - Initialization of the onboarding process
**HTTP Method:** POST

**Request (Out):**
```json
{
  "cookieConsent": true,
  "dataProcessingConsent": true,
  "selectedCountry": "CH",
  "serviceType": "bankAccount"
}
```

**Response (In):**
```json
{
  "processId": "proc_12345",
  "status": "initialized",
  "nextStep": "selfDeclaration"
}
```

#### `POST /process/self-declaration`
**Purpose:** Step 3 - Self-declaration for compliance
**HTTP Method:** POST

**Request (Out):**
```json
{
  "processId": "proc_12345",
  "economicBeneficiary": true,
  "taxDomicile": "CH",
  "usTaxLiability": false,
  "fatcaDeclaration": {
    "status": "non_us_person",
    "confirmed": true
  },
  "tin": "756.1234.5678.97",
  "sourceOfFunds": "employment",
  "nationalities": ["CH"]
}
```

#### `POST /process/background-checks`
**Purpose:** Step 7 - Background Checks and KYC verifications
**HTTP Method:** POST

**Request (Out):**
```json
{
  "processId": "proc_12345",
  "checksRequested": ["sanction", "pep", "crime", "credit"],
  "riskLevel": "standard"
}
```

**Response (In):**
```json
{
  "checksCompleted": {
    "sanctionCheck": "passed",
    "pepCheck": "passed",
    "crimeCheck": "passed",
    "creditCheck": "passed"
  },
  "riskAssessment": {
    "overallRisk": "low",
    "riskScore": 2,
    "factors": []
  },
  "complianceStatus": "approved"
}
```

#### `POST /process/contract-signature`
**Purpose:** Step 9 - Digital contract signing
**HTTP Method:** POST

**Request (Out):**
```json
{
  "processId": "proc_12345",
  "signatureType": "QES",
  "documentsToSign": ["terms_conditions", "privacy_policy", "product_agreement"],
  "signatureData": {
    "certificate": "-----BEGIN CERTIFICATE-----...",
    "timestamp": "2025-01-15T10:00:00Z",
    "deviceInfo": "browser_info"
  }
}
```

---

## Granular Data Endpoints

The API offers granular endpoints for specific data subsets to enable minimal data transmission and precise consent control:

**Consent-based Data Access Control:** → [Detailed Consent Flow Architectures in Conclusion 06 Consent and Security Flow](./06-consent-security-flow.md)

### Available Granular Endpoints:
- `POST /customer/basic` - Master data (Name, Date of Birth, Nationality)
- `POST /customer/address` - Address data (Residential & Correspondence address)
- `POST /customer/contact` - Contact data (Telephone, E-Mail)
- `POST /customer/kyc` - KYC attributes without identity documents

---

### Basic Customer Data API

#### `POST /customer/basic`
**Purpose:** Only master data (Name, First Name, Date of Birth, Nationality)
**HTTP Method:** POST

**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value"
}
```

**Response (In):**
```json
{
  "lastName": "Doe",
  "firstName": "John",
  "dateOfBirth": "1990-01-01",
  "nationality": ["CH"],
  "gender": "male",
  "title": "Mr"
}
```

### Address Data API

#### `POST /customer/address`
**Purpose:** Only address data (Main & Correspondence address)
**HTTP Method:** POST

**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value"
}
```

**Response (In):**
```json
{
  "residentialAddress": {
    "addressType": "residential",
    "street": "Main Street",
    "houseNumber": "123",
    "postalCode": "8001",
    "city": "Zurich",
    "country": "CH",
    "canton": "ZH",
    "validFrom": "2020-01-01"
  },
  "correspondenceAddress": {
    "addressType": "correspondence",
    "street": "PO Box",
    "houseNumber": "456", 
    "postalCode": "8002",
    "city": "Zurich",
    "country": "CH",
    "canton": "ZH",
    "validFrom": "2024-01-01"
  }
}
```

### Contact Data API

#### `POST /customer/contact`
**Purpose:** Only contact data (Telephone, E-Mail)
**HTTP Method:** POST

**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value"
}
```

**Response (In):**
```json
{
  "phoneNumber": "+41791234567",
  "mobileNumber": "+41791234567",
  "emailAddress": "john.doe@example.ch",
  "preferredChannel": "email",
  "verificationStatus": {
    "phoneVerified": true,
    "emailVerified": true,
    "lastVerification": "2025-01-15T10:00:00Z"
  }
}
```

### KYC Attributes API

#### `POST /customer/kyc`
**Purpose:** Only KYC attributes without identity documents
**HTTP Method:** POST

**Request (Out):**
```json
{
  "sharedCustomerHash": "sha256_hash_value"
}
```

**Response (In):**
```json
{
  "amlRiskClass": "low",
  "pepStatus": "no",
  "pepCategory": null,
  "economicBeneficiary": true,
  "fatcaStatus": "non_us_person",
  "tin": "756.1234.5678.97",
  "taxDomicile": "CH",
  "usTaxLiability": false,
  "sourceOfFunds": "employment",
  "riskAssessment": {
    "riskScore": 2,
    "riskFactors": [],
    "lastAssessment": "2025-01-15T10:00:00Z"
  }
}
```

---

## API Data Structures

### Technical Specifications

**API Version:** 2.0
**Standard:** OpenAPI 3.0 compliant specification
**Architecture:** RESTful API
**Data Format:** JSON
**Security:** JWT Token with Consent Claims → [Complete JWT token architecture and consent claims structure in Conclusion 06](./06-consent-security-flow.md#jwt-token-architecture-and-consent-claims)
**Authentication:** Header-based JWT transmission

### Modular Data Building Blocks (Version 2.0)

The Open API Customer Relationship Version 2.0 defines modular data building blocks according to the reference process → [Detailed data structures in Conclusion 03 Reference Process](./03-reference-process.md):

**Available Data Building Blocks:**
- **Identity:** Personal master data with verification level (QEAA/EAA/self-declared)
- **Address:** Residential and correspondence addresses with validity periods
- **Contact:** Communication channels with verification status
- **Consent:** Consent management → [Detailed structures in Conclusion 06](./06-consent-security-flow.md)
- **KYC/Compliance:** Regulatory compliance data (AML, FATCA, PEP)

**Integration:** These data building blocks can be retrieved individually or combined via the corresponding API endpoints.

#### Building Block: Identity
```json
{
  "identity": {
    "personalData": {
      "title": "string - Salutation (Mr, Ms, etc.)",
      "firstName": "string - First Name",
      "lastName": "string - Last Name",
      "gender": "string - Gender",
      "dateOfBirth": "date - Date of Birth (YYYY-MM-DD)",
      "placeOfBirth": "string - Place of Birth",
      "nationality": "array - Nationality(ies)",
      "maritalStatus": "string - Marital Status"
    },
    "verificationLevel": "string - QEAA|EAA|self-declared",
    "verificationDate": "datetime - Verification Time",
    "verificationProvider": "string - Identity Service Provider"
  }
}
```

#### Building Block: Address
```json
{
  "address": {
    "addressType": "string - residential|correspondence|business",
    "street": "string - Street",
    "houseNumber": "string - House Number",
    "postalCode": "string - Postal Code",
    "city": "string - City",
    "country": "string - Country (ISO Code)",
    "canton": "string - Canton/Region",
    "validFrom": "date - Valid from",
    "validTo": "date - Valid until"
  }
}
```

#### Building Block: Contact
```json
{
  "contact": {
    "phoneNumber": "string - Phone Number",
    "mobileNumber": "string - Mobile Number",
    "emailAddress": "string - E-Mail Address",
    "preferredChannel": "string - email|sms|phone|app",
    "verificationStatus": "string - verified|pending|unverified"
  }
}
```

#### Building Block: Consent
**Consent Management Structures:** → [Complete consent data structures, JWT claims, and lifecycle management in Conclusion 06 Consent and Security Flow](./06-consent-security-flow.md)

Basic consent reference structure:
```json
{
  "consentId": "uuid - Unique Consent ID", 
  "dataCategories": "array - Requested data categories",
  "purposes": "array - Data usage purposes",
  "status": "active|revoked|expired"
}
```

#### Building Block: KYC/Compliance
```json
{
  "kycData": {
    "economicBeneficiary": "boolean - Beneficial Ownership",
    "taxDomicile": "string - Tax Domicile",
    "usTaxLiability": "boolean - US Tax Liability",
    "fatcaStatus": "string - FATCA Status",
    "tin": "string - Tax Number (AHV Number)",
    "amlRiskClass": "string - AML Risk Class",
    "pepStatus": "string - PEP Status",
    "sourceOfFunds": "string - Source of Funds",
    "riskAssessment": {
      "riskScore": "number - Risk Score",
      "riskFactors": "array - Risk Factors",
      "lastAssessment": "datetime - Last Assessment"
    }
  }
}
```


### sharedCustomerHash Concept

**Purpose:** Unique but anonymous identification of customers across providers
**Implementation:** SHA-256 hash of standardized identity data
**Security:** Salt-based hashing for additional security
**Privacy:** GDPR-compliant through pseudonymization

**Hash Input Data:**
```
hash_input = normalize(
  firstName + lastName + dateOfBirth + 
  placeOfBirth + nationality + salt
)
sharedCustomerHash = SHA256(hash_input)
```

---

## Use Case Implementation

**Detailed implementation examples and technical integration patterns:** → [Complete use case implementations in Implementation and Execution](../implementation/use-case-implementation-examples.md)

The implementation guide covers:
- **Bank Onboarding:** Complete API call sequences and integration patterns
- **Customer Discovery & Verification:** Step-by-step technical implementation  
- **Consent Management & Data Request:** JWT-based consent flows
- **Business Impact Metrics:** Efficiency gains and customer benefits

---

## Implementation Guidelines

The complete technical implementation guidelines, including Request/Response formats, Error Handling, Pagination, and OpenAPI 3.0 specifications, are available in the separate technical documentation.

**Central Implementation Standards:**
- **OpenAPI 3.0** Specification for automatic code generation
- **FAPI 2.0 Security** → [Detailed Security Requirements in Conclusion 06](./06-consent-security-flow.md)
- **Semantic Versioning** with Backward Compatibility
- **Comprehensive Testing** → [Testing Framework in Conclusion 08](./08-testing-verification.md)

This conceptual API specification provides the basis for the technical implementation.

---

**Version:** 1.1
**Date:** November 2025
**Status:** Reviewed for Alpha Version 1.0

---

[Sources and References](./sources-and-references.md)
