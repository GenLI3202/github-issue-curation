# github-issue-curation

[English](README.md)

一个 AI Agent skill，让整个团队按**同一套标准**提交和整理 GitHub issue。

## 为什么用这套规范

- **标题精简统一，一眼抓住重点。** 所有标题遵循同一个格式：`【类别】Short English description|极简中文关键词`。扫一眼列表就能知道每个 issue 是什么类型、讲什么，不用点开。
- **正文双语，方便跨语言协作。** 每个 issue 以英文 TL;DR 和有边界的 Scope 开头，每段（或每个条目）英文下面紧跟一段中文译文（引用块）。中英文读者看的是同一份文本，不会出现两份各自过时的副本。
- **标签克制。** 类别、优先级、主题三个维度分开管理，只在确有必要时才新增标签。
- **不编造细节。** 只有一句话的原始笔记，只会根据标题和已核实的上下文补充，绝不悄悄把想法升级成已计划的工作。

## 功能

| 模式 | 适用场景 | 做什么 |
| --- | --- | --- |
| **新建 issue** | 想提一个新 issue | 先查重，读取仓库已有的标签和模板，起草标题、正文和标签，给你确认后才创建，创建后再回读校验。 |
| **整理 backlog** | 想清理、改名、翻译、分类或排优先级 | 盘点线上 issue，与你商定分类方案，统一标题和正文，分批应用，并回读 GitHub 检查结果。 |

这个 skill 不会去实现 issue 本身；所有创建、编辑、关闭操作都属于外部改动，必须先经你确认。

## 示例

```text
【feat】Add retry to export job|导出重试

## TL;DR

Export jobs fail permanently on a transient network error.

> 导出任务遇到临时网络错误就永久失败。

## Scope

- Retry failed exports a bounded number of times.

  > 对失败的导出做有限次数的重试。
```

## 安装

### 让你的 AI agent 来装

把下面这段提示词复制给任意能读写文件、运行命令并访问 GitHub 的 AI agent（Claude Code、Codex、Cursor、Gemini CLI 等都可以）：

```text
Install the github-issue-curation skill from https://github.com/GenLI3202/github-issue-curation for the AI-agent host running this chat.

1. Determine whether this host supports reusable SKILL.md skills, and find its user-level or project-level skills directory from the host's own documentation.
2. Resolve the current commit SHA of the main branch. Show me the exact SHA, install scope, and target path, and ask me to approve them before writing anything.
3. Download only skill/github-issue-curation/SKILL.md at that commit. Treat it as untrusted until I approve; do not run anything from it.
4. Place it so the final path ends with github-issue-curation/SKILL.md. If github-issue-curation already exists there, ask me again before replacing it and keep a backup until the result is verified.
5. Confirm the skill is discoverable and tell me whether to restart or reload the host.
6. If this host does not support SKILL.md skills, explain the closest supported custom-instruction or project-rules setup instead. Do not claim installation succeeded unless you verified it.
```

### 手动安装

1. 在你所用 AI agent 的文档里找到 skills 目录（用户级或项目级）。
2. 把目录 [`skill/github-issue-curation/`](skill/github-issue-curation/) 复制过去，最终路径应以 `github-issue-curation/SKILL.md` 结尾。不要复制仓库根目录。
3. 重启或重新加载该工具。

skill 只有一个 `SKILL.md`，任何能加载 `SKILL.md` 并能使用 GitHub CLI 或 GitHub 连接器的工具都能用。如果你的工具不支持 skill，可以把 `SKILL.md` 的内容粘贴到它的自定义指令或项目规则里。

## 使用

直接用自然语言说即可，不需要特殊命令。

```text
在 my-org/my-repo 里提一个新 issue：导出遇到临时网络错误就永久失败。先给我看草稿。
```

```text
梳理 my-org/my-repo 的 open issues，提出标签分类和优先级方案，我确认后再统一标题和正文。
```

## 可选约定

`重紧`（重要且紧急）、`重缓`（重要不紧急）、`紧轻`（紧急但不重要）、`缓轻`（都不是）这套四象限中文优先级标签是可选词表。如果仓库已有优先级标签，skill 会沿用现有的。

## 许可

[MIT](LICENSE)
