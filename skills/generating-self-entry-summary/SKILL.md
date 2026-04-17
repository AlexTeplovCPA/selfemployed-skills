---
name: generating-self-entry-summary
description: Generate a grouped-by-form self-entry summary for a Canadian IT contractor after income, expenses, and supporting facts have been organized by earlier skills. Use when the user wants a plain-language summary for tax software entry, needs amounts grouped by T1 and T2125 areas, or wants to see which items are ready, unclear, or require CPA review before entry. Reads prior skill outputs and produces a form-grouped summary with readiness labels, missing items, review warnings, and next steps.
metadata:
    author: Teplov CPA
    version: 1.0
    updated: 2026-04-17
---

# Generate Self-Entry Summary

Generate a grouped-by-form self-entry summary after the file has been organized by earlier skills.

## Core Rules

- Work only from organized prior results, not from raw guesswork.
- Group amounts by form and field where possible.
- Distinguish clearly between ready items, unresolved items, and review items.
- Preserve uncertainty where support is incomplete.
- Use plain language suitable for a non-practitioner.
- Organize and summarize, do not advise.
- Do not verify completeness or accuracy.
- Do not determine final filing positions.
- Do not state that an unresolved amount is safe to enter.
- Do not hide review flags or missing items.
- Do not confirm that every mapped amount is deductible.
- Do not tell the user that no CPA review is needed.
- Do not generate a vague summary with no field-level structure.
- Use this phrase where relevant: "That is outside what this workflow covers. It is a question for a CPA before you file."

## Inputs

Do not ask the user to share SIN, business number, account numbers, or client names. Use general descriptions and rounded amounts.

Accept any of:

- outputs from earlier skills in the repository
- a partially aggregated case output object
- organized income mappings
- organized expense mappings
- missing-items output
- GST/HST review output if relevant
- instalment review output if relevant

Minimum useful input:

- at least one organized form-relevant result from a prior skill
- at least one status or mapping that can be shown to the user

Read from the shared input schema where available: `case_id`, `tax_year`, `engagement_mode`, `user_profile`, `form_context`, `review_state`, `output_preferences`.

Read from prior skill outputs where available, especially: `collecting-tax-documents`, `identifying-income-sources`, `identifying-expense-categories`, `organizing-t2125-gross-business-income`, `organizing-t2125-routine-operating-expenses`, `organizing-t2125-8523-meals-and-entertainment`, `organizing-t2125-business-use-of-home`, `organizing-t2125-capital-assets-and-cca`, `organizing-t2125-other-expenses`, `checking-gst-hst`, `reviewing-foreign-platform-and-us-income`, `reviewing-instalments-and-tax-payments`.

## Workflow

### 1. Confirm self-entry mode is appropriate

Use this skill when the user wants a grouped-by-form summary for tax software entry or a combined view of mapped fields and unresolved items.

If the user needs a practitioner-facing handoff package instead, route to `generating-cpa-handoff-summary`.

### 2. Gather prior mapped results

Collect relevant prior outputs and organize them by form.

Typical forms or sections: T2125, T1, GST/HST review status if relevant.

Use prior `mappings_proposed`, `flags`, `open_questions`, and `status` values.

Do not invent field mappings that were not supported by earlier skills.

### 3. Group items by form and field

Build a grouped summary using broad field labels a user can understand.

Examples:

- T2125 gross business income
- T2125 routine operating expenses
- T2125 meals and entertainment
- T2125 business-use-of-home expenses
- T1 T4 income
- T1 T4A income
- T1 RRSP deduction
- T1 instalment payments

For each item, show: label, amount if known, status, short basis, caution note if needed, missing items if needed.

### 4. Determine field readiness

For each grouped field or bucket, assign one of:

- ready for entry
- clarification required
- CPA review recommended
- not applicable

Use the strongest unresolved issue that still affects the field. Do not downgrade caution just to make the summary look cleaner.

### 5. Aggregate missing items and review warnings

Create a short section for missing items, review warnings, and unresolved questions that still matter for entry.

Only include issues that materially affect the user's next step. Do not duplicate the same issue in multiple sections unless the duplication improves clarity.

### 6. Generate entry readiness summary

Summarize at a high level:

- count of fields or sections ready for entry
- count needing clarification
- count with CPA review recommended
- overall readiness: `complete`, `partial`, or `not ready`

### 7. Write a client-safe final summary

Produce a plain-language output that groups items by form, highlights what appears ready, highlights what still needs clarification, and reminds the user that the summary does not confirm correctness or deductibility.

## Resource Map

- `references/grouped-by-form-template.md`: use for the visible output structure
- `../../references/self-entry-summary-template.md`: use as the master template
- `../../references/shared-input-schema.md`: read to populate input fields
- `../../references/shared-output-schema.md`: read to format output fields

## Output

Return using the shared output schema. Include:

- `mappings_proposed`: aggregated prior mappings only where earlier skills already produced them
- `flags`: carry forward only flags that still matter at summary level
- `open_questions`: carry forward only unresolved questions that still block or affect entry
- `status`: one of `ready_for_entry`, `clarification_required`, `incomplete`, `cpa_review_recommended`
- `client_safe_summary`: plain language, grouped by form

Also produce a visible grouped-by-form self-entry summary using the template, including:

- Completion Status (overall result and short explanation)
- T2125 section grouped by: business income, business expenses, business-use-of-home, capital and asset-related items
- T1 section grouped by: slips and income, deductions, tax-related items
- Missing Items
- Review Warnings
- Entry Readiness (counts and overall readiness)
- Next Steps

## Status Guidance

- `ready_for_entry`: summary can be generated and at least some fields are clearly ready for entry
- `clarification_required`: summary can be generated but unresolved items materially remain
- `cpa_review_recommended`: major parts of the file are too uncertain for confident self-entry
- `incomplete`: too little organized information to generate a useful summary

Do not use `ready_for_entry` to imply that the whole return is ready to file.

## Validation

- Every T2125 and T1 section is present or explicitly marked not applicable.
- Each field or bucket has a readiness label.
- Missing Items and Review Warnings sections are present even if empty.
- Overall readiness is one of: `complete`, `partial`, `not ready`.
- `client_safe_summary` is present and contains no tax advice.
- No major unresolved flag from a prior skill is hidden in the summary.
