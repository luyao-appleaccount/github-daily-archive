# 每日 GitHub 精选 · 2026-11-25（第 29 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [ersinkoc/phonebox](https://github.com/ersinkoc/phonebox) | 应用项目 | JavaScript / C# / Kotlin | 6.0k | 周均 ≈2,350 ⭐（建库 18 天） |
| 2 | [shy3130/tick-stock-panel](https://github.com/shy3130/tick-stock-panel) | 应用项目 | Python | 8.3k | 周均 ≈360 ⭐（建库 160 天） |
| 3 | [mizorewww/laya-mlx](https://github.com/mizorewww/laya-mlx) | 算法/模型 | Python | 7.1k | 周均 ≈740 ⭐（建库 67 天） |
| 4 | [erkamyaman/rust-anything](https://github.com/erkamyaman/rust-anything) | 工程实践 | Rust | 9.2k | 周均 ≈7,200 ⭐（建库 9 天） |
| 5 | [rocketride-org/rocketride-server](https://github.com/rocketride-org/rocketride-server) | AI Agent | Python / TypeScript / C++ | 20.0k | 周均 ≈490 ⭐（建库 287 天） |

---

## 1. PhoneBox —— 把旧安卓手机变成电脑的桌面控制面板

**一句话简介**：抽屉里那台旧安卓手机，摇身一变成了电脑的「第二块仪表屏」：CPU 温度、Claude 配额、OBS 快捷键全在上面，Agent 要权限时手机震一下，点个批准就继续干活。

**仓库信息**
- 地址：https://github.com/ersinkoc/phonebox
- 类目：应用项目 ｜ 语言：JavaScript / C# / Kotlin ｜ Stars：6.0k（6042）｜ 近期增量：周均 ≈2,350 ⭐（建库 18 天）
- 协议：MIT ｜ 官网 / 文档：在线 demo（浏览器直接体验）+ 20 语种 README + 官网文档 + v0.9.29 高频 Release（11-23）+ GitHub Actions 构建流水线

**核心功能**
- **旧手机秒变桌面面板**：浏览器可视化编辑器里搭面板：132 种组件、30 套模板、多页面 + 实时预览；多台手机各自布局，也可一部手机在多台电脑间切换配对。
- **AI 编码会话的驾驶舱**：实时显示 Claude Code / Codex / OpenCode 的配额、重置时间与用量预测，本地会话（含 WSL 内）与 GitHub review、CI 状态一并上屏。
- **手机上批准权限请求**：可选接入 Claude Code / Codex / OpenCode 的权限提示，Allow / Deny 直接在手机上点——人离开电脑，Agent 也不会卡在等待确认上。
- **触控宏与自动化联动**：应用/URL 快捷方式、按键组合与宏，OBS、媒体、应用音频控制；Webhook 数值通知、Home Assistant 控件与联动规则，按电脑活动自动触发。

**技术栈**
安卓 App（Android 5+）+ 桌面 Agent（.NET 10，覆盖 Windows/Linux/macOS）；USB 数据线或 Wi-Fi 配对，无需 root、无账号、无云服务；MIT 协议。

**适用场景**
把闲置旧安卓手机改造成系统监控 / AI 编码仪表盘；远程盯 Agent 会话并随手批准权限请求的 AI 编码重度用户；需要 OBS 与媒体触控面板的主播；Home Assistant 玩家。

**推荐理由**
- **废物利用 + 高频刚需的组合拳**：旧手机零成本再利用，而「盯 AI 编码会话 + 远程批权限」是当下真实的新痛点；18 天 6k star、v0.9.x 一天多更，社区热度直接印证。
- **无云、无 root 的克制设计**：USB/Wi-Fi 直连本机 Agent，数据不出局域网；20 语种 README、在线 demo、CI 一应俱全，完成度远超一般个人项目。

> **注意**：桌面 Agent 需常驻运行；Wi-Fi 配对走本机网络，跨网段要靠 Tailscale 等自组网；AI 会话信息依赖读取本机 CLI 的日志与配置，CLI 大版本更新可能需跟版适配；深度功能集中在开发者场景，普通办公用户收益有限；Android 5/6 老机型体验未充分保障。

> **一句话理解**：像给电脑配了块二手「流媒体小键盘」：系统状态、AI 配额、直播快捷键全排布在旧手机屏幕上，编码 Agent 弹权限请求时手机震一下，点个 Allow 就接着跑。

---

## 2. Tick Stock Panel —— 自托管零运维的 A 股量化研究工作台

**一句话简介**：同花顺之外难得的功能完整开源替代：行情进来、策略写好、回测跑完，净值曲线和回撤直接摆在看板上——AI 只帮你取数写分析，不替你拍板买什么。

**仓库信息**
- 地址：https://github.com/shy3130/tick-stock-panel
- 类目：应用项目 ｜ 语言：Python ｜ Stars：8.3k（8251）｜ 近期增量：周均 ≈360 ⭐（建库 160 天）
- 协议：MIT ｜ 官网 / 文档：官网 tsp.shy313.com + 官方在线演示 + Docker CI 与前后端测试双流水线 + v0.4.1 正式 Release + AI 接入 / 扩展导入分层文档

**核心功能**
- **策略 + 监控 + 回测一体**：首页看板呈现指数、板块热度与盘中监控；策略页写策略，回测页直接给出净值曲线、回撤与成交记录，研究闭环不走第三方平台。
- **概念板块轮动分析**：盘中轮动曲线、切换强度、涨跌排行等板块维度视图，A 股特有的概念炒作风向一屏看清。
- **核心能力全部开放成接口**：取数、指标计算、回测等能力以 API 暴露，可自由接第三方数据源与个性化扩展；DuckDB + Polars 本地高性能计算。
- **LLM 驱动的研究辅助**：AI 助手用于取数、分析与策略研究，自然语言定制策略与个股复盘；官方明确范围不含 AI 荐股与涨停预测。

**技术栈**
Python 3.11+（FastAPI）后端 + React 18 前端 + DuckDB/Polars 分析引擎；Docker 自托管部署；行情数据经插件接入第三方来源；MIT 协议。

**适用场景**
想自建而非租用量化平台的 A 股研究者；要求策略与回测数据留在本地的隐私敏感用户；想用 LLM 辅助写策略、又不想被「荐股 AI」收割的个人投资者。

**推荐理由**
- **把「量化研究工作台」真正开源化了**：回测、监控、板块分析、扩展接口齐备且明确走研究路线而非荐股营销；160 天 8.3k star 稳步爬升，非流量冲榜型项目。
- **工程质量在线**：前后端双 CI、Docker CI、正式 Release、官网与在线演示一应俱全；自托管零运维的定位把部署门槛压到了个人可承受的范围。

> **注意**：定位研究工作台而非实盘交易系统，无自动下单；行情数据需自行接入第三方源，数据质量决定分析上限；AI 功能消耗模型 token；涉及投资研究，结论仅供个人参考，不构成投资建议；open issue 较多（84 个），使用前先查已知问题。

> **一句话理解**：像在自己电脑上装了套「私人研究所」：数据、策略、回测、板块风向全在自己手里，AI 是那个帮你跑腿取数写初稿的研究员——签字画押买不买，仍然是你。

---

## 3. Laya-MLX —— 类型化决策模型的苹果芯原生推理引擎

**一句话简介**：大模型回答一个选择题要生成一堆 token 再解析 JSON；它一次前向直接吐出每个选项的概率——给 Agent 流程里成千上万次的小判断省下 99% 的延迟与费用。

**仓库信息**
- 地址：https://github.com/mizorewww/laya-mlx
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：7.1k（7123）｜ 近期增量：周均 ≈740 ⭐（建库 67 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：PyPI 包（laya-mlx）+ HuggingFace 权重（含模型卡与校验哈希）+ BENCHMARKS 基准 + USAGE 用法参考 + 中英双语 README + v0.8.1 Release

**核心功能**
- **一次前向出决策**：choice（选项）、score（量表）、noul（是非）三类问题，输出带校准概率与置信度；不生成 token、无需解析 JSON，M3 Max 上 13.4ms 出结果。
- **MLX 原生，苹果芯全本地**：基于 Apple MLX，无 PyTorch / Transformers 依赖，pip install 即用；三个官方预转换 FP16 权重（英文 421M / 多语 322M 等）开箱即下。
- **工程化周边齐全**：语言路由自动选检查点、批量预测共享前向、置信度门控标记低置信答案、大选项集的 embedding 短名单与锦标赛模式。
- **开箱即用的集成面**：CLI、HTTP 服务、MCP server 三种形态，另有 LangChain / LlamaIndex / CrewAI / Agno extras；laya-mlx convert 可导出独立 MLX 权重。

**技术栈**
Python 3.11+，Apple MLX 原生运行时；权重托管 HuggingFace（附校验和）；Apache-2.0 协议；仅支持 Apple Silicon + macOS 14+。

**适用场景**
Agent 工作流里高频低延迟的小判断（意图路由、工单分派、内容打分、真假判断）；给自动化流程加廉价分类器；苹果芯本地部署、不想为分类调用云端 LLM 的场景。

**推荐理由**
- **「不生成 token 的模型」找到了最佳载体**：Laya 的价值在极低延迟的类型化决策，而 MLX 是 Apple Silicon 上最贴近硬件的推理路径——模型与运行时这次真正咬合上了。
- **基准与权重治理一丝不苟**：每个公开检查点附模型卡、验证结果、来源与校验哈希，BENCHMARKS 公开可复现；7.1k star 是社区对「可信小模型」的投票。

> **注意**：仅支持 Apple Silicon + macOS 14+，x86 与 Linux/Windows 用户用不了；512~1024 上下文决定只适合短输入判断；置信度不保证新任务准确率，关键场景需人工抽检；上游 Laya 系生态有多个同名仓库，认准 mizorewww/laya-mlx 与 HuggingFace aac6fef 权重。

> **一句话理解**：别的模型像请了个会写作文的顾问回答「这单派给谁」；它是专用裁判——不写字，直接把「账务 92%、技术 6%、销售 2%」拍在桌上，13 毫秒完事。

---

## 4. rust-anything —— 用「录制-重放比对」把应用逐步重写成 Rust

**一句话简介**：「用 Rust 重写」喊了十年，卡点从来不是翻译代码，而是没人敢保证行为没变——它把保证做成了流程：录下来、逐段重写、重放比对，逐字节一致才放行。

**仓库信息**
- 地址：https://github.com/erkamyaman/rust-anything
- 类目：工程实践 ｜ 语言：Rust ｜ Stars：9.2k（9248）｜ 近期增量：周均 ≈7,200 ⭐（建库 9 天）
- 协议：MIT ｜ 官网 / 文档：官方文档站 rust-anything.com + how-it-works / real-world / FAQ 分层文档 + crates.io 与 npm 双渠道 + MCP Registry 收录 + CodeRabbit 全量 PR 审查

**核心功能**
- **Record：先把原程序行为录下来**：用生成的边界用例、语义陷阱和你自己的输入跑原程序，把每个输入的返回值与异常全部存档，成为后续重写的「验收标准」。
- **Bridge + Port：逐段移植不破坏调用方**：自动生成 Rust crate 与包装层，调用方 API 保持不变；你或编码 Agent 一段一段写 Rust，原程序全程不被触碰。
- **Diff + Gate：重放比对，逐字节一致才放行**：每段移植完重放全部录制用例，全对且通过 gate 才算过；混不进 Rust 的部分走 FFI/回退并显式标注，绝不静默换行为。
- **App Lift：整应用毕业**：全部录制用例零回退通过后，一键把整个应用变成纯 Rust；实测案例：Prettier 快 19 倍、json-server 内存 74MB → 3.5MB。

**技术栈**
Rust 编写；基于 napi-rs / PyO3 / wasm-bindgen 打通 TypeScript、Python、C、Go、Ruby、Java、Kotlin 与 Rust 互操作；crates.io + npm 分发；MIT 协议。

**适用场景**
性能热点明显的 TS/Python 服务想换 Rust 又怕改坏行为；把关键库逐函数迁移到 Rust 的团队；给 AI 编码 Agent 配「重写验证脚手架」；追求小体积单二进制分发的工具作者。

**推荐理由**
- **把重写从「勇气活」变成「流程活」**：录制-重放-比对的验收机制让每次移植都有客观通过标准，正好补上 AI 编码时代「改得快、验得慢」的最大短板。
- **战果可核验，不是营销数字**：Prettier 59 个真实文件逐字节对比全程公开、17,224 条录制运行可追溯；9 天 9.2k star 建立在 demo 可复现之上。

> **注意**：只能捕获录制覆盖到的行为，录制没跑到的不确定性仍需自担（官方明示 What it can't catch）；依赖原程序可被程序化驱动，GUI 应用不适用；工具管验证不管生成质量，Rust 侧仍需真功夫；项目仅 9 天大，长期维护与大型项目案例尚待观察。

> **一句话理解**：像给搬家装了「逐箱对比验收」：旧房子里每件家具拍照建档，新家摆完一件对一张，摆错当场打回——全对才允许拆旧房，谁也别想蒙混过关。

---

## 5. RocketRide —— 开源 AI 管线开发环境：C++ 引擎跑可视化编排

**一句话简介**：LangChain 管编排、Dify 管画布，但底下跑的还是 Python 解释器——它把执行层换成了多线程 C++ 引擎，AI 管线第一次有了「引擎盖下面的性能」。

**仓库信息**
- 地址：https://github.com/rocketride-org/rocketride-server
- 类目：AI Agent ｜ 语言：Python / TypeScript / C++ ｜ Stars：20.0k（19988）｜ 近期增量：周均 ≈490 ⭐（建库 287 天）
- 协议：MIT ｜ 官网 / 文档：docs.rocketride.org 文档站 + VS Code Marketplace / Open VSX 双渠道插件 + PyPI/npm SDK + MCP Server + 官网 rocketride.org + CI 流水线

**核心功能**
- **IDE 里的可视化管线画布**：VS Code 插件里拖拽连线搭管线，实时观测 token 用量、LLM 调用与延迟；管线是可版本控制的便携 JSON，可分享、可在任何环境复跑。
- **100+ 节点、C++ 运行时**：15+ LLM 供应商、9 种向量库、OCR、NER、PII 匿名化、分块策略等节点全内置，均可 Python 扩展；执行层是原生多线程 C++ 引擎。
- **SDK 三件套 + MCP**：Python / TypeScript SDK 几行代码把管线嵌进应用；管线可暴露为 MCP 工具供 Claude / Cursor 等调用，自动识别你的编码 Agent。
- **自带依赖管理，三种部署形态**：Python 环境、C++ 工具链、Java/Tika 全部自动托管；本地零注册即跑，也可 Docker 自托管或用官方云，无厂商锁定。

**技术栈**
C++ 高吞吐运行时 + Python/TypeScript SDK + VS Code 插件；管线定义为便携 JSON；全量 MIT 开源（无企业版付费墙），文档站与 CI 齐备。

**适用场景**
RAG / 文档处理 / 多模态检索等数据密集型 AI 管线的生产化部署；给 Agent 应用做可观测的底层管线层；想在 VS Code 里一体化完成「搭-调-部署」的团队；需自托管、无厂商锁定的企业。

**推荐理由**
- **定位在 harness 之下，避开了内卷**：编码 Agent 满天飞的当下，它做的是「Agent 底下那层」：数据管线 + 运行时 + 观测，C++ 引擎是同类可视化工具里少见的差异化底牌。
- **开源诚意可验证**：引擎全量 MIT、文档站/SDK/MCP/插件市场一次配齐、CI 全绿；287 天 20k star 稳定爬升，596 个 open issue 也侧面说明真实使用量大。

> **注意**：open issue 偏高（596 个），复杂管线踩坑时要做好翻 issue 的准备；可视化画布对数百节点级超大规模管线的可维护性有待验证；云版为托管服务，敏感数据请走自托管路径；prerelease 迭代节奏快，生产环境建议锁版本。

> **一句话理解**：别的工具给你一张「AI 流程设计图纸」，它是连图纸带工厂一起给你：画布上拖出管线，底下 C++ 流水线真开动机器，token 花了多少、哪步慢了，仪表盘实时看得见。

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

- 本期网络形态：GitHub HTTPS 恢复正常（真 Sectigo 证书链），bash 侧 curl + gh api（授权额度 5,000/h）取数全程顺畅；open.feishu.cn openssl 实测 issuer=SANGFOR-AC（中间证书替换），飞书通道以发布脚本实测为准。
- Trending 日榜 16 条 / 周榜 13 条，可用新增为零：全部为已推送仓库回潮或技能/插件合集，本期 5 个入选全部来自 Search API 补池（created:>2026-11-05、topic:machine-learning、topic:agent-framework、topic:rust tools 等多组查询）。
- 增量口径：全部按「累计 star ÷ 建库天数 × 7」估算周均并标注，五个入选仓库周均估算均 ≥360，无需破例。
- 观察期转正说明：erkamyaman/rust-anything（上期「同构话术新作」观察期）本期转正——已形成真实交付（Prettier 移植逐字节对比公开可复现、v4.1.0 高频 Release、官方文档站、crates.io/npm/MCP 三渠道分发），与已推送的 morluto/rea（逆向理解）定位不同；mizorewww/laya-mlx 为已推送 NandhaKishorM/laya 的独立 MLX 运行时（不同维护者、不同交付物：PyPI 包 + 预转换权重），按独立仓库收录。

**本期按规则排除的候选**

- elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、cathrynlavery/diagram-design、google-labs-code/stitch-skills、mvanhorn/last30days-skill、kajisho5/ffmpeg-skill、tradermonty/claude-trading-skills、janestreet/agent_skills、heydamir/unslop、wheresryan22/anatomy —— 技能/插件合集，按口径排除
- Marvisak/VIctory（GTA VI 重编译）、zortos293/Lichii（Switch 2 模拟器）、xcl-dev/xcl（Xbox 兼容层）、jhaizhou-ops/S2Arm、tangerineturtle1/NX2navi、huami1314/GestaltX —— 游戏重编译 / 模拟器 / MobileGestalt 篡改等版权与灰区，排除
- JenkinWoo/sheeridVerify —— 学生资格校验绕过，合规存疑；Hut-hzf/ung220z-tool —— 光猫凭据提取工具，滥用风险高；均排除
- Minireel/HGhub、simplexai-labs/linger、qwdwqfwq/topconf-paper-figure-gallery、TrenTorch/TrenTorch、datawhalechina/leedl-tutorial —— NOASSERTION 或资源聚合 / 教程类，排除
- storytold/craft-anything 等 storytold 族 —— 同账号批量同构发布，延续整族排除；ccch1mneyyy/dsh-Go —— DSH 生态重复；anefzaoui/misterdownloadmanager —— 观察期延续
- 666ghj/BettaFish、RightNow-AI/openfang、NirDiamant/agents-towards-production —— 最近提交超 30 天活性线，排除
- deepseek-ai/chat-demo —— 仓库仅 279KB、无描述无 topics，信息密度不足未入选；XinaTian/MROffice —— 合格（AGPL-3.0，周均 ≈1,380）但应用类目配额已满，让位备选
- eigent-ai/eigent（周均 ≈230）、aden-hive/hive（≈246）、strands-agents/harness-sdk（≈133）、NVlabs/Sana（≈55）—— 增量估算不达标，排除
- firecrawl/firecrawl、nginx/nginx、openvinotoolkit/openvino、alibaba/open-code-review、Tracer-Cloud/opensre、backnotprop/plannotator、meta/astryx、we-promise/sure 等 —— 已推送或知名回潮，避让

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-25 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
