---
name: identify-income-sources
description: "Guides self-employed Canadians through identifying and documenting all income sources for the current tax year. Use when a self-employed Canadian needs to organize income before tax filing or a CPA review. Trigger on: T4A, T4, invoices, self-employment income, income summary, prepare for CPA, organize my income, what income do I need to report, I don't know if I have everything, I need to pull together my income."
metadata:
  author: Alex Teplov
  version: 1.0.0
  category: tax-preparation
---

# Identify Income Sources

**Workflow position:** This is the first skill in the selfemployed-skills sequence. Run this before `check-gst-hst`, `classify-expenses`, and `cpa-review-prep`. Those skills assume this step is complete or in progress.

Run this workflow conversationally. Ask questions, read uploaded documents, fill gaps, and produce a clean income summary the user can send to a CPA or use to prepare their return.

**Core constraint: this workflow organizes information. It does not verify completeness or accuracy. State this to the user before starting.**

---

## Your Role

Do not give tax advice. When the user asks what is taxable, how to treat an unusual payment, or whether they need to file a specific form, redirect the advisory part of the question and continue the workflow.

---

## Step 1: Open the Conversation

State the following before asking any questions:

1. This workflow will help build a complete income summary for the tax year.
2. State explicitly: "This process relies on what you provide. It will not catch everything on its own."
3. Deliver the data handling notice below.
4. Ask which tax year they are filing for.
5. Ask them to upload any income documents they have: T4A slips, T4 slips, invoices, foreign payment confirmations, platform earnings summaries, or bank statements showing income deposits.

**Data handling notice. State this before they upload anything:**

> Do not type your SIN, business number, or client names into this conversation. Amounts and income types are all we need. If uploading photos of tax slips, cover or black out your SIN before photographing. Avoid sharing sensitive business details you would not be comfortable storing in a third-party system. Your inputs and uploaded documents may be stored by this AI tool according to its policies. Review those policies before proceeding if you have concerns.

---

## Step 2: Review Uploaded Documents

Assume documents are incomplete unless the user clearly states otherwise. Do not assume totals from a single document represent all income for that source.

When the user uploads documents:

- Read each document and extract: income source type, amount in CAD, payer type (not name), date (if visible), and any notes such as unclear amounts or missing information
- If a document is unreadable, state this immediately and ask the user to retake the photo. If retaking is not possible, ask them to enter the amount and document type manually and flag it as "manually entered, verify against original"
- Do not ask questions yet. Complete the document review first

After reviewing all documents, state:
1. What income sources were confirmed from the documents
2. What was unclear or unreadable
3. What common income sources for a self-employed Canadian may be missing based on what was uploaded

---

## Step 3: Fill the Gaps

Ask questions one at a time. Wait for the answer before asking the next question. Skip any area already confirmed from documents. Cover these areas in order:

**Employment income**
Did they have any T4 employment income in addition to self-employment? Includes part-time, casual, or any work where an employer deducted CPP and EI.

**Self-employment income without a slip**
Did they invoice any Canadian clients who did not issue a T4A? All invoiced income is taxable whether or not a slip was issued.

**Cash, e-transfer, or informal payments**
Did they receive any cash, e-transfer, or informal payments not reflected in invoices or slips?

**Platform income**
Did they receive income through platforms such as Upwork, Fiverr, Toptal, or PayPal that was not captured in uploaded documents?

**Foreign income**
Did they receive payment from clients outside Canada? If yes, ask for the original currency and amount. Flag it for CAD conversion using a reasonable method, often the Bank of Canada annual average exchange rate for the tax year. Do not convert it yourself. Flag it clearly in the Notes column.

**Other income**
Any amounts that do not clearly relate to regular business or employment activity. Do not default informal payments here unless they are clearly not business-related.

**Bank deposit cross-check**
Ask the user to scan their bank statements for any deposits not already captured in the summary. Treat this as a final completeness check. If unmatched deposits are identified, keep them in the table as "Not yet confirmed" rather than excluding them.

---

## Partial Output Fallback

If the user stops early or cannot complete all steps, produce a partial income summary using what is known. Mark all incomplete areas clearly as "Not yet confirmed." State to the user that a partial summary is still useful for a CPA review.

---

## Step 4: Produce the Income Summary

Once gaps are filled, or the user indicates they are done, produce a table with five columns. Do not remove or merge entries unless the user explicitly confirms they refer to the same income source.

| Income Source Type | Amount (CAD) | Document Status | Likely Category | Notes |

Document status values:
- **Confirmed from document:** extracted from an uploaded photo or file
- **Estimated:** amount provided by user without a document
- **Missing, need to obtain:** income source identified but amount not confirmed
- **Manually entered, verify against original:** document was unreadable
- **Not yet confirmed:** partial output, follow-up required

Likely category values:
- **Business income:** self-employment income, invoiced work, platform income, cash or informal payments that relate to business activity
- **Employment income:** T4 income where employer deducted CPP and EI
- **Other income:** amounts that do not clearly relate to regular business or employment activity
- **Review required:** classification is unclear; assign this when in doubt

After producing the table:
- Ask the user to review and flag anything that looks wrong
- State: "This summary is ready to send to a CPA for review and completion of your return."
- If they do not have a CPA, state that a CPA can review this summary and complete their return. Do not name or recommend a specific CPA.

---

## Common Mistakes to Watch For

**No T4A does not mean no income**
If the user says they only have one T4A or no slips, ask specifically about invoiced income. Every dollar of self-employment income is taxable whether or not a slip was issued.

**Duplicate income reporting**
If the same income appears in multiple places, such as a T4A and invoices for the same work, or platform reports and bank deposits, make sure it is counted only once. Ask the user to confirm if the same amount appears in more than one source. If duplication is suspected but not confirmed, keep both entries and flag them in Notes for CPA review.

**Net vs gross confusion**
Users may report net deposits after fees rather than gross income. If a platform or payment processor is involved, such as Stripe, PayPal, or Upwork, confirm whether the amount is before or after fees. Income is generally reported on a gross basis before fees.

**Refunds and reversals**
If income was refunded or reversed during the year, confirm whether the reported amounts already reflect that. Do not count income that was later returned.

**Foreign income left in original currency**
If the user mentions USD or any other foreign currency without flagging conversion, catch it. Flag it in the Notes column. Do not convert it yourself.

**Income outside the tax year**
If dates are visible on documents or provided by the user, confirm that income falls within the selected tax year. Flag anything outside the year in Notes rather than excluding it.

**January payments for prior-year work**
If the user mentions a payment received in January, confirm which year it was received, not which year the work was done. Income is reported in the year received.

**SIN visible on uploaded document**
If a SIN is readable in an uploaded document, do not record or reference it. State that the SIN is visible and remind the user of the redaction instruction. Proceed using only the income information.

---

## Stop and Refer to a CPA If:

- They received income from a corporation they own or control
- They have income from a partnership
- They received government support or loans and are unsure how to treat them
- They are unsure whether a payment is income or a reimbursement of expenses
- They are unsure how to allocate income across provinces
- Their total foreign assets exceeded CAD 100,000 at any point in the year
- They have collected GST/HST but are unsure about registration or remittance status

For each of these, state: "That is outside what this workflow covers. It is a question for a CPA before you file."

---

## Where a CPA Adds Value

At the end of the workflow, state this:

> This summary reflects what you have identified and provided. A CPA will test it against your bank activity, identify missing income streams, confirm proper classification, and apply the correct reporting treatment for each type of income. The value is not in retyping this table. It is in validating and adjusting it before it goes on your return.
