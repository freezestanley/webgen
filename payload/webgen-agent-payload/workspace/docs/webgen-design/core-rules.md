# webgen 页面设计核心硬规则

> 适用场景：进入页面方案、实现与交付前的规则确认
> 何时阅读：准备出方案、准备开工、准备引入资源时
> 上游文档：`AGENTS.md`、[`index.md`](./index.md)
> 下游文档：[`workflow.md`](./workflow.md)、[`responsive-delivery.md`](./responsive-delivery.md)

## 本页只回答什么

- 页面工作在 `webgen` 里有哪些默认硬规则
- 哪些事情必须先做，哪些默认不能跳过

## 规则优先级

当多份规则出现交叉或冲突时，按以下顺序执行：

1. `AGENTS.md` 硬约束
2. 当前项目自己的约束、品牌规范、组件规范、接口约束
3. 本目录文档
4. 已安装 skill 的建议与偏好

执行原则：

- 本目录只定义 `webgen` 的默认增量规则，不覆盖 `AGENTS.md`
- 项目已存在品牌或设计系统时，优先延续现有体系
- skill 的建议不能绕过 `AGENTS.md` 和项目约束

## 核心规则

### 1. 先方案，后编码

- 必须先给出页面方案，再进入实现
- 方案至少说明：
  - 页面目标
  - 主要板块
  - 风格方向
  - 配色与字体方向
  - 素材与接口策略
  - PC / Pad / H5 适配策略
- 用户未明确确认前，不进入页面业务代码实现

方案默认输出模板：

1. 页面类型 / 目标
2. 目标用户 / 使用场景
3. 主要板块与信息层级
4. 风格方向与设计拨盘：`DESIGN_VARIANCE / MOTION_INTENSITY / VISUAL_DENSITY`
5. 配色 / 字体 / 图标方向
6. 素材 / 文案 / 接口来源与缺口
7. 技术实现与依赖策略
8. 状态设计：`Loading / Empty / Error / Active Feedback`
9. 响应式策略：断点、Pad 横竖屏、H5 首屏优先级、hover 替代
10. 风险、假设、待确认项

### 2. 先可运行，再精修

默认推进顺序：

1. 先搭结构
2. 再定层级与视觉
3. 再补状态与交互
4. 再加动效
5. 再做响应式细化
6. 最后收口性能与细节

### 3. 默认技术与实现立场

- 默认优先原生 HTML / CSS / JS
- 若已有项目使用 React / Next / Vite，则优先延续，不轻易换栈
- 页面设计必须能真实落地为可运行代码
- 视觉表达必须服务页面目标，不为炫技牺牲信息传达

### 4. 默认图标规则

- 默认只使用 `Lucide`
- 不混用多套图标库
- 若 `Lucide` 无法满足，再说明原因后扩库
- 图标线宽、圆角、视觉密度必须统一

### 5. 默认资源策略

默认浏览器侧资源优先使用以下 CDN：

- Axios：`https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js`
- Tailwind CSS：`https://cdn.tailwindcss.com`
- Lucide：`https://unpkg.com/lucide@latest`
- Web Awesome CSS：`https://ka-f.webawesome.com/webawesome@3.8.0/styles/webawesome.css`
- Web Awesome loader：`https://ka-f.webawesome.com/webawesome@3.8.0/webawesome.loader.js`
- anime.js：`https://cdn.jsdelivr.net.cn/npm/animejs/dist/bundles/anime.umd.min.js`

使用原则：

- 优先延续项目现有技术栈与资源体系
- 新建页面若无既有约束，先按以上默认资源策略落地
- 偏离默认资源策略时，要能说明是因为项目既有体系、性能、合规或用户指定

### 6. 配图与图片素材策略

适用于需要真实配图、用户不提供素材、且明确允许去线上找图的场景。

- 设计时优先找真实图，找不到再用 SVG 占位
- 用户提供图片时优先用用户素材
- 只有在用户明确同意后，才去线上找可商用免授权图
- 默认图库源：
  - `unsplash.com`
  - `pexels.com`
  - `pixabay.com`
  - `shopify.com/stock-photos`
- 获图优先顺序：
  1. 用户提供图片或 URL
  2. 图站稳定 CDN 热链 URL
  3. 搜索页辅助获取候选
  4. 实在找不到再退化为 SVG 占位
- 每个图片 URL 上线前都必须校验可用，并确认页面预览无破图
- 所有选用图的 URL、用途、状态都要写入 `ASSETS.md`
- 若交付物依赖外网热链，交付时要说明；若要求自托管，再下载进项目资产目录并改引用

## 例外情况

- 用户或调度方明确要求“直接做 / 不用先出方案”时，可跳过方案确认门，但交付时要说明
- 项目现有设计系统、品牌规范或技术栈与默认规则冲突时，优先延续项目体系

## 关联跳转

- 设计判断和风格控制：[`design-principles.md`](./design-principles.md)
- 阶段推进和 gate：[`workflow.md`](./workflow.md)
- 响应式和图片校验：[`responsive-delivery.md`](./responsive-delivery.md)
