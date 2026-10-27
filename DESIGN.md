# 技术设计文档

## 1. 技术栈
- 纯 HTML5 + CSS3 + 原生 JavaScript（ES6），零框架、零构建、零外部依赖
- 字体：系统字体栈（等宽用 Cascadia Code / Consolas；正文用 -apple-system / Segoe UI / 微软雅黑）
- 部署：GitHub Pages，`Deploy from a branch` + `/ (root)` 模式

## 2. 选型理由
- 单页展示型网站不需要框架与构建工具，纯静态最简、加载最快
- 零外部依赖可保证任何网络环境下样式完整（吸取 Tailwind CDN 外链风险的教训）
- GitHub Pages 已在电商插件项目上验证可用，且免额外注册授权

## 3. 目录结构
```
PersonalWebsite/
├── index.html   # 单页入口（结构 + 内联 JS：打字动画、滚动显现）
├── style.css    # 全部样式（深色终端主题）
├── PRD.md       # 产品需求文档
├── DESIGN.md    # 本文档
└── Agent.md     # AI 开发规范
```

## 4. 关键技术点
1. **打字机动画**：原生 JS `setTimeout` 逐字输出命令到 `#typed`，CSS `@keyframes blink` 实现光标闪烁
2. **滚动显现**：`IntersectionObserver` 监听 `.reveal` 元素进入视口后加 `.visible` 类，CSS 过渡淡入上移
3. **终端窗口**：CSS 圆角深色窗口 + 三个状态圆点（红黄绿）+ 等宽字体内容区 + 顶部标题栏
4. **网格背景**：`linear-gradient` 双向 1px 线条平铺绘制，`background-size: 40px 40px`
5. **响应式**：≤768px 时项目卡片改单列、Hero 字号缩小、导航链接间距收紧

## 5. 性能与兼容
- 单 HTML + 单 CSS，总体积 < 30KB，无图片资源（图标用 emoji 与 CSS 绘制）
- 兼容近两年版本的 Edge / Chrome / Firefox（用了 IntersectionObserver，不支持时直接显示不隐藏）

## 6. 部署流程
1. 仓库根目录放 `index.html`（GitHub Pages root 模式硬性要求）
2. `git push` 后到 Settings → Pages 选择 main 分支 `/ (root)`，Save
3. 1-2 分钟后生成 `https://<用户名>.github.io/<仓库名>/` 域名
