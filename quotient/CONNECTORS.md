# Connectors

## How tool references work

Skill files in this plugin use `~~category` as a placeholder for whatever tool the
company connects in that category (for example, `~~accounting` might mean Xero,
QuickBooks, or another accounting platform with an MCP connector). The skills are
tool-agnostic by design: they describe the quote-to-cash workflow in terms of
categories rather than one specific vendor, so the plugin works whether a company runs
Xero or QuickBooks, HubSpot or Salesforce, Stripe or another payment processor.

When a placeholder is mentioned, it means "if a connector for this category is
available, use it; otherwise, produce the same output as a document/checklist and note
that connecting a tool in this category would let it happen automatically."

## Connectors for this plugin

| Category | Placeholder | Common options | Used by |
|---|---|---|---|
| CRM | `~~crm` | HubSpot, Salesforce, Pipedrive | qtc-quote-builder, qtc-contract-handoff, qtc-collections-revrec |
| Accounting | `~~accounting` | Xero, QuickBooks | qtc-quote-builder, qtc-billing-setup, qtc-collections-revrec |
| Payments | `~~payments` | Stripe, Paddle, Braintree | qtc-billing-setup, qtc-collections-revrec |
| E-signature | `~~e-signature` | DocuSign, PandaDoc, HelloSign | qtc-contract-handoff |
| Project tracker | `~~project tracker` | Asana, Linear, Jira, Monday | qtc-contract-handoff, qtc-collections-revrec |
| Workflow automation | `~~workflow automation` | n8n, Make, Zapier | qtc-billing-setup |
| Chat/notifications | `~~chat` | Slack, Microsoft Teams | qtc-collections-revrec |

None of these connectors are required for the skills to be useful: every skill produces
a complete, structured output (a quote, an order/checklist, an invoice, a dunning
sequence, an audit report) on its own. Connecting tools in these categories lets the
output be pushed directly into the company's systems instead of handled as a document.
