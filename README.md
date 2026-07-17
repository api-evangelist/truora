# Truora (truora)

Truora is a Latin American identity verification and fraud-prevention platform. Its REST APIs run background checks on people, vehicles, and companies across LatAm, validate documents/faces/email/phone for KYC, and orchestrate web and WhatsApp conversational onboarding flows. All requests authenticate with a `Truora-API-Key` header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/truora/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/truora/refs/heads/main/apis.yml)

## Tags

- Identity Verification
- KYC
- Background Checks
- Fraud Prevention
- LatAm
- WhatsApp

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Truora Checks API

Runs full background checks on persons, vehicles, and companies across LatAm databases (CO, CL, MX, PE, BR, SV, CR), returning identity, criminal, international, and professional-background variables plus a risk score, PDF summary, attachments, and continuous monitoring.

- **Human URL:** [https://dev.truora.com/checks/create/](https://dev.truora.com/checks/create/)
- **Base URL:** `https://api.checks.truora.com`

#### Tags

- Background Checks
- KYC
- Fraud Prevention

#### Properties

- [Documentation](https://dev.truora.com/checks/create/)
- [API Reference](https://dev.truora.com/docs/)
- [OpenAPI](openapi/truora-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/truora.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Truora Validators API

Creates KYC validations — document verification, facial recognition and re-validation, email, phone, and electronic signature — returning signed upload URLs for subject media and extracted OCR/match details on retrieval.

- **Human URL:** [https://dev.truora.com/validators/document_validation_api/](https://dev.truora.com/validators/document_validation_api/)
- **Base URL:** `https://api.validations.truora.com`

#### Tags

- Document Validation
- Facial Recognition
- KYC

#### Properties

- [Documentation](https://dev.truora.com/validators/document_validation_api/)
- [API Reference](https://dev.truora.com/docs/)
- [OpenAPI](openapi/truora-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/truora.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Truora Digital Identity API

Retrieves the state and consolidated results of Digital Identity verification processes launched through hosted web flows or WhatsApp conversational onboarding, combining document, face, and liveness checks into a single scored decision.

- **Human URL:** [https://dev.truora.com/digital-identity/get_results/](https://dev.truora.com/digital-identity/get_results/)
- **Base URL:** `https://api.identity.truora.com`

#### Tags

- Digital Identity
- WhatsApp
- Onboarding

#### Properties

- [Documentation](https://dev.truora.com/digital-identity/create_process_link/)
- [API Reference](https://dev.truora.com/docs/)
- [OpenAPI](openapi/truora-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/truora.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Truora Account API

Issues and manages Truora API keys — backend JWTs for server-to-server calls and short-lived web integration tokens (`key_type=web`) used to launch Digital Identity processes in the browser or WhatsApp flows.

- **Human URL:** [https://dev.truora.com/guides/web_integration_token/](https://dev.truora.com/guides/web_integration_token/)
- **Base URL:** `https://api.account.truora.com`

#### Tags

- Authentication
- API Keys
- Tokens

#### Properties

- [Documentation](https://dev.truora.com/validators/authentication/)
- [API Reference](https://dev.truora.com/docs/)
- [OpenAPI](openapi/truora-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/truora.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

## Common Properties

- [GitHub Organization](https://github.com/truora)
- [LinkedIn](https://www.linkedin.com/company/truora)
- [Website](https://www.truora.com/)
- [Documentation](https://dev.truora.com/)
- [Plans](plans/truora-plans-pricing.yml)
- [Rate Limits](rate-limits/truora-rate-limits.yml)
- [Fin Ops](finops/truora-finops.yml)
- [Blog](https://www.truora.com/en/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
