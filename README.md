# it-contractors-skills

Client-facing AI workflow skills for Canadian IT contractors and consultants preparing for CPA review.

This repository is designed for the preparation layer before professional review. The skills help users gather documents, organize income and expenses, identify missing items, surface higher-risk issues for CPA attention, and arrive at the CPA review stage with a cleaner and more structured file.

These workflows are built from real accounting work with Canadian IT contractors. They do not replace CPA judgment, tax advice, or filing.

## Repository Purpose

This repository is public and client-facing.

Its role is to help IT contractors and consultants prepare their records before working with a CPA. The focus is on structured intake, document organization, issue spotting, and handoff preparation.

This is separate from [**cpa-skills**](https://github.com/alexteplovcpa/cpa-skills), which is practitioner-facing and designed for accountants and bookkeepers.

## Who This Is For

This repository is for:

- Canadian IT contractors and consultants who want to organize tax and bookkeeping information before CPA review
- incorporated and sole proprietor contractors who need a cleaner preparation workflow
- practitioners who want a more consistent intake structure for IT contractor clients

These skills organize what the user provides. A CPA reviews the file, confirms tax treatment, identifies what is missing, and completes the return.

## Disclosure

These workflows organize information provided by the user. They do not verify completeness or accuracy, provide tax advice, determine final tax treatment, or create a professional relationship of any kind. Use of these skills does not replace review by a qualified CPA before filing.

## How the Repository Is Structured

The repository is organized by workflow stage.

### 1. Intake
These skills help the user gather records and clean up the initial file before deeper review begins.

### 2. Income and Compliance
These skills organize income records, GST/HST context, and foreign client support.

### 3. Expense and Support
These skills classify expenses and collect support for common deduction areas such as home office and vehicle use.

### 4. Incorporated Contractor Risk Areas
These skills focus on the issues that commonly require closer CPA attention in incorporated contractor files, including PSB screening, shareholder transactions, and owner compensation records.

### 5. Handoff
These skills assemble CPA-ready summaries and determine whether the file is ready for intake.

## Current Skill Map

### Intake

- `collecting-tax-documents-it-contractors`
- `normalizing-it-contractor-uploads`

### Income and Compliance

- `identifying-income-sources-it-contractors`
- `checking-contractor-gst-hst-threshold-support`
- `collecting-foreign-client-income-support`
- `reconciling-contractor-income-to-deposits`

### Expense and Support

- `classifying-expenses-it-contractors`
- `collecting-home-office-support-it-contractors`
- `collecting-vehicle-support-it-contractors`

### Incorporated Contractor Risk Areas

- `screening-psb-risk`
- `reviewing-shareholder-transactions-it-contractors`
- `collecting-owner-compensation-records`

### Handoff

- `preparing-cpa-t1-package-it-contractors`
- `preparing-cpa-t2-package-it-contractors`
- `validating-it-contractor-readiness`

## What the Skills Are Designed to Do

These skills are designed to:

- collect and organize tax and bookkeeping records
- turn messy client information into structured summaries
- identify missing documents and unresolved items
- flag higher-risk issues for CPA review
- improve the quality of the handoff into professional review

They are not designed to:

- replace a CPA
- determine final filing positions
- provide legal or tax advice
- file returns
- resolve technical tax issues without review

## Planned Repository Structure

```text
skills/
  collecting-tax-documents-it-contractors/
    SKILL.md
    agents/
      openai.yaml
    references/
      checklist-t1.md
      checklist-t2.md

  normalizing-it-contractor-uploads/
    SKILL.md
    agents/
      openai.yaml

  identifying-income-sources-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  checking-contractor-gst-hst-threshold-support/
    SKILL.md
    agents/
      openai.yaml

  collecting-foreign-client-income-support/
    SKILL.md
    agents/
      openai.yaml

  reconciling-contractor-income-to-deposits/
    SKILL.md
    agents/
      openai.yaml

  classifying-expenses-it-contractors/
    SKILL.md
    agents/
      openai.yaml
    references/
      vendor-categories.md

  collecting-home-office-support-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  collecting-vehicle-support-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  screening-psb-risk/
    SKILL.md
    agents/
      openai.yaml

  reviewing-shareholder-transactions-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  collecting-owner-compensation-records/
    SKILL.md
    agents/
      openai.yaml

  preparing-cpa-t1-package-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  preparing-cpa-t2-package-it-contractors/
    SKILL.md
    agents/
      openai.yaml

  validating-it-contractor-readiness/
    SKILL.md
    agents/
      openai.yaml

docs/
  repo-scope.md
  writing-rules.md

examples/
  income-summary.csv
  expense-log.csv
  gst-hst-records.csv
  t1-package/
  t2-package/
```

## Installation

### Claude (claude.ai)
1. Download or clone this repository
2. Zip the individual skill folder you want to install
3. Go to Settings → Capabilities → Skills
4. Upload the skill ZIP

### Claude Code
Place the skill folder in:

```text
~/.claude/skills/
```

### OpenAI Codex
Place the skill folder in:

```text
~/.agents/skills/
```

### Google Gemini CLI
Place the skill folder in one of:

```text
~/.gemini/skills/
~/.agents/skills/
```

These skills follow an open agent-skill style structure and are being developed primarily around Claude-style workflows. Behavior may vary across tools.

## How to Use the Repository

A user does not need to run every skill.

A typical path might look like this:

1. collect documents  
2. normalize uploads  
3. identify income sources  
4. review GST/HST context if relevant  
5. classify expenses  
6. collect additional support for home office, vehicle, or foreign client income if needed  
7. review incorporated contractor risk areas where relevant  
8. prepare the T1 package, T2 package, or both  
9. validate readiness before CPA intake  

## Example Workflow

```text
request: I need to get my IT contractor tax information ready for my CPA
skills used:
- collecting-tax-documents-it-contractors
- identifying-income-sources-it-contractors
- classifying-expenses-it-contractors
- preparing-cpa-t1-package-it-contractors

output:
- organized summaries
- missing item list
- CPA question list
- handoff package for review
```

## Related Repositories

- [**cpa-skills**](https://github.com/alexteplovcpa/cpa-skills) — Practice-tested AI workflow skills for CPAs and bookkeepers.
- [**ecommerce-skills**](https://github.com/alexteplovcpa/ecommerce-skills) — Accounting workflows for Canadian e-commerce sellers.

## About

Built by [Alex Teplov, CPA](https://www.linkedin.com/in/alex-teplov/).

This repository is part of a broader effort to build practical, profession-grounded AI workflow libraries for accounting work in Canada, with separate repositories for client-facing preparation workflows and practitioner-facing CPA workflows.
