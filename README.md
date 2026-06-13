# GOV.UK Pay

UK government digital payment service providing a REST API for accepting card payments, managing payment links, and processing refunds for government digital services. Built and operated by the Government Digital Service (GDS), GOV.UK Pay enables over 1,500 public sector organisations to take payments securely without managing their own PCI DSS compliance.

- **Human URL:** https://www.payments.service.gov.uk/
- **Base URL:** https://publicapi.payments.service.gov.uk/

## Description

GOV.UK Pay is a shared payment platform for the UK public sector, processing over 70,000 payments per day. It handles PCI DSS compliance centrally, supports digital wallets (Apple Pay, Google Pay), recurring payments, telephone (MOTO) payments, and provides webhooks for real-time event notifications.

The platform is free to use; only Payment Service Provider (PSP) transaction fees apply, negotiated through Crown Commercial Service or directly with Adyen or Stripe.

## Links

- **Documentation:** https://docs.payments.service.gov.uk/
- **API Reference:** https://docs.payments.service.gov.uk/api_reference/
- **Webhooks:** https://docs.payments.service.gov.uk/webhooks/
- **Status Page:** https://payments.statuspage.io/
- **Source Code:** https://github.com/alphagov/pay-publicapi
- **Support:** https://www.payments.service.gov.uk/support/
- **Terms of Service:** https://www.payments.service.gov.uk/terms/
- **Privacy Policy:** https://www.payments.service.gov.uk/privacy/

## Key API Endpoints

| Method | Path | Purpose |
|--------|------|---------|
| POST | /v1/payments | Create a payment |
| GET | /v1/payments/{id} | Get payment details |
| GET | /v1/payments/{id}/events | Get payment event history |
| POST | /v1/payments/{id}/cancel | Cancel a payment |
| POST | /v1/payments/{id}/capture | Capture a delayed payment |
| GET | /v1/payments | Search payments |
| POST | /v1/payments/{id}/refunds | Create a refund |
| GET | /v1/payments/{id}/refunds/{rid} | Get refund status |
| GET | /v1/payments/{id}/refunds | List refunds for a payment |
| GET | /v1/refunds | Search all refunds |
| POST | /v1/agreements | Create recurring payment agreement |
| GET | /v1/agreements/{id} | Get agreement details |
| POST | /v1/agreements/{id}/cancel | Cancel agreement |
| GET | /v1/agreements | Search agreements |
| GET | /v1/disputes | Search disputes |
| POST | /v1/auth | Authorise MOTO payment |

## Authentication

Bearer token authentication using API keys from the GOV.UK Pay admin tool:

```
Authorization: Bearer {YOUR_API_KEY}
```

The same base URL serves both test and live environments; the API key determines which environment is used.

## Rate Limits

- 15 POST requests/second to create payments
- 15 POST requests/second to capture delayed payments
- 15 other POST requests/second
- GET requests have a very high limit
- HTTP 429 / error code P0900 returned when exceeded; retry after 1 second

## Pricing

The GOV.UK Pay platform is **free** for eligible public sector organisations. PSP transaction fees are paid separately and negotiated via Crown Commercial Service or directly with Adyen/Stripe.

---

*This profile is part of the [APIs.io](https://apis.io) catalog maintained by [API Evangelist](https://apievangelist.com).*
