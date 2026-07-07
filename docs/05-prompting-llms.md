---
layout: page
title: "5. LLM Prompting"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 5. LLM prompting

LLMs are attractive because they can classify text from instructions alone. The same simplicity is the danger: a fluent answer can conceal unstable measurement. Treat LLM prompting as a formal measurement instrument, not as an informal chat.

## Prompt structure

A robust classification prompt usually has:

1. **Role-independent task statement**: avoid theatrical roles; specify the classification task.
2. **Construct definition**: concise operational definition.
3. **Labels**: exact label names and mutually exclusive decision rules.
4. **Context rule**: what information may be used.
5. **Examples**: only if representative and not drawn from the final test set.
6. **Output schema**: strict JSON or a single allowed label.
7. **Refusal rule**: what to do with ambiguity or insufficient evidence.

## Prompt engineering without overfitting

Use development data for prompt iteration and freeze the prompt before final evaluation. Do not keep rewriting the prompt until the final test looks good. That turns the test set into training data.

## Stability protocol

For every serious LLM classification task:

- Run the same prompt at least twice on the development set.
- Test semantically equivalent prompt variants.
- Report agreement between prompt variants or runs.
- Inspect disagreements as likely edge cases.
- Keep raw model outputs, not only parsed labels.
- Record provider, model ID, date, temperature, seed if supported, and system prompt.

## Recommended settings

| Setting | Recommendation | Rationale |
|---|---|---|
| Temperature | `0` or low | Increases repeatability |
| Output | JSON schema or fixed labels | Reduces parsing errors |
| Rationale | Optional and short | Useful for audit, but do not treat as explanation of actual model reasoning |
| Label order | Randomize or test variants | Detects order sensitivity |
| Few-shot examples | Use cautiously | Can help but may bias output toward example distribution |
| Label distribution hint | Test empirically | May reduce prevalence distortion but can also overcorrect |

## Example prompt skeleton

```text
You classify one target text according to a communication-science codebook.

Construct: [definition]
Labels:
- FOR: [definition]
- AGAINST: [definition]
- NO_STANCE: [definition]

Use the context only to interpret the target text. Classify the target text itself.
If the target text does not clearly express the construct, choose NO_STANCE.
Return exactly this JSON: {"label": "FOR|AGAINST|NO_STANCE"}.

Context before:
[context_before]

Target text:
[target_text]

Context after:
[context_after]
```

## When not to use LLM prompting alone

Do not rely on prompting alone when the final claim depends on small differences in prevalence, rare classes, highly contested frames, or downstream regression coefficients. In these settings, either validate very carefully or use LLMs as annotation assistants rather than final measurement devices.
