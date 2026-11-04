# 每日 GitHub 精选 · 2026-11-04（第 18 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（1）、工程实践（2）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [ghostty-org/ghostty](https://github.com/ghostty-org/ghostty) | 应用项目 | Zig | 63.4k | 周榜 +771 ⭐ |
| 2 | [D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling) | 工程实践 | Python | 95.0k | 日榜 +1,658 ⭐ |
| 3 | [floci-io/floci](https://github.com/floci-io/floci) | 工程实践 | Java | 28.9k | 日榜 +482 ⭐ |
| 4 | [hiyouga/LlamaFactory](https://github.com/hiyouga/LlamaFactory) | 算法/模型 | Python | 75.9k | 周均 ≈420 ⭐（估算） |
| 5 | [vercel-labs/agent-desktop](https://github.com/vercel-labs/agent-desktop) | AI Agent | Rust | 13.0k | 日榜 +3,791 ⭐ |

---

## 1. Ghostty —— 用 Zig 重写的原生终端：GPU 渲染不牺牲手感，还顺手拆出可嵌入的终端库

**一句话简介**：选终端长期是个三选一：要快就牺牲功能，要功能就牺牲原生手感——Ghostty 想证明这三件事可以同时成立。

**仓库信息**
- 地址：https://github.com/ghostty-org/ghostty
- 类目：应用项目 ｜ 语言：Zig ｜ Stars：63.4k（63450）｜ 近期增量：周榜 +771 ⭐
- 协议：MIT ｜ 官网 / 文档：ghostty.org 官网与安装页 + libghostty 的 C API Doxygen 文档 + 公开 Roadmap 与 xterm 兼容性审计用例 + GitHub Releases 提供 macOS 通用包与 Linux 各发行版安装包

**核心功能**
- **原生，不是套壳**：macOS 端是真正的 SwiftUI 应用：Metal 渲染、CoreText 字体发现，支持 AppleScript 与 Shortcuts；Linux 端是 GTK 应用并深度集成 systemd（单实例开新窗口、cgroup 隔离），不是同一套控件硬搬。
- **标准兼容做得很硬**：行为优先级明确写死为「标准 → xterm → 其他流行终端」，对遗留序列做过完整 xterm 审计并沉淀成一致性测试；同时支持 Kitty 图形协议、剪贴板序列、同步渲染、明暗模式通知等现代序列。
- **一个应用，也是一个库**：除终端本体外提供零依赖的 C / Zig 库 libghostty；已可用的 libghostty-vt 负责序列解析与终端状态维护，兼容 macOS / Linux / Windows / WebAssembly，可直接嵌进自己的应用（官方给了 Ghostling 这个最小示例项目）。
- **窗口与配置齐全**：多窗口、标签页、分屏，支持标签重命名与配色；配置为纯文本（快捷键、主题、字体等），可以纳入 dotfiles 版本管理。

**技术栈**
核心用 Zig 编写；macOS 侧 SwiftUI + Metal，Linux 侧 GTK4 + systemd 集成；渲染走 GPU 加速，另对外暴露 C ABI 的 libghostty。

**适用场景**
日常替代 iTerm2 / Alacritty / kitty；把终端能力嵌进自家桌面应用（用 libghostty）；需要脚本化控制终端窗口的 macOS 自动化；对终端协议兼容性要求高的 TUI 开发与调试。

**推荐理由**
- **绕开了老取舍**：「GPU 快的不好看、好看的慢」是终端圈的老问题，Ghostty 用共享 Zig 核心加各平台原生 UI 的组合破局，63.4k star、周榜 +771 说明认可度不是一时热度。
- **库化思路更有长期价值**：把终端解析抽成可支持 WASM 的 libghostty-vt，意味着终端能力可以进入 Web 与嵌入式场景，这比「又一个好看的终端」的想象空间大得多。

> **注意**：Windows 版仍在路线图内未完成，目前只有 macOS 与 Linux 可用；libghostty 尚未打版本号、C API 签名仍在变动，生产嵌入需锁定 commit；「Ghostty 独有控制序列」一项官方明确标注尚未开始，跨终端脚本不要依赖；Linux 包跟随发行版仓库，老旧发行版需自行编译。

> **一句话理解**：别的终端是把同一台发动机塞进不同外壳，Ghostty 是按每个平台的路况重新调校底盘——手感是本地原生的，但引擎是同一套。

---

## 2. Scrapling —— 从单次请求到整站采集：解析快一个数量级，网站改版也不怕选择器失效

**一句话简介**：爬虫真正贵的不是写，是维护——网站一改版选择器就全崩，Scrapling 主要就是在压这笔维护成本。

**仓库信息**
- 地址：https://github.com/D4Vinci/Scrapling
- 类目：工程实践 ｜ 语言：Python ｜ Stars：95.0k（95046）｜ 近期增量：日榜 +1,658 ⭐
- 协议：BSD-3-Clause ｜ 官网 / 文档：scrapling.readthedocs.io 完整文档 + PyPI 包 + Docker 官方镜像 + GitHub Actions 测试 + MCP Server 与可安装 Agent Skill + 十种语言 README（含简体中文）

**核心功能**
- **解析层快一个数量级**：官方基准：自研解析器约 2ms / 次，BS4 + lxml 约 1562ms、Selectolax 约 197ms；提供 CSS、XPath、文本、正则四种选择方式与相似元素匹配。
- **自适应选择器**：元素定位不写死 CSS 路径，而是按元素特征定位，网站改版后仍能找回同一批节点，显著降低「一改版就全部失效」的重写成本。
- **Fetcher 分层升级**：从纯 HTTP 请求，到 stealth 浏览器、JS 渲染、Cloudflare Turnstile 处理、持久登录会话、后台 API 抓包，按目标站难度逐级加码，不必一上来就开浏览器。
- **采集工程化**：Spider 支持并发、代理轮换、自动重试、AutoThrottle、暂停 / 续爬、流式处理，结果直接导出 JSON / JSONL / CSV / XML，或一键转成 LLM 可读的干净 Markdown。
- **为 Agent 准备的两件套**：内置 MCP Server（支持 CDP 远程浏览器与 HTTP 传输鉴权）与可安装的 Agent Skill，让编码 Agent 写出的调用代码跟得上最新 API，而不是照旧版本瞎猜。

**技术栈**
纯 Python（≥3.10），解析器自研、浏览器层基于 Playwright 系内核；按需分层安装 extras（fetchers / ai / rag / shell），PyPI 与 Docker 双路分发。

**适用场景**
竞品价格与舆情监控；把站内文档整站转成 RAG 语料；需要登录态与反爬对抗的数据采集；让 AI Agent 自主取网页数据（走 MCP）。

**推荐理由**
- **覆盖面罕见**：多数库只解决解析、或只解决并发，Scrapling 从单次请求一路做到整站爬取、导出与 Agent 调用；95.0k star、日榜 +1658 且只有 7 个 open issue，工程完成度很扎实。
- **给 LLM 时代补了课**：markdown() 一行把页面转成干净语料、MCP Server 直接给 Agent 用，这两点恰恰是老牌爬虫库普遍缺失的部分。

> **注意**：反爬与绕过 Cloudflare 的能力有明确合规边界，只应用于自有或已授权站点，抓取前先看目标站 robots 与 ToS；`pip install scrapling` 默认只装解析器，用 fetcher 或 spider 需装 `scrapling[fetchers]` 并执行 `scrapling install` 下载浏览器与系统依赖；浏览器层内存与磁盘占用不小，容器化时预留空间；BSD-3-Clause 可商用但需保留版权声明。

> **一句话理解**：传统爬虫像按一张老地图找门牌，网站一装修地图就作废；自适应选择器像按「门口那棵歪树」认路——换了招牌也还认得出是哪家。

---

## 3. Floci —— MIT 的 AWS 本地模拟器：53 项服务跑在本地，社区版不阉割功能

**一句话简介**：云上开发的循环是「改代码 → 部署 → 等 → 看账单」，Floci 想把这段压成本地几秒钟、零账单。

**仓库信息**
- 地址：https://github.com/floci-io/floci
- 类目：工程实践 ｜ 语言：Java ｜ Stars：28.9k（28871）｜ 近期增量：日榜 +482 ⭐
- 协议：MIT ｜ 官网 / 文档：floci.io 官网与服务矩阵文档 + Docker 镜像（含 LocalStack 兼容层）+ 原生二进制（Quarkus + GraalVM，amd64 / Apple Silicon）+ docker compose overlay + Testcontainers 用法

**核心功能**
- **53 项服务本地跑**：计算（EC2 / ECS / EKS / Lambda / Batch）、存储与数据库（S3 / DynamoDB 含 PartiQL 与时间点恢复 / RDS / Neptune）、消息（SQS / SNS / Kinesis / EventBridge 含 replay）、网络（VPC / Route 53 / CloudFront / API Gateway）、身份（Cognito 含 MFA 与 SRP / IAM / KMS / Secrets Manager），另有 CloudFormation、Step Functions、Bedrock、Athena 等。
- **细粒度 IAM 授权模拟**：基于 AWS Service Reference 生成资源 ARN 检查表，覆盖上千个操作，能真实复现「权限不够」的报错——而不是本地一律放行、上线才炸。
- **LocalStack 平滑替换**：提供 `-compat` 镜像，内置 awslocal 包装脚本与 `/etc/localstack/init/ready.d/` 初始化钩子，并对 PERSISTENCE、EDGE_PORT、GATEWAY_LISTEN 等变量做翻译，现有脚本改个镜像名即可跑。
- **两种分发形态**：Docker 镜像（可挂载 docker socket 以启动 Lambda / 容器类服务），以及 Quarkus + GraalVM 编译的原生二进制（启动快、内存小，支持 amd64 与 Apple Silicon，可 make native-install）。
- **状态可持久化**：支持持久化路径，重启后实例、备份任务等状态可恢复，适合需要长期保留测试数据的集成测试。

**技术栈**
Java / Quarkus 构建，GraalVM（Mandrel）编译原生镜像；Docker 分发，配 docker compose overlay 与 Testcontainers 集成方式。

**适用场景**
本地开发与 CI 里跑依赖 AWS 的集成测试；离线 / 内网环境复现云上行为；用 Testcontainers 起一套临时 AWS；上线前验证 IAM 策略是否真的够用。

**推荐理由**
- **解决真金白银的痛点**：LocalStack 功能完整的版本收费，Floci 以 MIT 全功能免费加原生二进制的低资源占用切入，日榜 +482、当天仍在提交，活跃度可信。
- **兼容层做得细**：不是只改端口号，而是把错误码、分页行为、IAM 资源级检查都对到 AWS 的实际行为——这类「像不像」的细节，才决定测试到底有没有意义。

> **注意**：不是所有服务都 100% 等价：Rekognition 只做图像分析、不支持流处理，Elastic Beanstalk 与 Redshift Serverless 的 IAM 资源检查尚不完整；169 个 open issue 说明边角服务仍在追赶；部分场景的 awslocal 需显式 `--endpoint-url`；本地模拟无法替代对真实环境的配额、网络与计费行为验证。

> **一句话理解**：它相当于给 AWS 配了一台飞行模拟器：仪表盘、告警灯、操作手感都尽量还原，但你不会拿它去验证真实气象。

---

## 4. LlamaFactory —— 一套配置微调 100+ 大模型：显存账算得清，零代码也能跑

**一句话简介**：微调的门槛从来不是会不会写训练脚本，而是每个模型一套模板、换一个模型就要重写一遍——LlamaFactory 把这层胶水做成了产品。

**仓库信息**
- 地址：https://github.com/hiyouga/LlamaFactory
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：75.9k（75868）｜ 近期增量：周均 ≈420 ⭐（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：llamafactory.readthedocs.io 官方文档 + ACL 2024 论文 + LlamaBoard Web UI + HuggingFace Space / ModelScope 在线体验 + Docker 镜像（含 Ascend NPU 版）

**核心功能**
- **100+ 模型统一入口**：LLaMA、Qwen3 / Qwen3-VL、DeepSeek、Gemma、GLM、Phi、Mistral / Mixtral-MoE、MiniCPM 等，新模型通常 Day 0 / Day 1 跟进，训练配置基本不用改。
- **训练方法全谱系**：预训练、SFT（含多模态）、奖励建模、PPO、DPO、KTO、ORPO、SimPO，每种都支持 Full / Freeze / LoRA / QLoRA；量化侧覆盖 AQLM、AWQ、GPTQ、HQQ、EETQ 等 2–8 bit 方案。
- **显存优化组合拳**：GaLore、BAdam、APOLLO、DoRA、LongLoRA、PiSSA、LoRA+，配合 FlashAttention-2、Unsloth、Liger Kernel 与 FSDP+QLoRA——官方给出的数字是 2×24GB 显卡即可微调 70B。
- **零代码 Web UI**：`llamafactory-cli webui` 启动 LlamaBoard，浏览器里完成训练、评估、推理与权重导出；实验追踪可接 TensorBoard、Wandb、MLflow、SwanLab。
- **多硬件后端**：CUDA、AMD ROCm 与华为 Ascend NPU 都有支持，NPU 侧提供预构建镜像，国内团队落地阻力小。

**技术栈**
Python（≥3.11）+ PyTorch（≥2.0）+ transformers / peft / trl / accelerate；LlamaBoard 基于 Gradio；分布式侧支持 DeepSpeed 与 FSDP，推理可接 vLLM / SGLang。

**适用场景**
用企业私有数据做领域 SFT；把开源模型对齐成客服 / 代码 / 多模态助手；在有限显卡上验证 QLoRA 方案；教学与论文复现（ACL 2024 配套实现）。

**推荐理由**
- **省掉的是最脏的活**：chat template 对齐、多模态数据 collator、分布式启动参数这些「每个模型都不一样」的细节被收敛进 YAML，这才是 75.9k star 的真实来源。
- **显存账提前算清**：README 直接给出 7B–70B 各训练方法的最低显存表，选型时不用先踩一遍 OOM 才知道方案行不行。

> **注意**：必须使用与模型匹配的 chat template，且训练与推理要用同一套，否则效果明显劣化（推理版模型用 `_nothink` 后缀区分）；部分新模型需从 main 分支安装 transformers 并设 `DISABLE_VERSION_CHECK=1`；Windows 需手动装 GPU 版 PyTorch，QLoRA 另装 bitsandbytes，FlashAttention-2 需自行编译；1216 个 open issue 说明社区问题积压较多，冷门模型组合要有自己排障的准备；模型权重仍受各自许可证约束。

> **一句话理解**：它像一台万能转接头：各种模型、各种训练方法、各种显卡都插得上，你只需要选档位（写 YAML），不用为每个插头重新焊一遍线。

---

## 5. agent-desktop —— 让 Agent 用无障碍树操作桌面，不靠截图猜按钮

**一句话简介**：GUI 自动化绕了十年「截图 + 图像识别」的远路，agent-desktop 回到操作系统本来就在提供的答案：无障碍树。

**仓库信息**
- 地址：https://github.com/vercel-labs/agent-desktop
- 类目：AI Agent ｜ 语言：Rust ｜ Stars：13.0k（13007）｜ 近期增量：日榜 +3,791 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：agent-browser.dev/desktop 官方文档站（安装 / 快照与 ref / 错误恢复 / 平台差异 / C API）+ GitHub Releases 原生包 + npm 与 Homebrew 分发 + MCP 模式 + CONTRIBUTING / SECURITY

**核心功能**
- **不截图也能操作**：直接读桌面应用的无障碍树（macOS AX / Windows UI Automation / Linux AT-SPI），返回结构化 JSON，每个可操作元素带 ref（形如 `@s8f3k2p9:e8`），点击、输入、选择都针对 ref 执行。
- **观察—动作—复核的闭环**：Agent 先 snapshot 拿 ref，再 click / type，然后重新 snapshot 确认结果；UI 变了会返回 `STALE_REF` 或 `AMBIGUOUS_TARGET`，逼着 Agent 重新观察而不是盲点。
- **默认无头执行**：动作默认不移动鼠标、不抢焦点（headless），需要真实物理输入时加 `--headed`；60 个命令覆盖窗口管理、剪贴板、通知、滚动、拖拽、会话与 trace。
- **三种接入方式**：CLI（每条命令输出统一 JSON envelope）、C 库 `libagent_desktop_ffi`（进程内调用，官方给了 ctypes 示例）、`agent-desktop mcp` 把全部命令暴露成 MCP 工具走 stdio。
- **自带 Agent 说明书**：二进制内置与版本匹配的 guide：`agent-desktop skills get desktop / platform` 直接输出怎么用、何时可安全重试、平台差异在哪，可装进 skills.sh 或写进 AGENTS.md。

**技术栈**
Rust 编写，按平台拆 crate（core / macos / windows / linux）+ PlatformAdapter 抽象；对外提供 C ABI 的 FFI 动态库；npm、Homebrew、Release 原生包三路分发。

**适用场景**
让 Agent 操作没有 API 的老客户端软件（ERP、财务、内网工具）；回归测试里的端到端 GUI 验证；替代基于图像识别的 RPA；需要三平台统一接口的桌面自动化。

**推荐理由**
- **路线选择正确**：图像识别驱动的 GUI Agent 很容易被分辨率、主题、DPI 搞崩，无障碍树是语义化的，稳定性与 token 效率都更好，日榜 +3791 说明这个判断被市场认可。
- **工程化程度高**：统一的 JSON envelope、明确的错误码与重试语义、按 OS 拆 crate 的 CI（cargo test -p …）、文档站与 C 库齐全，不像实验性 demo。

> **注意**：强依赖操作系统无障碍权限：macOS 需在「辅助功能」里授权，否则命令直接失败（`permissions --guide` 可引导）；Linux 要求 Ubuntu 24.04+ 且 X11 与 Wayland 行为不同，Windows 需 10 1809+；快照、剪贴板、截图可能含隐私内容，官方明确提醒不要写进公开日志或上传；key-down / key-up / mouse-down / mouse-up 四个命令要等 daemon 能释放按键才可用；只能看到暴露进无障碍树的控件，自绘 UI（游戏、Canvas）不可见。

> **一句话理解**：截图识别像用眼睛看照片猜按钮在哪，无障碍树像直接读界面的目录结构——前者换个皮肤就认错，后者告诉你每个按钮叫什么、能点什么。

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

- Trending 日榜 13 条 / 周榜 16 条，合并去重 27 条：其中 6 条往期已推送、10 条为技能 / 插件 / 规则包合集。本期 5 个入选覆盖应用 / 工程 / 算法 / Agent 四类目（应用 1、工程 2、算法 1、Agent 1），License、活性与 release 均已逐个核验。
- 口径说明：日 / 周榜增量取自 Trending 实测值；LlamaFactory 未上 Trending，标「周均 ≈420」为「累计 star ÷ 建库天数 → 周均」的估算（建库约 1,256 天），仅作热度参考，不与实测值混用。
- 环境说明：本期本机出口网络的 HTTPS 被中间设备整体替换证书（命令行侧全部校验失败），命令行取数通道不可用；数据改由工具侧通道抓取 Trending、Search API 与仓库页，归档推送与飞书推送按「失败只跳过并说明」原则处理，未降低任何证书校验。

**本期按规则排除的候选**

- Usagi-org/ai-goofish-monitor（16.5k，日榜 +228，MIT）—— 闲鱼商品监控类爬虫，平台 ToS 与合规边界存疑，且 10-10 后无提交、已贴近 30 天线，名额让位。
- p-e-w/heretic（38.9k，日榜 +701）—— 「去除模型审查」类工具，用途合规风险，排除。
- max-sixty/worktrunk（10.6k，日榜 +438，Rust，MIT）—— 面向并行 Agent 的 git worktree 管理 CLI，项目合格，但工程类目已由 Scrapling 与 floci 占满，名额让位。
- shiyu-coder/Kronos（46.6k，日榜 +503）—— 2026-04 之后无提交，不满足「30 天内有提交」，排除。
- anomalyco/hex（4.6k，日榜 +410）—— 本地语音听写，与往期已推的 Handy 同类，让位。
- spotify/portal-ai-plugins（3.1k，日榜 +91）—— 插件集合，且日增刚过门槛、以内部插件为主，排除。
- Gathin23/cleanyourtv（51.4k）—— License 为 NOASSERTION，按既有口径排除。
- Ebony-Vinyl/dsh-our-free-model、HunYiSage/dsh-purge —— 免 Key 白嫖模型 / 越狱破甲类，合规存疑，排除。
- storytold/photocraft、pdfcraft、wordcraft —— 同一组织的纯 Rust 重写家族，同源同质，延续整族排除。
- thedotmack/claude-mem、pingdotgg/t3code、JustVugg/colibri、JetBrains/thinkrail、TauricResearch/TradingAgents、affaan-m/ECC —— 均已推送过，去重排除。
- mattpocock/skills、obra/superpowers、anthropics/skills、jakubkrehel/skills、multica-ai/andrej-karpathy-skills、AgriciDaniel/claude-seo、cloudflare/security-audit-skill、Donchitos/Claude-Code-Game-Studios、Nutlope/hallmark、pbakaus/impeccable —— 技能 / 插件 / 规则包合集，照旧排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-04 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
