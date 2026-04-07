# CLAUDE.md — it-contractors-skills

Client-facing AI workflow skills for Canadian IT contractors preparing for CPA review.

This repository contains preparation workflows, not filing workflows. Skills in this repository help users gather documents, organize records, identify gaps, and prepare cleaner CPA handoff packages. They do not replace CPA judgment, provide tax advice, or determine final filing positions.

Built by Alex Teplov, CPA.

---

## Repository Scope

This repository is scoped to **Canadian IT contractors** only.

Use this repository for workflows involving:

- document collection before CPA review
- income organization
- expense classification
- GST/HST information gathering
- home office and vehicle support collection
- shareholder and owner-compensation support collection
- T1 and T2 package preparation
- readiness checks before CPA intake

Do not use this repository for:

- generic self-employed workflows not specific to IT contractors
- e-commerce seller workflows
- accountant-facing internal review workflows
- technical tax analysis intended for practitioner use only

Those belong in other repositories.

---

## Current Repository Structure

Use this structure unless the user explicitly wants a different layout.

```text
skills/
  collecting-tax-documents/
    SKILL.md
    agents/
      openai.yaml
    references/
      checklist-t1.md
      checklist-t2.md

  normalizing-uploads/
    SKILL.md
    agents/
      openai.yaml

  identifying-income-sources/
    SKILL.md
    agents/
      openai.yaml

  checking-gst-hst/
    SKILL.md
    agents/
      openai.yaml

  collecting-foreign-income-support/
    SKILL.md
    agents/
      openai.yaml

  reconciling-income-to-deposits/
    SKILL.md
    agents/
      openai.yaml

  classifying-expenses/
    SKILL.md
    agents/
      openai.yaml
    references/
      vendor-categories.md

  collecting-home-office-support/
    SKILL.md
    agents/
      openai.yaml

  collecting-vehicle-support/
    SKILL.md
    agents/
      openai.yaml

  screening-psb-risk/
    SKILL.md
    agents/
      openai.yaml

  reviewing-shareholder-transactions/
    SKILL.md
    agents/
      openai.yaml

  collecting-owner-compensation-records/
    SKILL.md
    agents/
      openai.yaml

  preparing-cpa-t1-package/
    SKILL.md
    agents/
      openai.yaml

  preparing-cpa-t2-package/
    SKILL.md
    agents/
      openai.yaml

  validating-readiness/
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

Use `skills/` as the root for all actual skills. Do not create empty placeholder skill folders just to show roadmap ideas. Planned skills belong in the README until there is real content.

---

## Skill Naming Rules

All skill names in this repository use:

- gerund form where natural
- kebab-case only
- lowercase letters, numbers, and hyphens only
- no repo audience suffix in the skill name, because the repo scope already defines the audience

Correct examples:

- `collecting-tax-documents`
- `identifying-income-sources`
- `checking-gst-hst`
- `classifying-expenses`
- `preparing-cpa-t1-package`
- `reviewing-shareholder-transactions`

Avoid:

- `collect-tax-documents`
- `check_gst_hst`
- `ClassifyingExpenses`
- `collecting-tax-documents-it-contractors`

Within this repository, keep these aligned:

- skill folder name
- `name:` field in `SKILL.md`
- skill name shown in README
- any references to the skill in docs

One skill should have one name everywhere.

---

## Frontmatter Rules

Every `SKILL.md` should use minimal YAML frontmatter.

Required fields:

- `name`
- `description`

Do not add extra frontmatter fields unless there is a strong reason and the user explicitly wants them.

Use this pattern:

```yaml
---
name: collecting-tax-documents
description: collects and organizes the tax documents a canadian it contractor needs before cpa review. use when preparing for tax filing, gathering records for an accountant, or identifying missing documents for a t1 or t2 package.
---
```

### Frontmatter Rules

#### `name`
- must match the skill folder name exactly
- maximum 64 characters
- lowercase letters, numbers, and hyphens only
- no spaces
- no underscores
- no reserved words such as `anthropic` or `claude`

#### `description`
- written in third person
- lower-case preferred for consistency
- under 1024 characters
- includes both:
  - what the skill does
  - when to use it
- no XML tags
- do not stuff it with long trigger lists unless truly needed

The description is for discovery. Make it specific enough that the right skill can be selected without turning it into keyword spam.

---

## Skill Body Structure

Keep `SKILL.md` concise and workflow-first.

Default structure:

1. Title
2. Core rules or constraints
3. Workflow
4. Required output
5. Stop and refer conditions
6. Optional references section

Use this as a default pattern, not a rigid law. Some skills may need small variations.

### Recommended Shape

```markdown
# Collecting Tax Documents

## Core Rules

- organize information only
- do not provide tax advice
- do not request or repeat SINs, business numbers, client names, or account numbers
- clearly separate confirmed items, missing items, and CPA questions

## Workflow

### Step 1: ...
### Step 2: ...
### Step 3: ...

## Required Output

[template]

## Stop and Refer

[conditions]

## References

See [references/checklist-t1.md](references/checklist-t1.md).
```

---

## Required Content Rules

### 1. Data handling notice
If the workflow involves user uploads, tax slips, or sensitive business information, include a data handling notice near the start.

Use a blockquote.

Standard baseline text:

> Do not type your SIN, business number, account numbers, or client names into this conversation. Use general descriptions and rounded amounts where possible. If uploading tax slips or screenshots, redact sensitive identifiers first. Avoid sharing sensitive information you would not be comfortable storing in a third-party system.

Adjust only when needed.

### 2. Accuracy boundary
Near the top, state that the workflow organizes information and does not verify completeness or accuracy unless that skill genuinely includes a verification mechanism.

### 3. No tax advice
Where the workflow touches tax treatment, deductibility, filing positions, or compliance judgment, explicitly instruct the model to organize and flag, not advise.

### 4. Stop and refer conditions
Where relevant, list situations that should be escalated to a CPA before filing or further action.

Preferred standard phrase:

> That is outside what this workflow covers. It is a question for a CPA before you file.

### 5. Required output
Most skills in this repository should define a clear final output:
- checklist
- summary table
- gap list
- readiness result
- CPA handoff summary

Do not leave the output vague.

---

## Writing Rules

Write instructions to the model, not to the end user.

Use:

- short sections
- direct wording
- consistent terminology
- american spelling conventions for consistency across the repo
- no em dashes

Avoid:

- long conceptual explanations
- generic tax education the model already knows
- legalistic boilerplate walls
- speculative language
- overly rigid filler sections that do not help execution

Prefer:

- “organize”
- “flag”
- “collect”
- “review”
- “prepare”

Be consistent. Do not switch between synonyms unnecessarily.

Examples:
- pick `income` or `revenue` and use it consistently in a skill
- pick `upload` or `attach` and use it consistently
- pick `CRA` or `Canada Revenue Agency` and stay consistent

---

## Progressive Disclosure Rules

Keep `SKILL.md` compact. Treat it as the control layer.

### House rules
- target under 300 lines for `SKILL.md`
- move long checklists, examples, or reference material into `references/`
- keep references one level deep from `SKILL.md`
- do not nest references inside references
- use forward slashes in all paths

If a reference file is longer than 100 lines, add a table of contents near the top.

Good:

- `references/checklist-t1.md`
- `references/checklist-t2.md`
- `references/vendor-categories.md`

Avoid:
- deeply nested reference trees
- massive SKILL bodies
- duplicated checklist content across multiple skills

---

## Current Repo Conventions

### No scripts by default
This repository currently favors instruction-first skills and reference files.

Do not add `scripts/` unless:
- the task is fragile enough to justify code
- the user specifically wants executable support
- there is a clear deterministic operation worth scripting

### No MCP assumptions
Do not assume MCP tools, private connectors, or special runtime access inside this repository unless the user explicitly changes the repo direction.

### No skill-local README files
Do not add `README.md` inside each skill folder unless the user explicitly asks for that structure.

### Client-facing tone
Skills in this repository are client-facing. They should feel:
- structured
- practical
- bounded
- reassuring

They should not sound:
- like internal accountant workflow notes
- like marketing copy
- like technical specs for engineers

---

## Development-State Policy

When developing the repo:

### Show in the repo
- completed skills
- real in-progress skills with meaningful `SKILL.md` content
- real reference files
- README roadmap

### Do not show in the repo
- large trees of empty placeholder skill folders
- fake “finished” skills with no substance
- speculative structure beyond what is useful

Use these status labels in README where helpful:
- Active
- In progress
- Planned

A skill folder should exist only when there is real content.

---

## Quality Checklist

Before finalizing any `SKILL.md`, check all of the following:

- [ ] folder name matches `name:` exactly
- [ ] name is clear, gerund-based where natural, and kebab-case
- [ ] description explains what the skill does and when to use it
- [ ] frontmatter includes only the fields actually needed
- [ ] no em dashes anywhere
- [ ] instructions are written to the model
- [ ] data handling notice is present where sensitive info may appear
- [ ] accuracy boundary is stated near the top
- [ ] output format is clearly defined
- [ ] stop-and-refer conditions are present where relevant
- [ ] references are one level deep
- [ ] all file paths use forward slashes
- [ ] `SKILL.md` stays concise

Do not commit a skill with known checklist failures unless the user explicitly asks for a draft state.

---

## Consistency Check Procedure

When asked to check consistency across this repo:

1. compare folder names, `name:` fields, and README references
2. flag any naming mismatches
3. check that descriptions follow the same style and purpose pattern
4. check that data-handling and no-advice boundaries are consistent where relevant
5. check that reference files are one level deep
6. report findings in a table:

`File | Issue | Severity`

Severity options:
- must fix
- should fix
- minor

Do not silently rewrite the repo when asked only for a consistency review.

---

## Git Conventions

Commit messages should be:
- plain English
- imperative mood
- under 72 characters when possible

Good:
- `Add collecting-tax-documents skill`
- `Refine gst hst wording in checking-gst-hst`
- `Move checklists into references folder`

Avoid:
- `updated stuff`
- `fixed files`
- `misc changes`

Stage only related files together. Do not bundle unrelated repo cleanup into the same commit.

---

## Related Repositories

- `cpa-skills` — practitioner-facing workflows for CPAs and bookkeepers
- `ecommerce-skills` — client-facing workflows for Canadian e-commerce sellers

This repository remains client-facing and IT-contractor-specific. It prepares input for CPA review. It does not replace it.
