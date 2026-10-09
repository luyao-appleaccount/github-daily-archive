# 每日 GitHub 精选 · 2026-10-09（第 3 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [DuarteSantos8/openGym](https://github.com/DuarteSantos8/openGym) | 应用项目 | JavaScript (React / Node) | 8.2k | +6,086 ⭐ 周榜 |
| 2 | [boykopovar/AnyPS5](https://github.com/boykopovar/AnyPS5) | 算法/模型（二进制翻译 / 重编译） | C++ | 17.1k | +4,669 ⭐ 日榜 / +10,243 ⭐ 周榜 |
| 3 | [EpicGames/raddebugger](https://github.com/EpicGames/raddebugger) | 工程实践/工具链 | C | 8.2k | +279 ⭐ 日榜 / +448 ⭐ 周榜 |
| 4 | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | AI Agent 及基础设施 | TypeScript | 98.7k | +670 ⭐ 日榜 / +3,153 ⭐ 周榜 |
| 5 | [earthtojake/text-to-cad](https://github.com/earthtojake/text-to-cad) | AI Agent 及基础设施 | Python | 18.6k | +1,898 ⭐ 周榜 |

---

## 1. openGym —— 自托管健身追踪

**一句话简介**：自托管健身与体重追踪应用：周计划、引导式训练、逐组记录、肌肉热力图与体重曲线全跑在你自己的服务器上，Passkey 无密码登录 + 多设备字段级合并，还自带可选的 AI 教练与只读 MCP 服务。

**仓库信息**
- 地址：https://github.com/DuarteSantos8/openGym
- 类目：应用项目 ｜ 语言：JavaScript (React / Node) ｜ Stars：8.2k（8191）｜ 近期增量：+6,086 ⭐ 周榜
- 协议：AGPL-3.0 ｜ 官网 / 文档：opengym.duarte-santos.ch

**核心功能**
- **数据完全在你自己手里**：`docker compose up` 即起；前端是 React 19 + Vite 打成的静态文件，后端是纯 `node:http`（只有 `@simplewebauthn/server` 与 `web-push` 两个依赖），数据以 JSON 存在 `./data` 目录；镜像同时发布到 GitLab Registry 与 GHCR，amd64 / arm64 双架构。
- **训练记录细致到专业级**：超级组、热身组、递减组、rest-pause、计时动作（平板支撑 / 悬垂 / 农夫走）、按时间与速度的有氧、每组自定义休息、计划性减载；重量按上次预填、PR 实时识别、杠铃 / EZ 杆 / 六角杠 / 史密斯机自动算片。
- **进阶策略可解释**：线性、Greyskull LP、在可见次数区间内的双重进阶、加时间四种规则；每个目标都会解释「为什么是这个数字」，掉次数不加重量、停滞自动减载。
- **进度可视化**：估算 1RM 曲线、结构平衡比（Poliquin / Thibaudeau / ATG）、一年活跃度热力图、三种模式的肌肉图（训练量去向 / 恢复中 / 未训练）、体重曲线对目标线、进度照片时间轴前后对比滑块。
- **无密码登录与多设备同步**：Passkey（Face ID / Touch ID / 指纹）按档案跨设备同步；两台设备同时编辑时按**字段级合并**而非互相覆盖；可从 FitNotes / Strong / Hevy / Apple Health 导入，也能随时把全部数据导出成一个 JSON。
- **手机端与可选增强**：同一套代码用 Capacitor 打包成离线 App（Android 有签名 APK，iPhone 走 PWA）；可选 AI 教练（自带 Anthropic / OpenAI / Gemini / Ollama key，每处改动都要你批准）与只读本地 MCP 服务（Claude Desktop 可查询训练历史）。
- **工程规范度高于多数同类开源 App**：GitHub Actions 测试 + GitLab 覆盖率徽章、17 项 `.env` 配置列成表、OpenAPI 规格（`api/openapi.yaml`）、自托管指南覆盖 Cloudflare Tunnel / Caddy / Traefik / nginx 与 Kubernetes、界面支持 18 种语言（含 RTL 阿拉伯语）。

**技术栈**
前端 React 19 + Vite（React Router、Zustand），在 Docker 内构建为静态文件；后端纯 `node:http` + `@simplewebauthn/server` + `web-push`，数据落 `./data` 的 JSON；nginx 做单源同源代理 `/api`（Passkey 要求同源）；Capacitor 复用同一套代码打包手机端；Docker Compose 一键起（也可 `--build` 本地构建，宿主机不需要 Node）；训练逻辑（进阶规则、1RM、历史回读）写成可测纯函数，测试与实现同目录。

**适用场景**
想把训练数据攥在自己手里、拒绝订阅制的健身者；有 NAS / 小主机或云主机、愿意用 Docker 自托管的人；需要「计划 + 记录 + 分析」一体化而非零散 App 的进阶训练者；想给自己的训练数据接 AI 教练、或让助手查询历史记录的开发者。

**推荐理由**
- **与主流健身 App 的路线正好相反**：数据存在你自己机器的 `./data` 里，公司倒闭或改条款都不影响你，随时可以 fork 或迁移——这是它最核心的立场。
- **训练学的细节没糊弄**：进阶规则、RIR / RPE 强度、结构平衡比这些「专业教练才用」的概念都真正落进了产品，而且每条进阶目标都会解释依据，不是黑箱。
- **工程成熟度超过同类开源项目**：真实可用的 Docker 部署、双 registry 镜像、CI 测试 + 覆盖率、OpenAPI 规格、字段级冲突合并——属于能长期自托管运行的成色。

> **注意**：① 协议是 **AGPL-3.0**：若你把修改后的版本作为网络服务对外提供，需要按 AGPL 开放修改后的源码，商用前先确认合规；② 首次启动要下载约 140MB 的示范动作素材；③ 手机端要用 Passkey 必须给实例配 HTTPS 域名（自托管指南给了 Cloudflare Tunnel / LAN HTTPS 等方案），iPhone 因 App Store 限制只能自托管后加 PWA 或自己用 Xcode 装；④ AI 教练需自备模型 key，MCP 服务为只读且不包含在 Docker 构建里。

> **一句话理解**：像把训练日志从别人的云笔记搬回自家书柜：格式仍是现代 App 的样子（Passkey、离线可用、多设备同步），但钥匙和本子都在你手上。

---

## 2. AnyPS5 —— 可执行文件移植 / 重链接

**一句话简介**：PS5 可执行文件的自动移植工具：用重链接器（relinker）把可执行文件转成目标系统的原生格式，再补上系统库的动态链接实现，让程序在 Linux / Windows 上原生跑起来——不靠模拟器，也没有额外的运行时进程。

**仓库信息**
- 地址：https://github.com/boykopovar/AnyPS5
- 类目：算法/模型（二进制翻译 / 重编译） ｜ 语言：C++ ｜ Stars：17.1k（17097）｜ 近期增量：+4,669 ⭐ 日榜 / +10,243 ⭐ 周榜
- 协议：GPL-2.0 ｜ 官网 / 文档：boykopovar.github.io/AnyPS5

**核心功能**
- **重链接器而非解释器**：`core/relinker` 把 PS5 可执行文件**转换**成目标系统的原生格式，而不是逐条指令解释执行——这是它与「模拟器」路线的根本区别。
- **系统库替代实现**：`core/libs/prx` 里逐个实现 PS5 的系统 prx 库函数，做成适合动态链接的形式，按需补齐函数面。
- **着色器重编译**：`core/shader/recompiler` 把 PS5 着色器重编译成 SPIR-V，可在开启 `ANYPS5_ENABLE_SPIRV_TOOLS` 时用 Spirv-Tools 做校验。
- **兼容性口径透明**：仓库维护已验证游戏清单（`docs/user/COMPATIBILITY.md`）；首页进度图按「已声明函数占比」与着色器覆盖率生成实时徽章，并明确说明这是「**已声明**的系统函数」占比，而非全部 PS5 系统函数——不夸大兼容度。
- **输入映射**：支持 SDL 手柄（含摇杆与扳机）；键盘鼠标可通过 `anyps5-input.ini` 配置。
- **失败即显式报错**：遇到不支持或意外状态严格抛 `std::runtime_error`，把 `what()` 打到 stderr 后终止进程——不静默降级，便于定位问题。
- **文档分层清晰**：使用指南、构建说明、架构文档、技术债清单（`TechnicalDebt.md`）、代码风格约定、贡献指南各自独立成篇。

**技术栈**
C++ 为主，依赖 `3rdparty/` 下的第三方库（如 SPIRV-Tools）；两大核心模块为 `core/relinker`（重链接）与 `core/libs/prx`（系统库实现）；通过 GitHub Pages 发布覆盖率 / 进度徽章；实测环境为 GTX 1050 Ti / i5-7500 @3.4GHz（2D 平台游戏 Dreaming Sarah 稳定 60fps）。

**适用场景**
对二进制翻译 / 重编译、系统 ABI 兼容层感兴趣的系统与安全研究者；做游戏保存（preservation）与互操作性工作的团队；想学习「不靠模拟器做跨平台移植」这套工程方法的学生与工程师；需要拿真实大型二进制做静态分析与重编译实验的平台。

**推荐理由**
- **换了一条技术路线**：不解释指令，而是把可执行文件重链接成宿主原生格式并补上系统库——这在同类项目里属于相对少见、研究价值更集中的一支。
- **诚实度罕见**：进度按「已声明函数」算的诚实口径，兼容游戏清单与技术债清单都公开，不吹「完美兼容」。
- **合规姿态写得清楚**：README 有专门免责声明：不包含、不分发、也不要求任何受版权保护的软件、固件、密钥或专有库，并要求使用者自行确保二进制的获取与使用合法。

> **注意**：① 项目仍处早期，可用范围由已验证游戏清单界定，多数商业游戏尚不可用；② **使用前提是你自己拥有合法的二进制**——README 把合法性责任明确交给使用者，务必先确认当地法律与授权；③ GPL-2.0（only）是强 copyleft，并入闭源商业产品前需谨慎评估；④ 当前主要面向 x86-64 的 Linux / Windows 目标平台。

> **一句话理解**：像把一本外语书按目标语言**重新排版**并补齐缺失的注解，而不是请一位翻译在边上逐句同声传译——排版是永久的，翻译是临时的。

---

## 3. RAD Debugger —— 巨型工程调试与工具链

**一句话简介**：Epic Games 开源的 Windows 原生图形化调试器：面向「巨型程序」做多进程多线程调试，并附带自研调试信息格式 RDI 与一个专为超大工程优化的 RAD 链接器（调试信息达数 GB 时链接快 50%）。

**仓库信息**
- 地址：https://github.com/EpicGames/raddebugger
- 类目：工程实践/工具链 ｜ 语言：C ｜ Stars：8.2k（8179）｜ 近期增量：+279 ⭐ 日榜 / +448 ⭐ 周榜
- 协议：MIT ｜ 官网 / 文档：GitHub Releases（README 为技术综述，使用手册随 release 包提供）

**核心功能**
- **原生图形化调试器**：用户态、多进程、多线程；当前支持本机 Windows x64 + PDB，官方路线图规划扩展到原生 Linux 与 DWARF。
- **自研调试信息格式 RDI**：调试器解析自定义的 RAD Debug Info，而非直接吃 PDB / DWARF；现有工具链产出的 PDB（以及后续带 DWARF 的 PE / ELF）**按需转换**成 RDI，避免运行时反复解析原始格式。
- **radbin 转换与转储工具**：在原生调试信息格式与 RDI 之间做转换，也可导出 RDI 内容的文本 dump；通过调试器的 `--bin` 参数也能直接调用。
- **RAD Linker**：面向 x64 PE / COFF 的高性能链接器，为「超大可执行文件」优化：实测调试信息达数 GB 时链接时间缩短 50%；命令行语法与 MSVC 完全兼容，可选原生生成 RDI——顺带绕开超大工程里 32 位内部表溢出导致 PDB 损坏的问题。
- **为巨型链接场景专门优化**：官方直接用「调试信息多 GB」的用例做基准，正是普通链接器与调试器最容易顶不住的地方。
- **大页内存支持**：为巨型进程的调试做内存布局优化（README 说明 Windows 下大页若使用不当会很快造成内存碎片）。

**技术栈**
纯 C 实现（含自研 layer 代码生成），Windows 平台；用 MSVC C/C++ Build Tools v15(2017)+ 或 Clang 构建，配合 Windows SDK；构建脚本 `build.bat`（release 模式编译时间显著更长，可指定 `radlink` / `radbin`）；产出 `raddbg.exe` 及配套工具，README 内含 RDI 格式与链接器的设计说明。

**适用场景**
在 Windows 上调试超大 C/C++ 工程（游戏引擎、CAD、图形应用）的开发者；需要处理「PDB 过大 / 调试信息溢出」这类工具链极限问题的团队；想研究调试器与链接器内部实现（调试信息格式设计、DWARF / PDB 解析）的工程师；追求高速链接的超大单体构建。

**推荐理由**
- **出自实战工具链而非玩具**：目标就是「巨型程序」这一类其他调试器容易顶不住的场景，并且把 RDI 格式与 RAD Linker 一并开源——价值不止一个调试器。
- **用真实极限做基准**：官方直接给「调试信息数 GB 时链接快 50%」这类可验证数字，说明优化方向来自真实痛点。
- **工程完整度高**：MIT 协议、预编译 release 二进制可直接下载、README 是完整技术综述（含 RDI 与链接器设计）、构建步骤细到编译器版本。

> **注意**：① 官方明确标注处于 **ALPHA**，功能与稳定性都在演进中，重要项目上建议与现有调试器配合使用；② 当前仅支持**本机 Windows x64 + PDB**，跨平台与 DWARF 仍在路线图上，非 Windows 用户暂时只能作为技术参考；③ 自行构建需要 MSVC Build Tools 与 Windows SDK；④ README 特意说明它**不含使用手册**——使用说明随 release 包或本地 `build` 目录提供，别只看 GitHub 首页。

> **一句话理解**：像给「大件货物」专门修通道：普通调试器相当于标准门框，程序一大就卡住；它的做法是从链接器开始就把门框加大——自研调试信息格式 + 为 GB 级调试信息优化的链接器。

---

## 4. claude-mem —— Agent 持久记忆系统

**一句话简介**：给编码 Agent 的持久记忆系统：把会话里发生的一切自动捕获、用 AI 压缩成结构化的「观察」与摘要，存进本地 SQLite + 向量库，下次会话直接检索复用——不用再反复给 Agent 讲项目背景。

**仓库信息**
- 地址：https://github.com/thedotmack/claude-mem
- 类目：AI Agent 及基础设施 ｜ 语言：TypeScript ｜ Stars：98.7k（98713）｜ 近期增量：+670 ⭐ 日榜 / +3,153 ⭐ 周榜
- 协议：Apache-2.0 ｜ 官网 / 文档：docs.claude-mem.ai

**核心功能**
- **全生命周期自动捕获**：5 个生命周期 Hook（SessionStart、UserPromptSubmit、PostToolUse、Stop、SessionEnd，共 6 个脚本）覆盖一次会话的完整过程，不需要你手动记录。
- **把过程压缩成记忆**：会话中的动作与结论被压缩为结构化「观察（observations）」与摘要，而不是原样堆日志——这是它区别于「把 transcript 存下来」的关键。
- **本地存储与混合检索**：SQLite 存会话 / 观察 / 摘要，Chroma 向量库提供语义 + 关键词的混合检索；Worker Service 是 Bun 管理的本地 HTTP API，带 Web 阅读界面与搜索端点。
- **3 层 MCP 检索省 token**：`search` 只返回带 ID 的紧凑索引（约 50–100 token/条）→ `timeline` 给出时间线上下文 → 只对筛出来的 ID 调 `get_observations` 取全文（约 500–1000 token/条）；官方称「先过滤、再取全文」可省约 10 倍 token。
- **mem-search 技能**：用自然语言查询记忆，采用渐进式披露（progressive disclosure）：先给线索，再按需深入。
- **安装简单、适配面广**：`npx claude-mem install --ide <ide>` 一条命令装；支持 Claude Code、Grok Bot 等；提供 20+ 语种 README 与独立文档站（配置 / 开发 / 分支策略 / 排障）。
- **迭代节奏快**：README 徽章显示版本已到 v13.34.2，属高频发布、持续维护的项目。

**技术栈**
TypeScript（Node.js ≥ 20）+ Bun（运行时与进程管理，缺失时自动安装）；SQLite 3 做持久化（内置），Chroma 向量库配合 uv 管理 Python 侧向量检索依赖（缺失时自动安装）；通过 MCP 暴露 4 个检索工具；仓库体量较大（包含文档站与多语言文档）。

**适用场景**
长期用 Claude Code 等编码 Agent 做跨天 / 跨周项目的开发者（新会话总要重新交代上下文的痛点）；希望 Agent 记住「上次那条 bug 是怎么修的」的团队；研究 Agent 记忆分层与检索成本优化的人；需要本地、可审计（数据不出本机）记忆方案的组织。

**推荐理由**
- **解决的是编码 Agent 最真实的摩擦点**：上下文遗忘。它不是往 prompt 里塞更长的历史，而是把历史**压缩成可检索的记忆**，从「塞满窗口」变成「按需取用」。
- **检索设计上非常讲究成本**：3 层渐进式检索把「先过滤、再取全文」制度化，官方给出约 10× token 节省的量化口径——在长会话场景里这是实打实的开销。
- **本地优先 + 生态适配广**：SQLite + 本地向量库存本机，Worker Service 是本地 HTTP API；MCP 工具与技能形态可被多种 Agent 复用，且提供 20+ 语种 README 与独立文档站。

> **注意**：① 依赖链较长（Node 20+、Bun、uv、SQLite、Chroma），首次安装虽会自动补装，但企业内网 / 受限环境最好提前准备；② 版本已到 13.x，属快速迭代期，跨大版本升级前先看仓库的分支策略与变更说明（区分 stable 与 core-dev / community-edge）；③ 记忆内容会被发往你配置的模型做压缩，涉及敏感代码库时先确认数据流向与保留策略；④ 仓库体积很大（含文档站与多语言 README），克隆前注意磁盘占用。

> **一句话理解**：像给 Agent 配了一位会自动写工作日志、还能按关键词翻旧账的助理：你只需问「上次那个认证 bug 怎么解的」，它先递一张索引卡片，你圈出相关的几条，它再把详情拿给你——而不是每次都把整本日志搬到你面前。

---

## 5. text-to-cad —— 给 Agent 装上 CAD

**一句话简介**：给 Agent 装上 CAD 能力：以插件 / 技能形态把本地 3D 建模工作流接进 Claude Code、Codex、Cursor 等 Agent，直接产出 STEP / GLB / STL / 3MF 文件，还能做面向制造的设计检查、出工程图并对接 3D 打印 / 钣金 / CNC 服务。

**仓库信息**
- 地址：https://github.com/earthtojake/text-to-cad
- 类目：AI Agent 及基础设施 ｜ 语言：Python ｜ Stars：18.6k（18554）｜ 近期增量：+1,898 ⭐ 周榜
- 协议：MIT ｜ 官网 / 文档：texttocad.dev

**核心功能**
- **真 CAD，不是网格玩具**：以 build123d + Open CASCADE 为内核，输出的是带精确几何的 **STEP 工程文件**，而非只有三角面的 STL。
- **多格式产出**：STEP、GLB、STL、3MF 四种，覆盖工程交换、渲染与 3D 打印的不同用途。
- **可制造性检查（DFM）**：生成后自动做面向制造的设计校验，把「画得出来但造不出来」的问题提前暴露。
- **工程图生成**：可产出工程图，供打样与加工沟通使用。
- **对接制造服务**：连接主流 3D 打印、钣金与 CNC 加工服务，让「建模 → 下单」在同一次 Agent 会话里完成。
- **广谱 Agent 适配**：支持所有支持插件或 skills 框架的 Agent，包括 Claude Code、Codex、Cursor、Gemini、Grok；Claude Code / Claude Desktop / Codex / Cursor 各有独立的安装与更新命令。
- **交互式查看**：在能显示 app view 的客户端里以 viewer card 呈现模型（可旋转、可加入 prompt）；终端环境则给一个在浏览器 CAD Viewer 打开的链接。
- **MCP 双形态**：既可装插件（带 skills），也可只装 MCP 服务（`cadgen mcp`），让不支持插件的 Agent 也能用。
- **工程规范**：GitHub Actions 测试工作流、PyPI 包（`cadgen`）、独立文档站（texttocad.dev）、多 Agent 的安装 / 更新 / 重装说明齐备。

**技术栈**
Python 3.11+ 的 `cadgen` 包（PyPI 发布），CAD 内核为 build123d 0.11 + Open CASCADE 7.9；通过 uv / uvx 分发与运行（首次运行下载 CAD 运行时，需联网）；配套 Node.js 20+ 的文档站；插件形态基于 skills 框架，兼容 Claude Code、Codex、Cursor 等；同时提供 MCP 服务器模式。

**适用场景**
需要「用自然语言改 CAD 模型」的机械 / 硬件工程师与产品设计者；把建模纳入 Agent 自动化的团队（例如按参数批量出件、按需求出图）；需要快速生成可打印件或钣金件的创客与初创硬件团队；想给自家 Agent 增加 3D 输出能力的开发者。

**推荐理由**
- **补上了「Agent 只会写字」到「Agent 能出图纸」的这一段**：精确几何 STEP + DFM 检查 + 制造服务对接，是少见的端到端能力（描述 → 模型 → 可制造性 → 下单）。
- **内核选型靠谱**：build123d + Open CASCADE 是成熟的参数化 CAD 与几何内核组合，产出模型能被主流 CAD 软件与工厂侧接受，而不是只能在自家查看器里看。
- **落地门槛低**：四种 Agent 的安装 / 更新命令写得很细，PyPI 有包、有 CI 测试、有独立文档站，MIT 协议，属于即装即用的一类。

> **注意**：① 首次使用需要联网下载 CAD 运行时（体积不小），离线环境要提前准备；② 依赖 uv / Python 3.11+，环境不满足时需先装 uv；③ **默认开启使用统计与崩溃上报**（随机 ID，不含你的文件 / 路径 / prompt），可用 `uvx cadgen telemetry off` 关闭——数据敏感场合先关掉；④ 生成结果属「辅助建模」，涉及公差、材料与安全关键件时仍需专业工程师复核，不要直接照图投产。

> **一句话理解**：像把一位「会写代码的建模师」请进对话：你说「做个能夹住 20mm 方管的支架，壁厚 3mm」，它直接给你一个能用 CAD 打开、还能送去 3D 打印的 STEP 文件，而不是给你一段文字描述。

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

- 候选池：日榜 9 条 + 周榜 11 条，去掉 4 个两榜重叠（`boykopovar/AnyPS5`、`EpicGames/raddebugger`、`thedotmack/claude-mem`、`mattpocock/skills`），共 **16** 个候选；逐一核对 total stars、近 30 天提交、License、fork / 归档状态后入选 5 个。
- 类目配额：应用项目 ×1、算法/模型 ×1、工程实践/工具链 ×1、AI Agent 及基础设施 ×2 —— 覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：AGPL-3.0 / GPL-2.0 / MIT ×3，均为明确 License；5 个仓库都有 README 正文，其中 4 个带独立文档站或完整技术综述。
- 去重检查：与第 1 期（hindsight / open-code-review / WeKnora / scriptc / quiche）和第 2 期（univer / colibri / claude-code-templates / orca / cua）均无重叠，基线为 `archive/index.json`。
- 说明：本期「算法/模型」类目由 `boykopovar/AnyPS5` 承担（二进制重链接 / 着色器重编译方向）；榜单当日缺少标准的模型 / 预训练类项目，因此未强行凑数，宁缺毋滥。

**本期按规则排除的候选**

- `mattpocock/skills`：个人 `.agents` 目录直出的技能集合，属资源聚合型（非具体项目），按「非 awesome / 资源聚合列表」排除。
- `liquidslr/system-design-notes`：读书笔记型教程大纲，且最近提交为 2026-08-12，超出 30 天活性窗口。
- `pablostanley/yoinks`：最近提交 2026-07-17，超出 30 天活性窗口。
- `cursor/plugins`：License 未标注，不满足「License 明确」要求。
- `storytold/artcraft`：License 标记为 NOASSERTION（不明确），且仓库体积约 1.3GB。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-09 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
