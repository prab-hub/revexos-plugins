---
name: qtc-collections-revrec
description: >
  This skill should be used when the user asks "the customer hasn't paid", "set up a
  dunning sequence", "build an AR follow-up flow", "reconcile payments to invoices",
  "set up revenue recognition", "how do I recognize revenue for this contract", "build a
  deferred revenue schedule", or needs help with collections, accounts receivable
  follow-up, or ASC 606/IFRS 15-aligned revenue recognition for a B2B service or SaaS
  contract.
metadata:
  version: "0.1.0"
---

# Collections & Revenue Recognition

Cover the back half of quote-to-cash: getting paid on time, reconciling payments, and
recognizing revenue correctly once cash and contracts diverge (which they almost always
do). Read `references/asc606-revrec-primer.md` before building a revenue recognition
schedule — do not improvise the accounting treatment.

## Part A — Collections & AR follow-up

### Step 1: Design the dunning cadence

Build an explicit, staged cadence rather than a single "send a reminder" step:

| Stage | Timing | Action |
|---|---|---|
| Pre-due reminder | 3–5 days before due date | Friendly email reminder |
| Due date | Day 0 | Payment attempt (if on autopay/card) or invoice reminder |
| First follow-up | Day +3–5 | Email + payment retry if card-based |
| Second follow-up | Day +14 | Email + task to account owner/CSM for a personal check-in |
| Escalation | Day +30 | Finance/collections involvement; consider service restriction per contract terms |
| Final notice | Day +60–90 | Formal notice per contract; evaluate write-off or legal escalation path |

State which stage a given overdue invoice is at and the next action, rather than treating
every overdue invoice the same way. Adjust timing to the customer's specific payment
terms and any negotiated grace period from the order.

### Step 2: AR aging and prioritization

Bucket outstanding invoices by age (0–30, 31–60, 61–90, 90+ days) and prioritize
follow-up by a combination of age and dollar amount — a large 31-day invoice usually
warrants attention before a small 60-day one. If a CRM connector (~~crm) is available,
note that aging invoices should generate tasks for the account owner, not just sit in a
finance report no one else sees.

### Step 3: Payment reconciliation

- Match payments from a payments connector (~~payments) against open invoices in the
  accounting system (~~accounting) by amount and reference/invoice number.
- Handle partial payments explicitly: state whether the remaining balance stays open on
  the same invoice or generates a new one, per the user's process.
- Flag unmatched payments (wrong amount, missing reference) for manual review rather than
  guessing which invoice they apply to.

### Step 4: Service impact of non-payment

State, based on the contract, what happens if an invoice goes unpaid past the escalation
threshold — service suspension, feature restriction, or continued service with
collections handled separately. Never assume suspension is automatic; confirm it's in the
contract terms surfaced during `qtc-contract-handoff`.

## Part B — Revenue recognition

### Step 1: Determine the recognition pattern

Using the ASC 606 / IFRS 15 five-step framework detailed in
`references/asc606-revrec-primer.md`, classify each contract's performance obligations:

- **Point-in-time**: recognized when a deliverable is completed/accepted (e.g., a fixed
  project milestone).
- **Over-time, ratable**: recognized evenly across the contract term (the standard
  treatment for SaaS subscriptions).
- **Over-time, percentage-of-completion**: recognized as work progresses, based on
  effort or cost incurred relative to total estimated effort/cost (common for larger
  services engagements).

### Step 2: Handle multi-element arrangements

For hybrid deals (one-time implementation fee + recurring subscription, or a bundled
service + software deal), do not recognize the one-time fee entirely on receipt if it
represents setup work with no standalone value to the customer — in many cases it should
be recognized over the expected customer relationship period alongside the subscription.
Flag this as a judgment call requiring the user's accountant/auditor's sign-off; this
skill provides the standard framework, not a substitute for professional accounting
judgment on a specific contract.

### Step 3: Build the deferred revenue schedule

For any contract billed in advance of the period it covers (annual prepay SaaS, retainer
paid upfront), construct a month-by-month recognition schedule so billed cash and
recognized revenue are tracked separately. See the worked example in
`references/asc606-revrec-primer.md`.

### Step 4: Handle contract changes

- **Upgrades/downgrades mid-term**: adjust the remaining recognition schedule
  prospectively from the change date, not retroactively, unless the change qualifies as a
  contract modification requiring a full re-assessment (flag this distinction rather than
  picking one silently).
- **Early termination**: stop recognizing future periods as of the termination date, and
  flag any deferred revenue that must be reversed or any earned-but-unbilled revenue that
  must be recognized.

## Common mistakes to avoid

- Treating every overdue invoice identically regardless of age or amount.
- Guessing which invoice an unmatched payment applies to instead of flagging it.
- Recognizing a bundled one-time fee entirely upfront without checking whether it has
  standalone value.
- Recognizing annual-prepay revenue as a lump sum instead of ratably over the term.
- Making a revenue recognition call without noting it should be confirmed with the
  user's accountant, especially for judgment-heavy cases (modifications, bundling).
