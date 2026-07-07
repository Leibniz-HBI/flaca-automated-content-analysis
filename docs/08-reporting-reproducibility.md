---
layout: page
title: "8. Reporting and Reproducibility"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 8. Reporting and reproducibility

A reader should be able to understand exactly how the measurement was produced, even when data cannot be fully shared. Automated content analysis is reproducible only when the research object, codebook, model, environment, and validation decisions are documented together.

## Methods appendix template

Use these headings:

1. **Research goal and construct**
2. **Corpus and sampling**
3. **Coding unit and context window**
4. **Codebook and annotation process**
5. **Gold-standard data and reliability/adjudication**
6. **Model families considered**
7. **Prompt or training setup**
8. **Validation design**
9. **Final prediction pipeline**
10. **Uncertainty, errors, and limitations**
11. **Data/code availability**
12. **Ethical/legal constraints**

## Reproducibility bundle

Publish, where legally possible:

| Item | Why it matters |
|---|---|
| Codebook version | Defines the construct |
| Annotation guidelines | Explains human coding decisions |
| Prompt versions | Required for LLM replication |
| Training scripts | Required for supervised replication |
| Environment file | Locks libraries and runtimes |
| Model card | Identifies model versions and limitations |
| Data-split IDs | Prevents silent resplitting |
| Validation labels | Enables independent metric calculation |
| Raw predictions | Enables error analysis and downstream correction |
| Analysis notebooks | Documents aggregation and substantive inference |

If copyrighted or platform-restricted texts cannot be shared, share document IDs, query logic, synthetic examples, code, prompts, and metadata schemas.

## Reporting LLM use

For every LLM result, report:

- provider and model ID;
- date of execution;
- full system and user prompts;
- decoding parameters;
- number of runs;
- output parser;
- examples used in prompts;
- prompt-stability checks;
- validation data and results;
- any manual adjudication.

## Reporting fine-tuning

For every fine-tuned model, report:

- base model and tokenizer;
- training data size by class;
- sampling/rebalancing;
- hyperparameters;
- seeds and repeated runs;
- hardware and runtime;
- validation metrics;
- where the model or adapter can be accessed.

## Ethical and legal notes

Communication-science corpora often contain copyrighted news, personal social-media data, or politically sensitive speech. Data minimization and privacy-by-design matter. For sensitive texts, prefer local or institutionally controlled models unless the legal basis for external API processing is clear.

## Interpretation discipline

Do not write “the model found” when the better statement is “the model classified according to our operationalization.” Automated labels are measurements under assumptions, not direct observations of social meaning.
