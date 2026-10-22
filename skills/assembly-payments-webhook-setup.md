---
name: assembly-payments-webhook-setup
description: Subscribe to Zai webhooks, set the signing secret, and inspect delivery jobs.
api: Webhooks API
operations:
- createSecretKey
- createWebhook
- getAllWebhooks
- getJobs
- getJob
generated: '2026-10-22'
method: generated
---

# Subscribe to Zai webhooks, set the signing secret, and inspect delivery jobs.

1. Create a signing secret with `createSecretKey` and use it to verify webhook signatures (see https://developer.hellozai.com/docs/verify-webhook-signatures).
2. Register an endpoint with `createWebhook`.
3. List subscriptions with `getAllWebhooks`.
4. Inspect deliveries with `getJobs` / `getJob` when troubleshooting.

## Rules

- Authenticate with an OAuth2 client-credentials bearer token (Zai auth host); never log the token.
- Use the sandbox / prelive servers in the spec before production.
- PATCH state transitions are not documented as idempotent in the saved contract: read status before retrying a mutating call.
