# 每日 GitHub 精选 · 2026-10-26（第 13 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [pollen-robotics/microduck](https://github.com/pollen-robotics/microduck) | 应用项目 | Rust | 11.8k | 日榜 +647 ⭐ |
| 2 | [jub0t/Concat](https://github.com/jub0t/Concat) | 应用项目 | Rust | 11.6k | 建库 62 天 ≈+1,300 ⭐ 周均（估算） |
| 3 | [deeplethe/utopia](https://github.com/deeplethe/utopia) | 算法/模型 | Rust | 8.5k | 建库 80 天 ≈+750 ⭐ 周均（估算） |
| 4 | [coollabsio/coolify](https://github.com/coollabsio/coolify) | 工程实践 | PHP | 64.5k | 日榜 +152 ⭐ |
| 5 | [TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents) | AI Agent | Python | 114.7k | 日榜 +381 ⭐ |

---

## 1. Microduck —— 25 厘米双足机器人把「大脑」整层开源了：7 个 Rust 守护进程 + 50Hz 神经策略控制环

**一句话简介**：开源机器人项目常见的是 CAD 图纸和一堆 ROS 包，真正难的那层——**实时控制环、OTA 更新、故障回滚**——往往被藏起来。Pollen Robotics（Reachy 机械臂的团队）把微鸭的这层整个放了出来：`robotd` 管 50Hz 控制环与电机总线，`updaterd` 装签名 release 并在自检不通过时自动回滚，`mediad` 用 WebRTC 推摄像头，七个守护进程用同一条 JSON-RPC 契约通信。策略不是手写步态，而是在隔壁 `microduck_rl` 里用 MuJoCo + PPO 训出来、导出 ONNX 直接上板——一条完整的 sim2real 链路，从仿真到 800 克的实体鸭子。

**仓库信息**
- 地址：https://github.com/pollen-robotics/microduck
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：11.8k（11753）｜ 近期增量：日榜 +647 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：pollen-robotics.com/microduck 官网（可下单/硬件资料）+ docs/robot/cheatsheet.md 全命令速查 + docs/design/architecture.md 一页纸系统设计（逐部件分页）+ docs/project/ 事故与待解决问题记录 + GitHub Actions CI + 正式 release 标签（如 daemon-dev-ground-grasp-x，更新可回滚可钉版本）+ 配套 microduck_rl 训练仓（MuJoCo/PPO/domain randomisation/ONNX 导出）+ scripts/duck-sim 仿真器

**核心功能**
- **七个守护进程 + 一条 JSON-RPC 契约**：`robotd` 拥有控制环与电机总线，`updaterd` 负责签名更新与健康门禁，`configd` 管 Wi-Fi 与身份，`btd` 是手机用的蓝牙通道，`padd` 读手柄，`mediad` 走 WebRTC 出画面，`tofd` 供深度传感器。App、控制台、手柄、你自己的脚本发的都是同一套调用，没有第二套私有接口。
- **50Hz 控制环 + 15 个舵机**：神经网络策略直接输出关节目标，控制环以 50Hz 稳定下发——这是「像生物一样走路」和「像机床一样抖动」的分界线。
- **换个策略就是换个技能**：走路、装轮子滚（roller mode）、低头用喙捡东西、被踢翻自己站起来、坐下、踢球、嘎嘎叫，都是加载不同 ONNX 策略的结果，不是写死的动画。
- **更新不怕变砖**：每次更新都验证签名、跑完健康检查才提交，不健康就回滚，还能把版本钉住——机器人产品化的真痛点，它写进架构里了。
- **没有鸭子也能开发**：`scripts/duck-sim` 让真实的守护进程跑在 MuJoCo 里的虚拟身体上，可以开一只窗口看，也可以起四只当机器登进去测。
- **决策都写下来了**：`docs/design/` 解释为什么这样设计，`docs/project/` 记录出过什么事、什么能堵住它——比 README 里堆徽章有用得多。

**技术栈**
Rust（单 workspace、不引框架），跑在 Rockchip RK3566 的 Linux 上；进程间一条 Unix socket 上的 JSON-RPC；策略来自 microduck_rl（MuJoCo + PPO + 域随机化，导出 ONNX）；Apache-2.0；GitHub Actions CI + 签名 release + 逐版回滚；文档按「你已经有鸭子 / 你在它上面做开发」两条线组织。

**适用场景**
想完整走一遍 sim2real 的机器人工程师（训练在 MuJoCo、部署到 800 克实机）；做嵌入式 Linux 多守护进程 + OTA 架构的团队（这套更新门禁可以直接当范本读）；具身智能/机器人课程的教学平台（能跑仿真、能上真机、代码量可控）；给孩子一台「可以改代码」的机器宠物。

**推荐理由**
- **它开源的是最难开源的那部分**：多数开源机器人给你结构和演示视频，微鸭给你实时控制环、进程编排、签名更新与回滚——这些才是把 demo 变成产品的分水岭。
- **sim2real 链路闭合且可复现**：训练仓、导出格式、加载路径、仿真器四者对得上：改一个奖励函数，能一路走到真机上看效果，这在开源里很稀缺。
- **工程细节值得逐页抄**：「健康检查不通过就回滚」「所有客户端共用一套 RPC」「事故写进 docs/project」——这三条能省掉很多团队半年的坑。
- **硬件真的能买**：不是只有代码的 PPT 项目，官网可下单；开源的是软件栈，意味着你买的是硬件、拿到的是一整套可改造的固件。

> **注意**：① **仓库是机器人端的软件栈，不是仿真玩具**：没有实体鸭子只能跑 `duck-sim`，完整体验要硬件；② 15 个舵机 + RK3566 单板的 BOM 不便宜，下单前先看清官网价格与地区；③ 预置策略是厂商训好的，想自己训要 GPU、MuJoCo 经验和 sim2real 调参耐心；④ 文档大量以「你已经有一台鸭子」为前提，纯软件读者会略过很多页；⑤ 2026-07 建库，daemon 契约与 API 仍可能变；⑥ 79 个 open issue 说明活跃，也说明边角没打磨完，别直接拿去做商业产品。

> **一句话理解**：像一家车厂把整车的行车电脑、线控总成和 OTA 通道全开源了：你可以只买车身，但真正值钱的是那套让 15 个关节在 20 毫秒内听话、还能安全升级的调度逻辑。

---

## 2. Concat —— 纯 Rust 的开源剪映替代品：本地 Whisper 字幕、声音克隆、4K 导出，还内置 MCP 让 Agent 剪片

**一句话简介**：剪映好用，但要账号、要上传、有水印、高级功能要订阅。Concat 把这些「附加条件」全砍了：**原生 Rust 引擎 + GPU 合成器**，素材只在你硬盘上，字幕用本地 Whisper、配音用本地 TTS 与几秒录音的声音克隆、抠像本地推理，装完从设置里下一次模型就能全程离线。更少见的是它把自己也做成了机器可用的工具——`concat --mcp` 起一个 MCP 服务器，Claude 这类 Agent 能直接建轨道、下字幕、导时间线；源码构建还额外带 gRPC 与 CLI。62 天 11.6k star、1.4k fork，说明「不想被订阅绑住」是真需求。

**仓库信息**
- 地址：https://github.com/jub0t/Concat
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：11.6k（11566）｜ 近期增量：建库 62 天 ≈+1,300 ⭐ 周均（估算）
- 协议：AGPL-3.0 ｜ 官网 / 文档：concatenate.pages.dev 官网（下载/系统要求/指南）+ 开发者文档站（JSON-RPC 与 gRPC 两种传输）+ docs/MCP.md 一步接入 Agent + CODE_SIGNING.md 说明为什么 Windows 包未签名、以及联网发了什么 + GitHub Actions CI（fmt/clippy/测试/构建）+ 逐版 release（v0.2.8，各平台安装包与校验和）+ 26 语种 README

**核心功能**
- **一切本地，且真的离线**：Whisper 字幕、TTS 与声音克隆、人物/物体抠像、100 个特效滤镜转场全部本地跑；模型一次性下载，之后断网可用，素材不出本机。
- **剪辑基本功不缺**：多轨多时间线、磁性时间线、切分/修剪/波纹/合并/冻结帧/变速、混合模式、裁切翻转，位置缩放旋转不透明度与特效参数都能打关键帧，自带曲线编辑器。
- **字幕与配音是主打**：本地 Whisper 按模型大小选精度直接上时间线，样式可套；配音可选免费本地音色，或用几秒录音克隆一个；一键降噪、增强人声、响度对齐。
- **导出规格够用**：H.264 / HEVC / AV1，最高 4K 60、10bit 色彩，代理与硬件解码保证 4K 时间线拖得动。
- **给 Agent 和脚本留了门**：`concat --mcp` 起 MCP server，一行配置接进 Claude 等 Agent；JSON-RPC API 给自动化脚本；源码构建还带 gRPC 与命令行工具。
- **五端同一份工程文件**：macOS（Intel/Apple Silicon）、Windows、Linux（deb/rpm/AppImage/Arch/Flatpak）、Android、iOS 侧载，同一 App、同一工程格式、26 种界面语言。

**技术栈**
Rust 1.93+（原生引擎、GPU 合成器、代理、硬件解码），编解码依赖 FFmpeg 7+，UI 与引擎同一个 cargo workspace；CI 跑 fmt、clippy（`-D warnings`）与测试；本地 AI 用 Whisper/TTS/抠像模型；AGPL-3.0-or-later；本地化字符串由 `scripts/locales.py` 统一维护。

**适用场景**
做短视频/Reels/Shorts 但不想被剪映订阅和水印绑住的创作者；需要批量、可脚本化出片的自动化流程（JSON-RPC / CLI）；想让 Agent 直接改片子（口播切片、自动加字幕）的开发者；对素材保密有要求、不能上传云端的团队（法务、医疗、内部培训）。

**推荐理由**
- **「不加水印不上传」不是口号而是架构**：本地 Rust 引擎 + 本地模型是硬约束下做出来的，不是把云端 API 换个皮——这也是它能在 62 天拿到 11.6k star 的原因。
- **把剪辑器做成了可编程对象**：内置 MCP server 这一步很少见：视频剪辑恰好是「步骤多、判断多、纯手工」的活，交给 Agent 编排的收益比聊天画图高得多。
- **工程规范不像个人项目**：CI 有 clippy `-D warnings`、26 语种 README、CODE_SIGNING.md 明说联网行为、逐版校验和——作者对「可信」这件事是有自觉的。
- **跨端覆盖罕见**：手机端也能剪同一份工程，对「拍了就发」的场景比桌面独占的工具顺手。

> **注意**：① **仍是 beta**：作者自己写「能用，但还有毛边」，215 个 open issue，别把重要交付压在上面做唯一工具；② 安装包未签名：Windows 需绕过 SmartScreen、macOS 首次要 `xattr -dr com.apple.quarantine`，企业环境会被策略拦；③ **AGPL-3.0**，闭源分发或做成 SaaS 前务必读清传染范围；④ 首次用字幕/配音/抠像要联网下模型，模型体积与磁盘占用按精度递增；⑤ Windows ARM 构建已暂停（见 issue #326）；⑥ 复杂多轨 4K 工程在弱机上仍会卡，官方建议开代理；⑦ 快捷键与操作逻辑仍会变，跟教程时要看版本号。

> **一句话理解**：像把一整间剪辑室塞进你的笔记本：字幕员（Whisper）、配音员（TTS）、抠像师都在本地待命，不用把素材寄给任何云；同时还把操作台的开关键（MCP）交给了 AI 助手。

---

## 3. Utopia —— 双时态知识图谱当底座：一个 Rust 二进制 + 一个 Postgres，能回答「2024 年 3 月那天条款是什么」

**一句话简介**：向量库和普通知识图谱优化的是「现在正确」，但企业真正难的问题是**「当时我们以为是什么」**。Utopia 把时间塞进底座：每条事实带两个时钟——在世界里何时成立、系统何时才知道；改错不覆盖，而是关掉旧版本并把新版本链上去，于是任何一次决策事后都能复盘出「依据是哪句、什么时候生效」。工程上它很克制：**一个 Rust 二进制 + 一个 Postgres**，全文用内置 Tantivy、向量进 pgvector、任务队列就是一张表，没有第五个中间件。本体（schema.org / PROV-O / W3C Org / FOAF / IOF Core）随二进制分发，公理能编译成前向链规则推导新事实，冲突分三类各给三条处置选项。

**仓库信息**
- 地址：https://github.com/deeplethe/utopia
- 类目：算法/模型 ｜ 语言：Rust ｜ Stars：8.5k（8539）｜ 近期增量：建库 80 天 ≈+750 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：utopia.bi 官网（含 philosophy 与 roadmap 长文）+ 仓库内 walkthrough（curl 跑通入库→提问→带证据回答）+ web/src/docs/mcp.md 的 MCP 工具清单 + 两套公开 benchmark（contracts 合同语料、scripts/bench 时序 QA）+ GHCR 多架构预构建镜像 + Discussions + 简体中文 README

**核心功能**
- **双时态是核心，不是插件**：两个时间轴：事实在现实世界生效的区间，和系统相信它的区间。修正一条付款条款不会抹掉历史，而是把旧条款「关闭」并把新事实链上去，边界可追溯。
- **一个二进制 + 一个 Postgres**：全文检索是编进二进制的 Tantivy，向量存 pgvector，任务队列是一张表，RRF 融合两路召回；整套可 air-gapped 离线跑。
- **入库覆盖真实企业格式**：PDF/DOCX/PPTX/XLSX/XLS/ODS/CSV/TSV/Markdown/HTML/纯文本，老编码自动识别；扫描件走 MinerU 或视觉模型，录音走带说话人标注的转写；网页、RSS、GitHub、Jira、Notion、WebDAV、S3 可定时同步。
- **实体消歧 + 人工复核队列**：三阶段合并：精确名/别名 → 向量相似 → 模型裁决可疑对；每次合并可撤销，低置信抽取、疑似重复、基数冲突都进 review 队列等人拍板。
- **本体驱动的推理与冲突检测**：五套本体包随二进制分发，公理编译成规则做前向链推导（默认关闭，因为错的公理推出错的事实）；事实冲突给「关旧/并存/拒绝」，公理违背（自环、非对称、传递环、基数）给「撤回/放宽/接受」——先查本体自身是否自相矛盾。
- **给 Agent 的手是「只读 + 提案」**：每个知识库一个 MCP server，Claude Desktop / Cursor 等可接；查的是「某实体在某日的事实」「两点之间的路径」「上周变了什么」，返回带稳定 ID 与证据；写入一律变提案进人工队列。
- **还能挂数据库问**：把 Postgres/MySQL/ClickHouse/Trino/Databricks/Snowflake 挂到知识库上，对话里同时查文档与表；映射方案由 Agent 提议、人确认（背后方法论文 Ontology2SQL 在 BIRD Mini-Dev 上刷到 SOTA）。

**技术栈**
Rust 单二进制 + Postgres（pgvector 存向量、Tantivy 内置全文、队列表）；Web UI 含系统控制台、图浏览器与本体工作台；Docker 镜像发布在 GHCR（linux/amd64 + linux/arm64）；LLM 走任意 OpenAI 兼容端点（DeepSeek/Qwen/GLM/Ollama/vLLM）；Apache-2.0；自带 contracts 语料与时序 QA 两套公开 benchmark 与端到端走查脚本。

**适用场景**
合同/采购链里需要回答「某年某月生效的是哪一版条款、出自哪次修订」的法务与合规团队；人事、财务、研发记录频繁更正，需要区分「当时的事实」与「后来才知道」的组织；要给 Agent 一个可信、带证据、可审计的知识底座的工程团队；机器人/监控场景把「某物 08:05 在哪」这类观测按时间推入图谱的开发者。

**推荐理由**
- **把「时间」当一等公民，切中了 RAG 的真短板**：主流 RAG 只能回答「现在文档里怎么写」，一问「当时怎么规定」就只能瞎编；双时态图谱让这类问题变成一次带区间的查询。
- **工程克制得少见**：一个二进制一个库就整套跑起来，容器镜像多架构现成，对比动辄要起五六个组件的 GraphRAG 方案，运维成本低一个量级。
- **治理链路是闭合的**：抽取→消歧→复核→冲突处置→推导→决策账本，每一环都留痕且可撤销；对「AI 结论要能被审计」的场景，这比模型精度更重要。
- **有公开 benchmark 而非只有截图**：合同语料与时序 QA 两套 bench 都在仓库里，能拿自己的数据先验证再决定要不要投入建模。

> **注意**：① **仍是 0.1.0-rc9（RC 阶段）**：schema、API、迁移路径都可能变，生产用先锁镜像 tag；② 不是「丢文档就出答案」的通用 RAG：要先接受本体 + 双时态的建模范式，冷启动得选本体包、确认术语，学习曲线明显陡于向量库；③ 抽取质量高度依赖你配的 LLM，弱模型会把脏事实写进图（有 review 队列兜底，但要人真的去看）；④ 「world model / 企业世界模型」是它的营销词，本质是时序知识图谱 + 决策留痕，别按仿真世界模型期待；⑤ 85 个 open issue，部分高级能力（决策智能、场景叠加推演）仍在路线图上未完成；⑥ 单机 Postgres 架构在超大规模图上有上限，先按自己的数据量做压测。

> **一句话理解**：像给公司的记忆装了一台「行车记录仪 + 时间机器」：它不只告诉你现在是什么，还能倒回 2024 年 3 月 15 日，调出那天生效的条款原文，以及当时我们以为的条款——两者不一样时，它能指出是哪次修订改的。

---

## 4. Coolify —— 自己服务器上的 Vercel：一条 SSH 接管机器，Git 推送即部署、360+ 一键服务、自动 HTTPS

**一句话简介**：「不想为一个小项目付 20 美元/月的平台费」是很多人的起点。Coolify 把云平台那块控制台搬到你的 VPS 上：**只要能 SSH 进去，不管是一台 5 美元的 VPS、一台二手服务器还是一块树莓派**，都能被它接管——Git 推送自动构建部署、PR 预览环境、自动申请 HTTPS、多服务器编排、数据库备份与定时任务。技术栈是 Laravel + Svelte 5，2021 年至今迭代到 v4.5.0，64.5k star / 5.8k fork 的社区规模说明它不是玩票。更关键的一条承诺：**停用 Coolify，已经跑起来的资源照旧运行、照旧可管理**——配置留在你的机器上，不锁死。

**仓库信息**
- 地址：https://github.com/coollabsio/coolify
- 类目：工程实践 ｜ 语言：PHP ｜ Stars：64.5k（64497）｜ 近期增量：日榜 +152 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：coolify.io 官网 + coolify.io/docs 完整文档（安装/服务器/资源/备份）+ 官网 philosophy 说明「永不收费墙」的立场 + Discord 与 GitHub Discussions + 一键安装脚本（仓库内 scripts/install.sh 可先审再跑）+ Coolify Cloud 托管版 + 正式 release（v4.5.0，2026-10-23）

**核心功能**
- **部署任何东西**：GitHub / GitLab / Bitbucket / Gitea 拉代码，构建走 Nixpacks、Railpack、Dockerfile、Docker Compose 或预构建镜像；静态站点、Node、Python、PHP、Go、Rust 都能直上。
- **360+ 一键服务与托管数据库**：Postgres/MySQL/MariaDB/Redis/Mongo 等带持久化卷与自动生成凭据，另有 360 多个一键服务模板，点一下就有。
- **推送即部署 + 预览环境**：每个 Git push 自动重建，可为 PR 生成独立预览域名，支持部署 webhook 与回滚到保留的历史镜像。
- **网络这层不用自己拼**：自定义域名、自动 HTTPS 证书（含续期）、反向代理、健康检查、容器网络与端口映射全部由面板接管。
- **多机运维视角**：一个面板管多台服务器，看部署与运行时日志、开容器终端、看资源曲线；备份、定时任务、环境变量与密钥、通知集中配置。
- **四种入口 + 团队权限**：Dashboard 之外还有 REST API、CLI、MCP，可以接进自己的流水线或让 Agent 触发部署；支持团队与角色权限。
- **不锁死这条最值钱**：所有配置存在你自己的服务器上，卸载面板后已部署的容器与数据仍在，迁移成本远低于 SaaS 平台。

**技术栈**
后端 Laravel（PHP），前端 Svelte 5 + Next.js（Inertia），目标服务器靠 Docker / Docker Compose 编排，SSH 下发指令；Apache-2.0；v4.5.0（2026-10-23）；一条 curl 安装脚本，源码在 scripts/install.sh 可先审；文档站 coolify.io/docs 覆盖安装、服务器、备份与故障排查。

**适用场景**
想用一台 VPS 跑十几个小项目、又不想逐个手写 compose 与 Nginx 配置的独立开发者；预算敏感但需要 PR 预览与自动部署的小团队（自托管替代 Vercel）；要把部署面收到内网/自有硬件的公司（合规、数据不出境）；想给客户交付「可自助部署」产品的 SaaS 团队。

**推荐理由**
- **成熟度经得起生产**：2021 年至今、v4.5.0、5.8k fork，功能矩阵（部署/数据库/备份/多机/权限）已经覆盖大多数自托管需求，不是半成品。
- **把「平台税」换成「运维时间」的划算交易**：同样功能在托管平台按月计费，Coolify 只花机器钱；对长期跑、数量多的项目，成本差距会随规模放大。
- **反锁定设计值得学**：配置留在本机、卸载后资源照旧——这条产品决策本身就值得做基础设施的人抄。
- **生态与文档完整**：官方文档、Discord、Discussions 齐全，360+ 服务模板降低了「自己写 compose」的门槛。

> **注意**：① **官方推荐架构是「一台跑面板 + 若干台跑业务」**，单机 all-in-one 只适合玩票，把面板和业务混在一台上，业务一崩面板也失联；② 面板自己也要备份——它挂了不影响已部署资源，但管理面和历史配置会丢；③ 363 个 open issue：功能面很宽，边角 bug 不少，生产环境建议锁 release 版本、别追 main；④ 免费版没有官方 SLA，要托管与支持得用付费的 Coolify Cloud；⑤ 自托管意味着 CVE、系统补丁、证书续期都得你自己跟，安全责任在你；⑥ 团队/细粒度权限仍在迭代，多租户场景先验证。

> **一句话理解**：像给你的 VPS 装了一块「云厂商控制台」：点几下就有自动 HTTPS、一键数据库和 Git 自动部署，账单从每月订阅变成了电费——代价是机房里的活也得你自己干。

---

## 5. TradingAgents —— 把一家交易公司拆成 LLM 团队：四个分析师并行、多空研究员对辩、风控能否决、经理签字

**一句话简介**：单个 LLM 问「这只票能不能买」，得到的往往是一段四平八稳的废话。TradingAgents 换了个思路：**把投研流程本身做成多智能体图**——四个分析师（基本面、情绪、新闻宏观、技术指标）各自带工具并行跑完才进入研究辩论，看多与看空研究员结构化对辩，Trader 给出时机与仓位，风控团队评估波动与流动性，最后由组合经理批准或否决。有 arXiv 论文（2412.20138）、v0.7.0 版本、22k fork，更难得的是它在「可复现」上下了功夫：point-in-time 数据保真（分析日之后才发布的数据一律不可见）、决策日志与 LangGraph checkpoint 续跑、回测按每次决策后的第一个收盘价结算。

**仓库信息**
- 地址：https://github.com/TauricResearch/TradingAgents
- 类目：AI Agent ｜ 语言：Python ｜ Stars：114.7k（114746）｜ 近期增量：日榜 +381 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：arXiv 2412.20138 论文 + CHANGELOG.md 逐版变更说明（v0.2.0 → v0.7.0） + 官方 CLI（`--ticker` / `--date` 免交互跑批） + Docker Compose 一键起 + 每版 GitHub Release 附 wheel 包 + 报告导出为单页 HTML + Discord 社区 + 八语种 README（含简体中文）

**核心功能**
- **四个分析师并行出报告**：基本面（财报与指标、内在价值与红旗）、情绪（新闻标题 + StockTwits + Reddit 聚合成一个情绪读数）、新闻宏观、技术面（MACD/RSI 等形态），各跑各的工具，全部完成才进辩论。
- **多空研究员结构化对辩**：看多与看空研究员拿着同一批分析师报告互相攻击，权衡收益与风险，输出不带结论偏好的研究结论。
- **交易员 + 风控 + 组合经理三级把关**：Trader 定时机与仓位，风控团队按波动、流动性等风险因子评估并调整策略，组合经理批准后订单才发往模拟交易所——「有人能否决」是这套设计的核心。
- **可复现性被认真对待**：point-in-time 保真覆盖 FRED 宏观、社交情绪与决策记忆；回测只在分析日可见数据上运行；每次运行的设置写进报告；checkpoint 可断点续跑。
- **模型与数据源自由组合**：多供应商（OpenAI/Anthropic/Google/Qwen/DeepSeek/GLM/Mistral/Bedrock/Ollama/任意 OpenAI 兼容端点），还能给不同模型档位配不同 provider，让分析师与管理层跑不同模型。
- **跑批与出报告都顺手**：CLI 用 `--ticker` `--date` 免交互跑网格回测，报告导出成单页 HTML，每版 release 附 wheel 便于装进自己的流水线。

**技术栈**
Python 3.11+，LangGraph 编排多智能体图（含 checkpoint 断点续跑），多供应商 LLM 适配层；数据源含 Yahoo Finance、Alpha Vantage、FRED、Polymarket、SEC EDGAR、Reddit/StockTwits；Docker Compose 部署；CI 门禁；Apache-2.0；v0.7.0，每版附 wheel 与 CHANGELOG。

**适用场景**
研究多智能体协作与「辩论式推理」的研究者与算法工程师（这是它最主要的定位）；想搭投研辅助工作流、但人工做尽调的团队（当信息汇聚与初筛工具用）；教学场景（一家交易公司的角色分工可以完整映射成一张图）；要学 LangGraph 复杂图编排与状态管理的开发者。

**推荐理由**
- **多智能体不是堆角色，是有对抗的结构**：「分析师 → 多空辩论 → 交易 → 风控否决 → 经理签字」这条链上每一步都有制衡，比「让十个 Agent 各写一段再汇总」更接近真实决策，也更容易观察偏差从哪来。
- **对「回测作弊」有清醒认识**：point-in-time 保真、按决策后首个收盘价结算、把运行设置写进报告——多数金融 Agent 项目在这三点上装死。
- **论文 + 版本 + wheel 三重可核验**：有 arXiv 论文可读方法，有 CHANGELOG 可看演进，有 wheel 可直接装，评估成本比只有 README 的项目低很多。
- **是学 LangGraph 的好样本**：并行分析、辩论循环、条件路由、checkpoint 续跑、结构化输出，一张图里几乎覆盖了 LangGraph 的主要用法。

> **注意**：① **作者明确写着「仅用于研究」**，不构成投资建议；把它当实盘信号源，亏钱是设计外行为；② 结果强依赖所选模型、temperature 与数据质量，同一 ticker 跑两次结论可能不同——这是多智能体的固有方差，不是 bug；③ 订单只发往**模拟交易所**，接真实券商要自己解决 API、合规与风控，仓库不提供；④ 一次完整运行要烧相当多 token（四分析师并行 + 多轮辩论 + 三级决策），成本先算清再跑网格回测；⑤ 22k fork 里大量是「fork 了没改」的噪声，fork 数不能当质量指标；⑥ 最近提交 2026-10-16，节奏稳但不是每天动，新模型支持会滞后于厂商发布；⑦ 金融数据源多数需要自行申请 API Key，部分有免费额度上限。

> **一句话理解**：像把一家小投研团队塞进一台服务器：四个分析师各看各的盘、两个研究员当庭对辩、风控在旁边随时喊停、经理最后签字——只是每个角色都是一次 LLM 调用，所以「开会」是要按 token 付费的。

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

- 候选池：Trending 日榜 11 条 + 周榜 14 条（合并去重后 21 个），其中 9 个已在往期推送、7 个属技能/插件合集；新增可用候选仅 5 个，靠 4 组 Search API 查询补池（`created:>2026-08-20 stars:>4000 pushed:>2026-10-18`、`topic:llm created:>2026-07-01 stars:>8000`、`topic:inference created:>2026-05-01 stars:>3000`、`topic:machine-learning created:>2026-06-01 stars:>3000`），另对 9 个单仓逐个核验 License / 活跃度 / release。
- 类目配额：应用项目 ×2（Microduck、Concat）、算法/模型 ×1（Utopia）、工程实践 ×1（Coolify）、AI Agent ×1（TradingAgents）——覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：Apache-2.0 ×4（Microduck、Utopia、Coolify、TradingAgents）+ AGPL-3.0 ×1（Concat）。5 个仓库均有完整 README 正文与正式 release（Microduck 用 release 标签而非语义版本号，Concat v0.2.8、Utopia v0.1.0-rc9、Coolify v4.5.0、TradingAgents v0.7.0）；Microduck / Concat / Utopia（GHCR 镜像 + bench）/ TradingAgents 均有 CI 或公开 benchmark，Coolify 有完整文档站与 5.8k fork 社区。
- 去重检查：与往期十二期（09-28 至 10-23，共 60 个仓库）均无重叠，基线为 `archive/index.json`；本期五个仓库无同名双仓与同组织家族问题（storytold 家族已整族排除）。10-24、10-25 两期未运行，本期为第 13 期，归档日期链存在两天缺口，已在 index.json 中如实反映。
- 数据口径：total stars、License、最近提交、release 取自 `gh api repos/*`（5 个仓库 `pushed_at` 为 10-16 至 10-26，全部在 30 天活性线内）；Microduck（+647）、Coolify（+152）、TradingAgents（+381）为 Trending **日榜原始数字**；Concat（62 天 ≈1,300/周）、Utopia（80 天 ≈750/周）未上榜，增量由「累计 star ÷ 建库天数」换算，速览表统一标注「估算」，不与原始数字混用。
- 本期风险提示（与功能同等看待）：`Concat` 仍是 beta、安装包未签名、且为 AGPL-3.0，商用分发前必须评估传染范围；`Utopia` 处于 0.1.0-rc9，schema 与 API 会变，且建模范式学习曲线陡；`Coolify` 363 个 open issue、免费版无 SLA，自托管的安全补丁要自己跟；`TradingAgents` 作者明示仅用于研究、只对接模拟交易所、单次运行 token 成本高；`Microduck` 需要实体硬件才能完整体验，BOM 不便宜，且 daemon 契约仍可能变。

**本期按规则排除的候选**

- `debpalash/VoiceStudio`（日 +1,592）、`anomalyco/opencode`（周 +5,921）、`stablyai/orca`（周 +9,622）、`heygen-com/hyperframes`（周 +5,612）、`akitaonrails/ai-memory`（周 +3,254）、`Comfy-Org/ComfyUI`（周 +4,790）、`vllm-project/vllm`（周 +1,445）、`pingdotgg/t3code`（周 +1,770）：热度全部达标，但均已在往期推送，按 `archive/index.json` 去重基线（前 12 期 / 60 个仓库）排除。
- `cloudflare/security-audit-skill`（日 +2,878 / 周 +15,072）、`anthropics/knowledge-work-plugins`（周 +2,790）、`anthropics/claude-plugins-official`（周 +2,245）、`android/skills`（周 +1,070）、`multica-ai/andrej-karpathy-skills`（周 +2,937）、`Nutlope/hallmark`（34.1k，「anti-AI-slop design skill」）、`AgriciDaniel/claude-seo`（21.0k，26 个子技能 + 19 个子 Agent）、`ruvnet/ruflo`（周 +2,987）、`Graphify-Labs/graphify`（周 +6,903，实质以 Claude Code skill 分发）：产物形态是 agent 技能/插件/提示词集合，属资源聚合型；`security-audit-skill` 且最后提交 09-14 已超 30 天活性线。按既有口径整类排除。
- `pbakaus/impeccable`（87.9k，Rust，Apache-2.0，日 +1,092）：本期热度最高的新面孔，但产品实质是「给 AI harness 用的设计语言/规则包 + 引擎」，与上条同一类产物形态，按口径排除——它的增量说明「让 Agent 输出好看」已成显性需求，值得单独关注。
- `storytold/photocraft`（72.9k）、`pdfcraft`（17.9k）、`filmcraft`（16.3k）、`wordcraft`（16.1k）、`lightcraft`（14.7k）、`vectorcraft`（10.7k）：同一组织的纯 Rust 重写家族，延续 10-14 期口径（同源同质只取其一，`artcraft` 已推送），整族不再重复入选。
- `Ebony-Vinyl/dsh-our-free-model`（43.1k，建库 32 天）、`hypit-ai/hypit`（25.6k，NOASSERTION）、`Gathin23/cleanyourtv`（35.6k，NOASSERTION）、`trailhq/Trail-Code`（10.8k，无正式 release、250 open issue 待观察）：分别按「合规存疑」「License 不明确」「发布成熟度不足」排除。
- `eternity4719/HowToLiveBetter`（69.1k）与 `cdyforever/how-to-live-better`（13.4k，License 缺失）：书籍/指南在线阅读页，非可运行软件项目，按「非纯教程大纲」口径排除。
- `makecindy/cindy`（5.0k，TS，Apache-2.0，日 +675）、`Renhuai123/ziwei-doushu`（7.7k，TS，MIT，日 +199）：指标与 License 均合格，但前者 star 总量偏低且与本期 TradingAgents 的 Agent 名额重叠，后者属领域排盘算法引擎、受众过窄，本期让位。
- `Human-Agent-Society/reef`（7.7k，Python，Apache-2.0，CI + PyPI + 文档站 + v0.1.3，建库 56 天 ≈970/周估）：10-20 期列为优先候选的「持续自改进 Agent 基础设施」，本期再次因 Agent 类目配额（TradingAgents 占位）让位，继续留作下期首选。
- `KnifeLemon/Filee`（12.4k，C#，MIT，建库 27 天 ≈3,200/周估）、`KKKKhazix/AIHOT`（8.6k，TS，MIT）、`mizorewww/laya-mlx`（7.0k，Python，Apache-2.0）：均合格，但应用/算法名额已由 Microduck、Concat、Utopia 占满，按类目配额让位。
- `JetBrains/thinkrail`（1.9k，日 +51，Apache-2.0）、`coollabsio/coolify` 之外的泛用 PaaS 候选：thinkrail 日增量 51 未过 80 门槛、star 也未到 1k×(增量) 的合理热度，按热度规则排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-26 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
