---
name: preparing-cpa-t1-package
description: "Assembles a personal tax handoff package for a Canadian with self-employment income and, where relevant, coordinates with a separate corporate package for an incorporated owner-manager's personal T1 filing. Guides the user through collecting the outputs of prior workflow steps, identifying missing items, and producing a cover summary the CPA can act on directly. Does not give tax advice, complete forms, or advise on filing positions. Trigger on: 'prepare for my CPA meeting', 'get my tax documents ready', 'what does my accountant need from me', 'organize everything for tax season', 'put together my tax package', 'what should I send my CPA', 'I have a meeting with my accountant'."
metadata:
  author: Alex Teplov
  version: 1.0.0
  category: tax-preparation
---

# Preparing CPA T1 Package

**Workflow position:** Consolidation skill in the selfemployed-skills personal tax sequence. Typically runs after `01-identifying-income-sources`, a profession-specific variant of `03-classifying-expenses` (for example, `03-classifying-expenses/it-contractors`), and `02-checking-gst-hst`, but can also run earlier to identify missing items before a CPA meeting. If the user is incorporated, note that a separate corporate package may also be needed, typically through `05-preparing-cpa-t2-package`. Together, the personal and corporate summaries help the CPA understand the personal and corporate sides of the owner-manager file.

**Core constraint:** This workflow organizes information the user provides. It does not guarantee completeness and may not detect items the user has omitted or described inaccurately. State this to the user before starting.

---

## Role

Do not give tax advice. When the user asks about deductibility, filing positions, or what they should claim, redirect the advisory part and continue the workflow. The goal is a well-organized package, not a filing position.

## Workflow

This skill operates in two modes:

**Consolidation mode:** The user has completed prior workflow steps. This skill assembles their outputs into a CPA-ready package.

**Fresh intake mode:** The user has not completed prior steps. This skill collects the same information directly and produces the package from scratch.

Ask which mode applies in Step 1. Steps 3, 4, and 5 handle both modes.

Copy this checklist at the start of each session:

```
Progress:
- [ ] Step 1: Open conversation and deliver data notice
- [ ] Step 2: Collect prior year context
- [ ] Step 3: Confirm income summary
- [ ] Step 4: Confirm expense summary
- [ ] Step 5: Confirm GST/HST status
- [ ] Step 6: Collect personal and other items
- [ ] Step 7: Identify gaps and flag questions
- [ ] Step 8: Produce cover summary
```

### Step 1: Open the Conversation

State before asking any questions:

1. This workflow assembles a CPA-ready package from the user's organized financial information.
2. "This process organizes what you provide and prompts for common items, but it may still miss information you have omitted or described inaccurately."
3. Deliver the data handling notice below.
4. Ask which tax year the package is for.
5. Ask whether they have completed the income, expense, and GST/HST workflow steps already, or whether they are starting fresh.
6. If they completed the expense step, ask which classifying-expenses variant they used. Current variants are in `03-classifying-expenses/` subfolders. If they do not know the folder name, ask what type of self-employment work they do and note the profession for the cover summary.

**Data handling notice. State before collecting any information:**

> Do not type your SIN, business number, or client names into this conversation. Amounts, document types, and general descriptions are all that are needed. If uploading documents, cover or black out your SIN before uploading. Avoid sharing sensitive business details you would not be comfortable storing in a third-party system. Your inputs and uploaded documents may be stored by this AI tool according to its policies. Review those policies before proceeding if you have concerns.

---

### Step 2: Collect Prior Year Context

Prior year information affects what the CPA needs to complete the return. Collect before moving to current year items.

Ask one question at a time:

- Do they have their prior year Notice of Assessment (NOA) from CRA? If yes, confirm the year it covers. If not, note as missing.
- Did they make instalment payments to CRA during the tax year? If yes, ask for total instalments paid. CRA My Account shows instalment history under "Payments."
- Do they carry forward Capital Cost Allowance (CCA) from prior years? This applies if they have depreciable assets: vehicle used for business, home office equipment claimed previously, tools. If yes, ask them to note which asset classes and the prior year UCC (Undepreciated Capital Cost) balance. If they do not know, flag for CPA.
- Did they carry forward a business loss from a prior year? If yes, flag for CPA, note the year and amount if known.
- Ask whether they have the RRSP deduction limit shown on their prior year NOA, and note the amount if available.

---

### Step 3: Confirm Income Summary

If the user completed `01-identifying-income-sources`, ask them to paste or summarize the output. Review it for completeness before accepting.

If starting fresh, collect:

- All T4A slips received (payer type, amount)
- All T4 slips if any employment income alongside self-employment
- Invoiced income where no T4A was issued, total by client type
- Platform or marketplace income, and income received through payment processors or online platforms (Upwork, Fiverr, Stripe, similar)
- Any other amounts received for services or goods

After collecting, state the total gross income figure and confirm with the user before proceeding.

Note: Do not advise on whether specific amounts are taxable. Flag unusual items for CPA review.

---

### Step 4: Confirm Expense Summary

First, confirm whether the user is a sole proprietor or operates through a corporation. This determines what belongs in the T1 package expense section.

**If sole proprietor:** Collect business expenses relevant to T2125. Proceed with the full expense collection below.

**If incorporated:** Business income and operating expenses belong to the corporation and are handled through the T2 package. Do not collect a full corporate expense summary here. Instead, note that the corporate expense picture belongs in `05-preparing-cpa-t2-package` and collect only T1-relevant items: any personal self-employment income earned outside the corporation, compensation received from the corporation such as salary or dividends, and note that other personal tax items will be collected in Step 6.

For sole proprietors, confirm which classifying-expenses variant was used. If already captured in Step 1, carry it forward. If not, ask now. Record the variant name for the cover summary.

If the user completed a classifying-expenses variant, ask them to paste or summarize the output.

If starting fresh, ask what type of self-employment work they do, then collect expenses by category. Ask for totals, not line-by-line detail:

- Cost of goods sold or direct project costs
- Subcontractors or contract labour
- Professional fees: accounting, legal, consulting paid to third parties
- Software and subscriptions
- Office expenses and supplies
- Advertising and promotion
- Home office: portion of rent, utilities, internet if a dedicated workspace exists
- Vehicle: fuel, insurance, maintenance, lease payments for business travel
- Bank charges and interest
- Meals and entertainment
- Capital purchases: equipment, computers, furniture over approximately $500. Flag separately for CPA review as potential capital items rather than regular operating expenses. These may need to be added to the CCA schedule instead of deducted directly.
- Other business expenses

Flag incomplete or missing amounts without advising on what to claim.

---

### Step 5: Confirm GST/HST Status

Apply the same structure filter established in Step 4 before collecting GST/HST information.

**If sole proprietor:** Collect GST/HST status relating to the personal business activity. If the user completed `02-checking-gst-hst`, ask them to paste or summarize the output. If starting fresh, collect:

- Registered or not registered
- If registered: RT account number, reporting period (annual, quarterly, monthly), last filing period completed, HST collected total for the year, ITCs claimed total for the year
- If not registered: note approximate gross revenue to help assess whether the small supplier threshold may have been crossed. Flag for CPA if near or above the threshold

If there is a gap in filing history or uncertainty about remittances, flag for CPA. Do not advise on what to file.

**If incorporated:** Do not collect full corporate GST/HST detail here. GST/HST tracking belongs to the corporation and is handled in the T2 package. Note only whether any GST/HST filings may be outstanding as a flag item, and confirm that the detail will be covered in `05-preparing-cpa-t2-package`.

---

### Step 6: Collect Personal and Other Items

These affect the T1 return and the CPA needs them even if they are not related to self-employment.

Ask one question at a time. Skip any the user confirms do not apply.

- RRSP contributions made in the tax year or in the first 60 days of the following year. Confirm total and whether they have RRSP contribution receipts.
- Charitable donations. Confirm total and whether receipts are available.
- Medical expenses. Confirm total and whether receipts are on hand.
- Tuition or education amounts for themselves or a dependant.
- Any changes in marital status or dependants during the year.
- Any foreign income or assets. If yes, flag for CPA without collecting details.
- Moving expenses if they relocated for work or to start a business.
- Any CRA correspondence, requests, or outstanding balances from prior years.

---

### Step 7: Identify Gaps and Flag Questions

Before producing the summary, review the collected information and identify:

**Missing items:** List anything that is noted as missing or not confirmed: prior year NOA, RRSP receipts, instalment totals, CCA schedules, GST/HST account status.

**Flagged items:** List anything noted during collection that requires CPA attention before the return is filed. State each as: "Item: [description]. Flag reason: [what is unclear or requires professional judgment]."

Ask the user to confirm the gap and flag list before producing the cover summary.

---

### Step 8: Produce Cover Summary

Produce a structured summary the user can send to their CPA. Format as a plain document, not a table. Use the structure below.

---

**CPA Package Cover Summary**
Tax year: [year]
Prepared: [today's date]

**Income**
Total gross income: $[amount]
Sources confirmed: [list by type, no client names]
Notes: [any income flags from Step 3]

**Expenses**
Business structure: [sole proprietor / incorporated]
Corporate expense package: [not applicable / handled separately in T2 package / not yet prepared]
Total operating expenses: $[amount] / [not applicable, incorporated]
Expense variant used: [classifying-expenses/variant-name / not used, collected fresh / not applicable]
Categories with amounts: [list / not applicable]
Capital purchases flagged for CCA review: [list items and amounts / none]
Notes: [vehicle/home office business-use percentage needed, any flags]

**GST/HST**
GST/HST structure: [sole proprietor / incorporated]
If sole proprietor: Registration status [registered / not registered], RT account [last 4 digits only if registered], reporting period [annual/quarterly/monthly], last period filed [period], HST collected [amount], ITCs [amount], small supplier status [confirmed / not confirmed, flag if near threshold]
If incorporated: Detail handled separately in T2 package. Outstanding filings or issues: [note / none flagged]
Notes: [any GST/HST flags]

**Prior Year and Personal Items**
Prior year NOA: [on hand / missing]
Instalments paid: $[amount] / [not applicable / not confirmed]
CCA carryforward: [note] / [not applicable]
Business loss carryforward: [note] / [not applicable]
RRSP deduction limit from prior NOA: $[amount] / [not available]
RRSP contributions this year: $[amount] / [none]
Charitable donations: $[amount] / [none]
Medical expenses: $[amount] / [none]
Other personal items: [list or none]

**Missing Items**
[List each missing item, one per line]

**Questions for CPA**
[List each flagged item and flag reason, one per line]

---

If the user does not have a CPA, state that a CPA can use this summary to scope the engagement and prepare the return. Do not recommend a specific CPA.

If the user is incorporated, ask whether they have also prepared or started `05-preparing-cpa-t2-package`. If not, note in the cover summary that a corporate package may also be needed before the CPA meeting.

---

## Common Mistakes to Watch For

**Treating the package as complete when information is missing:** If prior workflows were skipped and the same information was not collected directly in this workflow, the package is incomplete. State what is missing before producing the cover summary. If no classifying-expenses variant exists for the user's profession, note this and collect expenses fresh using the categories in Step 4.

**Capital purchases in operating expenses:** If the expense summary includes equipment, computers, or similar items over approximately $500 without a flag, flag them separately for CPA review as potential capital items. They may need to be added to the CCA schedule rather than deducted as current operating expenses.

**Including SIN or business number in the summary:** If either appears in collected information, do not include it in the cover summary. Note in the summary that the CPA will need it directly from the user.

**Mixing tax years:** If the user references income or expenses from multiple years, confirm which year each item belongs to before including it.

**Assuming the prior year NOA is not needed:** The prior year NOA confirms RRSP room, prior instalments on account, and any outstanding balance. If it is missing, flag it, do not skip it.

**Confusing instalments with tax owing:** Instalments paid during the year reduce tax owing on the return. They are not a separate filing. If the user is unclear on this, clarify and continue.

**Reporting GST/HST amounts without confirming basis:** If the basis used for GST/HST tracking is unclear, note the uncertainty and flag for CPA.

**Marking foreign income as confirmed without CPA review:** Any foreign income or foreign assets trigger potential reporting obligations beyond the T1. Flag without collecting details.

---

## Stop and Refer to a CPA If:

- The user reports foreign income or foreign property that may trigger additional reporting. If foreign property may have approached or exceeded CAD $100,000 at any point in the year, flag this clearly for CPA review. "That is outside what this workflow covers. It is a question for a CPA before you file."
- The user has unreported income from prior years they are now disclosing. "That is outside what this workflow covers. It is a question for a CPA before you file."
- The user received a CRA audit notice, proposal letter, or reassessment for any year covered by or related to this return. "That is outside what this workflow covers. It is a question for a CPA before you file."
- The user has a corporate structure and is unclear whether income belongs on the personal return or the corporate return. "That is outside what this workflow covers. It is a question for a CPA before you file."
- The user made an RRSP contribution exceeding their available room. "That is outside what this workflow covers. It is a question for a CPA before you file."
- The GST/HST filing history has gaps or unremitted amounts. "That is outside what this workflow covers. It is a question for a CPA before you file."

---

## Where a CPA Adds Value

At the end of the workflow, state:

> This package organizes what you have gathered. A CPA will review it for completeness, identify items you have not thought to include, apply the correct treatment to each line of the return, optimize the order and timing of deductions, and file on your behalf. The value is not in having organized documents. It is in what the CPA does with them once they have them.
