---
name: organizing-t2125-8523-meals-and-entertainment
description: Organize likely meals and entertainment expenses for line 8523 of form T2125 for a Canadian IT contractor after expense categories have already been identified. Use when the user needs to review restaurant, coffee meeting, client meal, or similar expenses, separate likely business meals from personal or unclear charges, or prepare a structured mapping for self-entry or CPA handoff. Accepts prior skill output, expense logs, receipts, and transaction summaries. Produces a provisional line 8523 mapping with support strength, business purpose flags, and downstream routing.
metadata:
    author: Teplov CPA
    version: 1.0
    updated: 2026-04-17
---

# T2125 8523 Meals and Entertainment

Organize likely meals and entertainment expenses for line 8523 of T2125 after the broader expense picture has already been identified.

## Core Rules

- Work from identified expense categories, not from vague assumptions.
- Focus on likely meal and entertainment expenses that may belong in T2125 line 8523.
- Separate likely business meals from personal, mixed, unsupported, or unclear charges.
- Preserve uncertainty where support is incomplete or business purpose is weak.
- Organize and flag, do not advise.
- Do not determine final deductibility.
- Do not determine final GST/HST treatment.
- Do not assume every restaurant or cafe charge is business-related.
- Do not force unsupported items into line 8523.
- Do not state that a restaurant or meal charge is definitely allowable.
- Do not state that the user is ready to file.
- Use this phrase where relevant: "That is outside what this workflow covers. It is a question for a CPA before you file."

## Inputs

Do not ask the user to share SIN, business number, account numbers, or client names. Use general descriptions and rounded amounts.

Accept any of:

- output from `identifying-expense-categories`
- expense log or CSV
- uploaded receipts
- bank or card transaction summaries
- user explanation in chat
- bookkeeping export

Minimum useful input:

- vendor or description suggesting a meal or entertainment cost
- amount
- some explanation of what the expense was for

Read from the shared input schema where available: `case_id`, `tax_year`, `engagement_mode`, `user_profile`, `facts.business_activity`, `documents.expense_support`, `transactions.expense_items`, `form_context`, `review_state`.

Read from prior skill outputs where available: `identifying-expense-categories`.

## Workflow

### 1. Confirm that meals and entertainment review is relevant

Check whether available facts suggest one or more expenses that may belong in T2125 line 8523.

Typical indicators: restaurant charges, cafe or coffee meeting charges, client dinner or lunch charges, food delivery described as business-related, entertainment charges tied to business meetings.

If the file does not support a meals and entertainment review, preserve that uncertainty and do not force a mapping.

### 2. Build the candidate meals and entertainment set

Create a working set of expenses that may belong in line 8523.

Typical candidates: restaurant meals, coffee meetings, client lunches or dinners, food delivery claimed as business-related, entertainment-type charges with a stated business purpose.

Do not automatically include: undocumented personal meals, groceries with no business context, travel costs that are only transport or accommodation, mixed retail purchases where the meal component is unclear, charges with no plausible business purpose.

### 3. Extract key facts for each candidate item

For each candidate, identify: vendor, date, amount, description, receipt status, business purpose explanation, whether attendees are known, and whether the charge may include a personal component.

Do not invent missing details.

### 4. Assess support strength

For each candidate, mark support as `sufficient`, `partial`, `weak`, or `none`.

A receipt alone may still be weak if business purpose is not clear.

### 5. Build the provisional line 8523 mapping

Map candidate items into one of:

- likely include in line 8523
- include with caution
- exclude_or_clarify
- needs_manual_review
- not_applicable

Use line reference `8523` when the item appears to belong in Meals and entertainment. Do not overstate confidence.

### 6. Flag issues that affect line 8523 readiness

Flag issues such as:

- no receipt
- business purpose unclear
- attendee information missing where relevant
- personal and business use may be mixed
- charge may belong in another category
- charge appears duplicated
- support is too weak to rely on directly

Only flag issues that materially affect readiness.

### 7. Prepare downstream routing

Indicate likely downstream uses:

- `generating-self-entry-summary`
- `generating-cpa-handoff-summary`
- `generating-missing-items-summary`

Do not run those workflows inside this skill.

## Resource Map

- `../../references/shared-input-schema.md`: read to populate input fields
- `../../references/shared-output-schema.md`: read to format output fields

## Output

Return using the shared output schema. Include:

- `facts_accepted`: usable expense facts the skill relied on
- `mappings_proposed`: use entries such as likely include in 8523, include with caution, exclude_or_clarify, needs_manual_review, not_applicable; use field reference `8523`
- `flags`: use `missing_support`, `mapping_uncertain`, `possible_personal_component`, `possible_duplication` where applicable
- `open_questions`: only questions needed to resolve meaningful uncertainty; typical useful questions include: What was the business purpose? Who attended? Do you have the receipt? Was any personal portion included?
- `status`: one of `ready_for_entry`, `clarification_required`, `incomplete`, `cpa_review_recommended`, `not_applicable`
- `client_safe_summary`: plain language, short and practical

Also include a meals and entertainment mapping grouped into:

- likely included in line 8523 (show vendor or item label, amount if known, support strength, confidence level)
- excluded or separately reviewed items
- unclear items needing clarification

## Status Guidance

- `ready_for_entry`: likely line 8523 items are sufficiently organized for downstream summary use
- `clarification_required`: meal-related items are identified but support or business purpose is incomplete
- `cpa_review_recommended`: file includes material mixed-use, unclear business purpose, or repeated weak support
- `incomplete`: major meal-related support is still missing
- `not_applicable`: line 8523 review does not appear relevant from the facts provided

Do not use `ready_for_entry` if the business purpose of key items remains unclear.

## Validation

- Every candidate item is mapped or explicitly excluded.
- Each included item has a stated or noted business purpose.
- Business purpose flags are applied wherever purpose is missing or weak.
- At least one downstream skill is identified in routing.
- `status` is one of the five standard values.
- `client_safe_summary` is present and contains no tax advice.
