# Awesome-Sales-Tax-Compliance

## Top Sales Tax Compliance Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Tax Calculation Engines, Nexus Determination & Self-Hosted Compliance Infrastructure*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Sales Tax Compliance**. These tools enable merchants and software platforms to calculate sales tax, VAT, and GST accurately across jurisdictions, determine economic nexus obligations, and manage exemption certificates—reducing audit risk while supporting global commerce.



**Examples** include Shopify Tax, Avalara AvaTax, Vertex Cloud, TaxJar, Anrok, Sovos, Thomson Reuters ONESOURCE, Stripe Tax, Zamp, and Quaderno (the category leaders).



**Open-source emphasis**: Sales Tax Compliance is a domain where open-source tooling is **emerging but still far from turnkey**. The strongest active project is **Cbox Tax** (cboxdk/laravel-tax), a self-hostable consumption-tax engine for Laravel that owns calculation logic per jurisdiction—place-of-supply, reverse-charge, nexus determination, and US taxability—while sourcing only rate data behind a pluggable contract . **nexus-tax** provides a framework-agnostic PHP engine with temporal rate resolution, hierarchical compound taxes, and an immutable audit log . However, **massive rate databases and filing automation** (Avalara, TaxJar) remain proprietary; no open-source project matches their jurisdiction coverage or remittance workflows.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Shopify Tax](https://help.shopify.com/en/manual/taxes/shopify-tax/choose-tax-service)**  

  Native tax service for Shopify merchants; free until $100K GMV per calendar year per store (thresholds vary by region: $100K USD for US, €100K for EU, £100K for UK, $100K CAD for Canada), then standard rates apply on eligible orders where you collect tax . Supports US, EU, UK, Canada, and other regions with dynamic tax-inclusive pricing in 17 additional countries as of March 2026 . Basic Tax is no longer available for new stores selling to Canada, UK, and EU as of May 13, 2026 .



- **[Avalara AvaTax](https://marketplace.microsoft.com/en-us/product/avalara.avatax-agentic-tax-and-compliance)**  

  Global tax engine delivering real-time sales tax, use tax, VAT, and GST calculations across the **US and 190+ countries**; a certified Streamlined Sales Tax (SST) CSP, with several US states licensing Avalara's technology for their own rate lookup tools . Supports VAT in 50+ countries/regions including Argentina, Australia, EU member states, India, Japan, Saudi Arabia, UAE, and UK . The most comprehensive commercial coverage available.



- **[Vertex Cloud](https://www.vertexinc.com/)**  

  Enterprise tax technology platform with sales and use tax, VAT, and compliance automation; integrates with major ERPs and ecommerce platforms.



- **[TaxJar](https://www.taxjar.com/)**  

  Sales tax automation platform (now part of Stripe) with real-time calculation APIs, rooftop-level rate lookups, transaction recording, and automated filing across US states and international jurisdictions .



- **[Anrok](https://www.anrok.com/)**  

  SaaS-focused global sales tax and VAT compliance platform with a REST API for real-time calculation, nexus registration management across 11,000+ US jurisdictions, and exemption certificate handling .



- **[Sovos](https://sovos.com/)**  

  Global tax compliance and regulatory reporting platform covering sales tax, VAT, and e-invoicing across 70+ countries.



- **[Thomson Reuters ONESOURCE](https://tax.thomsonreuters.com/)**  

  Enterprise tax determination and compliance suite with global coverage for sales tax, VAT, and indirect tax.



- **[Stripe Tax](https://stripe.com/tax)**  

  Tax calculation and collection integrated with Stripe payments; automates sales tax, VAT, and GST for businesses selling globally.



- **[Zamp](https://www.zamp.com/)**  

  Sales tax automation platform with AI-powered nexus monitoring, registration, calculation, and filing for growing businesses.



- **[Quaderno](https://quaderno.io/)**  

  Tax compliance platform for SaaS and digital products with real-time calculation, VAT validation, and automated filing; WooCommerce plugin available .



## Open-Source GitHub Projects



- **[Cbox Tax (cboxdk/laravel-tax)](https://github.com/cboxdk/laravel-tax)**  

  The most comprehensive open-source consumption-tax engine available for Laravel (PHP). Owns the **calculation logic per jurisdiction**—place-of-supply rules, reverse-charge determination, rate application, inclusive/exclusive pricing, and nexus gating—while sourcing only rate data behind a pluggable `TaxRateSource` contract . Covers **EU VAT** (Art. 44/45/58 place-of-supply, intra-EU B2B reverse charge, Art. 59c micro-business relief), **US sales tax** (nexus thresholds, 25-category taxability, intrastate sourcing for 9 states, address-exact for 30 states), **UK, Switzerland, Norway, Australia, New Zealand, Mexico, Singapore, Taiwan, UAE, Saudi Arabia, Bahrain, Oman, Turkey, Chile, Indonesia, Vietnam, Philippines, Japan, Korea, Thailand, Ukraine, India GST, Malaysia SST, and Canada GST/HST** . **Critical design principle**: a missing rate is **refused, never assumed 0%**—the engine omits jurisdictions where rate data cannot be verified rather than shipping a wrong charge . Multi-entity routing correctly taxes the same buyer differently based on which selling entity issues the invoice (German entity → reverse charge for French B2B; French entity → French VAT) . **This is the closest open-source equivalent to Avalara/TaxJar's calculation engine**, though it requires Laravel and does not handle filing/remittance.



- **[nexus-tax (azaharizaman)](https://github.com/azaharizaman/nexus-tax)**  

  Framework-agnostic PHP tax calculation engine with multi-jurisdiction support. Features **temporal rate resolution** (tax holidays modeled as 0% rates with date ranges), **hierarchical compound taxes** (federal → state → local sequential application), **reverse charge mechanism** for EU B2B cross-border transactions, **economic nexus determination**, **partial exemptions** with percentage-based taxable base reduction, and **immutable audit log** (no UPDATE/DELETE; corrections via contra-transaction with negative amounts) . Stateless calculation engine designed for Symfony/Laravel integration. **Strong for complex tax structures** but does not ship with built-in jurisdiction data—rates and rules must be supplied.



- **[OpenSalesTax](https://github.com/opensalestax)**  

  Open-source US sales tax calculation API with a PHP SDK and connectors for Saleor (TypeScript) and Drupal Commerce (PHP) . Self-hosted engine for destination-based US sales tax calculation; **calculation only**—merchant remits. The PHP SDK and ecommerce integrations make it practical for platforms wanting US tax calculation without SaaS dependency, though coverage is US-focused.



- **[node-sales-tax (valeriansaliou)](https://github.com/valeriansaliou/node-sales-tax)**  

  International sales tax calculator for Node.js (311 GitHub stars); **offline operation** with tax rates kept up-to-date, optional online VAT number fraud check . Provides a lightweight, dependency-free way to calculate VAT/GST for international sales without API calls—useful for digital products and SaaS billing.



- **[Python European VAT Rates](https://github.com/topics/sales-tax)**  

  Official-source European VAT rates for Python; daily-checked, typed, offline data for **45 jurisdictions** (last updated August 2026) . **Rate data only**—not a calculation engine, but provides the verified rate foundation that engines like nexus-tax or Cbox Tax require for EU coverage.



- **[US Tax Data Dataset](https://github.com/cboxdk/laravel-tax)**  

  The `us-tax-data` dataset bundled with Cbox Tax provides **all 51 US jurisdictions**: state rates, 25-category taxability rules, economic-nexus thresholds, and intrastate sourcing rules . This is the most complete open-source US sales tax data available, enabling address-exact calculation for 30 states and correct nexus gating.



### Additional Strong Open-Source Options



- **Saleor Tax App** — Open-source connector for Saleor ecommerce that uses the self-hosted OpenSalesTax engine for destination-based US sales tax calculation .

- **Drupal Commerce Tax Plugin** — Drupal Commerce 3.x tax type plugin for US sales tax via OpenSalesTax; calculation only, merchant remits .

- **Lemon Squeezy** — Merchant-of-record platform that handles global sales tax, VAT, and compliance on the seller's behalf; open-source components available but the compliance service is managed .



**Frameworks for building custom systems**: **Cbox Tax** provides the most complete open-source foundation for multi-jurisdiction tax calculation with US nexus, EU VAT, and 20+ national regimes . **nexus-tax** provides a framework-agnostic engine for complex tax structures requiring temporal rates and compound taxes . **OpenSalesTax** provides US-focused calculation with ecommerce connectors . **Python European VAT Rates** and the **us-tax-data dataset** provide verified rate foundations. No open-source project handles filing or remittance—organizations must integrate with filing services or manage compliance manually.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Sales tax compliance platforms must comply with applicable tax regulations in every jurisdiction of operation; **incorrect tax calculation can create significant legal and financial exposure**. Rate data and nexus rules change frequently—verify against primary sources.

- **Open-source sales tax compliance is emerging but incomplete**—Cbox Tax and nexus-tax provide strong calculation engines, but **filing, remittance, and jurisdiction registration** remain manual or require integration with commercial services. Avalara and TaxJar maintain proprietary rate databases and filing infrastructure that open-source cannot replicate. Organizations with complex multi-jurisdiction obligations should evaluate commercial platforms.

- Verify license terms for commercial use; Cbox Tax is open-source (Laravel package) , nexus-tax is open-source (PHP) , and OpenSalesTax is open-source (PHP/TypeScript) .



---



**Made for ecommerce operators, SaaS finance teams, tax engineers, and compliance architects.**  

Let's make sales tax compliance more open, but with clear eyes about the rate-data moats and filing complexity that remain.
