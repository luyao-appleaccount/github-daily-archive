# 每日 GitHub 精选 · 2026-10-23（第 12 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [tangency-labs/solidcraft](https://github.com/tangency-labs/solidcraft) | 应用项目 | Rust | 9.3k | 建库 16 天 ≈+4,100 ⭐ 周均（估算） |
| 2 | [shihabal3amri/DiPlay](https://github.com/shihabal3amri/DiPlay) | 应用项目 | Kotlin | 12.1k | 建库 29 天 ≈+2,900 ⭐ 周均（估算） |
| 3 | [jaredpalmer/kev](https://github.com/jaredpalmer/kev) | 算法/模型 | Python | 9.5k | 建库 36 天 ≈+1,840 ⭐ 周均（估算） |
| 4 | [php/php-src](https://github.com/php/php-src) | 工程实践 | C | 41.2k | +287 ⭐ 日榜 |
| 5 | [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | AI Agent | Python | 49.3k | 建库 264 天 ≈+1,300 ⭐ 周均（估算） |

---

## 1. SolidCraft —— 纯 Rust 写的参数化 3D CAD：桌面、浏览器、CLI、MCP 四端同核

**一句话简介**：参数化 3D CAD 长期被商业软件把持，开源侧 FreeCAD 界面老旧、Onshape 在云端闭源。SolidCraft 用纯 Rust 从零写了一套：**草图 + 约束求解器 + 可回放的特征时间线**，改一个尺寸整个模型自动重建；同一套命令同时跑在桌面应用、浏览器、无头 CLI 和 MCP 服务器上——最后这一点意味着可以让 Claude 这类 Agent 直接下指令建模。建库仅 16 天即 9.3k star，是本期增速最陡的应用类项目。

**仓库信息**
- 地址：https://github.com/tangency-labs/solidcraft
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：9.3k（9347）｜ 近期增量：建库 16 天 ≈+4,100 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：solidcraft.io（官网/下载）+ docs.solidcraft.io 文档站 + GitHub Actions CI + GitHub Releases（Windows MSI/macOS DMG/Linux AppImage/Snap）+ 浏览器版直接试用 + docs/ 架构、能力清单、MCP 指南与 oracle 体积校验

**核心功能**
- **参数化建模全流程**：线/弧/样条/文字草图由自研约束求解器驱动；拉伸、旋转、扫掠、放样、圆角、抽壳、孔、螺纹、阵列、镜像挂在可编辑的特征时间线上，配参数化尺寸与单位表达式。
- **装配与钣金**：装配体支持关节、运动学仿真、接触集、干涉检查与质量属性；钣金有折边、卷边、折叠/展开与平面展开图，还带塑料外壳特征。
- **格式进出全**：STEP、IGES、3MF、STL、OBJ、glTF 双向导入导出（按支持度），另有 URDF 导出，可直接喂给机器人仿真。
- **四端同核 + MCP**：桌面 App、浏览器版、headless CLI 与 MCP 服务器跑的是同一套命令注册表；`solidcraft-cli mcp` 接入 Claude Code 后，Agent 能无头驱动设计会话，或 `--connect` 连上正在运行的窗口边改边看。
- **几何正确性有 oracle 兜底**：76 个公开参考件中 75 个体积/面积/质心/包围盒与分析解或 FreeCAD 计算值一致，另一件是已跟踪的 bug——几何内核不是口头说准。

**技术栈**
纯 Rust（含自研约束求解器与几何内核，底层依赖同作者的 SolidCore）；WebAssembly 支撑浏览器版；Apache-2.0；GitHub Actions CI（fmt/clippy/测试/wasm）+ 正式 release 三平台分发 + Snap Store，文档站 docs.solidcraft.io 独立维护。

**适用场景**
想要免费可自托管的参数化 CAD 的创客与硬件工程师；需要把 CAD 能力嵌进自己工具链的团队（headless CLI 批量出 STEP）；想用自然语言驱动建模、把 CAD 接进 Agent 工作流的探索者；教学场景（特征时间线完全可视化）。

**推荐理由**
- **补了开源 CAD 最大的一块短板**：开源世界一直缺一个「现代 UI + 参数化内核 + 浏览器可用」三者齐备的 CAD，SolidCraft 用 16 天的增速证明了痛点真实存在。
- **MCP 接入是真正的差异化**：CAD 恰好是「有明确目标函数但操作繁琐」的典型场景，Agent 下指令、CAD 内核负责几何正确性，这个组合比聊天机器人画图靠谱得多。
- **工程质量自觉**：oracle 几何校验、CI 徽章、架构文档、演示脚本全部开源可复现，不是只有截图的展示型项目。

> **注意**：① **官方自述 early but usable for simple parts**：适合简单零件，复杂装配与工业级可靠性仍在路上（v0.20.0，发布节奏极快）；② 三平台安装包均未签名，Windows 需绕过 SmartScreen、macOS 首次需右键打开；③ 0.11–0.14 版本升级需手动下载一次；④ 浏览器版依赖 WASM，超大装配的性能与桌面端有差距；⑤ 与 FreeCAD 的成熟生态（插件、教程、行业标准）比还差得远，生产切换前先做试点。

> **一句话理解**：像有人把参数化 CAD 的发动机拆开重造了一遍，还顺手给它装了个「AI 遥控器」：你说「把壳加高 8 毫米」，它自己拧螺丝。

---

## 2. DiPlay —— 在比亚迪车机上跑 iPhone 的 CarPlay：免越狱、免硬件的开源投屏方案

**一句话简介**：比亚迪车机是 Android，但 iPhone 用户想要 CarPlay 只能靠第三方盒子。DiPlay 把投屏做成了一个**直接装在车机上的 App**：不用越狱、不用转接盒、不用 Mac 或认证服务器，有线 USB 和无线 Wi-Fi 都能连，还把箭头导航投到了 HUD 上。README 里实车验证记录、逐版本发布说明、诊断导出一条龙俱全——建库 29 天 12.1k star，是本期最「解决具体痛点」的项目。

**仓库信息**
- 地址：https://github.com/shihabal3amri/DiPlay
- 类目：应用项目 ｜ 语言：Kotlin ｜ Stars：12.1k（12080）｜ 近期增量：建库 29 天 ≈+2,900 ⭐ 周均（估算）
- 协议：GPL-3.0 ｜ 官网 / 文档：shihabal3amri.github.io/DiPlay 官网 + docs/ 安装、兼容性、无线调优、隐私、构建文档 + 逐版本 RELEASE-NOTES + VALIDATION.md 实车验证记录 + ANDROID9_WIFI_DIRECT.md 等专项文档 + GitHub Releases（APK）

**核心功能**
- **免硬件有线/无线 CarPlay**：核心 CarPlay 连接不需要 ADB：装到车机即可用；无线支持 Wi-Fi Direct、车机热点或同一路由器三种路径，Android 10+ 会校验协商的组频率。
- **BYD HUD 导航**：在已验证固件上把转向箭头、距离与街道名投到抬头显示，这是多数盒子方案都没做干净的部分。
- **音频与通话打磨**：音频缓冲优化、underrun 恢复、无系统 Opus 编码器的车机上软件降级，通话结束音乐自动恢复。
- **本地诊断与隐私**：设置里一键导出诊断报告，只有用户主动选择才上报；文档明确「永不发热点密码」。
- **八语种含简体中文**：App 内置英/阿/俄/乌/西/简中/繁中/日多语言，Android 13+ 跟随系统逐应用语言设置。

**技术栈**
Kotlin（Android 7.0+，API 24）独立 App `com.shihab.diplay`，可与原厂 DiAuto 并存安装；基于 xcertplay（GPL-3.0）与 DiAuto（AGPL-3.0）的 UI 资产；GitHub Releases 直接分发 APK，v0.2.21 公测中。

**适用场景**
比亚迪 DiLink 4.0/5.x 车机的 iPhone 车主；想在安卓车机上研究 CarPlay iAP2 协议与 AirPlay 握手实现的开发者；车机固件兼容性社区测试的参与者。

**推荐理由**
- **痛点极其具体且普遍**：「BYD + iPhone」是数百万车主的日常，官方不做的功能被社区补上了——29 天 12k star 全是真实需求投票。
- **文档诚实到罕见**：它明说「不是苹果认证产品」、身份来自第三方固件提取、哪些固件验证过哪些没有，风险与边界写得清清楚楚。
- **工程迭代快且有数据支撑**：每一版 release notes 都对应具体修复（音频同步、断线自恢复、麦克风崩溃），VALIDATION.md 记录了开发车与社区测试车的实测结果。

> **注意**：① **未获苹果认证**：APK 捆绑了从公开 Carlinkit 固件提取的实验性配件身份（私钥可被提取），iOS 未来版本可能直接封杀，法律与兼容风险自担；② 官方只支持 BYD 车机，其他品牌明确不修；③ Android 7.0–8.1 的车机兼容性未实车验证；④ 无线 Wi-Fi Direct 在 Android 9 走固件相关的旧路径，频率不可控；⑤ 音频仍有偶发断裂，依赖社区诊断报告继续修；⑥ 这是公测（public preview），别当作日常唯一导航方案。

> **一句话理解**：车机是台安卓电视，DiPlay 是把 iPhone 屏幕搬上电视的投屏 App——只是这道门锁是苹果私有的，它靠一把「借来的钥匙」开门，且明牌告诉你钥匙随时可能被换锁。

---

## 3. Kev —— 可自训练自托管的 Jev 式决策模型家族：0.8B 到 27B 四档全开源

**一句话简介**：让大模型回答「这段合同要不要升级人工」时，它会写一篇小作文再给结论。Jev 类决策模型反其道而行：**一次非自回归前向同时判定是/否、多选与打分**，快且概率可校准。Kev 把这条路线完全开源——四档权重（0.8B 跑笔记本、27B 吃 80GB 单卡）、训练与微调脚本、冻结评测套件全给你，API 与 TypeSafe 官方 SDK 兼容，27B 在未见数据集上的准确率（0.851）距官方 Jev（0.857）不到一个百分点。

**仓库信息**
- 地址：https://github.com/jaredpalmer/kev
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：9.5k（9459）｜ 近期增量：建库 36 天 ≈+1,840 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：Hugging Face Space 在线试用（kev-4b/0.8b）+ docs/model-cards/ 四档模型卡（上下文长度、Brier 分数、逐长度精度）+ 冻结评测套件 jaredpalmer/kev-suites + GitHub release kev-1.0（含 SHA-256 校验）+ GitHub Actions CI

**核心功能**
- **一次前向出三种答案**：同一份文本上，是/否（noul）、多选（choice）、打分（score）问题在单次请求里同时作答，题目之间互相不可见；默认带逐档拟合的温度校准，概率是可信的。
- **四档模型一次发布**：Kev 1.0 把 0.8B/4B/9B/27B 的 checkpoint、模型卡、评测套件与服务代码作为冻结基线一起发布，Hub 上每个权重有 v1.0 tag，可精确复现。
- **评测口径认真**：held-out 数据集是 5 领域 14 个公开数据集的测试集（训练从未见过）；同时报告 Brier 分数衡量整条概率分布，不只看答对没。
- **端侧与端云都覆盖**：CUDA/ROCm 走 PyTorch，Apple Silicon 走 MLX，设备自动探测带隔离探针；一条命令部署自己的 HTTPS 端点，空闲缩容到零。
- **可微调可复现**：用自己的标注样本微调，配套的 coding-agent skill 能在 Modal 上跑完「找问题→训练→服务」全流程。

**技术栈**
Python 3.12/3.13 + uv；0.8B/4B/9B 为 Qwen3.5 base 上的冻结底座 + 小适配器，27B 基于 Qwen3.8 后训练版全参数微调（51GB 权重）；Apache-2.0（代码与权重基座）；服务端实现 TypeSafe System One 兼容 API。

**适用场景**
需要高吞吐、低延迟、概率可校准的结构化判定场景：工单分流、内容风控初筛、合同条款升级人工判断、大规模问卷/评分自动化；想复现或改进 System 1 决策模型的研究者；不想把数据送到 TypeSafe 云端的隐私敏感团队。

**推荐理由**
- **把「黑盒 API」变成「自家权重」**：官方 Jev 只能调云 API，Kev 给出从数据、训练到服务的完整开源对照物，且评测口径（held-out + Brier）比多数开源复刻认真。
- **工程发布纪律罕见**：版本化权重 tag、SHA-256 校验、冻结评测套件、逐长度精度表——像发布数据库一样发布模型。
- **数字诚实**：明确标注 0.8B 在新数据源上准确率掉到 0.648、27B 上下文外的表现未实测、与 Jev 的对比不构成受控实验。

> **注意**：① **PyPI 重名陷阱**：`pip install kev` 装到的是 2016 年的另一个无关包（K.E.V. ORM），本项目只能从源码安装；② 27B 需 80GB 显存（B200/H200/H100-80G）或 96–128GB 内存 Mac，51GB 权重只在 Hub 上；③ 与 Jev 的对比不受控——Jev 的训练数据未知，0.851 vs 0.857 别过度解读；④ 0.8B/4B 在未见数据源上的准确率明显下降，跨域场景先跑评测；⑤ 决策模型只做分类与打分，不生成文本，别拿它当聊天模型用。

> **一句话理解**：大模型答题像每道题都写一篇小作文再划对错；Kev 是考试只涂答题卡的「判卷机器」——快、概率准、还能把判卷标准（权重）搬回自己机房。

---

## 4. php-src —— PHP 解释器本体：三十年 C 语言运行时的活工程，靠版本节奏重回热榜

**一句话简介**：被调侃了二十年的 PHP，它的源码仓库恰恰是工程界的常青树：php-src 是 PHP 解释器本体——**Zend 引擎、JIT 编译器、几十个核心扩展、上千个 phpt 测试全在这一个 C 仓库里**，从 PHP 4 时代一路演进至今仍保持高频提交。本期它以日榜 +287 出现在 Trending，通常与版本发布节奏相关；对学习者来说，这是一份带完整测试与模糊测试基础设施、且仍在线上进化的编译器级 C 工程教材。

**仓库信息**
- 地址：https://github.com/php/php-src
- 类目：工程实践 ｜ 语言：C ｜ Stars：41.2k（41188）｜ 近期增量：+287 ⭐ 日榜
- 协议：BSD-3-Clause ｜ 官网 / 文档：php.net/docs 官方手册 + wiki.php.net（RFC 与内部开发文档）+ GitHub Actions 测试工作流 + OSS-Fuzz 持续模糊测试 + 逐版本 NEWS 变更记录 + UPGRADING 升级说明

**核心功能**
- **解释器全链路在一个仓库**：词法/语法（re2c + bison）、Zend 虚拟机、OPcache 与 JIT、垃圾回收、扩展 API（PECL 的宿主）——想读懂一门语言的完整实现，这里链条最全。
- **质量基础设施完备**：GitHub Actions 测试矩阵 + OSS-Fuzz 持续模糊测试 + 覆盖语言行为的海量 phpt 测试；RFC 流程在 wiki.php.net 公开可追溯。
- **向后兼容的演进纪律**：每个版本有 UPGRADING 说明与 NEWS 逐条记录；核心变更走 RFC 投票，三十年间 API 与语义的迁移路径都有文档。
- **构建系统自洽**：autoconf + 自研 buildconf，Unix 与 Windows 双端构建文档齐备；从 Git 源码最小构建只需 autoconf/bison/re2c 三个工具。

**技术栈**
C（Zend 引擎 + 扩展体系），构建工具链 re2c/bison/autoconf；BSD-3-Clause；测试体系 phpt + GitHub Actions + OSS-Fuzz；官方手册 php.net/docs，RFC 与内部文档在 wiki.php.net。

**适用场景**
想系统学习「一门语言解释器怎么写」的工程师（虚拟机、JIT、GC 的真实工业实现）；为 PHP 生态贡献扩展或修 bug 的维护者；需要自行编译定制 PHP（特定扩展组合、性能调优）的运维；研究大型 C 项目长期维护策略的团队。

**推荐理由**
- **三十年仍高频演进的 C 工程**：多数语言运行时换过几代实现，php-src 在同一套架构上持续演进且保持每周大量提交——大型 C 代码库的生命周期管理范本。
- **质量基础设施是教科书级**：OSS-Fuzz 模糊测试常年在线，phpt 测试覆盖到语义边角，RFC 流程透明——看它怎么做工程比看它做什么更重要。
- **PHP 生态仍在前行的支点**：热榜常客不是因为「复古」，而是因为整个 PHP 生态的每次版本节奏都从这里发出；对依赖 PHP 的团队是必须跟踪的上游。

> **注意**：① 这不是面向使用者的项目：普通开发者用发行版打包的 PHP 即可，从源码编译是构建/贡献/学习场景；② 贡献门槛高：需要对 C、虚拟机与语言语义有较深理解，小修也要过 RFC 或核心开发者评审；③ README 本身极简，学习入口在 wiki.php.net/internals 与源码内注释；④ 日榜 +287 属事件驱动型热度，会随发布周期回落，别据此判断「PHP 回潮」；⑤ 历史包袱重：部分遗留扩展与语义怪癖为兼容性保留，新项目选型请综合评估。

> **一句话理解**：如果说 PHP 应用是街边小馆，php-src 就是那台三十年没熄过火的灶台——所有人吐槽菜色，但灶台本身的锻造与维护工艺，是真能学到东西的。

---

## 5. nanobot —— 自托管个人 AI Agent 框架：WebUI + 八类聊天渠道 + 长期记忆 + 定时任务

**一句话简介**：个人 Agent 框架很多，nanobot 的差异点在「渠道 + 记忆 + 自托管」三件套：**同一个 Agent 同时接 Telegram、Discord、Slack、微信、邮件、Linear 等八类渠道**，会话历史与长期记忆（Dream）持久保存，cron 定时任务与长程目标开箱即用——全部跑在你自己的机器上。HKUDS（港大数据智能实验室）出品，与其 10-20 期推送的 CLI-Anything 同门，49.3k star 说明「自己养一个数字员工」的需求已成主流。

**仓库信息**
- 地址：https://github.com/HKUDS/nanobot
- 类目：AI Agent ｜ 语言：Python ｜ Stars：49.3k（49286）｜ 近期增量：建库 264 天 ≈+1,300 ⭐ 周均（估算）
- 协议：MIT ｜ 官网 / 文档：nanobot.wiki 十语种文档站（含简体中文）+ docs/ 配置、架构、部署、记忆、自动化、渠道接入指南 + PyPI（nanobot-ai）+ GitHub Actions CI + Python SDK 与 OpenAI 兼容 API 文档 + Discord 社区

**核心功能**
- **聊天渠道全覆盖**：WebUI、终端 TUI 之外，Telegram/Discord/Slack/微信/邮件/Mattermost/Linear 等渠道即插即用，消息从哪来 Agent 就在哪回。
- **文件与工具内置**：PDF/Word/Excel/PPT 内置读取工具；shell、网页搜索抓取、MCP 集成、cron 定时、图像生成、多 Agent 委派全部开箱可用。
- **Dream 长期记忆**：跨会话保存偏好与事实记忆，配合会话历史形成长期工作上下文——今天教过的习惯，明天还记得。
- **长程目标与自动化**：long-horizon goals 让 Agent 跨天推进任务，scheduled automations 把重复工作变成定时流水线，可部署为常驻服务或 Agent 网关。
- **模型自由 + 双 API**：接任意 OpenAI 兼容端点或本地模型，支持多供应商回退；对外暴露 Python SDK 与 OpenAI 兼容 API，方便嵌进自己的系统。

**技术栈**
Python ≥3.11（uv/pip/安装器三路分发，稳定版走隔离环境）；MIT；WebUI + TUI 双前端；GitHub Actions CI；PyPI 包 nanobot-ai 持续发布（v0.3.5）；文档站 nanobot.wiki 覆盖 10 个语种。

**适用场景**
想在自己服务器上养一个长期个人助手的独立开发者；需要把 AI 助手接入团队已有聊天工具（Slack/飞书/微信生态）的小团队；做多渠道 Agent 网关、记忆系统或定时自动化的二次开发者；对数据主权敏感、不愿用 SaaS Agent 的用户。

**推荐理由**
- **「渠道矩阵」是真实刚需**：个人 Agent 的价值在「随手可达」，八类渠道 + 持久记忆的组合让它从玩具变成每天真的会用的东西。
- **轻量可读，便于二开**：官方卖点就是 small core、readable internals——相比动辄十几个服务的 Agent 平台，它适合当底座改造而不是黑盒使用。
- **实验室出品且运营成熟**：港大团队持续迭代，十语种文档、PyPI 稳定发布、CI 齐全，「无技术背景安装指南」这类细节说明用户面已超出开发者圈。

> **注意**：① **模型费用自理**：nanobot 不附带模型账号，接云端 API 记得配额与密钥管理，接本地模型看显存；② 把微信/邮箱/Slack 权限交给常驻 Agent 前，先想清楚数据边界与误操作面（它有 shell 工具）；③ 264 天 49.3k star 的增速由建库时长折算，早期爆发占比大，不代表当前仍在此斜率；④ 版本迭代快（v0.3.5），升级前按官方 updating 文档备份；⑤ 多 Agent 委派与图像生成属较新能力，生产使用前单独验证。

> **一句话理解**：相当于开源自托管的「个人数字员工底座」：消息从微信、Telegram、邮件涌进来，同一个员工在后面记事、干活、定时打卡——办公室就在你自己机房里。

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

- 候选池：Trending 日榜 9 条 + 周榜 15 条（合并约 22 个仓库），其中 10 个已在往期推送；新增候选里技能/插件合集与 `NOASSERTION` 仍占大半，靠 Search API 补池（`created:>2026-09-10 stars:>1200` 新建高星一组 + `topic:agent-framework` 一组，另对 8 个单仓逐个核验元数据）。
- 类目配额：应用项目 ×2（SolidCraft、DiPlay）、算法/模型 ×1（Kev）、工程实践 ×1（php-src）、AI Agent ×1（nanobot）——覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：Apache-2.0 ×2（SolidCraft、Kev）+ MIT ×1（nanobot）+ GPL-3.0 ×1（DiPlay）+ BSD-3-Clause ×1（php-src）。5 个仓库均有完整 README 正文与正式 release；SolidCraft/Kev/nanobot 有 CI，php-src 另有 OSS-Fuzz，DiPlay 有逐版发布说明与实车验证记录。
- 去重检查：与往期十一期（09-28 至 10-22，共 55 个仓库）均无重叠，基线为 `archive/index.json`；本期五个仓库亦无 storytold 家族、同名双仓等甄别问题。
- 数据口径：total stars、License、最近提交取自 `gh api repos/*`（5 个仓库 `pushed_at` 均在 2026-10-22 当天或其后，30 天活性线内）；php-src 的 +287 为 Trending 日榜原始数字，其余四个未上榜，「周均增量」为**由「累计 star ÷ 建库天数」换算的估算值**（SolidCraft 16 天 ≈4,100/周、DiPlay 29 天 ≈2,900/周、Kev 36 天 ≈1,840/周、nanobot 264 天 ≈1,300/周），速览表统一标注「估算」。
- 本期风险提示（与功能同等看待）：`DiPlay` 未获苹果认证且捆绑第三方固件提取的配件身份，iOS 更新或法律边界都可能突变；`SolidCraft` 官方自述仅适合简单零件且安装包未签名；`Kev` 的 PyPI 同名包陷阱必须从源码安装，27B 需 80GB 显存；`php-src` 日榜热度属事件驱动型，且项目门槛对普通开发者极高；`nanobot` 把微信/邮箱等私有渠道交给常驻 Agent 前务必先做数据边界评估。

**本期按规则排除的候选**

- `supabase/supabase`（日 +693）、`anomalyco/opencode`（周 +6,750）、`HKUDS/CLI-Anything`（周 +3,275）、`akitaonrails/ai-memory`（周 +3,322）、`debpalash/VoiceStudio`（周 +13,581）、`heygen-com/hyperframes`（周 +5,669）、`NationalSecurityAgency/ghidra`（周 +4,892）、`stablyai/orca`（周 +9,401）、`Comfy-Org/ComfyUI`（周 +4,375）、`morluto/rea`（周 +106,341）、`NandhaKishorM/laya`、`Niko1221/Strata`、`yetone/magpie`、`browser-use/jev-ultrafast`、`deepseek-ai/DeepInfer`、`robbietilton/Compositor`、`Droid-Deck/DroidDeck`：热度全部达标，但均已在往期推送，按 `archive/index.json` 去重基线排除。
- `anthropics/claude-plugins-official`（周 +5,649）、`android/skills`（周 +1,384）、`K-Dense-AI/scientific-agent-skills`（周 +3,967）、`cursor/plugins`（周 +2,046）、`DietrichGebert/ponytail`（173.6k）、`Graphify-Labs/graphify`（133.0k）、`ruvnet/ruflo`（78.5k）、`wheresryan22/anatomy`（19.2k，单个绘图 skill）、`rehan-remade/universal-modder`（8.7k，技能/工具合集）、`yihui-dev/awesome-opus5-5-videos`（9.3k，视频合集）：产物形态是 agent 技能/插件/提示词/媒体集合，属资源聚合型，按规则排除——本期榜单此类仍占大半。
- `luongnv89/claude-howto`（43.3k，日榜 +177，MIT）：示例驱动的 Claude Code 图文教程加复制即用模板集，属教程/资源聚合，非可运行软件项目，按「非纯教程大纲」口径排除。
- `Meloong-Git/PCL`（8.7k，日榜 +119，Minecraft 启动器）、`Gathin23/cleanyourtv`（24.3k）、`NirDiamant/agents-towards-production`（21.7k，Jupyter 教程合集）：License 为 `NOASSERTION` 或缺失，按「License 明确」口径排除。
- `storytold/photocraft`（71.4k）、`pdfcraft`（17.2k）、`filmcraft`（15.8k）、`wordcraft`（15.6k）、`lightcraft`（14.3k）、`vectorcraft`（10.4k）：同一组织的纯 Rust 重写家族（延续 10-14 期口径：同源同质只取其一，`artcraft` 已推送），整族不再重复入选。
- `Ebony-Vinyl/dsh-our-free-model`（36.9k，建库 29 天）：延续上期判定——「免登录免 API Key 用前沿模型」的插件，合规与可持续性存疑，不推荐。
- `openai/math`（15.4k，Lean，研究手稿合集）、`google-research/harness2`（18.0k，README 无项目描述）、`cdyforever/how-to-live-better`（13.1k，书籍在线阅读页非软件）、`xai-org/grok-build`（镜像仓）、`cloudflare/security-audit-skill`（最后提交 09-14，超 30 天活性线）：分别按既有口径排除。
- `KnifeLemon/Filee`（10.2k，C#，MIT，建库 24 天 ≈2,975/周估）：离线 255 格式文件转换器，指标合格且实用，但应用类目两个名额让位给工程含量更高的 SolidCraft 与痛点更普遍的 DiPlay。
- `fastapi/fastapi`（103.8k，日榜 +101，MIT）、`pydantic/pydantic-ai`（20.8k）、`microsoft/agent-framework`（14.3k）、`esengine/DeepSeek-Reasonix`（35.9k）、`eigent-ai/eigent`（15.6k）、`omnigent-ai/omnigent`（11.0k）、`666ghj/BettaFish`（42.5k，pushed 10-16）、`HKUDS/nanobot` 同门候选：均合格或接近合格，但本期工程/Agent 名额有限，fastapi 增量仅勉强过线，Agent 类目取热度最高的 nanobot，其余让位。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-23 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
