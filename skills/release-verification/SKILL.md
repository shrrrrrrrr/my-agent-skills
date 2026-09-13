---
name: release-verification
description: Use when implementation is claimed complete, before release, merge, deployment, or handoff, especially after code or configuration changes.
---

# 发布前验证

完成声明必须对应新鲜、可复现的证据。

1. 检查变更范围和未提交文件。
2. 运行与改动直接相关的测试，再运行项目要求的完整检查。
3. 验证构建、类型检查、格式检查和关键用户路径。
4. 检查配置、迁移、密钥引用、兼容性和回滚方式。
5. 报告实际运行的命令、结果、未验证项和剩余风险。

检查失败时不得称为完成；说明失败原因和下一步。

