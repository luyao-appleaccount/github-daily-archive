# 每日 GitHub 精选 · 2026-10-16（第 7 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [Droid-Deck/DroidDeck](https://github.com/Droid-Deck/DroidDeck) | 应用项目 | Kotlin | 9.0k | ≈+2,860 ⭐ 周均（估算） |
| 2 | [magnitudedev/magnitude](https://github.com/magnitudedev/magnitude) | 算法/模型 | Rust | 6.9k | ≈+381 ⭐ 周均（估算） |
| 3 | [NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra) | 工程实践/工具链 | Java | 88.8k | +1,369 ⭐ 日榜 / +6,614 ⭐ 周榜 |
| 4 | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | AI Agent | TypeScript | 250.5k | ≈+27,400 ⭐ 周均（估算） |
| 5 | [lexmount/moli](https://github.com/lexmount/moli) | AI Agent | Rust | 18.7k | ≈+1,950 ⭐ 周均（估算） |

---

## 1. DroidDeck —— 把 SteamOS 体验搬进 Android 掌机

**一句话简介**：让 Android 掌机变成一台「Steam Deck」：装上 DroidDeck 后 Valve 的 Steam 客户端以大屏模式启动，Windows 游戏通过 Valve 的 ARM64 Proton 运行。它不是模拟器前端，而是把 Linux 运行时（Proton 谱系 + 图形转译 + 音频）连同 Steam、桌面与模拟器一起装进 APK，全流程不需要 root。

**仓库信息**
- 地址：https://github.com/Droid-Deck/DroidDeck
- 类目：应用项目 ｜ 语言：Kotlin ｜ Stars：9.0k（8997）｜ 近期增量：≈+2,860 ⭐ 周均（估算）
- 协议：GPL-3.0 ｜ 官网 / 文档：GitHub Releases（0.4.0）+ 仓库内 docs/ 与构建脚本

**核心功能**
- **大屏 Steam 与 Proton 一体打包**：内置 Valve Steam 客户端（大屏模式）与 ARM64 Proton，Windows 游戏走 Proton 转译运行，不依赖串流或云游戏。
- **非 root，但把兼容清单写清楚**：无需 root；要求 Android 9+ 且 Adreno 730 或 8xx 及以上，Adreno 6xx 为实验性（DirectX 11 走 DXVK 2 可能能跑、DirectX 12 仍可能崩），Mali / Xclipse / PowerVR / Adreno 710 明确不支持。
- **把第三方商店并进同一个启动器**：Stores 页面可登录 GOG、Epic Games 与 Amazon Games，浏览目录与库、下载到 Games 目录，并以「非 Steam 游戏」方式挂进 Steam，因此同样从 Proton 启动。
- **Linux 应用与桌面也留了位置**：Store 通过 Flatpak 安装 Flathub 的 ARM64 应用与游戏，也支持 AppImage 与自定义脚本；另可安装 Desktop & apps 模块使用桌面与模拟器。
- **构建与回归测试都在仓库里**：`tools/build_local.sh`（Docker + Java 17 + Android SDK/NDK + Rust + Python 3 + zstd）复现与 CI 相同的原生库与依赖校验，`tools/test_local.sh` 跑预载回归；Releases 里有正式 APK。

**技术栈**
Kotlin 编写的 Android 应用 + 打包进 APK 的 Linux 运行时（底层沿用 WinNative、Bannerlator 等 Proton / Wine 谱系，商店能力来自 Legendary 与 gogdl 的改编）；官方构建依赖 Docker、Java 17、Android SDK/NDK、Rust 与 Python 3；GPL-3.0 分发。Steam 本体不在包里，首次启动会下载。

**适用场景**
手上有骁龙 + Adreno 掌机（或平板、手机），想在同一个设备上玩 PC 游戏又不接受串流延迟的人；想把 Steam 库、Linux 应用与模拟器收进一个启动器的折腾型玩家；研究 Android 图形兼容层（DXVK / Proton / 软件合成栈）的开发者。

**推荐理由**
- **它把「Android 上的桌面级游戏栈」做成了可安装的东西**：不是壳或小工具，而是把 Proton、图形转译、Steam 客户端与第三方商店整合成一次 APK 安装加运行时下发，非 root 即可跑通。
- **兼容边界写得诚实**：README 直接列出支持的 Adreno 型号、哪些属于实验性、Android 14+ 需要打开哪个开发者选项，省掉了大量试错成本。
- **桌面与模拟器没有被落下**：除了玩 Steam 游戏，还提供桌面环境、Flathub 应用与模拟器入口，等于把掌机当成一台小电脑用。

> **注意**：① **强依赖 GPU 型号**——仅 Adreno 730+ / 8xx 属支持范围，Mali、Xclipse、PowerVR 与 Adreno 710 明确不支持，Adreno 6xx 只算实验；② 需预留约 **3 GB 运行时 + 1.1 GB 桌面与模拟器**空间，且首次启动要从 Steam 下载游戏；③ Android 14+ 必须打开「停用子进程限制」开发者选项，否则 Steam 起不来；④ 桌面合成走**软件渲染**，Firefox 沙箱在 proot 下被削减，**兼容性与性能按机型差异很大**、官方称硬件验证有限；⑤ 项目**与 Valve 无关联**，Steam / Proton 归 Valve，LSFG 帧生成需自备付费的 Lossless Scaling；⑥ README 专门提示**没有独立官网**，任何自称官方的下载站都别信；⑦ 采用 **GPL-3.0**，二次分发需遵守其条款。

> **一句话理解**：把它想成「给 Android 掌机装上一套轻量版 SteamOS」：系统仍是 Android，但你点开的是 Steam 大屏界面、跑的是 Windows 游戏——代价是得有一块 Adreno 730 以上的 GPU，以及一只愿意折腾的手。

---

## 2. Magnitude —— 在你的芯片上现场调核的本地推理引擎

**一句话简介**：把「手写 kernel」换成「现场搜索」：Magnitude 在模型下载后用最多约一分钟在你的真实芯片上尝试不同的线程切分、分块大小与预取深度，保留更快且**不改变输出**的组合。之后它以桌面应用形态运行开源模型，一键接入 Pi / OpenCode / Codex / Claude Code 等 Agent，其他工具走 OpenAI 兼容 API。

**仓库信息**
- 地址：https://github.com/magnitudedev/magnitude
- 类目：算法/模型 ｜ 语言：Rust ｜ Stars：6.9k（6866）｜ 近期增量：≈+381 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：docs.magnitude.dev（原理 / 基准 / 远程部署）+ GitHub Releases

**核心功能**
- **按硬件自动调核（auto-tuning）**：下载模型时在同机试不同 kernel 组合并取最快的一组——官方把「通用引擎只能用一刀切的 kernel」当作自己更快的原因，因此每个模型在你的芯片上各自调优。
- **内置最强的投机解码草稿模型**：每个模型附带其最快的 drafter 用于投机解码（speculative decoding）：先用小模型草拟若干 token、再由主模型批量校验，从而把逐 token 生成变快。
- **内存会伸缩的 KV 量化与缓存共享**：量化的 KV cache 让每个 Agent 的内存占用减半、Agent 停止后释放；多个并发会话共享 prefix cache，避免彼此拖慢。
- **一行接上你已经在用的 Agent**：一键连接 Pi、OpenCode、Hermes、OpenClaw、Codex、Claude Code、Oh My Pi、Cline；任何支持 OpenAI 协议的工具也能通过兼容 API 接入。
- **可以当常驻服务器用**：`magnitude server setup` 在 Linux / macOS 上把它装成开机自启、注销后继续运行、自带更新的服务，供其他机器上的浏览器与 Agent 调用。

**技术栈**
Rust 实现的开源推理引擎，以「桌面应用 + `magnitude` CLI」形态分发（macOS / Windows / Linux），支持 Apple Silicon、NVIDIA、AMD 以及纯 CPU；Apache-2.0；已写优化 kernel 的模型以主流开放权重家族为主（清单见 magnitude.dev/models）。

**适用场景**
想在本机离线跑开源模型、又嫌 Ollama / LM Studio 慢的人；需要给多个 coding agent 提供本地模型端点（含并发会话）的开发者；想把推理服务装成常驻后台供局域网其他机器使用的团队；对「数据不出本机」有硬要求、又不想持续付 API 费的用户。

**推荐理由**
- **优化思路是可解释的工程手段**：「按硬件调 kernel + 投机解码 + 量化 KV + prefix cache」每一步都能对上明确的加速来源，README 也把自动调优到底在试什么讲清楚了，而不是只丢一句「更快」。
- **基准给到了可核对的粒度**：给出对 Ollama 的平均对比：Mac 上 prefill 1.32× / decode 2.19×，NVIDIA 上 1.34× / 2.17×（11 个热门本地模型的平均），并附完整基准页。
- **对 Agent 负载做了针对性优化**：并发会话共享 prefix cache、KV 量化随 Agent 生灭——这两点直接对应「多个 agent 同时打同一个本地模型」的真实场景。

> **注意**：① **「比 Ollama 快 2 倍」是官方自述口径**（11 个热门本地模型的平均），换到你的模型、芯片与量化档差异可能很大，建议在本机复测；② 优化覆盖的是**主流开放权重家族**，冷门模型未必有调好的 kernel，选型前先查 magnitude.dev/models；③ 自动调优需要**最多约一分钟**的下载后处理，且必须与最终运行**同一台机器**（换机要重调）；④ 应用与引擎开源（Apache-2.0），但**模型权重各有自己的许可**，商用前需逐个确认；⑤ 无独显也能用纯 CPU，但只跑得动小模型；⑥ 项目 2026-06 建库、迭代很快，接口与模型清单可能变动，远程部署能力也相对新。

> **一句话理解**：可以理解成「给每台机器现磨一套刀头」：别人发的是同一把万能刀（通用 kernel），它在你的机器上磨一次，之后切同一个模型就更快——但换机器或换模型都得重新磨。

---

## 3. Ghidra —— NSA 开源的软件逆向工程框架

**一句话简介**：一套给逆向分析团队用的完整工作台：把可执行文件丢进去，得到反汇编、汇编、反编译与调用关系图；既能在图形界面里人工分析，也能用无界面（headless）模式在服务器上批量跑脚本。用户可用 Java 或 Python 写扩展与分析脚本，把流程固化下来并在团队间共享。

**仓库信息**
- 地址：https://github.com/NationalSecurityAgency/ghidra
- 类目：工程实践/工具链 ｜ 语言：Java ｜ Stars：88.8k（88829）｜ 近期增量：+1,369 ⭐ 日榜 / +6,614 ⭐ 周榜
- 协议：Apache-2.0 ｜ 官网 / 文档：ghidra-sre.org + 仓库内 GhidraDocs（Getting Started）与 DevGuide.md

**核心功能**
- **反编译到接近可读的伪代码**：内建 decompiler 把机器码还原成 C 风格伪代码，这是它最常用的能力，配合反汇编、符号恢复与类型修复一起看。
- **交互式与批处理两种模式**：既有完整的 GUI（CodeBrowser）做深度人工分析，也支持无人值守的自动化分析，适合把「一批样本跑一遍脚本」这类工作放到服务器上。
- **指令集与文件格式覆盖面大**：支持多种处理器指令集与可执行文件格式，因此 x86、ARM 等异构样本能在同一套工具里处理，不必为每种平台换软件。
- **可用 Java / Python 扩展**：官方提供 GhidraDev（Eclipse 插件）与 VS Code 集成路径，也能从 CodeBrowser 直接生成 VS Code 工程；分析脚本与插件可以随团队沉淀。
- **工程化底座完备**：仓库带 build-ghidra 的 GitHub Actions 构建与原生库编译流程（Gradle），有正式多平台 Release 包（最新 Ghidra 12.1.4）与 PyGhidra 入口（`support/pyghidraRun`），文档分 Getting Started 与 Developer's Guide。

**技术栈**
Java 开发的跨平台桌面框架（Windows / macOS / Linux）；运行需要 JDK 25 64 位，从源码构建还需 Gradle 9.1+（或用仓库自带 wrapper）与 GCC/Clang 或 MSVC 编译原生组件；脚本层支持 Java 与 Python（PyGhidra）；Apache-2.0。

**适用场景**
安全研究与恶意样本分析（NSA 自述的初衷正是复杂逆向的规模化与团队协作）；漏洞挖掘与代码审计中对第三方二进制做理解；固件与嵌入式、老平台的指令集逆向；需要把逆向步骤自动化、批量化或做成团队共享插件的场景；教学与逆向学习者（获取与扩展门槛远低于同类商业工具）。

**推荐理由**
- **事实标准级的工具，来源权威且完全开源**：由 NSA 研究部门创建并持续维护，长期是商业逆向工具最主要的开源替代；Apache-2.0 许可，代码、构建流程与安全公告全在公开仓库里。
- **规模化与协作是设计目标**：批处理模式、脚本化扩展、可共享插件，都是为「复杂逆向需要多人多机协作」准备的，而不是单机小工具。
- **生态与文档成熟**：多平台正式 Release、PyGhidra、Eclipse / VS Code 集成、Getting Started 与开发者指南齐备，可查资料远多于多数同类项目。

> **注意**：① **运行需要 JDK 25 64 位**，构建还需要 Gradle 9.1+ 与 C/C++ 工具链，环境门槛高于普通桌面软件；② **官方明确警告某些版本的 Ghidra 存在已知安全漏洞**，README 建议先读 Security Advisories；安装时**不要解压覆盖到已有目录**；③ 逆向分析的合法性取决于授权与用途——工具中立，但针对第三方软件与固件的使用有明确法律边界；④ 它是重型分析平台，启动与分析大样本都吃内存与磁盘，不适合当轻量脚本工具；⑤ 它属于长期维护型项目（2019 年即已开源），与本期其他「新项目」定位不同，此处作为工程实践类的稳定选项推荐。

> **一句话理解**：把它理解成「逆向工程师的 IDE」：普通工具丢给你一堆十六进制与汇编，它帮你把二进制还原成能读的伪代码、画出调用关系，并把整个过程做成可脚本化、可团队复用的工作流。

---

## 4. DeepSeek Harness（dsh）—— 一切皆插件的 Agent 运行时

**一句话简介**：不做「又一个客户端」，做可插拔的底座：DeepSeek Harness（dsh）把模型接入、工具与界面都做成插件，核心只负责插件的加载与组合，设计理念源自 arXiv 上关于「时空可组合性」的论文（依托 Cordis 框架）。上手只要 `npx @deepseek-ai/dsh web`，默认在 127.0.0.1:3080 起一个 Web UI。

**仓库信息**
- 地址：https://github.com/deepseek-ai/deepseek-harness
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：250.5k（250495）｜ 近期增量：≈+27,400 ⭐ 周均（估算）
- 协议：MIT ｜ 官网 / 文档：deepseek-harness.github.io（用户 / 架构 / 开发三套文档）+ GitHub Releases + Discussions

**核心功能**
- **一切皆插件的架构**：模型接入、工具、界面全部通过插件挂载，底座只解决「插件的加载与组合」；插件作者给仓库打上 `dsh-plugin` 主题即可被发现，生态已围绕该主题自然生长。
- **一条命令就能跑起来**：`npx @deepseek-ai/dsh web` 直接拉起本机 Web UI（默认 127.0.0.1:3080 并自动打开浏览器；SSH 场景只打印 URL，可加 `--no-open`）；从源码跑则是 `pnpm install && pnpm run build && pnpm dsh web`。
- **文档按角色分层**：官方站点分用户指南（Web UI 用法）、架构文档与开发指南三套；仓库内另有 AGENTS.md 专门写给「让 agent 自己改这个项目」，反馈与协作走 Discussions 与 Discord。
- **自带安全与合规材料**：提供 SAFETY.md 运行安全须知与 THIRD_PARTY_NOTICES.md 第三方依赖与许可清单，并在 README 中显式提示 developer preview 的破坏性变更。
- **已有围绕它的桌面端生态**：除官方 npm 包与源码两条路径，社区已出现把 dsh 做成桌面应用的配套项目，说明「插件化底座」确实被当作平台在使用。

**技术栈**
TypeScript 实现，基于插件框架 Cordis（设计见 arXiv:2608.25512《A Programming Paradigm for Spatiotemporal Composability》）；包管理与构建用 pnpm，产物包含 Web UI 与桌面端两条构建目标（Make 目标可查 `make help`）；MIT 许可，第三方依赖许可单独披露。最新版本 dsh-v0.2.1-alpha.4。

**适用场景**
想自建可深度定制的 Agent 运行时、而不是去改别人写死的客户端的团队；需要把模型、工具与 UI 都替换成自家实现的工程场景；研究「插件化 Agent 架构」如何组织的开发者（有论文、架构文档与 AGENTS.md 三条线索）；想用一条 npm 命令在本地快速评估 harness 形态的个人用户。

**推荐理由**
- **大厂官方出品，架构选择很大胆**：DeepSeek 直接把「插件系统」当产品，而不是包一个现成客户端再改；配论文与架构文档一起看，属于少见的「设计可验证」型项目。
- **上手成本与扩展成本都低**：评估只要一条 npx；扩展只要写插件并打 `dsh-plugin` 主题，底座与生态的分工是清楚的。
- **文档与开源治理相对规范**：用户 / 架构 / 开发三套文档、Discussions 与 Discord、SAFETY.md、第三方许可清单与明确的 MIT 许可——在同等热度的新项目里算相当齐整。

> **注意**：① **处于 developer preview（当前版本带 alpha 标记），README 用大写强调会有破坏性变更**，生产使用前请自行评估并跟随版本；② 运行依赖 Node.js，Web UI 默认只监听 127.0.0.1（安全默认值，对外服务需自行处理暴露与鉴权）；③ 运行前务必读 **SAFETY.md**——Agent 会调用工具并执行命令，权限边界要自己收紧；④ 插件生态尚在早期，**第三方插件质量与维护状况参差不齐**，安装即等于运行他人代码；⑤ 24 小时量级的 star 数极高，是典型的「热度跑在成熟度前面」，请以实际可用性而非星标数做决策；⑥ 围绕它的 dsh 桌面端与「免 API Key 使用第三方模型」类插件本期未选入：前者强绑定宿主、独立价值有限，后者合规性存疑。

> **一句话理解**：把它想成「Agent 世界的 VS Code」：作者不预设你用哪个模型、哪些工具、什么界面，只把插件接口与加载机制做好；你装什么插件，它就变成什么工具。

---

## 5. Moli —— 给 Agent 用的「结构优先」无头浏览器

**一句话简介**：「结构优先，像素按需」：Moli 把原生 DOM 与样式状态当作唯一事实来源，Agent 常见操作（取 HTML / Markdown、查 DOM、跑 JS、看网络与存储）**不触发布局与绘制**；只有读元素坐标、坐标输入、截图这类操作才现算一次布局、用完即弃。对外同时提供 CLI 与 CDP / WebDriver Classic / WebDriver BiDi 三种协议，Playwright 可以直接 `connectOverCDP` 连上来。

**仓库信息**
- 地址：https://github.com/lexmount/moli
- 类目：AI Agent ｜ 语言：Rust ｜ Stars：18.7k（18689）｜ 近期增量：≈+1,950 ⭐ 周均（估算）
- 协议：Apache-2.0 / MIT 双许可 ｜ 官网 / 文档：browser.lexmount.com + 仓库内多语言 docs/ 与 Lexbench 基准报告

**核心功能**
- **结构优先的代价模型**：多数自动化请求只需要页面结构而非渲染画面，Moli 因此跳过布局与绘制：截图时从当前 DOM / 样式重建一帧、用后即弃，不做持续渲染与维护可视状态。
- **三种标准协议共用一个二进制**：CDP、WebDriver Classic 与 WebDriver BiDi 共用同一内核与调度器，不再需要单独的 ChromeDriver / geckodriver，也不用手动安装浏览器。
- **为抽取优化的输出格式**：`moli fetch` 可直接产出 HTML、Markdown、JSON、语义文本树与帧感知序列化，支持按选择器 / 脚本 / 响应等待与网络追踪；加 `--layout` 后可输出视口截图、整页截图与内嵌字体的 PDF。
- **是完整 Web 运行时，不是「简化解析器」**：流式 HTML 解析、原生 DOM、V8、模块 / 定时器 / 微任务 / 事件、iframe 与 worker、CSS 级联、Fetch / XHR / WebSocket、Cookie、WebCrypto 与按 profile 隔离的存储（localStorage / IndexedDB / OPFS）都在。
- **效率有可复现的第三方基准**：Lexbench-Headless-Browser（1,928 个任务中取 1,308 个可比任务）：Moli 成功率 81.88%，领先 Kitesurf（62.08%）、Lightpanda（53.29%）、Obscura（44.88%），Chrome 参考值 99.85%；单位任务中位 CPU 用时 100.6 ms（Chrome 687 ms），峰值内存 92 MiB（Chrome 697 MiB）。

**技术栈**
Rust 编写的无头浏览器（Linux / macOS / Windows，提供预编译二进制与一行安装脚本），完整实现 V8、CSS、布局（Taffy）、文本排版（Parley）、命中测试与软件绘制；Apache-2.0 与 MIT 双许可（可择一，最新版本 v1.1.17）。Lexmount Browser 是围绕它构建的商业托管运行时，但开源本体可独立使用。

**适用场景**
给 coding agent / 调研 agent 提供网页抓取与提取能力的团队；爬虫与检索（RAG）数据管线；需要大量并发、低内存的浏览器自动化与评测环境；强化学习中的网页交互环境；CI 里跑 Playwright 脚本但不想维护浏览器镜像的工程团队。

**推荐理由**
- **成本模型抓住了 Agent 场景的本质**：Agent 大多只关心页面「讲了什么」而不关心「长什么样」；把布局与绘制改成按需触发，省下的是实打实的资源——约为 Chrome 的 15% CPU 时间与 13% 峰值内存。
- **兼容性走标准协议而不是自定义接口**：CDP + WebDriver Classic + BiDi 三协议并存、Playwright 可直接连，迁移成本低，这比「自己发明一套抓取 API」务实得多。
- **边界与失败模式写得很清楚**：README 明确列出不做 GUI / 持久窗口 / GPU 合成、不追求像素级对齐、`--layout` 也有未实现的截图与打印模式，并且**不支持的协议路径会显式报错而不是假装成功**——这在自动化工具里非常关键。

> **注意**：① **任务成功率仍与 Chrome 有差距**（81.88% vs 99.85%），复杂前端、Canvas / WebGL、媒体播放类页面不适用，官方明确不追求像素级一致；② 没有 GUI 浏览器、持久窗口与 GPU 合成，需要「看得见画面」的场景请回到 Chrome；③ 截图与打印只覆盖部分模式，`--layout` 是可选开关，忘加就没有布局与视觉能力；④ 与 Lexmount 的商业托管服务同源，**选型时要区分「开源本体」与「云服务」**，README 强调本体可独立使用；⑤ 基准由项目方自家维护（Lexbench 位于 lexmount 组织下），数字可复现但需注意利益相关；⑥ 项目 2026-08 建库、版本迭代很快（v1.1.x），接口与能力仍在演进。

> **一句话理解**：把它理解成「只看目录不看画面的浏览器」：多数时候 Agent 只需要知道页面上有什么、能点哪里，Moli 就不去渲染那一帧画面——像读菜谱而不是把每道菜都做出来看一遍，省时间也省材料。

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

- 候选池：Trending 日榜 12 条 + 周榜 11 条（去重后 21 个仓库），剔除 6 个已在往期推送的仓库（`morluto/rea`、`debpalash/VoiceStudio`、`boykopovar/AnyPS5`、`heygen-com/hyperframes`、`earthtojake/text-to-cad`、`DuarteSantos8/openGym`）后，剩 15 条为新增候选。
- Search API 补充：用 `created:>2026-09-01 stars:>1200 pushed:>2026-10-05`（151 条）、`created:>2026-08-01 stars:>2500 pushed:>2026-10-05`（130 条）、`inference engine stars:>2000 pushed:>2026-10-08 created:>2025-06-01`（6 条）、`topic:llm topic:quantization stars:>1500 pushed:>2026-10-05`（4 条）四组查询拉细分领域候选，并逐一核实 License、最近提交、README 与 release；`magnitudedev/magnitude` 与 `lexmount/moli` 由这条通道入选。
- 类目配额：应用项目 ×1、算法 / 模型 ×1、工程实践 / 工具链 ×1、AI Agent 及基础设施 ×2 —— 覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：Apache-2.0 ×2、MIT ×1、GPL-3.0 ×1、Apache-2.0 / MIT 双许可 ×1，全部为可识别的 SPDX 协议；5 个仓库均有完整 README 正文，且都具备「正式 release + 文档站 / 文档目录 / 基准报告」中的至少一项。
- 去重检查：与往期六期（09-28 / 09-29 / 10-09 / 10-10 / 10-12 / 10-14，共 30 个仓库）均无重叠，基线为 `archive/index.json`。
- 数据口径：total stars、License 与最近提交时间取自 GitHub API（`gh api repos/*`，含 `pushed_at`）；`ghidra` 的增量取自 Trending 原始数字（日榜 +1,369、周榜 +6,614）。`deepseek-harness`、`moli`、`magnitude`、`DroidDeck` 未直接登上本期榜单或榜单未给出增量，其「周均增量」为**由「累计 star ÷ 建库天数」换算的估算值**（分别为建库 64 天 250.5k ≈ 27.4k/周、67 天 18.7k ≈ 1.95k/周、126 天 6.9k ≈ 381/周、22 天 9.0k ≈ 2.86k/周），速览表中统一标注「估算」，不与榜单原始数字混用。
- 质量信号说明：`ghidra` 有 build-ghidra 的 Actions 工作流、多平台正式 Release（Ghidra 12.1.4）与完整开发者文档；`deepseek-harness` 有官方文档站、Discussions / Discord、SAFETY.md 与第三方许可清单；`moli` 有官方站点、多语言文档与可复现的 Lexbench 基准；`magnitude` 有文档站、独立基准页与三平台安装包；`DroidDeck` 有 GitHub Releases（0.4.0）、仓库内构建 / 回归脚本与 Discord 社区。
- 本期特别提示（数据边界差异）：`magnitude`（跑模型）与 `moli`（跑浏览器）属「数据不出本机」的本地方案；`deepseek-harness` 会让 Agent 调用工具并执行命令，需自行收紧权限；`ghidra` 面向的是你有权处理的二进制；`DroidDeck` 涉及 Proton / Steam 与第三方商店的合规使用。选型时请把这一点与功能同等看待。

**本期按规则排除的候选**

- `morluto/rea`（271.8k，日榜 +32,314 / 周榜 +239,477）、`debpalash/VoiceStudio`（日榜 +3,024）、`boykopovar/AnyPS5`（周榜 +25,174）、`heygen-com/hyperframes`（周榜 +5,318）、`earthtojake/text-to-cad`（周榜 +2,244）、`DuarteSantos8/openGym`（周榜 +4,471）：热度全部达标且当期仍在榜，但均已在往期（10-09 / 10-10 / 10-12 / 10-14）推送过，按去重基线排除。
- `anthropics/claude-plugins-official`（日榜 +307）、`obra/superpowers`（+582）、`K-Dense-AI/scientific-agent-skills`（+1,091）、`twostraws/SwiftUI-Agent-Skill`（周榜 +900）、`mattpocock/skills`（+12,147）、`cathrynlavery/diagram-design`（+10,237）、`cursor/plugins`（+1,214）、`affaan-m/ECC`（+1,013）：热度极高，但产物形态是「Agent 技能 / 插件集合」或插件目录，属于规则明确排除的资源聚合型仓库。
- `ruvnet/ruflo`（75.2k，日榜 +147）：MIT 且热度与活性达标，但其形态是给 Claude Code / Codex 用的插件与技能包合集（仓库主题包含 skills / ai-skills），与已排除的 `cursor/plugins` 同类，本期不选入。
- `mksglu/context-mode`（29.8k，日榜 +904）：方向对口 AI Agent 且当日活跃，但仓库页 License 为 `NOASSERTION`，按 License 口径排除；`0xShug0/audio.cpp`（3.6k）、`Tencent/AngelSlim`（1.8k）同样因 License 无法识别排除。
- `ranxianglei/billion-context`（1.4k，周榜 +659）：License 为 `NOASSERTION`，且 star 量级贴近 1,000 门槛，按规则排除。
- `storytold/*` 家族（`photocraft` 63.4k、`pdfcraft` 14.5k、`filmcraft` 13.9k、`wordcraft` 13.2k、`lightcraft` 13.0k、`vectorcraft` 9.2k）：均为同一组织的「纯 Rust 重写」应用，热度与活性都达标但同源同质，且该组织已于 10-14 推送过 `artcraft`，本期继续整体排除。
- `eternity4719/HowToLiveBetter`（63.9k）、`cdyforever/how-to-live-better`（12.1k）：属知识合集与单页阅读版，不是软件项目；`guillaumemeyer/watermarks-remover`（24.2k）剔除 AI 水印的方向存在版权与合规争议，本期均不推荐。
- `Ebony-Vinyl/dsh-our-free-model`（17.9k，MIT）、围绕第三方客户端 DSH 的桌面端与小组件项目（`dsh-desktop` 类）：前者绕开官方 API Key 使用第三方模型、合规性存疑，后者强绑定宿主、独立价值有限，均排除。
- `freeCodeCamp/freeCodeCamp`、`public-apis/public-apis`、`EbookFoundation/free-programming-books`、`vinta/awesome-python`、`awesome-selfhosted` 等：属教程站或资源聚合列表，规则明确排除；`torvalds/linux`、`react/react`、`tensorflow/tensorflow`、`ollama/ollama` 等则是已被广泛使用的顶级项目，作为「本期新发现」的推荐价值有限。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-16 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
