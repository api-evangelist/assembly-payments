---
name: assembly-payments-marketplace-payment
description: 'Take a marketplace payment end to end: onboard buyer and seller, attach a funding account, create an item, pay it, and track its status.'
api: Assembly API
operations:
- createUser
- createBankAccount
- createCardAccount
- createItem
- makePayment
- showItemStatus
- listItemTransactions
generated: '2026-10-22'
method: generated
---

# Take a marketplace payment end to end: onboard buyer and seller, attach a funding account, create an item, pay it, and track its status.

1. Create the buyer and the seller with `createUser`.
2. Attach a funding source to the buyer: `createCardAccount` or `createBankAccount`.
3. Create the payment item linking buyer, seller and amount with `createItem`.
4. Charge the buyer with `makePayment` (PATCH `/items/{id}/make_payment`); prefer `makePaymentAsync` for long-running payments.
5. Poll `showItemStatus` and read `listItemTransactions` to confirm settlement, or subscribe to callbacks instead of polling.

## Rules

- Authenticate with an OAuth2 client-credentials bearer token (Zai auth host); never log the token.
- Use the sandbox / prelive servers in the spec before production.
- PATCH state transitions are not documented as idempotent in the saved contract: read status before retrying a mutating call.
