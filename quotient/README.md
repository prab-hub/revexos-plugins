# Quotient: Quote-to-Cash Automation Toolkit

Quotient is a Cowork/Claude Code plugin that helps B2B digital service companies
(accounting, marketing, dev/software agencies) and B2B SaaS businesses run their
quote-to-cash cycle, from pricing a deal through getting paid and recognizing the
revenue, with less manual, ad hoc work.

## Overview

Quote-to-cash spans five stages: quoting/pricing, contracting/order setup, provisioning,
billing/invoicing, and collections/revenue recognition. Most B2B service and SaaS
companies handle this with a patchwork of spreadsheets, email, and disconnected tools,
which is where discounts go untracked, invoices go out wrong, and revenue gets
mis-recognized. Quotient packages the domain knowledge for each stage into a skill Claude
can apply directly.

## Components

Five skills, each triggered by natural request phrases (see each skill's description for
exact triggers):

| Skill | Purpose |
|---|---|
| `qtc-quote-builder` | Build B2B service and SaaS quotes/proposals with proper packaging, pricing models, and discount governance |
| `qtc-contract-handoff` | Turn an accepted quote into a reconciled order, contract package, and owned provisioning checklist |
| `qtc-billing-setup` | Configure recurring/usage-based billing, generate invoices, and handle proration on plan changes |
| `qtc-collections-revrec` | Build dunning/AR follow-up sequences and construct ASC 606/IFRS 15-aligned revenue recognition schedules |
| `qtc-process-audit` | Diagnose a company's current quote-to-cash maturity stage by stage and produce a prioritized automation roadmap (a good starting point or discovery-call tool) |

No agents, hooks, or MCP servers are bundled directly: this keeps the plugin usable
by any company regardless of which CRM, accounting, payments, e-signature, project
tracker, or automation tool they run.

## Setup

No required environment variables or configuration. If the company has MCP connectors
for their CRM, accounting, payments, e-signature, project tracker, or workflow
automation tool, the skills will reference them where relevant; see `CONNECTORS.md` for
the full mapping of tool categories to skills. Without any connectors, every skill still
produces a complete structured output (a quote, an order/checklist, an invoice, a dunning
sequence, or an audit report) as a document.

## Usage

Just describe the task in plain language and the relevant skill will trigger, for
example:

- "Build a quote for a $4k/month marketing retainer, annual prepay."
- "This SaaS deal just closed. Set up the order and provisioning checklist."
- "Generate this month's invoices for our retainer clients."
- "This customer is 45 days overdue: what's the next step?"
- "Set up a revenue recognition schedule for a $50k annual contract with a $10k
  implementation fee."
- "Audit our quote-to-cash process: where are we leaking money?"

Skills are typically used in this order for a new deal: `qtc-quote-builder` →
`qtc-contract-handoff` → `qtc-billing-setup` → `qtc-collections-revrec`.
`qtc-process-audit` can be used any time, and is a useful starting point when the company
doesn't yet know where their biggest quote-to-cash problem is.

## Customization

This plugin references external tools by category (`~~crm`, `~~accounting`, etc.)
rather than a specific vendor, so it works across different tool stacks. See
`CONNECTORS.md` for the full list of categories and common options. Use the plugin
customizer to bind these to a specific company's actual tools.
