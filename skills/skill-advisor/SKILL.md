---
name: skill-advisor
description: Recommend which locally installed Skill Manager Presets and skills to deploy for a stated goal. Use when the user asks which skills, preset, or workflow package should be enabled for a project, or asks to inspect and organize their skill library.
---

# Skill Advisor

根据用户描述的目标，先读取本机技能库和仓库清单，再给出最小够用的部署建议。这个技能只负责分析和推荐；没有明确确认时，不部署、不删除、不修改 GitHub。

## 数据源

按以下优先级读取：

1. `C:/Users/shr/.agents/skills`：当前全局可见的技能目录。
2. `C:/Users/shr/.skills-manager/skills-manager-cli.exe` 和 `C:/Users/shr/.skills-manager/skills`：Skill Manager 的安装状态、Preset 和来源。Windows 下实际 CLI 位于 `D:/APPS/Skills Manager/skills-manager-cli.exe`。
3. 本地 Git 仓库 `C:/Users/shr/Documents/Codex/2026-09-08/new-chat-3/my-agent-skills` 的 `catalog/presets.yml`、`skills/` 和 `packs/`。
4. 如果仓库不存在或用户要求最新清单，先在该仓库执行安全的 `git pull`；网络不可用时明确标注使用的是缓存清单。

不要把 GitHub 网页内容当作唯一事实；优先使用本地已检出的 `catalog/presets.yml`，并把实际 Manager 状态与仓库清单的差异列出来。

## 推荐流程

1. 把用户目标拆成领域、技术栈、交付阶段和风险约束。
2. 运行 `skills-manager-cli.exe --json repo status`、`presets list` 和 `skills list`，确认已安装技能与当前部署状态。
3. 读取 `catalog/presets.yml`，为每个候选 Preset 计算匹配理由。
4. 推荐一个“最小组合”：主 Preset、可选辅助 Preset，以及不建议启用的无关 Preset。
5. 解释每个推荐项会解决什么问题、预计会影响哪些 Agent/项目目录，并指出重复技能。
6. 给出可复制的预览命令，例如 `presets deploy <preset> --agent codex --dry-run`。只有用户明确说“部署/执行”后，才运行无 `--dry-run` 的部署命令。

## 输出格式

使用简洁的中文说明：

- 目标理解
- 推荐 Preset（主选、可选）
- 推荐理由与可能重复
- 不建议启用的 Preset
- 预览命令
- 需要用户确认的下一步

如果目标同时涉及多个领域，优先推荐一个工程流程 Preset，再叠加一个领域 Preset，而不是部署所有技能。若某个技能只存在于 GitHub 清单但本地未安装，标记为“需先安装”；不要假装它已经可用。

## 安全边界

- 不自动执行 `deploy`、`undeploy`、`skills remove`、Git push 或删除文件。
- 不修改 `skills-manager.db`；Preset 和技能变更必须使用 CLI 或图形界面。
- 发现中央库路径、Codex 目标路径或项目路径不一致时，先提醒用户确认，不要自行创建覆盖性链接。
- 所有会写入 Zotero、GitHub、数据库或线上服务的动作，先给出预览并等待明确确认。
