# 每日 GitHub 精选 · 2026-10-22（第 11 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（2）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [supabase/supabase](https://github.com/supabase/supabase) | 工程实践 | TypeScript | 113.0k | +504 ⭐ 日榜 |
| 2 | [anywhere-labs/dsh-desktop](https://github.com/anywhere-labs/dsh-desktop) | 应用项目 | TypeScript | 32.2k | ≈+3,220 ⭐ 周均（估算） |
| 3 | [deepseek-ai/DeepInfer](https://github.com/deepseek-ai/DeepInfer) | 算法/模型 | Python | 18.1k | 建库 6 天 ≈+21,000 ⭐ 周均（估算） |
| 4 | [FareedKhan-dev/kimi-k3-in-c](https://github.com/FareedKhan-dev/kimi-k3-in-c) | 算法/模型 | C | 9.1k | ≈+780 ⭐ 周均（估算） |
| 5 | [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) | AI Agent | Python | 23.4k | ≈+3,900 ⭐ 周均（估算） |

---

## 1. Supabase —— 把 Postgres 变成 Firebase：数据库、认证、API、存储一个开源平台全包

**一句话简介**：一个 Postgres 能不能顶半个后端团队？Supabase 的答案是：把认证（GoTrue）、REST API（PostgREST）、GraphQL（pg_graphql）、实时推送（Realtime）、对象存储（Storage）、边缘函数**全部插在同一个 Postgres 上**，每一块都是独立开源组件——既能云托管开箱即用，也能整体自托管。本期它以日榜 +504 回到热榜，是罕见的「上了 100k star 还在高速增长」的基础设施项目。

**仓库信息**
- 地址：https://github.com/supabase/supabase
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：113.0k（113040）｜ 近期增量：+504 ⭐ 日榜
- 协议：Apache-2.0 ｜ 官网 / 文档：supabase.com/docs（全量文档）+ docs/guides/hosting/overview（自托管指南）+ README 架构图与组件清单 + 客户端库矩阵（supabase-js / Python / Flutter 等）+ 社区论坛与分级支持

**核心功能**
- **建表即得 API，不用先写 CRUD**：PostgREST 把数据库 schema 直接翻成 RESTful API，pg_graphql 提供 GraphQL；Realtime 通过 Postgres 逻辑复制把 insert/update/delete 以 WebSocket 推给客户端——数据层即服务层。
- **认证与行级权限一体**：GoTrue 是 JWT 认证服务，登录态直接映射到 Postgres RLS（行级安全）策略：谁能看哪几行写在数据库里，而不是散落在业务代码中。
- **存储与边缘函数**：Storage 是带 Postgres 权限校验的 S3 封装；Edge Functions 基于 Deno，在离用户最近的节点跑服务端逻辑。
- **AI 与向量工具包**：内嵌 pgvector 生态的 embedding 工具链，语义搜索、文档检索可以和业务表放在同一个事务里。
- **云托管与自托管同构**：本地 CLI、云端 Dashboard、自托管 Docker 部署共用同一套组件，迁移不锁平台——这是它对比 Firebase 们最硬的底牌。

**技术栈**
TypeScript/JavaScript Monorepo；底层由 PostgreSQL + PostgREST + GoTrue + Realtime（Elixir）+ Storage API + pg_graphql + Envoy 组成，全部 MIT/Apache 开源组件；Apache-2.0；客户端库覆盖 JS/TS、Python、Flutter、Kotlin 等，文档站 supabase.com/docs 完整覆盖入门到自托管。

**适用场景**
快速起 Web/App 原型的独立开发者与小团队；想自建「带认证与实时推送」的后端但不想自研这些基础设施的公司；希望用 Postgres 生态（RLS、pgvector）统一数据与权限的中后台系统；Firebase 用户被数据导出/成本卡住时寻找开源替代。

**推荐理由**
- **Firebase 的体验、Postgres 的自由**：Firebase 锁定专有数据格式，Supabase 的底层就是标准 Postgres：随时可以 psql 连上、用任何 PG 工具迁移，退出成本低是它最核心的差异点。
- **组件全部可拆，不是黑盒**：Realtime、GoTrue、Storage 每一个都是独立开源项目：出问题能定位到具体组件，甚至只取其中一块用，平台不存在「整体绑架」。
- **113k star 的成熟度与活跃度**：多年大规模生产验证、文档分级完整、社区生态成熟（Discord/论坛/邮件支持），且仍在日榜快速增长——少数「可以直接押注」的开源基础设施。

> **注意**：① **不是 1:1 的 Firebase**：没有离线同步等特有能力，定位是「Postgres 开发平台」，迁移前先对齐功能清单；② **自托管不等于省心**：整套平台由十几个组件拼成，自己运维要同时面对监控、升级、备份的复合复杂度，小团队建议先用托管版再评估；③ RLS 策略写错就是权限漏洞——「权限在数据库里」既是优点也是责任，上线前务必做越权测试；④ 免费层与用量计费规则会调整，生产前核对当前定价；⑤ AI/向量能力依赖 pgvector，规模与索引参数要按数据量单独调优。

> **一句话理解**：像把一套精装房（Firebase）换成同一地皮上的毛坯加标准装修包（Postgres 加开源组件）：住进去体验差不多，但每面墙你都知道是什么砖，想拆哪面拆哪面。

---

## 2. DSH Desktop —— 给 DeepSeek Harness 套上原生桌面壳，插件即一切的 AI 工作台

**一句话简介**：DeepSeek Harness 本体（10-16 期已推送）是「本地 Web UI + Host 服务 + 插件系统」，想用起来得自己开终端、起服务、开浏览器。DSH Desktop 把这三件事装进一个原生应用：**自动拉起本地服务、常驻托盘、窗口化交互，且不捆绑改写上游——固定并原样运行特定上游版本**，自己的能力全部通过插件机制叠加。建库约 70 天拿下 32k star，是近期最陡的应用项目增量之一。

**仓库信息**
- 地址：https://github.com/anywhere-labs/dsh-desktop
- 类目：应用项目 ｜ 语言：TypeScript ｜ Stars：32.2k（32221）｜ 近期增量：≈+3,220 ⭐ 周均（估算）
- 协议：MIT ｜ 官网 / 文档：dshdesktop.cn（官网/下载站）+ docs/user-guide.md 与 faq.md 用户文档 + docs/architecture.md 架构说明 + 插件开发指南与插件生态倡议书 + GitHub Releases（Windows/macOS 正式安装包）+ 隐私政策单独成文

**核心功能**
- **原生桌面壳，零环境安装**：Windows x64 与 macOS Universal 安装包，无需 Node.js、无需命令行；应用自动启动并管理本地 Harness 服务，集成系统托盘与桌面窗口。
- **手机远程控制（已内置）**：iOS/Android 远程连接 Desktop，在手机上发起任务、查看 Agent 进度并跟进，2.0.9 及以上版本内置。
- **插件生态「万物皆插件」**：桌面本身也是一个插件：普通插件与 Desktop 插件两套接口，配套插件开发指南、统一插件 contract 讨论（DSH Community Fabric）与插件市场安全设计文档。
- **文档按角色分层**：普通用户从用户指南/FAQ 进入，开发者看架构说明与包级构建文档，隐私政策独立成文——比多数社区项目规整得多。

**技术栈**
TypeScript + Electron 壳（NSIS/DMG 安装器）；上游为 deepseek-ai/deepseek-harness 的本地 Web UI、Host 服务与插件机制；MIT；社区独立项目，README 明确声明与深度求索无隶属、合作、授权或背书关系。

**适用场景**
想用 DeepSeek Harness 但不想折腾 Node 与终端的普通用户；要在 Windows/macOS 上给非技术同事分发 AI 工作台的团队；想参与 DSH 插件生态、给桌面加能力的插件作者。

**推荐理由**
- **填的是真实空档**：上游 Harness 是面向开发者的本地服务，「桌面化 + 安装包 + 托盘」这一步官方没做——70 天 32k star 说明需求真实存在。
- **边界意识清晰**：固定上游版本、不改上游、自身能力走插件，降低了「壳」与「核」互相拖累的维护风险；README 还主动声明非官方项目，避免用户误读。
- **生态运营认真**：插件生态倡议书、统一插件框架调研、插件市场安全设计文档都进了仓库，不是只丢一个安装包的壳项目。

> **注意**：① **社区项目，与深度求索无隶属/授权**：Contributors 里显示的上游贡献者来自 fork 继承的历史提交，别误读成官方团队参与；② 固定并原样运行特定上游版本——上游更新不会自动跟进，安全补丁存在滞后窗口；③ 应用会在本地起 Harness 服务并监听端口，内网/公网环境注意访问控制；④ README 赞助位含多家第三方 API 中转站，属商业推广，选用前自行评估合规与稳定性；⑤ 新签名安装包可能触发 SmartScreen 告警，属新项目常态。

> **一句话理解**：上游 Harness 是一台性能很强但要自己接线的主机，DSH Desktop 是给它配的原生机箱、电源键和遥控器——内核没动，但普通用户终于可以直接按开机键。

---

## 3. DeepInfer —— DeepSeek 生产同款推理引擎开源：MoE 并行、置信度验证、确定性采样

**一句话简介**：这是驱动 DeepSeek 自家大规模线上服务的推理框架的**开源版本**（源自 vLLM 演进，另借鉴 SGLang 与 TensorRT-LLM）。本次发布的是离线推理部分：为 DeepSeek-V4.1-Flash 这类 MoE 大模型准备的专家并行、草稿验证与调度优化，全部经过真实生产负载打磨——建库仅 6 天即 18k star，是本期热度最高的算法类项目。

**仓库信息**
- 地址：https://github.com/deepseek-ai/DeepInfer
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：18.1k（18058）｜ 近期增量：建库 6 天 ≈+21,000 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：README 特性配置总表（环境变量逐项说明）+ examples/（离线推理与结构化输出示例）+ eval/README.md 评测说明 + run_sweep.sh 可复现 benchmark 脚本 + 吞吐-延迟 Pareto 图（doc/images）

**核心功能**
- **MoE 大模型并行全家桶**：Attention DP / 均衡 CP、MoE EP + EPLB，配合 FlashMLA、DeepGEMM、DeepEP、TileLang 自研内核——多机多卡跑 V4.1-Flash 的并行方案是现成的。
- **置信度调度验证（DSpark）**：用草稿 token 加速解码，并以置信度估计安排验证节奏；NEXTN 解码长度默认上限 5，通过 DEEPINFER_USE_NEXTN_DECODE 控制。
- **零开销异步调度 + SWA 有界回放**：CPU 批调度与设备执行重叠（默认开启）；SWA 窗口只回放有界后缀（默认保留 140 token），压缩 prefill 工作量。
- **确定性推理**：批量组成无关（batch-invariant）+ 固定 seed 的确定性采样：同样输入必然同样输出，是可复现实验与回归测试的地基。
- **结构化输出**：用 regex、JSON schema 或 EBNF 文法约束生成，走 SamplingParams 的 so_args，直接可用。

**技术栈**
Python 3.12 + CUDA 13（NVIDIA SM100）或 CANN 9.2（华为昇腾 950），GCC ≥13，源码编译（build.sh，DEEPINFER_ACCELERATOR 切换硬件）；Apache-2.0；源自 vLLM 演进，默认 checkpoint 为 deepseek-ai/DeepSeek-V4.1-Flash-1017。

**适用场景**
自建 DeepSeek 系列模型推理服务的团队（尤其已持有 SM100 或昇腾 950 硬件的）；需要确定性/批量无关推理做测试与回归的场景；研究 MoE 推理调度、草稿验证实现的工程师。

**推荐理由**
- **生产同源，不是实验室原型**：它就是 DeepSeek 线上服务所用框架的开源切片，性能 Pareto 图配了可复现脚本（run_sweep.sh），不是口头快。
- **国产硬件一等公民**：NVIDIA 之外明确支持昇腾 950 并给出 CANN 版本要求，这在头部推理框架里相当少见，对国产化算力团队是直接可用的选项。
- **MoE 推理的参考实现**：EPLB、置信度调度验证、SWA 有界回放这些论文级优点的工程落地代码本身就是高质量学习材料。

> **注意**：① **只含离线推理**：KV cache 系统、Prefill/Decode 分离部署、跨副本负载均衡都不在本发布内，要组完整在线服务得自己补；② 硬件门槛极高：仅 NVIDIA SM100 与昇腾 950，旧卡用户请继续用 vLLM/SGLang；③ 目前只适配 DeepSeek-V4.1-Flash 一个模型系列，通用性无法与 vLLM 比；④ 建库仅 6 天（2026-10-16），API 与环境变量大概率变动，生产请 pin 版本；⑤ 默认 checkpoint 为 TB 级，首次运行会下载到 HF cache，注意磁盘与带宽。

> **一句话理解**：好比餐厅后厨把自家旗舰门店同款灶台开源了：火力调度（并行）、出菜节奏（验证调度）都是真实高峰期磨出来的——但这套灶台只适配自家菜单（V4.1-Flash），也不含前台点单系统（在线服务层）。

---

## 4. kimi-k3-in-c —— 一个 CPU、8GB 内存、176KB 引擎：纯 C99 跑通 2.78 万亿参数模型

**一句话简介**：一个「把不可能变成可能」的工程演示：**2.78 万亿参数的 Kimi K3（磁盘 checkpoint 1.56TB）在一台 8GB 内存的普通笔记本 CPU 上完成推理，峰值内存 8.24GB，整个推理引擎只有 176KB 的 C99 代码**——没有 BLAS、没有框架、没有 GPU。靠的是 MoE 稀疏激活 + 权重按需从磁盘流式读取。上期因类目配额让位，本期如约补上。

**仓库信息**
- 地址：https://github.com/FareedKhan-dev/kimi-k3-in-c
- 类目：算法/模型 ｜ 语言：C ｜ Stars：9.1k（9146）｜ 近期增量：≈+780 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：README 性能表（8GB→128GB 各档实机数据）+ docs/data/ 全量测量数据 + CHANGELOG.md（v1.1.0）+ CONTRIBUTERS.md 贡献分工 + GitHub Actions CI（Linux/macOS/Windows）

**核心功能**
- **极致内存占用的推理引擎**：峰值 RSS 8.24GB 跑 2.78T 参数 MoE：只激活当前 token 需要的专家，权重不常驻内存，每步从磁盘流式读取。
- **便携 C99，零依赖**：无 BLAS、无框架，176KB 引擎代码可移植到 Linux/macOS/Windows（社区已贡献 macOS、Windows 与 NEON 移植）。
- **跨档位字节级一致**：8GB 到 128GB+ 各档机器输出完全一致——内存大小只影响速度（26.5s/token → 5.6s/token），不影响结果，天然适合复现与测试。
- **v1.1.0 的真实优化**：更快的 MXFP4 内核、逐 token 计算量降约 8×、追问场景快 3.9×、长 prompt 成本减半，数据在 docs/data/ 可查。

**技术栈**
C99（无外部依赖）；MoE 稀疏激活 + 磁盘流式权重读取 + MXFP4 量化内核；Apache-2.0；GitHub Actions CI 覆盖三平台，CHANGELOG 与贡献者分工文档齐全。

**适用场景**
想吃透 MoE 推理底层原理的学习者（代码即教材）；在无 GPU、离线、内存受限设备上做可行性验证的工程师；作为「极端资源约束下系统设计」的参考实现。

**推荐理由**
- **把「大模型=大显存」的直觉打碎**：1.56TB 的模型在 8GB 内存上出结果，核心是 MoE 稀疏性加 I/O 设计——这个思路对边缘侧推理有真实的启发价值。
- **教学价值罕见**：176KB、零依赖的 C 代码把注意力、MoE 路由、量化内核全部摊开，比啃框架源码友好得多。
- **数据诚实**：每档机器的 token 耗时、磁盘还是内存驻留、字节级一致输出都给了实测表与原始数据，宣传克制。

> **注意**：① **速度是硬伤**：8GB 内存档 26.5s/token，实用性接近零——它验证的是可行性，不是生产力工具；即便 128GB 全内存驻留也要 5.6s/token；② 需要先拿到 1.56TB 的 K3 权重文件，磁盘与下载成本是隐藏门槛；③ 偏个人/社区项目（v1.1.0），无生产级维护承诺；④ 依赖具体 checkpoint 格式，模型升级可能需要适配；⑤ CI 覆盖三平台，但 NEON 等移植仍在社区迭代中，性能口径以自己实测为准。

> **一句话理解**：像有人用一辆自行车驮着整套百科全书跑完马拉松：不是让你以后骑自行车运书，而是证明了「书可以按页现取」——这个取书机制才是值得带走的部分。

---

## 5. Jev Ultrafast —— 7.1 秒完成航班搜索的浏览器 Agent：动作与目标一次请求同时决策

**一句话简介**：传统浏览器 Agent 的速度瓶颈在「每一步都要问一次大模型」。Jev 换了打法：每次观察生成一张带编号的元素表，**操作（CLICK/SELECT/…）和目标元素由 TypeSafe 模型在同一次请求里给出**，只有 TYPE_TEXT 才叫小模型写字——苏黎世飞伦敦的 Google Flights 搜索 7.1 秒完成，含真实文本生成与页面等待，demo 视频是 1× 速度。

**仓库信息**
- 地址：https://github.com/browser-use/jev-ultrafast
- 类目：AI Agent ｜ 语言：Python ｜ Stars：23.4k（23423）｜ 近期增量：≈+3,900 ⭐ 周均（估算）
- 协议：MIT ｜ 官网 / 文档：docs/performance.md 测量文档 + docs/demo.mp4 真机演示（1× 速度）+ README 决策回路图 + inspector 调试界面（操作/目标概率可视化）+ jev_ultrafast/agent.py 源码导读

**核心功能**
- **动态索引操作空间**：每步只暴露当前可用的操作与兼容元素（如 CLICK [7]），投机性目标头只含可执行项——操作与目标两次决策合并为一次网络往返。
- **默认不走截图**：Agent 主循环消费结构化页面状态而非截图，省掉视觉模型延迟；截图仅供 inspector 调试与独立录屏。
- **执行前验证目标**：点击前校验文档、表单值、目标与周边上下文，解析当前几何位置并拒绝被遮挡的控件；动画不触发重预测。
- **智能等待**：combobox 输入后等可见建议（上限 200ms），其余交互最多等两帧或 50ms——把「等页面」变成可度量的等待。
- **既可演示也可当库**：Web inspector 支持逐步执行与暂停，Python 库形态 Agent(url, goal) 可直接嵌进自己的脚本。

**技术栈**
Python（uv 管理依赖）+ TypeSafe Jev 决策模型 + 小型文本模型（示例走 OpenRouter 的 mercury-2.5，可换 Gemini/GLM/DeepSeek 等任意 OpenAI 兼容端点）+ Browser Harness 驱动 Chrome（CDP）；MIT；performance.md 公开测量口径。

**适用场景**
对延迟敏感的浏览器自动化：高频重复表单、流程监控、端到端巡检；研究「动作空间索引 + 单请求双头决策」这条加速路线的工程师；需要可审计、可逐步暂停的网页操作任务。

**推荐理由**
- **加速思路有普适性**：「结构化状态 + 索引动作 + 一请求双头决策」不只是快——它同时降低 token 成本与不确定性，可迁移到浏览器之外的 Agent 领域。
- **数字可复核**：performance.md 给测量口径，demo 视频标注 1× 速度且策略里没有站点特判脚本，agent.py 源码公开可读。
- **工程细节扎实**：目标验证、几何解析、有界等待这些「慢变量」逐一处理——快是省出来的，不是省略出来的。

> **注意**：① **依赖 TypeSafe 云 API**：需 TYPESAFE_API_KEY，核心决策模型不在本地，隐私与用量成本要评估（文本模型可换任意 OpenAI 兼容端点）；② 演示场景（Google Flights、Wikipedia）之外的真实站点鲁棒性需自行验证，验证码与强风控站点不适用；③ Browser Harness 需允许 Chrome 远程调试，仅建议在受控环境开启；④ 项目年轻（2026-09-16 建库），API 可能变动；⑤ demo 明确不执行下单/预订，别把演示效果等同于生产可用。

> **一句话理解**：传统 Agent 像司机每过一个路口都要打电话问导航「现在我该往哪开」；Jev 是把整张路口清单编号塞进一次问答——「在 7 号路口左转」一句话解决，只有真要打字填表时才请个文书员。

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

- 候选池：Trending 日榜 12 条 + 周榜 16 条（合并去重 27 个仓库），其中 13 个已在往期推送；新增候选里技能/插件集合与 `NOASSERTION` 仍占大半，靠 Search API 补池（`created:>2026-07-01 stars:>3000 pushed:>2026-09-22`、`topic:llm-inference`、`topic:agent-framework` 三组查询）。
- 类目配额：工程实践 / 工具链 ×1（Supabase）、应用项目 ×1（DSH Desktop）、算法 / 模型 ×2（DeepInfer、kimi-k3-in-c）、AI Agent 及基础设施 ×1（Jev Ultrafast）——覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：Apache-2.0 ×3（Supabase、DeepInfer、kimi-k3-in-c）+ MIT ×2（DSH Desktop、Jev Ultrafast）。5 个仓库均有完整 README 正文；`kimi-k3-in-c` 与 `Supabase` 有 CI，`DeepInfer` 提供可复现 benchmark，`DSH Desktop` 与 `Jev Ultrafast` 有正式安装包 / 测量文档。
- 去重检查：与往期十期（09-28 / 09-29 / 10-09 / 10-10 / 10-12 / 10-14 / 10-16 / 10-19 / 10-20 / 10-21，共 50 个仓库）均无重叠，基线为 `archive/index.json`。另核验了 `dsh-desktop` 两个同名仓库（anywhere-labs 与 dataelement 同日建库、互非 fork），取星数更高的 anywhere-labs（32.2k）。
- 数据口径：total stars、License、最近提交取自 `gh api repos/*`（5 个仓库 `pushed_at` 均在 2026-10-02 之后，30 天活性线内）；`Supabase` 的 +504 为 Trending 日榜原始数字，其余四个未上榜，「周均增量」为**由「累计 star ÷ 建库天数」换算的估算值**（DeepInfer 6 天 ≈21,000/周、DSH Desktop 70 天 ≈3,220/周、Jev 36 天 ≈3,900/周、kimi-k3-in-c 82 天 ≈780/周），速览表统一标注「估算」，不与榜单原始数字混用。
- 本期风险提示（与功能同等看待）：`DeepInfer` 仅支持 SM100 / 昇腾 950 且只含离线推理，通用场景仍选 vLLM/SGLang；`kimi-k3-in-c` 是可行性演示（26.5s/token）不是生产力工具，且需先持有 1.56TB 权重；`Jev Ultrafast` 核心决策依赖 TypeSafe 云 API，注意隐私与成本；`DSH Desktop` 固定上游版本，安全补丁有滞后窗口；`Supabase` 自托管是十几个组件的复合运维，小团队建议托管版起步。

**本期按规则排除的候选**

- `vllm-project/vllm`（+441）、`stablyai/orca`（日 +1,541 / 周 +8,705）、`headroomlabs-ai/headroom`（+474）、`Comfy-Org/ComfyUI`（+939）、`morluto/rea`（周 +129,417）、`NationalSecurityAgency/ghidra`（+5,769）、`debpalash/VoiceStudio`（+15,125）、`heygen-com/hyperframes`（+5,740）、`HKUDS/CLI-Anything`（+3,681）、`akitaonrails/ai-memory`（+2,833）、`anomalyco/opencode`（+6,545）、`earthtojake/text-to-cad`（+2,000）：热度全部达标且仍在榜，但均已在往期（09-29 / 10-09 / 10-10 / 10-14 / 10-16 / 10-19 / 10-20 / 10-21）推送，按 `archive/index.json` 去重基线排除。
- `anthropics/claude-plugins-official`（周 +5,703）、`K-Dense-AI/scientific-agent-skills`（+4,719）、`android/skills`（+1,332）、`cursor/plugins`（+2,049）、`wshobson/agents`、`DietrichGebert/ponytail`（171.7k）、`Graphify-Labs/graphify`（130.3k）、`ruvnet/ruflo`（78.2k）、`awesome-dsh-plugin`（19.9k）：产物形态是 agent 技能 / 插件 / 提示词集合，属规则明确排除的资源聚合型仓库；本期榜单此类占比仍过半，是新增候选稀缺的主因。
- `twentyhq/twenty`（59.2k，日榜 +112，「开源 Salesforce 替代」）、`mksglu/context-mode`（31.7k）、`hypit-ai/hypit`（24.7k）、`Gathin23/cleanyourtv`（19.5k）：License 为 `NOASSERTION` 或缺失，按「License 明确」口径排除；`twenty` 本身很对口，遗憾在协议口径。
- `cloudflare/security-audit-skill`（36.6k，日榜 +2,012，MIT）：连续第二期因最后提交停留在 2026-09-14、超 30 天活性线落榜。
- `xai-org/grok-build`（27.5k，Rust，Apache-2.0）：自述 Synced from monorepo 的单向镜像、无 release、0 issue，连续第二期排除。
- `openai/math`（15.3k，Lean）：论文手稿与 Lean 形式化合集，属研究资料而非可运行软件。
- `Ebony-Vinyl/dsh-our-free-model`（34.0k，JS，MIT，建库 28 天）：形态是「免登录、免注册、免 API Key 使用前沿模型」的 DSH 插件，实质依赖非官方渠道，合规与可持续性存疑，不推荐。
- `gitleaks/gitleaks`（30.2k，Go，MIT，最后提交 09-30）：活性与协议合格，但由累计 star ÷ 建库时长估算的周均增量约 77，不达增量门槛。
- `pydantic/pydantic-ai`（20.8k，MIT）、`microsoft/agent-framework`（14.3k，MIT）、`ray-project/ray`（44.1k）：成熟且活跃的长期主流项目，近期增量不达门槛或非本期增量主线，名额让给更锐的候选。
- `google-research/harness2`（17.3k，Python，Apache-2.0，建库 16 天 ≈7.6k/周估）：指标合格，但 README 无项目描述、可读材料太少，与上期遗留优先项 `kimi-k3-in-c` 在算法/模型类目二选一时让位。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-22 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
