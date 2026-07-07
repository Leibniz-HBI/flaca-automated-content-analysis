---
layout: page
title: "3. Data Preparation"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 3. Data preparation

Data preparation determines what the model can learn and what the validation result means. In FLACA-style communication research, preprocessing is not a neutral technical step; it operationalizes the unit of analysis and the context available to the model.

## Corpus construction

Document the following:

| Component | Minimum documentation |
|---|---|
| Source universe | Databases, outlets/platforms, time period, language, inclusion/exclusion rules |
| Query/search strategy | Search strings, API endpoints, archive filters, deduplication rules |
| Legal/ethical constraints | Copyright, platform terms, personal data, sensitive data, data minimization |
| Text extraction | OCR/parsing tool, cleaning steps, error checks, handling of paywalls or malformed text |
| Metadata | Date, source, author/actor if available, document ID, section, platform fields |

## Unitization and context

Many communication-science categories do not live neatly at one level. A sentence may express the claim, but the stance target may be in the previous sentence. A paragraph may contain multiple positions. An article may be needed to interpret source attribution.

Use a table like this in the project repository:

| Field | Meaning | Example |
|---|---|---|
| `doc_id` | Stable document identifier | `zeit_2022_05_08_001` |
| `unit_id` | Stable unit identifier | `zeit_2022_05_08_001_s012` |
| `target_text` | Unit to classify | One sentence or paragraph |
| `context_before` | Preceding context | Two sentences |
| `context_after` | Following context | Two sentences |
| `source` | Outlet/platform | Newspaper or account |
| `date` | Publication date | ISO date |
| `split` | train/dev/test/final | Assigned once and frozen |

## Splitting data

Use at least three splits:

- **Training set:** labels used for supervised learning or prompt example selection.
- **Development set:** labels used to tune prompts, thresholds, hyperparameters, or model choice.
- **Final test set:** untouched labels used for the final validity claim.

For communication-science inference, add an **out-of-sample validation set** when possible. Examples: different outlets, regions, time periods, platforms, or genres.

## Leakage risks

Avoid splitting data at the sentence level when sentences from the same article can appear in both train and test. For article corpora, split by document or higher-level cluster. For social media threads, split by thread or author when author leakage is plausible.

## Handling imbalance

Do not hide real imbalance. You may rebalance training data to help the model learn minority classes, but final validation should include a realistic distribution or explicitly report how prevalence differs from the target corpus.

Recommended practice:

1. Estimate label prevalence in a random sample.
2. Create a balanced or enriched development set for learning.
3. Keep a realistic validation set for prevalence-sensitive claims.
4. Report both class-specific performance and expected prevalence distortion.
