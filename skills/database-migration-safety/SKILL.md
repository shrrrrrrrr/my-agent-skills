---
name: database-migration-safety
description: Use when planning, writing, reviewing, or deploying database schema or data migrations where compatibility, locking, rollback, or data loss matters.
---

# 数据库迁移安全

先确认数据库、版本、数据规模、流量模式、备份和允许停机时间。

优先采用扩展—迁移—收缩：先增加兼容结构，再回填并切换读写，最后删除旧结构。评估表锁、长事务、索引构建、默认值、空值、外键和应用版本兼容性。

执行前提供预检查、备份或恢复点、分批策略、监控指标、停止条件和回滚方案。生产环境写入必须获得明确授权；不得把不可逆迁移包装成普通更新。

