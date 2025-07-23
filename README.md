# Documentation Overview

Welcome to the **TransactionTree API & Data‑Feeds** documentation. This directory contains all of our reference materials, specifications, and examples for both REST APIs and file‑based data exchanges over SFTP.

---

## 📖 Purpose

* Provide a **single source of truth** for:

  * RESTful API definitions (OpenAPI/Swagger)
  * Inbound & outbound file‑feed specifications (CSV, ZIP, SQL)
  * Connection details, naming conventions, directory layouts
  * Sample payloads, Postman collections, and cURL scripts
* Streamline partner onboarding and developer self‑service
* Maintain **version control** and easy updates via Git

---

## 📂 Directory Structure

```
docs/
├── overview.md         ← This landing page: context & navigation  
├── sftp-guide.md       ← Complete SFTP User Guide (hosts, dirs, naming)  
├── feed-specs/
│     ├── inbound.md    ← Inbound feeds (audit, customers, POS events…)  
│     └── outbound.md   ← Outbound feeds (audit, coupons, reports…)  
└── reference/          ← Auto‑generated API reference (Markdown)  
      ├── authentication.md  
      ├── stores.md  
      └── …  
```

* **overview\.md**
  You’re here! Explains what lives in each file and how to navigate.
* **sftp-guide.md**
  Detailed SFTP connection info, directory usage, file‑naming patterns, delimiters.
* **feed-specs/**

  * `inbound.md` – Specs for files we receive from partners
  * `outbound.md` – Specs for files we send back to partners
* **reference/**
  Markdown docs generated from our OpenAPI spec, one file per endpoint group.

---

## 🚀 How to Navigate

1. **Read `overview.md`** to understand the layout and key sections.
2. **Open `sftp-guide.md`** before attempting any SFTP transfers:

   * Hostnames, ports, credentials
   * `/incoming` vs. `/outgoing` directories
   * Filename conventions, timestamp formats, delimiters
3. **Choose your feed** under `feed-specs/`:

   * Review directory path (e.g. `/incoming/customers`)
   * Confirm filename pattern, extension, and delimiter
   * See sample files or snippets
4. **Browse `reference/`** for REST API details:

   * Authentication flows
   * Endpoint parameters & schemas
   * Request/response examples (cURL, Postman)

---

## 🔗 Related Resources

* **Root README:** [`../README.md`](../README.md)
* **Postman Collection:** [`../examples/postman/TransactionTree.postman_collection.json`](../examples/postman/TransactionTree.postman_collection.json)
* **Live Developer Portal:** [https://developers.transactiontree.com/](https://developers.transactiontree.com/)
* **Support Contacts:**

  * Data‑Ops: data‑[ops@transactiontree.com](mailto:ops@transactiontree.com)
  * SFTP Helpdesk: [support@transactiontree.com](mailto:support@transactiontree.com)

---

## 🛠️ Contributing & Updates

* Make changes via **Pull Requests** against `main`.
* Use our **Issue** and **PR templates** under `.github/`.
* Upon merge, GitHub Actions will **rebuild and deploy** the updated docs.

---

Thank you for choosing TransactionTree! We’re here to help—reach out anytime with questions or feedback.
