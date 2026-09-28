# GitHub Daily Digest Archive

每日 GitHub 优质开源仓库精选的归档仓库，由自动化任务每天自动提交。

## 目录结构

```
daily/
  github-daily-YYYY-MM-DD.md      # 当日日报（Markdown）
  github-daily-YYYY-MM-DD.html    # 当日日报（HTML，可直接浏览）
index.json                        # 去重索引：每期推送过的仓库清单
```

## index.json 的作用

自动化任务在每次推送前会读取 `index.json`，把历史出现过的仓库排除掉，保证**同一个仓库不会被重复推送**。
每条记录的格式：

```json
{
  "date": "2026-09-28",
  "repos": ["vectorize-io/hindsight", "alibaba/open-code-review"]
}
```

## 如何检索

- 找某个仓库是哪天推的：在 `index.json` 里搜索仓库名
- 看某天的完整内容：打开 `daily/github-daily-<日期>.html`
- 全局关键词搜索：直接在本仓库用 GitHub 的 code search，或本地 `grep -r "关键词" daily/`

## 筛选标准

| 维度 | 标准 |
|------|------|
| 时间活性 | 最近 30 天内有提交，非归档仓库 |
| 热度门槛 | 周榜增量 ≥ 300 ⭐ 或日榜增量 ≥ 80 ⭐ |
| 存量门槛 | 总 stars ≥ 1,000 |
| 仓库资质 | 非 fork、非 awesome/资源聚合、License 明确、有 README 正文 |
| 类目配额 | 每期 2–5 个，至少覆盖 2 个类目，单类目 ≤ 2 个 |

类目定义：① 应用项目　② 算法/模型　③ 工程实践/工具链　④ AI Agent 及基础设施
