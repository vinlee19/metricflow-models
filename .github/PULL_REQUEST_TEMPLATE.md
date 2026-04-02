## 变更说明 / What Changed

<!-- 简要描述本次改动，例如：新增 apple_wallet 模型和视图 -->



## 变更类型 / Change Type

- [ ] 新增模型 (New Model)
- [ ] 新增视图 (New View)
- [ ] 模型字段调整 (Field Change)
- [ ] SQL 逻辑调整 (SQL Logic Change)
- [ ] Bug 修复 (Bug Fix)
- [ ] 其他 (Other)

> Label（`model`、`view`、`major-change`、`minor-change`、`patch-change`）由流水线自动打标，无需手动添加。

## 涉及文件 / Affected Files

<!-- 列出本次变更涉及的模型或视图文件路径 -->

- `models/xxx/xxx.yml`
- `views/xxx/xxx_view.yml`

## 变更详情 / Change Details

<!-- 根据变更类型，补充以下对应信息（可选） -->

**新增模型/视图：**
<!-- 模型/视图名称、所属业务模块、用途说明 -->

**字段调整：**
<!-- 新增/修改/删除了哪些 dimension、measure、parameter -->

**SQL 逻辑调整：**
<!-- 调整了哪个模型的 SQL、调整原因 -->

**Bug 修复：**
<!-- 问题描述、修复方式 -->

## 备注 / Notes

<!-- 其他需要说明的信息 -->



---

## 📖 发版规范 / Release Guide

### PR Label

以下 label 由流水线自动打标：

`model` · `view` · `major-change` · `minor-change` · `patch-change`

### Commit 前缀

| 前缀 | 用途 | 版本影响 |
|------|------|---------|
| `feat:` | 新增模型/View/功能 | MINOR +1 |
| `fix:` | Bug 修复 | PATCH +1 |
| `refactor:` | 重构（不影响功能） | PATCH +1 |
| `breaking:` | 不兼容变更 | MAJOR +1 |
| `chore:` | 杂项（CI、文档） | PATCH +1 |

### 分支流程

```
feature-xxx → development → staging → master → Tag (vX.Y.Z)
```

### 版本号规则

| 位 | 名称 | 含义 | 示例 |
|---|------|------|------|
| 第一位 | MAJOR | 重大架构变更 / 不兼容变更 | v1.0.0 → v2.0.0 |
| 第二位 | MINOR | 新增模型 / 新增 View / 功能迭代 | v0.1.0 → v0.2.0 |
| 第三位 | PATCH | Bug 修复 / 小改动 / 配置调整 | v0.1.0 → v0.1.1 |

> 详细规范请查看 [README](../blob/master/README.md)
