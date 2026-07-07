---
layout: page
title: "7. Evaluation and Validation"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 7. Evaluation and validation

Evaluation is where automated content analysis becomes social-scientific measurement. A high score on an artificial benchmark is insufficient if the model fails on the real corpus, the rare class, or the downstream inference.

## Quality criteria

| Criterion | Question | Evidence |
|---|---|---|
| Validity | Do predictions match the intended construct? | Gold-standard comparison, error analysis, construct discussion |
| Reliability | Are repeated runs stable? | Seed/run variation, prompt-run agreement |
| Replicability | Does the pipeline work on related data? | Outlet/time/platform/domain shift tests |
| Robustness | Do small parameter or prompt changes alter findings? | Prompt variants, thresholds, model variants |
| Reproducibility | Can the same analysis be rerun? | Code, environment, model versions, seeds, data splits |
| Feasibility | Are resources proportionate to the research goal? | Time, cost, hardware, annotation effort |

## Metrics

Report more than accuracy:

- **Confusion matrix**: shows systematic confusions.
- **Per-class precision and recall**: essential for minority classes.
- **Macro-F1**: gives rare classes equal weight.
- **Micro-F1 / accuracy**: useful only with distribution caveats.
- **MCC or Cohen’s κ**: useful complementary agreement-style measures.
- **Calibration / threshold curves**: useful for prevalence estimates.
- **Prevalence comparison**: predicted vs. human-labelled prevalence.

## Validation sets

Use multiple validation views:

| Validation set | Purpose | Warning sign |
|---|---|---|
| Development set | Prompt/model selection | High variance across runs |
| Balanced test set | Class separability | Good score but unrealistic prevalence |
| Realistic random test set | Corpus-level measurement | High false-positive share |
| Out-of-sample test set | Generalization | Performance collapse under domain shift |
| Edge-case set | Conceptual stress test | Model ignores codebook boundary rules |

## Error analysis

After quantitative evaluation, read examples. For each label, inspect:

- true positives;
- false positives;
- false negatives;
- high-confidence errors;
- disagreement between humans and model;
- disagreement between model runs.

Classify errors into conceptual ambiguity, missing context, source/genre shift, lexical shortcut, actor shortcut, negation/irony, parsing failure, and annotation error. This error typology should feed back into the codebook and model design.

## Downstream inference

When model predictions become variables in regressions, diversity indices, trend lines, or outlet comparisons, prediction error can bias substantive results. Validate the specific quantity of interest, not only the label. For example, a model with acceptable macro-F1 may still distort frame diversity if it overpredicts one rare frame.

## Minimum validation report

A publishable validation report should include:

1. Gold-data construction and coder process.
2. Final codebook version.
3. Train/dev/test split strategy.
4. Model and prompt versions.
5. Overall and per-class metrics.
6. Confusion matrix.
7. Prevalence comparison.
8. Out-of-sample results if available.
9. Error-analysis summary.
10. Limitations and allowed uses of predictions.
