# 每日 GitHub 精选 · 2026-11-02（第 17 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（2）、算法/模型（1）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [lightpanda-io/browser](https://github.com/lightpanda-io/browser) | 工程实践 | Zig | 40.2k | 日榜 +825 ⭐ |
| 2 | [cjpais/Handy](https://github.com/cjpais/Handy) | 应用项目 | Rust | 36.6k | 日榜 +339 ⭐ |
| 3 | [kornia/kornia](https://github.com/kornia/kornia) | 算法/模型 | Python | 11.8k | 日榜 +101 ⭐ |
| 4 | [CopilotKit/OpenBot](https://github.com/CopilotKit/OpenBot) | AI Agent | TypeScript | 9.6k | ≈870/周（估算） |
| 5 | [Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu) | 应用项目 | TypeScript | 13.2k | 日榜 +941 ⭐ |

---

## 1. Lightpanda —— 为 AI 与自动化从零打造的 headless 浏览器：内存省 16 倍、快 9 倍

**一句话简介**：Agent 时代每个自动化任务都要开浏览器，而 Chromium 一直是那个又慢又吃内存的「隐形税」——Lightpanda 干脆换掉了内核。

**仓库信息**
- 地址：https://github.com/lightpanda-io/browser
- 类目：工程实践 ｜ 语言：Zig ｜ Stars：40.2k（40218）｜ 近期增量：日榜 +825 ⭐
- 协议：AGPL-3.0 ｜ 官网 / 文档：官方文档站 lightpanda.io + Docker 官方镜像 + Homebrew / Nix / AUR 多渠道安装 + 独立基准测试仓库 lightpanda-io/demo + 正式 release 1.0.2（2026-10-23）

**核心功能**
- **为 Agent 而生的新内核**：不基于 Chromium 或 WebKit，用 Zig 从零实现网络与 DOM 栈，专为爬虫、自动化与 AI Agent「取 DOM、不渲染像素」的场景设计，冷启动快、二进制小。
- **数量级优势的基准**：官方基准：AWS 上抓 933 个真实网页，100 页峰值内存 123MB（headless Chrome 约 2GB、省约 16 倍），耗时 5 秒（Chrome 46 秒、快约 9 倍），方法与数据全部公开可复现。
- **CDP 协议兼容**：原生实现 Chrome DevTools Protocol，Playwright、Puppeteer 现有脚本改一个连接地址即可运行，抓取、DOM 交互等常用能力开箱即用。
- **部署渠道齐全**：Homebrew / Nix / AUR / 官方 Docker 镜像 / nightly 二进制全平台分发，Docker 一行命令即可起 CDP 服务（127.0.0.1:9222）。

**技术栈**
Zig 从零实现 + 原生 CDP 服务端 + libcurl 网络栈；无 Chromium / WebKit 依赖，单二进制分发。

**适用场景**
大规模网页抓取与数据采集；AI Agent 的浏览器工具（替代高内存 headless Chrome）；CI 里的轻量 DOM 测试；批量内容抽取管道。

**推荐理由**
- **Agent 时代的基础设施缺口**：Agent 规模化后 Chromium 的内存与启动开销是真实瓶颈，Lightpanda 是目前社区认可度最高的专用解（40.2k star、日榜 +825、1.0 正式版刚发布）。
- **迁移成本几乎为零**：坚持 CDP 兼容而非另起协议，Playwright / Puppeteer 用户换个 ws 地址就能切换，生态策略务实而非激进。

> **注意**：不渲染像素，不适合截图 / 视觉验证类场景；Zig 生态年轻，重型 JS 与强反爬站点的兼容性需逐站验证；AGPL-3.0 对商用嵌入有传染性约束；Linux 二进制依赖 glibc 2.35+，Alpine 需自行编译。

> **一句话理解**：headless Chrome 是开着全套设备的重型卡车，Lightpanda 是只装了取件箱的电动摩托——单页交付快得多、省电得多，但不能拉冰箱。

---

## 2. Handy —— 完全离线的开源语音转文字：按住说话、松手出字，语音不出本机

**一句话简介**：没有账号、没有订阅、没有上传——一个「装上就能用」的全局听写工具，把云厂商按月收费的能力变成了本地免费水电煤。

**仓库信息**
- 地址：https://github.com/cjpais/Handy
- 类目：应用项目 ｜ 语言：Rust ｜ Stars：36.6k（36615）｜ 近期增量：日榜 +339 ⭐
- 协议：MIT ｜ 官网 / 文档：handy.computer 官网 + 全平台安装包（Homebrew cask / winget / deb）+ Raycast 扩展 + CLI 远程控制参数 + 正式 release v0.9.8（2026-10-03）

**核心功能**
- **全局快捷键听写**：按住快捷键说话、松手即把文字粘贴进当前任意应用的输入框，支持 Hold / Toggle 等多种触发模式，微信、IDE、邮件、表单通吃。
- **纯本地推理**：Silero VAD 自动过滤静音，Whisper（Small 到 Large，GPU 加速）与 Parakeet V3（CPU 优化、自动语种检测）双模型可切换，音频全程不上云。
- **跨平台 + 可扩展**：Tauri v2 构建，Windows / macOS / Linux 全支持；自定义词典纠正专有名词，CLI 参数可远程控制正在运行的实例，另有无障碍定位的调试模式。
- **免费无障碍立场**：项目起因是「无障碍工具不该有付费墙」，完全免费开源，为键盘输入困难的用户与隐私敏感者提供了真正的替代品。

**技术栈**
Rust + Tauri v2 桌面壳 + Whisper / NVIDIA Parakeet V3 本地模型 + Silero VAD；CPU 可跑、有 GPU 自动加速。

**适用场景**
随时随地口述回消息、写文档；会议通话中快速记要点；不便打字的无障碍场景；不想把语音交给云服务的隐私敏感用户。

**推荐理由**
- **刚需 + 极致克制**：只做「说话进文本」一件事，不搞订阅不搞账号，36.6k star 与持续日增说明它精准命中了系统自带听写之外的真实缺口。
- **模型可换、留有后手**：Whisper 与 Parakeet V3 双模型可选，没有 GPU 的 CPU 机器也有可用档位，避免绑定单一模型的退化风险。

> **注意**：首次使用需下载模型（数百 MB 起）；专业术语与中英混杂准确率取决于所选模型档位；Homebrew cask 与 winget 渠道为社区维护非官方直发；v0.9.x 仍属 1.0 前版本，偶有平台权限问题需按 README 授予。

> **一句话理解**：Handy 像给电脑配了个「本地速记员」：你说完它打完，稿子永远不出家门——云听写则是把录音快递给外地打字员，快不快、秘不秘都得看别人。

---

## 3. Kornia —— PyTorch 生态的可微计算机视觉库：1200+ 算子，把几何代码变成 GPU 标准件

**一句话简介**：凡是「手写版本会写得很长很脆」的几何与增强代码，Kornia 大概率有现成、可微、GPU 批量化的实现——而且输赢基准全部公开。

**仓库信息**
- 地址：https://github.com/kornia/kornia
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：11.8k（11823）｜ 近期增量：日榜 +101 ⭐
- 协议：Apache-2.0 ｜ 官网 / 文档：kornia.org 官网 + readthedocs 文档站 + 浏览器在线 Playground + Colab 教程 + PyPI（v0.9.0，2026-10-23 发布）+ 官方逐算子性能与 ONNX 导出支持页

**核心功能**
- **1200+ 可微算子**：相机模型、对极几何、最小解算器与 RANSAC、特征检测与匹配（LoFTR、LightGlue、DISK 等）、形态学、图像损失，大部分算子在 torchvision 中没有对应物，且几乎全部支持反向传播。
- **一个批次各自参数**：gaussian_blur2d 可传 (B,2) 的 sigma、warp_affine 传 (B,2,3) 矩阵——torchvision 一次调用只能一组参数，批处理得自己写循环，Kornia 天生批量化。
- **GPU 上的几何求解**：基础矩阵 / 本征矩阵 / 单应 / PnP 求解器与 RANSAC 全部批量化跑在 GPU 上，配合 torch.compile 可整体编译成一张计算图，避开主机同步。
- **可编译可导出**：上千个算子配置支持 torch.compile 与 ONNX 导出，官方逐算子公布性能与导出支持矩阵——赢了输了都写明，基准诚实度罕见。

**技术栈**
纯 Python + PyTorch；GPU 批处理优先设计；与 OpenCV / scikit-image / torchvision 互补而非替代。

**适用场景**
SLAM / 三维重建 / 相机标定的批处理几何计算；训练管线中的图像增强（图像、掩码、框、关键点同步变换并可逆）；深度学习驱动的图像处理；边缘端 ONNX 部署。

**推荐理由**
- **填补 torchvision 的空集**：增强与几何这块 PyTorch 官方生态长期只覆盖基础变换，Kornia 是事实上的「可微 CV 参考实现」，2018 年至今持续维护、上个月刚发 0.9.0。
- **基准公开到逐算子**：官方性能页把对 OpenCV / torchvision 的输赢逐项公布（含「OpenCV 单图 CPU 仍更快」的结论），选型可以直接看数据不用听宣传。

> **注意**：与 torchvision 重叠的算子（翻转 / 裁剪 / 亮度）在 GPU 上未必更快，选型请看官方性能页；单张 uint8 CPU 图像处理 OpenCV 仍是首选；0.9.x API 演进较快，升级需看迁移说明；算子面广但学习曲线偏陡。

> **一句话理解**：Kornia 之于 OpenCV，好比「能求导的计算器」之于「普通计算器」：不只给你结果，还能算出结果对输入的敏感度——训练神经网络时这恰恰是必需品。

---

## 4. OpenBot —— 自托管 AI 同事平台：每个 Agent 一台带独立浏览器与登录态的虚拟电脑

**一句话简介**：「Agent 能用工具」和「敢让它靠近工具」是两回事——OpenBot 用独立容器 + 审计网关补上了企业敢真部署的那条线。

**仓库信息**
- 地址：https://github.com/CopilotKit/OpenBot
- 类目：AI Agent ｜ 语言：TypeScript ｜ Stars：9.6k（9558）｜ 近期增量：≈870/周（估算）
- 协议：MIT ｜ 官网 / 文档：copilotkit.ai/openbot 产品页 + docs/ 完整文档 + prompt.txt（喂给 AI 助手的防踩坑部署提示）+ CI 与安全审计双流水线 + release v0.2.0（2026-10-12）

**核心功能**
- **一个 Agent 一台电脑**：每个 Bot 分到一个独立容器：自己的 Chromium、自己的登录态、自己的文件工作区，互不污染，由 supervisor 统一创建与回收。
- **治理网关**：Bot 的所有工具调用（浏览器、文件、MCP、组件）都经过同一网关：先按策略裁决、再写审计行、最后才执行；拒绝时会指明触发的规则。
- **协议层解耦框架**：Bot 是任意讲 AG-UI 协议的端点，LangGraph、Mastra、CrewAI、Pydantic AI 或手写 Agent 接入方式一致，治理随协议走而非随框架走。
- **模板而非产品**：定位是克隆改造：内置通用助手与知识库两个开箱 Bot，examples/ 另有 10 个职场场景模板（报销核对、会议纪要跟进、值班交接等）可复制成自己的同事。

**技术栈**
TypeScript + Bun 1.4 + Docker Compose（数据落在自己的 PostgreSQL）+ AG-UI 协议 + CopilotKit Intelligence（可自托管）；模型 Key 管理员配置、静态加密。

**适用场景**
企业内网部署可控的 AI 员工；需要审计留痕的合规行业（金融、医疗）；给现有 LangGraph / CrewAI Agent 补一套界面、权限与隔离执行环境。

**推荐理由**
- **补上 Agent 落地最难的一环**：工具治理 + 全量审计 + 容器隔离正是企业部署最缺的骨架，OpenBot 把这套结构做成了开箱即用的模板，而非论文或 PPT。
- **工程姿态端正**：README 开头就写明 Beta、无托管版、需替换 examples 才能用，甚至为 AI 助手准备了逐条核对过仓库的 prompt.txt，成熟度标注透明。

> **注意**：Beta 早期项目，API 与行为会持续变动；依赖 CopilotKit Intelligence（免费计划可本地跑，但属于生态绑定）；Bun 1.4 等新工具链有版本敏感；需自备模型 Key，默认单管理员模式上线前务必开启登录。

> **一句话理解**：OpenBot 像给每个 AI 实习生发一台公司配的电脑和一张工卡：能上哪些网站、动哪些文件都有门禁记录，出了事查得到——而不是让实习生共用你自己的电脑和密码。

---

## 5. ziwei-doushu —— 开源紫微斗数排盘引擎：完整算法 + 67.5 万命盘 × 877 万段解读数据集

**一句话简介**：把一个通常闭源收费的领域做成了可复现的公共品：排盘算法全公开，877 万段解读每一条都能回查到讲课时间戳与古籍原文。

**仓库信息**
- 地址：https://github.com/Renhuai123/ziwei-doushu
- 类目：应用项目 ｜ 语言：TypeScript ｜ Stars：13.2k（13208）｜ 近期增量：日榜 +941 ⭐
- 协议：MIT（代码）/ CC BY 4.0（数据） ｜ 官网 / 文档：ouranic.cn 在线体验 + CI 流水线 + Release v4.0-13d（按年份 77 个数据文件）+ 中英双语 README + 完整「开源边界」说明（什么开源、什么不开源）

**核心功能**
- **完整排盘引擎**：十二宫安星、四化、大限流曜全套算法纯 TypeScript 实现，支持真太阳时校正、中国夏令时判定与海外出生地时区修正，历史钟表时间换算有专门的查表引擎。
- **超大解读数据集**：v4.0 数据集（2026-10-15 发布）：1950–2026 每个真实日期 × 12 时辰 × 男女 = 67.5 万张命盘 × 13 维 = 877 万段解读（约 204 亿字），压缩后仅 161MB、按年份分 77 个文件下载。
- **知识库有出处**：断语逐句对照倪海厦《天纪》讲课时间戳与《紫微斗数全书》原文校正，古籍引证 405 处可逐字回查——传统文化项目里罕见的可验证性。
- **许可边界清晰**：代码 MIT、数据集 CC BY 4.0、古籍公版、倪师原话 CC BY-NC-SA 非商用；README 还主动写明六亲判断在斗数体系中的方法论局限。

**技术栈**
TypeScript + Next.js 前端 Demo + 纯 TS 算法库（可独立引用）+ GitHub Release 分发的版本化数据集 + CI 自动化。

**适用场景**
传统命理应用与小程序的排盘后端；国学 / 民俗研究与教学素材；对话式 AI 的领域知识库（结构化断语 + 出处标注，适合 RAG）；个人系统学习紫微斗数。

**推荐理由**
- **把玄学做成了工程**：算法开源、数据可下载、引证可回查，13.2k star 与日榜 +941 说明这种「可验证的传统智慧」获得了极大的社区共鸣。
- **数据集本身就是资产**：56.6GB 解压后的结构化解读文本是现成的中文领域语料，对 RAG 与知识库构建者有直接价值，且压缩包仅 161MB、按需分年下载。

> **注意**：命理解读属传统文化范畴，项目自己也标注了六亲等维度的局限，请理性看待；断语库与线上完整版不开源；数据集用于商用解读时注意倪师原话的 NC（非商用）授权边界；界面是 Demo，与线上版有差距。

> **一句话理解**：排盘引擎像「标准计算器」，数据集像「附出处的一万本参考书」：市面同类产品往往只给黑盒服务，它把公式和书都摊开给你。

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

- Trending 日榜 17 条 / 周榜 16 条，合并去重 33 条，其中 8 个为往期已推送、10 个为技能 / 规则包类合集；本期 5 个入选覆盖应用 / 工程 / 算法 / Agent 四类目（应用 2、其余各 1），全部经 gh api 核验 License、活性与 release。
- 10-30 至 11-01 三天调度未产出（日期链存在缺口，index.json 如实反映），本期恢复正常。
- 口径说明：日 / 周榜为 Trending 实测值，标注「估算」者为「累计 star ÷ 建库天数 → 周均」（OpenBot 建 77 天），仅作热度参考。

**本期按规则排除的候选**

- YuJunZhiXue/dsh-purge（15.4k，周榜 +6,644）—— 模型越狱 / 破甲工具类，合规风险，排除（与 togg53192-cmd/jailbreaks 同口径）。
- beenuar/AiSOC（6.3k，日榜 +446，MIT，v21.0.0 高频发版）—— AI 安全运营平台本身合格，但应用 / Agent 类目配额已满，名额让位。
- milind-soni/OpenMausBot（10.6k，日榜 +922）—— 与 OpenBot 定位重叠（VM 隔离执行），且 640 个 open issue 反馈积压，名额让位。
- anomalyco/hex（3.3k，日榜 +1,179）—— 本地语音听写与已入选的 Handy 同类，类目配额已满，让位。
- hyprwm/Hyprland —— 日榜增量 +38 低于 80 门槛；ghostty-org/ghostty（周榜 +589）为长期成熟项目、无新增亮点，均未入选。
- public-apis/public-apis、patchy631/ai-engineering-hub —— 资源聚合列表，照旧排除。
- thedotmack/claude-mem、pingdotgg/t3code、JetBrains/thinkrail、TauricResearch/TradingAgents、affaan-m/ECC、FlashML-org/FreeToken、Nutlope/hallmark、pbakaus/impeccable —— 均已推送过，去重排除。
- obra/superpowers、anthropics/skills、jakubkrehel/skills、Leonxlnx/taste-skill、multica-ai/andrej-karpathy-skills、AgriciDaniel/claude-seo、cloudflare/security-audit-skill、Donchitos/Claude-Code-Game-Studios —— 技能 / 插件 / 规则包合集类，照旧排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-11-02 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
