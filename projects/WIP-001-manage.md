- 开始日期：2022/02/04 11:11:31
- 参考问题。(填写现有的相关问题，如果有的话)
- 实施PR。(留空)

# 摘要

项目管理最佳实践。

想法管理的最佳实践。

# 基本例子

这里只会保存个人项目的 `rfcs`，`org-rfcs` 应该有自己的仓库。

该项目文件结构。

```
[project]
  rfcs
```

`rfcs` 和 `ideas` 区别。 `rfc` 是 `feature-of-request` 对于已经 **存在的项目**。`ideas` 是新项目的想法。**一个 feature 的想法应该是 rfc**

`ideas` 使用 `issues` 进行管理，原因是似乎大多数开源作者都会这么做。暂时不需要新开一个 `ideas` 仓库，在 `rfc-repo` 管理就好了。

# 动机

**管理工具的迁移**

之前所有的项目管理都是在 Notion 中进行的，问题在于 Notion 并不是专业的，即使支持各种项目模板。

- Issue Track 显然需要更加专业的功能，比如关联 issue, pr 以及 milestone。这些可以是自动化的。- 所以尝试使用 `linear` 进行管理。
- 对于代码的 `RFC` 来说，原生的 `MD` 灵活性更高一些（通过键盘就行）

**为什么使用 rfcs**

最开始在开发之前，并没有进行 `rfc`。但是这样不利于，在项目开发一段时间之后，功能为什么这么设计的目的。

另外，开放之前梳理思路，调研，`rfc` 可以给我理由说服自己去这么实现，以及不需要这个功能的理由。

# 详细设计

思路为交给专业的工具来做

- issue-track: linear
- draft ideas: issues > notion

# 缺点

由于是从 Notion 迁移过来的，所以 Notion 之前可以实现一些 `Tag` 筛选功能，这部分在新的模式下就没有了。

# 替代方案

- issue-track 有原生的 github 支持，目前可以在 linear 上试用一下