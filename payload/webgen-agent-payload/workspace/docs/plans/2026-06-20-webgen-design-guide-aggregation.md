# Webgen Design Guide Aggregation Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** 将 `docs/webgen-design-guide.md` 从单篇大文档重构为“执行优先”的索引入口 + 子文档体系，提升可读性、可维护性与后续扩展稳定性。

**Architecture:** 保留旧入口文件以兼容历史引用，把正文按职责拆到 `docs/webgen-design/` 目录下。新体系由 `index.md` 负责“按任务找文档”，其余子文档各自只承载单一职责，避免规则、流程、skill、模板、检查清单继续混排。

**Tech Stack:** Markdown, ripgrep, sed, apply_patch

---

### Task 1: 建立新文档目录与入口骨架

**Files:**
- Create: `docs/webgen-design/index.md`
- Create: `docs/webgen-design/core-rules.md`
- Create: `docs/webgen-design/design-principles.md`
- Create: `docs/webgen-design/workflow.md`
- Create: `docs/webgen-design/skills-map.md`
- Create: `docs/webgen-design/motion-selection.md`
- Create: `docs/webgen-design/responsive-delivery.md`
- Create: `docs/webgen-design/anti-patterns.md`
- Create: `docs/webgen-design/checklist.md`
- Create: `docs/webgen-design/page-type-entry.md`

**Step 1: 创建目录和空文件骨架**

使用统一头部模板：

```md
# 标题

> 适用场景：
> 何时阅读：
> 上游文档：
> 下游文档：

## 本页只回答什么
## 核心规则
## 例外情况
## 关联跳转
```

**Step 2: 运行文件存在性检查**

Run: `rg --files docs/webgen-design`
Expected: 返回上述 9 个子文档和 `index.md`

**Step 3: 提交**

```bash
git add docs/webgen-design
git commit -m "docs: add webgen design guide split skeleton"
```

### Task 2: 重写主索引为执行优先入口

**Files:**
- Modify: `docs/webgen-design/index.md`

**Step 1: 写索引结构**

索引必须只保留：
- 文档定位
- 阅读顺序
- 按任务入口
- 配套文档入口
- 维护规则

**Step 2: 写按任务入口区**

至少覆盖：
- 我现在要开始做页面
- 我在定风格和版式
- 我在选 skill
- 我在做动画
- 我在处理响应式与交付
- 我需要页面方案模板

**Step 3: 校验索引没有大段重复正文**

Run: `sed -n '1,220p' docs/webgen-design/index.md`
Expected: 仅见入口和跳转，不见长段规则复制

**Step 4: 提交**

```bash
git add docs/webgen-design/index.md
git commit -m "docs: add execution-first design index"
```

### Task 3: 迁移核心约束与设计原则

**Files:**
- Modify: `docs/webgen-design/core-rules.md`
- Modify: `docs/webgen-design/design-principles.md`

**Step 1: 迁移核心约束**

把旧文档以下内容迁入 `core-rules.md`：
- `0. 使用方式` 的必要摘要
- `2. 最高优先级约束`

要求：
- 保留规则优先级
- 保留“先方案后编码、先可运行再精修、默认资源/图标/配图策略”
- 删除与流程、skill、清单重复的展开

**Step 2: 迁移设计原则**

把旧文档以下内容迁入 `design-principles.md`：
- `3. 设计总原则`
- `4. 基于 design-taste-frontend 与 impeccable 的增强规则`

要求：
- 明确保留三拨盘
- 保留反 AI 模板味规则
- 保留版式、排版、色彩、材质、状态、动效的设计原则

**Step 3: 校验重复标题是否已收敛**

Run: `rg -n "反 AI 模板味|默认图标规则|默认资源策略|状态设计规则" docs/webgen-design`
Expected: 每个主题只在一个主文件出现正文定义，其他地方只链接

**Step 4: 提交**

```bash
git add docs/webgen-design/core-rules.md docs/webgen-design/design-principles.md
git commit -m "docs: split core rules and design principles"
```

### Task 4: 迁移流程、skill 地图与动效选型

**Files:**
- Modify: `docs/webgen-design/workflow.md`
- Modify: `docs/webgen-design/skills-map.md`
- Modify: `docs/webgen-design/motion-selection.md`

**Step 1: 迁移标准流程**

把旧文档 `5. 页面设计标准流程` 迁入 `workflow.md`，并压缩为：
- 阶段目标
- 输入输出
- 前置依赖
- 完成判断

**Step 2: 迁移 skill 职责与串联**

把旧文档 `6. 已安装 skill 的职责分工` 和 `7. 常见任务下的 skill 串联方式` 迁入 `skills-map.md`。

要求：
- 先写“按能力找 skill”
- 再写“按场景串联”
- 去掉对同一规则的重复展开

**Step 3: 迁移动效选型**

把旧文档 `8. 动效与特效技术选型规则` 迁入 `motion-selection.md`。

要求：
- 强化“场景 -> 库”的决策表
- 单独列出移动端降级与禁止混用规则

**Step 4: 校验流程与 skill 已解耦**

Run: `rg -n "阶段 A|场景一|GSAP|Motion|Anime.js|Three.js" docs/webgen-design`
Expected: 流程类内容集中在 `workflow.md`，能力和选型集中在 `skills-map.md` 与 `motion-selection.md`

**Step 5: 提交**

```bash
git add docs/webgen-design/workflow.md docs/webgen-design/skills-map.md docs/webgen-design/motion-selection.md
git commit -m "docs: split workflow skill map and motion rules"
```

### Task 5: 迁移交付规则、反模式与清单

**Files:**
- Modify: `docs/webgen-design/responsive-delivery.md`
- Modify: `docs/webgen-design/anti-patterns.md`
- Modify: `docs/webgen-design/checklist.md`
- Modify: `docs/webgen-design/page-type-entry.md`

**Step 1: 迁移响应式与交付要求**

把旧文档 `11. 响应式与设备适配规则` 的主体迁入 `responsive-delivery.md`。

要求：
- 断点策略
- 触控热区
- Pad 横竖屏
- H5 首屏优先级
- Hover 替代
- 图片校验与交付要求

**Step 2: 迁移禁止项与降级**

把旧文档 `12. 禁止项与降级规则` 迁入 `anti-patterns.md`。

**Step 3: 迁移交付前清单**

把旧文档 `13. 页面交付前检查清单` 迁入 `checklist.md`。

要求：
- 按“基础运行 / 响应式 / 交互状态 / 动效 / 高审美复核”分组
- 把可执行检查与设计判断拆开写

**Step 4: 页面类型入口收口**

把旧文档 `9. 页面类型方案模板` 的入口迁入 `page-type-entry.md`，只保留：
- 适用页面类型
- 对应模板链接
- 使用顺序

**Step 5: 校验页面类型模板没有回流到总指南**

Run: `rg -n "Landing Page 方案模板|后管系统方案模板|表单页方案模板" docs/webgen-design docs/webgen-design-guide.md`
Expected: 正文入口只保留在 `page-type-entry.md` 和兼容入口链接中

**Step 6: 提交**

```bash
git add docs/webgen-design/responsive-delivery.md docs/webgen-design/anti-patterns.md docs/webgen-design/checklist.md docs/webgen-design/page-type-entry.md
git commit -m "docs: split delivery patterns checklist and page entry"
```

### Task 6: 瘦身兼容入口并修复引用

**Files:**
- Modify: `docs/webgen-design-guide.md`
- Modify: `docs/webgen-ops-index.md`
- Modify: `docs/session-routing-and-project-commands.md`
- Modify: `docs/webgen-skill-change-log.md`

**Step 1: 将旧入口改为兼容页**

`docs/webgen-design-guide.md` 只保留：
- 文档目的
- 优先级说明
- 默认阅读顺序
- 子文档索引
- 10 条内速查摘要

控制目标：
- 约 `80-120` 行
- 不再承载完整规则正文

**Step 2: 修复站内引用**

更新所有引用旧指南正文的文档，改为：
- 指向 `docs/webgen-design/index.md`
- 或指向具体子文档

**Step 3: 校验旧入口已瘦身**

Run: `wc -l docs/webgen-design-guide.md`
Expected: 行数明显低于当前 772 行

**Step 4: 校验没有失效引用**

Run: `rg -n "webgen-design-guide.md|webgen-design/index.md|webgen-design/" docs`
Expected: 旧入口仅作为兼容页存在，新入口和子文档已被引用

**Step 5: 提交**

```bash
git add docs/webgen-design-guide.md docs/webgen-ops-index.md docs/session-routing-and-project-commands.md docs/webgen-skill-change-log.md
git commit -m "docs: convert design guide into compatibility index"
```

### Task 7: 最终一致性检查

**Files:**
- Verify only

**Step 1: 检查新文档树**

Run: `rg --files docs/webgen-design`
Expected: 结构完整，无遗漏文件

**Step 2: 检查重复膨胀**

Run: `rg -n "默认资源策略|响应式与设备适配规则|页面交付前检查清单|常见任务下的 skill 串联方式" docs/webgen-design docs/webgen-design-guide.md`
Expected: 主体只在单一归属文件出现

**Step 3: 人工抽查阅读路径**

至少抽查这 3 条路径：
- 开始做页面：`index.md -> core-rules.md -> workflow.md`
- 做风格与版式：`index.md -> design-principles.md`
- 做交付验收：`index.md -> responsive-delivery.md -> checklist.md`

**Step 4: 提交**

```bash
git add docs/webgen-design docs/webgen-design-guide.md docs/webgen-ops-index.md docs/session-routing-and-project-commands.md docs/webgen-skill-change-log.md
git commit -m "docs: finish webgen design guide aggregation"
```
