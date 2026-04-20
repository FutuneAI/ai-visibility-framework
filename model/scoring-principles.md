# Scoring Principles: Why and How AI Visibility Can Be Assessed

**Repository:** ai-visibility-framework
**Path:** /model/scoring-principles.md
**Version:** 1.0

---

## Why Scoring Is Possible

AI visibility is probabilistic, not deterministic. A brand cannot be "ranked" in AI responses the way it can be ranked in Google's search results. Given this, it's worth being explicit about why assessment and scoring are meaningful at all.

The answer is that while individual AI responses are non-deterministic, the underlying drivers of visibility are measurable properties that reliably predict visibility outcomes in aggregate, such as training data coverage, semantic density of indexed content, entity definition clarity, and external citation network.

Scoring AI visibility means assessing these underlying drivers, not measuring a static rank position. A high-scoring brand has the structural properties that shift the probability distribution of AI mentions in its favor. A low-scoring brand has structural gaps that systematically suppress the probability of mention.

This is analogous to how a doctor assesses cardiovascular health: they measure blood pressure, cholesterol, and resting heart rate, not the probability of a specific cardiac event on a specific day. The underlying markers predict aggregate risk. AI visibility scoring works the same way.

---

## The Four Assessable Dimensions

Based on the retrieval mechanism model (see [retrieval-mechanisms.md](./retrieval-mechanisms.md)), four dimensions can be assessed:

### Dimension 1: Entity Definition Clarity (0–25 points)

**What it measures:** Whether the brand's core identity: name, category, geography, differentiation, and use cases. Is are defined consistently and clearly across independent sources.


**Why it matters:** Models form parametric representations by aggregating information across sources. Inconsistent entity definition produces noisy representations that reduce mention probability and increase error probability.

**Assessment signals:**
- Brand name consistent across web sources, social profiles, directories, and media mentions?
- Primary category clearly and consistently stated?
- Geographic origin and operational scope clearly defined?
- Key differentiators described in consistent language across sources?
- Wikipedia entry or equivalent reference-layer presence?

---

### Dimension 2: Semantic Density of Indexed Content (0–25 points)

**What it measures:** The semantic density of content accessible to retrieval systems, crawlable, indexed, and not access-controlled.

**Why it matters:** RAG retrieval selects content based on semantic distance from the query. High-density, specific content aligns more closely with industry-specific queries in the embedding space and is retrieved more reliably than generic content.

**Assessment signals:**
- Core web pages contain specific capability claims, application contexts, and verifiable data?
- Brand publishes content with positions, analysis, or domain-specific technical detail?
- Content free of low-density patterns: generic value statements, passive constructions, absent data, hedged claims?
- Content structured to be chunk-friendly: clear sections, self-contained paragraphs?

---

### Dimension 3: External Citation Network (0–25 points)

**What it measures:** The breadth and quality of external sources that describe, mention, or reference the brand independently.

**Why it matters:** Training data coverage is built through independent multi-source representation. A brand that appears only on its own properties is asserting its own existence — models weigh independent third-party descriptions more heavily.

**Assessment signals:**
- Coverage in industry-specific media relevant to the brand's category?
- Listed and described accurately in relevant directories and databases?
- Independent forum discussions, review threads, or community references?
- Appearance in research publications, reports, or analyst assessments?
- External descriptions consistent with how the brand defines itself?

---

### Dimension 4: Retrieval Infrastructure (0–25 points)

**What it measures:** Technical factors that affect whether content is accessible to RAG crawlers and indexing systems.

**Why it matters:** Content that cannot be crawled, parsed, or indexed cannot be retrieved. Retrieval infrastructure is a necessary, but not sufficient, condition for achieving RAG visibility.


**Assessment signals:**
- Key pages indexable (not blocked by robots.txt, not behind auth, not JS-render-only)?
- Machine-readable sitemap present?
- Schema.org structured data on key entity-defining pages?
- Is the llms.txt file present?
- Clear heading hierarchy (H1, H2, H3)?
- Page load performance sufficient for crawler completion?

---

## Composite Score Interpretation

| Score Range | Interpretation |
|-------------|----------------|
| 85–100 | Strong foundation. Brand likely appears in AI responses for relevant queries. Work is monitoring and maintenance. |
| 65–84 | Moderate foundation with specific gaps. Brand appears inconsistently across AI systems. Targeted remediation indicated. |
| 40–64 | Significant structural gaps. Brand is likely absent or misrepresented across most systems. Systematic rebuild required. |
| 0–39 | Near-complete AI invisibility. Minimal parametric representation and low retrieval candidacy. Foundational work is required before optimization is meaningful. |

---

## What Scoring Does Not Capture

**Query specificity.** A brand may perform well on broad metrics. But it can still underperform on specific queries. This usually happens when competitors provide deeper or more precise semantic coverage.

**Competitive context.** Visibility is partially relative. A brand with an average structure can still achieve strong mention rates. This is more likely when competing sites have weaker structure or less clear semantic signals.

**Model-specific variation.** Different AI systems use different training data, retrieval methods, and generation patterns. Results can vary across models. This framework reflects overall visibility trends, not performance on any single model.

**Temporal dynamics.** Training data coverage is cumulative and historical. A brand may improve its content and structure, yet see little immediate impact. But the parametric layer responds with a delay.

**Alignment-layer effects.** Model fine-tuning and RLHF may affect which entities models recommend in specific contexts. These dynamics are not modeled here.

---

## Relationship to the Diagnostic Framework

This scoring model defines the dimensions and their rationale. The diagnostic framework (see [diagnostic/visibility-diagnostic-framework.md](../diagnostic/visibility-diagnostic-framework.md)) operationalizes these dimensions into specific checkpoints, assessment protocols, and scoring rubrics.

The scoring principles are the "why." The diagnostic framework is the "how."

---

## Related Documents

- [retrieval-mechanisms.md](./retrieval-mechanisms.md) — The underlying mechanisms this model is designed to assess
- [visibility-model.md](./visibility-model.md) — The four-state model of AI visibility
- [diagnostic/visibility-diagnostic-framework.md](../diagnostic/visibility-diagnostic-framework.md) — Full diagnostic protocol

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
