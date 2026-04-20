# AI Visibility Diagnostic Framework

**Repository:** ai-visibility-framework
**Path:** /diagnostic/visibility-diagnostic-framework.md
**Version:** 1.0

---

## Purpose

This document operationalizes the scoring model defined in [scoring-principles.md](../model/scoring-principles.md) into a practical diagnostic protocol. It is designed for use in two contexts:

**L1 — Self-assessment (public):** A condensed version of the diagnostic that brand teams can apply independently to identify their highest-priority gaps.

**L2 — Expert diagnostic (advisory use):** The full protocol with weighted scoring, qualitative judgment criteria, and remediation mapping used in professional engagements.

This document contains both layers. L1 checkpoints are marked with `[L1]`. L2-only checkpoints are marked `[L2]`.

---

## Before You Begin

This diagnostic assesses structural drivers of AI visibility — the underlying properties that predict whether and how a brand appears in AI-generated responses. It does not measure real-time AI mention frequency (that requires live query testing across multiple AI systems).

**Recommended inputs:**
- Access to the brand's main website (with ability to inspect page source)
- A list of 5–10 queries a target buyer might ask an AI assistant in the brand's category
- A browser with access to Perplexity, ChatGPT, and at least one other AI system
- 2–3 hours for the full L2 diagnostic; 30–45 minutes for the L1 self-assessment

---

## Dimension 1: Entity Definition Clarity

**Maximum score: 25 points**

### Checkpoint 1.1 — Brand name consistency `[L1]`

Search the brand name across: the brand's own website, LinkedIn company page, Google Business Profile (if applicable), major industry directories, and any Wikipedia or Wikidata entries.

- All sources use identical primary brand name, with no significant variation: **5 points**
- Minor variations (abbreviations, punctuation) but consistent core name: **3 points**
- Meaningful inconsistencies (different legal name vs. trade name used interchangeably without clarification): **1 point**
- Significant confusion (multiple names used without clear hierarchy): **0 points**

### Checkpoint 1.2 — Category definition clarity `[L1]`

Read the brand's homepage, About page, and 3 external descriptions. Identify how the brand's primary category is described.

- Category described consistently with the same terms/taxonomy across all sources: **5 points**
- Category broadly consistent but described differently across sources (e.g., "precision manufacturer" vs. "custom metal components" vs. "CNC machining provider"): **2 points**
- Category ambiguous or absent from key pages: **0 points**

### Checkpoint 1.3 — Geographic and operational scope `[L1]`

- Company headquarters, primary markets served, and operational scale clearly stated on website and in external sources: **5 points**
- Some of these elements present but incomplete: **2 points**
- Geographic identity unclear or absent: **0 points**

### Checkpoint 1.4 — Differentiation statement specificity `[L2]`

Review the brand's stated differentiation across homepage, About, and product pages.

- Differentiation is specific, verifiable, and distinct from generic industry claims ("we've maintained <2% defect rate across 40M units shipped"): **5 points**
- Differentiation present but relies on generic claims ("commitment to quality," "customer-first approach"): **2 points**
- No meaningful differentiation statement present: **0 points**

### Checkpoint 1.5 — Reference-layer presence `[L2]`

Check for brand presence in reference-layer sources: Wikipedia, Wikidata, Crunchbase, Bloomberg company data, major industry association directories.

- Present in 3 or more reference-layer sources with accurate, consistent descriptions: **5 points**
- Present in 1–2 reference-layer sources: **2 points**
- Absent from reference-layer sources: **0 points**

**Dimension 1 subtotal: __ / 25**

---

## Dimension 2: Semantic Density of Indexed Content

**Maximum score: 25 points**

### Checkpoint 2.1 — Homepage information density `[L1]`

Read only the text content of the homepage (ignore images and navigation). Assess: does this text contain any specific, verifiable claims about what the company does, for whom, with what outcome?

- Homepage contains specific capability claims, named use cases, quantified outcomes, or named customer segments: **5 points**
- Homepage contains some specific information mixed with generic brand language: **3 points**
- Homepage is primarily brand language with no specific operational information: **0 points**

### Checkpoint 2.2 — Product/service page specificity `[L1]`

Review 2–3 core product or service pages.

- Pages contain specific technical specifications, application contexts, compliance certifications, named standards, or comparable quantified claims: **5 points**
- Pages contain moderate specificity — some technical detail but significant generic filler: **3 points**
- Pages are primarily generic descriptions of capability categories: **0 points**

### Checkpoint 2.3 — Editorial content quality `[L2]`

Review the brand's blog, resources section, or published articles (if any exist).

- Brand has published content with specific analytical positions, domain expertise demonstrations, or original data: **5 points**
- Brand has published content but it is primarily promotional or generic industry commentary: **2 points**
- Brand has no substantive editorial content: **0 points**

### Checkpoint 2.4 — Chunk-friendliness of content structure `[L2]`

Assess whether key pages are structured in a way that produces coherent, self-contained text chunks when segmented.

- Pages use clear heading hierarchy; paragraphs are self-contained and information-complete; no critical information locked in images or tables only: **5 points**
- Mixed: some well-structured sections, some that rely on visual layout or context to be understood: **2 points**
- Content is primarily visual, navigation-dependent, or structured in ways that produce incoherent chunks when extracted as text: **0 points**

### Checkpoint 2.5 — Query alignment test `[L1]`

Take 3 queries a target buyer might ask an AI about this category. For each query, identify which specific text from the brand's website would be relevant to retrieve. Can you find it?

- Clearly relevant, specific text exists for all 3 queries: **5 points**
- Relevant text exists for 1–2 queries: **2 points**
- No clearly relevant text exists for any of the 3 queries: **0 points**

**Dimension 2 subtotal: __ / 25**

---

## Dimension 3: External Citation Network

**Maximum score: 25 points**

### Checkpoint 3.1 — Industry media coverage `[L1]`

Search the brand name in 2–3 industry-specific publications or trade media relevant to the brand's category. Also search Google: "[brand name] site:[publication domain]"

- Coverage in 3 or more relevant industry publications in the past 2 years: **5 points**
- Coverage in 1–2 relevant industry publications: **3 points**
- No relevant industry media coverage: **0 points**

### Checkpoint 3.2 — Directory and database accuracy `[L1]`

Check the brand's presence and accuracy in: Alibaba/Global Sources (if applicable), industry association directories, Google Business Profile, LinkedIn company page, and 1–2 category-specific directories.

- Present in 4+ directories with accurate, consistent descriptions: **5 points**
- Present in 2–3 directories, descriptions mostly accurate: **3 points**
- Present in fewer than 2 directories, or descriptions significantly inaccurate: **0 points**

### Checkpoint 3.3 — Independent community references `[L2]`

Search for brand mentions in independent forums, communities, and discussion platforms: Reddit, industry-specific forums, B2B review platforms (G2, Capterra if applicable), and LinkedIn discussions.

- Authentic third-party discussions about the brand found in 3+ independent contexts: **5 points**
- Some independent references found: **2 points**
- No independent community references found: **0 points**

### Checkpoint 3.4 — Research and analyst coverage `[L2]`

Search for the brand in industry reports, analyst publications, academic references, or research contexts.

- Brand appears in 1 or more research/analyst contexts: **5 points**
- No research or analyst coverage found: **0 points**

### Checkpoint 3.5 — Description consistency across external sources `[L2]`

Compare how 5 external sources describe the brand. Assess consistency of: category, primary capability, geographic origin, and key differentiators.

- External descriptions consistent with each other and with how the brand defines itself: **5 points**
- Some inconsistencies but broadly aligned: **2 points**
- Significant inconsistencies, inaccuracies, or conflicting descriptions across external sources: **0 points**

**Dimension 3 subtotal: __ / 25**

---

## Dimension 4: Retrieval Infrastructure

**Maximum score: 25 points**

### Checkpoint 4.1 — Crawlability of key pages `[L1]`

Check robots.txt. Verify that homepage, About page, and core product pages are not blocked. Test that key pages render their text content without JavaScript execution (use a browser extension to disable JS and reload).

- All key pages crawlable with full text content available without JS: **5 points**
- Key pages crawlable but some content requires JS: **3 points**
- Key pages blocked or critical content locked behind JS rendering: **0 points**

### Checkpoint 4.2 — Sitemap presence `[L1]`

Check for sitemap at /sitemap.xml or referenced in robots.txt.

- Machine-readable sitemap present and includes key pages: **5 points**
- Sitemap present but incomplete or outdated: **2 points**
- No sitemap found: **0 points**

### Checkpoint 4.3 — Schema.org implementation `[L2]`

Use Google's Rich Results Test or a JSON-LD validator to check structured data on homepage and key pages.

- Organization schema with name, URL, description, address, and sameAs properties on homepage; relevant Product or Service schema on product pages: **5 points**
- Some schema present but incomplete or missing key properties: **2 points**
- No structured data present: **0 points**

### Checkpoint 4.4 — llms.txt presence `[L2]`

Check for /llms.txt file on the domain root.

- llms.txt present with accurate content summary: **5 points**
- Absent: **0 points**

### Checkpoint 4.5 — Heading structure `[L1]`

Inspect the heading hierarchy (H1–H3) on 3 key pages. Assess whether headings accurately describe the content that follows and would make sense as standalone labels in a retrieved chunk.

- Clear, descriptive heading hierarchy on all reviewed pages: **5 points**
- Mixed: some pages have good structure, others don't: **2 points**
- No meaningful heading structure: **0 points**

**Dimension 4 subtotal: __ / 25**

---

## Scoring Summary

| Dimension | L1 Checkpoints | L2 Checkpoints | Subtotal |
|-----------|---------------|---------------|---------|
| 1. Entity Definition Clarity | 1.1, 1.2, 1.3 | 1.4, 1.5 | __ / 25 |
| 2. Semantic Density | 2.1, 2.2, 2.5 | 2.3, 2.4 | __ / 25 |
| 3. External Citation Network | 3.1, 3.2 | 3.3, 3.4, 3.5 | __ / 25 |
| 4. Retrieval Infrastructure | 4.1, 4.2, 4.5 | 4.3, 4.4 | __ / 25 |
| **Total** | | | **__ / 100** |

---

## L1 Self-Assessment Score (8 checkpoints only)

For teams using only the public L1 checkpoints, the maximum score is 40 points (8 checkpoints × 5 points each). Interpret as follows:

| L1 Score | Interpretation |
|----------|----------------|
| 32–40 | Strong foundation on publicly visible indicators. Full L2 diagnostic recommended to identify deeper gaps. |
| 20–31 | Significant gaps visible in public-facing signals. High-priority remediation likely needed in at least 2 dimensions. |
| 0–19 | Foundational gaps. Brand likely has near-zero AI visibility. Systematic rebuild required before optimization is meaningful. |

---

## Priority Remediation Map

After scoring, identify the lowest-scoring dimension. Address dimensions in this order:

**If Dimension 4 (Infrastructure) is lowest:** Fix first. Content improvements have no impact if content cannot be crawled and indexed. Infrastructure is the prerequisite.

**If Dimension 1 (Entity Definition) is lowest:** Fix second. Inconsistent entity definition means improvements to other dimensions will attribute value to a fuzzy or incorrect brand representation.

**If Dimension 2 (Content Density) is lowest:** Fix third. This is the highest-leverage dimension for RAG retrieval performance and the one most directly actionable by the brand team.

**If Dimension 3 (Citation Network) is lowest:** Fix fourth. This is the longest-cycle dimension — it requires building external relationships and cannot be accelerated purely through owned-channel work.

---

## Related Documents

- [scoring-principles.md](../model/scoring-principles.md) — The rationale and design principles behind this scoring model
- [retrieval-mechanisms.md](../model/retrieval-mechanisms.md) — The technical mechanisms this diagnostic is designed to assess
- [entity-definition.md](../components/entity-definition.md) — Guidance on improving entity definition clarity
- [semantic-density.md](../components/semantic-density.md) — Guidance on improving content semantic density

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
