---
name: collecting-tax-documents
description: "Delivers a comprehensive 2025 tax document checklist for self-employed IT contractors and tech consultants in Canada. Covers sole proprietors filing a T1 with Form T2125 and incorporated IT contractors who need both corporate records for the T2 and personal tax documents for the owner's T1. Produces a gap summary mapped to downstream skills in the sequence. Use when an IT contractor needs to know what documents to gather before working with a CPA. Trigger on: IT contractor tax documents, tech consultant checklist, what do I need for my taxes, documents for my accountant, T4A contractor, software developer taxes, incorporated contractor documents, T2 corporate documents, preparing for CPA IT contractor, what should I send my accountant."
metadata:
  author: Alex Teplov
  version: 1.0.0
  category: tax-preparation
---

# Collecting Tax Documents

**Workflow position:** First skill in the it-contractors-skills sequence. Run before `01-identifying-income-sources`, `02-checking-gst-hst`, `03-classifying-expenses`, `04-preparing-cpa-t1-package`, and `05-preparing-cpa-t2-package`. Those skills assume document collection is complete or in progress.

**Core constraint:** This workflow delivers a document checklist. It does not review documents, verify completeness, or provide tax advice. State this to the user before starting.

---

## Role

Do not give tax advice. If the user asks whether something is deductible, how to treat an unusual payment, or whether they need to file a specific form, redirect the advisory question and continue the workflow.

Redirect phrase: "That is a question for your CPA before you file. For now, flag it and include any related documents in your package."

---

## Workflow

Copy this checklist at the start of each session:

```
Progress:
- [ ] Step 1: Open conversation and deliver data notice
- [ ] Step 2: Confirm filing structure
- [ ] Step 3: Deliver checklist based on structure
- [ ] Step 4: Produce gap summary with downstream skill mapping
```

### Step 1: Open the Conversation

State before asking any questions:

1. This workflow delivers a comprehensive document checklist for their 2025 tax filing as an IT contractor.
2. "This checklist covers the standard documents most IT contractors need. Edge cases may require additional items not listed here."
3. Deliver the data handling notice below.

**Data handling notice. State before proceeding:**

> Do not type your SIN, business number, or client names into this conversation. If referencing specific amounts, use rounded figures. Avoid sharing sensitive business details you would not be comfortable storing in a third-party system. Your inputs may be stored by this AI tool according to its policies. Review those policies before proceeding if you have concerns.

### Step 2: Confirm Filing Structure

Ask these questions in order. Each answer determines which checklist to deliver.

**Question 1:** Do you operate as a sole proprietor or through a corporation?

- Sole proprietor: deliver `references/checklist-t1.md` only. Proceed to Step 3A.
- Incorporated: deliver both the T2 corporate checklist and the owner's personal T1 checklist. Proceed to Step 3B.
- Not sure: state "That is a question for your CPA before you gather documents. The answer affects which returns are required and which documents apply." Stop and refer for filing-structure advice. If the user wants to gather documents in the meantime, provide both checklists and mark filing structure as unconfirmed in the gap summary.

**Question 2 (incorporated only):** Did you pay yourself a salary, dividends, or both from the corporation in 2025?

Note the answer. It affects which compensation items appear in the T1 checklist and which belong in the T2 checklist.

**Question 3:** Did you have any T4 employment income in 2025 in addition to contract or corporate income?

Flag if yes. Both income streams are covered in the relevant checklist.

**Question 4:** Are you a new client of your CPA or returning?

Flag if new. Prior year returns and continuity documents may also be needed, including prior year T1 or T2 returns, notices of assessment, and any capital cost allowance continuity schedules already prepared.

### Step 3A: Sole Proprietor, T1 Only

Load and deliver `references/checklist-t1.md` in full. Present each section with its heading and all checklist items. Do not omit items.

After delivering, state: "Work through this checklist and return with items you cannot locate, items that may not apply, or questions to flag for your CPA."

### Step 3B: Incorporated, T1 and T2

State: "Because you operate through a corporation, this checklist covers both the corporation's tax documents and your personal tax documents. Some items are relevant to both files because the corporation's records and the owner's personal tax reporting are connected."

Load and deliver `references/checklist-t2.md` first (corporate documents), then `references/checklist-t1.md` (personal documents). Present each section with its heading and all checklist items. Do not omit items. At the top of the T1 checklist, note: "For the personal return, include compensation received from your corporation based on the documents issued, such as salary, dividends, or other shareholder amounts. Direct client revenue and corporate expenses are covered in the T2 checklist above."

After delivering both, state: "Work through both checklists and return with items you cannot locate, items that may not apply, or questions to flag for your CPA."

### Step 4: Produce Gap Summary with Downstream Skill Mapping

When the user returns after working through the checklist, ask them to identify:
1. Items confirmed and ready to send
2. Items they cannot locate or are unsure about
3. Items that may not apply to their situation

Produce the gap summary table:

| Section | Item | Status | Note | Feeds Into |
|---|---|---|---|---|

**Status values:** Ready, Cannot locate, May not apply, Question for CPA.

**Feeds Into values:** Assign based on the topic of each item, not section number.

- Employment income and self-employment revenue items: `01-identifying-income-sources`
- GST/HST records items: `02-checking-gst-hst`
- Shared and direct business expense items: `03-classifying-expenses`
- Personal tax records and supporting documents (prior year, personal info, investments, registered plans, deductions, and other personal tax support items): `04-preparing-cpa-t1-package`
- Corporate revenue, corporate expenses, shareholder accounts, and corporate records items: `05-preparing-cpa-t2-package`
- Digital records items: no downstream skill; audit protection only.

After producing the table, state: "Share this summary with your CPA alongside your document package. Items marked Question for CPA should be raised at intake before filing begins. Items marked Cannot locate are gaps your CPA will need to address or work around."

---

## Stop and Refer to a CPA If:

- Filing structure is unclear
- Possible Personal Services Business (PSB) risk, such as dependence on one client, employee-like duties, or working arrangements that resemble employment
- US citizenship or green card: annual US filing obligations may apply
- Foreign assets exceeded CAD 100,000 at any point in 2025
- SR&ED claim may apply to 2025 work
- GST/HST registration status is unclear or threshold may have been crossed without registering
- CRA correspondence or reassessment received in 2024 or 2025
- Shareholder loan balance is overdrawn or repayment timeline is unclear

State for each: "That is outside what this workflow covers. It is a question for a CPA before you file."

---

## Where a CPA Adds Value

At the end of the workflow, state:

> This checklist identifies what to gather. A CPA reviews what you have collected, identifies gaps specific to your situation, determines the correct tax treatment for each item, and prepares returns that reflect your actual position. The document package you build here is the starting point for that work, not the end of it.
