# webgen 页面设计 Skill 职责地图

> 适用场景：需要确定 skill 选型和调用顺序
> 何时阅读：设计定向完成后、实现前或专项优化前
> 上游文档：[`workflow.md`](./workflow.md)、[`index.md`](./index.md)
> 下游文档：[`motion-selection.md`](./motion-selection.md)

## 本页只回答什么

- 当前任务应该调用哪个 skill
- 不同页面场景推荐怎样串联 skill

## 按能力找 Skill

### `design-taste-frontend`

作用：

- 先产出初始蓝图、布局骨架、层级方案与微交互方向
- 负责反模板味约束、版式节奏、材质控制、字体与色彩落地规则
- 强制补齐 `Loading / Empty / Error / Active Feedback`

使用时机：

- 从 0 到 1 做页面蓝图
- 页面普通、像模板，需要拉开结构与节奏
- 需要把审美方向直接落到首版 HTML / 前端布局

强制要求：

- 所有 landing page / 营销站 / 作品集 / 重设计类页面，进入最终实现前必须先由该 skill 输出初始蓝图
- 写任何页面代码前，先产出一行 `Design Read`
- 再根据 `Design Read` 确定 `DESIGN_VARIANCE / MOTION_INTENSITY / VISUAL_DENSITY`
- 再声明 `Atmosphere Layer`
- 将这些结论写入 `DISCOVERY.md`

### `impeccable`

作用：

- 作为质量体检与专项优化工具箱
- 可先用 `audit` 做专业体检，再根据问题调用 `arrange / typeset / colorize / polish / animate / harden`
- 风格稳定后，可在其体系内使用 `teach-impeccable` 沉淀长期风格约束

使用时机：

- 初始蓝图完成后，需要系统找问题
- 页面需要按布局、排版、色彩、细节、动效、稳健性分别打磨
- 项目风格已经清晰，希望记住风格以供后续复用

### `frontend-design`

作用：

- 把设计意图落实为页面结构、组件组织与前端实现方案
- 负责区块拆分、信息分层、结构落地
- 负责把蓝图和优化结论转成真实前端页面代码

使用时机：

- 需要从设计蓝图推进到真实页面实现
- 需要梳理组件组织和结构层级
- 需要把设计约束落成可运行页面

### `superpowers`

作用：

- 提供执行纪律、规划、分步推进、验证与收口流程
- 偏工作方法，不替代视觉设计

使用时机：

- 任务较大
- 需要多阶段推进
- 需要更强验证与交付秩序

### `gsap-*`

作用：

- 用于滚动叙事、时间线编排、多元素联动、复杂转场与性能收口
- 应按任务类型路由到具体 skill，而不是只写 `gsap-*`

推荐路由：

- `gsap-core`：基础 tween、easing、`transform / opacity`
- `gsap-timeline`：多步骤编排、时间线控制
- `gsap-scrolltrigger`：滚动驱动、`pin`、`scrub`、分段触发
- `gsap-react`：React / Next 生命周期、作用域与清理
- `gsap-performance`：性能收口、避免卡顿、降级建议

### `teach-impeccable`

作用：

- 在项目风格逐渐稳定后，记录长期有效的设计上下文与风格原则
- 让后续迭代尽量延续同一审美和品牌方向

使用时机：

- 已完成若干轮审查与优化，风格已明确
- 需要把项目长期风格约束沉淀下来

## 按场景串联

### 默认页面

推荐顺序：

1. `superpowers`
2. `design-taste-frontend`
3. `audit`
4. 按报告选择 `arrange / typeset / colorize / polish / animate / harden`
5. `frontend-design`
6. 需要动效时，再接 `Anime.js / Motion / gsap-*`
7. 风格稳定后，再用 `teach-impeccable`

### 首页需要滚动叙事与强动效

推荐顺序：

1. `design-taste-frontend`
2. `audit`
3. `gsap-core`
4. `gsap-timeline`
5. `gsap-scrolltrigger`
6. React 项目补 `gsap-react`
7. `animate + gsap-performance`
8. 再按报告补 `arrange / typeset / colorize / polish / harden`
9. `frontend-design`

### 后管系统工具界面

推荐顺序：

1. `superpowers`
2. `design-taste-frontend`
3. `frontend-design`
4. 必要时补 `Motion`
5. `audit`
6. 再按问题补 `arrange / typeset / colorize / polish / harden`

### 品牌页需要特效与记忆点

推荐顺序：

1. `design-taste-frontend`
2. `audit`
3. 先走 `arrange / typeset / colorize`
4. 场景判断后选择 `Anime.js / Motion / gsap-* / Three.js`
5. 若用 GSAP，按 `core -> timeline / scrolltrigger -> react -> performance`
6. 最后做 `polish / animate / harden`

## 例外情况

- 只有用户明确要求截图验收时，才额外走 CDP 截图
- `teach-impeccable` 不能替代初始蓝图、体检和专项优化

## 关联跳转

- 动效库选择：[`motion-selection.md`](./motion-selection.md)
- 标准流程：[`workflow.md`](./workflow.md)
