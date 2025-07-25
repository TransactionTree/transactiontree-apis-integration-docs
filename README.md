# Documentation Overview

Welcome to the **TransactionTree API & Data‑Feeds** documentation. This directory contains all of our reference materials, specifications, and examples for both REST APIs and file‑based data exchanges over SFTP.

---

## 📖 Purpose

* Provide a **single source of truth** for:

  * RESTful API definitions (OpenAPI/Swagger)
  * incoming & outgoing file‑feed specifications (CSV, ZIP, SQL)
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
│     ├── incoming.md    ← incoming feeds (audit, customers, POS events…)  
│     └── outgoing.md   ← outgoing feeds (audit, coupons, reports…)  
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

  * `incoming.md` – Specs for files we receive from partners
  * `outgoing.md` – Specs for files we send back to partners
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

* **Root README:** [`README.md`](README.md)
* **Postman Collection:** [`postman/TransactionTree.postman_collection.json`](postman/TransactionTree.postman_collection.json)
* **Live Developer Portal:** [https://esupport.transactiontree.com/](https://esupport.transactiontree.com/)
* **Support Contacts:**

  * Data‑Ops: [data‑ops@transactiontree.com](mailto:data-ops@transactiontree.com)
  * SFTP Helpdesk: [support@transactiontree.com](mailto:support@transactiontree.com)

---

## 🛠️ Contributing & Updates

* Make changes via **Pull Requests** against `main`.
* Use our **Issue** and **PR templates** under `.github/`.
* Upon merge, GitHub Actions will **rebuild and deploy** the updated docs.

---

Thank you for choosing TransactionTree! We’re here to help—reach out anytime with questions or feedback.
