# it-contractors-skills

AI workflow skills for IT contractors preparing for tax filing or CPA review.

These skills are built from real practice with IT contractors and consultants in Canada. Each skill runs as a structured conversation: the AI asks questions, reads uploaded documents, fills gaps, and produces organized output ready for a CPA to review.

These skills are a domain-specific extension of cpa-skills.

## Who This Is For

IT contractors and consultants in Canada who want to organize their tax information before working with a CPA. The skills handle the preparation layer. The CPA handles review, classification, and filing.

Practitioners working with IT contractor clients who want a consistent intake workflow before the engagement begins.

These skills are not a substitute for professional tax advice or CPA review. They organize what you have. A CPA validates and completes it.

## Disclosure

These workflows organize information provided by the user. They do not verify completeness or accuracy, provide tax advice, or create a professional relationship of any kind. Use of these skills does not replace a review by a qualified CPA before filing.

## How the Skills Work Together

The skills form a preparation sequence. Run them in order, or run the ones relevant to your situation.

`00-collecting-tax-documents` is the starting point. It delivers a complete document checklist before anything else begins, with branching for sole proprietors (T1) and incorporated contractors (T1 and T2). The other skills assume document collection is complete or in progress.

`01-identifying-income-sources` organizes all income sources for the tax year. Run after documents are collected.

`02-checking-gst-hst` checks registration status, threshold, and remittance. Run early if you are unsure about registration status or have crossed CAD 30,000 in revenue. Do not leave this for last.

`03-classifying-expenses` classifies expense transactions into CRA-aligned categories with branching logic for sole proprietors and incorporated contractors. Run after the income picture is clear.

`04-preparing-cpa-t1-package` pulls everything together into a personal T1 handoff package ready to send to a CPA. Run after the prior steps are complete or partially complete.

`05-preparing-cpa-t2-package` covers the corporate side for incorporated owner-managers. Run alongside `04-preparing-cpa-t1-package` when both a T1 and a T2 are being filed in the same engagement.

## Skills

| Skill | What It Does | Status |
|---|---|---|
| 00-collecting-tax-documents | Delivers a complete document checklist with T1 and T2 branches | Available |
| 01-identifying-income-sources | Identifies and documents all income sources for the tax year | Available |
| 02-checking-gst-hst | Checks registration status, threshold, and remittance | Available |
| 03-classifying-expenses | Classifies IT contractor expenses with CRA-aligned categories | Available |
| 04-preparing-cpa-t1-package | Builds a personal T1 handoff package ready to send to a CPA | Available |
| 05-preparing-cpa-t2-package | Builds a corporate T2 handoff package for incorporated owner-managers | Available |

## Installation

**Claude (claude.ai):**

1. Download or clone this repository
2. Zip the skill folder you want to install
3. Go to Settings > Capabilities > Skills > Upload skill

**Claude Code:** Place the skill folder in `~/.claude/skills/`

**OpenAI Codex:** Place the skill folder in `~/.agents/skills/`

**Google Gemini CLI:** Place the skill folder in `~/.gemini/skills/` or `~/.agents/skills/`

These skills follow the open Agent Skills standard and are tested primarily on Claude. Results may vary on other tools.

## How to Use a Skill

Once installed, the agent discovers and loads the relevant skill automatically based on your request. You do not need to invoke it manually.

Example:

```
request → "I need to collect my documents for my tax return"
agent loads → 00-collecting-tax-documents
output → complete document checklist with gap summary ready for CPA review
```

## Repository Structure

```
00-collecting-tax-documents/
   SKILL.md
   references/
      checklist-t1.md
      checklist-t2.md

01-identifying-income-sources/
   SKILL.md

02-checking-gst-hst/
   SKILL.md

03-classifying-expenses/
   SKILL.md
   references/
      vendor-categories.md

04-preparing-cpa-t1-package/
   SKILL.md

05-preparing-cpa-t2-package/
   SKILL.md

examples/
   income-summary.csv
   expense-log.csv
   gst-hst-records.csv
```

## Related Repositories

**cpa-skills** AI workflow skills for CPAs and bookkeepers. Practitioner-facing workflows for bookkeeping review, T1, T2, client communication, and CRA research.

## About

Built by [Alex Teplov, CPA](https://www.linkedin.com/in/alex-teplov/).

I run two specialized accounting practices in Canada and build these workflows from operational problems encountered in real practice.
