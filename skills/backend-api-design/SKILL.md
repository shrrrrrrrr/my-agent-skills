---
name: backend-api-design
description: Use when designing, implementing, or reviewing HTTP APIs, service boundaries, request validation, error contracts, authentication, pagination, or idempotency.
---

# 后端 API 设计

从调用者任务和失败场景出发设计接口。保持资源命名、状态码、错误结构、分页和版本策略一致。

对所有外部输入做边界验证；明确身份认证与权限授权的区别；敏感写操作考虑幂等、审计、速率限制和重放风险。数据库事务边界应与业务原子性一致。

交付时给出接口契约、示例请求与响应、错误情况、权限矩阵、兼容性策略和测试要点。具体安全结论以当前官方文档为准。

