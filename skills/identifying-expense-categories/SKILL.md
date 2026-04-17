---
name: identifying-expense-categories
description: Organize the expense categories of a Canadian IT contractor before deeper T2125 field mapping begins. Use when the user needs to sort business expenses into major buckets, identify possible capital items, separate mixed or unclear spending, or check what expense support is missing before preparing T2125 fields or related summaries. Accepts expense logs, bookkeeping exports, transaction summaries, receipts, and chat descriptions. Produces a grouped expense category map with support status, flags, and downstream routing toward T2125 field skills.
metadata:
    author: Teplov CPA
    version: 1.0
    updated: 2026-04-17
---

# Identifying Expense Categories

Organize the user's expense universe before deeper T2125 field mapping begins.

## Core Rules

- Organize expenses before trying to finalize field-level treatment.
- Group expenses by practical category first, not by guesswork about final deductibility.
- Separate likely routine expenses from possible capital items.
- Preserve uncertainty where support is incomplete or mixed.
- Identify missing or weak support that affects downstream review.
- Organize and flag, do not advise.
- Do not determine final deductibility.
- Do not determine final GST/HST treatment.
- Do not force every expense into a final T2125 line at this stage.
- Do not state that a category is definitely allowable.
- Do not finalize capital vs current treatment where uncertainty remains.
- Do not conclude that mixed-use items are fully business.
- Do not state that the user is ready to file.
- Use this phrase where relevant: "That is outside what this workflow covers. It is a question for a CPA before you file."

## Inputs

Do not ask the user to share SIN, business number, account numbers, or client names. Use general descriptions and rounded amounts.

Accept any of:

- expense log or CSV
- bookkeeping export
- bank or card transaction summaries
- uploaded receipts
- screenshots
- user explanation in chat
- vendor/category spreadsheet

Minimum useful input:

- vendor or expense description
- amount
- date or approximate timing
- user explanation of what the expense was for

Read from the shared input schema where available: `case_id`, `tax_year`, `engagement_mode`, `user_profile`, `facts.business_activity`, `facts.home_office`, `facts.vehicle_use`, `documents.expense_support`, `transactions.expense_items`, `review_state`.

## Workflow

### 1. Establish the expense context

Determine whether the file includes:

- routine operating expenses
- meals and entertainment
- travel
- home office related costs
- vehicle-related costs
- professional fees
- subcontractor or outside service costs
- one-time equipment or possible capital items
- other unclear or mixed expenses

If source data is incomplete, continue with the broadest useful categorization and preserve uncertainty.

### 2. Group expenses into practical categories

Sort expenses into:

- software and cloud tools
- office and admin expenses
- internet and phone
- meals and entertainment
- travel
- professional fees
- subcontractors and outside services
- workspace or rent-related costs
- home office related costs
- vehicle-related costs
- equipment and possible capital items
- unclear or other expenses

Use practical grouping first. Do not force a final tax treatment unless the category is clearly obvious and low-risk.

### 3. Assess support quality

For each category or item, mark support status as `received`, `mentioned_not_provided`, `missing`, `not_applicable`, or `unclear`.

Do not treat weak memory-based descriptions as strong support.

### 4. Separate likely routine expenses from possible capital items

Flag expenses that may require a later capital review.

Common examples: laptop purchases, monitors, phones, desks or office furniture, equipment bundles, other large one-time purchases.

Do not finalize the treatment here. Route likely capital items forward for later review.

### 5. Flag mixed or unclear items

Flag issues such as:

- personal and business use may be mixed
- business purpose unclear
- category unclear
- same charge may appear duplicated
- one expense may belong in a different review area
- home office or internet costs may require allocation
- meal or travel wording is too weak to rely on directly

Only flag issues that matter for downstream mapping or readiness.

### 6. Prepare downstream routing

Indicate which downstream skills are likely relevant:

- `organizing-t2125-routine-operating-expenses`
- `organizing-t2125-8523-meals-and-entertainment`
- `organizing-t2125-business-use-of-home`
- `organizing-t2125-capital-assets-and-cca`
- `organizing-t2125-other-expenses`
- `generating-self-entry-summary`
- `generating-cpa-handoff-summary`

Do not run downstream logic inside this skill.

## Resource Map

- `references/vendor-categories.md`: read when categorizing vendor types or unusual expense descriptions
- `../../references/shared-input-schema.md`: read to populate input fields
- `../../references/shared-output-schema.md`: read to format output fields

## Output

Return using the shared output schema. Include:

- `facts_accepted`: usable expense facts the skill relied on
- `mappings_proposed`: broad provisional mappings such as likely routine operating expenses, likely meals and entertainment, likely home office related costs, likely capital items requiring separate review, likely unclear or other expenses; do not overstate confidence
- `flags`: use `missing_support`, `mapping_uncertain`, `possible_personal_component`, `possible_capital_item`, `possible_duplication` where applicable
- `open_questions`: only questions needed to resolve meaningful uncertainty
- `status`: one of `ready_for_entry`, `clarification_required`, `incomplete`, `cpa_review_recommended`
- `client_safe_summary`: plain language, short and practical

Also include an expense category map grouped into:

- confirmed categories (show category label, representative items or examples, support status, likely downstream area)
- possible capital items
- mixed or unclear items
- missing-support items

## Status Guidance

- `ready_for_entry`: expense picture is sufficiently organized for downstream field mapping
- `clarification_required`: categories are mostly identified but support or classification is incomplete
- `cpa_review_recommended`: expense picture includes material mixed-use, capital, or unclear items
- `incomplete`: major expense information is still missing

Do not use `ready_for_entry` if significant categories remain weakly supported or materially unclear.

## Validation

- Every expense category present in the file is mapped or flagged.
- Possible capital items are identified in a separate group.
- Each category has a support status.
- At least one downstream skill is identified in routing.
- `status` is one of the four standard values.
- `client_safe_summary` is present and contains no tax advice.
