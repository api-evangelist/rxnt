# RXNT (rxnt)

RXNT is a cloud-based, integrated healthcare software company offering ONC-certified Electronic Health Records (EHR), EPCS-enabled electronic prescribing (eRx), practice management, medical billing, scheduling, and a patient portal for outpatient practices. Most of the RXNT platform is delivered as SaaS with **no broadly published developer API** - product integrations (labs, radiology, billing clearinghouses) are arranged privately with partners.

The one documented, publicly described API is the **RXNT Clinical Data API (CDAPI)**, an ONC-mandated interface that lets registered third-party applications retrieve a patient's Common Clinical Data Set (CCDS). **Access is partner-gated:** third parties must register with RXNT (support@rxnt.com) to receive credentials before calling it. The public reference repository has been archived read-only since December 2021.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/rxnt/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/rxnt/refs/heads/main/apis.yml)

## Access Model

- **Gated, not self-serve.** There is no open developer portal or self-service API key signup. To use the Clinical Data API, a third party must first register with RXNT (support@rxnt.com); RXNT then issues login credentials.
- **Authentication.** Callers POST their username/password to `AuthenticateUser` and receive a time-limited `Token` and `Signature`, which must be included in the body of every subsequent request along with `DoctorCompanyId`.
- **ONC-mandated scope.** The CDAPI exists to satisfy ONC 2015 Edition certification criteria for application access - Patient Selection (g)(7), Data Category Request (g)(8), and All Data Request (g)(9). It returns CCDS data as XML embedded in a JSON envelope.
- **The rest of the platform (EHR, eRx, practice management, billing, scheduling, patient portal) has no documented public API.** Those are commercial SaaS products; integrations are handled through RXNT partnerships rather than an open API.

## Tags

- Healthcare
- EHR
- E-Prescribing
- Clinical Data
- ONC Certified
- CCDS
- Medical Billing
- Practice Management

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs

### RXNT Clinical Data API

ONC-certified interface (45 CFR 170.315(g)(7), (g)(8), and (g)(9)) that lets registered third-party applications and patient representatives retrieve a patient's Common Clinical Data Set (CCDS) - demographics, problems, medications, allergies, vital signs, lab results, immunizations, procedures, care team, goals, health concerns, and implantable device identifiers. Callers authenticate with RXNT-issued credentials to obtain a time-limited token and signature, then request patient data (by category or in full) that is returned as CCDS XML embedded in a JSON envelope.

- **Human URL:** [https://github.com/RXNT/RxNTClinicalDataAPI](https://github.com/RXNT/RxNTClinicalDataAPI)
- **Base URL:** `https://app2.rxnt.com/MasterIndexExternalAPIServices/masterindexexternalapi/v1`

#### Tags

- Clinical Data
- CCDS
- Patient Data
- ONC Certified
- Interoperability

#### Properties

- [Documentation](https://github.com/RXNT/RxNTClinicalDataAPI)
- [API Reference](https://github.com/RXNT/RxNTClinicalDataAPI)
- [OpenAPI](openapi/rxnt-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

#### Documented Endpoints

- `POST /authentication/AuthenticateUser` — authenticate and obtain a time-limited token and signature
- `POST /patientdashboard/patientccd/GetV1PatientInfoByExternalPatientId` — verify a patient and request CCDS data by category (g7/g8)
- `POST /patientdashboard/patientccd/GetPatientCCDSData` — request all available CCDS data for a patient (g9)

> The OpenAPI definition models these three documented operations. Request and response schemas are honestly modeled from the field names in the RXNT reference (`x-endpoints-modeled: true`); the endpoint paths, methods, and CCDS categories are taken directly from RXNT's published documentation.

## Common Properties

- [GitHub Organization](https://github.com/RXNT)
- [LinkedIn](https://www.linkedin.com/company/rxnt)
- [Website](https://www.rxnt.com/)
- [Documentation](https://github.com/RXNT/RxNTClinicalDataAPI)
- [Plans](plans/rxnt-plans-pricing.yml)
- [Pricing](https://www.rxnt.com/pricing/)
- [Blog](https://www.rxnt.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
