---
name: assembly-payments-wallet-payout
description: Pay out funds from a wallet account to a user bank account and verify the disbursement.
api: Assembly API
operations:
- showUserWalletAccounts
- showWalletAccount
- setUserDisbursementAccount
- withdrawFunds
- listDisbursement
- showDisbursement
generated: '2026-10-22'
method: generated
---

# Pay out funds from a wallet account to a user bank account and verify the disbursement.

1. Find the wallet with `showUserWalletAccounts` and check its balance via `showWalletAccount`.
2. Set the payout bank account with `setUserDisbursementAccount`.
3. Move funds out with `withdrawFunds` (POST `/wallet_accounts/{id}/withdraw`).
4. Track the payout with `listDisbursement` / `showDisbursement`.

## Rules

- Authenticate with an OAuth2 client-credentials bearer token (Zai auth host); never log the token.
- Use the sandbox / prelive servers in the spec before production.
- PATCH state transitions are not documented as idempotent in the saved contract: read status before retrying a mutating call.
