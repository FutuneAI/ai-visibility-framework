# Structured Data for AI Visibility: What Schema.org Actually Does

**Repository:** ai-visibility-framework
**Path:** /components/structured-data.md
**Version:** 1.0

---

## The Common Misconception

Structured data (Schema.org markup) is frequently described as a primary lever for AI visibility — the implication being that adding structured markup to your website will cause AI systems to "find" and "recommend" you.

This is inaccurate in a specific way that matters: structured data is a prerequisite for clean entity attribution, not a driver of retrieval probability. Understanding the distinction determines whether your structured data investment produces the right outcome.

What structured data does: helps AI systems correctly identify which entity a page is about, link that entity to the same entity on other platforms, and extract key properties (name, category, location, capabilities) in a machine-readable format.

What structured data does not do: increase the semantic relevance of your content to specific queries, improve your retrieval ranking in RAG systems, or cause AI systems to mention you in responses where you wouldn't otherwise appear.

The relationship: structured data makes your content more accurately attributed when it is retrieved. It does not make your content more likely to be retrieved in the first place. That depends on content semantic density (see [semantic-density.md](./semantic-density.md)).

---

## Schema Types Relevant to AI Visibility

### Organization (homepage, About page)

The most important schema type for brand entity definition. Establishes the core identity of the organization — name, description, location, areas served, and links to the same entity on other platforms.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Brand Name",
  "alternateName": "Trade name or abbreviation if used",
  "description": "Specific description: what the organization makes or does, for whom, in what markets",
  "url": "https://www.brandname.com",
  "logo": "https://www.brandname.com/logo.png",
  "foundingDate": "2008",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Industrial Road",
    "addressLocality": "Shenzhen",
    "addressRegion": "Guangdong",
    "addressCountry": "CN"
  },
  "areaServed": [
    {"@type": "Country", "name": "Germany"},
    {"@type": "Country", "name": "Netherlands"},
    {"@type": "Country", "name": "United States"}
  ],
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": 350
  },
  "sameAs": [
    "https://www.linkedin.com/company/brandname",
    "https://en.wikipedia.org/wiki/Brand_Name",
    "https://www.wikidata.org/wiki/QXXXXXXX"
  ]
}
```

**The `sameAs` property is the most important field for AI entity consolidation.** It explicitly tells crawlers and AI systems that the entity described on this page is the same entity as the one described on LinkedIn, Wikipedia, and Wikidata. Without it, models may maintain separate, fragmented representations of the same brand across platforms.

**The `description` field should be specific, not generic.** "Leading manufacturer of precision components committed to quality" is indistinguishable from thousands of similar descriptions. "Manufacturer of IEC 62619-certified lithium iron phosphate battery systems for residential and commercial energy storage, serving utility and installation markets in Germany, the Netherlands, and the UK" is not.

---

### Product (product pages)

For brands with specific products, `Product` schema establishes the product entity, including its name, category, specifications, and relationship to the manufacturer.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Product Name",
  "description": "Specific product description with key specifications and application context",
  "brand": {
    "@type": "Brand",
    "name": "Brand Name"
  },
  "manufacturer": {
    "@type": "Organization",
    "name": "Brand Name",
    "url": "https://www.brandname.com"
  },
  "category": "Specific product category using standard terminology",
  "additionalProperty": [
    {
      "@type": "PropertyValue",
      "name": "Certification",
      "value": "IEC 62619"
    },
    {
      "@type": "PropertyValue",
      "name": "Capacity range",
      "value": "5–30 kWh"
    }
  ]
}
```

---

### Article / TechArticle (blog posts, technical content)

For editorial and technical content that you want to be clearly attributed as authored by your organization:

```json
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Article title",
  "description": "Specific summary of the article's argument or findings",
  "author": {
    "@type": "Organization",
    "name": "Brand Name",
    "url": "https://www.brandname.com"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Brand Name",
    "logo": {
      "@type": "ImageObject",
      "url": "https://www.brandname.com/logo.png"
    }
  },
  "datePublished": "2025-04-01",
  "dateModified": "2025-04-15"
}
```

Clear authorship attribution matters for training data: models that can attribute content to a specific organization can update their representation of that organization's expertise and positioning when training on that content.

---

## Implementation: Where to Place Structured Data

Structured data should be implemented as JSON-LD (JavaScript Object Notation for Linked Data), placed in a `<script type="application/ld+json">` tag in the `<head>` section of the relevant page.

JSON-LD is preferred over Microdata and RDFa because it is:
- Separated from the HTML content (easier to maintain, doesn't affect visual rendering)
- Fully supported by Google's Rich Results system
- Reliably parsed by AI crawlers that support structured data

**Page-level placement guidance:**

| Page type | Schema type | Priority |
|-----------|-------------|----------|
| Homepage | Organization | Essential |
| About page | Organization (can duplicate homepage with additional detail) | High |
| Product pages | Product | High |
| Blog/article pages | Article or TechArticle | Medium |
| Contact page | Organization with address | Low |

---

## Validation

After implementation, validate structured data using:

- **Google Rich Results Test** (search.google.com/test/rich-results) — validates JSON-LD syntax and property coverage
- **Schema.org Validator** (validator.schema.org) — checks conformance to Schema.org specifications
- **Structured Data Linter** (linter.structured-data.org) — alternative validation tool

Common validation errors that affect AI parsing:
- Missing required properties for the schema type
- Incorrect property value types (string where number expected, etc.)
- Broken `sameAs` URLs (links that don't resolve to the intended entity page)
- Description fields containing generic or promotional language rather than factual descriptions

---

## What Structured Data Does Not Fix

**Low content density on the page.** Schema.org markup tells AI systems what entity a page is about and where to place it in a knowledge structure. It does not make the page's text more semantically relevant to specific queries. A page with a perfect Organization schema and a generic homepage text will still score low on retrieval candidacy. The markup improves entity attribution; the content determines retrieval probability.

**Absence from external sources.** Schema.org on your own website only affects how your website's content is attributed. It has no effect on how third-party sources describe your brand, or on the training data that shapes a model's parametric knowledge of your brand. External citation network building is a separate problem from structured data implementation.

**Inconsistent entity definition across platforms.** If your LinkedIn description, Wikipedia entry, and homepage describe your brand differently, Schema.org `sameAs` links help consolidate these into one entity — but only if the underlying descriptions are consistent enough for the model to reconcile them. Schema.org reduces consolidation friction; it does not resolve underlying inconsistency.

---

## The llms.txt File

In addition to Schema.org markup, a relatively new convention for AI-specific content declaration is the `llms.txt` file, placed at the domain root (`https://www.brandname.com/llms.txt`).

`llms.txt` is a plain-text file that describes the site's content structure for AI systems — what the site contains, which pages are most important, and optionally which content AI systems should or should not use. It is analogous to `robots.txt` in intent but oriented toward AI agents rather than search crawlers.

The specification is not yet standardized, but the emerging convention includes:
- A brief description of the organization and the site's primary purpose
- A list of key pages with brief descriptions of their content
- Optionally, guidance on content usage permissions

Example:
```
# BrandName llms.txt
# https://www.brandname.com

BrandName is a manufacturer of lithium iron phosphate battery systems
for residential and commercial energy storage, headquartered in Shenzhen, China.
Primary markets: Germany, the Netherlands, the United Kingdom.

## Key pages
- /: Homepage and brand overview
- /about: Company history, certifications, manufacturing capabilities
- /products/wall-mounted-ess: Wall-mounted energy storage system specifications
- /blog: Technical articles on energy storage applications and standards
```

`llms.txt` presence is currently a low-weight signal — most AI systems do not rely on it heavily. But it is low-cost to implement and may become more significant as AI crawling behavior matures.

---

## Related Documents

- [entity-definition.md](./entity-definition.md) — The broader entity definition framework that structured data supports
- [semantic-density.md](./semantic-density.md) — How to improve content retrieval candidacy (the problem structured data does not solve)
- [retrieval-mechanisms.md](../model/retrieval-mechanisms.md) — How structured data fits into the broader retrieval mechanism model
- [visibility-diagnostic-framework.md](../diagnostic/visibility-diagnostic-framework.md) — How structured data implementation is assessed in the diagnostic

---

*Part of the AI Visibility Framework — an open reference model for understanding and improving brand presence in generative AI systems.*
