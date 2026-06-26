# Wiki Schema

## Domain
Software engineering: codebases, systems design, tooling, architecture, delivery, operations, and engineering practices.

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `event-driven-architecture.md`)
- Every wiki page starts with YAML frontmatter
- Use `[[wikilinks]]` to connect related pages; aim for at least 2 outbound links per page
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- On pages synthesizing 3+ sources, append provenance markers like `^[raw/articles/source-file.md]` at the end of source-specific paragraphs
- Prefer concise, scannable pages; split any page over ~200 lines into smaller pages
- If claims conflict, preserve both positions, note the contradiction in frontmatter, and flag it in the log

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
confidence: high | medium | low
contested: true
contradictions: [other-page-slug]
---
```

## Raw Source Frontmatter
Raw sources in `raw/` also get a minimal frontmatter block:

```yaml
---
source_url: https://example.com/article
ingested: YYYY-MM-DD
sha256: <hex digest of the body>
---
```

## Tag Taxonomy
Use only these top-level tags on wiki pages:
- architecture
- api
- backend
- frontend
- database
- devops
- testing
- security
- observability
- performance
- distributed-systems
- tooling
- product
- workflow
- concept
- entity
- comparison
- timeline
- incident
- reference

Add a new tag here before using it anywhere else.

## Page Thresholds
- Create a page when an entity or concept appears in 2+ sources, or is central to one source
- Add to an existing page when a source mentions something already covered
- Do not create pages for passing mentions or minor details
- Split a page when it exceeds ~200 lines
- Archive a page when it is fully superseded

## Page Types
### Entity
A concrete thing: service, product, repository, person, team, or tool.

### Concept
An idea or pattern: caching, event sourcing, monorepo hygiene, CI pipelines.

### Comparison
Side-by-side analysis of alternatives.

### Query
A filed answer to a question worth preserving.

### Summary
A synthesized overview or source digest.

## Update Policy
When new information conflicts with existing content:
1. Prefer newer sources when appropriate
2. Preserve genuinely conflicting claims side by side
3. Mark the page with `contested: true` and `contradictions: [...]`
4. Record the conflict in `log.md`
