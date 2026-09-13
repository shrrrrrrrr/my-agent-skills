# My Agent Skills

这是我的个人 Agent 技能仓库。它用 GitHub 保存经过筛选的自定义技能和 Skill Manager Preset 清单，适用于 Codex、Cursor、TRAE、WorkBuddy 等支持 Agent Skills 的工具。

## 先理解三个概念

- **Skill**：教 Agent 如何完成某一类工作的说明书，例如“系统化排查 Bug”。
- **Preset**：一组适合特定工作的 Skills，例如“React 前端开发”。
- **部署**：把某个 Preset 中的 Skills 复制到当前项目。只创建 Preset 不会让技能出现在 Codex 的 `/` 菜单中。

GitHub 是长期保存和版本管理的来源；Skill Manager 的本地库是实际部署时使用的副本。第三方技能只记录上游来源，不重复收录源码。

## 包含的 Preset

| Preset | 适用场景 | 优点 |
|---|---|---|
| 中文文学写作 | 小说、散文、人物、情节、中文表达与长文研究 | 强调中文语感、结构和原创表达，不只做表面润色 |
| 学术写作与合规改写 | 中文论文、论文审阅、引文检查、语言修订 | 保留原意与引用关系，不以规避查重或伪造文献为目标 |
| 文献研究与 Zotero | 查找论文、核验来源、整理 DOI、确认后导入 Zotero | 将“检索—筛选—入库—阅读笔记”连成一条流程 |
| 软件工程标准流程 | 从需求、方案、任务拆分到测试、调试、审查和发布 | 给各种软件项目提供一致的交付底座 |
| 前端与动效 | UI 设计、Apple 风格、动效、原型和动画评审 | 已有的高质量视觉与动效技能组合 |
| React 前端开发 | React/Next.js、组件架构、性能、可访问性、页面过渡 | 以 Vercel 工程实践为主，适合 React 项目按需部署 |
| 后端与 API 安全 | API 设计、认证、输入验证、限流和上线前安全检查 | 覆盖 FastAPI、Express 和 Serverless 常见风险 |
| PostgreSQL 数据库 | 表结构、索引、SQL、查询优化和迁移 | 针对 PostgreSQL/Supabase 项目，规则集中且体积小 |
| Prisma ORM | Prisma 初始化、Client API、CLI 和 Prisma Postgres | 只在使用 Prisma 的项目部署，避免污染其他数据库项目 |
| 笔记与知识整理 | 零散资料、项目知识、会议笔记、复盘和 Markdown 知识库 | 输出可检索、可链接、可继续维护的笔记，而非简单摘要 |
| 学习助教 | 学习计划、循序讲解、主动回忆、练习和阶段检查 | 根据掌握程度调整教学，不直接替代学习者思考 |
| 飞书 | 文档、表格、日历、会议、任务、消息等飞书 CLI 工作流 | 26 个飞书能力集中管理，不常驻全局菜单 |

每个 Preset 的精确成员和来源见 [catalog/presets.yml](catalog/presets.yml)，来源与许可证说明见 [catalog/sources.md](catalog/sources.md)。

## 小白使用教程

### 在一个项目中使用某个包

1. 打开 **Skills Manager**。
2. 点击左侧的 **Presets**。
3. 选择需要的包，例如“软件工程标准流程”。
4. 点击 **Deploy/部署**。
5. 选择目标 Agent 和项目目录。
6. 重新打开该项目的 Agent 会话，然后直接描述任务。

例如部署“React 前端开发”后，可以直接说：

> 检查这个 React 页面有没有不必要的重复渲染，并改善可访问性。

大多数技能会根据任务自动触发。标记为“仅手动”的技能，需要输入 `$技能名` 或在 `/` 菜单中选择。

### 每次使用都需要重新下载吗

不需要。Skill Manager 会在本机中央技能库保存一份副本。部署时，它再把需要的技能放进指定 Agent 或项目：

- GitHub：负责备份、版本和跨电脑同步；
- Skill Manager：负责本机安装、Preset 和部署；
- 项目技能目录：只保存当前项目实际使用的副本。

换电脑时，先克隆这个仓库，再按 `catalog/presets.yml` 恢复 Skill Manager。

### 怎么调用一个包

Preset 不是聊天命令。先在 Skill Manager 中部署，然后正常说需求：

- 中文文学写作：`帮我把这个人物小传发展成一个三幕式短篇。`
- 学术写作：`检查这一节的论证是否完整，并在不改变含义的前提下改写。`
- Zotero：`查找近五年相关论文，先列出候选清单，不要写入 Zotero。`
- 软件工程：`把这个需求整理成可验收的开发方案并实施。`
- 笔记整理：`把这些零散记录整理成可检索的主题笔记。`
- 学习助教：`用提问的方式检查我是否真正理解了数据库索引。`

## 删除方法

### 删除整个包

1. 在 Skill Manager 打开该 Preset。
2. 如果已经部署，先点击 **Undeploy/取消部署**。
3. 删除该 Preset。此操作只删除分组，不一定删除中央技能副本。
4. 如果某些技能不再属于任何 Preset，再到 **Skills** 页面删除它们。
5. 从 `catalog/presets.yml` 删除对应 Preset，提交并推送 Git。

### 删除包中的某一个 Skill

1. 在 Preset 详情中移除该 Skill。
2. 如果它仍属于其他 Preset，保留中央副本。
3. 如果没有任何 Preset 使用它，再从 Skill Manager 的 Skills 页面删除。
4. 同步修改 `catalog/presets.yml` 并提交 Git。

### 删除自定义 Skill

除完成上述步骤外，还要删除本仓库 `skills/技能名` 目录。第三方技能源码不在本仓库，只需删除清单中的来源项。

## 安全约定

- 所有会写入 Zotero、GitHub、数据库或线上服务的操作，先展示预览，再取得明确确认。
- API Key、Token、Cookie、数据库密码不提交到仓库。
- 不整库安装来源不明的技能；新增技能前检查 `SKILL.md`、脚本、依赖和许可证。
- Preset 默认不部署，避免 Codex `/` 菜单出现大量不相关技能。
