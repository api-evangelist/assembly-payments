---
name: assembly-payments-payto-agreement
description: Set up a PayTo agreement and initiate payments against it.
api: PayTo
operations:
- validateAgreement
- createAgreement
- getAgreementDetails
- initiatePaymentRequest
- getInitiatePaymentStatus
- amendAgreementStatus
generated: '2026-10-22'
method: generated
---

# Set up a PayTo agreement and initiate payments against it.

1. Validate the agreement terms with `validateAgreement`.
2. Create it with `createAgreement` using the returned agreement UUID; the payer must authorise it in their bank.
3. Check status with `getAgreementDetails` until it is active.
4. Initiate a debit with `initiatePaymentRequest` and track it with `getInitiatePaymentStatus`.
5. Suspend, resume or cancel via `amendAgreementStatus`.

## Rules

- Authenticate with an OAuth2 client-credentials bearer token (Zai auth host); never log the token.
- Use the sandbox / prelive servers in the spec before production.
- PATCH state transitions are not documented as idempotent in the saved contract: read status before retrying a mutating call.
