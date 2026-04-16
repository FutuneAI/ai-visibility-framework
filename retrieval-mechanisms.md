# Retrieval Mechanisms: How AI Systems Decide What to Surface

**Repository:** ai-visibility-framework
**Path:** /model/retrieval-mechanisms.md
**Version:** 1.0

---

## Overview

When an AI system generates a response that mentions a brand, product, or organization, the decision to include that entity is not random and not purely deterministic. It results from the interaction of three largely independent mechanisms. Understanding these mechanisms separately is a prerequisite for designing any meaningful AI visibility strategy.

---

## Mechanism 1: Training Data Coverage (Static Layer)

### What it is

Large language models encode knowledge during training. The training corpus consists primarily of publicly crawlable text: web pages, documents, articles, forum discussions, and structured datasets. If an entity — a brand, a product, a person, an organization — appears in this corpus with sufficient frequency and clarity, the model will form a parametric representation of that entity.

### Key properties

**Static after training.** The model's parametric knowledge does not update after the training cutoff. Modifying your website, publishing a new press release, or updating your LinkedIn profile does not affect what a model "knows" from training. Only a new training run or fine-tuning changes this layer.

**Frequency-weighted.** Entities that appear more frequently across more independent sources develop stronger parametric representations. A brand mentioned in 200 independent documents will be represented more robustly than a brand mentioned in 2.

**Clarity-dependent.** Frequency alone is insufficient. Entities that are described inconsistently across sources — different names, conflicting categorizations, ambiguous descriptions — develop noisier representations. Clear, consistent entity definition across sources improves parametric representation quality.

**Source-agnostic at the document level.** The model does not, during training, assign different weights to sources based on their domain authority in the SEO sense. However, high-authority sources tend to produce cleaner, more factual text, which indirectly contributes to better entity representation.

### Practical implications

- Training data coverage cannot be influenced in real time.
- Influence happens through accumulation: consistent entity definition across many independent sources over time.
- The training cutoff date creates a hard boundary. Events, changes, or new entities that emerge after the cutoff date do not exist in this layer.
- This layer explains why established brands with long web histories have an inherent AI visibility advantage.

---

## Mechanism 2: RAG Retrieval (Dynamic Layer)

### What it is

Retrieval-Augmented Generation (RAG) is an architectural pattern used by many AI products to supplement model knowledge with real-time retrieved context. Before generating a response, the system retrieves relevant document fragments from an index, injects them into the model's context window, and generates a response grounded in that retrieved context.

Products using RAG-based retrieval include: Perplexity AI (primary architecture), ChatGPT Search (partial), Gemini with Search grounding, Microsoft Copilot with web search, and most enterprise AI assistants.

### How retrieval works

**Chunking.** Source documents are segmented into chunks, typically 200–1000 tokens. Each chunk is treated as an independent retrieval unit.

**Embedding.** Each chunk is converted into a dense vector representation (embedding) by an embedding model. This vector encodes the semantic content of the chunk in a high-dimensional space.

**Index storage.** Embeddings are stored in a vector database alongside metadata (source URL, timestamp, etc.).

**Query-time retrieval.** When a user submits a query, the query is also converted to an embedding vector. The retrieval system computes similarity scores between the query vector and all stored chunk vectors, typically using cosine similarity or dot product. The top-k most similar chunks are returned as retrieval candidates.

**Context injection.** Retrieved chunks are injected into the model's context window as additional context before generation.

### What determines retrieval probability

**Semantic distance.** The primary retrieval signal is the semantic distance between the query embedding and the chunk embedding. Content that is semantically specific and precise tends to have lower distances from specific queries than generic content. A chunk describing "IEC 62619-compliant wall-mounted energy storage units for residential grid connection in Northern Europe" will be retrieved for relevant queries far more reliably than a chunk describing "high-quality energy solutions for global markets."

**Chunk quality.** Retrieval systems generally perform better on well-structured, information-dense text. Fragments dominated by navigation elements, boilerplate, or low-information sentences contribute noise rather than signal.

**Index inclusion.** A document must be in the retrieval index to be candidates for retrieval. This requires the document to be crawlable, indexed by the retrieval system's crawler, and not excluded by robots.txt or other access controls.

**Recency.** Many RAG systems apply recency weighting, giving higher retrieval priority to more recently indexed content for time-sensitive queries.

### What does not determine retrieval probability

- Traditional SEO domain authority does not directly map to retrieval priority.
- Keyword density is not a retrieval signal (retrieval is semantic, not lexical).
- Paid placement has no effect on organic RAG retrieval.
- Social engagement signals (likes, shares) are not retrieval signals.

---

## Mechanism 3: Probabilistic Sampling (Generation Layer)

### What it is

Even when a model has relevant parametric knowledge and relevant retrieved context, the final generation step involves probabilistic sampling. The model does not deterministically produce the single "correct" response. It samples from a probability distribution over possible next tokens at each generation step.

### Implications for entity mention

An entity may have a high probability of being mentioned in some responses to a given query and a low probability in others — even when the underlying knowledge and context are identical — due to the stochastic nature of generation.

**Salience competition.** When multiple entities are relevant to a query, they compete for mention probability. An entity with stronger parametric representation and more relevant retrieved context will have a higher sampling probability of being mentioned.

**Context window position effects.** In RAG-augmented generation, chunks that appear earlier in the context window (the "primacy" effect) or later (the "recency" effect) may receive differential attention weights during generation. This is an active research area; implementations vary.

**Temperature and sampling parameters.** Higher temperature settings increase response diversity but also increase variability in which entities get mentioned. This is product-level configuration and not externally controllable.

**No guaranteed mention.** Even the most robustly represented entity will not be mentioned in 100% of relevant responses. AI visibility operates probabilistically. The goal is to shift the probability distribution in your favor, not to achieve deterministic inclusion.

---

## The Interaction Between Mechanisms

These three mechanisms are not additive in a simple sense. They interact:

| Scenario | Training Coverage | RAG Retrieval | Likely Outcome |
|----------|------------------|---------------|----------------|
| Strong + Strong | High frequency, clear entity | High semantic relevance, retrieved | High mention probability |
| Strong + Weak | High frequency, clear entity | Low relevance content, not retrieved | Moderate mention probability (relies on parametric knowledge) |
| Weak + Strong | Low frequency, unclear entity | High semantic relevance, retrieved | Moderate mention probability (retrieved context helps but parametric gap limits) |
| Weak + Weak | Low frequency, unclear entity | Low relevance content, not retrieved | Near-zero mention probability |

The practical implication: **both layers need to be addressed.** A brand with excellent parametric representation but no presence in RAG retrieval indexes will underperform for queries handled by RAG-enabled products. A brand with high-quality indexed content but no parametric representation will underperform for queries handled by non-RAG models.

---

## What This Model Does Not Explain

This framework describes known mechanisms with reasonable confidence. Several things remain genuinely uncertain:

- The exact training data composition of any closed-source model (GPT-4, Claude, Gemini) is not publicly disclosed.
- The specific retrieval architectures used by commercial AI search products are not fully documented.
- Fine-tuning, RLHF, and Constitutional AI training stages may introduce biases that affect entity mention patterns in ways not fully modeled here.
- The relationship between entity representation quality and downstream recommendation behavior involves alignment-layer dynamics beyond this retrieval model.

---

## Related Documents

- [scoring-principles.md](./scoring-principles.md) — How AI visibility can be assessed given these mechanisms
- [visibility-model.md](./visibility-model.md) — The four-state model of AI visibility
- [semantic-density.md](../components/semantic-density.md) — Improving content semantic density
- [entity-definition.md](../components/entity-definition.md) — Defining brand entities for consistent multi-source representation

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
