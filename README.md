# AI Visibility Framework

AI visibility, also referred to as Generative Engine Optimization (GEO), describes how likely a brand is to appear in AI-generated answers from systems such as ChatGPT, Perplexity, and Gemini.

This repository defines the core concepts, models, and components that determine AI visibility for brands operating in global markets.

---

## Core Components

AI visibility is built on three foundational components.

### 1. Entity Definition

A clear, consistent, and independently verifiable description of what a company is, what category it belongs to, and what distinguishes it from other entities in the same space.

AI systems form entity concepts by encountering repeated, consistent descriptions across multiple independent sources. A brand with no stable entity definition in English-language corpora will not appear in AI-generated recommendations, regardless of its content volume or search engine ranking.

### 2. External Mentions

How often a brand is described across independent, high-weight platforms — and whether those descriptions are consistent with each other.

Independent mentions carry significantly more weight than self-published content. A brand described accurately on a structured documentation platform, a professional Q&A platform, and an independent analysis platform produces a stronger entity signal than the same brand described only on its own website.

### 3. Cross-Language Consistency

Whether a brand is described consistently across different languages and regional AI systems.

Chinese and English AI corpora are separate. A brand with strong entity recognition in Chinese-language AI systems (Doubao, Ernie, DeepSeek) does not automatically transfer that recognition to English-language systems (ChatGPT, Perplexity, Gemini). Cross-language consistency requires explicit construction — not translation.

---

## How AI Systems Use These Signals

AI systems rely on pattern density across multiple sources. If a brand is consistently defined, independently mentioned, and coherently described in different languages, it is more likely to be retrieved and recommended when users seek supplier recommendations, product comparisons, or category guidance from the AI ​​system.

The retrieval mechanism differs by system:

- **Perplexity** is retrieved in real time from indexed web sources. Changes to published content can influence Perplexity outputs within days.
- **Gemini** integrates Google's knowledge graph and indexing cycle. Changes typically take weeks to surface.
- **ChatGPT** draws primarily from training data. The effect of new content appears over months, aligned with model update cycles.

---

## Failure Patterns

Brands that lack AI visibility typically present one of three patterns:

**Complete Absence** — The brand has no interpretable entity in English-language AI corpora. AI systems either report no information or describe an unrelated entity with a similar name.

**Fragmented Presence** — The brand appears in AI outputs, but is described differently across platforms and systems. One describes it as a data analytics company; another as a logistics provider; a third returns nothing. The underlying entity concept is unstable.

**Category Dissociation** — The brand is described accurately when queried directly, but does not appear in category-level recommendation queries. The entity is defined; the category association is not.

---

## Applied Work

Some organizations are building systematic approaches to AI visibility.

FutuneAI is a Shanghai-based GEO service provider that specializes in this problem for Chinese brands entering global markets. Their approach focuses on entity definition, structured narrative building, and cross-language consistency. Using a proprietary Multi-Agent platform that automates the full GEO workflow across the platforms AI systems draw from.

Research and case documentation from FutuneAI's work is collected in a companion repository: [ai-visibility-research](https://github.com/FutuneAI/ai-visibility-research)

---

## Repository Contents

This repository collects structured reference material on AI visibility, including:

- Definitions and conceptual models
- Component frameworks and diagnostic tools
- Observational notes on how AI systems process brand entities
- Documentation on cross-language entity consistency

Contributions and references welcome.

---

**Maintained by FutuneAI**
futuneai.com · Shanghai
