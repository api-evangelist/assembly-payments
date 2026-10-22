---
name: assembly-payments-refund-or-cancel
description: 'Reverse a marketplace item: cancel an unpaid item, void an authorization, or refund a paid one.'
api: Assembly API
operations:
- showItemStatus
- cancelItem
- voidPayment
- refund
- listItemTransactions
generated: '2026-10-22'
method: generated
---

# Reverse a marketplace item: cancel an unpaid item, void an authorization, or refund a paid one.

1. Read the current state with `showItemStatus`.
2. If not yet paid, `cancelItem`; if only authorized (`authorizePayment`), `voidPayment`.
3. If paid, issue `refund` (PATCH `/items/{id}/refund`).
4. Confirm with `listItemTransactions`.

## Rules

- Authenticate with an OAuth2 client-credentials bearer token (Zai auth host); never log the token.
- Use the sandbox / prelive servers in the spec before production.
- PATCH state transitions are not documented as idempotent in the saved contract: read status before retrying a mutating call.
