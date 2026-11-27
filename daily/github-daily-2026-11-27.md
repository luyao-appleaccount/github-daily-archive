# 每日 GitHub 精选 · 2026-11-27（第 31 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（2）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [baidu/Unlimited-OCR](https://github.com/baidu/Unlimited-OCR) | 算法/模型 | Python | 32.9k | 周均 ≈1,423 ⭐（建库 162 天，Search 补池） |
| 2 | [DeusData/codebase-memory-mcp](https://github.com/DeusData/codebase-memory-mcp) | 工程实践 | C | 49.2k | 周均 ≈1,252 ⭐（建库 275 天，Search 补池） |
| 3 | [codewhale-hq/Codewhale](https://github.com/codewhale-hq/Codewhale) | AI Agent | Rust | 41.2k | 周均 ≈927 ⭐（建库 311 天，Search 补池） |
| 4 | [XinaTian/MROffice](https://github.com/XinaTian/MROffice) | 应用项目 | TypeScript | 4.5k | 周均 ≈1,839 ⭐（建库 17 天，Search 补池） |
| 5 | [chenglou/handwired](https://github.com/chenglou/handwired) | 算法/模型 | TypeScript | 2.2k | 周均 ≈355 ⭐（建库 43 天，Search 补池） |

---

## 1. Unlimited-OCR —— 百度把长文档 OCR 做成「无限长」

**一句话简介**：传统 OCR 一碰到几十页就崩：注意力随长度平方涨、显存炸掉、跨页表格被切成两半。Unlimited OCR 2 用 SR-SWA 把「看过的东西」压成固定 512 个参考 token，于是第 1 页和第 300 页的解码成本几乎一样。

**仓库信息**
- 地址：https://github.com/baidu/Unlimited-OCR
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：32.9k（32852）｜ 近期增量：周均 ≈1,423 ⭐（建库 162 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：arXiv 两篇论文（2606.23050 / 2610.39308）+ Hugging Face 权重与在线 Demo + ModelScope 镜像 + 百度智能云 API + Transformers / SGLang 部署文档齐全

**核心功能**
- **无限长解析（SR-SWA）**：新增的稀疏参考滑动窗口注意力，把文本-视觉交互压缩到固定大小的工作参考集（约 512 token），每步解码延迟与显存占用几乎不随文档长度增长，从机制上消除二次方复杂度。
- **超长文档双榜 SOTA**：在数十页级基准（MPDocBench）与上百页级极限基准（MarathonDocBench）上均达 SOTA，跨页的表格延续与版面连贯不再断裂。
- **两条推理路径**：Transformers 原生（快速验证，README 给了 A800-80GB 实测环境）与 SGLang（生产推荐，附 mem-fraction、CUDA graph、prefill 分桶等调参说明），对外是 OpenAI 兼容接口，可直接接进现有管线。
- **生态齐全**：权重同时上 HF 与 ModelScope，有 HF Space 在线 Demo、百度云 API；ms-swift 支持微调，vLLM 支持推理，从试用到训练再到服务化都有出口。

**技术栈**
Python / PyTorch（transformers 4.52.1、torch 2.13、bfloat16）+ SGLang 服务化；模型权重托管于 Hugging Face / ModelScope；推理侧兼容 OpenAI API 风格；MIT 协议。

**适用场景**
需要把几百页 PDF（年报、标书、扫描档案）转成结构化文本的团队；做文档 RAG 前处理、必须保住表格与版面结构的工程；要在自有 GPU 上自托管 OCR、不想按页付费的业务。

**推荐理由**
- **长文档这条线终于有人正面解**：多数 OCR 在几十页就退化，百度直接改注意力机制做到「长度无关」，并同时给出两个极端长度榜单的成绩、论文、权重和生产调参——可复现，不是跑分截图。
- **工程可用度少见地高**：不只丢权重：SGLang 启动参数怎么配、mem-fraction 为什么 0.7 而不是 0.75、prefill 分桶与 CUDA graph 怎么对齐，都是踩坑换来的经验，能省大量试错。

> **注意**：显存门槛实在：README 的实测环境是 A800-80GB，消费级卡需要量化或缩小分页窗口；SGLang 那一长串启动参数对并发与显存影响极大，照抄默认值容易 OOM 或吞吐腰斩；小窗口下跨页合体会丢上下文，需按文档类型取舍；开源权重与百度云 API 是两条线，商用前先确认权重许可与数据合规。

> **一句话理解**：像给抄写员换了个记忆方式：每次只看当前一页，外加一张 512 字的摘要卡。所以抄到第 300 页时，他脑子里要同时装的东西还是那么多——不会越抄越慢、越抄越乱。

---

## 2. codebase-memory-mcp —— 给编码 Agent 装一张本地代码地图

**一句话简介**：Agent 读代码的老办法是一个文件接一个文件翻，翻到第 30 个时上下文已经塞满。这个项目先把仓库编成一张图——谁调用谁、哪个 Dockerfile 部署了哪个服务——Agent 一次查询就拿到答案。

**仓库信息**
- 地址：https://github.com/DeusData/codebase-memory-mcp
- 类目：工程实践 ｜ 语言：C ｜ Stars：49.2k（49216）｜ 近期增量：周均 ≈1,252 ⭐（建库 275 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：完整文档站（安装 / 17 个 MCP 工具 / 语言支持 / 性能实测）+ arXiv 2603.27277 预印本 + 每版 GitHub Release（v0.12.1）+ 主分支 CI + SLSA 3 构建证明 + OpenSSF Scorecard

**核心功能**
- **本地代码知识图谱**：源码、文档、配置与基础设施（Dockerfile / Kubernetes / Ansible）编进持久化图；Cypher 查询 <1ms、调用链追踪（深度 5）<10ms、死代码检测约 150ms，全部在本机完成。
- **17 个 MCP 工具 · 164 种语言**：纯 C 后端自带 grammar，不依赖任何语言运行时；混合 LSP 类型解析覆盖 12 种主流语言（TS / Python / Go / Rust / Java / C# / PHP / Kotlin 等），参数绑定、返回类型推断、泛型替换都做了。
- **三路检索融合**：BM25 全文（SQLite FTS5，对 camelCase / snake_case 分词）+ 语义向量（内置 Nomic code embedding，768 维 int8，直接编进二进制）+ 图谱扩散，11 路信号合并打分。
- **零云依赖、零 Key**：索引与查询都可离线，无需托管服务或 API Key；安装器支持 46 种客户端自动配置（含 skills、agent profiles 与钩子）。
- **可视化 Lens（Beta）**：文件夹变成平台、文件与符号变成可点方块，可看 fan-in 热点、两层依赖扩散，也能顺着「谁部署了这个服务」一路追到源码。

**技术栈**
纯 C 后端（无语言运行时依赖）+ SQLite（FTS5）+ 内置 Nomic 代码嵌入 + MCP over stdio；发布覆盖 macOS / Linux / Windows，带 SLSA 3 构建证明与每版 VirusTotal 扫描；MIT 协议。

**适用场景**
接手大型陌生仓库、要在 monorepo 里评估改动影响面的工程；给 Claude Code / Codex / Cursor 一类 Agent 补「结构感知」以减少 token 与臆造；需要在离线或内网环境做代码检索的团队。

**推荐理由**
- **用图换 token，收益可量化**：官方预印本在 31 个仓库上实测：token 用量降约 10 倍、工具调用次数降 2.1 倍；Cypher <1ms 的响应让「多问几次」变得便宜——比单纯要求 Agent 少说话实在得多。
- **供应链严谨度罕见**：纯 C 零依赖、SLSA 3 构建证明、OpenSSF Scorecard、每版 VirusTotal 扫描、原生与前端测试齐全，在这个品类里属于做得最扎实的一档。

> **注意**：576 个 open issue，积压明显，关键功能建议先小范围验证再用；所有关系都是静态推断，运行时拼出的路径、模板变量会留缺口，别当成运行时真相；Lens 仍是 v0.0.1 开放测试；语义检索要传关键词数组而非自然语言长句，传错会明显掉召回；164 种语言里冷门语言的解析深度远不如那 12 种 LSP 语言。

> **一句话理解**：像给一栋大楼画了张带管线的施工图：不用每间房都推门看一遍，问一句「这层的水从哪来」，图上直接顺着管道指给你。

---

## 3. Codewhale —— Rust 写的终端编码 Agent，每一步都留收据

**一句话简介**：用编码 Agent 最不安的是「它到底动了什么」。Codewhale 把每一轮的文件改动、执行的命令、Web/MCP 调用、审批与失败都记成 receipts，`/undo` 一步退回——把不可见的自动化变成可审计的操作记录。

**仓库信息**
- 地址：https://github.com/codewhale-hq/Codewhale
- 类目：AI Agent ｜ 语言：Rust ｜ Stars：41.2k（41219）｜ 近期增量：周均 ≈927 ⭐（建库 311 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：官方网站 + 文档站（安装 / 供应商 / 收据 / 容器）+ 多语言 README（中 / 日 / 韩 / 西等）+ 每版 Release（v0.10.4，11-23）+ CI + crates.io / npm / winget 多渠道分发

**核心功能**
- **收据与回滚是一等功能**：`/receipts` 记录改动文件、命令、Web/MCP 调用、子 Agent、审批与失败；`/undo` 回退上一轮（含文件改动），`/restore` 把工作区回滚到更早的快照。
- **50+ 供应商自由切换**：Anthropic、OpenAI、DeepSeek、Google、Mistral、Moonshot、OpenRouter、xAI 与任意 OpenAI 兼容端点，也接 Ollama / vLLM / SGLang 本地模型；`/model auto` 按轮路由，`/turn inspect` 看延迟与花费。
- **子 Agent 编队**：sub-agents、Fleets 与 workflow 组合，把多轮任务拆开并行跑，主会话只收结果。
- **审批 + OS 级沙箱**：只读命令直接执行，改文件的 shell 命令必须批准（y 本次 / a 本会话同类 / n 拒绝），叠加操作系统级沙箱；Ask 模式下每条命令都问。
- **装法齐全**：校验和安装脚本、winget、npm、cargo、容器镜像，覆盖 macOS / Linux / Windows 的 x64 与 arm64，`codewhale update` 原地升级。

**技术栈**
Rust（单一静态二进制，TUI 交互）+ 校验收据与快照回滚；crates.io（codewhale-cli）/ npm（codewhale）/ winget 分发；README 附真实会话截图（本地 Ollama qwen3:4b 改文件→等审批→跑测试→报告结果）；MIT 协议。

**适用场景**
想要「能审计、能回滚」的终端编码 Agent 的开发者；需要按任务分配模型控成本（贵模型做规划、便宜模型跑执行）的团队；内网或本地模型环境下也要 coding agent 的场景。

**推荐理由**
- **把「可回滚」做成了产品级闭环**：同类工具大多只给 diff，它把 receipts + undo + restore 做成一等功能：出事能查、能退。对把 Agent 放进真实仓库的团队，这是最实际的一道保险。
- **供应商中立，不被单一模型绑死**：50+ 端点加本地运行时、再按轮路由，预算敏感或必须走内网的团队都能用同一套工作流，而不是换模型就换工具。

> **注意**：版本还在 0.10.x，命令与配置变化快，团队协作前先统一版本；50+ 供应商意味着配置面很大，新手上手成本不低；默认接 DeepSeek，换模型要自备 Key，成本与限流得自己盯；69 个 open issue，长尾体验问题仍在收敛；Agent 自动改文件请务必先提交或 stash，别依赖 undo 兜底。

> **一句话理解**：像请了个会写工作日志的装修队：每敲一锤都记在册子上（改了哪面墙、动了哪根管），不满意就照记录把那一轮恢复原样。

---

## 4. MR Office —— 在浏览器里直接改 Word / Excel / PPT 的开源编辑器

**一句话简介**：多数「在线 Office」改的是自家私有格式，导出时才转一遍，公式、样式、批注常走形。MR Office 开源的是它真在跑的编辑器：直接读写 docx / xlsx / pptx，AI 的改动落在文件的真实对象上，而且改前给你预览。

**仓库信息**
- 地址：https://github.com/XinaTian/MROffice
- 类目：应用项目 ｜ 语言：TypeScript ｜ Stars：4.5k（4466）｜ 近期增量：周均 ≈1,839 ⭐（建库 17 天，Search 补池）
- 协议：AGPL-3.0 ｜ 官网 / 文档：官网 mroffice.ai + 在线试用 + 桌面版下载 + GitHub Release（v0.1.9，11-26）+ npm SDK + MCP 接口 + 嵌入开发文档

**核心功能**
- **真文件，不是转格式**：文档、表格、演示、PDF、代码五类编辑器都在浏览器里跑，直接操作 Word / Excel / PowerPoint 真实格式，公式引擎与导出格式齐全，桌面版可离线。
- **AI 改的是文件里的对象**：选中或圈出内容说需求，它就地改段落、表格、单元格与公式、形状与幻灯片；改前预览、逐条可撤销；若文件在此期间被别人改过，提案自动作废，不覆盖你的内容。
- **可嵌入 + npm SDK**：提供嵌入模式与 npm SDK（localhost 1,000 会话/月、自有域名 100 会话/月起），适合把自己的产品直接变成「能编辑 Office 文件」的产品。
- **协同与 MCP**：实时协同编辑、分享链接；对外暴露 MCP 接口，让外部 Agent 直接调用编辑器能力，而不是把文档内容抽出来再塞回去。

**技术栈**
TypeScript + React 前端，编辑器全部在浏览器内运行，无需安装 Office；AGPL-3.0 开放编辑器源码；配套 npm SDK、MCP 接口与托管服务；版本 0.1.9（2026-11-26）。

**适用场景**
需要在自有系统里嵌入「打开并编辑 Word / Excel」能力的 SaaS 与内部平台；想摆脱桌面 Office 授权、又要保住文件格式兼容的团队；做 AI 文档助手、需要 AI 直接改真实文件而不是生成 Markdown 的产品。

**推荐理由**
- **格式兼容是硬门槛，它正面啃**：直接在真实 docx / xlsx / pptx 上编辑、自带公式引擎——这恰是「AI 办公」落地最容易翻车的一环，现在开源出来可以直接评估，而不是听厂商演示。
- **AI 交互的风险控制值得抄**：改前预览、文件冲突即作废、改动逐条可撤销，把「让 AI 改我的文件」的不安写进了交互设计，比事后道歉有用。

> **注意**：开源的是编辑器，AI 能力与托管服务属商业产品（个人/小团队有免费额度，重度使用 $29 / $149 每月），别指望完全免费自托管全栈；AGPL-3.0 有传染性，闭源产品嵌入前先确认授权路径；版本仅 0.1.x、建库 17 天，复杂宏、超大数据透视表这类边角未经长期验证；README 中与 ONLYOFFICE 的价格对比属厂商口径，采购前请自行核价。

> **一句话理解**：像把 Office 拆成乐高搬进浏览器：文件还是那个 .docx，但每个段落、单元格、公式都是能单独拿起来改的零件——AI 改的是一个零件，不是把整页重打一遍。

---

## 5. Handwired —— 把普通 JavaScript 编译成神经网络

**一句话简介**：一个反直觉的实验：不训练网络，而是把你的 if-else 和循环「翻译」成矩阵运算。结果是同一个程序，既能照原样精确跑，又能反向传播——于是「冻结的代码」与「可训练的模型」第一次能拼在一条计算图里。

**仓库信息**
- 地址：https://github.com/chenglou/handwired
- 类目：算法/模型 ｜ 语言：TypeScript ｜ Stars：2.2k（2173）｜ 近期增量：周均 ≈355 ⭐（建库 43 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：在线 Demo 站（chenglou.me/handwired）+ docs/ + src/ + template/；暂无正式 Release，clone 后 bun 直接跑

**核心功能**
- **控制流变成算术**：`a > 4 ? 10 : 12` 被改写成 `max(0, a-4) - max(0, a-5)` 这类 ReLU 组合：两条分支都算，由门控值选一个，整个程序只剩 matmul + relu。
- **不训练也精确**：权重是手写出来的而非学出来的，所以行为与原 JS 完全一致——不是近似拟合，可以逐位核对。
- **天然可微**：只有两种原语，整个程序可反向传播：既能解冻权重看它学成什么，也能把一段死代码接到 nanoGPT 上端到端训练。
- **跑在 WebGPU 上**：把 + / * / relu 收成大矩阵乘，JS 或 WebGPU 后端执行；官方 demo 用这招让单线程写法的 JS 拿到 GPU 级并行（JSON 搜索示例）。

**技术栈**
TypeScript（编译器 + 运行时），Bun 构建，JS / WebGPU 双后端；`bun install && bun start` 跑 demo；MIT 协议；暂无 npm 包与 Release。

**适用场景**
想弄明白「程序即网络」这件事的编译器 / ML 爱好者；需要把既有确定性逻辑与神经网络联合训练的研究；探索在 WebGPU 上以 matmul 统一表达通用计算的实验。

**推荐理由**
- **概念密度极高**：一个干净得可怕的观察（if-else 就是 ReLU 门控）打通了「程序」与「网络」两个世界，代码量小、demo 可点，是少见的「读完就能上手改」的项目。
- **打开了奇怪的组合空间**：冻结程序 + 可训练网络、单线程代码拿 GPU 并行——这些不是论文里的空想，仓库里就有能跑的样例。

> **注意**：研究性项目：无正式 Release、无 npm 包，需 clone 后用 bun 跑；`lab/` 是旧实验，可忽略，别当稳定 API；把真实业务代码编译成 matmul 后体积与算力都会膨胀，目前只适合小而逻辑密集的程序，不能替代正常编译；个人探索项目，长期维护无承诺，本期属「无 Release 但概念独特」的次优入选（已在附录说明）。

> **一句话理解**：像把一段「如果…就…否则…」的说明书改写成一组旋钮：每个判断变成一个 0/1 的开关，整本说明书变成一次巨大的乘法表——照着拧结果分毫不差，但你也可以微调某颗旋钮，看看它会变成什么样。

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

- 本期网络形态：GitHub 侧 HTTPS 正常（gh 授权额度 5,000/h 可用，curl + gh api 取数全程顺畅）；open.feishu.cn 的 curl 探测返回 000、证书仍被替换，飞书是否送达以发布脚本实测为准，失败则按规则跳过。
- Trending 日榜 16 条 / 周榜 15 条，可用新增为零：全部是往期已推送仓库的回潮（CLI-Anything、minimind、opensre、autoclip、Ghost-Downloader-3、plannotator、nod、chrome-devtools-mcp、ag-ui、astryx、sure、HermesEnabler、univer、open-code-review、firecrawl、nginx、openvino）或技能 / 插件合集。5 个入选全部来自 Search API 补池（created:>2026-06-01 stars:>2000、created:>2026-09-01、topic:llm-inference、topic:computer-vision、topic:inference、topic:developer-tools 等 9 组查询）。
- 增量口径：本期无 Trending 实测增量，五项的「周均 ≈」均为「累计 star ÷ 建库天数 × 7」估算，已在卡片逐条标注，不与 Trending 原始数字混用。
- 类目配置：应用 1 / 算法 2 / 工程 1 / Agent 1。算法类目本期有两个达标候选（Unlimited-OCR 与 handwired），故用满 2 个配额。
- handwired 属次优入选：无正式 Release、无 npm 包，按「有 CI / 测试 / 文档站 / 正式 release 者优先」的口径弱于其余四项；但其概念独特性突出、MIT 明确、2.2k star 与 ≈355 周均均过线，故保留并在卡片注意事项中写明。

**本期按规则排除的候选**

- 技能 / 插件合集，按口径排除：elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、cathrynlavery/diagram-design、mvanhorn/last30days-skill、google-labs-code/stitch-skills、mjmirza/app-store-compliance、kajisho5/ffmpeg-skill、tradermonty/claude-trading-skills、obsidianmd/obsidian-skills、sickn33/agentic-awesome-skills、awesome-dsh-plugin/awesome-dsh-plugin
- storytold 整族（photocraft / pdfcraft / filmcraft / wordcraft / lightcraft / craft-anything）—— 同账号批量同构发布，延续往期口径整簇排除
- License 缺失或 NOASSERTION，排除：toeverything/AFFiNE、lemomo-ai/lemo-opuscar、Zagitta/gpu-unlock、cdyforever/how-to-live-better、Ebony-Vinyl/dsh-our-free-model（免费令牌中转，另有 ToS 风险）
- 版权 / 平台灰区，排除：Marvisak/VIctory（GTA VI 重编译）、zortos293/Lichii 与 seedds/nxnative（Switch 模拟与移植）、BaaRai/ARTEX（自主渗透测试系统，本期不做推荐）
- 教程 / 书稿 / 资料聚合，排除：rohitg00/ai-engineering-from-scratch、fancyboi999/ai-engineering-from-scratch-zh、bojieli/ai-infra-book、eternity4719/HowToLiveBetter、usamahz/cpu-performance-engineering、openai/math、yihui-dev/awesome-opus5-5-videos
- 空壳或真实性存疑：anefzaoui/misterdownloadmanager（clean-room 同构话术、同类下载管理器已有成熟替代，本期让位）、milind-soni/OpenMausBot（718 open issue / 426MB）
- 合格但类目配额让位（列为备选，下期优先）：tt-a1i/archify（100.6k，周均 ≈3,119）、paperclipai/paperclip（117.4k，6,806 open issue）、cheaper-inference/OmniRoute（90.5k，「免费 token」营销话术待逐条核账）、RunanywhereAI/trnrt（AWS Trainium 推理引擎，周均 ≈428）、shirudo-dev/shirudo（eBPF 安全平台，周均 ≈367）、getagentseal/codeburn（周均 ≈368）

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-27 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
