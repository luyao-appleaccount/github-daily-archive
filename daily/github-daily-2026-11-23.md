# 每日 GitHub 精选 · 2026-11-23（第 27 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [pengchujin/aerial-tv](https://github.com/pengchujin/aerial-tv) | 应用项目 | Kotlin | 13.0k | 周均 ≈2,670 ⭐（建库 34 天） |
| 2 | [RoutineMiku/apkstart](https://github.com/RoutineMiku/apkstart) | 应用项目 | JavaScript | 9.2k | 周均 ≈2,570 ⭐（建库 25 天） |
| 3 | [Tracer-Cloud/opensre](https://github.com/Tracer-Cloud/opensre) | AI Agent | Python | 14.4k | 日榜 +399 ⭐（11-23） |
| 4 | [DIYgod/pinky](https://github.com/DIYgod/pinky) | AI Agent | Go | 2.7k | 周均 ≈1,100 ⭐（建库 17 天） |
| 5 | [strands-labs/strands-decider](https://github.com/strands-labs/strands-decider) | 算法/模型 | Python | 1.3k | 周均 ≈160 ⭐（建库 55 天，破例入选，见附录） |

---

## 1. Aerial TV —— 给国产电视的一块 tvOS 式干净桌面

**一句话简介**：国产电视的开机广告删不掉（那是固件播的），但广告之后的桌面可以整个换掉——Aerial 的思路是「不动系统，只接管前台」。

**仓库信息**
- 地址：https://github.com/pengchujin/aerial-tv
- 类目：应用项目 ｜ 语言：Kotlin ｜ Stars：13.0k（12987）｜ 近期增量：周均 ≈2,670 ⭐（建库 34 天）
- 协议：MIT ｜ 官网 / 文档：官网 aerial.qust.me + 一行命令安装脚本 + 分品牌 ADB 教程 + docs/devices 机型适配库 + 手机扫码协同配置

**核心功能**
- **无 root 接管桌面**：通过无障碍服务监听前台切换 + 通知监听复活被系统清理的进程，按 HOME 键和开机都回到 Aerial；不 root、不改系统应用，随时可还原回原桌面。
- **手机扫码整理应用**：电视上扫码后，在手机网页里拖拽排序、改名、换图标、加 HDMI 信号源——比用遥控器一格一格挪舒服得多；Apple TV、PS、Switch、Xbox 都有现成磁贴图标。
- **航拍屏保与控制中心**：内置 Apple TV 同款 114 段 4K 航拍影片屏保（支持杜比视界）、必应每日壁纸；信号源、音量、亮度、个性化设置收进一个控制中心。
- **机型适配文档是真功夫**：docs/devices 按机型记录实测结果，小米/TCL/海信/创维/极米等 ✅/⚠️/❌ 三档标注全部来自真实用户反馈，另有针对 Android 4.x 老电视的 120KB Lite 版。

**技术栈**
Kotlin + Jetpack Compose（完整版需 Android 5.0+，Lite 版纯 Views 兼容到 4.0）；无障碍服务 + 通知监听实现桌面接管与保活；Gradle 构建，JDK 17；MIT 协议。

**适用场景**
受够开机广告和推荐流的国产电视/投影/盒子用户；家里电视接 Apple TV、游戏机、想要统一干净入口的家庭；想研究「无障碍服务对抗厂商固件」实现方式的安卓开发者。

**推荐理由**
- **痛点极准，方案克制**：电视广告桌面是全民痛点，它没有走刷机、root 的激进路线，而是用无障碍 + 通知监听这类「系统能力内」的手段完成接管，安装简单、随时可退，风险极低。
- **完成度远超典型的 launcher 玩具**：手机协同配置、分品牌 ADB 教程、机型适配库、AI Agent 安装流程（agent.md）一应俱全，34 天 13k star 是用户用脚投出来的。

> **注意**：开机广告本身由固件播放，本项目去不掉；部分机型开机仍会先闪原桌面几秒到几十秒；雷鸟部分机型、坚果投影等固件会强杀第三方桌面，完全不适用；海信工厂菜单操作有变砖风险（README 已警告）；只装 APK 不执行 ADB 命令时，HOME 键接管与开机自启不生效。

> **一句话理解**：像给装修好的房子不改水电、只换了一套全屋开关面板：墙还是那面墙（系统固件），但每天摸的界面焕然一新，不喜欢随时换回来。

---

## 2. ApkStart —— 让安卓应用在 Windows 上像原生软件一样装和用

**一句话简介**：WSA 停更、模拟器全家桶塞广告的年代，一个「双击 APK 就像双击 exe」的工具精准踩中了空档——而且它是个下班时间维护的个人项目。

**仓库信息**
- 地址：https://github.com/RoutineMiku/apkstart
- 类目：应用项目 ｜ 语言：JavaScript ｜ Stars：9.2k（9245）｜ 近期增量：周均 ≈2,570 ⭐（建库 25 天）
- 协议：MIT ｜ 官网 / 文档：README 极详尽（含实测数据与失败排查）+ GitHub/Gitee 双源 Release + 内置测速换源更新器 + 本机体检与驱动兼容补丁机制

**核心功能**
- **双击 APK 即安装**：注册文件关联后，在资源管理器双击 APK 自动解析、安装、生成桌面与开始菜单图标；应用窗口是真原生渲染（非投屏），可全屏、可拖拽缩放、尺寸按应用记忆。
- **自持运行时，不碰别的模拟器**：运行时组件自己下载校验管理（adb + Android Emulator + Android 14 镜像共约 1.6GB，官方源 10+ MB/s），不探测不接管 MuMu/雷电/WSA；网络走 QEMU 用户态 NAT，不创建虚拟网卡、不用装驱动。
- **工程细节堆得很满**：空闲预热常驻（冷启动 23 秒压到几乎不用等）、快照恢复（约 10 秒）、ARM-only 应用自动切兼容镜像、失败原因翻译成中文并给修复建议、企业网络可强制单一更新源。
- **壳层零依赖**：连 ZIP/PNG/ICO/AXML 解析都是手写的，按需拉起运行时、空闲自动回收；README 的「设计取舍」一节诚实说明哪些不是从零实现。

**技术栈**
Electron 壳 + 自管理 QEMU/Android Emulator 运行时；Android 14 x86_64 Google Play 镜像为基座（ARM 兼容靠镜像内置翻译层）；系统镜像 xz 压缩分发；MIT 协议。

**适用场景**
想在 Windows 上随手跑手机 App（扫码、办公、轻游戏）不想装模拟器全家桶的用户；开发者做安卓应用多开/自动化测试；需要离线分发「双击即用安卓应用」的内部场景。

**推荐理由**
- **踩准了 WSA 停更后的真空期**：微软 WSA 已停止支持，商业模拟器又普遍塞广告、绑账号；ApkStart MIT 免费、无广告、运行时全走 Google 官方源，立场干净得罕见。
- **工程质量远超「个人自娱自乐」的自评**：快照完整性校验、conhost 黑窗压制、/data 自建 ext4、双源测速下载这些细节，是很多商业产品都没做到的用心程度。

> **注意**：作者自述「早期版本、暂时不是很好用」，v0.x 阶段；安装包约 1.3GB、空闲预热常驻约 1GB 内存（可关）；需要 CPU 虚拟化支持，无硬件加速时回退软件模拟会明显变慢；ARM 兼容模式依赖 Google 镜像内置翻译层，个别强反模拟检测的应用（部分银行类）仍跑不了；作者声明无营销推广、谨防假冒下载站。

> **一句话理解**：像给 Windows 装了个「安卓应用的安装器」：APK 在它眼里就跟 exe 一样，双击装好、桌面点开就是一个独立窗口——底下那台安卓虚拟机被藏得严严实实，你完全感知不到。

---

## 3. OpenSRE —— 自动排查 CI 失败和生产事故的开源 Agent

**一句话简介**：「修因不修表」是它最值钱的设计哲学：先分清是代码坏了还是 CI 本身不稳——后者根本不该浪费工程师半夜去查。

**仓库信息**
- 地址：https://github.com/Tracer-Cloud/opensre
- 类目：AI Agent ｜ 语言：Python ｜ Stars：14.4k（14443）｜ 近期增量：日榜 +399 ⭐（11-23）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 opensre.com + Mintlify 文档站 + 一行命令安装脚本 + Discussions 社区 + 60+ 工具集成清单

**核心功能**
- **失败即刻自动调查**：CI 构建失败后立即读取日志、逐个验证假设、定位根因，最后推送带证据的修复 PR 供人工审阅——人只做最终决策，跑腿活全交出去。
- **量化 CI 的隐性成本**：统计失败率、因不可靠 CI 损失的开发时长、main 分支红灯总时长，把「我们的流水线老挂」变成可上报的数字。
- **不止 CI，也管生产事故**：接 EKS、CloudWatch、Kubernetes、Grafana、Datadog、Slack 等 60+ 集成，用自然语言描述事故或把告警直接路由给 Agent 调查。
- **自托管 + 自选模型 + 可审计**：支持 Anthropic/OpenAI/Ollama 等 9 家模型（含本地模型）；工具副作用分级、外部写入需审批；transcript 默认本地处理，遥测一个环境变量关闭。

**技术栈**
Python（mypy/Ruff/pytest 全套质量工具）+ litellm 多模型层；自研 pipeline（已从 LangGraph 迁出）；PyInstaller 打包 CLI，Docker/AMI 部署；Apache-2.0 协议。

**适用场景**
CI 频繁挂、根因排查占用大量工程师时间的团队；想给全员配一个同等深度「值班分析师」的平台组；对日志敏感、要求自托管与本地模型的组织；把事故响应嵌进自有 Python 服务的中台团队。

**推荐理由**
- **Agent 落地里少见的「工程化完成度」**：不是 demo：真实 e2e 云场景测试、副作用分级审批、证据关联回答、可审计 prompt，安全与隐私设计都按生产标准来的。
- **切入点聪明**：CI 失败排查是高频、低风险、结果可验证的场景，比直接让 Agent 碰生产变更稳得多，是团队接受「Agent 动基础设施」最平滑的入口。

> **注意**：当前为 Public Alpha，API 与集成仍在演进；首次启动需账户登录，默认激活 hosted model（可切本地）；遥测默认开启需手动 opt-out；Slack 后端已移出本仓库（gateway 模式仅支持 Telegram）；商业公司开源项目，存在 Cloud 托管服务与 trust.tracer.cloud 组件，评估时注意边界。

> **一句话理解**：像给团队雇了个不睡觉的初级 SRE：流水线一红他就去翻日志、查依赖、写排查报告，把结论和修复建议放到你面前——签字画押的权力始终在你手里。

---

## 4. Pinky —— 让 AI Agent 安全地替你操作手机

**一句话简介**：手机 GUI Agent 的难点从来不是「能不能点」，而是「敢不敢让它点」——Pinky 把安全做在了网关层而不是提示词层，这是它和同类项目的分水岭。

**仓库信息**
- 地址：https://github.com/DIYgod/pinky
- 类目：AI Agent ｜ 语言：Go ｜ Stars：2.7k（2675）｜ 近期增量：周均 ≈1,100 ⭐（建库 17 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：README 文档极详尽（实测数据/品牌差异/排查指南）+ brew/deb/exe 安装包 + RSSHub 作者出品 + pre-alpha 快速迭代

**核心功能**
- **任意 Agent 接入你的手机**：Claude Code、Codex、Cursor 等 MCP 客户端一键连接，就能操作真实的 iPhone/安卓：发消息、装应用、跑测试；也可在手机上独立运行、直接调用国产模型。
- **审批在网关强制执行**：支付、转账等风险操作必须人工点击确认，规则在网关层实现，智能体无法自行批准——即使屏幕上出现诱导文本也绕不过；银行、钱包类应用默认不可见。
- **隐私细节做满**：密码与验证码字段禁止输入、验证码自动打码；Android 13+ 可在隐藏的第二屏幕干活，主屏锁着不受影响；每步操作有截图与录像，可导出 HTML 报告。
- **轻量原生，全平台覆盖**：单一 Go 二进制无 cgo、无 Electron，下载仅 16-22MB、空闲约 70MB 内存；USB/Wi-Fi/Tailscale 远程多连接，拔线自动切换任务不断。

**技术栈**
Go 单二进制 + MyGo GPU 绘制 UI；Android 走 adb + 内置 scrcpy server，iOS 用 Xcode Device Hub 协议；FFmpeg 9 做视频解码；凭证存系统钥匙串；Apache-2.0 协议。

**适用场景**
让编程 Agent 代办手机上的重复操作（发消息、设闹钟、日常任务）；App 开发者做真机自动化测试（装包、看崩溃、截图出报告）；需要定时无人值守任务的场景；研究移动端 Agent 安全模型的团队。

**推荐理由**
- **安全模型是同类里最完整的**：网关层强制审批 + 敏感应用灰箱遮挡 + 验证码打码 + 全程录像审计，这套设计直接回答了「凭什么敢让 AI 碰我的手机」。
- **作者与工程底子都可信赖**：DIYgod 是 RSSHub/RSSHub 生态的知名维护者，Go 单二进制 20MB 做到三桌面 + 双手机平台覆盖，文档详尽到列了各国银行封禁行为。

> **注意**：pre-alpha 阶段，部分功能「已构建但尚未真机验证」；iOS 17.4-26 需 Mac + Xcode 签名安装，免费 Apple ID 每 7 天要重签；安卓无障碍服务开启时部分银行 App 会拒绝运行（多国银行明确封锁自动化）；浏览器内容依赖 OCR；可执行命令的 Agent 理论上可绕过 Pinky 直连 adb，README 建议配合沙箱隔离使用。

> **一句话理解**：像给手机配了个带监控和门禁的远程操作台：AI 可以坐上去帮你点按操作，但门禁卡在你手里（风险操作必须你确认）、保险柜它根本看不见（敏感应用屏蔽）、全程还有监控录像（操作报告）。

---

## 5. Strands Decider —— 比 LLM 快 10 倍的 Agent 专用决策模型

**一句话简介**：Agent 流程里 90% 的决策其实是选择题而不是作文题——用会写作文的大模型做选择题，贵且慢；Decider 把「生成」砍掉，只留「指向」。

**仓库信息**
- 地址：https://github.com/strands-labs/strands-decider
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：1.3k（1256）｜ 近期增量：周均 ≈160 ⭐（建库 55 天，破例入选，见附录）
- 协议：Apache-2.0 ｜ 官网 / 文档：strandsagents.com 文档站 + JevBench 第三方评测数据 + PyPI 包 + 配套「自定义决策」Agent Skill + Strands Agents SDK 官方生态

**核心功能**
- **架构巧：砍生成头换指针头**：拿 Qwen3.5-2B 当躯干，扔掉语言建模头，换一个约百万参数的指针头：一次前向比较各选项的隐状态直接给分，无生成、无解码循环；标签集由请求定义、不写死在权重里。
- **三种题型一个头**：是非题（noul）、N 选一（choice）、量表打分（score）都出自同一个 masked softmax；同一状态可一次读入后并行问多个问题，每问只增加自己的 token。
- **置信度是真校准的**：每个决策自带置信度：置信 0.9 以上的答案在没见过的短分类任务上准确率约 95%（第三方 JevBench 数据），低于阈值就转人工确认——这是 LLM 推理 API 不提供的能力。
- **落地件配齐**：pip 即装、CLI/HTTP 服务两种形态、Apple silicon MLX/CUDA/MPS/CPU 全设备支持；repo 里还有把它接进 Strands Agent 的完整示例和「用你自己的数据定制」的 Agent Skill。

**技术栈**
Python；预训练 decoder 躯干（Qwen3.5/Gemma 4 系列，2B-26B 多档）+ rank-16 LoRA 适配 + fp32 指针头；提供 2B/12B/26B-A4B/E4B/E2B 多档权重；Apache-2.0 协议。

**适用场景**
Agent 工作流里高频、低难度的判定环节：模型路由、工具选择、参数预检、请求分流、安全护栏分类；对成本和延迟敏感、想给 LLM 配「快速判官」的 Agent 平台；需要带置信度的分类打分服务。

**推荐理由**
- **把「系统一/系统二」做成了可用产品**：认知科学里快思考/慢思考的分工，落地成「LLM 管难题、Decider 管选择题」的混合架构，思路清晰且每一环都有量化证据（延迟、准确率、校准曲线）。
- **生态位置好**：出自 Strands Agents 官方 labs，与 Strands SDK 无缝集成，文档、评测、定制指南一应俱全，不是孤立的研究 demo。

> **注意**：本期破例入选：周均 ≈160 ⭐ 未达 300 门槛，但算法/模型类目本期无达标候选，且其为 Strands Agents 官方 labs 仓库、文档与第三方评测齐全，质量与实用性足以破例（口径已在条目内注明）；仅适合选项明确的判定类任务，开放式生成仍需 LLM；置信度校准在长文本与极端分布下未承诺同等表现。

> **一句话理解**：像考试时配了个「涂答题卡专用的快速阅卷机」：论述题还是交给老师（LLM），但选择题、判断题刷一下就出分——快一个数量级，还告诉你它对这题有多大把握。

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

- 本期网络形态：GitHub HTTPS 被网络侧替换为伪造 VeriSign 证书（bash 侧 curl/git 取数不可用），全部取数经 WebFetch 工具通道完成（Trending 聚合站 + Search API + 仓库页 README + api.github.com）。
- Trending 日榜 16 条 / 周榜 13 条，可用新增极少：技能/插件合集 9 条、已推送回潮 6 条、版权风险类 3 条；本期 5 个入选中 4 个来自 Search API 补池（created:>2026-10-20、created:>2026-11-05 等查询）。
- 算法/模型类目无达标候选，strands-decider 以周均 ≈160 ⭐ 破例入选（官方 labs 仓库 + 第三方评测 + 文档站齐全），已在条目内注明口径。
- 遗留候选顺延：KingKongRobotics/jumper（仿生机器蟹开放项目，Apache-2.0，≈405 周估，与巡检机器人方向相关）因应用类目配额满让位，下期可优先。

**本期按规则排除的候选**

- elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、google-labs-code/stitch-skills、mvanhorn/last30days-skill、kajisho5/ffmpeg-skill、janestreet/agent_skills、wheresryan22/anatomy —— 技能/插件合集，按口径排除
- ItsNotRexed/Leonida —— Xbox 版 GTA6 的 PC 原生重编译（建库 3 天 1.5 万 star），涉及未授权商业游戏代码，版权风险排除
- zortos293/Lichii、seedds/nxnative、jhaizhou-ops/S2Arm —— Switch 模拟/原生移植类，需自备游戏与密钥，版权灰区按口径排除
- BaaRai/ARTEX —— 自称译自 Autumn-27/ARTEX，但上游仓库已 404 无法核验来源与 License，排除
- huami1314/GestaltX、Kianuni/Erosion-CN —— MobileGestalt 系统配置篡改类工具，设备风险排除
- storytold/* 整族（photocraft/pdfcraft/filmcraft/wordcraft/craft-anything 等）—— 同账号数日内批量同构发布，延续整族排除
- firecrawl/firecrawl、nginx/nginx、openvinotoolkit/openvino、jingyaogong/minimind、alibaba/open-code-review 等 —— 知名项目热榜回潮，按选题口径避让
- erkamyaman/rust-anything、EL4CTEO/fast-anything —— 建库仅 7 天/2 天的同构话术新作（“rewrite anything in Rust”系列），进入观察期暂缓
- FrigadeHQ/yogurt、Eynnzerr/TelemetryCleaner、ersinkoc/phonebox —— 合格但应用类目配额已满，让位

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-23 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
