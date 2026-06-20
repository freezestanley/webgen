# webgen 页面设计指南

> 兼容入口页。完整正文已拆到 `docs/webgen-design/` 目录下，本文件只保留阅读顺序、索引和速查摘要。

## 使用方式

- 需要快速判断任务方向时，先看：`docs/webgen-design-cheatsheet.md`
- 需要完整规则、流程、skill 选型和交付要求时，再看：`docs/webgen-design/index.md`
- 默认顺序：`AGENTS.md` → `docs/webgen-design-cheatsheet.md` → `docs/webgen-design/index.md`

## 规则优先级

当多份规则出现交叉或冲突时，按以下优先级执行：

1. `AGENTS.md` 硬约束
2. 当前项目自己的约束、品牌规范、组件规范、接口约束
3. `docs/webgen-design/` 目录文档
4. 已安装 skill 的建议与偏好

## 任务入口

- 开始做页面：`docs/webgen-design/core-rules.md` + `docs/webgen-design/workflow.md`
- 定风格和版式：`docs/webgen-design/design-principles.md`
- 选 skill：`docs/webgen-design/skills-map.md`
- 做动效和特效：`docs/webgen-design/motion-selection.md`
- 处理响应式、素材和交付：`docs/webgen-design/responsive-delivery.md`
- 做最终验收：`docs/webgen-design/checklist.md`
- 找页面方案模板：`docs/webgen-design/page-type-entry.md`

## 速查摘要

1. 先方案，后编码；方案未确认不进入页面业务代码实现。
2. 先可运行，再精修；结构、状态、动效、响应式、性能按顺序推进。
3. 默认优先原生 HTML / CSS / JS；已有项目优先延续现有栈。
4. 默认图标库只用 `Lucide`，默认浏览器资源走既定 CDN。
5. 需要真实配图时，先用户素材，再真实图站，最后才退化为 SVG 占位。
6. 高审美页面先产出 `Design Read`、三拨盘和 `Atmosphere Layer`。
7. 设计质量优先来自结构、节奏、排版和材质，不靠紫蓝发光、玻璃和三等分卡片。
8. 动效选型按场景定：普通 UI 用 `Anime.js`，React 组件用 `Motion`，滚动叙事用 `GSAP`，沉浸式 3D 用 `Three.js`。
9. 页面默认必须覆盖 PC / Pad / H5，并明确断点、触控热区、Pad 横竖屏和 hover 替代策略。
10. 交付前至少完成一次真实预览验证和一次页面实看设计复核。

## 配套文档

- 入口硬约束：`AGENTS.md`
- 快速决策入口：`docs/webgen-design-cheatsheet.md`
- 执行优先索引：`docs/webgen-design/index.md`
- 页面类型方案模板已拆分，详见：`docs/webgen-page-type-proposal-templates.md`

## 后续维护

后续若有以下内容变更，优先更新 `docs/webgen-design/` 对应子文档：

- 页面设计规范
- skill 分工调整
- 动效技术选型策略
- 图标 / 组件 / 设计系统约束
- 新增前端审美与实现规则
- 新的交付检查要求
