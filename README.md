# RXNT (rxnt)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
