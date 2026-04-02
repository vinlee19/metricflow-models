# MetricFlow AfterShip Core Models

**English** | [中文](./README.md)

## Version Specification

### Version Format

Follows Semantic Versioning: `v{MAJOR}.{MINOR}.{PATCH}`

| Position | Name | Description | Example |
|----------|------|-------------|---------|
| 1st | MAJOR | Breaking changes / major architecture changes | v1.0.0 → v2.0.0 |
| 2nd | MINOR | New models / new Views / feature iterations | v0.1.0 → v0.2.0 |
| 3rd | PATCH | Bug fixes / minor changes / config adjustments | v0.1.0 → v0.1.1 |

### Version Increment Rules

**MAJOR (1st digit) increment**
- Major model DSL syntax changes
- Full model changes due to underlying data source migration
- Removal of a large number of published models or Views

**MINOR (2nd digit) increment**
- New models (e.g., adding `protection.yml`)
- New Views (e.g., adding `revenue_center_view.yml`)
- New model category directories (e.g., adding `tracking_notification/`)
- New dimension, measure, or parameter fields in models
- Major SQL logic changes in existing models (backward compatible)

**PATCH (3rd digit) increment**
- Bug fixes (e.g., placeholder, parameter quoting issues)
- Model field spelling/formatting corrections
- Minor expression fixes (e.g., value_format adjustments)

### Branch Strategy & Tag Relationship

```
feature-xxx  →  development  →  staging  →  master  →  Tag (vX.Y.Z)
```

| Branch | Purpose | Tag? |
|--------|---------|------|
| `feature-*` | Feature development | No |
| `development` | Development integration | No |
| `staging` | Pre-release / testing | No |
| `master` | Production main branch | **Yes, official release tag** |

> ⚠️ Tags are only created from the master branch

### Branch Naming Convention

| Type | Format | Example |
|------|--------|---------|
| New model/feature | `feature-{name}` | `feature-apple-wallet` |
| Hotfix | `hotfix-{description}` | `hotfix-parameter-quote` |

### Commit Prefix Convention

| Prefix | Purpose | Version Impact |
|--------|---------|---------------|
| `feat:` | New model/View/feature | MINOR +1 |
| `fix:` | Bug fix | PATCH +1 |
| `refactor:` | Refactoring (no functional change) | PATCH +1 |
| `breaking:` | Breaking change | MAJOR +1 |
| `chore:` | Miscellaneous (CI, docs) | PATCH +1 |

### GitHub Release Templates

#### MINOR version (new models/Views)

```markdown
## What's New

### New Models
- `models/apple_wallet/apple_wallet.yml` - Apple Wallet model

### New Views
- `views/apple_wallet/apple_wallet_view.yml` - Apple Wallet view

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.1.0...v0.2.0
```

#### PATCH version (bug fixes)

```markdown
## Bug Fixes
- Fix parameter quoting issue
- Fix missing model field reference

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.2.0...v0.2.1
```

#### MAJOR version (breaking changes)

```markdown
## Breaking Changes
- Model DSL syntax upgrade, incompatible with older versions

## Migration Guide
- Re-deploy semantic-api parsing service required

## New Models
- ...

**Full Changelog**: https://github.com/AfterShip/library-metricflow-aftership-core-models/compare/v0.x.x...v1.0.0
```

#### Available Release Notes Sections

| Section | When to Use |
|---------|------------|
| `## Breaking Changes` | MAJOR version, incompatible changes |
| `## New Models` | New model files added |
| `## New Views` | New view files added |
| `## Changes` | Model field additions/modifications |
| `## Bug Fixes` | Bug fixes |
| `## Migration Guide` | MAJOR version, migration instructions |
