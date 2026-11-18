# pages-deploy-template

> **这是 GitHub Pages 静态资源部署的示例仓库，作为模板保留，请勿修改。**
> 新项目请参考本仓库新建自己的仓库（GitHub 上点 **Use this template**，或复制本仓库代码），在这份代码基础上部署网页资源。

把若干静态页面（设计稿、原型、小工具）构建成一个站点，用 GitHub Actions 发布到 GitHub Pages：`https://<用户名>.github.io/<仓库名>/`，配置了自定义域名时为 `https://<域名>/<仓库名>/`。本仓库自身的示例站点：https://juiceless.cn/pages-deploy-template/

基于本模板的项目示例：[anthropic-ipo-monitor](https://github.com/bibi45c/anthropic-ipo-monitor)

## 用本模板开新项目

1. 用本仓库作模板新建仓库（**Use this template**），仓库名就是 URL 的第一段路径
2. 新仓库 Settings → Pages，把 Source 设为 **GitHub Actions**
3. 按下面「新增一个页面」放入自己的页面，推送到 `main` 即自动发布

## 新增一个页面

1. 复制 `_template/` 为新目录，目录名用小写短横线（它就是 URL）：`rewind-ui/` → `/<仓库名>/rewind-ui/`
2. 改 `index.html`；资源用相对路径（`./img.png`），不要用 `/img.png`
3. 改 `demo.json`（标题、描述、日期、标签）
4. 推送到 `main`，Actions 自动构建并发布

`"hidden": true` 只是不出现在首页列表里，页面本身仍然公开可访问。

自带构建的项目（Vite 等）：把构建产物放进对应目录，并把 `base` 设为 `/<仓库名>/<目录名>/`。

## 目录结构

| 路径 | 说明 |
|---|---|
| `_template/` | 新页面模板（构建时跳过） |
| `example/` | 示例页面 |
| `scripts/build.mjs` | 把每个含 `index.html` 的顶层目录复制到 `_site/`，并按 `demo.json` 生成首页索引 |
| `.github/workflows/pages.yml` | 推送到 `main` 时构建并发布到 GitHub Pages |

## 本地预览

```bash
node scripts/build.mjs
npx serve _site
```
