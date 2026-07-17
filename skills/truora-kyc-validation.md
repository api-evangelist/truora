---
name: Run a KYC document or face validation
description: Create a Truora KYC validation (document, face, email, phone, or e-signature), upload subject media to the returned signed URLs, then retrieve the extracted OCR/match details.
api: openapi/truora-openapi.yml
operations: [createValidation, getValidation]
---

# Run a KYC validation

Truora Validators verify a document, face, email, phone, or electronic signature.
Document/face validations return signed upload URLs for the subject's media.

## Auth
- Send `Truora-API-Key: <JWT>`. Host: `https://api.validations.truora.com`.

## Steps
1. **createValidation** — `POST /v1/validations` (form-encoded) with `type`
   (`document-validation` | `face-recognition` | `face-revalidation` | `email` |
   `phone` | `electronic-signature`), `country`, and `user_authorized=true`. For
   `document-validation` also set `document_type` (national-id, passport, foreign-id,
   driver-license). Keep the returned `validation_id`.
2. **Upload media** — for document/face validations, `PUT` the subject's image(s) to
   the signed `front_url` (and `reverse_url` for two-sided documents) returned by
   step 1. These are short-lived signed URLs — upload promptly.
3. **getValidation** — `GET /v1/validations/{validation_id}?show_details=true`. Poll
   `validation_status` until `success` or `failure`; with `show_details=true` the
   response includes extracted OCR data, match results, and image links in `details`.

## Rules
- `user_authorized=true` is required — the subject must consent (Habeas Data / GDPR).
- Errors use a `{code, message}` envelope; `401` = bad API key, `404` = unknown
  `validation_id`.
- `validation_status: failure` is a verification outcome, not an HTTP error.
