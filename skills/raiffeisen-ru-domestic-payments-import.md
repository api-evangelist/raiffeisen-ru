---
name: raiffeisen-ru-domestic-payments-import
description: Import ruble payment orders or mass payments from 1C, CSV, XML or MT103 files and track the import task.
api: openapi/raiffeisen-ru-domestic-payments-import-openapi.yml
operations:
- import1CDomesticPayment
- importCsvDomesticPayment
- importXmlDomesticPayment
- importMT103DomesticPayment
- import1CMassPayment
- getImportStatus
- getImportStatusFull
generated: '2026-10-09'
method: generated
source: openapi/raiffeisen-ru-domestic-payments-import-openapi.yml
---

# Рублевые переводы. Импорт платежей в форматах 1С, CSV, XML, MT103 (0.0.3)

Import ruble payment orders or mass payments from 1C, CSV, XML or MT103 files and track the import task.

Grounded in `openapi/raiffeisen-ru-domestic-payments-import-openapi.yml` (operationIds checked against the spec).

## Steps

1. Authenticate first; send the `Authorization` header parameter declared by each operation.
2. Upload the file to the matching import operation (`import1CDomesticPayment`, `importCsvDomesticPayment`, `importXmlDomesticPayment`, `importMT103DomesticPayment`, or the mass-payment equivalents such as `import1CMassPayment`); keep the importTaskId.
3. Poll `getImportStatus` for the task and `getImportStatusFull` for the status of every imported document.
4. The spec declares no idempotency key: do not blindly retry an upload that may have succeeded; check import status first.

## Notes

- Docs and the current spec are also reachable via the provider's MCP server (`https://api.raiffeisen.ru/developer-portal/public/mcp`, tools `list_public_apis`, `get_public_api_specification`).
- Error responses are as declared per operation in the spec; no provider idempotency-key convention is documented in it.
