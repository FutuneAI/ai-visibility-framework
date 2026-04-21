# Entity Definition: How AI Systems Identify and Represent a Brand

**Repository:** ai-visibility-framework
**Path:** /components/entity-definition.md
**Version:** 1.0

---

## What Is a Brand Entity, in AI Terms

In the context of large language models, an "entity" is a discrete, identifiable thing that the model can represent, such as a person, organization, product, place, or concept. When a model is asked about a company, it draws on patterns learned during training, along with any retrieved context, to generate a representation of that company: what it is, what it does, where it operates, how it differs from similar entities.

Entity definition is the process of ensuring that this representation is accurate, complete, and consistent. Across the model's training data, across retrieval sources, and across the external information landscape that shapes both.

In practice, a poorly defined entity is more likely to result in one of three observable failure modes:
- **Absence:** the model has no representation of the brand and omits it from relevant responses
- **Confusion:** the model conflates the brand with a similarly named entity or misattributes properties
- **Degradation:** the model has a representation, but it is outdated, inaccurate, or incomplete in ways that produce incorrect descriptions

---

## The Four Properties of a Well-Defined Entity

### 1. Name consistency

The brand's primary name and any acceptable variants should be used consistently across all sources. This includes the brand's own website, social profiles, directory listings, press coverage, and any other externally visible surface.

Inconsistency creates disambiguation problems. A model that encounters "Acme Manufacturing," "Acme Mfg," "Acme Precision," and "Acme Co." across different sources may treat these as separate entities, split its representation, or fail to consolidate information correctly.

**What to standardize:**
- Primary brand name (exact spelling, capitalization, punctuation)
- Legal name vs. trade name (clarify the relationship explicitly where both appear)
- Abbreviated forms (if used, use them consistently and in the same contexts)
- Name in non-English markets (if operating across languages, define the relationship between language variants)

### 2. Category classification

The brand's primary category, what type of organization it is, what industry it operates in, and what it primarily makes or does.All of these should be described using consistent terminology across sources.

Category classification influences how a brand is positioned within semantic representations and how likely it is to be retrieved for relevant queries. A brand described as a "precision manufacturer" in some sources, a "CNC machining provider" in others, and a "custom metal components company" in others occupies an ambiguous position. The model may represent it accurately in some contexts and incorrectly in others.

**What to define:**
- Primary industry category (use standard industry terminology where it exists)
- Specific product or service category (what the brand actually makes or does)
- Customer segment (who it serves — B2B, B2C, specific industries, specific company sizes)
- Operational model (manufacturer, distributor, platform, service provider)

### 3. Geographic and operational scope

Where the brand is headquartered, where it operates, and what markets it serves should be clearly and consistently stated.

Geographic identity is particularly important for international brands, where the same company may be described differently in different language environments. A Chinese manufacturer expanding to English-speaking markets may be described with inconsistent geographic framing, sometimes as a "China-based manufacturer," sometimes with no geographic context, sometimes with its international subsidiary as the implied entity.

**What to define:**
- Headquarters location (city and country)
- Primary markets served (by geography or by industry vertical)
- Operational scale indicators (approximate employee count, annual revenue range, production capacity, whichever is most relevant and verifiable)
- Entity relationships (parent company, subsidiaries, operating brands, need to clarify the structure)

### 4. Differentiation claims

What makes this brand distinct from others in its category should be expressed in specific, verifiable terms, rather than merely making generalized claims of quality.

Generic differentiation ("committed to quality," "customer-first approach," "innovative solutions") contributes nothing to entity definition. Every brand in a category makes these claims. They create no distinction in a model's representation.

Specific differentiation does: named certifications, documented performance metrics, specific application contexts, named customer segments, and verifiable track records. These create a distinct position in semantic space that a model can represent and retrieve.

**What to specify:**
- Technical certifications and standards compliance (with the standards named explicitly)
- Documented performance metrics (defect rates, delivery times, capacity figures)
- Named specializations (specific materials, processes, industries, tolerances)
- Verifiable track record indicators (years in operation, units shipped, customer count in a specific segment)

---

## Where Entity Definition Needs to Happen

Entity definition is not a single-page problem. It requires consistency across multiple surfaces, each of which contributes to the model's parametric representation through training data and to real-time retrieval through indexed content.

**Priority surfaces:**

| Surface | Why it matters |
|---------|---------------|
| Homepage | Primary source for entity classification; usually the highest-crawled page |
| About page | Most explicit source of entity definition; models weight this heavily |
| Core product/service pages | Establishes category and capability specifics |
| LinkedIn company page | Indexed by some systems; contributes to entity association signals |
| Google Business Profile | Structured data format; directly feeds some AI knowledge sources |
| Wikipedia / Wikidata | Reference-layer sources; high weight in training data; explicit entity definition format |
| Industry directory listings | Category-specific entity signals; contribute to training data through aggregation |
| Press coverage | Third-party entity descriptions; high training data weight |

**The consistency test:** pull the entity description from five independent sources and compare. If the category, name, geographic scope, and primary capability are described consistently, the entity definition is working. If they differ meaningfully, inconsistency suppresses accurate representation.

---

## Entity Definition and Schema.org

Schema.org structured markup is the most direct way to provide a machine-readable definition of a website entity. The `Organization` schema type supports the key entity properties:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Brand Name",
  "alternateName": "Abbreviated or alternate name if used",
  "description": "Specific, accurate description of what the organization does",
  "url": "https://www.brandname.com",
  "foundingDate": "2005",
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": 500
  },
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "City",
    "addressCountry": "CN"
  },
  "areaServed": ["DE", "NL", "US"],
  "sameAs": [
    "https://www.linkedin.com/company/brandname",
    "https://en.wikipedia.org/wiki/Brand_Name"
  ]
}
```

The `sameAs` property is particularly important: it explicitly links the website entity to the same entity on other platforms, helping search engines and downstream AI systems better associate and align information about the same entity across sources.

Schema.org markup does not replace content-level entity definition. It supplements it. A page with perfect Schema.org markup and generic content will still have low semantic density for retrieval purposes. In practice, Schema.org markup improves explicit entity attribution signals, while content density increases the likelihood of being selected in retrieval-based systems.

---

## Common Entity Definition Failures

**Name drift across platforms.** The legal entity name is used on the website, a shortened trade name on LinkedIn, a romanized version on international directories, and an abbreviated form in press coverage. Inconsistent signals across sources can lead to less reliable or fragmented representations in both model outputs and retrieval results.

**Category ambiguity on the homepage.** The homepage leads with brand values or visual identity rather than a clear statement of what the company does. Models struggle to categorize the brand accurately.

**Absent geographic context.** No clear statement of where the company is based or what markets it primarily serves. For international brands, this creates uncertainty about which entity is being described.

**Generic differentiation only.** All differentiation claims are category-generic ("quality," "reliability," "innovation"). The model has no basis for distinguishing this brand from hundreds of similar entities.

**Inconsistent entity across language versions.** The Chinese-language version of the website describes the company differently from the English-language version. Refer to different scope claims, different capability descriptions, and different named certifications. Models that index both versions form a fragmented representation.

---

## Related Documents

- [semantic-density.md](./semantic-density.md) — How to improve content information density for retrieval
- [structured-data.md](./structured-data.md) — Schema.org implementation for AI visibility
- [retrieval-mechanisms.md](../model/retrieval-mechanisms.md) — How entity representations are formed and used in AI responses
- [scoring-principles.md](../model/scoring-principles.md) — How entity definition clarity is assessed in the visibility diagnostic

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
