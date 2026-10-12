---
name: raiffeisen-ru-raif-pay-sbp-qr
description: 'Accept a payment through the Faster Payments System (SBP) with Raif Pay: register a QR, check payment, refund and reconcile.'
api: openapi/raiffeisen-ru-raif-pay-sbp-openapi.yml
operations:
- createQrV2
- getQrV2
- getPaymentInfo
- deleteQrV2
- createRefund
- getRefund
- getBanksForRefunds
- postApiSettingsV1Callback
- get-report-v1-transactions-summary
generated: '2026-10-09'
method: generated
source: openapi/raiffeisen-ru-raif-pay-sbp-openapi.yml
---

# API интеграции Системы быстрых платежей (СБП)

Accept a payment through the Faster Payments System (SBP) with Raif Pay: register a QR, check payment, refund and reconcile.

Grounded in `openapi/raiffeisen-ru-raif-pay-sbp-openapi.yml` (operationIds checked against the spec).

## Steps

1. Authenticate with the merchant secret key: `Authorization: Bearer <secretKey>` (securityScheme `secretKey`). Test against pay-test.raif.ru, production against pay.raif.ru.
2. Optionally register a callback URL with `postApiSettingsV1Callback`.
3. Register a QR with `createQrV2` and show it to the payer; read it back with `getQrV2`.
4. Check the payment with `getPaymentInfo` (GET /sbp/v1/qr/{qrId}/payment-info); cancel an unused QR with `deleteQrV2`.
5. Refund with `createRefund` and track it with `getRefund`; `getBanksForRefunds` lists eligible banks.
6. Reconcile with `get-report-v1-transactions-summary` over a period.

## Notes

- Docs and the current spec are also reachable via the provider's MCP server (`https://api.raiffeisen.ru/developer-portal/public/mcp`, tools `list_public_apis`, `get_public_api_specification`).
- Error responses are as declared per operation in the spec; no provider idempotency-key convention is documented in it.
