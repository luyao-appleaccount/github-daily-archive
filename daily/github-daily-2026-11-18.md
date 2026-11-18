# 每日 GitHub 精选 · 2026-11-18（第 24 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（1）、AI Agent（2）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [getarcaneapp/arcane](https://github.com/getarcaneapp/arcane) | 应用项目 | Go | 9.4k | 日榜 +618 ⭐ |
| 2 | [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | 算法/模型 | Python | 66.0k | 日榜 +192 ⭐ |
| 3 | [indexable-inc/blaze](https://github.com/indexable-inc/blaze) | 工程实践 | Rust | 2.4k | 建库 30 天 ≈562 ⭐/周（估算） |
| 4 | [google-research/paper-orchestra](https://github.com/google-research/paper-orchestra) | AI Agent | Python | 3.1k | 日榜 +1,072 ⭐ |
| 5 | [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | AI Agent | Python | 3.4k | 11-17 日榜 +873 ⭐ / 建库均摊 ≈160 ⭐/周（估算，上期遗留优先项） |

---

## 1. Arcane —— 给自托管玩家一个体面的 Docker 管理面板

**一句话简介**：服务器上的十几个容器不该靠一条条 docker ps 去盯：Arcane 把容器、镜像、网络、卷和 Compose 编排装进一个干净的 Web 面板，点几下就知道谁在跑、谁占内存、谁该重启。

**仓库信息**
- 地址：https://github.com/getarcaneapp/arcane
- 类目：应用项目 ｜ 语言：Go ｜ Stars：9.4k（9366）｜ 近期增量：日榜 +618 ⭐
- 协议：BSD-3-Clause ｜ 官网 / 文档：独立文档站 getarcane.app + SBOM 公开页（getarcane.app/sbom）+ Crowdin 多语言翻译 + Snyk 漏洞扫描徽章 + GitHub Actions CI

**核心功能**
- **全套容器运维一屏搞定**：容器的启停/重启/日志/终端、镜像清理、网络与卷管理、Compose 栈的部署与编排全部在 Web 界面完成，覆盖日常 docker 命令的大部分场景。
- **v3 整体重构**：main 分支已是 v3 架构（2.x 走独立维护分支），Go 后端 + SvelteKit 前端分层清晰，长期维护活跃（最近提交就在今天）。
- **为自托管场景设计**：支持多用户与权限、环境隔离，界面轻快不堆功能；对 Homelab 与小型团队服务器来说是「装上就能用」的那类工具。
- **安全与透明做得像正经产品**：公开软件物料清单（SBOM）、接 Snyk 漏洞扫描、Crowdin 社区翻译，文档站覆盖安装、配置与开发指南。

**技术栈**
Go 后端 + SvelteKit/TypeScript 前端；Docker 相关操作走官方 API；支持 Docker Compose 编排；BSD-3-Clause 协议，官方文档站 getarcane.app。

**适用场景**
Homelab / NAS / 小型 VPS 上管理一排自托管服务；不想 SSH 进服务器敲 docker 命令的运维日常；团队里需要一个有权限控制的容器面板而非人手一份 root。

**推荐理由**
- **在 Docker UI 这个老赛道做出了新意**：Portainer 偏企业、Dockge 偏极简，Arcane 用 Go+Svelte 的现代栈把「好看、快、功能全」三个愿望同时满足，日增 600+ 说明踩中了真实需求。
- **工程质量肉眼可见**：SBOM 公开页、Snyk 扫描、多语言、独立文档站——自托管开源项目里少见的正规军配置，长期用心里有底。

> **注意**：main 分支是 v3 大版本，从 2.x 升级需阅读迁移说明（旧版本在 release/2.x.x 分支维护）；管理 Docker 等于授权 root 级操作，面板务必放在内网或加反代认证，不要直接暴露公网；功能请求走 Discussions 而非 Issue。

> **一句话理解**：相当于给一堆集装箱（容器）配了一个调度室的大屏：哪箱在跑、哪箱超重、哪箱要挪走，一眼看清，点一下就办。

---

## 2. MiniMind —— 2 小时、3 块钱，从零训练一个你完全看得懂的 LLM

**一句话简介**：所有大模型课都从「Transformer 架构」讲起然后戛然而止；MiniMind 把预训练、SFT、RLHF、蒸馏整条链路压进 2 小时单卡实验，让「我亲手训过一个 LLM」变成一个花 3 块钱就能兑现的承诺。

**仓库信息**
- 地址：https://github.com/jingyaogong/minimind
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：66.0k（66050）｜ 近期增量：日榜 +192 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：双语 README（中文主笔）+ 文档站 jingyaogong.github.io/minimind + Hugging Face/ModelScope 模型集合 + 在线体验 Space + B 站视频讲解 + 系列 Discussion 拓展

**核心功能**
- **全链路白盒实现**：MoE、数据清洗、Pretrain、SFT、LoRA、RLHF（DPO）、RLAIF（PPO/GRPO/CISPO）、Tool Use、Agentic RL、自适应思考、模型蒸馏——每个环节的代码都从 0 用 PyTorch 原生写，不依赖高层封装。
- **门槛低到离谱**：最小版本约为 GPT-3 的 1/2700 体积，单张消费级 GPU 即可完成训练与复现；README 直说「2 小时」是 3090 跑 1 epoch SFT 的实测、「3 块钱」是对应的 GPU 租用成本。
- **不止一个模型**：主线之外拓展出视觉模态 MiniMind-V、多模态 Omni 版、扩散语言模型 dLM、线性注意力版本，同一个代码底座能横向对比多种架构思路。
- **教程属性拉满**：双语 README 按训练阶段分章讲解，配套在线体验、视频与 Hugging Face 权重，社区 issue 区有大量复现讨论可查。

**技术栈**
纯 PyTorch（无第三方训练框架封装）；Tokenizer/数据集处理与训练脚本齐备；权重托管 Hugging Face 与 ModelScope；Apache-2.0 开源，文档站与双语 README。

**适用场景**
想真正搞懂 LLM 预训练/对齐全流程而不是只会调 API 的工程师与学生；需要一个小到能在笔记本上跑、又能完整走通训练链路的实验基线；教学与内训场景的开箱课程底座。

**推荐理由**
- **把「训练 LLM」从仪式变成作业**：多数复现项目只给代码不给路径，MiniMind 给的是「今天下午就能跑完一遍」的完整脚本与预算表，66k star 是逐年积累的信任票。
- **实现层毫不掺水**：坚持 PyTorch 原生实现意味着你能看到 attention、MoE 路由、PPO 更新的每一行，而不是 import 一个库调个 trainer——这正是它长期被当教材用的原因。

> **注意**：64M 级模型的能力上限明确，别拿它做生产问答；「2 小时/3 元」指最小版本 SFT 单 epoch 的实测口径，跑完整预训练链路需要更多时长与算力；最近提交在 10 月下旬，仍属活跃但迭代节奏不如发布期密集。

> **一句话理解**：像航空专业学生先造一架遥控纸飞机：麻雀虽小，机翼、发动机、操控每个部件都得亲手装一遍——装完再看波音的图纸，每个词都不再抽象。

---

## 3. blaze —— 把 Rust 增量编译提速一个数量级的 cargo 替身

**一句话简介**：Rust 开发最磨人的不是写代码，是改一行等九秒编译；blaze 用一个常驻守护进程把「改完到能跑」压到 20 毫秒级——快到编译器像热重载的前端一样跟手。

**仓库信息**
- 地址：https://github.com/indexable-inc/blaze
- 类目：工程实践 ｜ 语言：Rust ｜ Stars：2.4k（2408）｜ 近期增量：建库 30 天 ≈562 ⭐/周（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：docs/ 目录含安装、工具链、基准测试、发布流程等完整文档 + 官网级 README（含深浅色品牌图）+ stable/canary 双通道发布 + 真实大项目基准数据公开

**核心功能**
- **编辑重建快 9-24 倍**：对 ripgrep / nushell / helix / bun（125 万行 Rust）等真实项目实测：改一个函数再构建，bun 从 cargo 的 9.11s 降到 451ms（20 倍），Linux 平台平均 24 倍提速。
- **像 live reload 一样跑**：首次 blaze build 全量编译后守护进程驻留，此后只重编译被改动的部分；还支持 live edits——存盘约 20ms 后正在运行的程序已在执行新代码。
- **替换而非封装 cargo**：blaze run / test / build / check / bench 与 cargo 命令一一对应，构建不经过 cargo 与 rustc，用自己的工具链（rustup 已有的相同 nightly 则复用）。
- **发布纪律严谨**：stable 通道必须先在 macOS/Linux 上把 zed、servo、bun、Codex CLI 等真实项目全部构建+测试通过才晋级，canary 随构建随发；基准数据全公开可复核。

**技术栈**
Rust 实现（自带工具链分发，约 125-160MB）；macOS Apple Silicon 与 Linux 原生支持；一行脚本安装 curl -fsSL https://ix.dev/blaze | sh；另有 crates.io 与 Nix 安装方式；Apache-2.0。

**适用场景**
任何被 Rust 编译等待折磨的日常开发（大 workspace 反复改-编译循环）；CI 之外的本地快速迭代与 TDD 节奏；做增量编译、构建缓存方向研究的团队可参考其基准方法。

**推荐理由**
- **打的是 Rust 生态最痛的一根刺**：编译慢是 Rust 被吐槽最多的问题，blaze 不做小优化而是换构建模型（守护进程 + 精确增量），量级差异肉眼可感，YC F26 背书也说明商业化路径清晰。
- **宣传口径克制、数据可查**：README 明确标注「这些是 v1 数字，v2 未测」，把测试项目、平台、内存磁盘开销全列出——工具类项目少见的诚实。

> **注意**：尚处早期：仅支持 macOS Apple Silicon 与 Linux，Windows 未覆盖；只接管 build/check/run/test/bench，其余 cargo 命令仍需回 cargo；首次安装要额外下载自有工具链（125-160MB）；v2 尚无官方基准，实际收益依项目结构而异。

> **一句话理解**：相当于把 cargo 的「每次都从冷灶开始炒菜」换成灶台一直热着：菜（代码）改哪样补炒哪样，锅铲起落之间就能上桌。

---

## 4. PaperOrchestra —— Google 开源的「多智能体论文写作流水线」

**一句话简介**：写论文最耗时间的不是实验，是把实验日志变成「像样文稿」的那两周；PaperOrchestra 把这道工序交给一个各司其职的 Agent 管弦乐团：有人翻文献、有人写章节、有人画图、有人校稿。

**仓库信息**
- 地址：https://github.com/google-research/paper-orchestra
- 类目：AI Agent ｜ 语言：Python ｜ Stars：3.1k（3095）｜ 近期增量：日榜 +1,072 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：官方项目主页 yiwen-song.github.io/paper_orchestra + Google Cloud AI Research 团队出品 + README 含安装/环境变量/运行指引 + overview 架构图

**核心功能**
- **五个专职 Agent 流水线**：Outline、Literature Review、Section Writing、Content Refinement、Plotting 各自独立又互相交接，从无格式的前期材料一路推进到投稿模板格式的 LaTeX 全文。
- **文献综述真去检索**：自动搜索、排序并把相关文献整合进稿件（接 Semantic Scholar API），不是让模型凭记忆编引用。
- **图表也归它管**：自动生成实验图表，支持插入概念示意图，产出「带图的完整稿」而不是纯文字骨架。
- **面向投稿模板**：LaTeX 输出对齐目标会议模板，模型可插拔（Gemini / Vertex AI / OpenAI 任选），demo 跑完还能自动发邮件通知。

**技术栈**
Python 3.11 + Conda 环境；多模型接入（GEMINI_API_KEY / VERTEX_AI / OPENAI_API_KEY）；文献检索走 Semantic Scholar API；Apache-2.0，Google Cloud AI Research 官方开源。

**适用场景**
研究人员把实验做完后的成稿阶段（尤其初稿与文献综述）；AI for Science 团队评估「论文自动化」的真实水位；多智能体编排的教学与二次开发参考实现。

**推荐理由**
- **大厂研究团队下场做「论文写作 Agent」**：不是个人周末项目：有正式团队署名、官方主页与架构图，日增 1,000+ 星说明学术界对这类工具的饥渴程度。
- **分工式编排是可复用的设计样本**：把长文档任务拆成专职 Agent 接力（而不是一个 mega-prompt 硬扛），这个模式可直接迁移到技术报告、尽调报告等任何长文档生产场景。

> **注意**：论文生成所用数据集不在仓库内、声称后续单独发布，完整复现需等待；强依赖外部 API（模型 + 文献检索），跑全流程有真实成本；生成稿件仍需人工核对文献真实性——自动化初稿不等于可以直接投稿；37 个 open issue 仍处早期。

> **一句话理解**：像请了一个虚拟写作组：查资料的查资料、执笔的执笔、画图的画图、改稿的改稿，你只需要把实验记录本摊开在桌上。

---

## 5. SkillEvaluator —— NVIDIA 给 Agent 技能生态造的质检仪

**一句话简介**：Agent 技能商城一年冒出几万个「skill」，但没人答得出「装了它到底有没有用」；NVIDIA 的答案是像测药品一样做对照实验——同一批任务，带技能跑一遍、不带再跑一遍，差值就是它真实的效果。

**仓库信息**
- 地址：https://github.com/NVIDIA/SkillEvaluator
- 类目：AI Agent ｜ 语言：Python ｜ Stars：3.4k（3357）｜ 近期增量：11-17 日榜 +873 ⭐ / 建库均摊 ≈160 ⭐/周（估算，上期遗留优先项）
- 协议：Apache-2.0 ｜ 官网 / 文档：docs.nvidia.com 官方文档站 + arXiv 论文 2608.20614 + NVIDIA 开发者博客 + PyPI 正式发包（skillevaluator）+ CI 模板 + NVIDIA Verified Skills 流水线成员

**核心功能**
- **三层评测漏斗**：先做不消耗 LLM key 的静态 quality-check（质量门 + 语义重叠检测），再跑合成评测集，最后做 live 对照评测——量化技能对 agent 行为的真实影响。
- **对照实验量化真效果**：同一批任务分别在「带技能」与「不带技能」下运行，直接测出技能改变了什么结果，把「看起来很厉害」变成可度量的差值。
- **开箱即 CLI + CI**：pip install skillevaluator 即用；官方 CI 模板让每个 skill 改动都自动过检，无需自己维护流水线。
- **生态级卡位**：属 NVIDIA Verified Skills 流水线组件，配官方文档站、arXiv 论文与开发者博客，是对 Agent Skills 开放规范（agentskills.io）的产业级补位。

**技术栈**
Python 3.12-3.14，PyPI 发行；评测分层（静态检查 / 合成数据集 / live agent 对照）；与 NVIDIA Build 免费配额集成；Apache-2.0 + 官方文档站 docs.nvidia.com/skills/skillevaluator。

**适用场景**
企业内发布自研 skill 前的质量/安全门禁；技能市场与技能包作者的回归测试；为「到底该给 agent 配哪些技能」提供数据化决策；Agent 评测方向研究者可参考其对照实验设计。

**推荐理由**
- **补上了技能生态最缺的一环**：技能数量爆炸后，「质量与效果无人背书」是生态最大短板；NVIDIA 用论文 + 文档站 + CI 模板的正规军姿势把它基础设施化，连续两期顺延后本次兑现入选。
- **对照评测方法论本身就有价值**：不评「代码写得好不好」而评「装上后 agent 变好了多少」，这个思路对任何 AI 能力资产（提示词、工具、插件）的验收都成立。

> **注意**：live 对照评测需要模型 key（可用 NVIDIA Build 免费 key）；3.4k star 中近两日增长占比较高，热度尚在爬坡；评测结论依赖所选任务集的代表性，不能替代业务场景实测；对非 Agent Skills 规范的插件需先适配。

> **一句话理解**：相当于给保健品做双盲实验：不是看包装上写了多少功效，而是让「吃的人」和「没吃的人」各跑一次体检，差值才算数。

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

- 类目覆盖：应用 1（arcane）/ 算法模型 1（minimind）/ 工程实践 1（blaze）/ AI Agent 2（paper-orchestra、SkillEvaluator），满足每期 ≥2 类目、单类目 ≤2。
- NVIDIA/SkillEvaluator 为连续两期因类目配额顺延的遗留优先项，本次兑现；其建库均摊周增量约 160 低于 300 门槛，但 11-17 日榜曾 +873 且近 30 天持续提交，作为遗留项入选并如实标注。
- jingyaogong/minimind 属知名项目回潮，但算法/模型类目本期无更优替代：日增 192 达标、22 天前仍有提交、Apache-2.0 且教育价值稀缺，破例入选并注明。
- sveltejs/svelte（日 +477）同为热榜回潮，非新增量场景，按既有口径避让未入选。
- Trending 日榜 15 条 / 周榜 14 条，其中过半为往期已推送仓库或技能/插件合集；工程类目靠 GitHub Search API 补池（blaze 即由 topic:developer-tools 命中）。
- 飞书推送：openssl 实测 open.feishu.cn 证书 issuer 为 SANGFOR-AC（网络层 TLS 拦截仍在），脚本按规则尝试后失败即跳过，未做任何降级校验。

**本期按规则排除的候选**

- elementalsouls/Claude-BugHunter（9.4k，日 +1,005）——82 个 skill 的红队技能合集，按技能包口径排除
- mvanhorn/last30days-skill（69.1k，日 +696）——单件 AI agent skill，同上排除
- google-labs-code/stitch-skills、tradermonty/claude-trading-skills、anthropics/skills、addyosmani/agent-skills、obra/superpowers、cursor/plugins——技能/插件合集，排除
- Nanako0129/sepia（3.9k）——以 Agent Skill 形式分发的写作风格包，同口径排除
- Folkbench/folkbench、fuxicodex/Fuxi——License 为 NOASSERTION，排除
- Ebony-Vinyl/dsh-our-free-model——NOASSERTION + 免费令牌中转，延续排除
- GoogleChrome/modern-web-guidance-src——Web 最佳实践内容规则库，按内容分发口径延续排除
- alibaba/open-code-review、dream-num/univer、ag-ui-protocol/ag-ui、backnotprop/plannotator、Tencent/LoopForge、affaan-m/ECC、we-promise/sure 等——往期已推送，去重排除

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-18 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
