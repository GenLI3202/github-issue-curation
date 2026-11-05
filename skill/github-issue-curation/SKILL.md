---
name: github-issue-curation
description: Create and curate GitHub issues to one shared team standard. Titles are short and follow one grammar, so the point lands at a glance; bodies are English-first with a Chinese translation under every paragraph, so teammates can collaborate across languages. Also covers TL;DR and Scope sections, restrained label governance, importance/urgency classification, raw-issue enrichment, and post-write QA. Use when a user asks to file, draft, clean up, classify, rename, translate, prioritize, or standardize issues; do not use it to implement the issues themselves.
---

# GitHub Issue Curation

Keep a team's GitHub issues in one consistent, evidence-bounded format — whether filing a new issue or turning an inconsistent backlog into a readable working system — without erasing issue history or silently changing project priorities.

Two entry points share the same rules:

- **Filing a new issue** — go to [Filing a new issue](#filing-a-new-issue), then apply sections 2, 4, and 6 for labels, title, and body.
- **Curating an existing backlog** — follow sections 1–10 in order.

## Operating boundary

- Resolve the exact repository before reading or writing.
- Read current issues, full bodies, states, labels, assignees, milestones, and relationships before proposing changes.
- Inspect repository authority, code, tests, documentation, or artifacts only when priority, scope, or completion claims depend on them.
- Treat issue and label changes as external mutations. Read-only inspection does not authorize edits, closures, new issues, or relationship changes.
- If the user asks to discuss taxonomy or priority first, stop after the proposal and wait for confirmation.
- Preserve unrelated labels, assignments, milestones, comments, and issue states unless the user explicitly includes them in scope.
- Do not edit local project files merely to curate GitHub metadata.

## 1. Inventory before designing

Build a compact inventory of every issue in scope:

- number, state, title, and body quality;
- current category, priority, and topic labels;
- whether the issue is a research question, experiment, implementation, architecture boundary, visualization, or other project-specific type;
- dependencies, parent/child relationships, and linked evidence;
- empty, stale, duplicated, partially completed, or apparently completed items.
- raw notes that contain only a title, fragment, or one-sentence idea and need enough context for another reader to understand them.

Use live GitHub state as authority. Historical notes may help locate context but never replace current verification.

## 2. Separate three label dimensions

Do not mix these dimensions in one label family:

1. **Category** — what kind of work it is.
2. **Priority** — importance and urgency relative to the current programme, not permanent intrinsic value.
3. **Topic** — a cross-cutting subject that can span categories.

Infer categories from the actual backlog. Respect any user cap, such as no more than five categories. Discuss ambiguous assignments rather than forcing a clean-looking taxonomy.

Use the repository's existing priority labels when it has them. Otherwise, agree a vocabulary with the user before creating labels. An optional importance/urgency convention is available; when the user chooses the Chinese vocabulary, use these exact label names instead of Q1–Q4:

- `重紧` — important and urgent;
- `重缓` — important but not urgent;
- `紧轻` — urgent but less important;
- `缓轻` — neither important nor urgent.

It is valid for a quadrant to be empty. A completed issue should normally be verified and closed rather than mislabeled as low priority.

Treat topic labels as an evolving project vocabulary, not a taxonomy to design exhaustively up front:

- identify the project's recurring technical components, research directions, product areas, or operational domains from the actual issues;
- add a topic label only when it improves retrieval, connects multiple issues, or represents a durable direction;
- add new topic labels incrementally as new issue content reveals a real need;
- avoid one-off labels, speculative future labels, and project-specific defaults carried over from another repository;
- periodically consolidate synonyms instead of accumulating near-duplicate tags.

Keep label descriptions concise and in English for mixed-language collaboration unless the user requests another language. Preserve standard GitHub labels unless removal is explicitly requested.

## 3. Agree before mutating

Present the proposed taxonomy and issue-to-priority mapping with short reasons. Surface decisions that change meaning, including:

- whether an apparently completed issue should close;
- whether a future feature is important or merely optional;
- whether an empty issue has enough information to scope;
- whether a broad issue crosses system or evidence layers and should split.

Do not manufacture urgency from issue age. Define urgency through current blockers, near-term decisions, deadlines, or explicitly active work.

## 4. Normalize titles exactly

Derive or confirm one title grammar before applying it across the backlog, then follow it literally. A useful bilingual compact convention is:

```text
【category】Short English description|极简中文关键词
```

Keep the English description short and specific. Keep the Chinese suffix to a few identifying words. Preserve acronyms that the repository actually defines; do not expand or reinterpret unknown acronyms. Treat this as a configurable convention, not a universal requirement when the user chooses another format.

## 5. Expand raw issues without inventing detail

A raw issue may be empty, a sentence fragment, or a quick note written before the author had time to structure it. Curation should make it understandable and actionable enough for later discussion without converting it into an unapproved specification.

For each raw issue:

1. Recover the minimum supported intent from its title, body, linked issues, repository terminology, and directly relevant docs or code.
2. Write a concise TL;DR that states the problem or idea, not an assumed solution.
3. Add a bounded Scope that distinguishes what the issue covers, what it does not yet decide, and any prerequisite.
4. Add a TODO or open question only when a concrete missing fact blocks further scoping.
5. Preserve the original fragment under `## Original note` when it carries useful provenance.

Do not invent owners, deadlines, interfaces, acceptance thresholds, implementation plans, or evidence. Mark material gaps as pending and ask the user when different answers would change the issue's meaning or priority. Keep an idea as an idea; enrichment must not silently promote it to planned work.

## 6. Normalize bodies without losing history

Lead every issue with a short English TL;DR and a bounded Scope. Put the Chinese translation immediately under the matching English content as a Markdown blockquote.

Paragraph pattern:

```markdown
English paragraph.

> 对应中文翻译。
```

Bullet pattern:

```markdown
- English bullet.

  > 对应中文翻译。
```

Numbered-item pattern:

```markdown
1. English item.

   > 对应中文翻译。
```

Rules:

- Translate each paragraph separately.
- Put one Chinese quote directly under each English bullet; never collect all Chinese bullets at the end of the list.
- Keep every Chinese body line inside a quote block. For multi-line quotes, include `>` on every quoted line.
- Keep actionable checkboxes only in the English primary text; the Chinese line is an annotation, not a second checkbox.
- Preserve formulas, code, links, issue numbers, units, case IDs, and evidence qualifications.
- Preserve detailed legacy content unless the user authorizes trimming. Rename a misleading legacy heading if necessary, but do not silently delete its content.
- For an empty or underspecified issue, write only what the title and verified context support. Mark missing facts as pending or TODO instead of inventing them.

Recommended top structure:

```markdown
## TL;DR

Concise English summary.

> 简短中文翻译。

## Scope

- Bounded English scope item.

  > 对应中文翻译。
```

## 7. Express layer boundaries with sub-issues when needed

This is an optional decomposition tool, not a default step. Split an issue when one item improperly combines outputs and claims from different system or evidence layers. For example, a measurement or benchmarking issue should produce its results before a downstream issue interprets business or compliance effects.

When splitting:

- keep the parent responsible for its own layer's question and outputs;
- make those outputs explicit inputs to the child;
- state what the child must not attribute back to the parent;
- create a formal GitHub sub-issue relationship when supported, otherwise add reciprocal links;
- do not create the child until the user accepts the decomposition or has clearly delegated that judgment.

## 8. Verify before closing when closure is in scope

Do not infer completion from a title, screenshot, old test result, or one implemented component. Compare the current implementation with every Scope item.

Use proportionate evidence:

- source and configuration for implementation presence;
- focused tests for behavior;
- documentation and artifacts for research traceability;
- screenshots for visible UI evidence only;
- live issue state for metadata claims.

If some acceptance items remain, mark the issue as partially complete and keep it open. When closure is authorized and all scope is verified, add a concise completion record and close it with the correct reason.

## Filing a new issue

Use this when a user wants to raise a single new issue. Filing is an external mutation: draft first, create only after the user approves the draft.

1. **Resolve the repository** explicitly (`owner/name`) before reading or writing.
2. **Check for duplicates.** Search open and closed issues for the same problem. If a match exists, show it and ask whether to comment there instead.
3. **Read the repository's conventions.** List existing labels, and look at a few recent issues and any issue templates (`.github/ISSUE_TEMPLATE`) so the new issue matches what is already there. A repository template takes precedence over the structure below; still apply the title grammar and bilingual rules unless the user says otherwise.
4. **Recover only what is supported.** Draw intent from the user's words and directly relevant context. Do not invent owners, deadlines, interfaces, acceptance thresholds, or evidence. Ask only when different answers would change the issue's meaning.
5. **Draft** the title (section 4) and body (section 6): TL;DR, bounded Scope, and a TODO or open question only when a concrete missing fact blocks scoping. Keep an idea as an idea; do not present it as planned work.
6. **Choose labels** from existing ones across the category, priority, and topic dimensions (section 2). Do not create a new label just for one issue; propose it and wait for approval.
7. **Show the draft** — title, body, labels, and target repository — and wait for an explicit yes.
8. **Create it** with the GitHub CLI or an available connector, then re-read the live issue and verify title grammar, quote blocks, and labels (section 10). Never blindly retry an uncertain creation; inspect live state first.
9. **Report** the issue number and URL, and state that no local project files were changed.

## 9. Apply changes safely

1. Inventory the backlog and identify raw issues.
2. Discuss category, priority, and any material scope interpretations.
3. Create or update only the agreed labels.
4. Normalize titles and enrich bodies while preserving unrelated metadata.
5. Create approved child issues or close verified issues only when those optional actions are in scope.
6. Never blindly retry an uncertain creation or relationship mutation; inspect live state first.

Use the GitHub CLI or an available GitHub connector. Prefer exact JSON reads for inventory and final verification. Resolve the target repository explicitly when the working directory is not sufficient.

## 10. Post-write QA

After every batch, re-read live GitHub state and verify:

- every issue in scope was processed exactly once;
- title grammar and category match;
- TL;DR and Scope exist and remain bounded;
- raw issues gained enough verified context to be understandable without gaining invented commitments;
- each English paragraph or list item is followed by its Chinese quote;
- no Chinese body line sits outside a quote block;
- no grouped Chinese translation list remains after an English list;
- label descriptions are non-empty English when that convention is active;
- each issue has the agreed category, priority, and topic labels, with valid exceptions documented;
- detailed legacy sections, formulas, links, and evidence boundaries remain present;
- issue state and any optional parent/child relation or completion reason are correct.

Report counts, closures, new relationships, validation evidence, and any unresolved gaps. State explicitly when no local project files were changed.

## Stop conditions

Pause and ask rather than guess when:

- category or importance materially depends on an unresolved project direction;
- an external interface or acronym is undefined;
- closing would require unverified implementation or acceptance evidence;
- splitting an issue would change ownership or research claims;
- the requested rewrite would remove detailed history or evidence boundaries.
