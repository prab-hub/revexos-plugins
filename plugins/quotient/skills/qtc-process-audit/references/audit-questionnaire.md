# QTC Audit Questionnaire & Leakage Pattern Library

Detailed interview questions and industry leakage patterns backing the
`qtc-process-audit` skill.

## Interview questionnaire by stage

### Stage 1 — Lead-to-quote

- How are quotes/proposals currently built (tool, template, who owns it)?
- Is there a defined discount approval process, and is it actually followed?
- How long does it typically take from "verbal agreement" to a quote in the customer's
  hands?
- Are pricing/packaging decisions consistent across reps, or ad hoc per deal?

### Stage 2 — Quote-to-contract

- What happens between "quote accepted" and "contract signed"? Is there a defined order
  form / SOW template?
- Is there a reconciliation check between what was quoted and what's in the contract?
- How is the contract routed for signature — manually emailed, or via an e-signature
  tool?
- Are renewal/auto-renewal terms tracked anywhere visible before they trigger?

### Stage 3 — Contract-to-provisioning

- Once signed, how does the delivery/ops/product team learn the deal closed?
- Is there a checklist for what needs to be provisioned, and is it owned/dated?
- How often does billing start before the customer is actually live (or vice versa)?

### Stage 4 — Billing-to-invoice

- Is billing generated manually each cycle, or automated?
- How are subscription changes (upgrades/downgrades, seat changes) reflected in
  billing — immediately, at next cycle, manually calculated?
- Is there a single system of record for invoices, or are they scattered across email/
  spreadsheets/multiple tools?
- How is usage-based billing (if any) metered and verified before invoicing?

### Stage 5 — Collections-to-revrec

- Is there a defined dunning/follow-up cadence for overdue invoices, or is it reactive?
- Who owns AR follow-up, and how much is currently outstanding by aging bucket?
- How is revenue currently recognized — cash basis, or accrual with a defined
  methodology?
- Are deferred revenue and unbilled revenue tracked, or only cash collected?

## Leakage pattern library by company type

### Accounting/bookkeeping firms

- Scope creep on "full-service" engagements billed at a flat retainer with no
  overage mechanism.
- Advisory hours performed but not tracked/billed separately from the core retainer.
- Manual, error-prone reconciliation between practice management software and the
  accounting system used for the firm's own billing.

### Marketing agencies

- Media spend markup inconsistently applied or not reconciled against actual ad
  platform spend.
- Scope creep on "unlimited revisions" or loosely defined retainer bands.
- Value-based/outcome fees with no reliable measurement of the outcome, causing disputes
  at invoicing time.

### Dev/software agencies

- T&M engagements with no not-to-exceed cap, causing customer pushback at invoicing.
- Fixed-fee projects with no change-order process, absorbing scope creep as unbilled
  effort.
- Milestone invoicing triggered by internal "done" rather than customer acceptance,
  causing payment disputes.

### B2B SaaS

- Manual proration calculations prone to error on upgrades/downgrades.
- Usage-based revenue leakage from incomplete or delayed metering data.
- No structured dunning process, leaving involuntary churn (failed payments) unaddressed
  until a customer complains about losing access.
- Revenue recognized as cash received rather than ratably, distorting reported metrics
  (especially ARR/MRR accuracy).

## Impact × effort scoring guide

When prioritizing findings, estimate both dimensions on a simple scale rather than a
false-precision score:

| | Low effort | High effort |
|---|---|---|
| **High impact** | Do first | Plan and resource next |
| **Low impact** | Fine to do opportunistically | Deprioritize |

Impact should be estimated in concrete terms where possible — dollars of leakage per
year, hours of manual work per month, or days of cash-collection delay — rather than a
vague "high/medium/low" with no basis.
