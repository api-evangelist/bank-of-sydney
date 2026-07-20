# Bank of Sydney (bank-of-sydney)

Bank of Sydney Ltd is an Australian authorised deposit-taking institution (ADI) headquartered in Sydney, New South Wales, offering personal and business banking, home loans, deposits, and everyday accounts. It is a wholly owned subsidiary of Lebanon-based Bank of Beirut. As a regulated ADI, Bank of Sydney participates in Australia's Consumer Data Right (CDR) / Open Banking regime, exposing a public, unauthenticated Product Reference Data (PRD) API that conforms to the Data Standards Body (DSB) Consumer Data Standards.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bank-of-sydney/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bank-of-sydney/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Product Reference Data
- ADI

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Bank of Sydney CDR Product Reference Data API

Public, unauthenticated Product Reference Data (PRD) API exposing Bank of Sydney's retail and business banking product catalogue (home loans, deposits, everyday accounts) under the Consumer Data Right. Confirmed live at HTTP 200 with an `x-v` response header (supports versions 4 and 5) returning a `data.products` array (29 products) conforming to the DSB Consumer Data Standards banking schema.

- **Human URL:** [https://www.banksyd.com.au/tools-support/open-banking/](https://www.banksyd.com.au/tools-support/open-banking/)
- **Base URL:** `https://openbank.api.banksyd.com.au/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Public

#### Properties

- [Documentation](https://www.banksyd.com.au/tools-support/open-banking/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#banking-products)
- [OpenAPI](openapi/bank-of-sydney-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.banksyd.com.au/)
- [Documentation](https://www.banksyd.com.au/tools-support/open-banking/)
- [LinkedIn](https://www.linkedin.com/company/bank-of-sydney)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
