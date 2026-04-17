---
name: organizing-t2125-routine-operating-expenses
description: Organize likely routine operating expenses for form T2125 for a Canadian IT contractor after expense categories have already been identified. Use when the user needs to group recurring business expenses into practical T2125 expense buckets, separate routine operating costs from meals, home office, travel, vehicle, or possible capital items, or prepare a structured mapping for self-entry or CPA handoff. Accepts prior skill output, expense logs, bookkeeping exports, and transaction summaries. Produces a provisional routine expense mapping with support strength, flags, and downstream routing.
metadata:
    author: Teplov CPA
    version: 1.0
    updated: 2026-04-17
---

# T2125 Routine Operating Expenses

Organize likely routine operating expenses for T2125 after the broader expense picture has already been identified.

## Core Rules

- Work from identified expense categories, not from vague assumptions.
- Focus on likely routine operating expenses that may belong in ordinary T2125 expense areas.
- Separate routine operating costs from meals, travel, vehicle, home office, subcontractors, professional fees, and possible capital items where possible.
- Preserve uncertainty where support is incomplete or classification is mixed.
- Organize and flag, do not advise.
- Do not determine final deductibility.
- Do not determine final GST/HST treatment.
- Do not force mixed-use items into a fully business amount without support.
- Do not finalize capital vs current treatment where the facts remain unclear.
- Do not state that an expense is definitely allowable.
- Do not treat mixed-use internet or phone as fully business without support.
- Do not state that the user is ready to file.
- Use this phrase where relevant: "That is outside what this workflow covers. It is a question for a CPA before you file."

## Inputs

Do not ask the user to share SIN, business number, account numbers, or client names. Use general descriptions and rounded amounts.

Accept any of:

- output from `identifying-expense-categories`
- expense log or CSV
- bookkeeping export
- bank or card transaction summaries
- uploaded receipts
- user explanation in chat
- vendor/category spreadsheet

Minimum useful input:

- at least one identified expense item or expense category
- some indication of what the expense was for
- some support or explanation for the amount

Read from the shared input schema where available: `case_id`, `tax_year`, `engagement_mode`, `user_profile`, `facts.business_activity`, `facts.home_office`, `facts.vehicle_use`, `documents.expense_support`, `transactions.expense_items`, `form_context`, `review_state`.

Read from prior skill outputs where available: `identifying-expense-categories`.

## Workflow

### 1. Confirm routine operating expense review is relevant

Check whether available facts suggest ordinary business expenses not better handled by a separate downstream skill.

Typical indicators: recurring software subscriptions, cloud hosting, office supplies, internet and phone costs used for business, low-risk admin costs, minor workspace-related costs.

If the file does not support a routine operating expense review, preserve that uncertainty and do not force a mapping.

### 2. Build the candidate routine expense set

Create a working set of expenses that may belong in routine T2125 operating expense areas.

Typical candidates:

- software and cloud tools
- office and admin costs
- internet and phone expenses
- minor workspace-related costs
- recurring developer tools or subscriptions
- low-risk supplies and small business-use purchases

Do not automatically include: restaurant and meal charges, travel or vehicle costs, home office allocations, large one-time equipment purchases, professional fees, subcontractor payments, or unclear charges with no plausible business link.

### 3. Separate routine items from other review areas

Group identified amounts into:

- likely routine operating expenses
- likely meals and entertainment
- likely home office related costs
- likely travel costs
- likely professional fees
- likely subcontractor or outside service costs
- likely possible capital items
- unclear or mixed-use amounts

Do not settle mixed classification if the facts are weak.

### 4. Assess support strength

For each candidate expense or grouped category, mark support as `sufficient`, `partial`, `weak`, or `none`.

If the expense appears business-related but is not well-supported, preserve it as provisional.

### 5. Build the provisional routine operating expense mapping

Map supported or plausibly supported expenses into broad T2125 routine operating groupings:

- software and cloud
- office and admin
- internet and phone
- routine supplies
- minor workspace-related costs
- other routine operating items

Use practical grouping first. Do not overstate confidence in final line-level placement where the category could still shift.

### 6. Flag issues that affect readiness

Flag issues such as:

- support missing for recurring expenses
- internet or phone appears mixed-use
- same expense may appear duplicated
- one-time larger purchase may not be routine
- description too vague to support category
- expense may belong to a different downstream skill
- software or service may partly relate to a non-business activity

Only flag issues that materially affect readiness.

### 7. Prepare downstream routing

Indicate likely downstream uses:

- `organizing-t2125-8523-meals-and-entertainment`
- `organizing-t2125-business-use-of-home`
- `organizing-t2125-capital-assets-and-cca`
- `organizing-t2125-other-expenses`
- `generating-self-entry-summary`
- `generating-cpa-handoff-summary`

Do not run those workflows inside this skill.

## Resource Map

- `../../references/shared-input-schema.md`: read to populate input fields
- `../../references/shared-output-schema.md`: read to format output fields

## Output

Return using the shared output schema. Include:

- `facts_accepted`: usable expense facts the skill relied on
- `mappings_proposed`: use entries such as likely include as routine operating expense, include with caution, exclude_or_clarify, carry_to_other_field, needs_manual_review; use broad groupings consistent with repo standards
- `flags`: use `missing_support`, `mapping_uncertain`, `possible_personal_component`, `possible_capital_item`, `possible_duplication` where applicable
- `open_questions`: only questions needed to resolve meaningful uncertainty
- `status`: one of `ready_for_entry`, `clarification_required`, `incomplete`, `cpa_review_recommended`, `not_applicable`
- `client_safe_summary`: plain language, short and practical

Also include a routine operating expense mapping grouped into:

- likely included routine operating expenses (show category label, representative vendor or item, amount if known, support strength, confidence level)
- excluded or separately reviewed amounts
- unclear or mixed-use amounts

## Status Guidance

- `ready_for_entry`: likely routine operating expenses are sufficiently organized for downstream summary use
- `clarification_required`: routine expenses are mostly identified but support or classification is incomplete
- `cpa_review_recommended`: file includes material mixed-use, unclear categorization, or possible misgrouping
- `incomplete`: major routine expense support is still missing
- `not_applicable`: routine operating expense review does not appear relevant from the facts provided

Do not use `ready_for_entry` if routine operating expenses still depend on unsupported explanations or if several items may actually belong in other categories.

## Validation

- Every candidate expense is mapped or explicitly routed to another skill.
- Each mapping entry has a support strength and confidence level.
- Internet or phone expenses are flagged if mixed-use is possible.
- At least one downstream skill is identified in routing.
- `status` is one of the five standard values.
- `client_safe_summary` is present and contains no tax advice.
