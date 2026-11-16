# 每日 GitHub 精选 · 2026-11-16（第 22 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、工程实践（2）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | 应用项目 | Python | 72.5k | 周榜 +4,548 ⭐ |
| 2 | [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | 工程实践 | TypeScript | 57.0k | 日榜 +717 ⭐ |
| 3 | [Tencent/LoopForge](https://github.com/Tencent/LoopForge) | 工程实践 | Go | 1.5k | 日榜 +423 ⭐ |
| 4 | [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | AI Agent | TypeScript | 17.9k | 日榜 +355 ⭐ |
| 5 | [google/elephant-goldfish-model](https://github.com/google/elephant-goldfish-model) | AI Agent | Python | 19.8k | 周榜 +5,060 ⭐ |

---

## 1. Daily Stock Analysis —— LLM 驱动的多市场股票自动分析与推送系统

**一句话简介**：README 顶部写着「不构成任何投资建议」，但架不住 72k 人想要一个每天自动读研报的机器人——这是 Trending 上中文社区规模最大的 LLM 实用项目。

**仓库信息**
- 地址：https://github.com/ZhuLinsen/daily_stock_analysis
- 类目：应用项目 ｜ 语言：Python ｜ Stars：72.5k（72531）｜ 近期增量：周榜 +4,548 ⭐
- 协议：MIT ｜ 官网 / 文档：中英繁三语 README + docs/ 完整配置与部署指南 + Web 工作台文档 + arXiv 引用元数据 + CI（backend-gate）+ Docker 镜像

**核心功能**
- **AI 决策报告与策略问股**：输出核心结论、评分、趋势、买卖点位、风险警报、催化因素与操作检查清单；支持均线、缠论、波浪、热点题材等 15 种内置策略的多轮 Agent 问股，Web / Bot / API 三入口。
- **六市场数据聚合**：覆盖 A股、港股、美股、日股、韩股、台股与 ETF 的行情、K 线、技术指标、新闻、公告与基本面；数据源分层可配（TickPlus / Tushare / AkShare / YFinance / Longbridge 等），带端点级熔断与降级规则。
- **零成本定时运行**：推荐姿势是 Fork 仓库 + 配 Secrets + 启用 Actions，每个工作日 18:00（北京时间）自动执行；也支持 Docker、本地定时与 FastAPI 常驻服务，非交易日自动跳过。
- **全渠道推送**：决策仪表盘与大盘复盘自动推送到企业微信 / 飞书 / Telegram / Discord / Slack / 邮箱，支持 Markdown 转图片的分享海报。
- **Web 工作台**：本地 WebUI 提供配置管理、任务监控、历史报告、回测、持仓管理与智能导入（图片 / CSV / Excel / 剪贴板），浅色 / 深色主题。

**技术栈**
Python + FastAPI + litellm 多模型路由（Gemini / Claude / OpenAI 兼容 / DeepSeek / Ollama 本地）；行情源 AkShare / Baostock / YFinance / Tushare / Longbridge；新闻搜索 SerpAPI / Tavily 等；部署 GitHub Actions / Docker / 本地定时；CI 与回归测试齐备。

**适用场景**
个人投资者的每日自选股盯盘与复盘；想学「LLM + 结构化数据管道」工程化落地（熔断、fallback、缓存、回归测试全套）的开发者；团队内部的行情播报机器人。

**推荐理由**
- **工程化程度罕见的完整**：从数据源熔断、凭据轮换到 Windows smoke test 一路有回归测试兜底，提交记录里能看到真实 CI 评审往来的痕迹——不是一蹴而就的爆款壳子。
- **中文社区最大规模的 LLM 应用样本之一**：72k stars / 57k forks 意味着大量真实用户在跑；对想抄「LLM 应用完整闭环」作业的团队，这是现成的高级参考实现。

> **注意**：仅供学习研究，不构成投资建议（README 明示免责声明）；免费行情源受上游限流影响稳定性不保证，长期定时建议自配 Tushare / Longbridge token；LLM 与新闻搜索 API Key 需自备（部分付费）；README 含赞助商推广位；分析质量取决于模型与数据源，切勿直接当交易信号。

> **一句话理解**：像一个每天 18 点准时给你发简报的机器人分析师：数据采集、模型解读、推送管道全套管齐——但它递给你的是「功课」，不是「答案」。

---

## 2. chrome-devtools-mcp —— 把 Chrome DevTools 变成编码 agent 的 MCP 工具箱

**一句话简介**：Chrome 官方团队把 DevTools 整个塞给了 AI：从此 agent 不只能打开网页，还能亲手量性能、截网络、翻堆快照。

**仓库信息**
- 地址：https://github.com/ChromeDevTools/chrome-devtools-mcp
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：57.0k（56971）｜ 近期增量：日榜 +717 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：README 完整 + v1.13.0 正式 release（11-11）+ npm 发布 + Claude / Cursor / Kimi Code / Gemini 多 agent 插件配置 + Lighthouse 集成 + CI

**核心功能**
- **完整 DevTools 工具面**：性能追踪（performance trace + 内置 Lighthouse 13.6）、网络模拟与 mock（含上游 mock 与二进制请求体保存）、堆快照分析、console 处理、CSS 样式检查（支持自定义变量内联解析）。
- **多 agent 开箱适配**：官方提供 .claude-plugin / .cursor-plugin / .kimi-code-plugin / .gemini 插件配置，主流编码 agent 直接安装；支持连接运行中的 Chrome 实例（--browserUrl / --wsEndpoint / --autoConnect）。
- **灵活运行模式**：可自启浏览器或接管现有实例，支持 --headless、指定 channel（如 Canary）与 --executablePath；新增 inspect-in-devtools skill 需 Chrome Canary M159+。
- **官方维护、迭代凶猛**：v1.13.0 于 11-11 正式发布，11-13 仍在合入功能提交；57.0k stars、日增 +717，是 DevTools 生态面向 agent 时代的官方答案。

**技术栈**
TypeScript + Chrome DevTools Protocol + Lighthouse；MCP 标准接口；npm 发布（chrome-devtools-mcp）；CI 与第三方许可声明（含 Lighthouse bundle notices）齐备。

**适用场景**
让编码 agent 自主调试前端：跑性能 trace 找长任务、mock 网络测边界、读堆快照查内存泄漏；CI 里做浏览器侧验收；agent 驱动的 UI 回归与样式审查。

**推荐理由**
- **官方出品，生态位独占**：Chrome DevTools 团队亲自维护，能力覆盖与协议演进同步，第三方 MCP 浏览器工具难以企及的「一手数据」深度。
- **把「agent 只能猜」变成「agent 能测」**：以前 agent 调前端靠截图与日志猜问题，现在能直接拿到 trace、网络、内存的一手证据，调试质量是质变不是量变。

> **注意**：需要本机安装 Chrome（部分能力要 Canary 版）；性能追踪等重能力在 agent 循环里调用开销不小，注意上下文与 token 消耗；沙箱 / 无界面环境使用前先验证浏览器启动路径。

> **一句话理解**：相当于给 AI 配了一副能看进浏览器内部的眼镜加一块仪表盘——从「看风景」升级成「读仪表读数、拆发动机」。

---

## 3. LoopForge —— 腾讯开源的多 agent 编码交付编排平台

**一句话简介**：腾讯把「一群 coding agent 接力交付一个项目」做成了带人工审批门的流水线：SOP 流程图排工序，人签字才放行。

**仓库信息**
- 地址：https://github.com/Tencent/LoopForge
- 类目：工程实践 ｜ 语言：Go ｜ Stars：1.5k（1526）｜ 近期增量：日榜 +423 ⭐
- 协议：MIT ｜ 官网 / 文档：双语 README + loopforge.cn 官网 + deploy/ 一键部署 + Contributing / Security policy / Code of Conduct 治理文件齐备 + amd64/arm64 镜像

**核心功能**
- **SOP 流程图编排**：以节点 + 边的流程图定义多阶段交付流程，支持拓扑排序执行、阶段 handoff、中间插节点；Local 工作流可配 multi.auto_mode 等 YAML 选项。
- **多 agent 编排**：编排 CodeBuddy、Codex、Claude Code 协同执行，另有 Cursor / Kimi / DeepSeek 相关条目；对话工作区跟踪每个交付的进度。
- **人工审批门**：关键节点插入「请求批准」门控（human-on-the-loop），原生审批组件就位；上一步产物未经人签收不进下一站。
- **沙箱执行与 Git 集成**：Docker 自定义镜像沙箱（挂载 Node / npm / Python 工具链）；GitHub 适配器与 SSH 仓库支持（per-host 用户密钥）；runner 经 bind-cli 装成 systemd 服务或 crontab @reboot。
- **平台化治理**：成员账号、共享 CodeBuddy Key、中英双语 UI、MySQL / SQLite 双数据库、amd64/arm64 镜像，官网 loopforge.cn。

**技术栈**
Go 编写；Docker 沙箱 + runner 执行机；MySQL（含 migrations）或 SQLite；Dockerfile + deploy/ 部署；324 commits、114 branches，开源治理文件齐备。

**适用场景**
团队把 coding agent 纳入正式研发流程：多 agent 接力改代码、人审关键合并；企业内网自托管 agent 工作台；SOP 化的重复交付任务（依赖升级、补丁批量移植等）。

**推荐理由**
- **「编排 + 审批」是 agent 落地的真缺口**：市面上不缺单兵 agent，缺的是把多个 agent 按企业流程组织起来、且人保留否决权的编排层；LoopForge 恰好补在这。
- **腾讯出品、起步期参与成本低**：Trending 日增 +423（本期 Go 项目最高），11-14 仍有提交；1.5k stars 意味着现在参与还能影响方向。

> **注意**：项目较新（1.5k stars、15 tags），API 与流程模型可能仍在快速演进；自托管需自行运维 runner 与数据库；与 CodeBuddy 生态耦合的功能在其他 agent 上体验可能打折。

> **一句话理解**：像一条带安检门的流水线：机器人各自干活，但每道工序的成品都要过人签收才能进下一站——效率来自机器，安全感来自那道门。

---

## 4. AG-UI —— 把 Agent 运行流接入前端的开放事件协议

**一句话简介**：MCP 管 agent 用什么工具，A2A 管 agent 之间怎么说话，AG-UI 补上第三块：agent 怎么把执行过程实时画进你的界面。

**仓库信息**
- 地址：https://github.com/ag-ui-protocol/ag-ui
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：17.9k（17897）｜ 近期增量：日榜 +355 ⭐
- 协议：MIT ｜ 官网 / 文档：docs/ 完整 + AG-UI 1.0 规范草案（RFC 2119 + JSON Schema）+ Dojo 示例站 + npx create-ag-ui-app 快速起步 + Discord 社区 + 双周工作组

**核心功能**
- **约 16 种标准事件**：定义运行生命周期（RUN_FINISHED / RUN_ERROR / interrupt / cancelled）、步骤、消息流式、工具调用（含 pendingToolCallIds）、token 用量（缓存读写分账）等事件族，JSON Schema 为唯一事实源。
- **传输无关 + 宽松匹配**：SSE / WebSocket / webhook 等任意传输皆可，middleware 层做宽松事件格式匹配；附参考 HTTP 实现与默认连接器，起步即用。
- **20+ 框架与运行时支持**：LangChain、CrewAI、Google ADK、Microsoft Agent Framework、AWS Strands、Mastra、Pydantic AI、Claude Agent SDK 等已支持或内置；社区 SDK 覆盖 Kotlin / Go / Dart / Java / Rust / Ruby / C++ / .NET。
- **1.0 规范草案落地**：RFC 2119 语言的行为规范 + JSON Schema + 跨 SDK 一致性 fixtures 语料库；生成器从 schema 产出 TS / Python / .NET / protobuf 类型，漂移门禁保证字节级一致。
- **Dojo 示例与 CLI**：npx create-ag-ui-app 秒建应用；Dojo 站用 50-200 行的小例子演示全部构建块，支持对已发布 npm / PyPI 包跑 e2e。

**技术栈**
TypeScript monorepo（nx）+ Python / .NET SDK + protobuf 传输；MIT 协议；npm / PyPI / NuGet 发布；CI 含 spec 漂移门禁与 Dojo e2e 矩阵。

**适用场景**
给自研 agent 配一个能实时流式展示推理与工具调用的前端；把 LangChain / CrewAI agent 嵌入产品 UI；需要 human-in-the-loop（打断、确认、审批）交互的 agent 应用。

**推荐理由**
- **协议位稀缺且已成事实标准**：agentic 协议栈里 UI 这一层此前无公认方案，AG-UI 靠 CopilotKit 与 LangChain / CrewAI 的出身拿下 20+ 框架内置支持，17.9k stars 印证。
- **工程严谨度像样**：JSON Schema 单一事实源 + 生成器 + 漂移门禁 + 跨 SDK 一致性语料，把「协议漂移」这个多语言生态的常见病按住了。

> **注意**：协议仍在 1.0 草案阶段，事件语义与兼容性承诺可能微调；部分框架集成标记 In Progress；深度集成（自定义传输、生成器扩展）仍需读规范文档。

> **一句话理解**：像是给 agent 装了一块标准化仪表盘与方向盘接口：不管引擎是哪家造的，中控台的转速表和按钮都能通用。

---

## 5. Elephant-Goldfish Model —— Google 开源的 agent 规格盲审插件

**一句话简介**：Google 开源的评审插件把「金鱼记性差」变成了优点：评审员故意不带历史上下文，专门挖你没写进文档里的假设。

**仓库信息**
- 地址：https://github.com/google/elephant-goldfish-model
- 类目：AI Agent ｜ 语言：Python ｜ Stars：19.8k（19808）｜ 近期增量：周榜 +5,060 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：egm.dev 文档站 + Quickstart / Architecture / Testing 分册 + CONTRIBUTING（stacked PR 工作流）/ ACCESSIBILITY / AI_POLICY + CI lint + 60 秒上手命令

**核心功能**
- **大象起草，金鱼盲审**：Elephant 角色持有项目上下文与历史决策、起草规格文档；Goldfish 评审员只看文档与它引用的源材料（不带先前对话），用全新子会话审出未言明假设、模糊需求与实现风险；你拍板架构取舍并批准规格。
- **60 秒评审现有文档**：对已有设计文档 / README / PR 计划直接跑 /egm:egm-review，无需重写规格；评审检查文档清晰度、与代码的匹配度与实现计划。
- **漂移检测**：/egm:egm-drift-report 对比 docs/ 目录每份文档与当前源码，报告哪些地方文档与实现已经分叉，由人决定改文档还是改代码。
- **多 harness 适配**：支持 Claude Code / Codex / Claude Cowork / ChatGPT 等安装路径；评审员隔离与插件资源路径有专门修复与参数化测试（test_claude / test_codex / test_harnesses）。
- **配套完整**：egm.dev 文档站、架构与测试分册、AI_POLICY、CI lint；19.8k stars、周增 +5,060，11-15 仍在合入安全修复。

**技术栈**
Python（pyproject）+ agent skill 插件体系；Claude / Codex 等 harness 的适配层与测试；Apache-2.0；README 明示「非官方支持的 Google 产品」。

**适用场景**
规格 / 设计文档的独立盲审；文档与代码漂移的例行巡检；团队引入「评审不带偏见」流程的参考实现；想学「子会话隔离评审」这一 agent 编排模式的开发者。

**推荐理由**
- **一个反直觉的好想法**：评审员「失忆」恰恰是价值来源：不带历史偏见，只对文档本身与代码事实提问——把 LLM 的上下文局限设计成了机制。
- **Google 出身、增长真实**：Apache-2.0、有文档站与 CI、11-15 仍在修 bare-mention 绕过这类评审隔离漏洞，周 +5,060 的增长由口碑驱动而非营销。

> **注意**：非官方支持的 Google 产品；盲审依赖 agent 能创建全新子会话，不支持的 harness 会主动停止评审；评审不替代测试与人的判断（README 明示验证边界）；名字奇特但项目实质完整，无占位迹象。

> **一句话理解**：像请一位刚入职的同事来审方案——他没参与之前的讨论，正因为「不记得你们聊过什么」，才能问出最扎心的那个问题。

---

## 附录：本期说明

### 数据来源与筛选口径

| 维度 | 标准 |
|------|------|
| 时间活性 | 最近 30 天内有提交，非归档仓库 |
| 热度门槛 | 周榜增量 ≥ 300 ⭐ 或日榜增量 ≥ 80 ⭐ |
| 存量门槛 | 总 stars ≥ 1,000 |
| 仓库资质 | 非 fork、非 awesome / 资源聚合列表、非纯教程大纲、非空壳；License 明确且有 README 正文 |
| 质量信号 | 有 CI / 测试 / 文档站 / 正式 release 者优先 |
| 类目配额 | 每期 2–5 个，至少覆盖 2 个类目，单类目 ≤ 2 个 |
| 去重基线 | `archive/index.json` 中记录的历史仓库 |

### 本期取舍说明

- 数据来源：Trending 日榜 12 条 / 周榜 11 条 / 月榜 15 条，合并去重后筛选；本期 5 个入选覆盖应用 1、工程 2、Agent 2 共三个类目，算法/模型类目空缺（见下）。五个仓库的 License（MIT ×3、Apache-2.0 ×2）与最近提交时间（全部为 11-13 之后）均逐个打开仓库页 / LICENSE 文件核验。
- 网络环境说明：本机 bash 侧 HTTPS 仍被网络层拦截（TLS 握手无法完成，与 11-04 同形态），api.github.com 不可达；取数与核验全流程改走 WebFetch 工具通道，且通道极不稳定（实测约每分钟仅 1 次请求成功），全部核验以串行间隔重试完成。发布环节若 push / 飞书仍被拦截，按规则跳过并保留本地 commit 待网络恢复补推。
- 算法/模型类目连续空缺：Trending 上唯一算法向候选 ggml-org/ggml 日增 +43 未达 80 门槛、周增量无法核验；Search API 在当前网络不可用，宁缺毋滥。
- daily_stock_analysis 的 fork 数（57.6k）超过常规比例属正常现象：推荐用法即 Fork 后配 Secrets 跑 GitHub Actions，天然促发大规模 fork，不是数据异常。
- egm 名称说明：Elephant-Goldfish Model 是项目正式名称（官方站点 egm.dev），README 与提交记录确认其为规格评审插件，无占位 / 测试仓库迹象。

**本期按规则排除的候选**

- anthropics/skills（195.4k，周 +6,077）、addyosmani/agent-skills（118.0k，周 +3,889）、google-labs-code/stitch-skills（9.3k，日 +247）、elementalsouls/Claude-BugHunter（6.5k，日 +98）、tradermonty/claude-trading-skills（5.6k，日 +706）、Nutlope/hallmark（55.5k，月 +25,448）、cloudflare/security-audit-skill、pbakaus/impeccable、Leonxlnx/taste-skill、AgriciDaniel/claude-seo、Vincentwei1021/video-shotcraft —— 技能 / 规则 / 提示词包合集，照旧整类排除。
- GoogleChrome/modern-web-guidance-src（7.2k，日 +1,219）—— 「给编码 agent 的 Web 最佳实践」内容分发仓库，按「非资源聚合」口径排除。
- dream-num/univer（25.9k，日 +988）、alibaba/open-code-review（52.1k，日 +691）、meta/astryx、sherlock-project/sherlock、vercel-labs/agent-browser、we-promise/sure、google-deepmind/mujoco —— 往期已推送，按 archive/index.json 去重排除。
- milind-soni/OpenMausBot（23.5k，周 +5,463）—— 维持既往排除口径（海量 open issues、仓库 426MB、宣传与实质不符）。
- ggml-org/ggml（15.9k，日 +43）—— 增量未达 80 门槛。backnotprop/plannotator（11.9k，日 +866）与 NVIDIA/SkillEvaluator（1.7k，日 +122）达标但 Agent / 工程类目配额已满（单类目 ≤ 2），留作后续候选。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-16 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
