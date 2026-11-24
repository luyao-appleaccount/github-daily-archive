# 每日 GitHub 精选 · 2026-11-24（第 28 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [rddmwmddr/android-ad-cleaner](https://github.com/rddmwmddr/android-ad-cleaner) | 应用项目 | Python | 8.9k | 周均 ≈2,000 ⭐（建库 31 天） |
| 2 | [wquguru/cicada](https://github.com/wquguru/cicada) | 应用项目 | Swift | 2.6k | 周均 ≈810 ⭐（建库 23 天） |
| 3 | [RainBowLuoCS/Gamer](https://github.com/RainBowLuoCS/Gamer) | 算法/模型 | 多语言（权重与文档为主） | 1.4k | 周均 ≈400 ⭐（建库 25 天） |
| 4 | [haydenschmitty/floorplan](https://github.com/haydenschmitty/floorplan) | 工程实践 | JavaScript | 6.5k | 周均 ≈1,620 ⭐（建库 28 天） |
| 5 | [KKKKhazix/agent-autoloop](https://github.com/KKKKhazix/agent-autoloop) | AI Agent | TypeScript | 6.4k | 周均 ≈2,130 ⭐（建库 21 天） |

---

## 1. 肉呆去广告 —— 给国产安卓手机一键关停系统级广告

**一句话简介**：国产手机系统的广告散落在通知、热搜、开屏、快应用几十个角落，各家关法还不一样——这个项目把「按机型逐个找开关」的脏活全部替你干了。

**仓库信息**
- 地址：https://github.com/rddmwmddr/android-ad-cleaner
- 类目：应用项目 ｜ 语言：Python ｜ Stars：8.9k（8858）｜ 近期增量：周均 ≈2,000 ⭐（建库 31 天）
- 协议：MIT ｜ 官网 / 文档：官网 ahuamiao.com + 介绍站 + 机型图文教程 + CHANGELOG 与社区问题处理记录 + GitHub/Gitee 双源 Release（安装包已签名公证）

**核心功能**
- **插线即用的桌面客户端**：Mac/Windows 客户端连上手机点几下按钮就行，不需要 Python 也不需要 AI 工具；安装包已通过苹果公证、Windows 提供安装版与免安装版，国内可走 Gitee 下载。
- **手机版 APK 免电脑**：安卓 11+ 装手机版即可本机执行，无需连电脑与无线调试配对；已支持 Sui；纯血鸿蒙接入通道也已开放（鸿蒙真机复测进行中）。
- **精细到通知渠道的处置**：营销通知按渠道勾选、服务类通知默认不动，避免「关广告把验证码也关了」；v0.4.5 刚重写了通知渠道处理层，先判断再统一动手，修复华为上的误关问题。
- **可还原、有备份、可审计**：所有改动可一键还原，已有备份保留；每步执行有实时日志与结果反馈，反馈自动附诊断信息；也支持让 AI 智能体按文档代为执行。

**技术栈**
Python 引擎 + adb/无障碍系统能力；桌面客户端覆盖 macOS（含 Intel）与 Windows 10/11，手机版为独立安卓应用；MIT 协议，Gitee 提供国内下载源。

**适用场景**
被 MIUI/EMUI/ColorOS 等国产系统广告、热搜、营销推送困扰又不想 root 的用户；给家人手机批量「除广告」；研究各厂商系统设置差异与无障碍/ADB 自动化实现的开发者。

**推荐理由**
- **痛点全民级，方案克制**：不 root、不改系统、可还原，所有操作都在系统开放能力之内；31 天 8.9k star，是中文社区真实需求驱动出来的项目。
- **机型适配是真正的护城河**：华为、荣耀、小米、vivo 等各家关闭路径不同，项目按机型维护脚本与图文教程，社区问题处理记录逐条公开，出错与修复都透明。

> **注意**：只能关系统层的广告与推荐，第三方应用（如短视频 App）内的广告无能为力；操作涉及系统设置，建议严格按机型教程执行并保留备份；鸿蒙通道尚未真机复测；仓库 open issue 较多（220+），遇到异常先查社区问题处理记录；用完建议关闭开发者模式。

> **一句话理解**：像请了个熟悉各品牌手机「设置暗门」的管家：插上线他照着机型清单逐项把广告开关关掉，还记下动过哪些地方——后悔了随时一键还原。

---

## 2. 知了 Cicada —— 任意会议直播的实时双语字幕与同传

**一句话简介**：会议软件不开放字幕、跨国会听不懂、听完了纪要没人写——它一个工具把「听、译、说、记」四件事全包了，而且别人在会上根本察觉不到它的存在。

**仓库信息**
- 地址：https://github.com/wquguru/cicada
- 类目：应用项目 ｜ 语言：Swift ｜ Stars：2.6k（2647）｜ 近期增量：周均 ≈810 ⭐（建库 23 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 cicada.indaloop.app + 四语 README + 多语种官网与下载页 + v1.10.1 正式 Release（11 个平台安装包）

**核心功能**
- **全场景系统音频监听**：腾讯会议、飞书、钉钉、Zoom、Teams、Discord、B 站直播、播客……只要电脑在放声音就能出双语字幕；不往会议里派 bot，参会者无感知。
- **按住说话键，说母语译外语**：轮到你发言时按住按键（Mac 右 ⌥ / Windows 右 Ctrl，可自定义）讲中文，对方在通话里听到的是翻译后的语音——同传级别的实时双向沟通。
- **本地识别，音频不出机**：Apple 芯片 Mac 上语音识别全部在本机运行，音频不离开电脑；边听边写结构化会议纪要，散会即得，不用再花一小时整理录音。
- **四平台原生客户端**：macOS 14.4+ / Windows 10+ / Ubuntu 22.04+ / Android 10+ 全覆盖，每期 Release 提供各平台安装包；README 有英/中/日/韩四语。

**技术栈**
Swift 原生客户端；Apple silicon 本地语音识别 + 系统音频采集；Apache-2.0 协议；官网提供各平台下载与使用文档。

**适用场景**
参加外语会议/跨国电话需要实时字幕与双向翻译的人；看外语直播、播客想挂字幕的观众；会议多、纪要整理耗时重的职场人；对隐私敏感、要求音频不出本机的团队。

**推荐理由**
- **产品完成度罕见地高**：不是概念 demo：v1.10.1 正式版、四平台安装包、四语文档、官网齐备，23 天 2.6k star 建立在「装上就能用」之上。
- **找对了技术路线**：走系统音频监听而不是会议软件 API 或进会 bot，天然兼容所有会议工具且无感知；本地 ASR 又把隐私与延迟同时解决。

> **注意**：手机端系统禁止采集通话与会议 App 的音频，手机上需外放使用「面对面」模式；非 Apple 芯片设备的识别走云端，注意敏感会议的隐私边界；实时同传有秒级延迟，快节奏对话需适应；会议软件版本更新可能影响音频采集方式，需跟版升级。

> **一句话理解**：像戴了副自带秘书的同传耳机：听不懂的字幕实时铺在屏幕上，你按住键说中文，对方听到翻好的外语——散会时纪要已经躺在桌面上。

---

## 3. Gamer —— 米哈游开源的屏幕级游戏 Agent 基础模型

**一句话简介**：它读的是屏幕画面、出手的是鼠标键盘——先「看」了几万小时人类操作录像学会套路，再靠真实对局反馈自己磨到熟练玩家水平，全程不需要游戏给任何特殊接口。

**仓库信息**
- 地址：https://github.com/RainBowLuoCS/Gamer
- 类目：算法/模型 ｜ 语言：多语言（权重与文档为主） ｜ Stars：1.4k（1431）｜ 近期增量：周均 ≈400 ⭐（建库 25 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：arXiv 论文 2611.18397 + HuggingFace 模型集合（THUSI-Lab/gamescaling-model）+ 项目页 mihoyo-gamer.github.io + 方法/结果/动作格式文档 + 游玩实录视频

**核心功能**
- **统一视觉控制接口**：观察输入只有屏幕图像，动作输出就是原生键鼠操作，2D 图形界面与 3D 虚拟世界共用一套接口——这也是它「通用游戏智能体」定位的根基。
- **真实键鼠轨迹的继续预训练**：用数万小时设备级键盘鼠标交互轨迹做 CPT，轨迹横跨模拟游戏与具身环境，让模型同时学到虚拟与物理世界的环境动力学。
- **TA-GRPO：长程任务的多轮 RL**：时间感知 GRPO 用记忆摘要把轨迹段串成链，配合可验证的环境反馈与时间信用分配，缓解上下文有限、误差累积、奖励稀疏三大难题。
- **Streaming-vLLM 实时推理引擎**：持久上下文复用 + 校验投机解码 + 动作提前分发，支撑数百个游戏环境并发的在线推理与部署（该组件代码尚未发布，见 TODO）。

**技术栈**
VLA 基础模型（感知-记忆-推理端到端）；训练流水线 CPT → 稀疏思考 SFT → 在线 RL；权重托管 HuggingFace；Apache-2.0 协议；米哈游崩坏 AI 研发团队与新加坡国立大学、清华大学、国科大、中科大联合出品。

**适用场景**
3D 开放世界游戏的长任务自动化与评测基准；GUI Agent / VLA 训练范式研究（键鼠轨迹与机器人操作数据同构，具身智能团队可借鉴其 scaling 路线）；多轮强化学习与记忆机制的方法实验。

**推荐理由**
- **证明了「重复键鼠轨迹」也能 scaling**：论文核心结论：看似枯燥的人机操作轨迹，靠数据与算法规模就能换来复杂技能的稳定习得——给数字与物理世界的通用 Agent 都指了一条数据获取的路。
- **产学研背书 + 全套可核验资产**：大厂研发团队 + 顶校联合，论文、权重、项目页、方法文档、演示视频一次配齐，不是 PPT 开源；TA-GRPO 与 Streaming-vLLM 都是可单独借鉴的方法组件。

> **注意**：Streaming-vLLM 推理引擎尚未发布（TODO 未勾选）；复现训练需要大量算力，个人难以从头训练；模型面向游戏与仿真环境，迁移到真实机器人控制仍需适配；论文 2026-11 刚发布，第三方独立复现结果还很少；周均 ≈400 ⭐ 压线过 300 门槛。

> **一句话理解**：像把一个「只看屏幕就会打游戏的手替」装进了模型：它读截图、出键鼠操作，先刷了几万小时人类操作录像学套路，再靠对局输赢反馈自己磨到熟练玩家——跟教练教人打球是一个流程。

---

## 4. Floorplan —— 让 AI 给你的代码库画一张可交互平面图

**一句话简介**：AI 帮你写完了一个能跑的应用，但「结账流程到底发生在哪、改这里会碰坏什么」没人说得清——Floorplan 把没人画的那张架构图补上，而且画的是人话。

**仓库信息**
- 地址：https://github.com/haydenschmitty/floorplan
- 类目：工程实践 ｜ 语言：JavaScript ｜ Stars：6.5k（6472）｜ 近期增量：周均 ≈1,620 ⭐（建库 28 天）
- 协议：MIT ｜ 官网 / 文档：在线 demo（Brewline 示例应用）+ 官方走查视频 + docs/ 文档目录 + FAQ + CHANGELOG（v0.11.0）+ GitHub Actions CI 测试

**核心功能**
- **一句话生成代码库地图**：对 Claude Code 或 Codex 说「给我画个 floorplan」，几分钟后得到一张可交互平面图：每个部分、文件、Web 请求都用通俗英文名命名，连接关系全部标出。
- **图上直接提问**：「用户结账时发生了什么」「改这个文件会破坏什么」都能在图上得到回答；地图随开发持续更新，不是一次性的静态截图。
- **零依赖、双插件分发**：Node 18+，零第三方依赖；以 Claude Code 与 Codex 插件两种形态安装，README 有安装、快速上手、原理、FAQ 完整链路。
- **质量件齐全**：GitHub Actions 测试流水线、语义化版本 CHANGELOG、无需安装的在线 demo（四仓库组成的示例咖啡订阅应用）、视频走查一应俱全。

**技术栈**
JavaScript，Node 18+，零第三方依赖；以 Claude Code / Codex 插件形式分发；MIT 协议。

**适用场景**
AI 辅助写出、但自己没通读过的代码库（vibe-coded 项目）；接手遗留系统想快速建立全局认知；新成员 onboarding；向产品/设计等非工程角色解释系统结构。

**推荐理由**
- **踩中了 AI 编程时代的新痛点**：代码生成速度远超人的阅读速度，「能跑但没人懂」成为常态；它把「理解」做成一张图而不是又一轮聊天，切入角度聪明。
- **工程洁癖式的克制**：零依赖、带测试、语义化版本、在线 demo，28 天 6.5k star；对一个开发效率工具来说，这种自洽程度不多见。

> **注意**：依赖 Claude Code 或 Codex 的现有订阅，地图生成消耗模型 token，大型 monorepo 首次构建开销可观；地图粒度与命名质量受底层模型影响；v0.11 仍在快速迭代，产物 schema 可能变化；对纯前端小组件项目收益有限。

> **一句话理解**：像给一套看不见装修过程的房子补了张全屋水电图：哪个开关管哪盏灯、拆这面墙会碰到哪根管子，图上点一下就能看——而画图的是 AI，看图的是你。

---

## 5. Agent Autoloop —— 让命令行 Agent 后台自动接活干到底

**一句话简介**：平时用命令行 Agent 是「人守着终端」：关掉窗口事情就断了。它把 Agent 变成常驻员工——活自己接、自己跟，只有需要签字的事才来问你。

**仓库信息**
- 地址：https://github.com/KKKKhazix/agent-autoloop
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：6.4k（6400）｜ 近期增量：周均 ≈2,130 ⭐（建库 21 天）
- 协议：MIT ｜ 官网 / 文档：中文为主的详尽 README + 架构图 + INSTALL/场景模板/插件体系分层文档 + 一行命令安装脚本 + Release 经全量检查后发布

**核心功能**
- **一台电脑就能跑的常驻内核**：零外部依赖的任务调度内核，Windows/Mac/Linux 一条命令安装，不用云服务器、不开公网端口；有事干时调度，没事干时不打扰。
- **任意 CLI Agent 即插即用**：不需要 SDK、不改 Agent 源码：能接收提示词并打印最后一条回复的命令行工具都能接，一行配置完成注册，Claude Code、Codex 等直接上岗。
- **卡片式人工拍板**：拿不准的事把决策卡片推到飞书、钉钉、企微、Slack、Discord 或桌面通知，人点一下选择即继续；想看全局进展，敲一行命令。
- **四个方向全插件化**：事件来源、Agent、通知通道、代码上线流水线全部拆成可替换插件；官方安装脚本装最新 Release，那是通过全部检查的版本。

**技术栈**
TypeScript，Node 24+；零外部依赖内核 + 插件架构；官方 PowerShell/sh 安装脚本，Release 附全量检查；MIT 协议。

**适用场景**
让编码 Agent 无人值守接活（issue 分诊、内容生产、定时巡检、自动化脚本维护）；个人开发者编排「数字员工」；需要在自动化流程里嵌人工审批卡点的团队。

**推荐理由**
- **定位切中了 coding agent 的下一站**：把「人守终端」变成「人只在决策点出现」，是编码 Agent 从玩具走向常驻生产力的关键一步；审批卡片的设计让「放权但不失控」有明确落点。
- **上手与扩展门槛都低**：一条 curl 安装、零依赖内核、中文文档与架构图完整；不改一行业务代码就能接新 Agent，21 天 6.4k star、发布即高频迭代。

> **注意**：需要 Node 24+ 与一个已登录的 CLI Agent；无人值守跑 Agent 要自行评估 token 成本与任务边界；项目仅三周大，长期稳定性、并发任务与失败恢复的边界尚待观察；推送决策卡片需对应 IM 的机器人权限；本期提示：这正是本条日报自动化流程的同款思路。

> **一句话理解**：像给远程员工配了个前台调度员：活来了自动派给你的 Agent 干，只有要签字的单子才递到你手机上——你从监工变成了审批人。

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

- 本期网络形态：GitHub HTTPS 恢复正常（真 Sectigo 证书链），bash 侧 curl + gh api（授权额度 5,000/h）取数全程顺畅；open.feishu.cn 通道状态以发布脚本实测为准。
- Trending 日榜 16 条 / 周榜 13 条，可用新增为零：全部为已推送仓库回潮或技能/插件合集，本期 5 个入选全部来自 Search API 补池（created:>2026-10-20、topic:reinforcement-learning、topic:developer-tools 等多组查询）。
- 增量口径：Trending 无原始增量数据，全部按「累计 star ÷ 建库天数 × 7」估算周均并标注，五个入选仓库周均估算均 ≥400，无需破例。
- 遗留候选关闭：KingKongRobotics/jumper（仿生机器蟹，上期遗留优先项）最近提交为 2026-10-30，超 30 天活性线，正式排除；horizon-rust/horizon（11.9k，Rust 重写 Minecraft）因游戏版权灰区口径与应用类目配额未入选。

**本期按规则排除的候选**

- elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、google-labs-code/stitch-skills、mvanhorn/last30days-skill、kajisho5/ffmpeg-skill、tradermonty/claude-trading-skills、janestreet/agent_skills、patch-gg/pixelfx、heydamir/unslop、QingYunA/answer-me-with-html —— 技能/插件合集，按口径排除
- KingKongRobotics/jumper —— 最近提交 2026-10-30，超 30 天活性线，排除（遗留优先项关闭）
- valentderah/totk-pc-recomp —— 任天堂游戏静态重编译，版权风险排除；Zagitta/gpu-unlock —— 无 License 信息，排除
- Minireel/HGhub、reacher-z/Awesome-CUA、qwdwqfwq/topconf-paper-figure-gallery、Folkbench/folkbench —— NOASSERTION 或资源聚合目录，排除
- storytold/craft-anything 等 storytold 族 —— 同账号批量同构发布，延续整族排除；ccch1mneyyy/dsh-Go、Ebony-Vinyl/dsh-our-free-model —— DSH 生态重复/合规存疑
- bojieli/ai-infra-book —— 开源书稿，教程类排除；unclebob/ub-mode —— 无描述空壳，排除
- firecrawl/firecrawl、nginx/nginx、openvinotoolkit/openvino、dream-num/univer、Tracer-Cloud/opensre 等 —— 已推送回潮，避让
- erkamyaman/rust-anything、EL4CTEO/fast-anything、anefzaoui/misterdownloadmanager —— 同构话术新作，观察期延续
- omlahore/RemoveMacAI、Verlintas/NOIR、xevrion/hatchzip、govijr/terminal-mac —— 合格但应用类目配额已满，让位

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-24 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
