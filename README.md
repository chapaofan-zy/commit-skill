# Git Commit Skills

一组用于定制化 Git 提交流程的 Agent Skills，帮助自动分析代码变更并生成规范的提交信息。

## 安装

```bash
# 安装所有 skills
npx skills add <your-username>/git-commit-skills

# 安装指定 skill
npx skills add <your-username>/git-commit-skills --skill git-commit

# 全局安装
npx skills add <your-username>/git-commit-skills -g
```

## 包含的 Skills

| Skill | 说明 |
|-------|------|
| `git-commit` | 分析代码变更，按 Conventional Commits 规范生成提交信息并执行提交 |

## 使用方式

安装后，当你对 Agent 说以下类似的话时，skill 会自动激活：

- "提交代码"
- "commit 一下"
- "帮我提交这些改动"
- "生成 commit message"

Agent 会自动：

1. 分析当前 `git diff` 变更内容
2. 生成符合 Conventional Commits 规范的提交信息
3. 展示给你确认后执行提交

## License

MIT
