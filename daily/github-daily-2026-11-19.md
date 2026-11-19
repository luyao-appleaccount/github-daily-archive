# 每日 GitHub 精选 · 2026-11-19（第 25 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [l0ng-ai/openidea](https://github.com/l0ng-ai/openidea) | 应用项目 | TypeScript / Rust | 9.4k | 周均 ≈2,270 ⭐（建库 29 天） |
| 2 | [qingjian-team/qingjian](https://github.com/qingjian-team/qingjian) | 应用项目 | Rust | 7.9k | 周均 ≈756 ⭐（建库 73 天） |
| 3 | [FlashML-org/FreeVideo](https://github.com/FlashML-org/FreeVideo) | 算法/模型 | Python | 3.3k | 周均 ≈344 ⭐（建库 67 天） |
| 4 | [AhmadHassan-BTed/OpenHeart](https://github.com/AhmadHassan-BTed/OpenHeart) | 工程实践 | Rust | 5.9k | 周均 ≈405 ⭐（建库 103 天） |
| 5 | [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent) | AI Agent | Python | 11.4k | 周均 ≈497 ⭐（建库 161 天） |

---

## 1. OpenIDEA —— 把 IntelliJ 的使用习惯搬进一个 Rust 原生 IDE

**一句话简介**：每次打开 IDEA 都要等十几秒、吃两三个 G 内存的人，会懂这个项目在赌什么：键位还是那套键位，只是底下换成 Rust 和 WebAssembly 插件。

**仓库信息**
- 地址：https://github.com/l0ng-ai/openidea
- 类目：应用项目 ｜ 语言：TypeScript / Rust ｜ Stars：9.4k（9398）｜ 近期增量：周均 ≈2,270 ⭐（建库 29 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：独立文档站 openidea.sh（含插件开发与贡献者指南）+ GitHub Releases 每日构建 + 自带 perf/compare 基准脚本 + 多语言 README（含简体中文）+ Discord / 微信群

**核心功能**
- **照抄 IDEA 的操作习惯，不是照抄界面**：快捷键映射、工具窗布局、Search Everywhere 这些「肌肉记忆」原样保留，切过来不用重新学一套 IDE；官方也明确声明与 JetBrains 无关联。
- **Rust 核心 + Tauri 外壳的原生栈**：编辑器、代码洞察、调试器、Git、终端、数据库客户端、HTTP 客户端都在一个原生窗口里，60+ 语言走 LSP，启动与内存开销按 README 的基准表比 IDEA 低一个量级。
- **插件跑在 WebAssembly 沙箱里**：插件以 WASM 组件形式加载，可加动作、补全、Quick Fix、工具窗、自定义编辑器与主题；主题、图标包、语言支持这类插件甚至不用写代码。
- **版本迭代密度罕见**：近一个月 release 号从 v0.1.x 一路推到 v0.1.48（11-18 仍在发版），main 分支每天有提交，说明还处在高速追赶功能缺口的阶段。

**技术栈**
Rust 核心 + Tauri 桌面外壳，前端 TypeScript；语言能力通过 LSP 接入，调试走 DAP；插件体系基于 WebAssembly Component Model；Apache-2.0 协议。

**适用场景**
常年用 IDEA 但被 JVM 内存和启动时间折磨的 Java/Kotlin 开发者；需要同时开几个大项目、机器内存又不够的笔记本用户；想研究「原生 IDE 怎么写」的客户端/编辑器开发者。

**推荐理由**
- **性能差距不是修辞，是给了可复跑的基准**：README 直接把自己和 IDEA 2026.2.3 摆在同一张表上（打开项目 0.9s vs 3.1s、就绪 1.1s vs 13.2s、内存 169MB vs 2011MB），还附带 perf/compare 让你在自己机器上复现——愿意被验证的项目，通常不会太差。
- **把「可扩展」做在最难的地方**：多数新 IDE 死在插件生态上：要么没有，要么必须重编译核心。用 WASM 沙箱做插件边界，既隔离又跨语言，这条路子对后来者是可借鉴的设计。

> **注意**：仍是 v0.1.x，插件 API 明确标注 preview，随时可能破坏性变更；核心代码是 Rust 但仓库语言统计显示 TypeScript（前端占比大），别被语言标签误导；Python 的语义分析深度目前不如 IDEA，README 自己也承认「ready 不等于做了同样的活」；商业 IDE 的调试器/重构能力仍有明显差距，别急着卸载 IDEA。

> **一句话理解**：相当于把一间用惯了的办公室原样搬进新楼：桌椅摆放、抽屉位置、灯开关高度都没变，但楼体从混凝土换成了钢结构，进门快、占地方小。

---

## 2. 青简 —— 打字的时候，候选词旁边多一行外语译词

**一句话简介**：学外语最难的从来不是背单词，是没机会用。青简把这件事塞进了你每天都要做的事——打字——里：选「架构」的时候，顺手看见 architecture。

**仓库信息**
- 地址：https://github.com/qingjian-team/qingjian
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：7.9k（7886）｜ 近期增量：周均 ≈756 ⭐（建库 73 天）
- 协议：GPL-3.0-or-later ｜ 官网 / 文档：独立文档站 qingjian.app/docs（安装/输入/学习/隐私/平台分册）+ GitHub Actions CI + 正式 release（v0.3.4，11-18）+ 7 种语言 README + QQ 内测群

**核心功能**
- **候选词旁的一条译词**：每次只显示一种学习语言的译词（英/日/西/越/德，可关），位置在辅助行，不抢主候选；输入法顺手变成生词本，统计页还能看今天、近 7 天与累计输入量。
- **该有的输入能力不缺**：整句输入、简拼、拼写纠错、双拼、五笔都支持，本地整句模型会在停顿后重排句子候选——它不是个「只会秀译词」的玩具。
- **隐私边界写得很明确**：拼音转换、词库查询、本地模型、输入习惯学习全在本机；输入日志与统计分开存，日志可关可清空；云联想默认关闭，开启后请求直连你自己填的 AI 服务商，不经过官方服务器。
- **Rust 写全平台，还带完整文档站**：macOS 13+/Windows 10/11 有安装包，Linux 走 Fcitx4/Fcitx5 源码安装，Android 有 arm64 预览版；文档站按平台、输入、学习、隐私分册，CI 与发版节奏稳定。

**技术栈**
Rust 实现输入法核心与本地语言模型推理；macOS/Windows 原生前端，Linux 走 Fcitx 插件，Android 为独立 App；GPL-3.0-or-later，随包数据另附来源与许可清单。

**适用场景**
每天大量中文输入、同时想维持外语手感的人；需要离线可用、不愿把输入内容交给云端的隐私敏感用户；想读一份「Rust 写输入法」完整工程范例的开发者。

**推荐理由**
- **把一个老品类做出了新动机**：输入法十几年没有真正的产品创新，青简没有去卷词库大小或皮肤，而是找到了「日常输入」和「语言学习」的交点——这类需求真实存在，却一直没人认真做。
- **工程完成度超出「个人项目」预期**：多平台安装包、Fcitx 适配、本地模型、文档站、CI、7 语 README，加上把隐私边界一条条写清楚，这套配置在同类开源输入法里属于少数派。

> **注意**：桌面版仍标注测试阶段，Linux 需手动启动后台服务、只提供源码安装，Android 是功能更少的预览版；GPL-3.0 传染性较强，二次分发/商用前务必读协议；项目名与 logo 不在代码授权范围内；官方强调只从官网、GitHub Releases 与更新日志里的网盘链接下载，其他地方的同名包不要装。

> **一句话理解**：像在键盘上贴了一层透明便签：你照常打字，便签只是安静地在旁边提醒「这个词英文这么说」，看久了自然就记住了。

---

## 3. FreeVideo —— 8GB 显存也能在本地跑 MiniMax H3 出视频

**一句话简介**：视频生成的门槛从来不是模型，是显存。FreeVideo 干的事很朴素：把权重、精度、内核、显存/内存/磁盘之间的搬运调度写好，让 8GB 的卡也能出一段能看的片子。

**仓库信息**
- 地址：https://github.com/FlashML-org/FreeVideo
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：3.3k（3292）｜ 近期增量：周均 ≈344 ⭐（建库 67 天）
- 协议：Apache-2.0（代码）/ MiniMax H3 社区协议（权重） ｜ 官网 / 文档：独立社区站 freevideo-community.pages.dev（作品画廊 + 四档画质对比）+ docs/ 下执行规划、LoRA、各平台指南 + 正式 release（v0.6.3，11-18）+ ComfyUI 模板

**核心功能**
- **硬件自适应执行**：启动时探测显卡型号与可用注意力内核，GeForce / RTX 30 系走 int8，工作站与数据中心卡走 FP8；同一份模型在不同卡上自动换最优权重格式，不用手工挑参数。
- **低显存推理的一整套工程**：权重流式加载、异步预取、分块计算三件套把峰值显存压下来，README 给的下限是 8GB 显存 + 16GB 内存；RTX 3090 上 int8 让 5 秒视频快约 2.3 倍。
- **ComfyUI 里的一块创作台**：以自定义节点形式接入 ComfyUI，提供专用工作区：两段式采样、批量生成、历史记录；要细调就切回节点视图加 LoRA、改工作流，生成结果可导出带参数与 GPU 信息的分享图。
- **一键部署 + 多模态输入**：Windows/macOS/Linux 各有启动器，自动装环境、复用已有模型目录、支持离线安装；输入支持文本、首尾帧以及图片/视频/音频参考。

**技术栈**
Python；基于 OpenVDN 的 8 步 VDN-H3（Video DeltaNet 混合注意力）模型；推理侧对 int8/FP8 量化、SageAttention、权重流式与分块计算做了封装；以 ComfyUI 自定义节点形式交付，桌面启动器用 Qt for Python。

**适用场景**
只有一张 8-16GB 消费级显卡、想本地跑视频生成的内容创作者；已有 ComfyUI 工作流、想加视频能力的人；研究「低显存推理调度」的实现者（execution-planning 文档值得读）。

**推荐理由**
- **补的是推理侧最脏最累的那部分**：模型权重是别人开源的，FreeVideo 的价值在于把「显存不够怎么办」拆成可执行的调度：权重放哪、什么时候预取、哪层用 int8——这类工程细节很少被完整开源。
- **发版节奏与硬件覆盖都很实在**：两个月从 v0.1.2 推到 v0.6.3，Windows/macOS/Linux 全平台启动器、代码签名、离线安装包、四档画质与社区画廊，是「给普通人用」而不是「给论文复现用」的完成度。

> **注意**：注意许可证是两截：代码 Apache-2.0，模型权重走 MiniMax H3 社区许可，含地域与用途限制，商用/分发前必须单独确认；703 个 open issue 说明问题不少，macOS 为 Apple silicon 预览版且未公证，首次打开需手动放行；社区镜像（夸克网盘）与第三方整合包存在被投毒风险，优先从 Releases 下载并核对 SHA-256。

> **一句话理解**：像给一台小排量车装上智能变速箱：发动机（模型）没换，但换挡时机、油电分配全按你实际的路况算，于是原本跑不动的路也能跑完。

---

## 4. OpenHeart —— 用 Rust 把 Java 源码拆成图，顺手画 19 种 UML

**一句话简介**：大多数「代码可视化」工具只是画个框连线；OpenHeart 想干的是编译器那套活：把源码压成可查询的图，再从图里长出图来。

**仓库信息**
- 地址：https://github.com/AhmadHassan-BTed/OpenHeart
- 类目：工程实践 ｜ 语言：Rust ｜ Stars：5.9k（5918）｜ 近期增量：周均 ≈405 ⭐（建库 103 天）
- 协议：MIT ｜ 官网 / 文档：GitHub Pages 在线 Diagram Studio + docs/status.md（能力矩阵与主张台账）+ GitHub Actions CI + 19 类图的可视化清单

**核心功能**
- **十阶段流水线，每段落成独立产物**：token 锚点（.tca）→ BP 编码 AST（.bpa）→ 符号表与类型层次（.sta）→ CSR 形式 CFG 与支配树（.cfa）→ SSA（.ssa）→ 调用图（.cga）→ 溯源索引（.tra）→ ROBDD 路径摘要（.psa），每段都能单独取用。
- **全程可溯源**：所有结构都锚在单调递增的 32 位 token_id 上，任意图节点能 O(1) 反查回源码位置，这对做审查、做 diff 分析的工具很关键。
- **19 种图的导出器**：结构类 7 种（类图/包图/组件图…）、行为类 7 种（时序/状态机/活动/用例…）、编译器 IR 类 5 种（CFG/DFG/CDG/调用图/ROBDD），统一导出 PlantUML、Mermaid 与 JSON。
- **浏览器里的 Diagram Studio**：GitHub Pages 上有在线画布，贴仓库地址就能出图（走前端启发式抽取）；要完整分析则本地跑 openheart server 用原生引擎。

**技术栈**
Rust 1.88+，tree-sitter 做 Java 解析；BP（平衡括号）编码 AST + rank/select 索引、CSR 控制流图、SSA、CHA 分派、ROBDD 路径摘要；导出 PlantUML / Mermaid / JSON；前端为声明式 manifest 驱动的 Web Studio。

**适用场景**
要给遗留 Java 系统做架构梳理、却不想手工画图的团队；研究静态分析/编译器 IR 的工程师（十段流水线的产物格式可以直接借）；教学场景里演示 CFG、SSA、支配树是怎么一步步算出来的。

**推荐理由**
- **把「做研究」和「做产品」的边界划得很诚实**：docs/status.md 里有一张主张台账，逐条记录已撤回的旧宣传（「128× 内存压缩」「六语言 F1=1.0000」「zero-copy 内存映射」等），并标明每个模块的实测状态。这种自我审计在热榜项目里极罕见。
- **流水线设计本身有参考价值**：单 token 锚点贯通全流程、每阶段独立二进制产物、图查询走 rank/select——这是一套可以直接搬到别的语言上的骨架，比成品更有用的是骨架。

> **注意**：README 自己写明是 experimental 研究软件：目前只支持 Java（连 Kotlin 都没有），精度无独立基准，19 种图里多数仍是模板或「未从程序推导」，CFG/DFG/调用图等导出器还没读对应产物——把它当参考架构看，别当生产工具；网页 Studio 用的是 JS 启发式抽取，不等于原生引擎结果；无正式 release。

> **一句话理解**：像给一栋大楼做结构测绘：不只画出外观（类图），还把承重墙、管线走向（CFG）、水电从哪进哪出（数据流）一层层标出来——只不过目前只测绘完了几层，还有几层画的是示意图。

---

## 5. Omnigent —— 一层壳套住你所有的编码 Agent

**一句话简介**：今天的现实是：你手上同时有 Claude Code、Codex、Cursor、Gemini CLI，各自一套登录、一套权限、一套会话。Omnigent 想当那个「总台」。

**仓库信息**
- 地址：https://github.com/omnigent-ai/omnigent
- 类目：AI Agent ｜ 语言：Python ｜ Stars：11.4k（11426）｜ 近期增量：周均 ≈497 ⭐（建库 161 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 omnigent.ai + docs/（策略、沙箱、harness 指南、遥测）+ PyPI/Homebrew 分发 + 正式 release（v0.22.0）+ tests/harness_bench 能力矩阵测试台

**核心功能**
- **一个入口，十几个 harness**：omnigent claude / codex / cursor / opencode / goose / copilot / qwen / kimi / devin / pi 等命令直接起对应 Agent，也能用 YAML 写自己的 Agent；同一会话里可以让一个 Agent 审查另一个的产出。
- **会话跟着人走**：终端里起头、浏览器里接着聊、手机上继续看，消息、子 Agent、终端、文件保持同步；队友可以加入同一会话围观、共驾或 fork 出去自己接着干。
- **策略引擎管住「能干什么」**：策略分三层（服务器级 / Agent 级 / 会话级，会话规则优先），可拦截 shell 执行、文件写入、工具调用次数，甚至直接设美元预算上限（cost_budget）；可以在对话里让 Agent 自己加策略。
- **沙箱与自托管都能落**：内置对接 Modal、Daytona、E2B、Kubernetes、microsandbox 等十余种沙箱执行环境；服务端可自托管，配 S3/hindsight 做存储与记忆。

**技术栈**
Python 3.12+；PyPI / Homebrew / 安装脚本分发，附 macOS 桌面 App；Agent 侧通过 ACP（Agent Client Protocol）、各厂商 SDK 与 CLI 适配；策略用 YAML + Python 函数式 handler；Apache-2.0。

**适用场景**
同时用两三个编码 Agent、需要统一权限与成本边界的团队；想让远程/手机端接管本地 Agent 会话的人；企业内要自托管、要能给 Agent 加审批与预算上限的场景。

**推荐理由**
- **解决的是「Agent 太多」这个真问题**：单个 Agent 不缺，缺的是把它们放进一个可控边界里的方法：统一会话、统一模型来源、统一策略、统一沙箱——这层「壳」比再做一个 Agent 更有长期价值。
- **治理能力不是 PPT**：策略分三级并落到具体内置 handler（shell 审批、工具调用上限、美元预算），沙箱有十余个真实后端，还提供 harness 能力矩阵测试台，是可运行的工程而不是概念图。

> **注意**：alpha 状态，接口会变；仓库 2400+ open issue，说明热度与维护压力同时很高；默认开启匿名遥测（需按文档主动关）；安装脚本会顺带装 Databricks CLI，企业环境需评估；体量很大（数百 MB 级），首次上手成本不低，建议先只看 policies 与 sandbox 两节判断是否匹配。

> **一句话理解**：像给家里所有牌子的智能音箱配一个总控面板：音箱还是各家的，但「谁能听什么指令、每月花多少钱、在哪个房间生效」由你在面板上统一说了算。

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

- 类目覆盖：应用项目 2（openidea、qingjian）/ 算法模型 1（FreeVideo）/ 工程实践 1（OpenHeart）/ AI Agent 1（omnigent），满足每期 ≥2 类目、单类目 ≤2。
- 本期 Trending 几乎全是「技能/插件合集」与知名项目回潮（nvm、uv、svelte、jquery、n8n、appwrite、solid、openvinotoolkit/openvino），可用新增量极少，5 个仓库全部由 GitHub Search API 补池（created:> / topic: 多组查询），增量一律按「总 star ÷ 建库天数 × 7」估算并标注「周均 ≈」。
- OpenHeart 虽无正式 release，但有 CI、docs 状态台账与 GitHub Pages 文档站，属「研究型工具」；其 README 主动撤回多项旧宣传，本报告按它自述的能力边界如实降级描述，未采用任何已撤回指标。
- FreeVideo 的代码与权重分属两套许可（Apache-2.0 / MiniMax H3 社区协议，含地域与用途限制），已在卡片「注意」里单列，避免读者误当纯 Apache 项目使用。
- horizon-rust/horizon（11.3k，Minecraft Java 版 Rust 重写，周均 ≈1,690，LGPL-3.0）、microsoft/agent-governance-toolkit（6.6k，周均 ≈176 不达门槛）、wquguru/cicada（2.4k，实时字幕，建库 18 天）本期因类目配额与门槛让位，列入下期优先。
- 飞书推送：本机 open.feishu.cn 仍被网络层 TLS 中间证书替换（SANGFOR），脚本按规则尝试后失败即跳过，未做任何降级校验。

**本期按规则排除的候选**

- cursor/plugins、mvanhorn/last30days-skill、obra/superpowers、anthropics/skills、google-labs-code/stitch-skills、tradermonty/claude-trading-skills——技能/插件合集，按既有口径排除
- punkpeye/awesome-mcp-servers——awesome 资源聚合列表，排除
- storytold/photocraft、pdfcraft、filmcraft、wordcraft、lightcraft、vectorcraft、designcraft、figcraft——同账号批量同构发布，整族排除
- Ebony-Vinyl/dsh-our-free-model（79.9k）——免费令牌中转，License 为 NOASSERTION，排除
- Gathin23/cleanyourtv（59.3k）、Zagitta/gpu-unlock（20.4k）、cdyforever/how-to-live-better（14.9k）——License 缺失或为 null，排除
- Oldcircle/geo-sleuth（7.2k）——以 Agent Skill 形式分发的单点能力包，同口径排除
- nvm-sh/nvm（+237 日）、astral-sh/uv（+258 日）、sveltejs/svelte（+692 日）、jquery/jquery、n8n-io/n8n、appwrite/appwrite、solidjs/solid——知名项目热榜回潮，非新增量场景，避让
- anefzaoui/misterdownloadmanager（13.1k，建库 21 天）——「clean-room 重写」同构话术，无 release 与测试信号，空壳风险高，排除

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-19 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
