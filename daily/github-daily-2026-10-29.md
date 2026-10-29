# 每日 GitHub 精选 · 2026-10-29（第 16 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、工程实践（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [ruvnet/RuView](https://github.com/ruvnet/RuView) | 应用项目 | Rust | 101.1k | 日榜 +557 ⭐ |
| 2 | [hmjz100/LinkSwift](https://github.com/hmjz100/LinkSwift) | 应用项目 | JavaScript | 34.9k | 日榜 +1,616 ⭐ |
| 3 | [pranshuparmar/witr](https://github.com/pranshuparmar/witr) | 工程实践 | Go | 22.8k | ≈510/周（估算） |
| 4 | [herdrdev/herdr](https://github.com/herdrdev/herdr) | AI Agent | Rust | 46.4k | ≈1,500/周（估算） |
| 5 | [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | AI Agent | Go | 36.0k | ≈1,320/周（估算） |

---

## 1. RuView —— 用 WiFi 信号「看见」人：穿墙检测、呼吸心率、姿态估计，无需摄像头与穿戴设备

**一句话简介**：房间里本来就充满 WiFi 电波，人在其中走动、呼吸都会扰动它——RuView 把这些扰动读成数据：谁在、在做什么、是否安好，全程无摄像头。

**仓库信息**
- 地址：https://github.com/ruvnet/RuView
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：101.1k（101099）｜ 近期增量：日榜 +557 ⭐
- 协议：MIT ｜ 官网 / 文档：docs/ 用户指南 + ESP32 固件仓库 + HuggingFace 预训练模型（wifi-densepose-pretrained）+ Home Assistant 集成文档 + 官方文档站

**核心功能**
- **穿墙环境感知**：利用 WiFi CSI（信道状态信息，即人对电波的细微扰动）隔墙检测有人与否、清点人数、跟踪进出，黑暗中照常工作，室内不需要任何摄像头。
- **非接触生命体征**：静坐或睡眠状态下连续测呼吸频率与心率，支持睡眠分期判别与呼吸暂停筛查，适合老人看护与婴儿监护场景。
- **WiFi 姿态估计**：从 CSI 时序模式估计 17 个身体关键点（WiFi DensePose），识别行走、坐立、手势与跌倒；预训练模型从 HuggingFace 加载，也可录制数据自训练并切换 LoRA 配置。
- **全栈开源 + 智能家居集成**：ESP32 节点固件、模型工作流、本地自动化引擎（状态 / 历史 / Wasm 插件 / HomeKit）全部开源，原生对接 Home Assistant 等四大智能家居生态。

**技术栈**
Rust 核心 + ESP32 CSI 固件（几美元级传感器）+ RVF 模型文件与 LoRA 配置切换，本地优先；HOMECORE 自动化引擎带签名 Wasm 插件。

**适用场景**
老人居家看护与跌倒检测；不想在卧室 / 浴室装摄像头的隐私敏感监测；智能家居「人在与否」联动；RF 感知研究与教学。

**推荐理由**
- **重新定义「传感器」**：不新增摄像头、不要求穿戴，把房间里已有的 WiFi 电波变成传感器，思路极巧，且从固件到模型全栈开源可复现。
- **诚实标注成熟度**：README 明确说明多源融合部分「精度仍是合成数据水平、待真实数据验证」——对前沿感知项目而言，这种透明度难得。

> **注意**：感知精度依赖房间环境与节点布位，需逐场景校准；穿墙姿态估计等高级能力部分仍属研究性质，生产使用前需自行验证；ESP32 节点需自行采购刷写。

> **一句话理解**：CSI 就像房间里的「水波纹」：人走动、呼吸就像往水池里扔小石子，RuView 读的是这些涟漪的形状——不用看，也知道谁在水里。

---

## 2. LinkSwift —— 九大网盘直链获取脚本：百度/阿里/夸克等直链解析 + 下载器联动，老牌直链助手续作

**一句话简介**：中文互联网的持久刚需：在网盘网页里点一下就拿到直链，交给多线程下载器拉文件——不装官方客户端、不开会员，脚本只做「取件码」这一件事。

**仓库信息**
- 地址：https://github.com/hmjz100/LinkSwift
- 类目：应用项目 ｜ 语言：JavaScript ｜ Stars：34.9k（34919）｜ 近期增量：日榜 +1,616 ⭐
- 协议：AGPL-3.0 ｜ 官网 / 文档：GitHub / OpenUserJS / 脚本猫三源分发 + 详细中文 README（含显式合规声明）+ 正式版与金丝雀版双更新通道 + 原 syhyz1990/baiduyun 血统（2022 年起持续维护）

**核心功能**
- **九大网盘全覆盖**：百度网盘、阿里云盘、天翼云盘、中国移动云盘、迅雷、夸克、UC、123 云盘、光鸭云盘一个脚本通吃，网页端直接解析文件直链。
- **下载器联动**：解析出的直链可直接交给 Aria2、IDM 等多线程下载器批量拉取，摆脱网页端单线程体验（速度取决于网盘接口策略）。
- **界面美化与持续增强**：在原版「网盘直链下载助手」基础上重构 UI 并持续增加功能，正式版 + 金丝雀版双通道，多安装源避免单点失效。
- **合规立场清晰**：README 明确声明全部基于服务商公开 API 获取直链、不破解限速，仅服务「不便使用官方客户端」的合法下载需求。

**技术栈**
纯 JavaScript 用户脚本（Tampermonkey / 油猴生态），GitHub / OpenUserJS / 脚本猫三源分发，基于 syhyz1990/baiduyun 修改增强。

**适用场景**
用 Aria2 / IDM 管理大文件下载；在服务器或 NAS 上拉取网盘文件；不想为偶尔的下载需求安装各家官方客户端。

**推荐理由**
- **刚需 + 长期主义**：网盘下载是中文互联网的持久刚需，项目自 2022 年持续维护至今，日榜 +1,616 说明社区基本盘极大。
- **边界感难得**：在同类工具普遍打擦边球的环境里，它把「能做什么、不能做什么」写在最显眼处，降低用户与维护者双方的风险。

> **注意**：实际下载速度完全取决于网盘对直链接口的策略，非会员场景随时可能失效或降速；需自装 Tampermonkey 并按 README 选择安装源；网盘接口变更需跟进脚本更新。

> **一句话理解**：直链相当于快递员把包裹直接递到你手上，而官方网页版要求你在营业厅排队取件——脚本只是帮你拿到「取件码」，包裹多快到手仍由快递公司（网盘）决定。

---

## 3. witr —— Why Is This Running：一条命令把进程/端口/容器/文件反查到完整启动链

**一句话简介**：每天都要问的问题终于有了专门工具：lsof + ps + docker inspect 各查一步的流程，收敛成一条命令——还有浏览器沙箱，零安装先玩再装。

**仓库信息**
- 地址：https://github.com/pranshuparmar/witr
- 类目：工程实践 ｜ 语言：Go ｜ Stars：22.8k（22828）｜ 近期增量：≈510/周（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：pranshuparmar.github.io/witr 在线交互沙箱（零安装体验）+ brew / conda / aur / winget / npm 等七渠道安装 + Trendshift / Product Hunt 收录 + 完整示例输出文档

**核心功能**
- **四类入口一个答案**：进程、监听端口、容器、文件任一为起点，反查「谁在什么时间、用什么命令、被哪条父进程链拉起来」，一条命令给出完整血缘。
- **三种输出形态**：人类可读文本、机器可读 JSON（供 CI 与脚本消费）、交互式 TUI，同一份调用随取随用。
- **全平台全渠道**：Linux / macOS / Windows / FreeBSD 四平台，brew、conda、aur、winget、npm 等七渠道分发，另有在线模拟沙箱做引导教程。
- **为 AI Agent 设计**：专门提供供编码代理调用的用法：Agent 排查「这个端口谁占的」时直接拿结构化答案，不必再人肉串联 ps / lsof。

**技术栈**
Go 单二进制，跨平台聚合进程 / 端口 / 容器信息，JSON 与 TUI 双输出，多包管理器分发，GitHub Pages 在线教程。

**适用场景**
排查「8080 被谁占了」「这个 node 进程哪来的」；接手陌生服务器时快速建立进程全景；写进自动化巡检与 Agent 运维工具链。

**推荐理由**
- **把高频人肉操作产品化**：进程溯源是运维与开发的日频痛点，witr 把三四个命令的串联收敛成一条，工具定位极准。
- **「小工具」做出基础设施完成度**：四平台 + 七渠道 + 在线沙箱 + JSON API + TUI，工程完成度罕见，22.8k star 实至名归。

> **注意**：只回答「为什么在跑、从哪来」，不做 kill / 管控动作；容器场景需要相应运行时权限；极老的 init 体系下血缘链可能不完整。

> **一句话理解**：传统排查像查户口要分别跑派出所、街道和单位；witr 相当于输入身份证号，一次性拿到「出生证明 + 全套家族谱系」。

---

## 4. herdr —— 编码代理的常驻运行时：断线不停工、多机一窗、Agent 原生 API

**一句话简介**：并行跑多个编码代理之后，「终端一关全没了、谁在等我根本不知道」是必撞的墙——herdr 给了系统级答案：代理们住进一间不用下班的办公室。

**仓库信息**
- 地址：https://github.com/herdrdev/herdr
- 类目：AI Agent ｜ 语言：Rust ｜ Stars：46.4k（46377）｜ 近期增量：≈1,500/周（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：herdr.dev 官方文档站（quick-start / session-state / connecting-machines 等）+ Homebrew formula + 中英双语 README（含简体中文）+ release 下载统计徽章

**核心功能**
- **断线不丢工作**：合上笔记本、SSH 掉线、客户机关闭，代理在后台服务器上继续跑；机器重启后自动恢复布局与会话状态（原进程需重启）。
- **多机一窗**：本地机器与多台已保存的 SSH 机器会话并列在一个窗口，统一代理列表、各自独立重连。
- **状态一目了然**：每个面板实时标注 working / blocked / idle，代理停下来等答复时主动提醒——不用挨个翻终端找「卡住的那个」。
- **Agent 原生接口**：代理可通过 CLI 与 socket API 驱动 herdr：自己开面板、提交提示、读取输出，把 herdr 当成自己的工位。

**技术栈**
Rust 编写，单机后台服务 + 客户端架构，支持 session-state 恢复、CLI 与 socket API，Homebrew 一键安装，官网全套文档。

**适用场景**
同时开多个编码代理跑长任务且要下班关机的个人开发者；SSH 到远程 GPU 服务器跑代理的团队；想把代理运行状态接入自有看板的人。

**推荐理由**
- **踩中多代理时代的真痛点**：从「单代理」走向「并行多代理」后，会话存活与状态可见是所有人的第一堵墙，herdr 把它做成了基础设施。
- **定位清醒**：不做代理框架、不绑定模型，只做「代理们脚下的地板」，与 Claude Code / Codex 等现有工具是叠加而非竞争关系。

> **注意**：机器重启后恢复的是布局与会话状态，原进程不存活，需依赖代理自身的会话续接能力；目前主要面向终端型编码代理，GUI 工具不在管理范围。

> **一句话理解**：tmux 让终端会话断线后存活；herdr 是给一群 AI 同事租了间不用下班的办公室——你走了它们接着干，你回来看板告诉你谁干完了、谁在等你拍板。

---

## 5. DeepSeek-Reasonix —— 开源命令行编码助手：任意模型、ACP 协议、扩展系统与 Studio 图形界面

**一句话简介**：国产开源编码助手里工程化程度的头部样本：行为契约（SPEC）写进仓库、协议（ACP）标准化、四份专项文档齐全，36k star 且发版活跃。

**仓库信息**
- 地址：https://github.com/esengine/DeepSeek-Reasonix
- 类目：AI Agent ｜ 语言：Go ｜ Stars：36.0k（35991）｜ 近期增量：≈1,320/周（估算）
- 协议：MIT ｜ 官网 / 文档：esengine.github.io/DeepSeek-Reasonix 文档站 + GUIDE / ACP / EXTENSIONS / SPEC 四份专项文档 + npm 包 reasonix + GitHub Actions CI 徽章 + Discord / QQ 双社区

**核心功能**
- **本地运行、模型自选**：程序跑在你电脑上，模型是可配置服务：接 DeepSeek、Claude、Kimi 均可，读什么代码由你说了算，任务只在指定项目目录内执行。
- **ACP 协议 + 扩展系统**：通过标准 ACP（Agent Client Protocol）接入编辑器与客户端，扩展机制开放能力边界，SPEC 文档把行为契约写进仓库。
- **Reasonix Studio 图形界面**：命令行之外提供 Studio 2.x 桌面端，编码会话、diff 与任务管理可视化操作。
- **工程规范齐全**：npm 包 reasonix 分发、CI 持续运行、GUIDE / ACP / EXTENSIONS / SPEC 四份文档 + 官网文档站，中英双语社区（Discord / QQ）。

**技术栈**
Go 实现，npm 分发（reasonix），ACP 协议，扩展系统，GitHub Actions CI，官网文档站与 Studio 桌面端。

**适用场景**
想要 Claude Code 的使用形态但不绑定任何一家的开发者；用国内模型（DeepSeek / Kimi）直连的编码助手需求；研究 ACP 协议与 agent 客户端集成的团队。

**推荐理由**
- **国产生态的成熟答卷**：36k star、发版活跃、文档四件套齐全，是开源命令行编码助手里工程化程度最高的国产项目之一。
- **契约先行**：把 SPEC（行为规范）与 ACP 协议文档放进仓库，对二次开发与集成方极其友好。

> **注意**：能力上限取决于所接模型服务，与闭源旗舰对比仍有差距；README 含赞助商推广位，选型时注意甄别；扩展生态尚在早期。

> **一句话理解**：它相当于一个「自备粮草」的实习生：活儿在你的项目目录里干，饭（模型 API）你自己定——换供应商不用换实习生。

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

- Trending 日榜 14 条 / 周榜 11 条，合并去重后绝大多数为已推送仓库或技能 / 插件合集，新候选 3 个（RuView、LinkSwift、macro）全部来自日榜；Agent 类目由上期遗留优先项（DeepSeek-Reasonix）与 Search 补池（herdr）兑现。
- 算法 / 模型类目本期无达标候选（litgpt、openevolve、vllm-omni 等周均估算均低于 300/周门槛），本期覆盖应用 / 工程 / Agent 三个类目。
- 口径说明：日 / 周榜为 Trending 实测值，标注「估算」者为「累计 star ÷ 建库天数 → 周均」，仅作热度参考。

**本期按规则排除的候选**

- elayadesign/ai-design-skills、expo/skills、obra/superpowers、ruvnet/ruflo —— Agent / 设计技能与插件合集，非独立软件项目，照旧排除。
- xiaolai/the-craft-of-selfteaching —— 教程书籍类仓库且无 License，排除。
- Nutlope/hallmark、pbakaus/impeccable —— 设计规则 / 规范包，实质为技能类资源，延续前几期口径。
- Graphify-Labs/graphify —— 实质以 Claude Code skill 分发，延续排除。
- macro-inc/macro —— 应用项目合格（Rust / AGPL-3.0 / 日榜 +117），但应用类目两席已给热度更高的 RuView 与 LinkSwift，名额让位。
- codewhale-hq/Codewhale、tinyhumansai/openhuman —— Agent 类目合格但与已入选的 herdr / DeepSeek-Reasonix 定位重叠（终端 agent / harness 同质化），名额让位。
- Lightning-AI/litgpt、algorithmicsuperintelligence/openevolve、vllm-project/vllm-omni —— 算法 / 模型类目周均增量不达标（<300/周）。
- cloudflare/security-audit-skill —— 周榜 +16,002 但为技能包且此前已因超 30 天未提交排除。
- TauricResearch/TradingAgents、anomalyco/opencode、HKUDS/DeepTutor、JetBrains/thinkrail、makecindy/cindy 等上榜仓库 —— 均已推送过，去重排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-29 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
