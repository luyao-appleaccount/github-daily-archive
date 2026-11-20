# 每日 GitHub 精选 · 2026-11-20（第 26 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [zhouxiaoka/autoclip](https://github.com/zhouxiaoka/autoclip) | 应用项目 | Python | 11.3k | 日榜 +126 ⭐（11-20） |
| 2 | [XiaoYouChR/Ghost-Downloader-3](https://github.com/XiaoYouChR/Ghost-Downloader-3) | 应用项目 | Python | 12.8k | 日榜 +341 ⭐（11-20） |
| 3 | [libracoder/kiri](https://github.com/libracoder/kiri) | 工程实践 | Rust | 11.3k | 周均 ≈4,390 ⭐（建库 18 天） |
| 4 | [wangzan101/Mika](https://github.com/wangzan101/Mika) | AI Agent | Kotlin | 9.2k | 周均 ≈2,920 ⭐（建库 22 天） |
| 5 | [wici-ai/inferssd](https://github.com/wici-ai/inferssd) | 算法/模型 | C++ | 1.3k | 周均 ≈303 ⭐（建库 29 天，压线入选） |

---

## 1. AutoClip —— 贴一个链接，长视频自动剪成能发的短视频

**一句话简介**：长视频变短视频这道工序里最耗人的从来不是渲染，是判断：哪里有钩子、哪句能当标题、怎么卡平台时长。AutoClip 把这一整条判断链做成了「贴链接即出片」。

**仓库信息**
- 地址：https://github.com/zhouxiaoka/autoclip
- 类目：应用项目 ｜ 语言：Python ｜ Stars：11.3k（11278）｜ 近期增量：日榜 +126 ⭐（11-20）
- 协议：MIT ｜ 官网 / 文档：官网与案例库（zhouxiaoka.github.io/autoclip_intro）+ 桌面/CLI/MCP 三形态同步发版 + 正式 release（v1.5.8，11-02）+ 7 语 README + trendshift 榜单认证

**核心功能**
- **一个链接，一键出片**：贴上播客、访谈、课程的链接或本地视频，选好目标平台，自动完成切片、字幕、封面与发布文案，产出直接适配抖音、小红书、TikTok、Reels、B 站等平台的时长与画幅要求。
- **在本机剪辑与渲染**：剪辑、字幕、渲染都在自己电脑上完成，成片不满意可进编辑器手工调整；桌面版、CLI、MCP 三种形态同步更新，MCP 接口能把「一键出片」接进自动化流水线。
- **成片质量先看后用**：README 直接挂出 16 条真实成片（访谈式、满屏播客式等），点开就能看完整效果并附原片链接——对内容工具来说，这是最诚实的展示方式。
- **附带传播研究**：docs/research 里有一篇「什么驱动播放量」的数据分析（2026-10），把标题、时长、开头钩子等因素与播放量做了关联，做短视频的人可以单独当资料读。

**技术栈**
Python + Tauri 桌面外壳；切片决策与文案由云端 LLM 按量调用，剪辑与渲染在本机；MIT 协议，另提供 autoclip-mcp 供 Agent 接入。

**适用场景**
做播客、访谈、课程切片的内容团队与个人博主；想把长视频批量转成多平台短内容的运营；想通过 MCP 把自动剪辑接进自己 Agent 工作流的开发者。

**推荐理由**
- **自动化的是最脏最累的那段**：切片式二创的瓶颈不是模型能力，是素材理解与平台适配的琐碎决策。它没有停在「生成字幕」这一步，而是把出片需要的四件事（切、配、封面、文案）一次做完。
- **展示方式可信，迭代节奏健康**：16 条真实成片可直接播放，桌面/CLI/MCP 同步发版、多语言 README、案例库齐全，是「给内容从业者用」而不是「给 demo 看」的完成度。

> **注意**：软件免费但云端模型按量计费，重度使用要算成本；切片质量依赖所接模型，中文内容表现好、小语种未验证；发布文案仍需人工把关各平台合规；MCP 接口在快速迭代，注意版本对齐。

> **一句话理解**：像请了个不知疲倦的剪辑学徒：你丢给他一个链接，他交回一条带字幕、封面和发布文案的成片——单条未必条条完美，但批量出活的能力是真人比不了的。

---

## 2. Ghost-Downloader-3 —— 一个应用装下 HTTP/BT/M3U8 全协议的下载器

**一句话简介**：下载器这个品类卷了几十年，卷的其实是「坏网络」：好网速下谁都快，差网、限速站、反爬站点上还能不能拉满，才是分水岭。

**仓库信息**
- 地址：https://github.com/XiaoYouChR/Ghost-Downloader-3
- 类目：应用项目 ｜ 语言：Python ｜ Stars：12.8k（12789）｜ 近期增量：日榜 +341 ⭐（11-20）
- 协议：GPL-3.0 ｜ 官网 / 文档：独立文档站 gd.xychr.com + 正式 release（v4.5.10，11-19）+ 浏览器扩展 + Discord/QQ 社群 + Windows/macOS/Linux/Android 四平台安装包

**核心功能**
- **弱网才是真正的考场**：智能分块下载且不需要事后合并文件，自动探测带宽动态调块数；TLS 指纹模拟真实浏览器，不易触发反爬——慢网与限速站点上提升最明显。
- **一个应用装下五种协议**：HTTP、磁力/BT、FTP、M3U8、MPEG-DASH 全部支持；YouTube 与 B 站可选清晰度、字幕、分 P 播放列表；GitHub 与 HuggingFace 下载走镜像加速。
- **浏览器里看到就能下**：扩展会列出当前页面的全部媒体，点一下桌面应用无缝接管，登录态自动继承；Android 端还能录制直播 M3U8 并后台下载。
- **下载过程始终可控**：兼容 aria2 的 RPC API 可接第三方工具，下载中途可改 URL、请求头与代理，进度不丢失。

**技术栈**
Python（Qt 桌面端）+ 多平台原生封装，覆盖 Windows/macOS/Linux/Android；协议栈覆盖 HTTP/BT/FTP/M3U8/DASH，扩展与桌面端通过本地通信接力；GPL-3.0 协议。

**适用场景**
常从 B 站/YouTube 存课程视频、要选清晰度与字幕的人；批量拉 HuggingFace 模型文件但直连缓慢的用户；需要 aria2 兼容接口做自动化的进阶玩家。

**推荐理由**
- **把下载器的碎片化需求收拢进一个应用**：过去要 IDM + qBittorrent + yt-dlp + N_m3u8DL 各装一个的场景，现在一个应用覆盖，且每项能力都不是「能凑合」的阉割版。
- **对国内网络环境做了真实优化**：GitHub/HuggingFace 镜像加速、B 站分 P、直播录制都是国内高频痛点，这些细节是翻译过来的海外产品覆盖不到的。

> **注意**：GPL-3.0 传染性较强，二次开发分发需注意合规；README 顶部有代理服务的赞助广告，与项目本体无关，别误认成功能；部分站点反爬升级后需跟进新版本；Android 端功能少于桌面版。

> **一句话理解**：像一把带五种刀头的多功能螺丝刀：十字、一字、内六角都是正经刀头不是凑数——单项未必比专用工具强，但日常九成的场景，一把就够。

---

## 3. Kiri —— 容器 2.5 毫秒启动的轻量 Docker Desktop 替代

**一句话简介**：替换类工具的生死题是迁移成本：Kiri 的答案是「一个命令都不用改」——它实现的是 Docker Engine API，你的肌肉记忆原封不动。

**仓库信息**
- 地址：https://github.com/libracoder/kiri
- 类目：工程实践 ｜ 语言：Rust ｜ Stars：11.3k（11292）｜ 近期增量：周均 ≈4,390 ⭐（建库 18 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 runkiri.com + docs/features.md 与 development.md + 正式 release（v0.2.2，11-19）+ 38 种界面语言（含简体中文）

**核心功能**
- **与 Docker 生态无缝兼容**：实现 Docker Engine API，现有 docker、Compose、buildx、docker login 命令原样可用；amd64 镜像在 Apple silicon 上经 Rosetta 运行，迁移成本接近零。
- **快与轻都是量化指标**：容器经 Docker API 启停约 2.5ms（约为 Docker Desktop 的 1/80），守护进程常驻约 15MB，VM 空闲 60 秒休眠、唤醒约 0.15s，指标都写在 README 可实测。
- **本地域名开箱即用**：每个容器自动获得 http://<name>.kiri.local 域名和 Kiri 自签 CA 签发的 HTTPS 证书，本机联调不用再手改 hosts、配端口映射。
- **不止容器**：一条命令起本地 Kubernetes 集群、可创建 Linux 虚拟机；原生窗口按 Compose 项目分组管理容器、镜像、卷与网络。

**技术栈**
Rust；macOS/Windows 上跑在一个轻量 Linux VM 里（Linux 直接用内核），实现 Docker Engine API 与 Compose/buildx 兼容层；Apache-2.0 协议。

**适用场景**
嫌 Docker Desktop 又慢又占内存、想要 OrbStack 之外选择的 macOS 用户；Windows 上不想装重型 WSL2 方案的开发者；本机微服务联调需要本地域名的团队。

**推荐理由**
- **兼容策略聪明：换引擎不换习惯**：不发明新 CLI、不逼用户迁移，直接实现 Docker Engine API——用户感知只是「后台那个东西变快变小了」，这是替换类产品最稳的路线。
- **增长与迭代都健康**：建库 18 天 11.3k star（周均 ≈4,390），release 周更，38 种语言界面说明瞄准全球开发者而非单一市场。

> **注意**：仍处 v0.2.x 早期，生产关键业务建议先在开发环境试用；Windows 支持成熟度低于 macOS；K8s 与 Linux 虚拟机是加分项但也更早期；与 Docker Inc.、OrbStack 无官方关系。

> **一句话理解**：相当于把 Docker Desktop 这台重型卡车换成一辆电动小车：装卸货的操作流程（docker 命令）一模一样，但起步快、占地小、等红灯不烧油。

---

## 4. Mika —— 装在安卓手机后台屏幕里干活的 AI Agent

**一句话简介**：桌面 GUI Agent 已经很多，手机端才是硬仗：屏幕小、后台限制严、目标 App 全是没开放接口的国民应用——Mika 用「后台隐藏屏幕」绕开了占用前台的死结。

**仓库信息**
- 地址：https://github.com/wangzan101/Mika
- 类目：AI Agent ｜ 语言：Kotlin ｜ Stars：9.2k（9192）｜ 近期增量：周均 ≈2,920 ⭐（建库 22 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 mikaphone.com + APK Releases（v0.1.49，11-19）+ 6 语 README（含简繁中文）+ trendshift Kotlin 日榜/周榜第一

**核心功能**
- **后台隐藏屏幕里干活**：Agent 的点击、滚动、输入都发生在一个隐藏的后台屏幕上，你可以同时正常用手机；任务做完自动停在该停的地方，比如加购后停在结算前。
- **演示全对着高频场景**：README 的动图是真实任务：总结微信群今天的聊天、在购物站按「30 美元以下、4.5 星以上」挑充电器加购、翻某博主的小红书并汇总近期内容。
- **操作而非接口**：走无障碍服务与屏幕操作路线，不依赖目标 App 的开放 API——理论上任何 App 都能操作，包括从不开放接口的微信、小红书。
- **Android 11+ 直接装**：APK 从 GitHub Releases 下载即可，Kotlin 原生实现，release 接近日更。

**技术栈**
Kotlin（Android 原生），基于无障碍服务与后台虚拟屏幕实现 GUI 自动化；任务规划与理解由 LLM 云端调用完成；Apache-2.0 协议。

**适用场景**
想让手机替自己完成重复操作的普通用户（发消息、汇总群聊、比价选品）；研究移动端 GUI Agent 落地形态的开发者；与 iOS 侧同类方案做对比的从业者。

**推荐理由**
- **移动端 GUI Agent 里少见的可用完成度**：手机端比桌面难做：屏幕小、后台限制严、App 不开放接口。Mika 的后台屏幕方案 + 真实场景动图，比多数停留在演示视频的项目实在。
- **对自动化边界处理克制**：「挑完加购就停、不代付」这类设计说明它清楚屏幕操作 Agent 的安全边界在哪，这种克制对高权限工具至关重要。

> **注意**：需要授予无障碍等高权限，务必只从官方 Releases 安装；云端模型调用产生费用，涉及账号的操作有风控风险；对微信等 App 做自动化需自行注意平台条款；v0.1.x 早期，稳定性待观察。

> **一句话理解**：像雇了个住在你手机里的实习生：你说「总结一下今天群里的消息」，他就在另一块你看不见的屏幕上翻记录、写摘要——你照常刷你的手机，互不打扰。

---

## 5. InferSSD —— 内存装不下的大模型，从 SSD 流式跑起来

**一句话简介**：MoE 模型每个 token 只激活少数专家，那么装不下的那部分权重为什么要常驻内存？InferSSD 把这个问题变成了工程答案：书放书库（SSD），讲到哪章翻哪章。

**仓库信息**
- 地址：https://github.com/wici-ai/inferssd
- 类目：算法/模型 ｜ 语言：C++ ｜ Stars：1.3k（1257）｜ 近期增量：周均 ≈303 ⭐（建库 29 天，压线入选）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 wici.ai/inferssd + 研究博客 + 桌面 App 下载 + Discord/Slack 社区 + release 节奏极快（11-19 一天两版）

**核心功能**
- **把 MoE 的稀疏性用在存储上**：MoE 每次前向只激活少量专家，InferSSD 让未激活的专家权重留在 SSD、用到再读，「内存装不下」不再是一票否决的硬门槛。
- **站在 llama.cpp 肩膀上**：基于 llama.cpp 改造，标准 GGUF 直接用、无需转换格式；Mac 走 Metal，Windows/Linux 走 CUDA 与 Vulkan（ROCm 在路上），桌面 App 内置浏览器聊天界面。
- **763B 级模型进消费级机器**：已实测 DeepSeek-V4.1-Flash（763B 总参/8-16B 激活）从 233GB 的 UD-IQ1_S 到 500GB 的 Q4 量化全档位，另有 Qwen3.8 Flash Next、Gemma4 E4B 等，直链与文件大小全列出。
- **两种使用形态**：面向普通用户的桌面 App（浏览器聊天界面），以及 OpenAI 兼容 API，可直接接进现有工具链。

**技术栈**
C++，基于 llama.cpp；核心是 MoE 专家权重的 SSD 流式调度（NVMe 随机读优化）；覆盖 macOS Metal、Windows CUDA/Vulkan、Linux；Apache-2.0 协议。

**适用场景**
内存 32-64GB 但想本地跑 700B 级 MoE 模型的玩家；不想为一次性推理采购大内存或多卡、手里有高速 NVMe 的团队；研究「存储换内存」推理架构的工程师。

**推荐理由**
- **把跑大模型的门槛从内存挪到硬盘**：MoE 天然稀疏 + NVMe 带宽逐年上涨，让 SSD 流式推理从论文思路走向可用产品；这是消费级硬件跑前沿大模型最现实的路线之一。
- **实测清单写得极具体**：每个模型的每个量化档位、文件大小、发布者直链全列在 README，复现路径清晰，不是只讲概念的 demo。

> **注意**：本期压线入选：建库 29 天、周均 ≈303 ⭐ 刚过增量门槛；生成速度受 SSD 随机读限制，明显慢于全内存方案，适合「能跑」优先于「跑得快」的场景；建议 NVMe SSD，SATA 盘体验会差很多；稠密模型（无稀疏专家结构）不适用此路线。

> **一句话理解**：像一本大部分章节你用不着的百科全书：与其把整本复印塞满书架（大内存），不如书放书库（SSD），讲到哪章翻哪章——翻页够快，读起来就像整本都在手边。

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

- 本期 Trending 日榜 16 条 / 周榜 13 条，有效新增候选极少：技能/插件合集 7 条、已推送回潮 6 条、NOASSERTION 2 条，实际可用候选仅 5 个。
- 算法/模型类目连续紧缺，本期 inferssd 以周均 ≈303 ⭐ 压线入选（建库 29 天），增量口径已在条目内注明。
- GitHub 侧网络本期恢复正常（真 Sectigo 证书），全部元数据经 gh api 逐仓核验（stars/license/pushed_at/releases）；飞书侧仍被 SANGFOR 中间证书拦截，本期推送按规则跳过。
- 遗留候选顺延：horizon-rust/horizon（≈1,690 周估）、wquguru/cicada（≈893 周估），增量不占优让位。

**本期按规则排除的候选**

- toeverything/AFFiNE —— 日榜 +182，但 License 为 NOASSERTION（未用标准 SPDX），按口径排除
- mjmirza/app-store-compliance —— 日榜 +377，实质为合规手册/技能包（NOASSERTION），排除
- firecrawl/firecrawl —— 日榜 +825、20.4 万 star，知名项目热榜回潮，按选题口径避让
- openvinotoolkit/openvino —— 日榜 +246，知名项目回潮避让
- JuneYaooo/rea-video —— 与 10-10 已推送的 morluto/rea 同族（rea 系列），按同族只取其一排除
- ccch1mneyyy/dsh-Go —— DSH 生态手机客户端，与已推送的 deepseek-harness/dsh-desktop 系列同生态，让位
- Trending 技能/插件合集 7 条（Claude-BugHunter、obra/superpowers、cursor/plugins、stitch-skills、last30days-skill、claude-trading-skills、ffmpeg-skill）按口径排除

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-20 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
