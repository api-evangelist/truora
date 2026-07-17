---
name: Launch and read a Digital Identity / WhatsApp verification process
description: Mint a web integration token, launch a Truora Digital Identity process (browser or WhatsApp), then poll and read the consolidated scored decision.
api: openapi/truora-openapi.yml
operations: [createApiKey, getProcess, getProcessResult]
---

# Launch a Digital Identity process

A Digital Identity process runs Truora's prebuilt, hosted verification flow
(document + face + liveness) in the browser or over WhatsApp, and returns one
consolidated scored decision.

## Auth
- Backend calls use a backend `Truora-API-Key`. Launching a browser/WhatsApp flow
  uses a short-lived **web integration token**.

## Steps
1. **createApiKey** — `POST /v1/api-keys` (form-encoded, host
   `https://api.account.truora.com`) with `key_type=web` and the appropriate
   `grant` (e.g. `digital-identity`). The returned JWT is the web integration token
   — it is shown once. Use it to open the hosted web flow (via the browser SDK) or
   start a WhatsApp flow.
2. **getProcess** — `GET /v1/processes/{process_id}` (host
   `https://api.identity.truora.com`). Poll `status` until the process completes.
   `process_id` comes from the launched flow (or a webhook).
3. **getProcessResult** — `GET /v1/processes/{process_id}/result` for the
   consolidated decision plus the underlying document/face/liveness validations.

## Rules
- Prefer webhooks over polling for production: subscribe to
  `identity_process.succeeded` / `identity_process.failed` (see
  `asyncapi/truora-webhooks.yml`); payloads arrive as a JWT.
- Web integration tokens are short-lived — mint one per launch, do not cache.
- For user-authenticated identity data reuse (OIDC), consider Truora Pass instead
  (`scopes/truora-scopes.yml`).
- Errors use a `{code, message}` envelope; `404` = unknown `process_id`.
