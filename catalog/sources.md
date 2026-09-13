# Skill sources

第三方技能不复制进本仓库。Skill Manager 从以下上游安装，本仓库只保存自定义技能和 Preset 成员清单。

| Skills | Upstream | License / notes |
|---|---|---|
| animate 等动效技能 | emilkowalski/skills | 上游使用；现有本地包迁移到 Manager |
| frontend-design | 现有本地技能 | 后续核对来源后再绑定更新地址 |
| lark-* | larksuite/cli，skills/名称 | 飞书 CLI 官方仓库 |
| 中文写作参考 | openakita/openakita | 仓库为 AGPL-3.0 且部分 name 不符合通用规范；不直接导入 |
| 学术写作四项 | bahayonghang/academic-writing-skills | 根目录未发现许可证；只引用上游，不再分发 |
| 学术核查、API 安全与项目技能 | jamditis/claude-skills-journalism | MIT；选取可跨 Agent 使用的具体技能 |
| tdd、diagnosing-bugs、resolving-merge-conflicts、teach | mattpocock/skills | MIT；排除依赖完整 setup 的技能 |
| React/Vercel 技能 | vercel-labs/agent-skills | 技能元数据声明 MIT；按具体目录引用 |
| postgres-best-practices | neondatabase/postgres-skills | Apache-2.0 |
| prisma-* | prisma/skills | MIT；Prisma 官方技能 |
| zotero | alex-roc/zotero-agent，skill | AGPL-3.0；需要另外安装 zot CLI |
| 本仓库 skills/* | shrrrrrrrr/my-agent-skills | 用户自定义技能 |

锁定版本时应记录具体 Git commit；升级前重新检查 SKILL.md、脚本、依赖和许可证。
