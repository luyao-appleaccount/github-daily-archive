# 每日 GitHub 精选 · 2026-11-26（第 30 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（2）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [n8n-io/nod](https://github.com/n8n-io/nod) | AI Agent | TypeScript | 3.6k | 周榜 +1,008 ⭐（建库 62 天） |
| 2 | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | 工程实践 | Go | 122.9k | 周均 ≈3,600 ⭐（建库 236 天） |
| 3 | [colbymchenry/codegraph](https://github.com/colbymchenry/codegraph) | 工程实践 | TypeScript | 78.7k | 周均 ≈1,770 ⭐（建库 312 天） |
| 4 | [jamiepine/voicebox](https://github.com/jamiepine/voicebox) | 应用项目 | Python | 61.3k | 周均 ≈1,400 ⭐（建库 305 天） |
| 5 | [algorithmicsuperintelligence/openevolve](https://github.com/algorithmicsuperintelligence/openevolve) | 算法/模型 | Python | 7.9k | 周均 ≈100 ⭐（建库 545 天，破例入选） |

---

## 1. Nod —— n8n 出品的个人 AI Agent，自带一台真电脑

**一句话简介**：工作流自动化老牌厂商 n8n 把「个人助理 Agent」做成了桌面应用：每天早上读你的邮件、日历和客户新闻，揉成一页会议简报；追账、退订阅这类杂活它直接上真实网站替你办。

**仓库信息**
- 地址：https://github.com/n8n-io/nod
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：3.6k（3590）｜ 近期增量：周榜 +1,008 ⭐（建库 62 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 nod.n8n.io + 完整文档站 + macOS/Windows/Linux 安装包 Release（v0.9.7，11-25）+ OpenSSF Best Practices 认证

**核心功能**
- **自带一台专属电脑**：Agent 在独立的虚拟电脑里操作真实浏览器与网站：追发票、取消试用期订阅、整理收据，网页任务闭环执行，而非只会给建议的聊天机器人。
- **动作之前先要你的点头**：替你发言（Slack 回复、邮件）与花钱动作默认拦截审批：草稿基于你的定价表和上下文生成，你确认后才发出——信任模型写在产品里，不是事后补救。
- **每天一页会议简报**：早晨自动通读邮件线程、日历与客户最新动态，为每个会话生成一页简报：背景、待办、风险点直接铺好。
- **模型自选、本机运行**：跑在你自己的机器上，接 ChatGPT Plus/Pro 订阅或自有 API Key；Gmail、Calendar、Slack、Notion 与浏览器一等公民集成。

**技术栈**
TypeScript 桌面应用（macOS 14+ / Windows 11 预览 / Linux x64 预览）+ 沙箱虚拟电脑；Apache-2.0 协议，OpenSSF 最佳实践认证。

**适用场景**
想找一个能上真实网站办事、而不仅是聊天的个人 Agent 的用户；被发票、订阅续费、会议准备这类杂务缠身的独立开发者与小团队；关注「审批优先」Agent 安全设计的工程团队。

**推荐理由**
- **大厂出品 + 真实网站执行闭环**：n8n（工作流自动化的头部开源项目）官方出品，把 Agent 从「建议生成器」推进到「在真实网站上完成任务」，62 天冲到 3.6k star、日更 Release，迭代凶猛。
- **审批优先的信任设计值得抄**：发言与支付动作强制人工批准的交互范式，是个人 Agent 落地最缺的一块拼图，对任何做 Agent 产品的团队都有参考价值。

> **注意**：目前为 research preview：Windows 与 Linux 均为预览版，稳定性待打磨；需 ChatGPT Plus/Pro 订阅或自有 API Key；让 Agent 操作真实网站涉及账号凭据与支付动作，务必逐条审批、不要放权给关键账户；109 个 open issue，新项目问题较多，先非核心账号试用。

> **一句话理解**：像雇了个通宵值班的数字实习生：早上把邮件、日历和客户新闻揉成一页简报，替你把发票追回来、把试用期订阅退掉——但每个要花钱、要发消息的动作，都得你先说 OK。

---

## 2. Caveman —— 让编码 Agent 少读少说的省 token 中间层

**一句话简介**：「为什么用很多 token，几个就够」：一句话把 Agent 的啰嗦回复改写成三句话电报体，超长测试日志压成摘要，结论不变、账单减半——HN 与 GitHub Trending 双料第一。

**仓库信息**
- 地址：https://github.com/JuliusBrussee/caveman
- 类目：工程实践 ｜ 语言：Go ｜ Stars：122.9k（122881）｜ 近期增量：周均 ≈3,600 ⭐（建库 236 天）
- 协议：Apache-2.0 ｜ 官网 / 文档：npm 包 @caveman-ai/cli + 30+ Agent 兼容列表 + 官网 caveman.so + 完整基准测量方法文档 + Adobe Research 论文引用 + JetBrains A/B 实测

**核心功能**
- **说人话变说电报（Say less）**：规则层把 Agent 回答改写成 caveman 电报体：63 个 token 的 React 重渲染长篇解释压成 20 个 token 的三句话，结论与代码语义不变。
- **读得更少（Read less）**：对超长工具输出做本地压缩：一次测试运行从 397 token 压到 76 token；官方实测整会话输入 token 减少 33.2%，18/18 任务答对。
- **Auto 档按任务定详细度**：自动在精简与详细间选择，85 个编码任务实测成本降到 Opus xhigh 档的 0.46 倍，得分差距在噪声范围内。
- **30+ 编码 Agent 即插即用**：Claude Code、Codex、Cursor、OpenCode 等主流 Agent 均可接入，npm 一条命令安装，本地代理不出网。

**技术栈**
Go 本地代理 + Skill 规则包，npm 分发；适配 30+ 编码 Agent；Apache-2.0 协议。

**适用场景**
重度使用编码 Agent 被 token 账单灼伤的开发者；长输出工具链（测试、构建日志）占大头的团队；研究 LLM 输出长度与成本关系的工程效能团队。

**推荐理由**
- **证据链罕见的开源优化层**：HN 第一、GitHub Trending 第一之外，还被 Adobe Research 论文实测引用（八模型 1.4~2.4 倍成本差）、JetBrains 官方博客 A/B 验证——「没人信这能行」最后都真香了。
- **立即可算的省钱账**：不动模型、不动提示词，只做输出改写与输入压缩，接上就省 30% 上下；236 天 12.3 万 star，是今年工程侧最硬核的爆款之一。

> **注意**：节省幅度依赖任务类型：长上下文、多工具输出场景收益最大，纯写作类任务收益有限；官方基准为自家跑分且与商业产品对比存在利益相关，建议按自己任务复测；电报体输出牺牲部分可读性，团队规范是否接受需先对齐；改写规则对中文任务的适配未经充分验证。

> **一句话理解**：像给话痨顾问戴上电报模式：原本 63 个 token 才讲完的原理分析，压成 20 个 token 的三句话——账单少了三分之二，干的活一模一样。

---

## 3. CodeGraph —— 给编码 Agent 用的本地代码知识图谱

**一句话简介**：编码 Agent 找上下文不再靠全文翻文件：函数调用关系、类型引用、模块依赖先建好图，改一处代码图自动跟着更新，Agent 一查就准——20+ 主流编码 Agent 都能接。

**仓库信息**
- 地址：https://github.com/colbymchenry/codegraph
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：78.7k（78714）｜ 近期增量：周均 ≈1,770 ⭐（建库 312 天）
- 协议：MIT ｜ 官网 / 文档：官方文档站（GitHub Pages）+ npm 签名与 attested 构建 + v1.6.4 Release（11-20）+ 20+ Agent 适配列表

**核心功能**
- **预索引 + 增量同步**：对整个代码库建语义知识图谱（调用关系、引用、依赖），代码一改自动增量更新，Agent 不用每次冷启动重新摸索。
- **手术刀级上下文供给**：Agent 提问时只给相关子图而非整文件堆，省 token 的同时显著降低改错位置的概率。
- **20+ 编码 Agent 适配**：Claude Code、Codex、Cursor、Gemini CLI、Copilot、Windsurf、Qwen Code 等统一接入，一次建图全家受益。
- **Rust 内核全本地**：解析与查询跑在 Rust 内核上，npm 分发自带 Node 运行时，零外部依赖、代码不出本机。

**技术栈**
TypeScript 外壳 + Rust 内核；npm 分发（签名 + attested 构建，三平台）；MIT 协议。

**适用场景**
给编码 Agent 接大代码库总改错地方的团队；monorepo 里想让多个 Agent 共享同一份代码理解的工程组；关注 Agent 上下文工程（context engineering）工具链的开发者。

**推荐理由**
- **上下文工程的关键基建**：Agent 改错代码八成是拿错上下文：把「翻文件找线索」换成「查图谱拿事实」，是当下最实在的 Agent 提效路径之一；312 天 7.9 万 star 验证了需求真实存在。
- **工程质量在线**：npm 签名与 attested 构建、双周节奏的 Release（v1.6.4 于 11-20）、独立文档站，供应链与维护完成度都超出一般个人项目。

> **注意**：open issue 251 个，冷门语言与框架的解析覆盖可能不全，先在小范围验证；首次索引大 monorepo 有构建成本；「Platform 平台」（PR 影响面分析、要测什么等高级能力）仍在 waitlist，属期货；对生成式图谱的准确性保持抽查习惯。

> **一句话理解**：像给 Agent 配了一张代码版的地铁图：不用挨个街区走路找路，直接查「谁调用了这个函数、改它会炸到谁」，一站直达。

---

## 4. Voicebox —— 本地优先的开源 AI 语音工作室

**一句话简介**：把配音棚、听写员和对讲机塞进一台笔记本：克隆声音、生成播报、全局听写一应俱全，还能用自己的音色跟编码 Agent 对话——语音这条 I/O 全链路不联网。

**仓库信息**
- 地址：https://github.com/jamiepine/voicebox
- 类目：应用项目 ｜ 语言：Python ｜ Stars：61.3k（61324）｜ 近期增量：周均 ≈1,400 ⭐（建库 305 天）
- 协议：MIT ｜ 官网 / 文档：官网 voicebox.sh + 文档站 docs.voicebox.sh + v0.6.0 Release（11-21）+ 安装包下载统计 + DeepWiki 集成

**核心功能**
- **声音克隆**：录几十秒样本即可克隆音色，任意文案用它朗读生成；适合播客、视频配音与无障碍朗读场景。
- **全局语音听写**：系统级听写输入：邮件、编辑器、聊天窗，任何能打字的地方都能说话输入，本地识别不上传。
- **语音 API 与 Agent 对话**：开放本地 API 供程序调用；可给自己的 Agent 配上「你自己的声音」，语音双向交互。
- **完整语音 I/O 栈**：克隆、合成、识别、播放一体化打包成桌面应用，macOS/Windows/Linux 安装包开箱即用。

**技术栈**
Python 本地模型栈 + 桌面应用（Tauri 类打包），三平台安装包；MIT 协议。

**适用场景**
需要本地语音合成的播客与视频创作者；对隐私敏感、不接受语音上云的听写用户；想给自己的 Agent 或桌面应用加语音接口的开发者。

**推荐理由**
- **语音全栈开源化的稀缺样本**：克隆 + 合成 + 听写 + API 一站集成且全本地，替代散装工具链拼装；作者 jamiepine 是 Standard Notes 联合创始人，工程信誉有底。
- **隐私叙事落在实处**：语音数据全程不出机器，与各家云端语音服务的订阅费和隐私条款形成直接对照；305 天 6.1 万 star 稳步爬升，非冲榜型项目。

> **注意**：克隆他人声音涉及肖像与授权合规，请仅克隆本人或已获授权的声音；本地推理对硬件有门槛，低配机器合成延迟明显；565 个 open issue，声卡与驱动类长尾问题需自查；部分模型权重首次使用需单独下载，体积不小。

> **一句话理解**：像把配音棚搬回家：录 30 秒自己的声音，从此任何文案都能用「你」的声音读出来，而且这间棚子永远不联网。

---

## 5. OpenEvolve —— AlphaEvolve 开源复现：LLM 进化式代码优化器

**一句话简介**：把遗传算法的「变异-选择」交给 LLM 来干：给它一个能打分的程序和一个目标，它一代代改写代码，最后可能进化出比人写的更快的实现——学术圈已经拿它刷出了新数学界纪录。

**仓库信息**
- 地址：https://github.com/algorithmicsuperintelligence/openevolve
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：7.9k（7866）｜ 近期增量：周均 ≈100 ⭐（建库 545 天，破例入选）
- 协议：Apache-2.0 ｜ 官网 / 文档：PyPI 包（月下载 17k+）+ v0.4.1 Release（11-02）+ 完整文档与示例库 + 「被引用论文」清单维护在 README

**核心功能**
- **LLM 驱动的进化搜索**：LLM 充当变异算子迭代改写程序，MAP-Elites 多维质量库与岛屿种群维持多样性，避免过早收敛，专治「局部最优」。
- **任何可打分的问题都能跑**：自定义评估函数即可：算法提速、张量网络缩并优化、组合数学界数搜索、系统性能研究均有公开案例产出新结果。
- **学术界的标准基线**：被数百篇研究论文引用（含安全红队、 extremal combinatorics 等方向），80+ 贡献者，月下载 17k+，复现实验的默认起点。
- **工程完成度高**：PyPI 一键安装、检查点恢复、可视化进化日志、异步并行评估，v0.4.1 持续活跃维护（最近提交 11-25）。

**技术栈**
Python（PyPI 包 openevolve），接入任意 LLM 提供商做变异算子；Apache-2.0 协议。

**适用场景**
想让 LLM 自动优化热点函数与算法性能的工程师；做 LLM 驱动算法发现研究的科研团队；给组合优化、数学猜想搜索等问题寻找自动化工具的研究者。

**推荐理由**
- **AlphaEvolve 的唯一成熟能开源替代**：DeepMind 用 AlphaEvolve 改进了矩阵乘法等经典问题，OpenEvolve 把这套「LLM 进化搜索」范式完整开源，且被学界实际用作基线——不是概念演示，是生产工具。
- **产出可验证的新知识**：README 维护着用它产出新数学界数、系统性能改进的论文清单，每一项都可复现、可核查，含金量在开源算法项目里罕见。

> **注意**：周均增量约 100、低于 300 门槛，破例入选：算法/模型类目本期无达标候选，而该项目是数百篇论文引用的事实标准基线、PyPI 月下载 17k+、v0.4.1 于 11-02 发布且持续活跃提交，价值与热度明显错配；进化搜索大量消耗 LLM 调用，跑一轮成本不低，先用小种群短轮次试跑；效果强依赖评估函数设计，打分写得差进化就跑偏。

> **一句话理解**：像把遗传算法的「变异-选择」外包给 LLM：给一个会打分的程序和一个目标，它自己一代代改代码，几轮之后可能给出比你手写快一倍的版本。

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

- 本期网络形态：GitHub HTTPS 正常（真 Sectigo 证书链），bash 侧 curl + gh api（授权额度 5,000/h）取数全程顺畅；open.feishu.cn openssl 实测 issuer=SANGFOR-AC（中间证书替换），飞书推送以发布脚本实测为准。
- Trending 日榜 16 条 / 周榜 14 条：可用新增仅 n8n-io/nod（周榜 +1,008，直接入选）；其余为已推送仓库回潮或技能/插件合集。补池主力为 Search API 多组查询（created:>2026-01-01 stars:>1000、topic:llm-inference、topic:reinforcement-learning、topic:llm created:>2026-09-01 等）。
- 增量口径：nod 采用 Trending 周榜实测值；其余按「累计 star ÷ 建库天数 × 7」估算周均并标注。openevolve 周均 ≈100 低于门槛，系算法/模型类目无达标候选下的破例入选，理由已写入其卡片注意事项。
- 本期 agent 侧刻意做减法：OmniRoute（cheaper-inference/OmniRoute，90.3k，MIT）数据合格，但 README 以「16.2 亿免费 token/月」等营销话术为主体、需逐条核账，本期让位观察；ultraworkers/claw-code（194.7k）自述为「Agent 无人维护的博物馆展品」，真实性存疑，列入观察期。

**本期按规则排除的候选**

- elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、cathrynlavery/diagram-design、google-labs-code/stitch-skills、mvanhorn/last30days-skill、kajisho5/ffmpeg-skill、tradermonty/claude-trading-skills、Leonxlnx/taste-skill、mjmirza/app-store-compliance —— 技能/插件合集，按口径排除
- toeverything/AFFiNE、reacher-z/Awesome-CUA、whitecircle/halo、Ebony-Vinyl/dsh-our-free-model、qwdwqfwq/topconf-paper-figure-gallery、nikopueringer/CorridorKey2.0 —— NOASSERTION 或资源聚合，排除
- VoltAgent/awesome-design-md —— awesome 列表；GoogleChrome/modern-web-guidance-src —— 规则内容库按内容分发排除；karpathy/autoresearch —— 无 License，排除
- firecrawl/firecrawl、nginx/nginx、openvinotoolkit/openvino、jingyaogong/minimind、HKUDS/CLI-Anything、Tracer-Cloud/opensre、zhouxiaoka/autoclip、XiaoYouChR/Ghost-Downloader-3、backnotprop/plannotator、ChromeDevTools/chrome-devtools-mcp、alibaba/open-code-review、meta/astryx、ag-ui-protocol/ag-ui、dream-num/univer、we-promise/sure、pookjw/HermesEnabler —— 已推送回潮，避让
- paperclipai/paperclip、nexu-io/open-design、tt-a1i/archify、koala73/worldmonitor、jamiepine/voicebox 同类应用候选中让位的 paperclip 等 —— 合格但类目配额让位，列为备选；ultraworkers/claw-code —— 描述异常（自述无人维护展品）观察期

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-26 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
