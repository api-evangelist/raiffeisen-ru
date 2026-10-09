---
name: raiffeisen-ru-raif-pay-payouts
description: Send SBP payouts to individuals with Raif Pay, singly or in bundles, and track their status.
api: openapi/raiffeisen-ru-raif-pay-payouts-openapi.yml
operations:
- get-payout-v3-sbp-banks
- post-payout-v1-payouts-draft
- put-payout-v1-payouts-id
- post-v2-payouts
- get-payout-v2-payouts-id
- post-payout-v3-payout-bundles
- get-v3-bundle-payouts
- post-settings-v1-callback
generated: '2026-10-09'
method: generated
source: openapi/raiffeisen-ru-raif-pay-payouts-openapi.yml
---

# API интеграции выплат

Send SBP payouts to individuals with Raif Pay, singly or in bundles, and track their status.

Grounded in `openapi/raiffeisen-ru-raif-pay-payouts-openapi.yml` (operationIds checked against the spec).

## Steps

1. Authenticate with `Authorization: Bearer <secretKey>` as declared by the spec's security schemes.
2. Look up the recipient's bank with `get-payout-v3-sbp-banks` (includes BIC).
3. Either pay directly with `post-v2-payouts`, or create a draft with `post-payout-v1-payouts-draft` and confirm it with `put-payout-v1-payouts-id`.
4. Track a payout with `get-payout-v2-payouts-id`; register a callback URL with `post-settings-v1-callback`.
5. For many recipients create a bundle with `post-payout-v3-payout-bundles` and list its payouts with `get-v3-bundle-payouts`.

## Notes

- Docs and the current spec are also reachable via the provider's MCP server (`https://api.raiffeisen.ru/developer-portal/public/mcp`, tools `list_public_apis`, `get_public_api_specification`).
- Error responses are as declared per operation in the spec; no provider idempotency-key convention is documented in it.
