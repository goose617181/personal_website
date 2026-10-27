# Agent.md — AI 开发规范

## 项目说明
木滋垚的个人网站：纯静态单页（HTML + CSS + 原生 JS），深色终端风格，部署在 GitHub Pages。

## 运行方式
- 本地预览：直接双击 index.html；或在本目录执行 `python -m http.server 8000` 后访问 localhost:8000
- 部署：`git push` 后 GitHub Pages 自动发布（root 模式）

## 硬性约定
1. 视觉规范以 PRD.md 第 5 节为准：深色终端主题、主色 #4ade80，禁止蓝紫渐变
2. 零外部依赖：禁止引入任何 CDN（JS / CSS / 字体 / 图片），样式全部手写在 style.css
3. 页面内容用中文，代码注释用中文
4. 每完成一个功能块（导航 / Hero / 项目卡 / 响应式）必须 `git commit` 一次，提交信息写清改动内容
5. 修改样式后必须本地打开 index.html 目检两种宽度（≥1024px 与 ≤768px），确认不破版才算完成
6. 不新增框架、不使用构建工具；动效只用 CSS + 原生 JS 实现
7. 仓库根目录必须保留 index.html，不得移入子目录（GitHub Pages root 部署要求）
