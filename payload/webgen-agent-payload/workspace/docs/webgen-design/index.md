# webgen 页面设计文档索引

> 适用场景：需要快速找到页面设计规则、流程、skill 选型与交付检查
> 何时阅读：进入页面方案、实现或验收前
> 上游文档：`AGENTS.md`、`docs/webgen-design-cheatsheet.md`
> 下游文档：本目录下各主题文档

## 本页只回答什么

这是一份执行优先入口，不重复铺正文，只回答两件事：

- 当前任务先看哪份文档
- 规则正文在哪一份子文档里

## 默认阅读顺序

1. `AGENTS.md`
2. `docs/webgen-design-cheatsheet.md`
3. `docs/webgen-design/index.md`
4. 按任务跳到对应子文档

## 按任务找文档

### 我现在要开始做页面

先看：

1. [核心硬规则](./core-rules.md)
2. [标准流程](./workflow.md)

适合解决：

- 方案里最少要写什么
- 什么时候能开工，什么时候必须阻塞
- 默认资源、图标、配图策略是什么

### 我在定风格和版式

先看：

1. [设计总原则](./design-principles.md)
2. [禁止项与降级规则](./anti-patterns.md)

适合解决：

- 如何避免 AI 模板味
- 三档位和气氛层怎么定
- 版式、排版、色彩、材质如何控制

### 我在选 skill

先看：

1. [Skill 职责地图](./skills-map.md)
2. [标准流程](./workflow.md)

适合解决：

- 当前任务该先调哪个 skill
- 哪些场景需要 `design-taste-frontend`、`frontend-design`、`impeccable`、`gsap-*`

### 我在做动效或特效

先看：

1. [动效与特效选型](./motion-selection.md)
2. [设计总原则](./design-principles.md)

适合解决：

- 该用 `Anime.js`、`Motion`、`GSAP` 还是 `Three.js`
- 什么时候该降级，什么时候不要混库

### 我在做响应式、素材和交付

先看：

1. [响应式与交付规则](./responsive-delivery.md)
2. [交付前检查清单](./checklist.md)

适合解决：

- PC / Pad / H5 断点和触控热区怎么定
- 图片如何校验和记录
- 交付前必须复核哪些项目

### 我需要页面方案模板

先看：

1. [页面类型入口](./page-type-entry.md)

适合解决：

- Landing、后管、表单类页面应该从哪个模板开始

## 子文档目录

- [核心硬规则](./core-rules.md)
- [设计总原则](./design-principles.md)
- [标准流程](./workflow.md)
- [Skill 职责地图](./skills-map.md)
- [动效与特效选型](./motion-selection.md)
- [响应式与交付规则](./responsive-delivery.md)
- [禁止项与降级规则](./anti-patterns.md)
- [交付前检查清单](./checklist.md)
- [页面类型入口](./page-type-entry.md)

## 配套文档

- 快速决策：`docs/webgen-design-cheatsheet.md`
- 方案模板汇总：`docs/webgen-page-type-proposal-templates.md`
- 兼容入口：`docs/webgen-design-guide.md`

## 维护规则

- 同一规则只保留一个主归属文件
- 本页只保留入口与跳转，不回填大段正文
- 新增设计规则时，优先更新子文档，再看是否需要补索引
