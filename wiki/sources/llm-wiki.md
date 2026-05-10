---
type: source
title: LLM Wiki — a pattern for personal knowledge bases with LLMs
authors: [unattributed]
published: ~2026
ingested: 2026-05-10
source_path: raw/llm-wiki.md
tags: [meta, methodology]
---

# LLM Wiki (meta-document)

> Methodology source, not a domain source. This is the blueprint that defines how this entire wiki operates. The concrete instantiation for this project lives in [[CLAUDE]].

## Summary

The "LLM Wiki" pattern proposes that LLMs maintain a **persistent, compounding** knowledge base instead of just doing query-time RAG over raw documents. The LLM ingests sources once, integrates them into an interlinked markdown wiki — entity pages, concept pages, summaries, an evolving synthesis — and keeps that wiki current as new sources arrive. The cross-references, contradictions, and synthesis are pre-computed; queries hit the compiled wiki rather than re-deriving everything from raw chunks each time.

The core insight is that maintenance, not reading, is the bottleneck for human-built wikis: updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. LLMs eliminate that cost — they don't get bored, don't forget to update a cross-reference, and can touch 10–15 files in one pass. The human's job becomes curating sources, directing analysis, and asking good questions; the LLM does the bookkeeping.

Architecturally there are three layers:
1. **Raw sources** — immutable. The LLM reads but never modifies.
2. **The wiki** — LLM-owned markdown files: summaries, entity pages, concept pages, comparisons, an overview.
3. **The schema** — a `CLAUDE.md` (or `AGENTS.md`) that codifies conventions and workflows. Co-evolved with the human.

Three operations: **ingest** (process a new source and propagate updates across the wiki), **query** (answer questions, optionally filing the answer back as a wiki page), and **lint** (periodically health-check for contradictions, stale claims, orphans, missing pages, gaps).

## Key claims and findings

- **Persistent compounding artifact** is the central differentiator vs. RAG / NotebookLM / ChatGPT file uploads — those re-derive on every query; this builds once and maintains.
- **File query results back** into the wiki as comparison or concept pages — explorations should compound, not disappear into chat history.
- **Two index files**: `index.md` (content-oriented, by category) and `log.md` (chronological, append-only, with parseable `## [YYYY-MM-DD] op | subject` prefix).
- **Index-based retrieval** scales to ~hundreds of pages without embedding/vector RAG. Adopt a search tool only when the index stops being enough.
- **Obsidian** is the recommended viewer — graph view shows wiki shape, Web Clipper imports articles, Marp/Dataview plugins enable extra outputs.
- **The wiki is just a git repo of markdown files** — version history, branching, collaboration come for free.
- Spiritual ancestor: **Vannevar Bush's Memex (1945)** — private, curated, with associative trails as valuable as the documents themselves. The unsolved part was who maintains it; LLMs solve that.
- The document is **intentionally abstract and modular** — "pick what's useful, ignore what isn't." Structure, conventions, and tooling are domain-dependent.

## Bootstrap choices made for this project (2026-05-10)

Codified in [[CLAUDE]]:
- Obsidian-flavor `[[wikilinks]]` (slug-only, since Obsidian resolves filenames across the vault).
- YAML frontmatter on every page (`type`, `title`, `added`, `updated`, `sources`, `tags`).
- Directory split: `sources/`, `entities/`, `concepts/`, `comparisons/`, plus top-level `index.md`, `log.md`, `overview.md`. Lazy directory creation.
- One-at-a-time ingest workflow with human-in-the-loop discussion before mass writes.
- Domain-specific tag taxonomy for medical AI (modality, task, model-family, evaluation, regulation, concern).
- Contradictions flagged inline rather than overwriting older claims.

## Entities and concepts touched

None — methodology source, not domain content. No entity or concept pages created from this ingest.

## Notes

- Tooling tips not adopted yet (revisit when relevant): [qmd](https://github.com/tobi/qmd) for hybrid BM25/vector search if the wiki outgrows the index file; Obsidian image-download hotkey; Marp slides; Dataview queries.
- This wiki is **not yet a git repo** (system reports the directory isn't under git). The pattern recommends git for free version history — worth raising with the human as the wiki accumulates content.
- The schema in [[CLAUDE]] is meant to be co-evolved. Update it whenever conventions change, rather than letting practice drift from the documented pattern.
