# 每日 GitHub 精选 · 归档

每天自动筛选 2–5 个优质开源仓库，覆盖 **应用项目 / 算法模型 / 工程实践 / AI Agent** 四类，
每个仓库附项目简介、核心功能、技术栈、适用场景与推荐理由（含局限）。

累计 **1** 期 · **5** 个仓库。

## 怎么读？

GitHub 对 `.html` **只显示源码**，不会渲染。所以请按下面的方式读：

| 想要的效果 | 点哪个 | 说明 |
|-----------|--------|------|
| 直接看内容 | 下表「**阅读**」 | 指向 `.md`，GitHub **原生渲染**成排版好的页面 ✅ 推荐 |
| 看网页版原貌 | 下表「**网页版**」+ 预览服务 | 见下方「网页版怎么打开」 |
| 一张图带走 / 发群 | 下表「**长图**」 | GitHub 会内联显示图片 |

### 网页版怎么打开

`daily/*.html` 是自包含的单文件网页，但需要「以网页方式」提供才能渲染，三种办法任选：

1. **开启 GitHub Pages（推荐，一次性设置）**
   仓库 `Settings → Pages → Source: Deploy from a branch → main / (root)` → Save。
   之后访问：https://luyao-appleaccount.github.io/github-daily-archive/
   每期网页版即为：`https://luyao-appleaccount.github.io/github-daily-archive/daily/github-daily-YYYY-MM-DD.html`

2. **免设置，用第三方预览服务**（把日期替换掉即可直接看）：
   `https://raw.githack.com/luyao-appleaccount/github-daily-archive/main/daily/github-daily-YYYY-MM-DD.html`

3. **本地看**：`git clone` 后用浏览器打开 `daily/github-daily-YYYY-MM-DD.html`。

> 换句话说：**要内容，读 `.md`；要样式，用 Pages；要一张图，看长图。**

> 🌐 在线浏览（GitHub Pages）：https://luyao-appleaccount.github.io/github-daily-archive/

## 归档目录

| 日期 | 本期收录 | 日报 |
|------|---------|------|
| **2026-09-28** | hindsight · open-code-review · WeKnora · scriptc 等 5 个 | [阅读](daily/github-daily-2026-09-28.md) · [网页版](daily/github-daily-2026-09-28.html) · [长图](daily/github-daily-2026-09-28.jpg) |

## 目录结构

```
daily/github-daily-YYYY-MM-DD.md     Markdown 日报（GitHub 原生渲染，推荐阅读）
daily/github-daily-YYYY-MM-DD.html   网页版（自包含单文件，配 Pages / 预览服务使用）
daily/github-daily-YYYY-MM-DD.jpg    整页长图（可选，GitHub 内联显示）
index.json                           去重索引：每期推送过的仓库清单
```

## 筛选标准

| 维度 | 标准 |
|------|------|
| 时间活性 | 最近 30 天内有提交，非归档仓库 |
| 热度门槛 | 周榜增量 ≥ 300 ⭐ 或日榜增量 ≥ 80 ⭐ |
| 存量门槛 | 总 stars ≥ 1,000 |
| 仓库资质 | 非 fork、非 awesome / 资源聚合列表、License 明确、有 README 正文 |
| 质量信号 | 有 CI / 测试 / 文档站 / 正式 release 者优先 |
| 类目配额 | 每期 2–5 个，至少覆盖 2 个类目，单类目 ≤ 2 个 |
| 排除项 | 刷星仓库、空壳仓库、纯教程大纲、往期已推送过的仓库 |

---

*由自动化任务每天自动提交 · 去重基线见 `index.json`*
