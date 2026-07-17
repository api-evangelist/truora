---
name: Run a LatAm background check and read the result
description: Create a Truora background check on a person, vehicle, or company, poll for completion, then read the risk score, variables, and PDF summary.
api: openapi/truora-openapi.yml
operations: [createCheck, getCheck, getCheckVariables, getCheckPdf]
---

# Run a LatAm background check

Truora runs background checks against LatAm public and legal-entity databases
(CO, CL, MX, PE, BR, SV, CR). Checks are asynchronous: create, then poll.

## Auth
- Send `Truora-API-Key: <JWT>` on every request (a backend key from the dashboard
  or `POST /v1/api-keys`). Host: `https://api.checks.truora.com`.

## Steps
1. **createCheck** — `POST /v1/checks` (form-encoded) with `national_id`, `country`
   (ISO: CO/CL/MX/PE/BR/SV/CR), and `type` (person|vehicle|company). Set
   `user_authorized=true` — LatAm Habeas Data requires end-user consent. Checks are
   de-duplicated by default; pass `force_creation=true` only to force a fresh check.
   Keep the returned `check_id`.
2. **getCheck** — `GET /v1/checks/{check_id}`. Poll until `status` is `completed`
   (other values: `not_started`, `in_progress`, `delayed`, `error`). Read `score`
   (0–1 risk score).
3. **getCheckVariables** — `GET /v1/checks/{check_id}/variables` for the individual
   findings behind the score.
4. **getCheckPdf** — `GET /v1/checks/{check_id}/pdf` for the shareable PDF summary.

## Rules
- Errors use a `{code, message}` JSON envelope (not RFC 9457). A `401` means a
  missing/invalid `Truora-API-Key`; `404` means the `check_id` does not exist.
- To monitor a subject over time instead of a one-shot check, use
  `createContinuousCheck` (`POST /v1/continuous-check`).
- Do not treat `status: error`/`delayed` as an HTTP failure — it is resource state.
