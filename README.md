<!-- 本文件说明如何维护和同步跨 agent 的个人提示词。 -->

# agent-rules

这个仓库维护跨 agent 共用的个人规则提示词。

## 文件

- `base.md`：基础协作规则。
- `tone.md`：回复语气规则。
- `git.md`：Git 分支、MR 和 push 习惯。
- `php.md`：PHP 项目代码习惯。
- `go.md`：Go 项目代码习惯。
- `csgo.md`：CSGO 相关项目习惯。
- `sync.sh`：按固定顺序拼接源文件，并同步到常见 agent 的默认规则文件。

## 使用

```bash
./sync.sh --dry-run
./sync.sh
```

默认目标：

- `$HOME/.codex/AGENTS.md`
- `$HOME/.gemini/GEMINI.md`
- `$HOME/.claude/CLAUDE.md`
- `$HOME/.config/opencode/AGENTS.md`
- `$HOME/.trae-cn/user_rules/rule-global.md`

临时指定目标：

```bash
AGENT_RULE_TARGETS="$HOME/.codex/AGENTS.md:$HOME/.gemini/GEMINI.md" ./sync.sh
```
