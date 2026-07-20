---
name: Get Bank of Sydney banking product reference data
description: >-
  Retrieve Bank of Sydney's public banking product catalogue and product detail via the
  Consumer Data Right (CDR) Product Reference Data API - no authentication required.
api: openapi/bank-of-sydney-cds-banking-products-openapi.yml
operations: [listBankingProducts, getBankingProductDetail]
auth: none
base_url: https://openbank.api.banksyd.com.au/cds-au/v1
---

# Get Bank of Sydney banking product reference data

Bank of Sydney exposes its retail and business product catalogue (home loans, deposits,
everyday accounts) as a **public, unauthenticated** CDR Product Reference Data (PRD) API.
No API key, OAuth token, or accreditation is required for these two operations.

## Rules that always apply
- **Version header is mandatory.** Every request must send `x-v` (a positive integer).
  Bank of Sydney PRD supports `x-v: 4` and `x-v: 5`. Sending an unsupported version
  returns `406 Unsupported Version`; a missing header returns `400 Missing Required Header`.
- **Errors** come back as a CDS `ResponseErrorListV2` envelope: `{ "errors": [ { "code",
  "title", "detail", "meta" } ] }` with `urn:au-cds:error:*` codes. See
  `errors/bank-of-sydney-problem-types.yml`.
- **Pagination** uses `page` (default 1) and `page-size` (default 25); the response
  carries `links` (first/prev/self/next/last) and `meta` (totalRecords/totalPages).

## Steps

1. **List products** - call `listBankingProducts`:
   `GET /banking/products` with header `x-v: 4`.
   Optional filters: `effective` (CURRENT|FUTURE|ALL), `updated-since` (DateTimeString),
   `brand`, `product-category` (e.g. `RESIDENTIAL_MORTGAGES`, `TERM_DEPOSITS`,
   `TRANS_AND_SAVINGS_ACCOUNTS`), `page`, `page-size`.
   Read `data.products[]` - each item has `productId`, `name`, `productCategory`, `brand`.

2. **Get product detail** - for a chosen `productId`, call `getBankingProductDetail`:
   `GET /banking/products/{productId}` with header `x-v: 4`.
   Returns the full `data` product detail (rates, fees, features, eligibility, constraints).
   A missing/unknown id returns `404 Resource Not Found`.

## Notes
- Only these two operations are public. Account, balance, transaction, payee, direct-debit
  and scheduled-payment operations in the same spec require **CDR authorisation** (an
  Accredited Data Recipient acting under consumer consent via OAuth2/OIDC + mutual-TLS) -
  see `authentication/bank-of-sydney-authentication.yml` and `scopes/bank-of-sydney-scopes.yml`.
