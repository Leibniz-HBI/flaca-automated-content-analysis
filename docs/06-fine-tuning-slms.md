---
layout: page
title: "6. Fine-tuning Smaller Language Models"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 6. Fine-tuning smaller language models

Fine-tuning still matters for communication science because it creates a task-specific measurement instrument that can be versioned, rerun, audited, and shared more easily than many proprietary LLM workflows.

## When fine-tuning is attractive

Use supervised adaptation when:

- you have a reliable labelled dataset;
- the task must be repeated over time;
- data cannot be sent to external APIs;
- model outputs feed into quantitative estimates;
- you need reproducibility and stable model versions;
- the category is domain-specific or non-English;
- prompt-based LLMs overpredict rare classes.

## Training workflow

1. Select a suitable pretrained multilingual or domain model.
2. Freeze train/dev/test splits.
3. Establish a simple baseline.
4. Train with multiple seeds.
5. Track training loss and validation metrics.
6. Evaluate per class and on out-of-sample data.
7. Calibrate thresholds if prevalence-sensitive estimates matter.
8. Save the model, tokenizer, label mapping, and training configuration.

## FLACA-style enhancements

| Technique | Use case | Why it helps |
|---|---|---|
| Near-domain adaptation | Target task has few labels but related labelled data exists | Transfers task-relevant linguistic patterns |
| Parameter-efficient fine-tuning | Compute or sharing constraints | Trains small adapters without updating the full model |
| PET-style classification | Few labels and meaningful label verbalizers | Uses label semantics instead of opaque class IDs |
| Entity/person-name shuffling | Classifier overfits to prominent actors | Reduces spurious association between names and labels |
| Class weights / resampling | Minority classes are rare | Increases attention to rare categories |
| Threshold calibration | False positives distort prevalence | Tunes the precision/recall trade-off for the research goal |

## Training-data size

There is no universal minimum. For a first supervised comparison, a few hundred high-quality annotations may be enough to test feasibility. For final measurement of complex categories, the required data depends on prevalence, label ambiguity, domain shift, and downstream use. Always report learning curves when possible: performance at 50, 100, 250, 500, and 1,000 labels is more informative than a single final score.

## Implementation checklist

- Store `label2id` and `id2label` mappings.
- Use stratified splits only when this does not create leakage.
- Keep a realistic validation distribution somewhere, even if training is balanced.
- Repeat with several seeds.
- Save exact library versions.
- Export predictions for qualitative error analysis.
- Report failure cases as well as aggregate scores.
