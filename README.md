# selfemployed-skills

AI workflow skills for self-employed Canadians preparing for tax filing or CPA review.

These skills are built from real practice with IT contractors, mortgage agents, trades contractors, and real estate professionals in Canada. Each skill runs as a structured conversation: the AI asks questions, reads uploaded documents, fills gaps, and produces organized output ready for a CPA to review.

These skills are a domain-specific extension of [cpa-skills](https://github.com/alexteplovcpa/cpa-skills).

---

## Who This Is For

**Self-employed Canadians** who want to organize their tax information before working with a CPA. The skills handle the preparation layer. The CPA handles review, classification, and filing.

**Practitioners** working with self-employed clients who want a consistent intake workflow before the engagement begins.

These skills are not a substitute for professional tax advice or CPA review. They organize what you have. A CPA validates and completes it.

---

## Disclosure

These workflows organize information provided by the user. They do not verify completeness or accuracy, provide tax advice, or create a professional relationship of any kind. Use of these skills does not replace a review by a qualified CPA before filing.

---

## How the Skills Work Together

The four skills in this repository form a preparation sequence. Run them in order, or run the ones relevant to your situation.

`identify-income-sources` is the starting point. The other skills assume it is complete or in progress.

Run `check-gst-hst` early if you are unsure about your registration status or have crossed CAD 30,000 in revenue. Do not leave this for last.

`classify-expenses` assumes you have a clear picture of your income sources.

`cpa-review-prep` pulls everything together into a package ready to send to a CPA. It assumes the prior steps are complete or partially complete.

---

## Skills

### General Skills

These skills apply to any self-employed Canadian regardless of profession.

| Skill | What It Does | Status |
|---|---|---|
| `identify-income-sources` | Identifies and documents all income sources for the tax year | Available |
| `check-gst-hst` | Checks registration status, threshold, and remittance | Available |
| `cpa-review-prep` | Builds a structured package ready to send to a CPA | Available |

### IT Contractor Skills

Profession-specific skills for IT contractors and consultants.

| Skill | What It Does | Status |
|---|---|---|
| `it-contractor/classify-expenses` | Classifies IT contractor expenses with CRA-aligned categories | Available |

Additional profession-specific skills for mortgage agents, trades contractors, and real estate professionals are planned for future releases.

---

## Installation

**Claude (claude.ai):**
1. Download or clone this repository
2. Zip the skill folder you want to install
3. Go to Settings > Capabilities > Skills > Upload skill

**Claude Code:**
Place the skill folder in `~/.claude/skills/`

**OpenAI Codex:**
Place the skill folder in `~/.agents/skills/`

**Google Gemini CLI:**
Place the skill folder in `~/.gemini/skills/` or `~/.agents/skills/`

These skills follow the open [Agent Skills standard](https://agentskills.io) and are tested primarily on Claude. Results may vary on other tools.

---

## How to Use a Skill

Once installed, the agent discovers and loads the relevant skill automatically based on your request. You do not need to invoke it manually.

Example:

```text
request: "I need to organize my income for my tax return"
agent loads: identify-income-sources
output: structured income summary ready for CPA review
```

---

## Repository Structure

```text
identify-income-sources/
   SKILL.md

check-gst-hst/
   SKILL.md

cpa-review-prep/
   SKILL.md

it-contractor/
   classify-expenses/
      SKILL.md

examples/
   income-summary.csv
   expense-log.csv
   gst-hst-records.csv
```

---

## Related Repositories

**[cpa-skills](https://github.com/alexteplovcpa/cpa-skills)**
AI workflow skills for CPAs and bookkeepers. Practitioner-facing workflows for bookkeeping review, T1, T2, client communication, and CRA research.

**[ecommerce-skills](https://github.com/alexteplovcpa/ecommerce-skills)**
Specialized workflows for Canadian e-commerce sellers.

---

## About

Built by [Alex Teplov, CPA](https://www.linkedin.com/in/alex-teplov/).

I run two specialized accounting practices in Canada and build these workflows from operational problems encountered in real practice.
