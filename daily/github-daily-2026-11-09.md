# 每日 GitHub 精选 · 2026-11-09（第 20 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [sherlock-project/sherlock](https://github.com/sherlock-project/sherlock) | 应用项目 | Python | 103.8k | 日榜 +2,373 ⭐ |
| 2 | [meta/astryx](https://github.com/meta/astryx) | 应用项目 | TypeScript | 17.0k | 日榜 +875 ⭐ |
| 3 | [github/spec-kit](https://github.com/github/spec-kit) | 工程实践 | Python | 148.7k | 周榜 +4,045 ⭐ |
| 4 | [mw00/project-maya](https://github.com/mw00/project-maya) | 算法/模型 | Cuda | 2.7k | 建库 34 天 ≈557/周（估算） |
| 5 | [microsoft/TokenEconomizer](https://github.com/microsoft/TokenEconomizer) | AI Agent | Python | 5.3k | 建库 27 天 ≈1,372/周（估算） |

---

## 1. Sherlock —— 输一个用户名，在 400+ 社交网络里找出他注册过哪些账号

**一句话简介**：查一个网名在全网的所有马甲，过去要手动开几十个网站挨个搜；现在一条命令，几分钟出清单。

**仓库信息**
- 地址：https://github.com/sherlock-project/sherlock
- 类目：应用项目 ｜ 语言：Python ｜ Stars：103.8k（103786）｜ 近期增量：日榜 +2,373 ⭐
- 协议：MIT ｜ 官网 / 文档：官方文档站 sherlockproject.xyz（安装 / 用法 / 贡献三页齐）+ 官方 Docker 镜像 + PyPI / Homebrew / dnf / Kali / BlackArch 多路分发 + v0.16.2 正式 release

**核心功能**
- **400+ 站点并行排查**：站点清单收在仓内 `data.json`（含 URL 模板与「账号存在」的判定特征），逐站异步请求比对，命中即列出；清单由社区持续维护，也可用 `--json` 加载自己的清单或直接引用上游 PR 编号。
- **结果多格式落盘**：默认按用户名生成独立 txt，可切 `--csv` / `--xlsx`；`--print-all` 连「没找到」的站点也打印，方便人工复核判定质量。
- **代理与调试友好**：`--proxy` 支持 socks5/http，配合 `--timeout` 对慢站点兜底；`--dump-response` 把 HTTP 响应直接打到 stdout，用来定位某个站点为什么误报。
- **用户名变体自动展开**：`{}` 占位符把同一个网名按 `_` / `-` / `.` 变体批量查一遍，覆盖「jon.doe」和「jon_doe」不是同一个人的常见情况。
- **十年持续维护**：2018 年建库至今仍在活跃提交（最近一次 11-08），v0.16 系列持续发版，安装方式覆盖 pipx / Docker / 各发行版包管理器。

**技术栈**
Python 3 异步请求；分发走 pipx / pip / uv、官方 Docker 镜像（sherlock/sherlock）、dnf 与社区维护的 Debian / Homebrew / Kali / BlackArch 包；输出 txt / csv / xlsx；判定特征与站点清单均为纯 JSON，可离线自定义。

**适用场景**
安全从业者的账号侦察与外部资产梳理；品牌与个人舆情的同名账号监测；招聘背调、尽调场景的交叉验证；找回自己多年前注册过但想不起在哪些平台的旧账号。

**推荐理由**
- **老牌且活得很好**：OSINT 领域的教科书级工具，10 万+ star 不是蹭热点堆出来的：十年间判定特征、站点清单、安装链路一直在维护，最近提交就在昨天。
- **上手成本几乎为零**：一条 `pipx install sherlock-project` 加一个用户名参数就出结果，不用注册、不用 API key；这是它长期被各类安全课程引用的根因。

> **注意**：误报不可避免：部分站点对「不存在」也返回通用页面，`--dump-response` 可逐站核查，`--ignore-exclusions` 会放大误报不要日常开；ParrotOS 与 Ubuntu 24.04 的第三方包已知损坏，官方建议改用 pipx / Docker；NSFW 站点默认排除，需 `--nsfw` 显式开启；用于排查他人账号时注意当地法律与平台条款，别拿来做骚扰或人肉；最新 release v0.16.2 发布于 2026-09-08，之后的修复走 master 直接分发。

> **一句话理解**：像给每个社交网站群发同一句「这个网名是你吗」，谁回了「是」就记下来——只不过「回信」是靠 HTTP 状态码和页面特征判读的。

---

## 2. Astryx —— Meta 内部最大设计系统开源：150+ 组件，人和 AI Agent 用同一套工具

**一句话简介**：组件库的下一场竞赛不是谁更漂亮，而是谁能让 Claude Code 和人类设计师读同一份说明书还不打架。

**仓库信息**
- 地址：https://github.com/meta/astryx
- 类目：应用项目 ｜ 语言：TypeScript ｜ Stars：17.0k（16988）｜ 近期增量：日榜 +875 ⭐
- 协议：MIT ｜ 官网 / 文档：astryx.atmeta.com 文档站 + 在线 Storybook + 浏览器 Sandbox + npm @astryxdesign/core 全家桶 + 七套主题包 + v0.7.11 release（2026-11-07，两天前）

**核心功能**
- **内部结构全部开放**：组件按「可任意层级的组合」设计，底层积木直接导出；要改得更深时 `swizzle` 把某个组件的完整源码 eject 进你的项目，从「用别人的」变成「拥有自己的」。
- **零样式锁定**：内部用 StyleX 写样式，但对使用者完全不可见：覆盖样式用 `className` 配 Tailwind、CSS Modules 或纯 CSS 都行，不必为它引入新的样式体系。
- **主题即 CSS 变量**：整套换肤就是一组 custom property 覆盖，设计师不用 fork、不用包裹组件源码就能让 Astryx 变成自家品牌的样子；官方自带七套主题（从 neutral 到 y2k）。
- **为人和 Agent 共同设计**：CLI、文档与组件 API 三者对齐：全局装一次 CLI，任何文件夹里 `astryx docs ...` / `astryx component --list` 都能给编码代理喂出与版本一致的说明——人查的和 AI 查的是同一份参考。
- **React 19 开箱即用**：导入预构建 CSS + 主题 Provider 就能跑，无 build 插件、无 PostCSS / Babel 配置；Next.js / Vite / CDN 各有现成接入指南。

**技术栈**
React 19+ / TypeScript；样式层 StyleX（编译期提取、运行时零开销）；@astryxdesign/core + cli + build + 七主题包经 npm 分发；文档站 / Storybook / Sandbox 全套在线；图表组件（vega/charts）还在 canary dist-tag。

**适用场景**
给 React 项目换一套开箱即用的无障碍组件库；团队要做品牌级主题定制而不想维护 fork；把设计规范喂给 AI 编码代理、让生成的 UI 风格统一；从零搭内部平台 / SaaS 前端。

**推荐理由**
- **八年内部实战背书**：这不是从零攒的开源 demo，而是 Meta 内部使用量最大的设计系统（13,000+ 应用），工程成熟度与无障碍覆盖是真实产品环境磨出来的。
- **踩中 2026 年前端的真实工作方式**：「人和 Agent 同一工具链」不是口号：CLI 输出直接面向编码代理，文档与版本强绑定，解决的是「AI 生成的 UI 各画各的」这个当下最普遍的痛点。

> **注意**：明确处于 Beta，API 可能变动，先别上关键生产链路；硬性要求 React 19+，老项目要先把 React 升上去；自己改源码构建时需要 StyleX build 插件（使用预构建产物则无感）；图表组件尚无稳定版；由 Meta 主导，后续社区治理与路线图话语权分布还需观察。

> **一句话理解**：以前的组件库像精装房：好看，但不能砸墙。Astryx 把图纸和工具箱一起交给你——想改哪面墙，swizzle 一下，源码就搬进你家了。

---

## 3. Spec Kit —— GitHub 官方「规格驱动开发」工具包：先写清要什么，再让编码 Agent 动手

**一句话简介**：Agent 写代码不可怕，可怕的是它自信满满地解错题；Spec Kit 的思路是把「题目本身」标准化，让 Agent 没机会自由发挥。

**仓库信息**
- 地址：https://github.com/github/spec-kit
- 类目：工程实践 ｜ 语言：Python ｜ Stars：148.7k（148735）｜ 近期增量：周榜 +4,045 ⭐
- 协议：MIT ｜ 官网 / 文档：GitHub Pages 文档站（扩展 / 预设 / 工作流 / 目录四大体系各有专页）+ 四语 README（英 / 简中 / 日 / 韩）+ specify CLI 经 uv 分发 + v1.3.2 release（2026-11-06）

**核心功能**
- **SDD 核心流程**：constitution → specify → clarify → plan → tasks → implement：每一步产物都落盘可评审，需求不再是聊天记录里的一句话，而是能进 PR 的规格文档。
- **三类独立入口**：建功能走 SDD；修 bug 走「评估原因 → 界定修复 → 记录验证」的扩展流程；判断想法值不值得投入走「证据支持的 go / clarify / stop」决策——互相独立、按需取用，不是强制流水线。
- **可组合的机制层**：extension / preset / workflow / bundle / catalog 五类原语：组织可以塞进自己的质量门与合规标准、监听编码代理生命周期事件、给命令挂前后置 hook，也能自托管私有组件目录。
- **多代理统一接入**：Copilot、Claude Code、Codex 等主流编码代理一键初始化集成，同一份规格在换代理时不用重写。
- **离线与私有化**：air-gapped 安装、本地组件源、私有目录鉴权都有专章，企业内网不是二等公民。

**技术栈**
Python 3.11+ 的 specify CLI（uv tool install 分发）；流程本体是模板 + 命令 + hook 的组合系统，扩展运行时支持生命周期事件；文档站托管在 GitHub Pages；社区目录可检索，组织可加自己的审计源。

**适用场景**
团队要把 AI 编码从「凭感觉生成」升级成有评审入口的工程流程；企业要把安全 / 合规门塞进 Agent 工作流；给多个编码代理统一协作规范；开源项目给贡献者一套可复现的 PR 流程。

**推荐理由**
- **方法论的事实标准实现**：GitHub 官方出品、148.7k star、四语文档：提到规格驱动开发（SDD），Spec Kit 就是绕不开的参照系，生态位类似当年的 Git Flow。
- **已经长成流程平台**：v1.3.2 一周内持续发版，扩展 / 目录 / 工作流 overlay 让它从「一套 Markdown 模板」进化成可运营、可定制、可审计的流程系统，而不只是口号。

> **注意**：引入的是流程税：小改动走完整 SDD 会明显变重，官方也提供了 bug 修复这类轻量入口，按任务类型选；各编码代理的集成深度不一，切换代理时规格文件的兼容性要自查；catalog 里的社区组件「不是审计或背书」，安装前必须自己读代码；依赖 Python 3.11+ 与 uv。

> **一句话理解**：以前给 Agent 下需求像在便签上写菜名，做出来靠缘分；Spec Kit 是把菜单、食谱、验收标准全钉在厨房墙上，每道工序做完都要签字。

---

## 4. Project Maya —— 一块消费级 GPU 跑 321B/748B 开源巨兽：MoE 专家冷热分层调度

**一句话简介**：模型太大装不下？它不压缩想法，只优化「哪块专家该住在哪」——把 SSD 当第三级显存用。

**仓库信息**
- 地址：https://github.com/mw00/project-maya
- 类目：算法/模型 ｜ 语言：Cuda ｜ Stars：2.7k（2706）｜ 近期增量：建库 34 天 ≈557/周（估算）
- 协议：MIT ｜ 官网 / 文档：四语 README（英 / 日 / 简中 / 葡）+ docs/ 全量文档 + HuggingFace 上三模型的 Maya 量化全家桶 + v1.1.56 高频 release（2026-11-06）+ setup.sh 一键部署

**核心功能**
- **MoE 专家冷热分层**：按对话热度把专家权重分三级驻留：当常用的留在 GPU 显存、次热的进 RAM、其余放 NVMe，边聊边搬；启动时实测你的 GPU / CPU / RAM / SSD 并自动调参，不要求背配置。
- **三引擎三巨兽**：GLM-5.3-Flash（321B/18B 激活）、DeepSeek-V4.1-Flash-1017（748B）、MiniMax-M3.1-Flash（428B/23B 激活）各有专属引擎，每个模型按显存池分 XS / S / M / L 四档量化。
- **保真度公开可查**：自研量化保留 FP8 模型 97.7–99.2% 零样本精度；DeepSeek 档逐 token 一致率 92.6%、MiniMax 87.6%——数据直接写在 README，不是「几乎无损」的营销话术。
- **双 API 即插即用**：OpenAI 与 Anthropic 兼容接口都带工具调用，编码代理可以直接指到 `127.0.0.1:8080`；最多 8 路并发，够一台工作站几个人或几个代理同时用。
- **整机交付**：浏览器聊天 + 实时监控、三模型生图、思考等级、模型下载 / 加载 / 删除管理页、Turbo 按钮，`./setup.sh` 问答式装完即启动。

**技术栈**
CUDA 为主（支持 AMD ROCm 与 Windows）；GGUF 量化；硬件弹性从单张消费卡到 16 卡（实测双 RTX 5090 + 4090 达 149 tok/s、单 5090 30+ tok/s）；HuggingFace 直连下载，setup.sh / START-MAYA.bat 双平台一键部署。

**适用场景**
不想为 API 付费或担心数据出域、要在本地跑 300B+ 级模型的个人与工作室；给编码代理供本地推理后端；多卡工作站的离线推理服务；量化保真度与 MoE 调度的研究参考。

**推荐理由**
- **把数据中心级模型拉到桌面**：「本地跑 748B」是今年本地推理最硬的痒点，34 天 2,706 star 说明需求真实；关键是它公开了各档硬件的实测 tok/s 与精度对比，可验证、可复现。
- **工程完成度罕见**：MIT 协议、以天为单位的 release 节奏、四语文档、三模型量化全家桶，一个社区项目做到了商业工具的交付标准。

> **注意**：内存需求依然不低：GLM Maya-S 约 96.5GB（RAM+VRAM 合计），DeepSeek Maya-XS 也要 277GB 级内存池，SSD 慢会直接拖垮首 token 延迟；量化档位越低精度损耗越大（MiniMax Maya-S 一致率 87.6%），精度敏感任务请选高档位；ROCm / Windows 支持在快速演进中；321B/748B 是总参数，MoE 每步实际激活仅 18–23B——这正是它在消费级硬件上能跑的前提。

> **一句话理解**：MoE 模型像一个 748 人的专家团队，每次提问只有 20 来人上台；Maya 干的是剧场座位调度——当红专家坐前排（显存），候补坐观众席（内存），没戏份的在外头候场（SSD），散客一喊随时换人。

---

## 5. TokenEconomizer —— 给编码代理省 token 的黑盒外挂：实测平均降费 18–31%

**一句话简介**：编码代理烧钱的三种姿势：每次重新摸清仓库、带着一堆用不上的工具上场、同一条报错撞三遍——它专治这三样。

**仓库信息**
- 地址：https://github.com/microsoft/TokenEconomizer
- 类目：AI Agent ｜ 语言：Python ｜ Stars：5.3k（5290）｜ 近期增量：建库 27 天 ≈1,372/周（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：arXiv 论文（2610.22732）+ 项目页 tokeneconomizer.github.io + README 机制逐条详解（含全部默认阈值）+ v0.1.0 release（2026-10-26）+ UC Berkeley × Microsoft Research 联合署名

**核心功能**
- **micro-skills：仓库小抄**：跨会话沉淀「这仓库怎么干活」的事实：测试得用 `python -m pytest`、某命令要哪个环境变量、生成文件在哪。事实要三次会话证实才生效、被后续会话反驳即退役——小抄本身也会过期。
- **工具裁剪：别带着没人用的工具上场**：每个已加载工具的定义都随每次请求重复计费；连续 p 次提示跨 m 个会话没人用的工具，直接不进下一轮请求，一条命令随时召回。
- **失败循环干预**：同一轮里反复撞同一种失败时，判官模型判断是否卡死；置信度超过阈值就往上下文里注入一句「换个思路」的提示，每轮最多一次；还不行就明确告诉你该人工停了——它自己从不替你停任务。
- **零侵入外挂**：以插件形式接入 Claude Code / Codex / GitHub Copilot CLI / Pi（另实验性支持 opencode、Cursor Agent 等 5 个 harness）；每个动作一行日志公告，插件自身故障时会话照常进行。
- **全部机制可关可调**：三个机制独立开关，学习周期 k、观察窗 p/m/s、判官置信度 c、干预上限 r 全部有默认值可改，行为完全可预期。

**技术栈**
Python 3.10+ 插件；事实提炼与判官调用复用编码代理自身的模型通道（同模型、同额度计费，不引入新依赖）；支持 Claude Code、Codex、GitHub Copilot CLI、Pi 四个 harness 深度集成。

**适用场景**
团队级编码代理成本治理（SWE-Bench 实测 30 个「仓库 × 组合」单元全部变便宜）；长期维护同一大仓库的日常 Agent 工作流；多代理并发跑批任务的降本；研究「经验驱动优化」方向的参考实现。

**推荐理由**
- **性价比数据几乎没有对手**：不改代理本体、不换模型，纯外挂把平均成本打降 18.4–30.9%，且五组里四组 Pass@1 不降反升——省钱不等于变笨，这是同方向工作里最难得的一点。
- **学术与工程双在线**：UC Berkeley × 微软研究院联合署名的论文 + 开源实现 + 项目页，机制解释细到每个阈值默认值，可复现性在同类「Agent 优化」项目里罕见地高。

> **注意**：省钱有前提：要跑得多才划得来，前几个会话是学习期，新仓库收益有限；判官与事实提炼的模型调用走你自己的代理额度，本身也花钱；v0.1.0 早期版本，实验性支持列表的 harness 兼容性不稳；它从不停任务，死循环最终还是要人来按停；Apache-2.0 可商用。

> **一句话理解**：像给新员工配了个旁观教练：他不上手干活，只在小本本上记「这仓库测试得这么跑」「那工具你从没用过」「这个错你已经撞三次了」——月底一看，工时省了三成。

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

- Trending 日榜 9 条 / 周榜 17 条，合并去重后新候选偏少（多条为已推送或技能合集）；本期 5 个入选覆盖应用 2、工程 1、算法 1、Agent 1 四类目，单类目不超过 2，License、活性与 release 均逐个核验（五个仓库全部有正式 release）。
- 口径说明：sherlock、astryx、spec-kit 的增量是 Trending 页实测值；project-maya（建库 34 天）与 TokenEconomizer（建库 27 天）无榜单增量，按「累计 star ÷ 建库天数」折算周均并标注估算，不与 Trending 原始数字混用。
- 环境说明：本机到 GitHub 的网络已完全恢复（真 Sectigo 证书链），取数走 Trending 页 + gh 令牌 API（5,000 次/小时，额度充足）；11-02 期积压的本地归档提交随本期发布脚本自动补推。
- 选题倾向：本期避开「知名大项目热榜回潮」（如 Hyprland、MuJoCo），优先选解决具体痒点的工具；Agent 类目刻意避开同质化的 harness（本期 Search 命中的 agent-framework / hive / evolver 等周均估算均不达标或同质），选择了方向独特的成本治理插件。

**本期按规则排除的候选**

- anthropics/skills（日榜 +792 / 周榜 +3,169）、mattpocock/skills（周榜 +9,635）、jakubkrehel/skills（周榜 +1,857）、blader/humanizer（66.5k，周榜 +3,118，「去除 AI 味」的 Agent skill）、Donchitos/Claude-Code-Game-Studios —— 技能 / 规则包合集，照旧整类排除。
- max-sixty/worktrunk（12.1k，周榜 +2,313）—— git worktree 管理 CLI，项目本身合格但 License 为 NOASSERTION，连续两期按既有口径排除。
- ranxianglei/billion-context（5.2k，日榜 +460）—— 上下文压缩插件，License 为 NOASSERTION，排除。
- dsx-ai-factory/nvke（875，日榜 +345，Apache-2.0）—— GPU Kubernetes 管理面，方向不错但总 star 未达 1,000 门槛。
- google-deepmind/mujoco（16.5k，日榜 +41）—— 老牌物理仿真引擎，日增量未达 80 门槛，且属高度知名项目。
- pingdotgg/t3code、D4Vinci/Scrapling、NVIDIA/auto-ontology、vercel-labs/agent-browser、thedotmack/claude-mem、Renhuai123/ziwei-doushu、The-PR-Agent/pr-agent —— 往期已推送，按 archive/index.json 去重排除。
- milind-soni/OpenMausBot（18.4k，周榜 +7,621）—— 往期已因 718 open issue / 仓库 426MB 让位，本期延续排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-09 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
