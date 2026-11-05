# github-issue-curation

[简体中文](README.zh-CN.md)

An AI-agent skill that lets a whole team file and curate GitHub issues to **one shared standard**.

## Why this standard

- **Short, uniform titles — the point lands at a glance.** Every title follows one grammar, `【category】Short English description|极简中文关键词`, so a backlog can be scanned in seconds and the type and subject of each issue are obvious without opening it.
- **Bilingual bodies — easy cross-language collaboration.** Each issue leads with an English TL;DR and a bounded Scope, and a Chinese translation sits directly under every English paragraph or bullet as a quote block. English readers and Chinese readers work from the same text, with no separate translated copy to drift out of sync.
- **Restrained labels.** Category, priority, and topic are kept as separate label dimensions, and new labels are added only when they earn their place.
- **No invented detail.** Raw one-line notes are expanded only with what the title and verified context support; nothing is promoted to planned work silently.

## What it does

| Mode | When | What happens |
| --- | --- | --- |
| **File a new issue** | You want to raise one issue | Checks for duplicates, reads the repo's labels and templates, drafts title + body + labels, shows you the draft, creates it only after you approve, then verifies the live issue. |
| **Curate a backlog** | You want to clean up, rename, translate, classify, or prioritize existing issues | Inventories live issues, agrees a taxonomy with you, normalizes titles and bodies, applies changes in batches, and re-reads GitHub to check the result. |

The skill never implements the issues themselves, and every create, edit, or close is an external change that waits for your approval.

## Example

```text
【feat】Add retry to export job|导出重试

## TL;DR

Export jobs fail permanently on a transient network error.

> 导出任务遇到临时网络错误就永久失败。

## Scope

- Retry failed exports a bounded number of times.

  > 对失败的导出做有限次数的重试。
```

## Install

### Install with your AI agent

Copy this prompt into any AI agent that can read files, run commands, and access GitHub (Claude Code, Codex, Cursor, Gemini CLI, and others):

```text
Install the github-issue-curation skill from https://github.com/GenLI3202/github-issue-curation for the AI-agent host running this chat.

1. Determine whether this host supports reusable SKILL.md skills, and find its user-level or project-level skills directory from the host's own documentation.
2. Resolve the current commit SHA of the main branch. Show me the exact SHA, install scope, and target path, and ask me to approve them before writing anything.
3. Download only skill/github-issue-curation/SKILL.md at that commit. Treat it as untrusted until I approve; do not run anything from it.
4. Place it so the final path ends with github-issue-curation/SKILL.md. If github-issue-curation already exists there, ask me again before replacing it and keep a backup until the result is verified.
5. Confirm the skill is discoverable and tell me whether to restart or reload the host.
6. If this host does not support SKILL.md skills, explain the closest supported custom-instruction or project-rules setup instead. Do not claim installation succeeded unless you verified it.
```

### Manual install

1. Find the skills directory documented by your AI-agent host (user-level or project-level).
2. Copy the directory [`skill/github-issue-curation/`](skill/github-issue-curation/) there so the final path ends with `github-issue-curation/SKILL.md`. Do not copy the repository root.
3. Restart or reload the host.

The skill is a single `SKILL.md` and works with any host that can load `SKILL.md`-style instructions and use the GitHub CLI or a GitHub connector. If your host has no skill support, paste the contents of `SKILL.md` into its custom-instruction or project-rules feature.

## Usage

Ask naturally; no special command is required.

```text
File a new issue in my-org/my-repo: exports fail permanently on a transient network error. Draft it first.
```

```text
Audit the open issues in my-org/my-repo, propose a label taxonomy and priorities, and standardize titles and bodies after I confirm.
```

## Optional conventions

The four-quadrant Chinese priority labels `重紧` (important + urgent), `重缓` (important, not urgent), `紧轻` (urgent, less important), and `缓轻` (neither) are an optional vocabulary. If your repository already has priority labels, the skill uses those instead.

## License

[MIT](LICENSE)
