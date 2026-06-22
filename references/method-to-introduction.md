# Method-to-Introduction Patterns

## Core Conversion

Convert Methods details into Introduction logic:

- Method object -> field/problem context.
- Measurement endpoint -> unresolved scientific or practical question.
- Control or baseline -> limitation of current approaches.
- Validation strategy -> credibility of the proposed approach.
- Dataset or cohort -> population, context, or scope where the gap matters.
- Statistical model or algorithm -> analytical bottleneck the study addresses.

Avoid copying procedural steps into the Introduction. Methods answer "what was done"; the Introduction should answer "why this needed to be done".

## Deep Routine: Closed-Loop Introduction

Use this routine for strong methods, AI, algorithm, or framework introductions.

The target author style is a dual-bottleneck or trade-off-driven Introduction. It should feel as if the method is inevitable because each module is forced by a prior limitation.

Default author-style length: 650-750 words for prose, or 700-850 words including contribution bullets. Use 3 substantial prose paragraphs plus a contribution list. The two reference examples are roughly 650 and 740 words, so avoid very short 300-word introductions, 5-paragraph school-style introductions, or sprawling 1200-word reviews unless requested.

### 1. Establish the paradigm, then stress it

Start with a recognized field-level paradigm and its value. Then immediately name the harder setting where the paradigm becomes insufficient.

Template:

`[Paradigm] has improved [broad capability] by [mechanism]. It is widely used in [applications]. However, [harder setting] requires [extra reasoning/data/measurement], making [standard version] insufficient.`

The first paragraph should not merely say the topic is important. It should create pressure: the reader must see why ordinary methods fail in the target scenario.

### 2. Taxonomize prior work to create structured gaps

Group prior work into 2-3 method families. Each family should receive a balanced treatment:

`method family -> what it improves -> residual bottleneck`.

This is stronger than a flat literature review because it turns background into an argument. The taxonomy should prepare the exact gaps the proposed method will answer.

Example logic:

- Family A addresses the single-step limitation, but still scores evidence independently.
- Family B adds structure or reasoning paths, but still loses information during long-range propagation.

For prompting or language-model adaptation papers, use trade-off taxonomy:

- Hard or discrete methods preserve interpretability, but restrict optimization and instance-level adaptability.
- Soft or continuous methods improve adaptability, but sacrifice interpretability or shared linguistic meaning.

For retrieval or reasoning papers, use process-stage taxonomy:

- Decomposition or subquery methods improve stepwise retrieval, but may still evaluate evidence independently.
- Structure or graph methods improve reasoning paths, but may attenuate information across long-range propagation.

### 3. Convert limitations into named bottlenecks

After discussing method families, compress the critique into 1-2 core bottlenecks. These bottlenecks become the hidden outline of the paper.

Good bottlenecks are mechanistic:

- independent scoring misses cooperative evidence.
- long-range reasoning attenuates previous information.
- full recomputation is too expensive.
- static representations cannot absorb newly inferred signals.
- task-level adaptation does not guarantee instance-level adaptation.
- interpretability and adaptability are difficult to preserve simultaneously.
- structured reasoning can improve traceability while still losing semantic detail.

Weak bottlenecks are vague:

- existing methods are bad.
- performance is limited.
- more research is needed.

### 4. Introduce the method as a conceptual shift

Do not introduce the method only as a name. Present it as a shift from an old operating principle to a new one.

Template:

`To address these challenges, we propose [method], which shifts from [old principle] to [new principle].`

Examples of old-to-new contrasts:

- isolated similarity retrieval -> combinatorial evidence selection.
- structured propagation -> incremental reasoning-state augmentation.
- fixed representations -> adaptive basis expansion.
- local relevance -> cooperative semantic coverage.
- manually designed prompts -> reinforced prompt exploration.
- shared prompt templates -> instance-aware prompt generation.
- task-wide adaptation -> joint task- and instance-level adaptation.

### 5. Map every method module to one bottleneck

Each major method component should answer a previously stated limitation.

Use this mapping:

`Earlier gap: [specific limitation]. Method response: [module]. Mechanism: [how it works conceptually]. Expected benefit: [what problem it reduces].`

Avoid presenting modules as a chronological recipe. The Introduction should explain intellectual necessity, not implementation order.

### 6. Close with validation and contribution symmetry

If results are provided, include a compact validation sentence with datasets and key metrics. Then list contributions so that each contribution mirrors the prior argument:

- Contribution 1 solves bottleneck 1.
- Contribution 2 solves bottleneck 2.
- Contribution 3 validates the whole framework.

The contribution list should feel inevitable after the Introduction, not appended.

Use this contribution order when possible:

1. Integrated framework: name the whole strategy and the trade-off it resolves.
2. Mechanistic module: describe the module that solves the most novel bottleneck.
3. Secondary module or first-use claim: describe the second module, new optimization route, or first application in the target task.
4. Validation: include datasets, benchmarks, and performance only if provided.

## Author-Style Sentence Moves

Use these moves sparingly and adapt them to the user's domain:

- `Unlike [ordinary setting], [target setting] presents unique challenges due to [mechanism].`
- `Despite these advances, existing methods still struggle to [specific bottleneck].`
- `Two primary paradigms have emerged in this context: [A] and [B].`
- `Although [A] offers [benefit], its [property] limits [capability].`
- `However, [B] inherently [limitation], despite [benefit].`
- `Critically, despite their differences, both approaches [shared limitation].`
- `This observation naturally raises the question of whether [capability A] can be achieved while preserving [capability B].`
- `To this end, we propose [method], a comprehensive strategy that [resolves trade-off].`

## Word Budget Pattern

Use this allocation for a 700-800 word Introduction:

1. Paragraph 1, task legitimacy and pressure: 130-170 words.
2. Paragraph 2, progress, two-family taxonomy, and contradiction: 230-300 words.
3. Paragraph 3, proposed method and module alignment: 230-300 words.
4. Contributions: 3 bullets, about 35-60 words each.

Compress by shortening applications and citation-heavy background first. Do not compress the two-family taxonomy or module alignment too aggressively, because those are the author's signature moves.

## Pattern A: Empirical Study

Use when Methods describe experiments, cohorts, interventions, assays, or observations.

1. Establish the biological, clinical, environmental, or technical importance of the topic.
2. State what is known from prior work.
3. Identify what remains untested, unresolved, or poorly quantified.
4. Explain why the provided design can address the gap.
5. End with the study objective and design.

## Pattern B: Methods or Tool Paper

Use when Methods describe a new assay, workflow, software, algorithm, database, or protocol.

1. Define the task or measurement need.
2. Explain limitations of existing methods in the context implied by the Methods.
3. Identify the bottleneck the new method targets.
4. Introduce the method at a conceptual level.
5. State the validation strategy and intended contribution.

## Pattern C: Computational or AI Study

Use when Methods include datasets, feature extraction, model training, prediction, classification, benchmarking, or explainability.

1. Introduce the scientific or practical task.
2. Explain why current data, annotations, models, or benchmarks are insufficient.
3. State the need for the specific data/model/workflow used.
4. Introduce the pipeline and evaluation design.
5. End with the objective and what the workflow enables.

For AI or RAG-style methods, prefer this three-paragraph sequence:

1. Paradigm, application breadth, and complex task pressure.
2. Prior work taxonomy with family-specific limitations, ending in the core contradiction.
3. Proposed method as conceptual shift, module-to-gap explanation, validation, and contribution setup.

## Pattern D: Clinical or Cohort Study

Use when Methods include patients, samples, inclusion criteria, endpoints, follow-up, or clinical variables.

1. Establish disease burden or clinical decision problem.
2. State the unresolved clinical or translational question.
3. Explain why the cohort, endpoint, or analysis strategy is appropriate.
4. State the study objective and design.
5. Keep claims about clinical utility provisional unless outcomes are provided.

## Overclaiming Guardrails

Do not infer:

- Positive results from the existence of an experiment.
- Superiority from the presence of a baseline comparison.
- Mechanism from association analysis alone.
- Clinical utility from retrospective modeling alone.
- Generalizability beyond the cohort, dataset, organism, or experimental system.
- A complete solution to all limitations when the method addresses only selected bottlenecks.
- A conceptual shift unless the Methods contain a real change in representation, optimization, decomposition, measurement, or inference logic.

Use placeholders when needed:

- `[specific disease/context]`
- `[key prior limitation]`
- `[primary endpoint]`
- `[comparison method]`
- `[main contribution supported by results]`

## Self-Review Questions

- Does paragraph 1 create a clear task pressure rather than only listing applications?
- Does the prior-work taxonomy have a reason for being split into these categories?
- Does each limitation point toward something the proposed method actually contains?
- Is the method introduced as a principle-level move before technical details?
- Can every contribution be traced back to an earlier gap?
- Are results and benchmark claims omitted unless the user provided them?
- Is there a visible symmetry between prior-work families, method modules, and contribution bullets?
- Is the prose close to the 650-750 word target, or shorter only because the Methods lacked enough information?
