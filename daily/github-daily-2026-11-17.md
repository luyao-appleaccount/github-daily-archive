# 每日 GitHub 精选 · 2026-11-17（第 23 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [KnifeLemon/Filee](https://github.com/KnifeLemon/Filee) | 应用项目 | C# | 28.1k | 周均 ≈4,000 ⭐（估算） |
| 2 | [Edge0-AI/Edge0](https://github.com/Edge0-AI/Edge0) | 算法/模型 | C++ | 12.0k | 周均 ≈1,200 ⭐（估算） |
| 3 | [backnotprop/plannotator](https://github.com/backnotprop/plannotator) | 工程实践 | TypeScript | 12.6k | 日榜 +696 / 周榜 +2,325 ⭐ |
| 4 | [deepseek-ai/dsh-superagent-prototype](https://github.com/deepseek-ai/dsh-superagent-prototype) | AI Agent | TypeScript | 23.5k | 周均 ≈9,700 ⭐（估算） |
| 5 | [CopilotKit/OpenBot](https://github.com/CopilotKit/OpenBot) | AI Agent | TypeScript | 12.6k | 周均 ≈960 ⭐（估算） |

---

## 1. Filee —— 按住一个键拖一下，就转成 270 种格式的离线转换器

**一句话简介**：转换文件这件事被压缩成一个动作：按住 Ctrl 把文件拖到光标处的格式圆环上，松手就完事——不装 Office、不传云端、不问你要邮箱。

**仓库信息**
- 地址：https://github.com/KnifeLemon/Filee
- 类目：应用项目 ｜ 语言：C# ｜ Stars：28.1k（28091）｜ 近期增量：周均 ≈4,000 ⭐（估算）
- 协议：MIT ｜ 官网 / 文档：独立官网 filee.sh + 11 语种 README + 格式总表与引擎说明 docs/ENGINES.md + CLI 文档 + GitHub Actions CI + Certum 签名的正式 release

**核心功能**
- **光标处的格式圆环**：按住 Ctrl（macOS 为 Option）拖动文件，光标处弹出只包含「这些文件能变成什么」的格式圆环，把文件甩到目标格式上即开始转换，进度环走完后新文件已落在同目录。
- **270 种格式，不依赖 Office**：图片（含相机 RAW、DICOM、PSD/PSB、EXR、FITS、iPhone Live Photo）、PDF、Word/Excel/PPT、HWP、电子书、压缩包、字体、CAD、3D 模型、地理数据之间互转，无需安装 Office、Hancom Office 或 LibreOffice。
- **圆环有两面**：按 Tab 或滚轮翻面，露出不常用格式与工具；右键菜单、快捷键、拖放区、命令行 `filee` 四种入口并存，不想用鼠标也能脚本化。
- **重型引擎按需下载**：Ghostscript / LibreOffice / Pandoc / calibre / FFmpeg 只在第一次用到相关格式时才拉取，主程序保持轻量；.NET 10 单文件发布，安装即用。
- **正经的工程底子**：GitHub Actions CI + 单元测试 + 用 Certum 开源代码签名证书签名的 Windows 安装包 + 正式 release + 独立官网与 CLI 文档，不是 demo 级项目。

**技术栈**
C# / .NET 10 + Avalonia 跨平台 UI（Windows 10/11、Linux x64/ARM64、macOS 13+ 预览）；图像链路走 SkiaSharp / ImageMagick 系库；构建 `dotnet build`、测试 `dotnet test`；CI 见 .github/workflows/ci.yml。

**适用场景**
每天被「把这个 PDF 转成 Word」「HEIC 转 JPG」「PSD 导 PNG」打断的人；不方便把文件上传到在线转换站（涉密 / 大文件 / 内网）的场景；需要批量转换脚本的运维与设计岗（走 CLI）。

**推荐理由**
- **把高频小痛点做到极短路径**：同类工具要么是网页（要上传、有体积上限），要么是重型套件（装完几个 G）。Filee 把「选格式」这一步变成手势，路径短到不需要思考。
- **不靠减功能换轻量**：常见做法是功能少所以轻；Filee 反过来——270 种格式覆盖 RAW、DICOM、HWP、CAD、3D，重引擎按需拉取，把能力与体积解耦。

> **注意**：macOS 版仍是预览，只做 ad-hoc 签名、未公证，首次打开需手动放行；Linux 安装脚本依赖系统 Python 3；长期未更新的 Windows 10 且启用 CET 的机器可能因 .NET 组件缺失而无法启动（README 给了缓解命令）；HEIC、HWP、CAD 等格式首次转换要联网下载可选引擎。

> **一句话理解**：像把「文件 → 格式」做成一个转盘：手一甩停在哪个格子，文件就变成哪种格式——不用翻菜单，也不用把文件传到别人的服务器上。

---

## 2. Edge0 —— 在单张消费级显卡上跑 145B MoE 的流式推理框架

**一句话简介**：把「大模型必须住在机房」撕开一条口子：145B 稀疏专家模型在 RTX 5090 24GB 上跑到 121 tok/s，靠的是把专家权重当页表一样按需换入。

**仓库信息**
- 地址：https://github.com/Edge0-AI/Edge0
- 类目：算法/模型 ｜ 语言：C++ ｜ Stars：12.0k（11952）｜ 近期增量：周均 ≈1,200 ⭐（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：arXiv 技术报告 2609.18063 + docs/models/ 模型页与完整基准表 + edge0-infer / edge0-strata 分模块文档 + 多语言 README（含中文）+ GitHub Releases + Hugging Face / ModelScope 权重

**核心功能**
- **流式 MoE：权重按需换入**：专家不必全部驻留显存，按训练过的路由预测把需要的专家从 SSD / 内存流式搬进来；145B Q3_K（40.81 GiB 权重）在 24GB 卡上以 23.14 GiB 显存 + 31.28 GiB 内存驻留运行，两套专家集合不重复计数。
- **统一推理引擎 edge0-infer**：基于 GGML 的一套 C++ API 同时覆盖 35B 原生引擎与 145B/120B 的 edge0-strata 引擎，自带 CLI、OpenAI 兼容本地 server 与桌面 / Android / iOS 聊天示例。
- **原生 4bit 训练与交付**：145B/120B 是从 Qwen3.8-Flash-Next 派生的 latent MoE，直接以 4bit 训练，提供 Q3_K 与 NVFP4 两种权重，Hugging Face 与 ModelScope 双通道发布。
- **可复核的基准**：RTX 5090 D 24GB：16K prefill 3,554.9 tok/s、agent decode 121.2 tok/s；六项基准（DeepSWE 1.1 64.6、Terminal-Bench 2.1 86.5、GPQA-Diamond 90.4、HLE 35.4）连同 4090、M2 Ultra、16GiB 显存受限配置逐档公开。
- **有论文、有 release、有官网**：技术报告 arXiv:2609.18063（The Other Half of the Memory Wall），Releases 提供 Windows / macOS 安装包，多语言 README 含中文，更新日志写到按日期分条。
- **不追求最大，追求能跑**：官方口径是「Think big. Run here.」——目标是让本地 agent 用上接近旗舰的质量，而不是刷一个离线的排行榜第一。

**技术栈**
C++ / GGML + edge0-strata（Strata 分叉，MIT）；后端 CUDA 13（Linux / Windows NVIDIA）、Metal（Apple Silicon）、Vulkan / CPU（35B 引擎）；权重 Q3_K / NVFP4；arXiv 技术报告 + Hugging Face / ModelScope 分发。

**适用场景**
想在本地或内网跑接近旗舰质量的 agent 与长上下文任务，但没有 A100 集群；做端侧与边缘推理（笔记本、迷你主机、Apple Silicon）；研究 MoE 流式换入、路由预测与量化交付的工程团队。

**推荐理由**
- **把「显存墙」当成可工程化的问题**：多数本地推理项目在「放不下就再量化一点」之间打转，Edge0 直接改内存层级：用路由预测把专家当分页调度，属于架构层解法而不是参数层妥协。
- **数据披露完整，可自行复核**：速度表把机型、构建、VRAM/RAM 配额、cgroup 限制都写清楚，甚至标注「16GiB VRAM 那行是同一张卡人为限流」；这种透明度在同类项目里罕见。

> **注意**：代码 Apache-2.0，但 Edge0 自有模型贡献另受「Edge0 Community Model License 1.0」约束（允许商用与生成物商用、不强制公开修改，再分发有额外条款），上生产前务必读 licenses/edge0-model；145B/120B 目前只支持 Linux/Windows + NVIDIA CUDA 13 或 macOS Apple Silicon Metal，iOS/Android 仅 35B；权重 40–48 GiB，实际速度强依赖 SSD 带宽与内存容量。

> **一句话理解**：像把一套 145 册的百科塞进只有一个书架的阅览室：不把整面墙搬进来，而是你翻到哪页，它就提前把下一册递过来——书架小，读得却不慢。

---

## 3. Plannotator —— 给编码 agent 装一块可批注的审阅台

**一句话简介**：agent 干活越来越快，人却越来越插不上话；Plannotator 把「看方案、圈问题、提意见、发回去」压缩成浏览器里的几次点击。

**仓库信息**
- 地址：https://github.com/backnotprop/plannotator
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：12.6k（12602）｜ 近期增量：日榜 +696 / 周榜 +2,325 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：docs.plannotator.ai 完整文档站 + 官网 plannotator.ai + 各 agent 集成 README（Claude Code / Codex / Copilot / Droid / Kiro / Pi）+ 安装脚本 + GitHub Releases 二进制 + 隐私政策（列明网络边界）

**核心功能**
- **就地批注，意见回流**：agent 提出决策、计划、HTML 或完成工作时，本地浏览器自动打开对应界面，你圈画、批注、写评论，点发送后内容直接成为 agent 的下一轮输入，不必再在聊天窗口里逐条复述。
- **代码审阅不止看 diff**：支持本地改动与远端 PR（Git、GitButler、Jujutsu、Perforce、GitHub、GitLab）；「Guided review」让 agent 把大改动拆成章节，核心变更在前、胶水代码在后，每章配一段概览。
- **Inbox：多 agent 的收件箱**：Plannotator Inbox 把多个 agent 的提问、方案、产物、待审文件聚到一个窗口，按「需要你做什么」分组；你不在时不会挂起 agent 会话，回复会送回发起它的那个会话。
- **能审真页面，不只是静态文件**：`plannotator annotate http://localhost:5173` 通过本地代理打开你正在开发的站点，在真实页面上批注，热更新照常工作。
- **几乎所有主流 agent 都能接**：一键安装器自动识别已装 agent 并写好 hooks / skills / slash 命令：Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、DeepSeek Harness、Pi；其他 agent 走 `plannotator inbox mcp`。
- **终端党也有份**：Herdr Annotate 插件与独立的 `plannotator-tui`（Homebrew tap）把同一套批注能力搬进终端，批注记录与图形界面共用同一数据目录。

**技术栈**
TypeScript + Node（本地二进制，GitHub Releases 分发）；浏览器端审阅界面 + 本地代理；插件 / hook / MCP 三种集成方式；另有 `@plannotator/pi-extension` 与 TUI 包。

**适用场景**
用 Claude Code / Codex 做较大改动，需要人在关键节点真正看懂并给结构性反馈；把 agent 的产出变成可评审材料再放行；多 agent 并行时统一收口「现在需要我做什么」。

**推荐理由**
- **补的是 agent 工作流里最缺的一环**：工具链已经解决了「agent 怎么改代码」，却没解决「人怎么高效地表示不完全同意」；批注 → 回流的闭环把 review 搬回它该在的地方。
- **集成面广，落地成本低**：一个安装器覆盖十种 agent、不绑定某一家；已用 Claude Code 插件的人两条命令就能跑起来，试错成本几乎为零。

> **注意**：安装器会联网从 GitHub Releases 解析版本、可选拉取 npm 包与 sidecar，敏感环境建议用 `--minimal` 只装二进制（网络边界见官网隐私政策）；Codex 的原生 Windows hook 仍是实验特性；批注只是「表达意图」，agent 未必按你的意思改对，最终仍要自己看 diff。

> **一句话理解**：像给实习生配一支红笔和一张能直接递回去的稿纸：他先写，你在稿纸上圈「这段不对、那段再展开」，笔迹回到他手上就是下一版的要求。

---

## 4. dsh-superagent —— DeepSeek 开源的「主动型仓库 Agent」原型

**一句话简介**：它不是等你敲 prompt 的助手，而是盯着一个仓库的同事：有人在 issue 里叫它，它自己开工作项、开分支干活、提 PR，再回到原帖回话。

**仓库信息**
- 地址：https://github.com/deepseek-ai/dsh-superagent-prototype
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：23.5k（23506）｜ 近期增量：周均 ≈9,700 ⭐（估算）
- 协议：MIT ｜ 官网 / 文档：docs/ 九篇编号文档（000 哲学 → 008 食谱）+ SETUP.md 交互式安装指南 + 设计文章 Exploring Super-agent Design + `pnpm check` 一键类型检查 / 测试 / 构建

**核心功能**
- **以仓库为单位的常驻 agent**：监听指定 GitHub 仓库（可选接入飞书），被授权的人向它提需求时，它创建 work item，在自己的 agent 会话与独立目录里干活，最后在原对话里以 PR 等形式回复。
- **「少占用注意力」的授权模型**：设计原则写得很直白：只在被要求、或团队事先写好的规则允许时才行动；只在需要人决策或结果可直接使用时才开口——避免一个能替全团队行动的 agent 同时浪费全团队的注意力。
- **人的位置留得清楚**：Web 面板只展示「现在需要人做什么」，把审批与判断集中到一处，而不是让人追着 agent 的日志跑。
- **文档即规格**：docs/ 从 000 到 008 依次是哲学、领域模型、授权、执行、提示词、面板、部署、架构、食谱（如何新增一个 Source），按顺序读就能复原设计意图。
- **安装也交给 agent**：SETUP.md 是给 agent 读的：它一次只问一个问题、装之前先把完整计划给你看，然后才动手装和配。

**技术栈**
TypeScript + pnpm（`pnpm check` 一次跑通 typecheck / test / build）；以 bundle 形式运行在 DeepSeek Harness 上；对接 GitHub API 与飞书开放接口；Web 面板作为人工干预入口。

**适用场景**
小团队想让 agent 承担仓库里的重复型工程任务（修依赖告警、补测试、回 issue）；研究「主动式 agent 的授权模型与注意力成本」；想把内部 IM（飞书）变成 agent 的任务入口。

**推荐理由**
- **难得把「授权」当第一性问题**：多数 agent 项目卖能力，这份原型的卖点是边界：什么情况下它可以自己动、什么情况必须等人——这才是企业落地真正的卡点。
- **官方原型 + 完整设计文档**：DeepSeek 团队从日常开发里长出来的代码，配套一篇设计文章与九篇编号文档；读文档的收获可能大于跑代码。

> **注意**：README 顶部明确写着「仅供研究参考、不是官方产品、非生产可用」，代码风格与工程实践自认不一致，用前必须自行审查；需要 DeepSeek Harness 环境，接 GitHub / 飞书要配 App 与权限；最近提交停在 10 月底，迭代节奏明显慢于榜上其他项目。

> **一句话理解**：像给仓库请了一位只在被叫到时才动手的同事：他不刷存在感、不主动开会，但你说「这块你处理一下」，他就自己建工单、改代码、开 PR，然后回到你说话的地方把结果放下。

---

## 5. OpenBot —— CopilotKit 开源自托管的「AI 同事」工作台

**一句话简介**：把公共 SaaS 里那群 AI 同事换成一个能装进自己机房的版本：模型自选、agent 自带、身份权限与审计自己管。

**仓库信息**
- 地址：https://github.com/CopilotKit/OpenBot
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：12.6k（12606）｜ 近期增量：周均 ≈960 ⭐（估算）
- 协议：MIT ｜ 官网 / 文档：docs/ 架构与配置文档 + Kubernetes / Helm 部署指南 + 官方站 open.bot + 签名镜像与两个 Helm chart + Mac / Windows 签名安装包 + Product Hunt / Trendshift 徽章

**核心功能**
- **模型自选**：OpenAI、Claude、Gemini，或任何 OpenAI 兼容端点的开源模型；可以托管在云上，也可以跑在自己的机器上，换模型不动上层。
- **agent 自带（AG-UI 通道）**：既可用内置 Bot，也可通过 AG-UI 把已有 agent 接进来——Bedrock AgentCore、Claude Managed Agents、LangChain、Microsoft Foundry、Google Agent Platform 等执行平台都能保留。
- **企业级控制面**：后端统一做登录、工具权限、动作策略与审计；内置 Bot 与外部 agent 共享同一工作区，权限在同一层收口，不用每家 agent 各配一套。
- **一条命令上笔记本，Helm 上集群**：Mac / Windows 安装包把前端与 Docker 后端打包在一起；团队用 `openbot-bundle` / `openbot` 两个 Helm chart 部署到 EKS / AKS / GKE 或自有集群（PostgreSQL + 持久卷）。
- **执行环境可插拔**：Bot 的「电脑」默认跑在 Kubernetes 沙箱里，也可接兼容的外部 computer provider；工具走 MCP + 适配器。入口覆盖 Mac / Windows / Web / iOS / Android / Slack / Teams。

**技术栈**
TypeScript（MIT 模板）+ CopilotKit 前端 + AG-UI 协议 + MCP 工具层；OpenBot 后端（签名镜像 + Helm charts）+ PostgreSQL；CopilotKit Intelligence 提供持久会话、记忆、自动学习与治理（单独授权）。

**适用场景**
想把 AI 同事放进内网、又不想把数据交给第三方 SaaS 的团队；已有自研 agent（LangChain / ADK / Bedrock）需要一个统一前端与权限层；需要在 Slack / Teams 里给 agent 开入口的企业。

**推荐理由**
- **自托管 + 开放协议，避开「再租一个 SaaS」**：它没有重新发明 agent 运行时，而是把工作区、权限、审计、多端入口这层做厚，agent 与模型都留在你自己的栈里。
- **同一团队刚把 AG-UI 推成事实标准**：CopilotKit 是 AG-UI 的发起方（上期刚推过 ag-ui），OpenBot 是这套协议第一个重量级「宿主应用」，两者对照看能理解协议为何这样设计。

> **注意**：仓库本身 MIT，但 Kubernetes / 生产部署需要 CopilotKit Intelligence 的试用或商业授权，不是完全免费；单机版仍需 Docker；K8s 评估建议按约 3.15 vCPU（EKS 三台 t3.large）起步；与上期推过的 ag-ui 同源，选型时注意别重复引入同一套协议栈。

> **一句话理解**：像公司自己装修一间 AI 同事办公室：门禁、工位、监控、访客登记都由你装，AI 员工可以是外聘的（接你已有的 agent）也可以自带（内置 Bot）——只是这栋楼的物业（Intelligence）要单独付费。

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

- 数据来源：Trending 日榜 14 条 / 周榜 14 条，合并去重后 28 条，其中 26 条为往期已推送或技能 / 规则合集，当日真正可用的新候选只有 2 个（`backnotprop/plannotator`、`NVIDIA/SkillEvaluator`），因此按既定策略用 Search API 补池（`created:>2026-08-15 stars:>1500`，按 stars 排序取 40 条）。本期 5 个仓库覆盖应用 1 / 算法 1 / 工程 1 / Agent 2，四个类目齐全且单类目不超过 2 个。
- 增量口径说明：只有 plannotator 同时在日榜（+696）与周榜（+2,325）；Filee、Edge0、dsh-superagent、OpenBot 当日未上 Trending，用「建库天数 → 周均星标」估算（分别约 4,000 / 1,200 / 9,700 / 960 每「周），均显著高于 300 的周门槛，日报里已标注「估算」以示区分。
- License 与活性核验：五个仓库逐个打开仓库页读取 SPDX 标识与默认分支，并用 commits.atom 核对最近提交——全部在 11-15 之后，仅 dsh-superagent 停在 10-31（仍在 30 天窗口内）；全部非 fork、非 awesome 列表、非教程大纲、非空壳。
- 两个项目的「开源边界」值得单独说明，已写进各自卡片：Edge0 代码 Apache-2.0，但自有模型贡献另受 Edge0 Community Model License 1.0 约束（允许商用与生成物商用，再分发有额外条款）；OpenBot 仓库 MIT，但 Kubernetes / 生产部署依赖单独授权的 CopilotKit Intelligence。
- 去重基线：archive/index.json 现有 22 期 / 110 个仓库，本期五个仓库均不在其中。`NVIDIA/SkillEvaluator`（日 +873）因 Agent 类目配额已满顺延，下期优先考虑。

**本期按规则排除的候选**

- 技能 / 规则合集整类排除：`anthropics/skills`（周 +5,666）、`addyosmani/agent-skills`（周 +3,960）、`google-labs-code/stitch-skills`（日 +529）、`tradermonty/claude-trading-skills`（日 +837）、`kajisho5/ffmpeg-skill`（日 +367）、`mvanhorn/last30days-skill`（日 +135）、`wheresryan22/anatomy`（27.7k）—— 本质是提示词 / 技能文件包，不是可运行项目。
- `GoogleChrome/modern-web-guidance-src`（周 +6,542）—— 给编码 agent 的 Web 最佳实践内容分发仓库，按「非资源聚合」口径排除。
- `storytold/*` 系列（photocraft 79.8k、craft-anything 34.8k、pdfcraft 20.9k、filmcraft 18.4k、wordcraft 18.1k 等）—— 同一账号在数日内批量发布结构雷同的「clean-room 重写」仓库，描述模板高度一致，按刷量与真实性存疑整簇排除，本期一个不取。
- `peach-mitao/peach`（15.1k，Python）—— 本地优先的媒体管理器，但面向成人内容（README 标注 18+），不适合公开日报推送。
- `openai/math`（17.6k）—— 内部模型产出的 721 篇数学手稿与 Lean 形式化归档，属于研究数据集合而非可复用工程，按内容型仓库排除。
- 一次性 / 合规风险仓库：`Ebony-Vinyl/dsh-our-free-model`（77.4k，免费令牌中转，ToS 风险）、`Gathin23/cleanyourtv`（58.7k，License 为 NOASSERTION）、`eternity4719/HowToLiveBetter` 与 `cdyforever/how-to-live-better`（同一本书的两个版本，内容型）、`yihui-dev/awesome-opus5-5-videos`（awesome 列表）。
- 增量不足或往期已推：`getarcaneapp/arcane`（日 +46，未达 80）、`sveltejs/svelte`（日 +115，知名框架回潮且价值增量有限）、`dream-num/univer`、`alibaba/open-code-review`、`ag-ui-protocol/ag-ui`、`ChromeDevTools/chrome-devtools-mcp`、`sherlock-project/sherlock` 等按 archive 去重排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-17 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
