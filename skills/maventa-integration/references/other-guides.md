# Maventa documentation: Other guides

Index of standalone Maventa documentation pages outside the main sections: one line per page with its summary.
Fetch a page by its `.md` URL to read it; the summaries are not enough to answer from.

Snapshot from 2026-11-26. The live index is https://documentation.maventa.com/llms.txt: read it if a
URL here returns 404 or a page you expect is missing.

- [AutoScan](https://documentation.maventa.com/autoscan.md): Receive PDF invoices as e-invoices with AutoScan: suppliers email PDFs to a scan address and Smartscan extracts the data with VERIFIED checks. Compared with Scan Network.
- [Changes to consumer invoicing activation in Norway](https://documentation.maventa.com/b2cno-activation-changes.md): What changed in Norwegian consumer invoicing activation on 15.11.2026: eFaktura under Maventa's MPS agreement, no Visma Sign, and new REST and SOAP API responses.
- [Maventa Connector](https://documentation.maventa.com/connector.md): Download Maventa Connector, the Windows service that moves invoices between local folders and Maventa, and upgrade to version 2.1: requirements, changes and FAQ.
- [Kivra moves to OmaPosti](https://documentation.maventa.com/kivra-to-omaposti.md): Update your integration for the move from Kivra to OmaPosti in Finland: renamed digital post parameters, new delivery method values and how to let invoices reach OmaPosti.
- [Maventa Peppol API](https://documentation.maventa.com/peppol-api.md): Integrate with Maventa as your Peppol Access Point step by step: partner access, KYC, company registration, authentication, sending and receiving invoices, and webhooks.
  - Operations:
    - `POST /oauth2/token`: OAuth2 token endpoint
    - `GET /oauth2/current`: Fetch information about the authenticated user and company
    - `POST /v1/users`: Create a User
    - `GET /v1/invoices`: List invoices
    - `POST /v1/invoices`: Upload new invoice
    - `GET /v1/invoices/{id}`: Invoice details
    - `GET /v1/invoices/{id}/files/{file_id}`: Fetch file content
    - `PUT /v1/invoices/{id}/reroute/einvoice`: Reroutes invoice via einvoice
    - `PUT /v1/invoices/{id}/reroute/email`: Reroutes invoice via email
    - `PUT /v1/invoices/{id}/reroute/print`: Reroutes invoice via print
    - `GET /v1/companies`: List active companies the user has access to
    - `POST /v1/companies`: Create a Company
    - `GET /v1/company/profiles`: List network registrations
    - `POST /v1/company/profiles`: Create network registration request
    - `GET /v1/company/settings`: Fetch company settings
    - `PATCH /v1/company/settings`: Modify company settings
    - `GET /v1/company/notifications`: List notification subscriptions
    - `POST /v1/company/notifications`: Create new notification subscription
    - `GET /v1/company/authorization`: Company authorization status.
    - `POST /v1/company/authorization`: Authorize your company.
    - `POST /v1/company/notifications_resend_unacknowledged`: [EXPERIMENTAL] Resend unacknowledged notifications
    - `GET /v1/lookup/receivers`: Lookup for B2B document receivers
- [Peppol Self-Billing](https://documentation.maventa.com/peppol-self-billing.md): Send and receive Peppol BIS Self-Billing 3.0 invoices and credit notes through Maventa: the required XML identifiers, self-billing profile registration and country support.
- [Perintäpalvelut — asiakasohje](https://documentation.maventa.com/receivables-customer-guide-fi.md): Finnish-language customer guide to Visma Amili receivables services in Maventa: activating Amili Kassavirta and Amili Perintä, assignments, reports and FAQ.
