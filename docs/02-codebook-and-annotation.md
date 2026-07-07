---
layout: page
title: "2. Codebook and Annotation"
---


**Navigation:** [Home](index.html) · [1 Scope](01-scope-and-design.html) · [2 Codebook](02-codebook-and-annotation.html) · [3 Data](03-data-preparation.html) · [4 Model choice](04-model-selection.html) · [5 LLM prompting](05-prompting-llms.html) · [6 Fine-tuning](06-fine-tuning-slms.html) · [7 Evaluation](07-evaluation-validation.html) · [8 Reporting](08-reporting-reproducibility.html) · [Checklists](09-checklists.html) · [Links](resources.html) · [References](references.html)

# 2. Codebook and annotation

A codebook does more than document categories. It connects theory, human annotation, model input, and validation. A key FLACA lesson is that codebooks need to work for trained coders and for computational workflows.

## A model-ready codebook contains

| Element | Purpose | Example question |
|---|---|---|
| Construct definition | Theoretical meaning | What exactly counts as a frame, argument, claim, stance, or actor? |
| Inclusion rules | Positive boundary | When must a unit receive the label? |
| Exclusion rules | Negative boundary | What looks similar but must not be labelled? |
| Decision hierarchy | Conflict resolution | Which rule overrides which? |
| Examples | Grounding | What are typical, borderline, and negative examples? |
| Context rule | Unit interpretation | May coders use previous/next sentences, headline, article lead, thread, or metadata? |
| Output schema | Machine readability | Must the result be one label, multiple labels, probability scores, or a JSON object? |

## Annotation workflow

1. **Pilot on heterogeneous material.** Include clear, borderline, and difficult cases.
2. **Discuss disagreements as concept problems.** Compute agreement, then use disagreement to improve the codebook.
3. **Freeze a codebook version before gold annotation.** Keep a changelog.
4. **Create separate train, development, and final test sets.** Never tune prompts or thresholds on the final test set.
5. **Preserve original text and context.** Store target unit, context window, document ID, source, date, and metadata separately.
6. **Adjudicate final labels.** For complex constructs, a reconciled expert label is usually better than raw majority voting.

## Human reliability as diagnosis

Low agreement can mean several things: the construct is under-specified, the unit is too small, the codebook lacks examples, or the phenomenon is genuinely ambiguous. Treat reliability results as feedback for measurement design.

## Translate codebooks into prompts

For LLM-based classification, do not paste a long manual codebook into the prompt. Convert it into model-readable instructions:

```text
Task: Classify the target unit according to the codebook.
Target construct: [definition]
Labels: [label names + short definitions]
Use context: [yes/no; exact rule]
Decision rules: [ordered list]
Return format: {"label": "...", "rationale": "short", "uncertainty": "low|medium|high"}
Do not infer information that is not present in the text.
```

Keep prompts versioned exactly like codebooks.

## Hybrid annotation option

A strong low-cost workflow is:

1. Run an LLM twice with the same frozen instructions.
2. Send only disagreements and high-uncertainty cases to human adjudication.
3. Use the reconciled labels as validation data or as training data for a supervised model.

This cannot replace expert validation, but it can direct human effort to the cases where it matters most.
