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

Default to 3 prose paragraphs plus a contribution list. Keep the opening deliberately compact and place most analytical detail in paragraphs 2 and 3. Aim for about 580-680 words of prose or 650-780 words including contribution bullets. Do not exceed 850 words unless the user explicitly asks for a longer version.

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
7. Allocate the word budget before drafting: paragraph 1 about 80-110 words, paragraph 2 about 230-280 words, paragraph 3 about 240-290 words, followed by 3 contribution bullets of about 35-50 words each. Treat 120 words as a hard ceiling for paragraph 1 unless the user requests otherwise.
8. Write the Introduction without adding Results unless the user provided them. End with objective, design, and contribution that are directly supported by the Methods.
9. Use citation placeholders like `[refs]` unless the user provides references or explicitly asks for literature search.
10. Revise the prose for argumentative flow. Replace list-like sentences with causal, contrastive, or progressive sentence sequences.
11. Include a short self-check: inferred gap, inferred objective, unsupported claims avoided, missing information, approximate word count, and enumeration overuse.

## Preferred Deep Structure

Use this structure especially for AI, computational, methods, or framework papers:

1. Paragraph 1: compact task pressure. Define the major paradigm in one sentence, identify the harder target setting, and end with the central need. Do not survey applications, classify prior work, name every challenge, or explain the proposed method here.
2. Paragraph 2: progress, taxonomy, and dual bottleneck. Acknowledge existing advances, group recent methods into 2-3 families, state each family's strength and residual limitation, then compress them into two bottlenecks or one explicit trade-off.
3. Paragraph 3: proposed method and module alignment. Introduce the method as a conceptual shift, explain how each major method module answers a prior bottleneck, mention validation only when provided, and lead into contributions.
4. Contribution list: make each contribution correspond to a gap, method module, or validation result.

## Author-Style Blueprint

When the input is an AI, NLP, RAG, machine learning, algorithm, or methods paper, prefer this exact three-paragraph rhetorical sequence:

- Paragraph 1: `Compact task legitimacy and pressure`. In 3-5 sentences, define the task, state why the target setting is harder, and identify the resulting need. Mention at most one representative application when it is essential to the problem; otherwise omit applications entirely.
- Paragraph 2: `Progress, taxonomy, and contradiction`. Acknowledge existing approaches, divide them into two paradigms, state each paradigm's benefit and residual limitation, then end with the core research question or trade-off.
- Paragraph 3: `Proposed method and module alignment`. Present the method as a comprehensive strategy or conceptual shift. Explain module 1 for bottleneck 1 and module 2 for bottleneck 2, then close with validation and contribution setup.

If the Methods contain only one clear module, still look for a second axis in the design: optimization, representation, instance specificity, scalability, interpretability, robustness, information preservation, or validation.

## Length Control

Follow this word budget by default:

- Introduction prose only: 580-680 words.
- Introduction plus contribution list: 650-780 words total.
- Contribution list: 3 bullets by default; 2 bullets only for a narrow paper, 4 only when the Methods clearly support four distinct contributions.
- Paragraph count: 3 substantial paragraphs before the contribution list.
- Paragraph 1: 80-110 words, with a default hard ceiling of 120 words.
- Paragraph 2: 230-280 words.
- Paragraph 3: 240-290 words.
- Maximum: 850 words unless the user requests a longer version.

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
- Avoid prose that reads like a compressed outline. Do not habitually package three or more functions, applications, benefits, costs, or abstract nouns into one sentence using comma-separated lists or `A, B, and C` constructions.
- Give each sentence one dominant argumentative job. When several ideas are necessary, connect them across sentences through cause, consequence, contrast, qualification, or progression instead of presenting them as co-equal items.
- Prefer explaining the most relevant example over naming several generic examples. Retain a short parallel pair only when the contrast itself carries the argument; reserve explicit enumeration for formal contribution lists, method taxonomies, and genuinely discrete variables.
- During revision, scan every sentence with two or more commas or a terminal `and`. If removing or reordering the listed items would not alter the logic, rewrite the sentence around the underlying relationship.
- Avoid repeated noun-heavy patterns such as `deliberation, verification, and integration` or `repeated rationales, growing costs, and diminishing returns`. Turn them into movement: state what happens first, why it creates a problem, and what follows.
- Keep paragraph 1 lean. It should establish pressure, not provide a miniature literature review. Remove generic claims, application inventories, repeated statements of importance, and any sentence whose deletion does not weaken the transition into paragraph 2.
- Draft paragraph 1 last when necessary. Once the two bottlenecks are clear, retain only the minimum context required for the reader to understand why those bottlenecks matter.
- When the method has multiple modules, write them as answers to separate bottlenecks rather than as a procedural sequence.
- Preserve the author's balanced critique pattern: `Although these methods..., however...`.
- Prefer a research-question bridge when there is a trade-off: `This naturally raises the question of whether...`.
- For contribution lists, preserve one-to-one correspondence among gap, method module, and validation.
- Keep paragraph lengths visibly uneven: a compact opening of no more than 120 words, followed by a longer taxonomy/contradiction paragraph and a longer method-alignment paragraph, then contribution bullets.
- For Chinese user requests or Chinese Methods text, draft the final Introduction in English by default unless the user asks for Chinese.

## Resources

Load `references/method-to-introduction.md` when the Methods are complex, the paper type is unclear, the user asks for multiple Introduction versions, contribution bullets, a paragraph-by-paragraph rationale, or a deep introduction writing routine.
