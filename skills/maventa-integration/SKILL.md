---
name: maventa-integration
description: >-
  Build, test and debug integrations with Maventa's e-invoicing and e-document
  exchange APIs, using the official Maventa documentation as the source. Use
  when the user works with the Maventa REST or SOAP API (OAuth2 tokens, vendor
  API key, company UUID), sends invoices (routing, Peppol, Finvoice, Peppol BIS
  3.0, email, printing, consumer invoicing in Finland, Norway and Sweden),
  receives invoices (Peppol registration, scanning, AutoScan, Detect fraud
  checks), exchanges orders and other Peppol documents, uses webhooks, manages
  companies, users and billing data, uses receivables and debt collection
  (Ropo, Amili), or asks about country rules and e-invoicing mandates where
  Maventa operates. Also use for Maventa error messages and for questions
  about the Maventa testing and production environments.
license: MIT
metadata:
  version: "1.0.2"
  generated: "2026-11-26"
  source: "https://documentation.maventa.com"
---

# Maventa integration

Maventa is an e-invoicing and e-document exchange service (part of Visma). An
ERP, accounting or billing system integrates with it over an API to send and
receive invoices and other business documents through Peppol, operator
networks, consumer channels (online banks, digital mailboxes), email and print.

This skill is a map of the official documentation at
https://documentation.maventa.com. The facts below are the stable basics.
**For anything else, fetch the page and answer from it.** The documentation
changes; this file and the indexes in `references/` are a snapshot.

## How to use the documentation

1. **Pick pages from the index.** Each file in `references/` lists every page
   of one documentation section with a one-line summary:
   - [references/integration-guide.md](references/integration-guide.md): how
     things work and which API calls to use, by task (sending, receiving,
     webhooks, Peppol, formats, accounts, receivables).
   - [references/api-specification.md](references/api-specification.md): REST
     and SOAP API reference pages, with every REST operation listed as one line
     (`METHOD /path: summary`) so you can find the right page for an endpoint.
   - [references/services-and-reach.md](references/services-and-reach.md):
     per-country pages (networks, formats, mandates, consumer channels) and
     upcoming changes.
   - [references/other-guides.md](references/other-guides.md): standalone
     guides (Peppol API, AutoScan, Connector, migration notices).
2. **Fetch the page as markdown.** Every URL in the indexes ends in `.md` and
   returns clean markdown. Fetch the one or two pages that match the question
   and answer from their content, citing the page URL (without `.md`, that is
   the human-readable page).
3. **If the index looks out of date** (a URL returns 404, or a page you expect
   is missing), read the live index at https://documentation.maventa.com/llms.txt,
   which has the same entries.
4. **Avoid `llms-full.txt`** (about 1.4 MB, the whole site) unless the user
   explicitly wants everything in one document.
5. **For anything time-sensitive** (deprecations, renamed parameters, new
   features, dates), also check:
   - Upcoming changes: https://documentation.maventa.com/services-and-reach/upcoming-changes.md
   - Developer changelog (API changes, with an index of entries): https://documentation.maventa.com/changelogs/developer-changelog.md
   - Product changelog (feature announcements): https://documentation.maventa.com/changelogs/product-changelog.md

Swagger UI with the full machine-readable specs: https://swagger.maventa.com.
REST API pages also show their endpoints as markdown tables in their `.md`.

## Core concepts

- **Company**: a Maventa account that sends and/or receives documents,
  identified by its company UUID. API calls act on one company at a time.
- **User**: belongs to one or more companies. Each user has a user API key.
  The user's role (admin or user) limits what its tokens may do.
- **Partner and vendor**: an integrator gets a partner company account. A
  *vendor* is the integrated software; each one has a **vendor API key**
  (Settings > Company settings > Software API keys). One partner can own
  several vendor API keys, for example per product or country.
- **Environments**: testing (`https://testing.maventa.com`, REST base hosts
  ending in `-stage`, such as `https://ax-stage.maventa.com`) and production
  (`https://secure.maventa.com`, `https://ax.maventa.com`). API keys are
  separate per environment and do not work across them; `USER NOT FOUND`
  usually means a key from the wrong environment.
- **Testing environment behaviour**: internal sends between Maventa customers
  and Peppol test network sends are real; external operator routes, consumer
  routes, email and print are simulated (marked SENT, not delivered).
  Notification emails go to real addresses. The database can be cleared
  without notice. Do not use production data there.
- **Going live**: the integration is tested in the testing environment and the
  Maventa Integration Agreement is signed before production keys are issued.
  Contact: integrations@maventa.com.

Source: https://documentation.maventa.com/integration-guide/getting-started.md

## Authentication

REST (recommended; new features come only to REST):

- `POST /oauth2/token` with `client_id` = company UUID, `client_secret` = user
  API key, plus `vendor_api_key`. Operators use `client_id` = operator id and
  `client_secret` = operator secret.
- **Request the scopes you need** in `scope`, space separated, for example
  `scope=company lookup invoice:send invoice:receive`. Without `scope` the
  token gets only `global` and `company`, and the invoice endpoints return
  `401 Unauthorized`.
- Cache the token and renew it a little before `expires_in` runs out. Tokens
  are signed JSON of variable length. A token that lacks rights for a resource
  will not be fixed by requesting a new one with the same credentials.
- The REST API is split across hosts (`ax`, `receivables`, `validator`,
  `bling`, each with a `-stage` variant); one token works for all of them.

SOAP (legacy, still supported): WSDL at `https://testing.maventa.com/apis/v1.1/wsdl`
and `https://secure.maventa.com/apis/v1.1/wsdl`, authenticated with API keys on
each request, dates as `YYYYMMDD`, UTF-8. It does not have every feature, and
both APIs can be used side by side during a migration.

Sources: https://documentation.maventa.com/api-specification/rest-api/getting-started.md,
https://documentation.maventa.com/api-specification/soap-api/getting-started.md

## Where to look

| Task | Start with |
| --- | --- |
| Plan an integration, get API keys, testing vs production | Integration guide: Getting Started |
| Send an invoice, recipient lookup and routing, delivery status | Integration guide: Invoice sending, then Invoices API |
| Send to consumers (B2C) | Consumer Invoicing and its Finland, Norway or Sweden variant, then B2CFI, B2CNO or B2CSE API |
| Print or email delivery | Printing (and its country variant), Email invoicing |
| Receive invoices, register as a Peppol receiver, polling | Invoice receiving, Peppol Network |
| Paper and PDF invoices into e-invoices | Scanning, AutoScan, Scanning API |
| Fraud and risk checks on received invoices | Detect, Fraud reporting, Detect API |
| Orders, catalogues, despatch advice, invoice responses | Peppol: Document Exchange and Invoice Response, then Documents API |
| Self-billing over Peppol | Self-billing support |
| Webhooks and event types | Webhooks (receivables events: Receivables webhooks) |
| Invoice XML formats, validation, document type codes | Invoicing formats, Validation, Peppol BIS 3.0, Finvoice 3.0, Document types, Validator API |
| Create and configure companies, settings, users | Companies and Settings, Department Company, Users, Companies & settings API, Partner API |
| Billing data for invoicing your own customers | Billing, Billing API |
| Reminders and debt collection | Accounts receivable, Ropo, Amili Kassavirta, Amili Perintä, Receivables API |
| Country rules, networks and mandates | Services & Reach: the country page |
| Look up whether a company is reachable | Lookups API (Maventa routing); for raw Peppol data, the Peppol Lookup tool at https://documentation.maventa.com/peppol-lookup/ |
| An endpoint, parameter or error code | `references/api-specification.md` operation list, then the API page |
| Something changed or is about to | Upcoming changes, developer changelog |

## Integration rules and common pitfalls

These come from the documentation; check the linked page for the current detail.

**Sending**

- Store the invoice ID (or send your own `uuid`) and track status by it. The
  only reliable way to prevent double sends is your own `uuid`: duplicates
  are rejected, so generate it once per invoice and reuse it on retries. The
  company setting `stop_duplicate_numbers` (same invoice number rejected for
  7 days with `DUPLICATE INVOICE NUMBER`) is only a safety net: it is not
  race-condition proof, so two sends at almost the same time can both get
  through. Never present the two as equivalent.
- API parameters override recipient details in the XML. Adding an operator
  code such as `PEPPOL` next to the e-invoice address forces that network and
  disables fallback routes. Use `disabled_routes` to block einvoice, email or
  print, not the legacy `PRINT`/`EMAIL` keywords in the XML.
- SENT is not delivered: an invoice can still fail after SENT. Prefer webhooks;
  if polling, poll a PENDING invoice hourly and a SENT one daily.
- A sent invoice cannot be cancelled; send a credit note.
- PDF attachments must not be encrypted or permission-restricted.
- Invoice numbers longer than 20 characters are truncated. Peppol BIS 3.0
  requires an EndpointID.
- A company in `company_state` unverified (-1) cannot send or receive
  (`Unauthorized`) until authorisation completes.
- Consumer e-invoicing in Finland (bank network) and the scanning pipeline can
  only be tested end to end in production.

Source: https://documentation.maventa.com/integration-guide/invoice-sending/invoice-sending.md

**Receiving**

- Register the company as a receiver first (VISMA Network, Peppol). A company
  registered at another Peppol Access Point must be deregistered there before
  Maventa can register it.
- Peppol profile registration is all-or-nothing: if any profile in the request
  is already registered, the whole request fails. Read
  `GET /v1/company/profiles` first and send only the missing ones. Ordering
  profiles need a profile version (`PEPPOLBIS30` or `EHF30`).
- Polling: list with `direction=RECEIVED` and a `received_at_start`/`_end`
  window that has a time zone offset, about a minute of overlap, and the
  stored timestamp advanced only after success. Poll at most once or twice a
  day, and once a day as a backup even with webhooks.
- When downloading in another format than the original, attachments are not
  embedded; fetch them from the files endpoint.
- Never retry `400` or `404` with the same input. Retry `429`, `500`, `503`
  and timeouts with exponential backoff.
- MLR (Message Level Response) is being replaced by MLS and retired in 2027:
  do not build on it or register new companies for it.

Sources: https://documentation.maventa.com/integration-guide/invoice-receiving.md,
https://documentation.maventa.com/integration-guide/peppol/peppol-network.md

**Webhooks**

- Delivery is at least once: deduplicate on `event`, `event_timestamp` and the
  document ID in `event_data`. Respond 2xx fast (Maventa waits 10 seconds) and
  do the work in the background.
- Failed deliveries are retried hourly for about 24 hours; a subscription
  that keeps failing for 30 days is deleted silently. Keep a polling fallback
  or subscribe to unacknowledged webhooks.
- Subscriptions are scoped to the company, not to a vendor or user.

Source: https://documentation.maventa.com/integration-guide/integration-tools/webhooks.md

**General**

- Handle service breaks gracefully; retry `503 service_unavailable` with
  backoff. Status: https://status.visma.com (Common Services, Maventa).
- Do not rely on IP allowlists: Maventa's IP addresses can change without
  notice.
- Lookup API: for Peppol Directory searches, use the `name` field for the name
  or business ID; `bid` does not work for Peppol lookups.

## Guardrails

- Develop and test against the testing environment (`-stage` hosts,
  testing.maventa.com) first. Do not send to production as a test: real
  invoices reach real recipients and are billed.
- Never ask the user to paste API keys, client secrets or tokens into the
  conversation, and never write them into code. Use environment variables or
  the project's secret store.
- This skill only reads Maventa's public documentation. It has no access to
  the user's Maventa account. For account-specific problems (a specific
  invoice, a locked company, production keys), point the user to Maventa
  support (support@maventa.com) or their integration contact.
- If the documentation does not answer the question, say so rather than
  guessing parameter names or behaviour.
