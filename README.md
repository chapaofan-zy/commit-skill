# Git Commit Skill

一个 Agent Skill，自动分析代码变更并生成规范的 Git 提交信息。

## 功能特性

- 自动分析 `git diff`，生成符合 [Conventional Commits](https://www.conventionalcommits.org/) 规范的提交信息
- 支持简洁模式和详细模式两种提交格式
- 智能推断 type 和 scope
- 中文 subject 描述
- 支持推送（push）和分支合并（merge）
- 多模块变更时主动建议拆分提交

## 安装

```bash
# 安装所有 skills
npx skills add https://github.com/chapaofan-zy/commit-skill

# 安装指定 skill
npx skills add https://github.com/chapaofan-zy/commit-skill --skill git-commit

# 全局安装
npx skills add https://github.com/chapaofan-zy/commit-skill -g
```

## 使用方式

安装后，对 Agent 说以下类似的话即可自动激活：

- "提交代码" / "commit 一下" / "帮我提交"
- "生成 commit message"
- "push 到远程" / "推送代码"
- "合入 main" / "merge 到 develop"

## 提交模式

| 模式           | 格式                                          | 触发方式         |
| -------------- | --------------------------------------------- | ---------------- |
| 简洁模式（默认） | `<type>(<scope>): <subject>`                  | 默认使用         |
| 详细模式       | `<type>(<scope>): <subject>` + body           | 说"详细提交"等   |

### 示例

简洁模式：

```
feat(auth): 添加用户登录功能
fix(cart): 修复购物车数量计算错误
docs: 更新 README 安装说明
```

详细模式：

```
feat(auth): 添加用户登录功能

- 实现基于 JWT 的用户认证
- 添加登录接口和中间件
- 新增用户模型定义
```

## 执行流程

1. 检查工作区状态（`git status`）
2. 分析变更内容，必要时询问是否暂存文件
3. 根据 diff 生成提交信息
4. 展示给用户确认后执行 `git commit`
5. 如用户要求，执行 `git pull --rebase` + `git push`
6. 如用户要求，合并到目标分支并推送

> 遇到 rebase 或 merge 冲突时会立即停止，展示冲突文件，等待用户手动解决。

## License

MIT
