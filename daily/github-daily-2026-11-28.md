# 每日 GitHub 精选 · 2026-11-28（第 32 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（2）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [nexu-io/open-design](https://github.com/nexu-io/open-design) | 应用项目 | TypeScript | 110.0k | 周均 ≈3,596 ⭐（建库 214 天，Search 补池） |
| 2 | [RunanywhereAI/trnrt](https://github.com/RunanywhereAI/trnrt) | 算法/模型 | Python | 1.7k | 周均 ≈401 ⭐（建库 29 天，Search 补池） |
| 3 | [shirudo-dev/shirudo](https://github.com/shirudo-dev/shirudo) | 工程实践 | C | 2.4k | 周均 ≈368 ⭐（建库 46 天，Search 补池） |
| 4 | [getagentseal/codeburn](https://github.com/getagentseal/codeburn) | 工程实践 | TypeScript | 11.9k | 周均 ≈366 ⭐（建库 228 天，Search 补池） |
| 5 | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | AI Agent | TypeScript | 117.7k | 周均 ≈3,039 ⭐（建库 271 天，Search 补池） |

---

## 1. OpenDesign —— 第一个协作式 AI 设计 Agent 工作区

**一句话简介**：设计类 AI 工具大多是「一句话出图」的单发模式，产出的界面和团队真正的设计规范无关。OpenDesign 把设计系统、原型、反馈、Agent 迭代放进同一个项目：AI 出的每一版都要过你们家的设计系统。

**仓库信息**
- 地址：https://github.com/nexu-io/open-design
- 类目：应用项目 ｜ 语言：TypeScript ｜ Stars：110.0k（109937）｜ 近期增量：周均 ≈3,596 ⭐（建库 214 天，Search 补池）
- 协议：Apache-2.0 ｜ 官网 / 文档：官网 open-design.ai + QUICKSTART（三条命令起步）+ 13 种语言 README（含简体中文）+ 双周节奏 Release（open-design-v0.27.2，11-19）+ Discord 社区

**核心功能**
- **协作式设计工作流**：从一个 brief 开始，用你的编码 Agent 或 OpenDesign Cloud 生成遵循设计系统的原型；团队在同一项目里反馈，Agent 再迭代——设计资产、媒体与原型集中管理，不再散落在聊天记录里。
- **开放可扩展的工作流**：Apache-2.0 开源：技能（skills）、设计模板、设计系统与插件都可检查、可魔改，接入自己的编码 Agent（Codex、Claude Code、DSH、OpenCode）或官方 Cloud。
- **多形态产出**：原型、网站、应用、仪表盘、演示、动效、图像与视频在一个工作区完成，跨形态资产共享同一套设计上下文。
- **工程配套齐**：本地优先 + Cloud 双形态，QUICKSTART 三条命令起步，13 种语言 README，release 节奏稳定（v0.27.x）。

**技术栈**
TypeScript + React；Apache-2.0；本地应用 + 托管 Cloud；官网与文档、固定节奏 Release（v0.27.2，2026-11-19）、Discord 社区运营。

**适用场景**
需要 AI 产出「符合自家设计系统」的前端原型而非一次性 demo 的产品与设计团队；想把设计资产、原型与团队反馈收进同一处的协作场景；想把设计流程接进自有编码 Agent 工作流的工程团队。

**推荐理由**
- **「设计系统一致性」是真痛点**：多数 AI 生成工具产出的界面与团队规范脱节，后期返工成本极高。OpenDesign 把设计系统作为一等公民放进 Agent 工作流，方向比「更炫的生成」更解决实际问题。
- **开放程度对得起星数**：编辑工作流以 Apache-2.0 开源，skills/模板/插件可审查；110k star、双周 release 与多语言文档说明是真实在用的产品，不是空壳。

> **注意**：README 顶部「庆祝 10 万星、Cloud 点数翻倍」营销色彩明显，开源与 Cloud 是两条线，自托管完整体验需自行评估；AI 产出质量强依赖接入的模型与 Agent；版本迭代快（v0.27.x），跟进成本不低；「第一个」是营销口径，同类竞品在快速出现。

> **一句话理解**：像给外包团队发了一本你公司的 VI 手册，并要求每一稿都按手册交——AI 出的不再是「好看的图」，而是「你们家的界面」。

---

## 2. TrnRT —— 跑在 AWS Trainium 上的开源推理引擎

**一句话简介**：GPU 不是推理的唯一答案。TrnRT 把解码步骤编成「一层约半个 kernel」的 NKI megakernel，在 AWS Trainium2 上提供 OpenAI 兼容 API——而且 README 里专门有一节「我们哪里比 H200 差」。

**仓库信息**
- 地址：https://github.com/RunanywhereAI/trnrt
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：1.7k（1662）｜ 近期增量：周均 ≈401 ⭐（建库 29 天，Search 补池）
- 协议：Apache-2.0 ｜ 官网 / 文档：docs/RESULTS.md（逐表给来源与口径的基准报告）+ docs/MEGAKERNELS.md + 官方博客复盘 + CI + OpenSSF Scorecard + v0.2.0 Release（11-25）

**核心功能**
- **NKI 层级 megakernel**：解码跑成约每层半个 kernel 的 megakernel（约一个 kernel 覆盖半层），batch-8 解码步从 32.2ms 压到 24ms；单台 trn2.48xlarge 即可服务，支持 1M-token 上下文。
- **性价比数据公开可查**：在 InferenceX AgentX（重放真实编码 Agent 会话）上实测：1-16 并发用户每美元 token 数超过 8 卡 H200 节点，12-32 并发为 H100 节点的 3.5-5.2 倍，价格按 AWS Capacity Block 牌价，每张表都附来源。
- **跨设备前缀缓存**：prefix cache 打通 device/host 内存，编码 Agent 这类长会话、高前缀复用的场景收益最大。
- **工程配套认真**：CI、OpenSSF Scorecard、megakernel 原理文档、博客复盘；GLM-5.3-Flash 为首个支持模型，更多开源模型在路上。

**技术栈**
Python 3.13 + AWS Neuron SDK 2.32（NKI）+ Trainium2；OpenAI 兼容 API；Apache-2.0；v0.2.0（2026-11-25）。

**适用场景**
在 AWS 上有 Trainium 配额、想压低推理成本的团队；研究「非 GPU 芯片跑 LLM」的 infra 工程师；为编码 Agent 服务做容量规划、想要一条 GPU 之外的比价曲线的场景。

**推荐理由**
- **罕见的诚实基准**：README 专设「Where we're behind」：单用户交互延迟只有 H200 的 1/4 到 1/2、24+ 并发时性价比反输 H200、无前缀复用的短序列更差——把自己短板写全的仓库，比跑分截图可信得多。
- **稀缺领域的高质量开源**：Trainium 生态的推理引擎选择极少，NKI megakernel 的写法与逐表给口径的基准方法论本身就是难得的学习材料。

> **注意**：硬件门槛高：必须有 trn2.48xlarge（Capacity Block 牌价 $35.76/实例小时），普通开发者无法复现；目前只正式支持 GLM-5.3-Flash 一个模型；v0.2.0 的 device 实测仍在排队，部分数字来自与 release 图等价的内部构建（README 已注明）；交互延迟敏感的场景慎选，它的强项是并发吞吐性价比。

> **一句话理解**：像一家只开一条产品线的工厂：机器型号固定（Trainium2）、只产一种货（GLM-5.3-Flash），但把每个工时和电费都贴在墙上——便宜是真的便宜，慢也是真的慢。

---

## 3. Shirudo —— OpenAI × Cisco 的内核级安全盾

**一句话简介**：内核安全通常靠「发现漏洞、出补丁、等重启」，窗口期就是风险期。Shirudo 换了个思路：开机后内核只接受签名 loader 装的 BPF 程序，缓解措施以签名微补丁随时下发，机器改到哪一步都有 TPM 签名的证据。

**仓库信息**
- 地址：https://github.com/shirudo-dev/shirudo
- 类目：工程实践 ｜ 语言：C ｜ Stars：2.4k（2421）｜ 近期增量：周均 ≈368 ⭐（建库 46 天，Search 补池）
- 协议：BSD-2-Clause ｜ 官网 / 文档：完整文档站 docs.shirudo.dev（quickstart / concepts / system-requirements）+ OpenAI 与 Cisco（Isovalent）官方博客发布公告 + CI（x86-64 全测试层 + arm64）+ 本地 VM 试用镜像

**核心功能**
- **签名 BPF 供应链**：boot 时初始化后，用户态加载 BPF 必须经过签名 loader——任何未签名的 eBPF 程序注入直接被内核拒绝，把近年最热的 BPF 攻击面关进签名门。
- **upatches 微补丁**：运维下发签名的「微补丁」，在内核钩子处封堵易受攻击的路径，也有 Java 应用层的 upatch；不用停机重启即可上线缓解措施。
- **TPM 证据核验**：用 TPM 2.0 签名的证据远程验证目标机器的 upatch 状态，合规审计从「口头承诺」变成机器可校验。
- **从观测到加固一条龙**：自带 kernel-obs 观测包（进程执行、网络活动、提权行为）；用例明确覆盖容器、Kubernetes Pod 与 LLM Agent 的系统加固。

**技术栈**
C（内核侧）+ eBPF + TPM 2.0；文档站 docs.shirudo.dev；CI 覆盖 x86-64 全测试层与 arm64 主机测试；BSD-2-Clause；OpenAI 与 Cisco 联合发布。

**适用场景**
对内核供应链有硬要求（禁止未签名 eBPF）的平台与安全团队；要给容器 / K8s / LLM Agent 沙箱加运行时加固的基础设施工程；设备更新周期长、需要远程下发缓解并核验状态的边缘场景。

**推荐理由**
- **大厂背书 + 方向稀缺**：OpenAI 与 Cisco（Isovalent，eBPF 的发源地）联合发布并开源，把「BPF 供应链安全」这个热点攻击面做成平台级方案，且代码可审计。
- **一个信任模型装下三件事**：观测（kernel-obs）、缓解（upatch）、审计（TPM 证据）在同一个签名信任链里，不必把三个不同出身的工具拼在一起。

> **注意**：pre-release：生产目标需要带签名 loader ABI 的内核补丁 + TPM 2.0，多数发行版开箱不可用，先按官方 VM 在本地试；release tag 还是 CI 构建号（test-kernel-*），尚无正式版本化发布；riscv64 目标校验未完成；eBPF 能力与内核版本强耦合，内核升级需同步评估兼容性。

> **一句话理解**：像给大楼装了一套「只有登记过的施工队才能动墙」的门禁：平时谁也凿不开承重墙；物业要修就发一张有签名的施工单（upatch），大堂再放一台盖章机（TPM），任何人都能验证这栋楼改到了哪一步。

---

## 4. CodeBurn —— 看清 AI 编码花销去哪了

**一句话简介**：账单只给一个月度总数，不说钱花在哪个项目、哪个模型、哪次跑偏的任务上。CodeBurn 直接读各编码工具自己落盘的 session 文件，本地算出按项目 / 模型 / 任务的分解，`npx codeburn` 一条命令出报告。

**仓库信息**
- 地址：https://github.com/getagentseal/codeburn
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：11.9k（11938）｜ 近期增量：周均 ≈366 ⭐（建库 228 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：npm 与 Homebrew 分发 + 全平台桌面安装包（macOS Developer ID 签名公证 / Windows 商店 / Linux deb、rpm、AppImage）+ v0.9.28 Release + Product Hunt 发布 + Discord

**核心功能**
- **37 个工具一网打尽**：Claude Code、Codex、Cursor、Gemini 等主流编码 Agent 的 session 文件都读，42 个集成持续核对；每个工具每次调用都会写 session 文件，里面的 token 与模型信息就是现成的账本。
- **维度切得细**：按项目、按模型、按任务/会话聚合，能看出「哪部分花费是被浪费的」——反复重试、超长上下文、低效模型混用，这些账单永远不告诉你的东西。
- **零上传、纯本地**：分析在本机完成，session 文件不出门；不用接云账单 API 也能算出分解。
- **分发顺手**：`npx codeburn` 免安装试用；npm / brew 全局安装；macOS 构建经 Apple 公证，Windows / Linux 全渠道桌面包。

**技术栈**
TypeScript，Node ≥22.15；本地解析各工具 session 文件后聚合；MIT；npm + Homebrew + 全平台桌面安装包；v0.9.28（2026-11-08）。

**适用场景**
同时开多个编码 Agent、月底被账单吓一跳的开发者；要给团队做 AI 编码成本核算与预算的 tech lead；想评估「哪个模型 / 哪种用法性价比更高」的采购与选型决策。

**推荐理由**
- **填了真空白**：云账单聚合与本地 session 明细之间一直缺一个「按工程视角分解」的工具，CodeBurn 是这个品类里覆盖面最全的（37 工具 / 42 集成），且迭代活跃。
- **本地优先，隐私干净**：不上传 session 数据、不依赖云 API，读完即走；对有数据合规要求的团队友好。

> **注意**：版本 0.9.x 未到 1.0：各编码工具的 session 文件格式一变，解析就可能失效，升级工具后留意兼容公告；依赖各工具落盘 session 的路径约定，自定义安装位置要手动配置；只做分析不拦截花费，想「防超支」还需另配预算闸门。

> **一句话理解**：像给家里每个插座都装了分电表：总账单只说这个月用了多少度电，它告诉你空调、热水器、和那台忘了关的服务器各吃掉多少。

---

## 5. Paperclip —— 给 Agent 团队开一家「公司」

**一句话简介**：「如果 OpenClaw 是员工，Paperclip 就是公司。」它不是又一个 Agent 框架，而是管 Agent 的组织系统：目标、角色、权限、预算、审批、考核——Agent 7×24 自主干活，人只在关键节点出手。

**仓库信息**
- 地址：https://github.com/paperclipai/paperclip
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：117.7k（117680）｜ 近期增量：周均 ≈3,039 ⭐（建库 271 天，Search 补池）
- 协议：MIT ｜ 官网 / 文档：文档站 docs.paperclip.ing（含 adapter 总览）+ 日期版 Release（v2026.1117，11-18）+ Superagent 安全态势扫描认证 + Discord / X 社区 + Cloud waitlist

**核心功能**
- **四大支柱**：Agentic 任务管理（声明意图 → Agent 干活 → 人验产出）、Agent 组织架构（角色 / 权限 / 边界 / 秘密范围）、Agent 培训（Skill Studio、evals、绩效考核）、Agentic OS（跨供应商运行时、沙箱、SSO / RBAC / 成本控制）。
- **Bring Your Own Agent**：OpenClaw、Claude Code、Codex、Cursor + Cloud、Gemini CLI、OpenCode、Kimi Code 等十余种 Agent 接入，「能发心跳就能雇佣」；自定义进程、HTTP 端点与 adapter 包可继续扩展。
- **目标驱动，而非 PR 驱动**：定目标（「把 AI 笔记应用做到 $1M MRR」）→ 招团队（CEO / CTO / 工程师，任意 bot 任意供应商）→ 批策略、设预算、看板监控，管理粒度是业务目标而不是单次提交。
- **治理与成本内建**：预算与成本监控、审批门、审计轨迹、按连接与身份的权限控制；安全态势经 Superagent 扫描认证。

**技术栈**
Node.js 服务端 + React UI；MIT；文档站 docs.paperclip.ing；按日期版本发布（v2026.1117）；Cloud 版 waitlist 中，可自托管。

**适用场景**
同时开 20 个 Claude Code 终端已管不过来的重度 Agent 用户；想把多 Agent 协作从「个人作坊」升级为有组织、有预算、有审计的团队生产方式；要让 Agent 7×24 自主运行但保留人工审批与审计的团队。

**推荐理由**
- **卡位准确：管 Agent 的「管理层」**：Agent 框架已经过剩，缺的是把散装 Agent 组成组织的那一层——org chart、预算、审批、考核这些「公司机制」被做成产品，这个思路在同品类里独一份。
- **规模即信任信号**：117.7k star、双周节奏的日期版 release、十余种 Agent adapter、安全扫描认证——成熟度在同类里属第一梯队。

> **注意**：6,806 个 open issue：项目扩张极快但 issue 积压严重，遇到问题先搜 issue 再动手；「AI 自主经营业务」的叙事大于多数团队的实际需求，普通用户更实用的是它的任务管理与看板部分；Cloud 版需排队 waitlist，自托管要自己维护 Node 服务与各 Agent 运行环境；多 Agent 自动化烧钱快，预算上限务必先设。

> **一句话理解**：像给一群自由散漫的外包程序员盖了一间公司：有工牌（身份权限）、有 KPI（目标与考核）、有财务卡预算、有前台审进出——AI 员工还是那些 AI 员工，但终于有人管了。

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

- 本期网络形态：GitHub HTTPS 正常（gh api 授权额度充足，取数全程顺畅）；open.feishu.cn 证书为真 RapidSSL 链、HTTP 层可达——连续多期的 TLS 拦截本期未复现，飞书是否送达以发布脚本实测为准。
- Trending 日榜 16 条，可用新增为零（全部为已推送回潮或技能 / 插件合集，连续多期）；周榜页 curl 25s 超时 3 次未取到。5 个入选全部来自上期遗留备选与 Search API 补池（created:>2026-09-01 stars:>2500、topic:llm-inference 等），增量均为「累计 star ÷ 建库天数 × 7」估算口径，已在卡片逐条标注。
- 类目配置：应用 1 / 算法 1 / 工程 2 / Agent 1，四类全覆盖、单类目不超 2 个。
- 本期兑现 11-27 期遗留备选 4 个：RunanywhereAI/trnrt、shirudo-dev/shirudo、getagentseal/codeburn、paperclipai/paperclip。tt-a1i/archify 核验时发现描述自述为「An Agent Skill for Claude Code, Codex, Cursor」，按技能分发口径排除，从备选清单移除。
- 上期遗留 cheaper-inference/OmniRoute 本期继续观察未入选：「16.2 亿免费 token/月」等营销话术逐条核账成本高，暂不为其背书。

**本期按规则排除的候选**

- 技能 / 插件合集，按口径排除：elementalsouls/Claude-BugHunter、obra/superpowers、cursor/plugins、cathrynlavery/diagram-design、mvanhorn/last30days-skill、google-labs-code/stitch-skills、mjmirza/app-store-compliance、tt-a1i/archify（自述 Agent Skill 分发）
- 知名回潮避让：firecrawl/firecrawl、nginx/nginx、openvinotoolkit/openvino、HKUDS/CLI-Anything、jingyaogong/minimind、Tracer-Cloud/opensre、XiaoYouChR/Ghost-Downloader-3、zhouxiaoka/autoclip
- License 缺失或 NOASSERTION，排除：toeverything/AFFiNE、lemomo-ai/lemo-opuscar、Zagitta/gpu-unlock、Ebony-Vinyl/dsh-our-free-model（免费令牌中转，另有 ToS 风险）
- storytold 整族（photocraft / pdfcraft / filmcraft / craft-anything）—— 同账号批量同构发布，延续往期口径整簇排除
- 教程 / 书稿 / 资料聚合，排除：eternity4719/HowToLiveBetter、bojieli/ai-infra-book
- 继续观察：cheaper-inference/OmniRoute（90.8k，「免费 token」营销话术待逐条核账）

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-28 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
