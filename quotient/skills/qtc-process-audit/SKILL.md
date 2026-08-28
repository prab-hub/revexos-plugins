---
name: qtc-process-audit
description: >
  This skill should be used when the user asks to "audit our quote-to-cash process",
  "assess our billing or invoicing setup", "do a quote-to-cash health check", "where are
  we losing time or money between sales and getting paid", "find automation
  opportunities in our sales-to-billing process", or wants a diagnostic assessment of a
  B2B service or SaaS company's current quoting, contracting, billing, collections, or
  revenue recognition process before deciding what to fix or automate.
metadata:
  version: "0.1.0"
---

# Quote-to-Cash Process Audit

Diagnose a company's current-state quote-to-cash process, score its maturity stage by
stage, and produce a prioritized automation roadmap. This skill is often the entry point
before using the other four skills in this plugin - use it when the user doesn't yet
know where their biggest QTC problem is. Read `references/audit-questionnaire.md` for
the full interview questions, maturity rubric, and industry-specific leakage patterns.

## Step 1: Gather current-state information

Work through the five QTC stages (lead-to-quote, quote-to-contract,
contract-to-provisioning, billing-to-invoice, collections-to-revrec) using the
questionnaire in `references/audit-questionnaire.md`. Prefer asking a focused set of
questions over an exhaustive interrogation - pull from any documents, spreadsheets, or
system exports the user shares rather than re-asking for information already given. If
this is an interactive session, ask questions in small batches per stage rather than all
at once.

## Step 2: Score maturity per stage

For each of the five stages, assign a maturity level using this rubric:

| Level | Label | Signal |
|---|---|---|
| 1 | Ad hoc / manual | Spreadsheets, email, no consistent template or system of record |
| 2 | Standardized but manual | Consistent templates/process, but still manually executed each time |
| 3 | Partially automated | Some steps automated (e.g., recurring invoices auto-generate) but with manual gaps or reconciliation |
| 4 | Fully automated & integrated | End-to-end automation with systems talking to each other and minimal manual intervention |

State the level and the specific evidence for it (e.g., "Level 1 on quoting - quotes are
built ad hoc in Google Docs with no discount approval trail") rather than a bare number.

## Step 3: Identify leakage and bottlenecks

Cross-reference the current state against the leakage pattern library in
`references/audit-questionnaire.md`, which is organized by company type (accounting
firm, marketing agency, dev/software agency, B2B SaaS). Typical high-value findings
include: unbilled scope creep, no discount governance trail, manual proration errors,
no dunning process (cash sitting uncollected), revenue recognized on a cash basis when
it shouldn't be, and provisioning delays that push out the billing start date without
anyone tracking it.

## Step 4: Prioritize the roadmap

Rank findings by impact × effort, not just severity:

- **High impact, low effort**: do first (e.g., adding a discount approval line to
  quotes, setting up a basic dunning cadence).
- **High impact, high effort**: plan next (e.g., migrating from spreadsheet billing to
  a proper subscription billing system).
- **Low impact**: deprioritize regardless of how easy it is; don't let quick wins
  crowd out addressing the actual biggest leak.

For each top finding, name which skill in this plugin addresses it directly
(`qtc-quote-builder`, `qtc-contract-handoff`, `qtc-billing-setup`, or
`qtc-collections-revrec`) so the user has a clear next step.

## Step 5: Produce the audit output

Structure the deliverable as:

1. Executive summary (1 paragraph): overall QTC maturity and the single biggest leak.
2. Maturity scorecard across the five stages (table).
3. Top 5 findings, each with the leakage/bottleneck, estimated impact, and recommended
   fix.
4. Prioritized roadmap (impact × effort).
5. Recommended next skill/action to start with.

Use the docx or pptx skill to format this as a polished deliverable if the user wants a
shareable document or a discovery-call presentation - this skill defines the content and
structure, not the file formatting.

## Note on using this as a sales/discovery tool

If the user is running this audit on behalf of a prospect or client (rather than their
own company), keep the tone diagnostic and specific rather than a generic sales pitch -
credibility comes from precise, evidenced findings, not from over-selling the other
skills in this plugin.

## Common mistakes to avoid

- Scoring maturity without citing the specific evidence behind the score.
- Producing a long list of findings with no prioritization.
- Treating every finding as equally urgent regardless of dollar impact.
- Skipping the "which skill/tool fixes this" mapping, leaving the user without a next
  step.
