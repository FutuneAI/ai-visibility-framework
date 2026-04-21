# Platform Weights: How Different AI Systems Form Brand Representations

**Repository:** ai-visibility-framework
**Path:** /components/platform-weights.md
**Version:** 1.0

---

## Overview

Not all AI systems form brand representations the same way. A brand that appears prominently in ChatGPT responses may be absent from Perplexity results, and vice versa. Understanding these differences benefits from examining how each major AI system acquires and uses information.

This document maps the primary AI platforms by their information architecture — specifically, how each platform's design affects the relative weight of training data versus real-time retrieval, and what that means for brand visibility strategy.

The following framework is a simplified model for reasoning about platform behavior. Actual system implementations are more complex and not fully disclosed.

---

## The Two-Axis Framework

AI systems often vary across multiple dimensions, with these two being among the most influential for brand visibility:

**Axis 1: Training-reliance vs. retrieval-reliance**
Some systems rely primarily on parametric knowledge encoded during training. Others retrieve real-time content before generating responses. Most use a combination, but the balance varies significantly.

**Axis 2: Open-web vs. curated sources**
Some systems draw from the broad public web. Others prioritize curated, high-authority sources. This determines which types of content are most influential.

| Platform | Primary mechanism | Source scope | Visibility lever |
|----------|------------------|--------------|-----------------|
| ChatGPT (no browsing) | Training-dominant | Open web (historical) | Training data coverage |
| ChatGPT Search | Training + RAG | Open web, real-time | Both layers |
| Perplexity | RAG-dominant | Open web, real-time | Retrieval candidacy |
| Gemini (standard) | Training-dominant | Google index + training | Training + Search index |
| Gemini with Search | Training + RAG | Google index, real-time | Google SEO + content density |
| Claude (standard) | Training-dominant | Open web (historical) | Training data coverage |
| Microsoft Copilot | Training + RAG | Bing index, real-time | Bing indexing + content density |
| Perplexity for Enterprise | RAG + curated | Selected premium sources | Premium source coverage |

---

## Platform-by-Platform Analysis

### ChatGPT (GPT-4, without browsing enabled)

**Primary mechanism:** Parametric knowledge from training data. No real-time retrieval in standard mode.

**Implication for brand visibility:** A brand's representation in ChatGPT is primarily influenced by patterns learned during training, with no direct access to real-time external content in standard mode. If a brand had a very limited or unclear presence in training data, it is less likely to appear in ChatGPT responses, regardless of current web presence.

**What influences it:**
- Volume of clear, consistent brand mentions across publicly crawlable sources before training cutoff
- Quality and specificity of those mentions (generic mentions contribute less than specific, attributed descriptions)
- Entity definition consistency across sources

**What does not directly influence it:**
- Current website content
- Recent press releases
- New blog posts published after training cutoff

**Strategic implication:** ChatGPT parametric visibility is a long-term accumulation problem. It cannot be fixed quickly. The primary lever is building a consistent, high-quality external presence over time so that future training runs include better brand representation.

---

### ChatGPT Search (browsing-enabled)

**Primary mechanism:** Hybrid — parametric knowledge supplemented by real-time Bing-based retrieval for queries that benefit from current information.

**Implication for brand visibility:** Brands can influence ChatGPT Search responses through current content quality and Bing indexing, even if their parametric representation is weak. Retrieval can supplement parametric knowledge and, in some cases, compensate for gaps in training data for specific queries.

**What influences it:**
- Bing index inclusion and crawlability of content
- Content semantic relevance to the query
- Page authority signals in Bing's ranking model
- Recency for time-sensitive queries

**Strategic implication:** Bing SEO is a meaningful lever for ChatGPT Search — not identical to Google SEO, but closely related. Brands that are well-indexed on Bing with high-density, category-relevant content have a direct path to ChatGPT Search visibility.

---

### Perplexity AI

**Primary mechanism:** RAG-dominant. Perplexity retrieves real-time sources for nearly all queries and grounds its responses in retrieved content. Parametric knowledge appears to play a less visible role compared to retrieval, as responses are typically grounded in cited sources, although the underlying model still influences synthesis and ranking.

**Implication for brand visibility:** Perplexity is the platform most directly influenced by current content quality and web presence. A brand with high-density, well-structured, and crawlable content may improve its chances of appearing in Perplexity results more quickly compared to training-dependent systems. However, outcomes still depend on query relevance and source authority.
platforms.

**What influences it:**
- Real-time crawlability of content
- Semantic relevance of content chunks to the query
- Source authority signals (domain trust, citation patterns)
- Content recency for current-information queries
- Structured page format (heading hierarchy, self-contained paragraphs)

**What does not influence it:**
- Keyword density (retrieval is semantic, not lexical)
- Meta descriptions (not a retrieval signal)
- Link-based authority signals (less transparent than Google)

**Strategic implication:** Perplexity is the highest-leverage platform for brands with good current content but weak historical training coverage. Investment in content density and technical crawlability has the fastest payback here.

---

### Gemini (Google)

**Primary mechanism:** Varies by product. Gemini standard relies heavily on training data. Gemini with Search grounding uses Google's Search index for real-time retrieval. Google AI Overviews (appearing in Google Search) also uses Search grounding.

**Implication for brand visibility:** Gemini's visibility is closely tied to Google SEO for the retrieval layer, but the training layer operates independently. Brands with strong Google SEO rankings are more likely to have an advantage in Gemini systems that incorporate Google Search results. AI Overviews are particularly influenced by Google's organic ranking signals.

**What influences it:**
- Google Search index inclusion and ranking (for retrieval-enabled versions)
- Training data coverage (for standard Gemini)
- Structured data markup (Schema.org — Google-native signal)
- Content quality and E-E-A-T signals (Experience, Expertise, Authoritativeness, Trustworthiness)

**Strategic implication:** For brands already investing in Google SEO, Gemini visibility is a natural extension of that work. The content requirements overlap significantly. Brands weak in Google SEO will be weak in Gemini retrieval.

---

### Microsoft Copilot

**Primary mechanism:** Training + Bing-based retrieval. Copilot (integrated in Microsoft 365 and Bing) draws on Bing's search index for web-sourced information.

**Implication for brand visibility:** Similar to ChatGPT Search but with deeper Microsoft ecosystem integration. Enterprise Copilot deployments may also access internal company knowledge bases — a separate channel entirely.

**What influences it:**
- Bing indexing and authority signals
- Content semantic density
- Microsoft ecosystem presence (LinkedIn, for enterprise contexts)

**Strategic implication:** Bing SEO is underinvested by most brands focused on Google. For brands targeting English-speaking markets, Bing indexing is a meaningful lever for both ChatGPT Search and Copilot visibility.

---

## Cross-Platform Strategy Implications

**There is no single optimization that reliably covers all platforms across all scenarios.** Each platform's architecture requires a different primary lever:

| Priority | Platform group | Primary lever |
|----------|---------------|---------------|
| Long-term parametric | ChatGPT, Claude | Multi-source training data accumulation |
| Real-time retrieval | Perplexity, ChatGPT Search | Content density + crawlability |
| Google ecosystem | Gemini, AI Overviews | Google SEO + Schema.org |
| Microsoft ecosystem | Copilot, Bing Chat | Bing indexing + LinkedIn presence |

**The overlapping foundation:** High-density, well-structured, clearly attributed content on a technically crawlable website is a prerequisite for all platforms. Platform-specific optimization builds on this foundation — it does not replace it.

**Training data is the slowest-moving lever.** Brands that are currently underrepresented in training data are unlikely to change this quickly. The realistic path is: build strong current content and external presence now, so that future training runs and retrieval-enabled systems can find the brand, and accept that parametric representation in training-dependent systems will improve on the timescale of months to years.

---

## Related Documents

- [retrieval-mechanisms.md](../model/retrieval-mechanisms.md) — Technical detail on training vs. RAG mechanisms
- [entity-definition.md](./entity-definition.md) — How entity definition affects cross-platform representation
- [semantic-density.md](./semantic-density.md) — Content density requirements for retrieval candidacy
- [scoring-principles.md](../model/scoring-principles.md) — How platform coverage is assessed in the visibility diagnostic

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
