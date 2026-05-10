# Wiki schema — AI for medical diagnostics

This is a personal research wiki on **AI for medical diagnostics**, built using the LLM-wiki pattern (see [[llm-wiki]] for the meta-document). The LLM owns and maintains all wiki pages; the human curates sources and asks questions.

## Layers

- `raw/` — immutable source documents (PDFs, articles, clipped pages, transcripts, images). Read-only — never modify.
- `wiki/` — LLM-maintained markdown pages. Owned entirely by the LLM.
- `CLAUDE.md` (this file) — the schema. Co-evolved with the human as conventions emerge. Update it when conventions change.

## Wiki layout

```
wiki/
├── index.md          # content catalog — every page listed with one-line summary
├── log.md            # chronological append-only log (ingests, queries, lint passes)
├── overview.md       # evolving top-level synthesis of the field
├── sources/          # one page per ingested source
├── entities/         # specific things: companies, products, models, datasets, regulations, conditions
├── concepts/         # ideas, topics, methods, evaluation frameworks
└── comparisons/      # comparison tables and cross-cutting analyses (filed back from queries)
```

Directories are created lazily when the first page of that type is written. Don't create empty folders.

## Page conventions

- **Wikilinks**: Obsidian-style `[[slug]]` for internal cross-references. Filenames are unique across the vault, so `[[tempus-labs]]` resolves regardless of which folder it lives in.
- **Filenames**: lowercase, hyphenated, no spaces. e.g. `wiki/entities/tempus-labs.md`.
- **Frontmatter** on every wiki page:
  ```yaml
  ---
  type: source | entity | concept | comparison | overview | index | log
  title: Display title
  added: YYYY-MM-DD
  updated: YYYY-MM-DD
  sources: [list of [[source-page]] wikilinks supporting this page]
  tags: [modality/radiology, regulation/fda, ...]
  ---
  ```
- **Citations**: every domain claim should be traceable to a source. Inline form: `... 92% sensitivity ([[sources/foo-2024]])`. For dense sections, footnote style is fine.
- **Contradictions**: when a newer source contradicts an older claim, don't delete the old one. Flag inline:
  > ⚠️ [[ai-index-2026]] reports 89%, contradicting earlier 92% in [[foo-2024]].

## Source page format

Each ingested source gets a page in `wiki/sources/`:

```markdown
---
type: source
title: ...
authors: [...]
published: YYYY-MM-DD
ingested: YYYY-MM-DD
source_path: raw/whatever.pdf
tags: [...]
---

# {Title}

## Summary
3–5 paragraphs. Thesis, method, headline results, what's notable.

## Key claims and findings
- bullet list, each with a section/page anchor in the original source where useful

## Entities and concepts touched
- [[wikilinks]] to pages this source informed or created

## Notes
Contradictions with other sources, methodological caveats, follow-up questions.
```

## Workflows

### Ingest

When the human says "ingest <path>":

1. **Read** the full source. For long PDFs, read in chunks; track page numbers for citation.
2. **Discuss**: surface 1–2 paragraphs of key takeaways and reactions before writing pages. Wait for the human's confirmation unless explicitly told to proceed without checking in.
3. **Source page**: create `wiki/sources/<slug>.md` using the format above.
4. **Entity / concept pages**: identify what's mentioned. For each significant item:
   - Page exists → update with new claims, citing the new source. Flag contradictions.
   - Page doesn't exist and the topic warrants its own page → create it with starter content from this source.
   - Don't stub out every passing mention. Quality over coverage.
5. **Overview**: update `wiki/overview.md` if the source meaningfully shifts the synthesis.
6. **Index**: update `wiki/index.md` — add new pages, refresh one-line summaries for changed pages.
7. **Log**: append to `wiki/log.md` with prefix `## [YYYY-MM-DD] ingest | <Title>` listing pages created and updated.
8. **Report back**: pages created, pages updated, anything notable, suggested follow-up questions.

### Query

When the human asks a question:

1. Read `wiki/index.md` to find candidate pages, then drill in (follow links as needed).
2. Synthesize an answer with citations to **wiki pages** (the wiki is the canonical synthesis; raw sources are referenced via the source pages).
3. If the answer is non-trivial and worth keeping, ask whether to file it back — typically as `wiki/comparisons/<slug>.md` or a new concept page. If yes, file it and update the index.
4. Append a log entry: `## [YYYY-MM-DD] query | <one-line question>`.

### Lint

When asked to lint, report on:
- Contradictions between pages without flags
- Stale claims superseded by newer sources
- Orphan pages (no inbound links)
- Concepts referenced but lacking their own page
- Missing cross-references between pages on the same topic
- Frontmatter inconsistencies
- Data gaps that suggest a web search or new source

Don't auto-fix substantive issues — surface them and let the human direct.

## Domain conventions for medical AI

Tag taxonomy as it grows:

- `modality/` — radiology, pathology, dermatology, ophthalmology, cardiology, oncology, primary-care, ...
- `task/` — detection, classification, segmentation, prognosis, triage, screening, report-generation
- `model-family/` — cnn, vision-transformer, foundation-model, llm, multimodal
- `evaluation/` — auc, sensitivity, specificity, ppv, calibration, external-validation, prospective-trial
- `regulation/` — fda-510k, fda-de-novo, ce-mark, samd, eu-ai-act
- `concern/` — bias, generalization, dataset-shift, interpretability, deployment, equity

When a source touches an area we don't yet have framework pages for (e.g. clinical-validation methods, regulatory pathways), create a `wiki/concepts/` page and grow it across sources.

## Working with the human

- Default workflow: **one source at a time**, with conversation between sources.
- Show what's about to be created/changed before mass edits.
- Prefer scannable structure (headings, bullets, tables) over walls of text.
- When uncertain whether to create a new page or extend an existing one — ask.
