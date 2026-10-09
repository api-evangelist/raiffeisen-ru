---
name: raiffeisen-ru-bank-statements
description: Generate an account statement asynchronously in a chosen format (XML, Excel, PDF, 1C, MT940/942, camt.052/053), poll its status and download the file.
api: openapi/raiffeisen-ru-bank-statements-openapi.yml
operations:
- camt053Request
- mt940Request
- oneCRequestV2
- pdfRequest
- reportStatus
- downloadReportFile
- mt940SyncRequest
generated: '2026-10-09'
method: generated
source: openapi/raiffeisen-ru-bank-statements-openapi.yml
---

# Выписки

Generate an account statement asynchronously in a chosen format (XML, Excel, PDF, 1C, MT940/942, camt.052/053), poll its status and download the file.

Grounded in `openapi/raiffeisen-ru-bank-statements-openapi.yml` (operationIds checked against the spec).

## Steps

1. Authenticate first (see raiffeisen-ru-authorization); pass the `Authorization` and ID-token header parameters the operation declares.
2. Request a statement with a format operation such as `camt053Request`, `mt940Request`, `oneCRequestV2` or `pdfRequest`; keep the returned report id.
3. Poll `reportStatus` (GET /v1/reports/{reportId}/status) until generation completes; it can return 400, 401, 404 or 500.
4. Download with `downloadReportFile` (GET /v1/reports/{reportId}/file).
5. For a single-call flow use the synchronous variants (`mt940SyncRequest`, etc.), which return the file directly.

## Notes

- Docs and the current spec are also reachable via the provider's MCP server (`https://api.raiffeisen.ru/developer-portal/public/mcp`, tools `list_public_apis`, `get_public_api_specification`).
- Error responses are as declared per operation in the spec; no provider idempotency-key convention is documented in it.
