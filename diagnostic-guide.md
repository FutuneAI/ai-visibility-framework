# Diagnostic Guide: The Four States of AI Visibility

**Repository:** ai-visibility-framework
**Path:** /diagnostic-guide.md
**Version:** 1.0

---

## Purpose

This guide provides a practical framework for determining which of four AI visibility states a brand currently occupies, and what actions correspond to each state.

It is designed to be used before the full diagnostic (see [visibility-diagnostic-framework.md](./diagnostic/visibility-diagnostic-framework.md)) — as a quick triage to understand where to focus, rather than a comprehensive scoring exercise.

---

## The Four States

### State 1: Complete Absence

**Definition:** The AI system has no usable representation of the brand. The brand does not appear in responses about its category, and when queried directly, the system either disclaims knowledge, produces a confabulated description, or describes a different entity with a similar name.

**How to identify it:**

Run these three tests across at least two AI systems (e.g., ChatGPT and Perplexity):

*Test A — Direct brand query:*
Ask: "What is [Brand Name]? What do they do?"
→ If the system says it doesn't know, confabulates a plausible but inaccurate description, or describes a different company: **likely State 1**

*Test B — Category query without naming the brand:*
Ask: "Which [category] companies in [geography] are known for [specific capability]?"
→ If the brand never appears across multiple variations of this query: **consistent with State 1**

*Test C — Name disambiguation:*
Ask: "Is there a company called [Brand Name] that makes [product]?"
→ If the system cannot confirm basic facts: **State 1 confirmed**

**Root causes (most common):**
- Brand name is too generic or shared with a more prominent entity
- No English-language web presence or extremely limited presence
- All web presence is on platforms that are poorly crawled (WeChat, closed platforms)
- Company is too recently founded to appear in training data
- Brand operates entirely through distributors with no direct web identity

**Priority actions:**
1. Establish basic English-language web presence with clear entity definition
2. Create or claim Wikipedia/Wikidata entry if brand meets notability criteria
3. Ensure brand appears in at least 3 independent, crawlable external sources
4. Implement Organization Schema.org markup on homepage
5. Register and complete Google Business Profile and LinkedIn company page

---

### State 2: Partial or Inaccurate Representation

**Definition:** The AI system has a representation of the brand, but it contains errors, is outdated, or conflates the brand with another entity. The system can be prompted to describe the brand, but the description is wrong in ways that matter — wrong category, wrong geography, wrong capabilities, wrong ownership.

**How to identify it:**

*Test A — Description accuracy:*
Ask: "Tell me about [Brand Name] — what do they make and where are they based?"
→ Compare the AI response to accurate facts. Note specific errors.

*Test B — Category placement:*
Ask: "What type of company is [Brand Name]?"
→ If the category is wrong or too broad: **State 2 indicator**

*Test C — Cross-platform consistency:*
Run the same queries on ChatGPT, Perplexity, and Gemini.
→ If different systems produce meaningfully different descriptions of the same brand: **State 2 confirmed** — the brand's representation is fragmented across the information landscape

**Common error patterns:**
- Brand is described as its parent company or a subsidiary (entity confusion)
- Old product lines or discontinued capabilities still dominate the description
- Geographic scope is wrong (described as domestic when international, or vice versa)
- Brand name is confused with a similarly named company in a different category
- Key differentiators are absent; description is generic and interchangeable with competitors

**Root causes:**
- Inconsistent entity definition across external sources (see [entity-definition.md](./components/entity-definition.md))
- Old information dominates training data; recent changes not yet reflected
- Brand name creates disambiguation confusion
- Chinese-language presence not aligned with English-language presence

**Priority actions:**
1. Audit all external source descriptions for the specific errors the AI is producing
2. Correct Wikipedia/Wikidata entries if they contain errors (these are high-weight sources)
3. Standardize entity definition across all owned and controllable external surfaces
4. Publish content that explicitly states the correct information in the format AI systems cite (industry media, authoritative directories)
5. Use Schema.org `sameAs` to link all brand profiles to a single canonical entity

---

### State 3: Accurate but Passive Representation

**Definition:** The AI system can describe the brand accurately when asked directly, but the brand does not surface proactively in category-level or recommendation queries. The model "knows" the brand exists but does not associate it strongly enough with specific use cases to surface it unprompted.

This is the most common state for established brands that have not actively built AI visibility. It is also the state most often misdiagnosed as "good" — because the brand appears when searched directly, teams assume visibility is adequate. The problem is that most buyer queries don't name brands — they describe needs.

**How to identify it:**

*Test A — Direct query (should work in State 3):*
Ask: "What is [Brand Name]?"
→ System provides accurate description ✓

*Test B — Category query (the diagnostic test):*
Ask: "Which companies should I consider for [use case] in [geography]?"
Variations: "What are the top [category] suppliers for [application]?"
→ If the brand never appears across 10+ variations of category queries: **State 3 confirmed**

*Test C — Comparison query:*
Ask: "How does [Brand Name] compare to [Competitor]?"
→ If the system struggles or deflects rather than producing a comparison: **State 3 indicator**

**Root causes:**
- Content exists but lacks semantic specificity — it doesn't associate the brand with specific use cases, applications, or buyer queries
- External citations exist but are generic (directory listings, not substantive descriptions)
- Brand is described in general terms everywhere; no source creates a specific association between brand and particular buyer needs
- Content is technically accessible but semantically thin — passes crawl but fails retrieval relevance for specific queries

**Priority actions:**
1. Map the 5–10 specific queries target buyers would ask an AI about this category
2. For each query: identify whether any owned content would be semantically relevant to retrieve — if not, create it
3. Shift content strategy from general capability descriptions to specific use-case and application content
4. Publish in industry media with content that explicitly addresses specific buyer questions
5. Build external references that associate the brand with specific applications, not just the general category

---

### State 4: Active Recommendation Presence

**Definition:** The brand surfaces proactively when users ask AI systems about relevant categories, use cases, or supplier recommendations — without naming the brand in the query. This represents functional AI visibility.

**How to identify it:**

Run 20+ variations of category and use-case queries across 3+ AI platforms. If the brand appears in responses to at least half of relevant queries on at least two platforms: **State 4 confirmed**

Note: State 4 is probabilistic, not absolute. A brand in State 4 will not appear in every relevant response — AI generation is non-deterministic. The diagnostic indicator is consistent appearance across a pattern of queries, not 100% inclusion.

**Maintenance actions (State 4 is not permanent):**
- Monitor for accuracy degradation — active presence can coexist with description errors
- Track competitor visibility — if competitors move into State 4, relative visibility shifts
- Continue external citation building — parametric representation can decay if a brand's information footprint doesn't keep pace with industry growth
- Update content as capabilities, markets, or positioning changes — old associations can persist and become inaccurate

---

## Quick Triage Decision Tree

```
Q1: When you ask an AI "What is [Brand Name]?" — does it know?
│
├── No / Wrong answer → State 1 or State 2
│   │
│   └── Q2: Is the answer completely absent, or wrong in specific ways?
│       ├── Completely absent → State 1
│       └── Wrong but present → State 2
│
└── Yes, accurate → State 3 or State 4
    │
    └── Q3: Does the brand appear in category queries WITHOUT being named?
        ├── Rarely or never → State 3
        └── Consistently → State 4
```

---

## Using This Guide with the Full Diagnostic

This guide identifies which state a brand is in. The [visibility-diagnostic-framework.md](./diagnostic/visibility-diagnostic-framework.md) identifies *why* — which structural gaps are causing the state, scored across four dimensions (entity definition, content density, external citation network, retrieval infrastructure).

The recommended sequence:
1. Use this guide to determine current state (15–30 minutes)
2. If State 1 or 2: address the root causes identified here before running the full diagnostic
3. If State 3: run the full diagnostic to identify which structural dimensions need work
4. If State 4: use the full diagnostic for monitoring and maintenance

---

## Related Documents

- [visibility-diagnostic-framework.md](./diagnostic/visibility-diagnostic-framework.md) — Full scored diagnostic protocol
- [retrieval-mechanisms.md](./model/retrieval-mechanisms.md) — Why each state occurs mechanistically
- [entity-definition.md](./components/entity-definition.md) — Primary lever for States 1 and 2
- [semantic-density.md](./components/semantic-density.md) — Primary lever for State 3
- [scoring-principles.md](./model/scoring-principles.md) — How to measure progress between states

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
