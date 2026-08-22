# GOV.UK Pay

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
