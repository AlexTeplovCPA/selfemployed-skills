# CLAUDE.md — it-contractors-skills

AI workflow skills for Canadian IT contractors preparing for tax filing or CPA review.
Built by Alex Teplov, CPA. Canadian tax domain. No scripts. No MCP tools. Document-first workflows.

---

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
```

Numeric folder prefixes enforce workflow order in GitHub's alphabetical display. The `name:` field in YAML frontmatter uses the unprefixed gerund name (e.g., `classifying-expenses`, not `03-classifying-expenses`).

Use `references/` subfolder only if SKILL.md body exceeds 300 lines. Keep references one level deep from SKILL.md.

---

## Skill Authoring Rules

Every SKILL.md in this repository must follow all rules below without exception. Apply them when creating new skills and when editing existing ones.

### Naming

Gerund form, kebab-case only. No spaces, no capitals, no underscores.

Correct: `identifying-income-sources`, `checking-gst-hst`, `classifying-expenses`
Wrong: `identify-income-sources`, `check_gst_hst`, `ClassifyExpenses`

Folder name and the `name:` field in frontmatter must match exactly (unprefixed).

### YAML Frontmatter

Required fields: `name`, `description`, `metadata` (with `author`, `version`, `category`).

Rules for `name`:
- Maximum 64 characters
- Lowercase letters, numbers, and hyphens only
- No XML tags
- No reserved words: "anthropic", "claude"

Rules for `description`:
- Third person only. Never "I", "you", or "we"
- Wrapped in double quotes
- Under 1024 characters
- Includes what the skill does and when to trigger it. Both are required: Claude uses the description to select the right skill from potentially many available skills.
- Ends with trigger phrases in user voice after "Trigger on:"
- No XML tags

Other frontmatter rules:
- `version` starts at `1.0.0` for any skill committed to the repo
- `author` is always `Alex Teplov`
- `category` is always `tax-preparation`

Example (from `01-identifying-income-sources`):

```yaml
---
name: identifying-income-sources
description: "Identifies and documents all income sources for a self-employed Canadian for the current tax year. Use when a self-employed Canadian needs to organize income before tax filing or CPA review. Trigger on: T4A, T4, invoices, self-employment income, income summary, prepare for CPA, organize my income, what income do I need to report, I don't know if I have everything, I need to pull together my income."
metadata:
  author: Alex Teplov
  version: 1.0.0
  category: tax-preparation
---
```

### Body Structure

Every skill has these five sections in this order:

1. **Workflow position note** — which skills come before and after this one
2. **Core constraint** — accuracy and completeness disclaimer; state this to the user before starting
3. **Role** — no tax advice; redirect advisory questions and continue the workflow
4. **Workflow** — numbered steps with copy-paste progress checklist for skills with three or more steps
5. **Common mistakes / stop conditions / CPA value** — inline in the body

Horizontal rule (`---`) separates the YAML block from the body. One horizontal rule appears between the Core constraint and the Role section. No horizontal rule between Role and Workflow.

### Five Required Elements

Every skill must contain all five. No exceptions.

**1. Data handling notice**
Delivered before any document upload. Covers: no SIN or business number, commercial sensitivity, third-party storage risk. For document upload skills, add SIN redaction recommendation. Deliver as a blockquote.

Standard text (adapt minimally if needed):
> Do not type your SIN, business number, or client names into this conversation. Amounts and income types are all we need. If uploading photos of tax slips, cover or black out your SIN before photographing. Avoid sharing sensitive business details you would not be comfortable storing in a third-party system. Your inputs and uploaded documents may be stored by this AI tool according to its policies. Review those policies before proceeding if you have concerns.

**2. Accuracy statement**
State near the top that this workflow organizes information and does not verify completeness or accuracy.

**3. Progress checklist**
Copy-paste checklist at the start of the workflow section. Format:

```
Progress:
- [ ] Step 1: ...
- [ ] Step 2: ...
```

**4. Stop and refer conditions**
List specific scenarios that require a CPA before the user proceeds. For each condition, state exactly: "That is outside what this workflow covers. It is a question for a CPA before you file."

**5. CPA value section**
Final section. States what the CPA does with the output that this workflow cannot do. Delivered as a blockquote.

### Writing Rules

- Instructions are written to Claude, not to the user. Claude delivers content to the user conversationally.
- No em dashes anywhere in the file. Use colons, commas, or restructure the sentence.
- No hedging language.
- No boilerplate walls.
- No time-sensitive information (specific tax years, current CRA thresholds that change annually). Exception: thresholds that are stable reference points may be noted with a flag to verify.
- No explanatory text Claude does not need. Assume Claude knows standard accounting and tax concepts. Include only Canadian-specific context: CRA thresholds, Canadian slip types, province-specific rules.
- British spellings are not used. Canadian English follows American spelling conventions for these files.
- Use consistent terminology throughout. Choose one term and use it everywhere. Do not mix synonyms: pick "income" or "revenue", pick "upload" or "attach", pick "CRA" or "Canada Revenue Agency".
- Body target: under 300 lines. This is a house rule, stricter than the platform limit of 500 lines. Current skills run 140 to 165 lines. That is the correct range.
- Reference files longer than 100 lines must include a table of contents at the top. Claude may preview large files with partial reads; a table of contents ensures it can see the full scope before deciding what to load.

### Section Heading Format

Use `###` for step headings inside the Workflow section. Do not use bold paragraphs as pseudo-headings.

Correct:
```markdown
### Step 1: Open the Conversation
```

Wrong:
```markdown
**Step 1: Open the Conversation**
```

Use `---` horizontal rules to separate major sections as shown in the existing skills.

---

## Quality Checklist

Run this checklist before finalizing any SKILL.md. Fix every failure before committing.

- [ ] Name is gerund, kebab-case, matches folder name (unprefixed), under 64 characters, no reserved words
- [ ] Description is third person, wrapped in double quotes, under 1024 characters, includes both what the skill does and when to trigger it
- [ ] No XML tags in frontmatter
- [ ] Version is 1.0.0
- [ ] Author is Alex Teplov
- [ ] Category is tax-preparation
- [ ] No em dashes anywhere in the body
- [ ] Data handling notice present, delivered as blockquote before any upload step
- [ ] Accuracy statement present near the top
- [ ] Progress checklist present in correct format
- [ ] Stop conditions present, each followed by the standard redirect phrase
- [ ] CPA value section present as the final section, delivered as blockquote
- [ ] Step headings use `###`, not bold paragraphs
- [ ] `---` separators present between major sections
- [ ] Body is under 300 lines
- [ ] Reference files (if any) are one level deep from SKILL.md
- [ ] Reference files longer than 100 lines have a table of contents at the top
- [ ] All file paths use forward slashes
- [ ] Instructions written to Claude, not to the user

---

## Consistency Check Procedure

When asked to check consistency across skills, do the following for each SKILL.md in the repository:

1. Run the quality checklist above and list every failure by file and item
2. Check that workflow position notes are mutually consistent (if skill A says it comes before skill B, skill B should reference skill A as a predecessor)
3. Check that the data handling notice text is consistent across all skills that include it
4. Check that stop condition redirect phrases use the exact standard wording
5. Check that reference files longer than 100 lines have a table of contents
6. Report all findings in a table: File | Issue | Severity (must fix / minor)

Do not fix anything without confirming the change list with the user first.

---

## Repo-Wide Conventions

- All skills in this repository are scoped to IT contractors. Branching logic within a skill handles the T1/T2 split for sole proprietors and incorporated contractors rather than splitting into separate skills.
- Reference data stays separate from workflow logic. Vendor classification data lives in `references/vendor-categories.md`, not embedded in SKILL.md.
- Functional CRA categories surface in skills, not form line numbers.
- No README.md inside individual skill folders.
- No scripts anywhere in the repository.
- No MCP tool references anywhere in the repository.
- Keep all reference files one level deep from SKILL.md. Do not nest references inside references. Claude may use partial reads (`head -100`) when navigating deeply nested files and miss critical content.
- Use forward slashes in all file paths. Never backslashes.

---

## Git Conventions

Commit messages are plain English, imperative mood, under 72 characters.

Correct: `Add checking-gst-hst skill`, `Fix step heading format in classifying-expenses`
Wrong: `Updated the skill file`, `fixed stuff`

Stage only the files relevant to the change. Do not batch unrelated changes in one commit.

Before committing any SKILL.md, run the quality checklist. Do not commit a file with known checklist failures unless the user explicitly instructs it.

---

## Related Repositories

**cpa-skills** — practitioner-facing; CPAs and bookkeepers. Separate audience, separate tone.

Skills in this repository are client-facing. They prepare input for CPA review. They do not replace it.
