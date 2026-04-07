# it-contractors-skills

Tax preparation workflow skills for Canadian IT contractors.

This repository contains structured AI workflows designed to help Canadian IT contractors prepare their tax information before working with a CPA. Each workflow runs as a guided process: collecting documents, organizing income, classifying expenses, reviewing GST/HST, and assembling a CPA-ready package.

These workflows are built from real accounting practice and are intended as a starting point for reusable, profession-grounded workflow standards.

## Who This Is For

- Canadian IT contractors preparing for tax filing or CPA review
- Sole proprietor and incorporated IT contractors managing T1 and T2 requirements
- Practitioners who want a consistent intake workflow for IT contractor clients

These workflows handle preparation. A CPA reviews, validates, and files.

## What These Skills Do

The workflows:

- guide document collection
- identify income sources
- classify expenses into CRA-aligned categories
- organize GST/HST information
- assemble CPA-ready T1 and T2 packages

They do not:

- provide tax advice
- verify completeness or accuracy
- replace CPA review

## Workflow Sequence

The skills follow a preparation sequence. Run them in order or use individual steps as needed.

- `collecting-tax-documents` — starting point, full checklist
- `identifying-income-sources` — builds income summary
- `checking-gst-hst` — organizes GST/HST position
- `classifying-expenses` — categorizes transactions
- `preparing-cpa-t1-package` — builds personal tax package
- `preparing-cpa-t2-package` — builds corporate tax package

## Current Repository Structure

```text
collecting-tax-documents/
   SKILL.md
   references/
      checklist-t1.md
      checklist-t2.md

identifying-income-sources/
   SKILL.md

checking-gst-hst/
   SKILL.md

classifying-expenses/
   SKILL.md
   references/
      vendor-categories.md

preparing-cpa-t1-package/
   SKILL.md

preparing-cpa-t2-package/
   SKILL.md

examples/
   income-summary.csv
   expense-log.csv
   gst-hst-records.csv
```

## How to Use

Once installed in a compatible AI agent, the relevant workflow is automatically selected based on your request.

Example:

```text
request → "I need to prepare my documents for my accountant"
agent loads → collecting-tax-documents
output → structured checklist and gap summary
```

You do not need to manually select a skill.

## Disclosure

These workflows organize information provided by the user. They do not verify completeness or accuracy, provide tax advice, or create a professional relationship of any kind.

Use of these workflows does not replace review by a qualified CPA before filing.

## Related Repositories

[**cpa-skills**](https://github.com/alexteplovcpa/cpa-skills)  
Practice-tested AI workflow skills for CPAs and bookkeepers.

[**ecommerce-skills**](https://github.com/alexteplovcpa/ecommerce-skills)  
Accounting workflows for Canadian e-commerce sellers.

## License

This repository is licensed under the MIT License.

These workflows are built from real accounting practice. If you adapt or use them, attribution is appreciated.

See the [LICENSE](LICENSE) file for details.

## About

Built by [Alex Teplov, CPA](https://www.linkedin.com/in/alex-teplov/).

I run specialized accounting practices in Canada focused on IT contractors and e-commerce sellers, and build these workflows from real operational bottlenecks encountered in practice.