# Maventa documentation: Integration Guide

Index of the Integration Guide section of the Maventa documentation: one line per page with its summary.
Fetch a page by its `.md` URL to read it; the summaries are not enough to answer from.

Snapshot from 2026-11-26. The live index is https://documentation.maventa.com/llms.txt: read it if a
URL here returns 404 or a page you expect is missing.

## Integration Guide

- [Getting Started](https://documentation.maventa.com/integration-guide/getting-started.md): Plan a Maventa integration: compare the REST and SOAP APIs, choose integration scope and level, get testing and production API keys, and see how the test environment works.

## Invoice sending

- [Invoice sending](https://documentation.maventa.com/integration-guide/invoice-sending/invoice-sending.md): Send invoices with the Maventa REST API: prepare Peppol BIS 3.0 or other invoice XML, look up recipients, add attachments, control routing and track delivery with webhooks or polling.
- [Consumer Invoicing](https://documentation.maventa.com/integration-guide/invoice-sending/consumer-invoicing.md): Send B2C invoices to consumers in Finland, Sweden and Norway through netbanks, digital mailboxes such as OmaPosti and Kivra, direct debit, email and print.
  - [Consumer Invoicing (Finland)](https://documentation.maventa.com/integration-guide/invoice-sending/consumer-invoicing/fi.md): Send invoices to Finnish consumers as netbank e-invoices, direct payments (suoramaksu) or to the OmaPosti digital mailbox, including SI and RI messages, routing and testing.
  - [Consumer Invoicing (Norway)](https://documentation.maventa.com/integration-guide/invoice-sending/consumer-invoicing/no.md): Send invoices to Norwegian consumers as eFaktura to netbanks and Vipps, AvtaleGiro direct debit or Digital Postkasse Innbygger, including activation, JTTA lookup and route order.
  - [Consumer Invoicing (Sweden)](https://documentation.maventa.com/integration-guide/invoice-sending/consumer-invoicing/se.md): Send invoices to Swedish consumers as netbank e-invoices or to Kivra and Billo through InConx, including activation, consumer onboarding, bank account selection and routing.
- [Printing](https://documentation.maventa.com/integration-guide/invoice-sending/printing.md): Deliver invoices as printed letters with the Maventa print service: activate it, force the print route, meet the PDF template rules, and handle attachments and errors.
  - [Printing (Germany)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/de.md): Print rules for German senders: invoices are produced at the Finnish facility, with template and colour options, attachment limits, C6, C5 and C4 envelopes and delivery schedules.
  - [Printing (Denmark)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/dk.md): Print rules for Danish senders: invoices are produced and mailed from Norway under Norwegian rules, covering template, colour, attachments, C5 and C4 envelopes and delivery.
  - [Printing (Finland)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/fi.md): Print rules for Finnish senders: template and cover sheet options, colour, attachments, envelope sizes, Priority and Economy letter classes, OmaPosti and the e-instruction page.
  - [Printing (Netherlands)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/nl.md): Print rules for Dutch senders: your own invoice image with an automatic cover sheet, colour printing by default, attachments enabled by default and same-day mail handover.
  - [Printing (Norway)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/no.md): Print rules for Norwegian senders: template and layout rules, colour option, attachments, C5 and C4 envelope sizes, delivery schedules and automatic return post handling.
  - [Printing (Other countries)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/other.md): Print rules for countries without a local print facility, such as Estonia, Belgium, Iceland and Poland: invoices are printed and mailed from Finland under Finnish rules.
  - [Printing (Sweden)](https://documentation.maventa.com/integration-guide/invoice-sending/printing/se.md): Print rules for Swedish senders: template and layout rules, colour option, attachments, C5 and C4 envelope sizes, and Economy (B-post) or Priority (A-post) delivery.
- [Email invoicing](https://documentation.maventa.com/integration-guide/invoice-sending/email-invoicing.md): Send invoices by email through Maventa: force the email route, choose download links or PDF attachments, add a header image and payment links, set the language and track delivery.

## Invoice receiving

- [Invoice receiving](https://documentation.maventa.com/integration-guide/invoice-receiving.md): Receive invoices through Maventa: activate receiving in VISMA Network and Peppol, fetch invoices with webhooks or polling, download images and attachments, and handle API errors.
- [Scanning](https://documentation.maventa.com/integration-guide/invoice-receiving/scanning.md): Turn paper and PDF invoices into e-invoices with AutoScan, Scan Network, Visma Scanner or DocScan: compare features by country, open the service and use supplier activation.
- [Detect](https://documentation.maventa.com/integration-guide/invoice-receiving/detect.md): Check incoming invoices for fraud and errors with Detect: VAT, BID (FI, NO, NL), warning list, supplier activation and bank account change checks, and how to activate them and show results.
- [Fraud reporting](https://documentation.maventa.com/integration-guide/invoice-receiving/fraud-reporting.md): Let users report suspected fraudulent invoices through the AutoXChange API, then view or delete reports. Reported senders can end up on the Detect warning list.

## Integration tools

- [Webhooks](https://documentation.maventa.com/integration-guide/integration-tools/webhooks.md): Get real-time Maventa event notifications with webhooks: register for one company or all vendor companies, handle payloads, secure the endpoint and review the event types.
- [Reference implementations](https://documentation.maventa.com/integration-guide/integration-tools/reference-implementations.md): Start a Maventa REST API integration from the Java and C# reference implementations, covering authentication, account creation, invoice sending and receiving, and webhooks.
- [AI agent skill](https://documentation.maventa.com/integration-guide/integration-tools/ai-agent-skill.md): Install the Maventa integration skill in Claude Code, Codex, Cursor, Copilot or claude.ai so your AI coding agent answers from the current Maventa documentation.
- [Maventa Connector](https://documentation.maventa.com/integration-guide/integration-tools/maventa-connector.md): Download and upgrade Maventa Connector, the Windows service that moves e-documents between Maventa and local folders for ERP systems without a direct API integration.
- [Embeddable User Interface](https://documentation.maventa.com/integration-guide/integration-tools/embeddable-user-interface.md): Embed the Maventa user interface (EUI) in your ERP with a script or iframe: fetch access tokens, pick views with setup parameters and direct URLs, and handle unverified companies.

## Peppol

- [Peppol Network](https://documentation.maventa.com/integration-guide/peppol/peppol-network.md): Send and receive invoices over the Peppol network with Maventa as your Access Point: Peppol addresses, recipient lookup, receiver registration, supported countries and MLS.
- [Document Exchange](https://documentation.maventa.com/integration-guide/peppol/document-exchange.md): Exchange Peppol orders, order responses, catalogues, despatch advice and other business documents through the Maventa Documents API, including statuses, events and registration.
- [Invoice Response](https://documentation.maventa.com/integration-guide/peppol/invoice-response.md): Send and receive Peppol BIS Invoice Response messages through Maventa to tell the seller an invoice was approved, rejected, queried or paid, with setup steps and response codes.
- [Self-billing support](https://documentation.maventa.com/integration-guide/peppol/self-billing-support.md): Send and receive Peppol BIS Self-Billing 3.0 invoices and credit notes through Maventa: the required XML identifiers, self-billing profile registration and country support.

## Invoicing formats

- [Invoicing formats](https://documentation.maventa.com/integration-guide/invoicing-formats/invoicing-formats.md): See which XML invoice formats Maventa supports and converts between, with recommendations for Peppol BIS 3.0, Finvoice 3.0 and TEAPPSXML, example files and EN16931 compliance.
- [Validation](https://documentation.maventa.com/integration-guide/invoicing-formats/validation.md): Find out how Maventa validates outgoing invoices against minimum content rules, Peppol and EN16931 schematrons and bank network requirements, and how to avoid validation errors.
- [Peppol BIS 3.0](https://documentation.maventa.com/integration-guide/invoicing-formats/peppolbis30.md): Build valid Peppol BIS Billing 3.0 invoices and credit notes in UBL 2.1: document identifiers, parties, tax totals, invoice lines, allowances and charges, attachments and code lists.
- [Finvoice 3.0](https://documentation.maventa.com/integration-guide/invoicing-formats/finvoice.md): Build valid Finvoice 3.0 invoices for Maventa: supported versions, EN16931 validation, row discounts and charges, credit notes, reminder invoices and recipient complementation.
- [Document types and type codes](https://documentation.maventa.com/integration-guide/invoicing-formats/document-types.md): Look up invoice type codes for Finvoice, TEAPPS, Peppol BIS 3.0, OIOUBL and SI-UBL, and see how Maventa preserves document subtypes when converting between formats.

## Account management

- [Companies and Settings](https://documentation.maventa.com/integration-guide/account-management/companies-and-settings.md): Open, configure and authenticate Maventa company accounts through the API or UI, with supported identifiers per country, Visma Sign authentication, partner accounts and data retention.
- [Department Company](https://documentation.maventa.com/integration-guide/account-management/department-company.md): Register locations or subsidiaries as Maventa Department Companies, each with its own GLN address and inbox under one parent company, including Peppol registration and limitations.
- [Users](https://documentation.maventa.com/integration-guide/account-management/users.md): Create and manage Maventa users and API users, assign user or admin roles, configure user settings and understand the automatic deletion policy for inactive accounts.
- [Billing](https://documentation.maventa.com/integration-guide/account-management/billing.md): Understand how Maventa bills partners per transaction based on the vendor API key, read the monthly transaction report and fetch billed counts with the Billing API v2.

## Accounts receivable

- [Accounts receivable](https://documentation.maventa.com/integration-guide/accounts-receivable.md): Compare Maventa accounts receivable services for payment monitoring, reminders and debt collection: Ropo, Amili Kassavirta and Amili Perintä, with the shared Receivables API flow.
- [Ropo's reminder and collection service](https://documentation.maventa.com/integration-guide/accounts-receivable/ropo-debt-collection.md): Transfer overdue invoices to Ropo for reminders and debt collection in Finland, Sweden and Norway through Maventa: activation, assignments, events and the collection schedule.
- [Amili Kassavirta](https://documentation.maventa.com/integration-guide/accounts-receivable/amili-kassavirta.md): Route all invoices of a Finnish company through Amili Kassavirta for payment monitoring, reminders and debt collection by Visma Amili: activation, service levels, assignments and events.
- [Amili Perintä](https://documentation.maventa.com/integration-guide/accounts-receivable/amili-perinta.md): Hand selected overdue invoices of Finnish companies to Visma Amili for reminders and debt collection with Amili Perintä: KYC activation, transfers, assignments and events.
- [Receivables webhooks](https://documentation.maventa.com/integration-guide/accounts-receivable/webhooks.md): Receive webhooks when a payment, credit note, reminder or collection stage change happens on a receivables assignment, with event types, payload, authentication and retries.
