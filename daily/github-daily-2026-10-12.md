# 每日 GitHub 精选 · 2026-10-12（第 5 期）

> 筛选范围：GitHub Trending（日榜 + 周榜）+ Search API 补充近期 star 增量高、30 天内有提交的细分领域项目
> 本期入选 5 个，覆盖类目：应用项目（1）、算法/模型（2）、工程实践（1）、AI Agent（1）
> 与往期去重：本期仓库均未在往期推送（去重基线 `archive/index.json`）

---

## 速览

| # | 仓库 | 类目 | 语言 | Stars | 近期增量 |
|---|------|------|------|-------|----------|
| 1 | [robbietilton/Compositor](https://github.com/robbietilton/Compositor) | 应用项目 | Swift | 15.9k | ≈+4,284 ⭐ 周均（估算） |
| 2 | [NandhaKishorM/laya](https://github.com/NandhaKishorM/laya) | 算法/模型 | Python | 32.4k | ≈+9,437 ⭐ 周均（估算） |
| 3 | [lyogavin/airllm](https://github.com/lyogavin/airllm) | 算法/模型 | Python | 36.5k | +548 ⭐ 日榜 |
| 4 | [tester-army/e2e](https://github.com/tester-army/e2e) | 工程实践/工具链 | TypeScript | 9.1k | +6,440 ⭐ 周榜 |
| 5 | [mvschwarz/openrig](https://github.com/mvschwarz/openrig) | AI Agent 及基础设施 | TypeScript | 7.0k | +2,028 ⭐ 周榜 |

---

## 1. Compositor —— 用 Swift 从零写的 macOS 图像编辑器

**一句话简介**：对标 Photoshop 的免费开源位图编辑器，原生 macOS（Apple 芯片）应用：图层 / 蒙版 / 调整图层 / 图层效果 / 内容感知填充 / Camera Raw 一应俱全，可直接读入 PSD 并保留图层与蒙版，工程文件 `.comp` 就是「一堆 PNG 图层 + 一份清单」，Agent 能直接生成与改写你的设计稿。

**仓库信息**
- 地址：https://github.com/robbietilton/Compositor
- 类目：应用项目 ｜ 语言：Swift ｜ Stars：15.9k（15911）｜ 近期增量：≈+4,284 ⭐ 周均（估算）
- 协议：MIT ｜ 官网 / 文档：robbietilton.com/compositor + GitHub Releases / Homebrew cask

**核心功能**
- **图层与蒙版对标 Photoshop**：图层与图层组、完整混合模式、组不透明度、图层蒙版（绘制 / 填充 / 反相 / 模糊 / 羽化，且能画到图层像素范围之外）、剪贴蒙版与组蒙版；调整图层涵盖色相饱和度、色阶、曲线、曝光、渐变映射、颗粒、黑白、色彩平衡、反相、高斯模糊、动感模糊与噪点。
- **图层效果与非破坏变换都在 GPU 上**：描边、投影、颜色叠加、内阴影、外发光、内发光随时可改；移动 / 缩放 / 旋转 / 翻转都不破坏原分辨率，支持自由变形（⌘ 拖拽手柄）与多图层 / 整组一起变换，并有画布与图层边缘吸附。
- **选区与修图链路完整**：矩形与椭圆选框、自由套索、多边形套索、魔棒（按颜色）与对象描边双模（Tab 切换）、选择主体、扩展 / 收缩 / 羽化、内容感知填充（甚至能把画面补到画布之外）；画笔、内容感知修复画笔、仿制图章、模糊工具、渐变与形状（保持可编辑而非栅格化）、可拖动缩放的多行文字段落框、吸管与完整取色器。
- **Camera Raw 级调色面板**：亮度、色彩、曲线、颜色混合器、颜色分级、细节、光学与几何集中在画布旁的独立面板，实时预览且存在选区时只作用于选区；另有色阶 / 曲线 / 色相饱和度 / 曝光 / 渐变映射等独立调整与高斯模糊、动感模糊、暗角、辉光、镜头校正、去背景等滤镜。
- **PSD / PSB 可编辑导入**：支持 JPEG、PNG、HEIC、TIFF、WebP、SVG、相机 RAW（先显影）以及 PSD / PSB（8 位 RGB）；Photoshop 的图层、蒙版、混合模式、填充矩形与椭圆、简单横排文字都保持可编辑，其余矢量与竖排文字转为像素，且**应用前会展示转换报告**。
- **原生 macOS 手感**：多标签工程、⌘F 命令搜索（类似 Raycast 的全局命令面板）、F 键全屏专注画布、标尺与可拖参考线、可调布局网格与吸附、导航迷你地图、导出 PNG / JPEG / 单页 PDF、自动更新（已签名与公证）、Photoshop 风格快捷键且可重映射。
- **为 AI Agent 设计的工程格式**：一个 `.comp` 就是「PNG 图层文件夹 + manifest」，Agent 或脚本可以直接构建与修改工程，打开中的工程会随文件写入**实时更新**（见 `docs/writing-comp-files.md`）。

**技术栈**
纯原生 macOS 应用：Swift + Xcode 工程（Xcode 26+ 构建），图层效果走 GPU 渲染。发行渠道为 GitHub Releases 的 DMG 与 Homebrew cask（`brew install --cask robbietilton-compositor`），`scripts/release.sh` 负责签名、公证与打包。要求 macOS 26.0 或更高版本，且仅限 Apple 芯片。

**适用场景**
不想订阅 Adobe、又觉得 GIMP 交互不顺手的设计与摄影后期用户；需要在 Mac 上做合成、修图、批量导出的独立创作者；想把「AI 生成 / Agent 编排」接进真实图层工程的工作流（让 Agent 写 `.comp`，在打开的编辑器里继续手工精修）；想读源码学习专业图像编辑器架构与 PSD 解析的开发者。

**推荐理由**
- **功能覆盖度不像个人项目**：从图层组不透明度、蒙版可超出图层像素、非破坏变换，到内容感知填充与 Camera Raw 面板，这是一条完整的专业合成链路；而它由一位维护者完成，MIT 协议，代码完全可改。
- **PSD 兼容策略很务实**：不追求 100% 保真，而是「能保留就保留、不能保留转为像素」，并在应用前给出转换报告——比静默丢数据或干脆拒绝打开都更可用。
- **Agent 友好是设计出来的，不是蹭概念**：把工程格式定义成「PNG 图层 + 清单」并支持实时重载，意味着 AI 生成的设计稿可以真正落进一个能继续手工精修的编辑器里，而不是停在图片层面。

> **注意**：① **仅支持 macOS 26.0+ 与 Apple 芯片**，Intel Mac 与 Windows / Linux 均不可用；② 目前**只有英文界面**，且作者明确不接受翻译 PR（单人维护、无法审校自己看不懂的语言），要中文界面只能自行改源码；③ PSD / PSB 导入限 8 位 RGB，**不支持 CMYK**，印刷流程需另行处理；④ 属「个人作品级」项目，长期维护强度与响应速度需自行评估；⑤ 从源码构建需 Xcode 26+ 并自行配置签名与公证凭据。

> **一句话理解**：可以理解成「一个 MIT 协议、能读 PSD、还能让 AI 直接往里面写图层」的 Photoshop 精简替代品：重点不是全面替代，而是把最常用的合成链路做扎实，并且把工程文件开放给脚本。

---

## 2. Laya —— 非自回归的多语言「决策」小模型

**一句话简介**：把「分类 / 打分 / 是否」这类决策从「让大模型生成一段文字再解析」改成「一次前向直接出答案」：非自回归 System 1 决策引擎，单问题约 33ms、批量 7.2ms/问题，覆盖 100+ 语言，用一个 Router 按请求挑 checkpoint；输出是概率而非文本，因此没有解析失败、也没有幻觉。

**仓库信息**
- 地址：https://github.com/NandhaKishorM/laya
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：32.4k（32354）｜ 近期增量：≈+9,437 ⭐ 周均（估算）
- 协议：Apache-2.0 ｜ 官网 / 文档：nandhakishorm.github.io/laya（另有 BENCHMARKS.md 全量基准报告）

**核心功能**
- **三种封闭式决策类型**：`choice`（多选项）、`score`（有序打分）、`noul`（是 / 否概率），对任意文本载体（邮件、工单、JSON 文档）都能提问，返回概率分布而不是生成的文字。
- **一次前向，不做自回归生成**：没有逐 token 生成，因此没有需要解析的结构、也没有可幻觉的自由文本；T4 上测得单问题 p50 约 32.8ms，批量吞吐可达 103–332 问题/秒。
- **按语言自动路由**：`Router` 用纯 Python 在 0.5ms 内检测文字脚本，非英文自动切换到多语言 checkpoint——官方基准显示英文 checkpoint 在非拉丁脚本上会「高置信度答错」（高棉语原始温度下 0.000 准确率却有 0.952 置信度），所以路由不是优化而是必需。
- **RLCD 训练 + 可校准的置信度**：以严格适当评分规则（strictly proper scoring rules）做强化学习训练，并提供温度缩放校准流程；官方报告在 typed-decisions（2,000 条决策）上微调后准确率 0.766（基座 0.362），ECE 0.081（对比同赛道 TypeSafe Jev 的 0.246）。
- **生态接入点很多**：PyPI 包 + TypeScript SDK（`laya-ts`）+ Java 实现；可选 `laya[serve]` HTTP 服务、`laya[mcp]` MCP 服务、`laya[langchain]` / `laya[llamaindex]` / `laya[crewai]` 集成、`laya[onnx]` ONNX Runtime、`laya[fast]` TileLang GPU 快路径、`laya[structured]` 配合 pydantic。
- **把「限制」写得很直白**：`BENCHMARKS.md` 给出全部 51 种语言的逐语言数据，并主动列出自己落后的场景（选项数 > 20 时因 head token 预算分摊导致标签难区分，Banking77 仅 0.425 对比 Jev 0.870）、置信度不等于正确性、以及各 checkpoint 出厂即过度自信需自行拟合温度。

**技术栈**
Python 3.10+（`pip install laya`），基于 ModernBERT-large（421M）/ mmBERT-base（322M）；三个 checkpoint 以 Apache-2.0 发布在 Hugging Face（convaiinnovations/laya、laya-multilingual、laya-typed-decisions）；依赖 transformers 5.x / torch 2.14 / huggingface_hub 1.x。另有 TypeScript（laya-ts）与 Java 实现，Apple MPS 与 CUDA 均可运行，支持 ONNX Runtime 与 CPU-only 部署。

**适用场景**
客服工单路由与意图分类；邮件 / 评论的多维标注（部门 + 紧急度 + 流失风险这类多问题一次问）；内容审核与合规判定；任何「低延迟、要概率、要能设阈值」而不是「要一段自然语言」的场合；希望把 LLM 的分类调用换成小模型以省 token 与延迟的团队；需要覆盖多语言但不想每种语言各训一个模型的项目。

**推荐理由**
- **在一个窄问题上做到实在的更好**：官方基准中它在多数任务上准确率略优于同赛道的 TypeSafe Jev（typed-decisions 0.766 vs 0.727、AG News 0.950 vs 0.910、DAIR Emotion 0.595 vs 0.480），延迟快 6–8 倍（32.8ms vs 236–276ms），ECE 好 3 倍，权重还是 Apache-2.0 开放——这几点在同赛道里很突出。
- **把「不做生成」变成工程优势**：分类任务用生成模型最大的隐患是解析失败与幻觉，非自回归一次前向从结构上消掉了这两类问题，也就省掉了 prompt 里那些「请只输出标签」的约束与后处理。
- **对局限的诚实程度罕见**：主动写明 >20 选项场景自己落后、置信度不等于正确、出厂概率未校准需自行拟合温度、以及每种语言的实际表现——这种自我暴露反而显著提高了可信度。

> **注意**：① 它**不是通用 LLM**，只做 choice / score / yes-no 三类封闭式决策，写作、总结、多轮对话都不在射程内；② 选项数超过 20 时默认设置下明显掉点（Banking77 的 77 选项仅 0.425），需要调大 `head_max_len` 或先用 `predict_shortlist` 缩小候选；③ 出厂 checkpoint **概率是过度自信的**，用阈值做业务门禁前必须先在自己的数据上做温度校准并验证；④ 路由只做脚本级语言判断，长文本多语混排时可能选错 checkpoint；⑤ 长文档需显式传 `max_len=8192`，否则默认 1024 截断；⑥ 部分示例与基准由社区贡献（含中文场景的飞书式决策集），引用前建议自行复现。

> **一句话理解**：把它想成「一个专门做选择题的 400M 小模型」：给它一段邮件和几个候选选项，它不写文字、直接吐概率——相当于把「请只输出分类标签」的 LLM 调用换成了一个 30 毫秒的本地判别器。

---

## 3. AirLLM —— 用 4GB 显存跑 70B（乃至 2.8T）模型

**一句话简介**：不做量化、不蒸馏、不剪枝，靠「按层流式加载」把推理显存压到极低：单张 4GB 显卡可跑 70B，官方实测 Kimi K3（2.8T）仅 3.72GB、Qwen3.8-Flash-Next（125B）5.95GB、DeepSeek-V3（671B）约 12GB，并且已支持在小显存上做微调（只把适配器留在 GPU）。

**仓库信息**
- 地址：https://github.com/lyogavin/airllm
- 类目：算法/模型 ｜ 语言：Python ｜ Stars：36.5k（36503）｜ 近期增量：+548 ⭐ 日榜
- 协议：Apache-2.0 ｜ 官网 / 文档：PyPI airllm + Colab 示例 notebook（README 内含逐模型实测数据）

**核心功能**
- **无需量化即可降低显存**：核心是逐层分解与流式加载：推理时只把当前层放进显存，因此不用 4bit / 8bit 量化也能跑起远超显存容量的模型，权重精度与原始 checkpoint 一致。
- **一行代码换模型**：`AutoModel.from_pretrained("Qwen/Qwen3-32B")` 即可，几乎任何主流模型通用（v2.6 起自动识别模型类型，无需指定模型类），也支持本地路径与 `layer_shards_saving_path` 指定切分缓存位置。
- **MoE 按需加载专家**：对混合专家模型（如 Kimi K3）只加载当前 token 实际路由到的专家——这是 2.8T 模型能压进 3.72GB 的关键。
- **可选的块状量化加速**：提供基于块状量化的压缩模式，官方称最多再提速 3 倍且精度损失「几乎可忽略」（依据 arXiv 2212.09720）；默认关闭，需要速度时再开。
- **预取重叠加载与计算**：v2.5 起加入预取，把权重加载与计算重叠，减少纯流式方案的空转时间（官方称约 10% 提速）。
- **小显存也能微调**：2026-09 新增训练支持：逐层流式传入冻结权重、只把适配器留在 GPU，官方称 125B 模型在 6GB（RTX 3060 Ti）下可训、27B 在约 2GB 下可训（seq 512）。
- **CPU 与 Mac 也能跑**：支持 CPU 推理（v2.10.1）与在 macOS 上跑 70B（v2.8.2），不强制要求 CUDA。

**技术栈**
Python，`pip install airllm`；依赖 Hugging Face transformers / safetensors / torch，模型侧支持 Qwen（含 MoE 与多模态）、Llama 3.x / 4、DeepSeek V2 / V3、Phi-4、Gemma、ChatGLM 等；PyPI 正式发版（6 个 release），提供多个 Colab 示例 notebook。个别新模型需要特定栈组合（如 Kimi K3 要求 CUDA 12 版 torch 与 transformers 4.56.x）。

**适用场景**
只有一张消费级显卡（4–12GB）却想本地试跑超大开源模型的个人开发者与研究者；显存紧张、又不愿接受量化精度损失、愿意用时间换空间的场景；在 Mac 或纯 CPU 机器上做本地推理验证；需要在小显存上做 LoRA 类微调实验的团队；以及做「超大模型可行性验证」而非线上高并发服务的场合。

**推荐理由**
- **思路简单但效果硬**：把「显存不够」这个最常见的门槛，用逐层流式加载直接绕开，而且不需要改动模型权重——这意味着输出质量与原始模型一致，而不是「能量化出个大概」。
- **对新模型的跟进很激进**：2026-06 起陆续支持 Qwen3-235B（约 3GB）、Qwen3.8-27B（3.33GB）、Qwen3.8-Flash-Next（5.95GB），2026-07 跟上 2.8T 的 Kimi K3，2026-09 又补上训练路径——这正是它 36.5k star 能持续增长的原因。
- **文档给的是实测数字与环境要求**：每个模型都标注了实测显存以及对应的 transformers / torch / CUDA 要求（例如 K3 强制 flash-attn 且只支持 CUDA 12 构建），而不是笼统写一句「支持」。

> **注意**：① 这是**用时间换空间**的方案：逐层从磁盘与主机内存搬运权重，单 token 延迟远高于常规推理，不适合在线高并发或低延迟服务，定位是「跑得起来」而不是「跑得快」；② 首次运行会先把模型**分层切分并落盘**，非常占磁盘（官方 FAQ 里最常见的报错就是磁盘满导致的 MetadataIncompleteBuffer），需预留远超模型体积的空间，`delete_original=True` 可省一半但会删掉原始 checkpoint；③ 新模型常要求特定栈组合（如 Kimi K3 需 CUDA 12 版 torch、transformers 4.56.x 与 compressed-tensors、flash-attn），环境准备比调 API 麻烦；④ 训练支持是 2026-09 才加入的早期能力，生产使用需自行验证；⑤ README 中含付费推广位（AI 素材 / 表情编辑器链接），引用时注意区分官方信息与广告。

> **一句话理解**：就像把一本 200 斤的百科全书放在书架上、而不是整本摊在桌上：需要哪一页就抽哪一页，所以桌子（显存）很小也能读——代价是每翻一页都要去书架取一次，读起来慢。

---

## 4. e2e —— 用自然语言驱动的端到端测试框架

**一句话简介**：把「用自然语言描述目标、让 Agent 去点」和「用定位器与断言做精确校验」放进同一个测试用例：Agent 步骤一旦被后续断言验证过就会被记录，**下次运行直接回放、不再调模型**——于是测试既好写，又不会每次跑 CI 都烧 token。

**仓库信息**
- 地址：https://github.com/tester-army/e2e
- 类目：工程实践/工具链 ｜ 语言：TypeScript ｜ Stars：9.1k（9053）｜ 近期增量：+6,440 ⭐ 周榜
- 协议：Apache-2.0 ｜ 官网 / 文档：e2e.tester.army/docs（文档随 npm 包发布，可离线给 Agent 读）

**核心功能**
- **Agent 步骤与断言混用**：`await agent.act('把工作区升级到 Pro 套餐')` 接 `await agent.assert('发票预览显示按比例计费金额')`，再接常规的 `expect(screen.getByRole('status')).toContainText('Pro')`——语义化操作与确定性断言写在同一个 test 里。
- **回放机制省掉重复的模型调用**：被后续断言验证过的 Agent 步骤会记录动作，**下一次运行直接回放，直到应用发生变化才重新调用模型**；不含 Agent 步骤的测试完全不需要模型。
- **自带模型选择权**：支持自带订阅、API Key 或本地模型（Bring your own），不绑定单一厂商。
- **Web 与移动端一套 API**：Web 引擎通过 Playwright 驱动 Chromium / Firefox / WebKit；移动引擎通过 agent-device 驱动 iOS 模拟器与 Android 模拟器，测试写法一致。
- **开箱即用的工程化配套**：`npx e2e init` 交互式生成配置与示例测试；`examples/` 提供 Vite、Next.js、Astro、Expo、SwiftUI、Jetpack Compose、Kotlin Multiplatform、Flutter 八个可跑通的独立工程；另有 PR 评论 reporter（`@e2e-dev/github`）与托管浏览器 / 模拟器包（`@e2e-dev/kernel`、`@e2e-dev/eas`、`@e2e-dev/smol`）。
- **文档可离线给 Agent 读**：完整文档站 e2e.tester.army/docs，且 `e2e` 包会把每个页面一起发布，编码 Agent 可以直接在 `node_modules/e2e/docs` 里离线读取。

**技术栈**
TypeScript / Node.js，npm 包按职责拆分：`e2e` 为 SDK + runner + CLI，`@e2e-dev/web`、`@e2e-dev/mobile` 为引擎，`@e2e-dev/decision` 为决策模型执行器；Web 侧底层是 Playwright，移动侧是 agent-device。Apache-2.0 协议，npm 正式发版（32 个 release），有 Discord 社区、CONTRIBUTING 与 SECURITY 流程。

**适用场景**
前端团队的 E2E 与冒烟测试：把「打开设置页 → 升级到 Pro → 校验发票」这类以用户目标描述的流程交给 Agent 执行，同时保留确定性的角色定位器断言；移动 App（iOS / Android）的回归测试；在 PR 上自动跑测试并把结果以评论形式回帖；希望编码 Agent 自己维护测试套件的团队。

**推荐理由**
- **回放机制解决了 AI 测试最大的成本痛点**：「Agent 探索一次、之后按记录回放」让模型调用从「每次 CI 都跑」变成「应用变了才跑」，既保留自然语言的易写性，又避免了测试成本随运行次数线性上升。
- **没有放弃确定性断言**：它没有把校验也交给模型，而是把最终判定交回 Playwright 式定位器与断言——这恰恰是纯「让 AI 点一点」方案最容易被质疑的地方。
- **示例覆盖真实技术栈**：八个框架的独立可跑工程（含 SwiftUI、Jetpack Compose、KMP、Flutter）比只给一个 React demo 更能说明可用性。

> **注意**：① **尚在 1.0 之前**，官方 README 明确写着小版本之间 API 与配置仍可能变化，不建议现在就当成不可变的基础设施依赖；② Agent 步骤需要模型，虽然支持本地模型，但仍需自备额度或算力，且首次探索的成本高于回放；③ 移动端依赖模拟器环境，CI 上需要相应 runner（官方提供托管的 EAS Simulators 与 smol 微虚拟机方案，属商业服务）；④ CLI **默认开启匿名遥测**（可 `npx e2e telemetry disable` 或设 `E2E_TELEMETRY_DISABLED=1` 关闭），企业内使用需评估；⑤ 由 TesterArmy 公司主导开发，Apache-2.0 开源，但长期路线与商业版边界需自行判断。

> **一句话理解**：像「先让实习生按目标自己摸索一遍并把操作录下来，之后回归测试就按录像重放」——只有当页面改版让录像失效时，才再请实习生重走一遍。

---

## 5. OpenRig —— 用 YAML 把 Agent 编成一个常驻团队

**一句话简介**：「harness 包装模型，rig 包装你的 harness」：用 YAML 定义一支多 Agent 团队（角色、模型、上下文、权限），一条命令拉起，让 Claude Code 与 Codex 在同一个 rig 里被当成一个系统管理；你只跟 lead 谈目标，它去协调跨团队的专家并回报结果与需要你拍板的决策。

**仓库信息**
- 地址：https://github.com/mvschwarz/openrig
- 类目：AI Agent 及基础设施 ｜ 语言：TypeScript ｜ Stars：7.0k（6978）｜ 近期增量：+2,028 ⭐ 周榜
- 协议：Apache-2.0 ｜ 官网 / 文档：openrig.dev + 仓库内 docs/ 参考手册与 Discussions Q&A

**核心功能**
- **团队用 YAML 定义，一条命令拉起**：`rig up starter --cwd . --plan` 先预览再启动；TUI 里可以先看团队拓扑图，再看座位表（每个座位的运行时、模型、上下文与状态），最后看单个座位详情。
- **异构 harness 混编**：同一个 rig 里可以同时放 Claude Code 和 Codex，按座位指定 provider 与模型；缺哪个就装哪个，不强制你同时订阅两家。
- **预置三档团队，按需扩展**：`starter`（一个 Claude 构建者 + 一个 Codex 评审者，做一件有边界的改动）、`workshop`（lead / builder / QA / reviewer，单仓库持续工作）、`factory`（七个座位：lead、advisor、build、QA、design 与两个独立评审，做持续产品开发）。
- **工作有队列、有地址、可追踪**：座位有稳定地址（如 `dev-build@starter`），用 `rig send` 派活、`rig queue list` 查任务；上下文与在制品留在固定地址上，而不是散落在若干终端会话里。
- **面向「有界改动」的完整闭环**：官方给出的用法是：给 builder 一件有边界的事 → 它记录任务并返回 ID → 本地验证行为 → 请本 rig 内的 reviewer 评审候选产物 → 你看最终产物与评审意见 → 再回到同一个 builder 做下一件。
- **把「改了本机什么」写成一张表**：README 专门列出一节说明会写入的东西（`~/.openrig` 实例状态、`~/.tmux.conf` 块、`~/.claude/skills` 与 `~/.agents/skills` 中的技能、Claude / Codex 的 hooks 与 workspace trust 记录、仓库内 `.codex/plugins` 等），并明确提示先备份。
- **活动遥测的边界写清楚了**：活动中继只发送事件类型、座位 / 运行时身份、时间戳与原生会话标识，**不含提示词文本与工具参数**。

**技术栈**
TypeScript / Node.js（要求 Node 22 或 24）+ tmux；macOS 与 Linux 原生支持，Windows 走 WSL2（原生 Windows 不支持，官方自动化测试也尚未在 WSL2 上跑）。通过 npm 发布 `@openrig/cli`（提供 `rig` 与 `openrig-tui` 两个命令），另有带 `--dry-run` 预览的安装脚本、TUI 面板、Herdr / Ghostty 终端集成与 rig bundle 分发机制；Apache-2.0，44 个正式 release。

**适用场景**
已经在用 Claude Code / Codex、却被「一堆并行终端会话 + 上下文丢失」困住的开发者；想把「一个人 + 多个 Agent」组织成有角色分工、有评审环节的稳定流程的小团队；需要在同一个仓库里让构建者与评审者用不同模型交叉验证的场景；研究多 Agent 系统编排（作者本人的 AI civilization 实验）的人。

**推荐理由**
- **切中的是「组织问题」而非「模型能力」**：它不提供模型，也不跟你比谁的提示词更好，而是解决「多个 Agent 怎么分工、上下文放哪、谁负责评审」——这是实际用多 Agent 时最先撞上的墙。
- **异构与可替换是设计前提**：Claude Code 与 Codex 同处一个 rig、按座位选 provider，避免了被单一厂商锁定；这一点会随模型迭代加速而越来越值钱。
- **对「会改你的机器」毫不遮掩**：明文列出写入路径与遥测字段，并建议先备份、说明权限策略的粒度——在一个动不动就写 hooks 与 trust 配置的时代，这种透明是加分项。
- **文档与发布运营到位**：v0.5.x 起有兼容性历史记录、Getting started 引导路径、topology naming 指南、Discussions 的 Q&A、YouTube 演示，以及 npm 正式发版与约定一天内响应 issue / PR。

> **注意**：① 安装与启动会**写入 provider hooks、workspace trust 设置、`~/.tmux.conf` 与技能目录**，务必先读 README 的「What OpenRig changes on your machine」并备份相关文件；② 环境要求偏硬：Node 22 / 24 + tmux，Windows 只能走 WSL2 且官方自动化测试尚未覆盖 WSL2；③ 官方给的「一句话安装」脚本会直接 `npm install -g` 并执行 `rig setup`，企业内使用建议先 `--dry-run` 或逐条执行，而不是直接管道进 sh；④ `workshop` 团队的「非中断模式」会绕过权限提示与 harness 警告弹窗，属高权限配置，需明确知情后再用；⑤ 项目仍在快速演进（v0.6.x），用于生产前建议锁定版本；⑥ 需要你**已有** Claude Code 或 Codex 账号——它只复用你的订阅，不自带模型。

> **一句话理解**：以前是「开五个终端窗口分别跟五个 AI 聊，上下文靠你自己记」；OpenRig 相当于给这五个 AI 发工牌、排座位、建了通讯录和任务看板，你只要找组长（lead）提需求。

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

- 候选池：Trending 日榜 8 条 + 周榜 12 条，去掉 6 个已在往期推送的仓库（`morluto/rea`、`boykopovar/AnyPS5`、`thedotmack/claude-mem`、`EpicGames/raddebugger`、`heygen-com/hyperframes`、`earthtojake/text-to-cad`）后，剩 14 条为新增候选。
- Search API 补充：本期用 GitHub Search API 按「建库时间 + star 门槛 + 30 天内有提交」拉细分领域候选（三组查询合计命中 106 / 770 / 145 条），另核实了 12 个高分候选的 License、最近提交与 README，其中 `robbietilton/Compositor`（应用项目）与 `NandhaKishorM/laya`（算法 / 模型）最终入选。
- 类目配额：应用项目 ×1、算法 / 模型 ×2、工程实践 / 工具链 ×1、AI Agent 及基础设施 ×1 —— 覆盖 4 个类目，单类目不超过 2 个。
- 本期入选协议：Apache-2.0 ×4、MIT ×1，全部为明确 License；5 个仓库都有完整 README 正文，且均具备正式 release（6–45 个不等）与文档站 / 文档目录 / notebook 中的至少一项。
- 去重检查：与往期四期（09-28 / 09-29 / 10-09 / 10-10，共 20 个仓库）均无重叠，基线为 `archive/index.json`。
- 数据口径：total stars、License、最近提交时间取自 GitHub 仓库页与 `commits.atom`；`airllm`（+548 日榜）、`tester-army/e2e`（+6,440 周榜）、`mvschwarz/openrig`（+2,028 周榜）的增量取自 Trending 原始数字；`Compositor` 与 `laya` 仅由 Search API 命中、没有榜单增量，其「周均增量」是**由「累计 star ÷ 建库天数」换算的估算值**（Compositor 建库 26 天 15.9k ≈ 4.3k/周；laya 建库 24 天 32.4k ≈ 9.4k/周），速览表中已标注「估算」。
- 质量信号说明：`laya` 有独立文档站、公开基准报告与 Hugging Face 模型卡；`airllm` 有 PyPI 发版与 Colab notebook；`e2e` 有文档站、npm 多包发版与 Discord；`openrig` 有 npm 发版、兼容性历史与 Discussions；`Compositor` 有 GitHub Releases、Homebrew cask 与已公证签名。
- 本期排除口径保持一致的几类：Agent 技能 / 提示词集合型仓库（`mattpocock/skills`、`cursor/plugins`、`danyuchn/asd-ste100-skill`、`cathrynlavery/diagram-design`）、资源聚合与清单型仓库（`avelino/awesome-go`、`eternity4719/HowToLiveBetter`）、以及 License 为 `NOASSERTION` / 无 License 的仓库（`bilawalsidhu/gods-eye-view`、`chrislgarry/Apollo-11`）。
- 与往期的口径差异说明：`mvschwarz/openrig` 在 10-10 那期因「单类目 ≤ 2」配额让位，本期 AI Agent 类目只有一个名额、且它仍活跃（周榜 +2,028、当日有提交），故本期正式入选。

**本期按规则排除的候选**

- `mattpocock/skills`（286.2k，周榜 +10,330）：Agent 技能集合型仓库，非具体项目，按既有口径排除。
- `cursor/plugins`（10.9k，周榜 +1,140）：插件集合的分发载体，且仓库页 License 显示为 `NOASSERTION`，双重不满足。
- `cathrynlavery/diagram-design`（50.4k，日榜 +1,083）：产出图表 HTML 的 Agent 技能 / 样式包，与 `mattpocock/skills` 同类，按「技能集合」口径排除。
- `danyuchn/asd-ste100-skill`（4.5k，周榜 +936）：单技能包，同类排除。
- `bilawalsidhu/gods-eye-view`（51.7k，日榜 +886）：各项通用指标均达标（3D 地球 / 地理情报可视化，当日有提交），但仓库页 License 为 `NOASSERTION`，不满足「License 明确」的硬门槛。
- `chrislgarry/Apollo-11`（74.3k，日榜 +466）：阿波罗制导计算机源码存档，仓库页 License 为 `NOASSERTION`（NASA 公开材料无标准开源协议），且最近提交为 2026-07-15、超出 30 天活性窗口，双重不满足。
- `storytold/artcraft`（18.0k，日榜 +2,957）与 `storytold/photocraft`（47.8k）：均为 Apache-2.0 且在活跃期，但与本期入选的 `robbietilton/Compositor` 同属「图像 / 媒体编辑器」方向，为避免同类重复，本期让位。
- `JuliusBrussee/caveman`（111.1k）：Apache-2.0、当日活跃、且被 Adobe Research 与 JetBrains 引用，指标全部达标；但产物形态偏「输出风格 / 提示层」优化，与已入选的 `tester-army/e2e`（真实测试框架）相比更偏策略类，本期作为备选、名额让给覆盖面更广的项目。
- `pytorch/pytorch`（104.5k，日榜 +315）、`flutter/flutter`（179.8k，周榜 +680）：热度与活性均达标，但属已被广泛使用的顶级基础设施，作为「每期 2–5 个的新发现」推荐价值有限（`pytorch` 的仓库页也未给出可识别的 SPDX License）。
- `ranxianglei/billion-context`（904，周榜 +337）：总 stars 904 < 1,000，未达存量门槛。
- `googleworkspace/cli`（31.4k）：最近提交为 2026-03-31，超出 30 天活性窗口，排除。

---

*本期由 WorkBuddy 每日 GitHub 精选任务自动生成 · 数据截至 2026-10-12 · 归档仓库：https://github.com/luyao-appleaccount/github-daily-archive*
