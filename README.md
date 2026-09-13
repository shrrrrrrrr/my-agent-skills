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

## Skill Manager 完整操作说明

以下命令在 PowerShell 中执行。先定义 CLI 路径：

```powershell
$sm = 'D:\APPS\Skills Manager\skills-manager-cli.exe'
```

### 查看状态

```powershell
& $sm --json repo status
& $sm --json agents list
& $sm --json skills list
& $sm --json presets list
```

它们依次显示中央库、Agent 目标目录、技能和 Preset。不要直接编辑 `skills-manager.db`。

### 新建和编辑 Preset

```powershell
& $sm --json presets create '我的新技能包' --description '这个包适合什么工作' --icon '🧩'
& $sm --json presets add-skill '我的新技能包' skill-one skill-two
& $sm --json presets remove-skill '我的新技能包' skill-one
```

Preset 只是分组，新建后不会部署。增删成员只改变关系，不删除中央库 Skill。完成后同步修改 `catalog/presets.yml`。

### 安装或纳管 Skill

```powershell
& $sm --json skills install 'owner/repository@skill-name' --git
& $sm --json skills adopt 'C:\完整路径\skill-folder'
& $sm skills install --help
& $sm skills set-source --help
```

仓库结构不同时，按帮助指定 URL、分支和子路径。安装前检查 `SKILL.md`、脚本、依赖和许可证。安装一次后保存在中央库，不需每次下载。GitHub Skill 应使用 `set-source` 绑定来源。

### 部署和取消部署

```powershell
& $sm --json presets deploy '我的新技能包' --agent codex --dry-run
& $sm --json presets deploy '我的新技能包' --agent codex
& $sm --json presets undeploy '我的新技能包' --agent codex
```

先 dry-run 再部署。部署是叠加式的；不要用旧的 `presets apply` 做日常部署，因为它是排他式切换。取消部署只清理 Manager 记录的部署副本，保留 Preset、中央库和 GitHub。手动复制或改名的文件不一定被清理。

### 删除 Preset

1. 对所有已部署 Agent 执行 `presets undeploy`。
2. 在 Skill Manager 界面删除 Preset。
3. 从 `catalog/presets.yml` 删除对应条目。
4. 检查其中 Skill 是否仍被其他 Preset 使用。
5. 提交并推送仓库。

删除 Preset 通常只删除分组，不等于删除其中的 Skill。

### 删除中央库 Skill

先从所有 Preset 移除并取消部署：

```powershell
& $sm --json skills remove skill-name
```

若 CLI 报告仍有引用，先处理引用；确认目标后才按帮助增加确认参数。第三方上游仓库不会被删除。若是自定义 Skill，还要删除 `skills/skill-name/`、更新清单并提交：

```powershell
git add .
git commit -m 'remove unused skill'
git push
```

### 修改自定义 Skill

在本地仓库修改 `skills/skill-name/`，检查名称、触发描述和引用文件，提交并推送 GitHub，再在 Skill Manager 同步/更新并重新部署。GitHub 应作为自定义 Skill 的源头，中央库不应是唯一编辑副本。

### 不部署时是否删除文件

不会。GitHub、中央库和 Preset 都保留，只是不新增到目标 Agent。以前部署过的内容必须执行 `undeploy` 才会移除由 Manager 管理的副本。

### GitHub 与本地的职责

- GitHub：源码、README、Preset 清单、版本和跨电脑备份。
- Skill Manager 中央库：本机已安装、可部署的 Skill。
- Skill Manager 数据库：实际 Preset 成员、来源和部署记录。
- Agent/项目技能目录：真正暴露给 Agent 的副本。

`catalog/presets.yml` 是可读备份，目前不会自动导入 Manager 数据库。

## 常驻 Skill Advisor

`skill-advisor` 常驻全局目录。只需描述目标，例如：

> 我要做一个 React + PostgreSQL 的后台管理系统，应该部署哪些 Preset？

它会比较 Manager 状态和 `catalog/presets.yml`，给出主 Preset、可选 Preset、重复项和部署预览命令。默认只推荐，不会未经确认部署、删除或推送。

源文件在 `skills/skill-advisor/`，全局入口在 `C:\Users\shr\.agents\skills\skill-advisor`。全局入口是指向仓库源目录的 Junction，因此本地仓库一更新就立即生效；GitHub 上的新提交仍需先 `git pull` 到本机。

## 全局常驻技能

全局技能直接从 `C:\Users\shr\.agents\skills` 被 Codex 发现，不需要经过 Skill Manager 部署，也不应在 `C:\Users\shr\.skills-manager\skills` 再保存一份。

由本仓库直接管理的常驻技能：

- `find-skills`：发现可安装的技能；上游为 `vercel-labs/skills`。
- `grilling`：通过连续追问压力测试方案；上游为 `mattpocock/skills`。
- `humanizer-zh`：中文文本去 AI 痕迹与自然化编辑。
- `skill-advisor`：根据目标推荐最小够用的 Preset。

这四个目录在 `.agents\skills` 中都是 Junction，实际指向本仓库的 `skills/`。修改本地仓库会立即反映到全局目录；其他电脑在 GitHub 更新后，需要先执行 `git pull`。

同目录下由 Codex/开发工作流提供的其他全局技能不复制进仓库，避免产生需要手工追踪的第二份平台源码；它们的名称登记在 [catalog/global-skills.yml](catalog/global-skills.yml)，可在 GitHub 中查看和盘点。

全局技能不要加入 Preset。Preset 若依赖某个全局技能，应在 `catalog/presets.yml` 使用 `global_dependencies` 标记，而不是再安装到 Skill Manager 中央库。