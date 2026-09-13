---
name: literature-to-zotero
description: Use when searching for scholarly literature, screening candidate papers, validating metadata, and preparing or performing a confirmed import into Zotero.
---

# 文献检索到 Zotero

默认只读。将“发现候选文献”和“写入 Zotero”分开。

1. 将研究问题转换为关键词、同义词、时间范围和纳入或排除标准。
2. 优先检索权威学术索引和论文原始页面，记录 DOI、标题、作者、年份、来源和链接。
3. 去重并核验 DOI 与书目信息；无法确认的条目标记为未验证。
4. 先提供候选清单、相关性理由和排除项，不立即写入。
5. 用户确认目标 Zotero Collection、标签和条目后，才调用 zot CLI、Zotero API，或生成 RIS/BibTeX 导入文件。
6. 写入后重新查询，报告成功、重复、失败和缺失附件。

不要虚构论文或引文。API Key 和 Zotero 凭证只从环境或安全凭据存储读取，不写入输出或仓库。删除、合并和批量改写条目需要单独确认。

