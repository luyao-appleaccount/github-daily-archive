# 每日 GitHub 精选 · 2026-11-13（第 21 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [we-promise/sure](https://github.com/we-promise/sure) | 应用项目 | Ruby | 14.0k | 日榜 +967 ⭐ |
| 2 | [pookjw/HermesEnabler](https://github.com/pookjw/HermesEnabler) | 应用项目 | Objective-C | 1.5k | 日榜 +218 ⭐ |
| 3 | [google-deepmind/mujoco](https://github.com/google-deepmind/mujoco) | 算法/模型 | C++ | 17.8k | 周榜 +1,671 ⭐ |
| 4 | [openai/codex-security](https://github.com/openai/codex-security) | 工程实践 | TypeScript | 12.4k | 日榜 +643 ⭐ |
| 5 | [QwenLM/qwen-code](https://github.com/QwenLM/qwen-code) | AI Agent | TypeScript | 29.8k | 日榜 +151 ⭐ |

---

## 1. Sure —— 断更开源理财应用 Maybe 的社区续命分支：净资产、同步、AI 助手全都要

**一句话简介**：Maybe 团队花近 100 万美元做的理财应用 2023 年停更开源后，社区把它接过来继续养——日榜 +967 说明「能自己管钱的应用」需求远未饱和。

**仓库信息**
- 地址：https://github.com/we-promise/sure
- 类目：应用项目 ｜ 语言：Ruby ｜ Stars：14.0k（13954）｜ 近期增量：日榜 +967 ⭐
- 协议：AGPL-3.0 ｜ 官网 / 文档：官网 sure.am + 仓内 docs/ 完整托管文档（Docker / Render / PikaPods / Hostim 多路一键部署）+ 演示数据一键加载 + Discussions 活跃

**核心功能**
- **完整理财功能集继承**：现金流、净资产、支出概览三大仪表盘 + 账户 / 交易 / 分类体系全部来自 Maybe 原版；支持一键加载演示数据，五分钟体验全部功能再决定要不要自建。
- **券商与银行数据同步**：集成 SimpleFIN、SnapTrade、Trade Republic 等数据源，持仓批次（holding lots）会计规则含 FIFO / 加权平均 / 拆股处理，可与券商数据对账重映射。
- **AI 助手三种部署模式**：无 AI / OpenAI 简单模式 / 外部 AI（AlphaClaw）三档可选，AI 版走 pgvector 向量存储支持文档导入问答；MCP 端点暴露 35+ 工具，LLM Agent 可以直接替你查账。
- **多端覆盖**：浏览器主站 + Tauri 桌面客户端（macOS，可连局域网自托管服务器）+ API 客户端；移动端与桌面端共享同一份自托管数据。
- **部署链路成熟**：Docker Compose（含 AI 版 compose 模板）为推荐姿势，Render / PikaPods / Hostim 一键模板三选一，Helm chart 支持上 Kubernetes；CI、Brakeman 安全扫描、Dev Container 一应俱全。

**技术栈**
Ruby on Rails + PostgreSQL（AI 版需 pgvector）+ Redis + Sidekiq；前端 Tailwind CSS 4 + ViewComponent 组件体系；桌面端 Tauri；部署 Docker Compose / Helm，CI 走 GitHub Actions。

**适用场景**
想完全掌控自己财务数据的个人 / 家庭自托管记账；Maybe 老用户寻找仍在维护的续作；理财产品的开发参考（持仓批次会计规则与数据同步层实现很完整）；给 LLM Agent 挂一个能查账的 MCP 数据源。

**推荐理由**
- **百万美元级代码库的免费续命**：Maybe 当年按商业产品标准投入开发（含「咨询顾问」功能），代码质量与功能完整度远超社区白手起家的记账项目；社区分支让它避免重蹈「上游归档、无人可用」的结局。
- **本期 Trending 最热的实用应用**：日榜 +967 是今天全站前三的增量，热度集中在「自托管 + AI 助手 + 数据同步」这条完整链路上，不是炒作型空壳。

> **注意**：AGPL-3.0 传染性协议，二次开发对外提供服务需开源；「Maybe」名称与 logo 是商标，fork 禁止沿用；数据量大时有已知性能瓶颈（项目用 Skylight 面板公开追踪，欢迎优化贡献）；上游 Maybe 已归档、发展方向由社区主导存在不确定性；数据同步源以欧美服务为主，国内券商 / 银行基本要靠手动导入或自己写 Provider。

> **一句话理解**：像一家烧了上亿融资后关门的餐厅把菜谱全公开了，社区大厨们合伙把店重新开起来——菜单没变，掌勺的换成了志愿者。

---

## 2. HermesEnabler —— 把爱马仕联名表盘装进任意 Apple Watch 的解锁工具

**一句话简介**：爱马仕表盘官方只在 Hermès 款 Watch 上卖，这台工具把「机型锁定」直接绕开——本质是消费电子圈对硬件区隔定价的一次民间反抗。

**仓库信息**
- 地址：https://github.com/pookjw/HermesEnabler
- 类目：应用项目 ｜ 语言：Objective-C ｜ Stars：1.5k（1548）｜ 近期增量：日榜 +218 ⭐
- 协议：MIT ｜ 官网 / 文档：八语 README（含简中 / 繁中）+ Releases 预编译 IPA + 仓内侧载与签名排障文档（11-13 刚更新）+ macOS / Windows 双平台安装指南

**核心功能**
- **机型区隔一键破除**：原理是修改设备上报的机型信息（MobileGestalt），让系统认为这是 Hermès 款从而解锁联名表盘；改动在 Watch 端的 HermesEnabler2 应用内完成，有引导步骤。
- **三条安装通道**：macOS 用 Sideloadly 签 IPA 或 Xcode 直跑，Windows 用社区工具 WatchBridge 完成 USB 开发者模式准备与双端安装；iPhone 与 Watch 的开发者模式开启步骤逐条写明。
- **watchOS 适配极快**：11-13 当天就合并了对 watchOS 24R363 / 24S5086l 的支持提交；版本窗口要求 watchOS 27.0–27.3 beta 1，README 顶部明确标注。
- **文档质量罕见地认真**：八语 README、排障文档覆盖 Sideloadly 0.72 已知剥 Watch 应用的 bug、免费证书 7 天过期、App Groups 权限需付费开发者账号等全部坑点。
- **回滚有保障**：改机型信息前会做 MobileGestalt 备份，删除应用前要求先通过应用内功能恢复备份，把变砖风险压到最低。

**技术栈**
Objective-C（Watch 端 HermesEnabler2 + iPhone 宿主 App，Xcode 工程）+ Swift/SwiftUI 配套 Companion；分发走 GitHub Releases IPA；签名依赖 Sideloadly（macOS）/ WatchBridge（Windows）；核心机制引用 Gester 项目的 MobileGestalt 改写代码。

**适用场景**
非爱马仕款 Apple Watch 用户想用联名表盘；iOS 逆向 / 私有 API 研究者参考 MobileGestalt 改机与双端侧载流程；想了解 Apple「硬件区隔定价」技术实现机制的案例。

**推荐理由**
- **精准戳中一个真实痒点**：表盘是 Apple 生态里少有的「花几万买手表才能看」的内容区隔，1,548 star 与日榜 +218 说明需求真实且传播快。
- **工程与文档完成度远超同类越狱式项目**：版本适配当天跟进、八语文档、双平台指南、排障与备份恢复流程齐全——这类民间工具通常是「能用但没人管」的状态，它明显例外。

> **注意**：支持窗口很窄：仅 watchOS 27.0–27.3 beta 1，升系统前先确认适配；免费 Personal Team 证书 7 天过期要重签，App Groups 权限免费账号无法签名（可能需要付费开发者账号，99 美元/年）；本质是修改系统私有机制，有变砖理论风险，README 明确「Use at your own risk」；解锁付费内容属于灰色地带，商用与分发需自行评估法律风险。

> **一句话理解**：就像用一张改造过的会员卡骗过了商场闸机，进去了本来只让 VIP 进的展厅——技术上是卡信息上报环节动了手脚，进得去，但商场随时可能换闸机。

---

## 3. MuJoCo —— 机器人强化学习事实标准的物理仿真引擎，四足/人形运动控制训练的起点

**一句话简介**：训练一只机器狗走路之前，先在 MuJoCo 里把路「摔」个几千次——真实硬件摔一次几万块，仿真里摔一次只要几毫秒。

**仓库信息**
- 地址：https://github.com/google-deepmind/mujoco
- 类目：算法/模型 ｜ 语言：C++ ｜ Stars：17.8k（17764）｜ 近期增量：周榜 +1,671 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：mujoco.org 官网 + Google DeepMind 官方文档站 + PyPI（mujoco）Python 绑定 + Unity 插件 + DM-Control / mjrl 等生态工具链 + 原始论文（Todorov 等，IEEE T-RO 2012）

**核心功能**
- **快而准的接触动力学**：专为铰接结构与环境交互优化：预分配的低层数据结构 + XML 编译器，运行时零内存分配，速度快到可以做实时可视化与大规模并行训练，这正是它被 RL 社区选中的根因。
- **C API + Python 绑定 + Unity 插件三通道**：研究者用 C/C++ 榨性能、算法工程师用 Python（mujoco 包）快速迭代、游戏与可视化团队走 Unity 插件；原生桌面窗口与浏览器 WebGL 两种可视化都内置。
- **物理量工具函数全家桶**：除仿真循环外还暴露雅可比、逆动力学、接触力、扰动等大量物理量计算工具，做模型预测控制（MPC）与系统辨识不用自己另造轮子。
- **机器人研究的生态底座**：DM Control、Gymnasium Robotics、四足与人形基准模型（Unitree 系列第三方模型包等）都以其 XML 格式为通用描述语言，学会它等于接通整个机器人 RL 生态。
- **Google DeepMind 长期供养**：2022 年被 DeepMind 收购后开源并持续活跃（最近提交 11-12），从学术项目升级为有商业团队维护的基础设施，Apache-2.0 可商用。

**技术栈**
C/C++ 核心（Apache-2.0）+ Python 绑定（PyPI：mujoco）+ Unity 插件；模型用 MJCF XML 描述（也兼容 URDF）；构建支持 CMake 与 Bazel；可视化原生 OpenGL 与浏览器 WebGL 双通道；GPU 并行可配 MJX（JAX 后端）。

**适用场景**
四足 / 人形机器人运动控制的 RL 与 MPC 算法训练与验证；机械臂抓取与操作仿真；生物力学步态分析；图形动画的物理驱动角色；将仿真策略迁移到真机前的 Sim-to-Real 基础环节。

**推荐理由**
- **领域事实标准，生态无可替代**：机器人 RL 领域的论文基准、开源模型、课程教材几乎默认 MuJoCo 格式；DeepMind 接手后维护强度只增不减，17.8k star 是长期复利的结果而非短期热点。
- **周榜 +1,671 的回潮有实因**：人形与四足机器人这两年从实验室走向量产，大量新团队第一次认真对待仿真；对做巡检机器人、运动控制落地的团队，它是绕不开的第一站。

> **注意**：它是仿真引擎不是机器人解决方案：没有开箱即用的「让机器狗走路」，模型、奖励函数、训练循环都要自己搭（可从 DM Control 与 mujoco_menagerie 模型库起步）；接触动力学快是靠软约束近似换的，参数（solimp/solref）调不好会穿模或抖动；Sim-to-Real 仍有域差，真机部署前需做域随机化；学习曲线对非科班团队偏陡。

> **一句话理解**：MuJoCo 之于机器人，好比风洞之于飞机设计师：产品还没造出来就能在虚拟风洞里试几千次机翼角度——便宜、快、摔不坏，但最后还得真飞一次才算数。

---

## 4. Codex Security —— OpenAI 开源的安全扫描 CLI：发现、验证、修复代码漏洞一条龙

**一句话简介**：传统 SAST 扫描器给你一屏幕误报，它多做了两步：先用模型验证「这个洞是不是真的」，再直接生成修好它的补丁。

**仓库信息**
- 地址：https://github.com/openai/codex-security
- 类目：工程实践 ｜ 语言：TypeScript ｜ Stars：12.4k（12445）｜ 近期增量：日榜 +643 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：developers.openai.com/codex/security 官方文档 + npm @openai/codex-security（v0.10.0，2026-11）+ 官方 GitHub Action 模板 + SARIF / JSON / CSV 导出 + Jira / Linear / ServiceNow 集成

**核心功能**
- **三档扫描范围**：整仓扫描、`--path` 指定路径、`--diff origin/main` 只扫本次变更——最后一档对「只想在 PR 里拦住新漏洞」的团队最实用；Deep Scan 模式重复扫描并去重汇总。
- **验证与修复闭环**：不只报问题：候选漏洞先经模型调查验证真伪，确认后生成修复补丁，还能反向验证既有修复是否真的堵住了洞；扫描结果本地保存、可查历史与去重。
- **策略与威胁建模**：`cs policy` 起草 / 更新 SECURITY.md 并保存威胁模型，可导出为 artifact；把「安全要求文档化」从一次性合规动作变成可维护的活文档。
- **第三方报告导入与工单打通**：可导入 Tenable、CrowdStrike FCS 等 IaC / 漏洞报告，统一按严重度评估后发往 Linear / Jira / GitHub，导出 SARIF / JSON / CSV 接入既有安全流程。
- **CI 自动化**：官方 GitHub Action 模板支持每周定时扫描（单次约 5 美元费用上限），Docker 容器化批量扫描覆盖多仓；多模型通道可选 OpenAI、Bedrock、OpenRouter、Fireworks。

**技术栈**
TypeScript CLI + SDK（npm 全局安装即用，Node 22.13+ / 24 / 26）+ Python 3.10+ 工具链；Bun 构建、Wolfi 容器、GitHub Actions；模型通道支持 OpenAI API、AWS Bedrock（无需 OpenAI 账号）、OpenRouter、Fireworks。

**适用场景**
在 PR / 定时 CI 里拦安全漏洞的工程团队；接手老项目要先摸清漏洞底数的安全工程师；把 SAST 报告去重、定级、派单的安全运营流程；给 Codex 等编码 Agent 挂「写完就扫」的安全工作流。

**推荐理由**
- **把「验证」环节补进了扫描链路**：误报是传统扫描器最大的痛，模型验证 + 补丁生成让输出从「疑似问题清单」变成「已确认问题 + 修法」，这是它与 grep 式 SAST 的本质区别。
- **OpenAI 官方出品且工程化完整**：Apache-2.0、npm 一条命令、官方 Action、SARIF 与工单生态全打通，日榜 +643 说明安全团队对「AI 原生扫描器」的尝鲜意愿极强。

> **注意**：按扫描计费：GitHub Action 示例单次约 5 美元上限，进行中的请求可能超限，批量跑多仓前先算成本；部分网络安全类请求与「受保护发现」需要 Trusted Access for Cyber 资质；本地 serve 与浏览器仪表盘已被移除（旧数据可读）；扫描报告有排除项（exclusions），读 REPORT 才能理解覆盖率；模型验证不是银弹，高危结论仍需人工复核。

> **一句话理解**：普通扫描器像烟雾报警器：一烧糊早餐就尖叫。它更像请了个安全顾问：先确认是不是真着火，再顺手把灭火器递给你并演示怎么喷。

---

## 5. Qwen Code —— 通义开源的终端编码 Agent：从 Gemini CLI 分叉后长成了全入口工具集

**一句话简介**：编码 Agent 的竞争已经卷到「入口」层面：同一个 Agent，终端里是 CLI、编辑器里是插件、微信里是聊天机器人，它把三条路都铺了。

**仓库信息**
- 地址：https://github.com/QwenLM/qwen-code
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：29.8k（29816）｜ 近期增量：日榜 +151 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：qwenlm.github.io/qwen-code-docs 官方文档站 + npm / Homebrew / 一键脚本三路分发 + VS Code / Zed / JetBrains 插件 + macOS / Windows / Linux 桌面版 + v1.x release 持续发版

**核心功能**
- **开箱即用的 Agentic 能力**：Auto-Memory、Auto-Skills、SubAgents、Agent Teams、MCP 全部零配置默认开启；动态工作流让复杂任务自动拆解执行，不用先学一套提示词工程。
- **多协议模型热切换**：支持 OpenAI、Anthropic、Gemini、Qwen API 及任意第三方 / 本地模型（Ollama / vLLM），运行时可切——不想被单一厂商锁定时尤其有用。
- **入口全覆盖**：终端 TUI 之外还有 VS Code / Zed / JetBrains 插件、桌面应用、Web UI、TS / Python / Java SDK，以及 Telegram / 钉钉 / 微信 / 飞书聊天集成（`qwen channel start`）。
- **Daemon 与 Headless 双模式**：`qwen serve` 起常驻服务，多客户端共享同一 Agent 会话（HTTP + SSE + Web Shell）；`qwen -p "..."` 无头模式直接接脚本与 CI/CD。
- **独家：Agent Arena**：多个模型同题对战、同一任务并行对比输出质量——选模型、测回归时是个很实用的「考场」功能。

**技术栈**
TypeScript / Node.js（pnpm monorepo，Vitest + Playwright 测试齐备）+ Java 控制平面（managed-agent 服务端，Spring + MySQL）；分发 npm / Homebrew / 安装脚本；Qwen 3.7 Max 在 SWE-bench Verified 七个版本平均 76.40–77.80%。

**适用场景**
想用一个 Agent 覆盖终端 / IDE / IM 全入口的个人与小团队；需要模型不锁定的多模型混用场景（本地 Ollama + 云端 API 随切）；把编码 Agent 接进钉钉 / 飞书做团队共享助手的国内团队；CI/CD 里的无人值守代码任务。

**推荐理由**
- **国产模型生态里完成度最高的开源编码 Agent**：从 Gemini CLI 分叉后已独立演进上万次提交，文档站、桌面端、IM 通道、企业控制平面都做齐了，不是「套壳 demo」级别的项目。
- **微信 / 钉钉 / 飞书集成是差异化刚需**：国际编码 Agent 基本只覆盖 Telegram / Discord，它把国内团队日常工作的 IM 入口做进去了——这点对国内用户是实打实的便利。

> **注意**：Node ≥ 22，需 Qwen Plus/Pro 订阅或 API key（也支持第三方协议接其他模型）；安全注意：Daemon 默认只监听 loopback 且无认证，本机任何进程都能调它的完整 API（含代码执行），共享主机务必设 `QWEN_SERVER_TOKEN` 并 `--require-auth`；Web UI 与 Daemon 标注实验性；2223 个 open issue 反映社区庞大但响应有积压。

> **一句话理解**：别的编码 Agent 是一把好用的电钻，它是整套电动工具墙：钻头（终端）、锯（IDE 插件）、吸尘器（IM 机器人）共用同一个电机和电池——干活的地方变了，核心始终是那一个。

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

- Trending 日榜 12 条 / 周榜 10 条，合并去重后新候选约三分之一；本期 5 个入选覆盖应用 2、算法 1、工程 1、Agent 1 四类目，单类目不超过 2；五个仓库的 License、活性（全部最近 24 小时内有提交）、非 fork 状态均经 GitHub API 逐个核验。
- 环境说明：本机所在网络对 github.com 与 open.feishu.cn 的 HTTPS 做全量证书替换（伪造 VeriSign Class 1 EV CA，与 11-02 / 11-04 同源），bash 侧 curl / node fetch / git push 全部不可用。本期取数全流程改走 WebFetch 工具通道（Trending 页 + api.github.com + 仓库页 README），产物与本地产物归档照常完成；push 与飞书推送按规则跳过，本地 commit 保留待网络恢复后由发布脚本自动补推。
- MuJoCo 入选说明：上期附录曾以「知名大项目热榜回潮」为由避让，本期破例入选并注明——周榜 +1,671 远超 300 门槛、算法类目无其他达标候选（TensorFold 日增量 +54 不达标且周增量无法核验），且机器人仿真场景（四足 / 人形运动控制训练）对巡检机器人方向的团队有直接参考价值。
- 增量口径：sure、HermesEnabler、codex-security、qwen-code 的增量为 Trending 日榜实测值，mujoco 为周榜实测值；本期无「估算」条目。

**本期按规则排除的候选**

- addyosmani/agent-skills（116.7k，日榜 +816）、anthropics/skills（193.7k，周榜 +6,055）、mattpocock/skills（323k，周榜 +8,731）、google/skills（24.1k，周榜 +1,933）、cloudflare/security-audit-skill（71.2k，周榜 +10,700，且曾因超 30 天未提交排除）—— 技能 / 规则包合集，照旧整类排除。
- GoogleChrome/modern-web-guidance-src（3.1k，日榜 +739，Apache-2.0）—— 「让编码 agent 保持 Web 最佳实践」的规则源仓库，本质是内容 / 规则分发而非可运行软件，按「非资源聚合」口径排除。
- Alishahryar1/free-claude-code（69.3k，日榜 +415）—— 免费多 harness 令牌中转（宣称 1.3B+ 免费 token），ToS / 合规风险，主动排除（同 heretic、闲鱼爬虫案例口径）。
- ggml-org/llama.cpp（134.6k，日榜 +176）、zed-industries/zed（94.9k，周榜 +2,339）、nodejs/node、nvm-sh/nvm（日增量未达 80）—— 高度知名项目的热榜回潮；llama.cpp 增量达标但属知名回潮且算法类目已由 MuJoCo 占位。
- ashhart/TensorFold（2.0k，日榜 +54）—— Zig 写的 Metal/CUDA/Vulkan LLM 推理引擎，方向不错但日增量未达 80 门槛，周榜未见、增量无法核验。
- meta/astryx、CopilotKit/OpenBot、vercel-labs/agent-desktop、vercel-labs/agent-browser、NVIDIA/auto-ontology、D4Vinci/Scrapling、milind-soni/OpenMausBot（曾因 718 open issue / 426MB 让位，本期延续）—— 往期已推送，按 archive/index.json 去重排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-13 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
