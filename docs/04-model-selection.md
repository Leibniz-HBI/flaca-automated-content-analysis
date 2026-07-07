---
layout: page
title: "4. Model Selection"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 4. Model selection

No model is best for every automated content analysis task. The choice depends on construct complexity, training data, privacy constraints, reproducibility requirements, and the downstream quantity of interest.

![Model choice map](assets/figures/model-choice.svg)

*Figure 3. Original model choice map, CC0/public domain dedication.*

## Decision matrix

| Approach | Best used when | Main risk | Minimum validation |
|---|---|---|---|
| Dictionary / rule-based | The category is manifest and lexicalized | Low recall, context blindness | Manual sample of hits and non-hits |
| Classical supervised model | Many labels, simple features sufficient | Poor transfer to new domains | Held-out and out-of-sample test |
| Fine-tuned transformer / SLM | Moderate labels, task-specific accuracy needed | Overfitting, imbalance, compute needs | Per-class metrics, repeated runs |
| PEFT / adapters | Need shareable, efficient task modules | More implementation complexity | Same as fine-tuning plus reproducibility check |
| Prompted LLM | Rapid prototyping, low training data, codebook is clear | Prompt sensitivity, hidden model changes, hallucinated rationale | Human-labelled gold set, prompt stability test |
| Hybrid LLM + human | Annotation budget is limited but validation is still required | Human review may inherit model framing | Audit disagreement and adjudication logs |

## FLACA-derived model advice

- Use **prompted LLMs** for exploration, pilot annotation, codebook stress tests, and first-pass labels when the codebook is mature.
- Use **fine-tuned or parameter-efficient smaller models** when you need stable, shareable, reproducible measurement and have enough high-quality labels.
- Use **hybrid workflows** when categories are complex and annotation budgets are constrained.
- Use **domain adaptation** when the target corpus differs from the model’s original training domain or when labels are scarce.
- Compare models on the same gold data; do not compare claims from different datasets or different test distributions.

## Practical default

For a new communication-science project with complex semantic categories, a practical default is:

1. Build a small gold set.
2. Run a simple baseline.
3. Test one prompted LLM.
4. Fine-tune one multilingual transformer or open model if at least a few hundred reliable labels are available.
5. Keep the best approach only if it passes class-specific and out-of-sample validation.

## Model card fields

Document every model with:

- model name and version/hash;
- provider or local runtime;
- license and data protection implications;
- prompt, chat template, or training script version;
- decoding settings or training hyperparameters;
- random seeds;
- hardware;
- date of execution;
- validation results by class;
- known failure modes.
