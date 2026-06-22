---
name: laoli-paper
description: Laoli-style academic paper writing skills. Currently provides the introduce module for drafting manuscript Introduction sections from a user-provided Methods section, methodology draft, protocol, experimental design, analysis pipeline, model description, dataset construction procedure, or study workflow. Use when the user asks for laoli-paper, introduce, introduction, intro, background, rationale, research gap, study objective, contribution framing, manuscript opening, or contribution list. The introduce module infers the research problem, decomposes the gap, aligns method modules to those gaps, and writes a closed-loop Introduction without inventing unsupported results.
---

# Laoli Paper

## Available Skills

- `introduce`: Draft a manuscript Introduction from the user's Methods section in the author's three-paragraph, dual-bottleneck, module-alignment style.

## Purpose

Use the `introduce` skill when the user provides the Methods section, methods notes, protocol, pipeline, or experimental design and wants an academic manuscript Introduction. Work backward from what the study actually does to build a plausible research background, gap, rationale, objective, and contribution list.

The skill should not write a generic introduction first and then mention the method. It should infer the Introduction from the method's scientific logic.

Default to an author-style closed loop: field importance -> harder task pressure -> existing method families -> two residual bottlenecks or a central trade-off -> proposed method as a conceptual shift -> two method modules mapped to the bottlenecks -> validation -> contribution symmetry.

Default length and paragraphing should follow the supplied author examples: 3 substantial prose paragraphs plus a contribution list, about 650-750 words for the prose or 700-850 words total when contribution bullets are included. Do not exceed 900 words unless the user explicitly asks for a longer version.

## Method-First Intake

Extract these items from the provided Methods before drafting:

- Field, system, disease, material, task, organism, cohort, model, dataset, or research object.
- Main intervention, method, assay, algorithm, workflow, comparison, or experimental design.
- Inputs and outputs: samples, data types, measurements, endpoints, labels, variables, or evaluation metrics.
- Controls, baselines, validation strategy, statistical tests, or comparison groups.
- Scale and scope: sample size, time span, geographic scope, species, model type, dataset source, or platform.
- Implied limitation in prior work that this method appears designed to solve.
- Distinct method modules and which prior-work limitation each module appears designed to address.
- Whether the Methods imply a two-module solution, a two-stage pipeline, or a trade-off such as interpretability versus adaptability, accuracy versus efficiency, global coverage versus local relevance, or structure versus flexibility.
- Implied study objective: what the method enables the authors to test, measure, compare, predict, classify, or explain.
- Evidence boundary: what the Methods support and what they do not support.

If the Methods do not reveal the paper's field, objective, or contribution clearly, ask one concise question. Otherwise draft with `Assumptions or missing inputs:` and use bracketed placeholders for uncertain details.

## Workflow

1. Parse the Methods into a method map:
   `object -> action/method -> comparison/validation -> measured endpoint -> expected claim`.
2. Infer the introduction's argument spine:
   `Although [field/problem] is important, [specific gap] limits [progress]. To address this, this study uses [method/design] to [objective], enabling [contribution].`
3. Build the author-style contradiction:
   `existing family A offers [benefit] but suffers from [limitation A]; family B offers [benefit] but suffers from [limitation B]; therefore the field needs [combined capability/trade-off resolution]`.
4. Build a gap-module alignment table:
   `prior method family -> what it solves -> residual limitation -> proposed method module -> intended advantage`.
5. Identify the likely introduction pattern:
   - Empirical study: significance -> known context -> gap -> objective/design.
   - Methods paper: task need -> current limitation -> technical bottleneck -> new method.
   - Computational or AI paper: data/task importance -> limitations of current models or annotations -> proposed pipeline -> validation.
   - Clinical or cohort study: disease burden -> unresolved clinical question -> cohort/design -> endpoint.
6. Draft an author-style paragraph blueprint before prose. Use 3 substantial paragraphs plus a contribution list for AI, algorithm, and methods papers unless the user requests a different structure.
7. Allocate the word budget before drafting: paragraph 1 about 130-170 words, paragraph 2 about 230-300 words, paragraph 3 about 230-300 words, followed by 3 contribution bullets of about 35-60 words each.
8. Write the Introduction without adding Results unless the user provided them. End with objective, design, and contribution that are directly supported by the Methods.
9. Use citation placeholders like `[refs]` unless the user provides references or explicitly asks for literature search.
10. Include a short self-check: inferred gap, inferred objective, unsupported claims avoided, missing information, and approximate word count.

## Preferred Deep Structure

Use this structure especially for AI, computational, methods, or framework papers:

1. Paragraph 1: broad field value plus harder target setting. Establish the major paradigm, why it matters, where it is used, and why the target task is harder than the ordinary version.
2. Paragraph 2: progress, taxonomy, and dual bottleneck. Acknowledge existing advances, group recent methods into 2-3 families, state each family's strength and residual limitation, then compress them into two bottlenecks or one explicit trade-off.
3. Paragraph 3: proposed method and module alignment. Introduce the method as a conceptual shift, explain how each major method module answers a prior bottleneck, mention validation only when provided, and lead into contributions.
4. Contribution list: make each contribution correspond to a gap, method module, or validation result.

## Author-Style Blueprint

When the input is an AI, NLP, RAG, machine learning, algorithm, or methods paper, prefer this exact three-paragraph rhetorical sequence:

- Paragraph 1: `Task legitimacy and pressure`. Define the task, state its importance and applications, then distinguish the harder target setting from the ordinary version.
- Paragraph 2: `Progress, taxonomy, and contradiction`. Acknowledge existing approaches, divide them into two paradigms, state each paradigm's benefit and residual limitation, then end with the core research question or trade-off.
- Paragraph 3: `Proposed method and module alignment`. Present the method as a comprehensive strategy or conceptual shift. Explain module 1 for bottleneck 1 and module 2 for bottleneck 2, then close with validation and contribution setup.

If the Methods contain only one clear module, still look for a second axis in the design: optimization, representation, instance specificity, scalability, interpretability, robustness, information preservation, or validation.

## Length Control

Follow this word budget by default:

- Introduction prose only: 650-750 words.
- Introduction plus contribution list: 700-850 words total.
- Contribution list: 3 bullets by default; 2 bullets only for a narrow paper, 4 only when the Methods clearly support four distinct contributions.
- Paragraph count: 3 substantial paragraphs before the contribution list.
- Paragraph 1: 130-170 words.
- Paragraph 2: 230-300 words.
- Paragraph 3: 230-300 words.
- Maximum: 900 words unless the user requests a longer version.

If the provided Methods are sparse, write a shorter 450-600 word draft and list missing inputs rather than padding.

## Default Output

Return these sections unless the user asks for only prose:

- `Inferred argument`: one sentence.
- `Author-style contradiction`: one sentence naming the two bottlenecks or trade-off.
- `Gap-module alignment`: concise table or bullets.
- `Paragraph blueprint`: 3 bullets using the author-style sequence when appropriate.
- `Word budget`: target length and paragraph allocation.
- `Draft Introduction`: polished manuscript prose.
- `Contribution list`: 2-4 bullets when supported by the Methods.
- `Assumptions or missing inputs`: concise list.
- `Self-check`: risks such as missing citations, overclaiming, or unclear contribution.

## Style Rules

- Keep the Introduction anchored to the Methods. Every major claim should explain why the provided design, assay, dataset, model, or analysis is needed.
- Do not invent findings, effect sizes, mechanisms, sample characteristics, or novelty claims absent from the Methods.
- Do not make the method sound more general than the validation supports.
- Prefer restrained gap language: `remains unclear`, `has not been systematically evaluated`, `is difficult to measure`, `lacks scalable tools`, or `has rarely been tested in [context]`.
- Avoid listing procedural details in the Introduction. Translate method details into rationale, objective, and study design.
- When the method has multiple modules, write them as answers to separate bottlenecks rather than as a procedural sequence.
- Preserve the author's balanced critique pattern: `Although these methods..., however...`.
- Prefer a research-question bridge when there is a trade-off: `This naturally raises the question of whether...`.
- For contribution lists, preserve one-to-one correspondence among gap, method module, and validation.
- Keep paragraph lengths uneven in the author's pattern: shorter opening, long taxonomy/contradiction paragraph, long method-alignment paragraph, then contribution bullets.
- For Chinese user requests or Chinese Methods text, draft the final Introduction in English by default unless the user asks for Chinese.

## Resources

Load `references/method-to-introduction.md` when the Methods are complex, the paper type is unclear, the user asks for multiple Introduction versions, contribution bullets, a paragraph-by-paragraph rationale, or a deep introduction writing routine.
