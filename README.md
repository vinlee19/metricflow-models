# MetricFlow AfterShip Core Models

[English](./README_EN.md) | **中文**

## 版本规范

### 版本号格式

采用语义化版本（Semantic Versioning）：`v{MAJOR}.{MINOR}.{PATCH}`

| 位 | 名称 | 含义 | 示例 |
|---|------|------|------|
| 第一位 | MAJOR | 重大架构变更 / 不兼容变更 | v1.0.0 → v2.0.0 |
| 第二位 | MINOR | 新增模型 / 新增 View / 功能迭代 | v0.1.0 → v0.2.0 |
| 第三位 | PATCH | Bug 修复 / 小改动 / 配置调整 | v0.1.0 → v0.1.1 |

### 版本递增规则

**MAJOR（第一位）递增**
- 模型 DSL 语法重大调整
- 底层数据源迁移导致全量模型变更
- 删除大量已发布的模型或 View

**MINOR（第二位）递增**
- 新增模型（如新增 `protection.yml`）
- 新增 View（如新增 `revenue_center_view.yml`）
- 新增模型分类目录（如新增 `tracking_notification/`）
- 模型中新增 dimension、measure、parameter 等字段
- 现有模型的 SQL 逻辑重大调整（不破坏兼容性）

**PATCH（第三位）递增**
- Bug 修复（如 placeholder、parameter 引号问题）
- 模型字段拼写/格式修正
- 微小的表达式修正（如 value_format 调整）

### 分支策略与 Tag 关系

```
feature-xxx  →  development  →  staging  →  master  →  Tag (vX.Y.Z)
```

| 分支 | 用途 | 是否打 Tag |
|------|------|-----------|
| `feature-*` | 功能开发 | 否 |
| `development` | 开发集成 | 否 |
| `staging` | 预发布/测试 | 否 |
| `master` | 生产主分支 | **是，正式 release tag** |

> ⚠️ Tag 只从 master 分支打出

### 分支命名规范

| 类型 | 格式 | 示例 |
|------|------|------|
| 新模型/功能 | `feature-{name}` | `feature-apple-wallet` |
| hotfix | `hotfix-{description}` | `hotfix-parameter-quote` |

### Commit 前缀规范

| 前缀 | 用途 | 版本影响 |
|------|------|---------|
| `feat:` | 新增模型/View/功能 | MINOR +1 |
| `fix:` | Bug 修复 | PATCH +1 |
| `refactor:` | 重构（不影响功能） | PATCH +1 |
| `breaking:` | 不兼容变更 | MAJOR +1 |
| `chore:` | 杂项（CI、文档） | PATCH +1 |

### GitHub Release 模板

#### MINOR 版本（新增模型/View）

```markdown
## What's New

### New Models
- `models/apple_wallet/apple_wallet.yml` - Apple Wallet 模型

### New Views
- `views/apple_wallet/apple_wallet_view.yml` - Apple Wallet 视图

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.1.0...v0.2.0
```

#### PATCH 版本（Bug 修复）

```markdown
## Bug Fixes
- 修复 parameter 引号解析问题
- 修复模型字段引用缺失

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.2.0...v0.2.1
```

#### MAJOR 版本（重大变更）

```markdown
## Breaking Changes
- 模型 DSL 语法升级，旧版本不兼容

## Migration Guide
- 需要重新部署 semantic-api 解析服务

## New Models
- ...

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.x.x...v1.0.0
```

#### Release Notes 可用 Section

| Section | 何时使用 |
|---------|---------|
| `## Breaking Changes` | MAJOR 版本，不兼容变更 |
| `## New Models` | 新增模型文件 |
| `## New Views` | 新增视图文件 |
| `## Changes` | 模型字段新增/调整 |
| `## Bug Fixes` | 修复问题 |
| `## Migration Guide` | MAJOR 版本，迁移说明 |
