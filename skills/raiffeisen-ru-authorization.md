---
name: raiffeisen-ru-authorization
description: Obtain, refresh, check and revoke OAuth2 tokens for Raiffeisen corporate APIs via the Authorization API (id.business.raiffeisen.ru).
api: openapi/raiffeisen-ru-authorization-openapi.yml
operations:
- authorize
- token
- tokenLiveness
- revokeToken
- getJwks
generated: '2026-10-09'
method: generated
source: openapi/raiffeisen-ru-authorization-openapi.yml
---

# Авторизация в сервисах Райффайзен Банка

Obtain, refresh, check and revoke OAuth2 tokens for Raiffeisen corporate APIs via the Authorization API (id.business.raiffeisen.ru).

Grounded in `openapi/raiffeisen-ru-authorization-openapi.yml` (operationIds checked against the spec).

## Steps

1. Send the user to `authorize` (GET /oauth2/authorize, Code Flow) to obtain an authorization code.
2. Exchange the code at `token` (POST /oauth2/token); call the same operation with a refresh token to renew.
3. Check an access token with `tokenLiveness` before long jobs; verify JWT signatures with keys from `getJwks`.
4. Revoke tokens at logout with `revokeToken`.
5. Corporate APIs (statements, payments) take the access token in the `Authorization` header parameter (Bearer) and, where declared, an ID token header; read each operation's parameters rather than assuming.

## Notes

- Docs and the current spec are also reachable via the provider's MCP server (`https://api.raiffeisen.ru/developer-portal/public/mcp`, tools `list_public_apis`, `get_public_api_specification`).
- Error responses are as declared per operation in the spec; no provider idempotency-key convention is documented in it.
