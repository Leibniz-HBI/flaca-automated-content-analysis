---
layout: page
title: "Checklists"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# Checklists

## Project-start checklist

- [ ] Research question identifies a concrete quantity of interest.
- [ ] Construct is defined in theory-language and coding-language.
- [ ] Coding unit is justified.
- [ ] Context window is specified.
- [ ] Corpus universe and sampling frame are documented.
- [ ] Legal/ethical constraints are checked.
- [ ] Expected class prevalence is estimated.
- [ ] Validation plan is written before scaling.

## Codebook checklist

- [ ] Mutually exclusive labels or explicit multilabel rules.
- [ ] Inclusion and exclusion rules.
- [ ] Borderline examples.
- [ ] Negative examples.
- [ ] Decision hierarchy.
- [ ] Context-use rule.
- [ ] Version number and changelog.
- [ ] Prompt-adapted version if using LLMs.

## LLM prompting checklist

- [ ] Prompt generated from frozen codebook.
- [ ] Output format constrained.
- [ ] Temperature and model version recorded.
- [ ] Prompt variants tested.
- [ ] At least two runs assessed for stability.
- [ ] Parser failures logged.
- [ ] Final test set not used for prompt tuning.
- [ ] Human validation reported.

## Fine-tuning checklist

- [ ] Train/dev/test split frozen.
- [ ] Document-level leakage prevented.
- [ ] Label distribution reported.
- [ ] Baseline model evaluated.
- [ ] Multiple seeds or runs used.
- [ ] Per-class precision/recall/F1 reported.
- [ ] Thresholds calibrated only on development data.
- [ ] Model, tokenizer, label mapping, and environment saved.

## Validation checklist

- [ ] Confusion matrix.
- [ ] Per-class precision and recall.
- [ ] Macro-F1.
- [ ] Realistic prevalence evaluation.
- [ ] Out-of-sample test where possible.
- [ ] Qualitative error analysis.
- [ ] Downstream estimate sensitivity check.
- [ ] Statement of valid and invalid uses of the predictions.

## Publication checklist

- [ ] Codebook linked or appended.
- [ ] Corpus construction described.
- [ ] Data protection/copyright limitations stated.
- [ ] Prompt/training scripts shared.
- [ ] Model and software versions reported.
- [ ] Validation data or at least prediction/label tables shared where legal.
- [ ] Limitations discuss ambiguity, imbalance, and generalization.
- [ ] Substantive claims do not exceed measurement validity.

## Downloadable templates

- [Evaluation plan template](templates/evaluation-plan.md)
- [Prompt log template](templates/prompt-log.md)
- [Model card template](templates/model-card.md)
