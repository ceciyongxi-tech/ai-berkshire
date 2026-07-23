# AI采纳与企业组织重构价值链：物理基础设施与模型期权

> **子课题范围**：①物理基础设施与供应链瓶颈；⑥基础模型和端侧模型高风险期权  
> **数据截止日**：2026-07-16（JST；研究启动时以 `date` 命令确认）  
> **口径**：仅纳入截止日前发布的信息；优先公司 IR、SEC、年报及官方技术文档。未上市公司与上市股票分列；不作估值或买入结论。  
> **证据等级**：A=审计财务/SEC/量产收入；B=公司季度披露、订单/付费席位或具名生产案例；C=公司新闻稿、规划、样品/试点；D=缺乏可核验商业数据。公司自述 ROI 均视为“供应商案例”，不是独立审计。

## 结论先行

1. **最像长期收费站的不是“所有算力”，而是少数难以绕开的系统级控制点**：先进制程与封装（TSMC）、HBM 量产与客户认证、GPU 软件生态（NVIDIA）、定制 XPU/交换芯片协同（Broadcom），以及电网到机架的供配电与热管理（Eaton/Vertiv）。这些环节已经出现收入、量产、订单或 backlog，而不只是发布会。
2. **当前最硬的商业验证依次是**：NVIDIA FY27 Q1 数据中心收入 752 亿美元、同比 +92%（计算 604 亿、网络 148 亿）；Broadcom FY26 Q2 AI 半导体收入 108 亿美元、同比 +143%；TSMC 2026Q1 收入 359 亿美元、毛利率 66.2%；Micron HBM4 对一个主客户高量出货；Vertiv 2026Q1 销售同比 +30%、有机 +23%；Eaton 电气业务订单/backlog 大增。相反，Rubin 的多项下一代云实例、MI450 首批 1GW、OpenAI/Broadcom Jalapeño、Apple 2027 系统特性、Qualcomm FY29 数据中心目标仍属未来部署或规划，不能当作当前收入。
3. **模型商品化并不等于模型公司没有价值，但意味着其收费权更脆弱**。Alphabet 披露 2025 年 Gemini serving unit cost 下降 78%；Microsoft Foundry 已提供逾 11,000 个模型；Apple 以统一 `LanguageModel` 协议允许 Apple、Claude、Gemini 和本地模型互换。这些是一手证据，说明价格/性能进步和路由层会削弱单一模型 API 的议价权。
4. **模型层更可能保留的控制点**是：全球消费入口与品牌、专有反馈/训练数据、推理规模效率、开发者工作流、强安全/合规信誉，以及深入客户流程的部署工程。但当模型通过 AWS/Azure/Google Cloud 或操作系统分发时，身份、权限、计费、数据驻留和审计往往由云/系统平台掌握；模型供应商可能成为高增长但高资本、可替换的“内容层”。
5. **上市公司中的基础模型敞口优先研究全栈分发者而非纯模型故事**：Alphabet、Microsoft、Amazon、Alibaba 已披露 AI 收入/付费席位/云 backlog 或芯片收入；Meta 的 Llama 仍无独立收入披露；Apple 的端侧控制点强，但截至截止日新一代框架多为预览/测试；Qualcomm 的 FY29 目标主要是前瞻指引。未上市 OpenAI、Anthropic 增长数据显著，但均为公司自报、未审计，且资本需求与云/芯片依赖极高，必须单列为高风险期权。

## 一、逻辑链与反证

```text
企业AI从聊天试用进入生产
  → token、推理并发、上下文长度与Agent执行次数上升
    → 每个有效任务需要更多内存带宽、互连、供电与散热
      → 先进制程/封装、HBM、网络、电力与热管理形成阶段性瓶颈
        → 只有能把“短缺”转成量产收入、长期合同或高转换成本者成为收费站

同时：模型能力扩散 + 推理单位成本下降 + 多模型路由
  → 单一模型更容易被替换
    → 收费权迁移到分发入口、企业数据/权限、工作流、审计和系统执行层
      → 基础模型/端侧模型保留高上行，但作为高风险期权而非确定性收费站
```

| 箭头 | 已发生验证 | 最强反面证据 | 判断 |
|---|---|---|---|
| AI需求→算力收入 | [NVIDIA FY27Q1](https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Announces-Financial-Results-for-First-Quarter-Fiscal-2027/default.aspx) 数据中心收入 752 亿美元、同比 +92%；[Broadcom FY26Q2](https://investors.broadcom.com/news-releases/news-release-details/broadcom-inc-announces-second-quarter-fiscal-year-2026-financial) AI 半导体收入 108 亿美元、同比 +143% | NVIDIA 明确 FY27Q2 指引不假设中国数据中心计算收入；大客户自研 ASIC 持续替代通用 GPU | 已验证，但客户集中与出口限制高 |
| 算力→制程/封装/HBM | [TSMC 2025 年报](https://investor.tsmc.com/static/annualReports/2025/english/index.html)显示 3nm 占晶圆收入 24%、先进节点占 74%，N2 已于 2025Q4 高量产；[Micron 2026Q3](https://investors.micron.com/news-releases/news-release-details/micron-technology-inc-reports-record-results-third-quarter)称 HBM4 已向主客户高量出货 | HBM4 对其他客户仍是 qualification samples；内存历史上强周期，新增产能会压低稀缺租 | 已验证到量产，但并非所有客户/代际均已量产 |
| 机架密度→电力/散热 | [Vertiv 2026Q1](https://investors.vertiv.com/news/news-details/2026/Vertiv-Reports-Strong-First-Quarter-with-Diluted-EPS-Growth-of-136-Adjusted-Diluted-EPS-Growth-of-83-Raises-Full-Year-Guidance/default.aspx)销售 +30%、有机 +23%；[Eaton 2026Q1](https://www.eaton.com/us/en-us/company/news-insights/news-releases/2026/eaton-reports-record-first-quarter-2026-results.html) Electrical Americas 订单滚动均值 +42%、backlog +44% | backlog 可延期/取消；项目建设周期长，客户可双源采购，设备制造并非软件式垄断 | 强验证，但收费权来自认证、交付与服务网络而非绝对垄断 |
| 模型能力→模型收费权 | [OpenAI](https://openai.com/index/next-phase-of-enterprise-ai/)称企业收入占比已逾 40%；[Anthropic](https://www.anthropic.com/news/series-h)称 2026-05 run-rate revenue 470 亿美元 | 两者均未上市且数据未审计；[Alphabet](https://abc.xyz/investor/events/event-details/2026/2025-Q4-Earnings-Call-2026-Dr_C033hS6/default.aspx)称 Gemini 单位服务成本一年下降 78%；多模型平台弱化锁定 | 高增长已发生，长期毛利/资本回报未验证 |
| 端侧模型→端侧收费权 | [Arm FY26Q4 call](https://investors.arm.com/static-files/78526857-5997-46eb-9b65-0d3249d83711)称 royalty revenue +11%，云 AI 是最大增量，Armv9/CSS 提升每设备 royalty；Apple 已有本地 Foundation Models API | [Apple 2026 文档](https://developer.apple.com/documentation/FoundationModels/)多项 PCC 能力仍标 Beta；[统一模型协议](https://developer.apple.com/videos/play/wwdc2026/339/)允许替换模型，模型未必占据租值 | 芯片架构/OS入口优于“端侧模型本身” |

## 二、①物理基础设施与供应链瓶颈

### 2.1 瓶颈排序

| 排名 | 环节 | 收费站强度 | 为什么模型商品化后仍保留控制点 | 主要失效方式 |
|---:|---|---|---|---|
| 1 | 先进制程 + 先进封装 | 很强 | 无论调用哪家模型，领先 XPU 均需高良率制程、CoWoS/3D 堆叠和长期协同；认证与 tape-out 周期长 | 地缘冲突；客户/政府扶持第二来源；资本密集导致回报下降 |
| 2 | HBM + 高带宽内存封装 | 强但周期性高 | Agent/长上下文增加内存容量与带宽，客户认证和热/良率管理难 | 三家寡头扩产、标准化及供需反转；客户自定义逻辑 die 改变价值分配 |
| 3 | GPU/XPU 计算平台与软件 | 强 | CUDA/库/集群管理/开发者生态带来切换成本；推理仍需大规模部署 | 定制 ASIC、开放软件栈、推理专用芯片及客户议价；中国市场限制 |
| 4 | 定制 ASIC + 交换/互连芯片 | 强 | XPU、SerDes、DSP、交换芯片和共同设计深度绑定 hyperscaler 路线图 | 客户集中、客户自有 tooling；Ethernet/UALink/NVLink 路线竞争 |
| 5 | 供配电、液冷和热管理 | 中强 | 上电许可、可靠性认证、安装服务和已装机维护不能被模型降价替代 | 制造扩产、模块标准化、项目延迟；大客户压价 |
| 6 | AI 网络系统/光互连 | 中强 | job completion time 依赖无损网络、遥测与 NOS，软件与已装网络存在切换成本 | 商用芯片依赖、白盒化、客户自研网络；光模块供给扩张 |
| 7 | AI 云/“neocloud” | 中低 | 可快速聚合 GPU、电力、调度软件与融资，短期稀缺时有价值 | 资产重、债务高、客户集中；hyperscaler 扩产后算力租金被压平 |

### 2.2 头部候选：证据、反证与状态

| 公司（代码/市场） | 当前商业验证：发布/试点/生产 | 商品化后保留控制点 | 每个看多结论的最强反证 | 证据/信息充分度 | 研究处置 |
|---|---|---|---|---|---|
| **TSMC 台积电**（2330 TW / TSM US） | **生产**：2026Q1 收入 359 亿美元、毛利率 66.2%、经营利润率 58.1%（[Q1 IR](https://investor.tsmc.com/english/quarterly-results/2026/q1)）；2025 年 N2 已于 Q4 高量产，3nm 占全年晶圆收入 24%（[年报](https://investor.tsmc.com/static/annualReports/2025/english/index.html)）。A16/N2P 计划 2026H2 量产，仍是未来节点。**截止说明**：Q2 正式财报在本研究启动时尚未发布，因此未使用。 | 领先制程、CoWoS/SoIC、良率、EDA/IP 生态与客户信任的组合 | 台海地缘为单点风险；海外 fab 成本更高；超大客户可能寻求第二来源 | **A** | **优先深挖**；是本层最接近中立收费站者 |
| **NVIDIA**（NVDA US） | **生产收入**：FY27Q1 总收入 816 亿美元，数据中心 752 亿美元、+92%；其中计算 604 亿、网络 148 亿，网络同比 +199%。**发布/未来**：多项 Rubin 云实例及下一代平台仍是宣布/预览；不可并入当前收入。[FY27Q1](https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Announces-Financial-Results-for-First-Quarter-Fiscal-2027/default.aspx) / [FY26 10-K](https://investor.nvidia.com/financial-info/sec-filings/sec-filings-details/default.aspx?FilingId=19184805) | CUDA、库、网络、整机 reference design、开发者生态 | hyperscaler 自研 TPU/Trainium；FY27Q2 指引不假设中国数据中心计算收入；技术迭代导致客户资本折旧；规模客户议价 | **A** | 优先深挖，但不能把 Rubin 宣布当产量 |
| **Broadcom**（AVGO US） | **生产收入**：FY26Q2 AI 半导体收入 108 亿美元、+143%。**合同**：与 Google 签长期 TPU/网络供应至 2031。[8-K](https://www.sec.gov/Archives/edgar/data/1730168/000119312526144028/d87999d8k.htm)。**未来**：OpenAI Jalapeño 仅 tape-out，计划 2026 年底初始部署。[公告](https://investors.broadcom.com/news-releases/news-release-details/openai-and-broadcom-unveil-llm-optimized-intelligence-processor) | 定制 ASIC 共同设计、SerDes/DSP/交换芯片及机架协同 | [10-Q](https://www.sec.gov/Archives/edgar/data/1730168/000173016826000016/avgo-20260201.htm)显示一个分销客户占季度收入 42%；客户可采用自有 tooling；AI rack backstop 最大风险敞口 290 亿美元（[后续 10-Q](https://www.sec.gov/Archives/edgar/data/1730168/000173016826000054/avgo-20260503.htm)） | **A** | **优先深挖**；同时把集中度与表外/担保风险列为核心问题 |
| **Micron**（MU US） | **生产**：2026Q3 HBM4 向主客户高量出货；其他多个客户仅送 qualification samples；HBM4E 预计 2027 量产。[Q3 结果](https://investors.micron.com/news-releases/news-release-details/micron-technology-inc-reports-record-results-third-quarter) | HBM 认证、DRAM 工艺、先进堆叠与客户定制 base die | 当前高量出货集中于一个 lead customer；内存价格/毛利极端周期；SK hynix/Samsung 竞争 | **A-** | 深挖供需与客户结构；不能把 samples 计为 production |
| **SK hynix**（000660 KS） | **生产+利润兑现**：公司 2026Q1 披露收入 52.58 万亿韩元、营业利润 37.61 万亿、营业利润率约 72%，称 HBM/服务器 DRAM/eSSD 拉动；HBM4 已进入 mass production（[Q1 公司结果](https://news.skhynix.com/q1-2026-business-results/) / [2026 更新](https://news.skhynix.com/computex-2026-review/)）。2025-09 的“readies mass production”只应视为量产准备。 | HBM 客户认证、MR-MUF 封装、热与良率 | HBM 收入仍未单列；72% 营业利润率明显包含供需周期，三星已开始 HBM4 mass product sales，美光也在高量出货 | **A-** | 优先候选，但必须做周期归一化和份额验证 |
| **Samsung Electronics**（005930 KS） | **生产**：2026Q1 DS 收入 81.7 万亿韩元、营业利润 53.7 万亿；公司称已开始面向 NVIDIA Vera Rubin 的 HBM4/SOCAMM2 mass product sales。[Q1 公司结果](https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2026-results) | DRAM+foundry+base die 垂直整合、HBM 量产与客户认证 | 集团业务高度多元，HBM 收入未单列；Foundry 同季盈利承压；高 ASP 与紧缺使当前利润不可线性外推 | **A-** | HBM 竞争反证与候选；主题纯度低于 SK hynix/Micron |
| **ASML**（ASML NL/US） | **生产**：2026Q1 销售 88 亿欧元、净利润 28 亿欧元；其中净系统销售 63 亿欧元、EUV 超 41 亿欧元。[Q1 结果](https://www.asml.com/en/news/press-releases/2026/q1-2026-financial-results) | EUV 光刻、光源/镜头/软件、installed base 服务 | AI 归因是间接的；订单可取消/延迟；对华出口限制；客户仅少数先进晶圆厂 | **A** | 优先候选但不是纯 AI；用全周期设备需求而非主题叙事验证 |
| **AMD**（AMD US） | **生产收入**：2026Q1 数据中心收入 57.75 亿美元、同比 +57%。**未来部署**：Meta 最多 6GW 计划中首个 1GW 才由 MI450 定制 GPU 驱动。[Q1 SEC slides](https://ir.amd.com/financial-information/sec-filings/content/0000002488-26-000072/amdq126earningsslidesfin.htm) | CPU+GPU+ROCm+机架级系统，开放生态的第二来源价值 | CUDA 软件差距；“最多 6GW”并非已实现收入；数据中心分部含 CPU，未披露纯 AI accelerator 收入 | **A-** | 候选；等待 MI450 实际交付和 ROCm 生产迁移证据 |
| **Amazon**（AMZN US） | **生产**：Trainium+Graviton 2025Q4 ARR 超 100 亿美元；2026Q1 芯片业务（含 Nitro）ARR 超 200 亿美元；Trainium2 承载 Bedrock 多数推理且 Bedrock 被逾 10 万家公司使用。[Q4](https://ir.aboutamazon.com/news-release/news-release-details/2026/Amazon-com-Announces-Fourth-Quarter-Results/default.aspx) / [Q1](https://ir.aboutamazon.com/news-release/news-release-details/2026/Amazon-com-Announces-First-Quarter-Results/) | 自研硅+AWS 分发+Bedrock 权限/计费/数据驻留 | 口径在 Q1 扩大到 Nitro，不可与前期直接比较；OpenAI 2GW 从 2027 才 ramp；芯片外部可比收入不透明 | **B+** | 全栈候选；需要拆分 AWS 芯片真实增量和资本回报 |
| **Vertiv**（VRT US） | **生产+订单**：2026Q1 销售 26.5 亿美元、+30%，有机 +23%，调整后经营利润率 20.8%；2025Q4 backlog 150 亿美元、同比 +109%。[Q1](https://investors.vertiv.com/news/news-details/2026/Vertiv-Reports-Strong-First-Quarter-with-Diluted-EPS-Growth-of-136-Adjusted-Diluted-EPS-Growth-of-83-Raises-Full-Year-Guidance/default.aspx) / [Q4](https://investors.vertiv.com/news/news-details/2026/Vertiv-Reports-Strong-Fourth-Quarter-with-Organic-Orders-Growth-of-252-and-Diluted-EPS-Growth-of-200-Adjusted-Diluted-EPS-37/) | 供电、热管理、液冷、服务与整站设计；已装机服务网络 | backlog 不等于收入且可能取消；大额固定价项目、产能扩张和客户集中会反噬毛利 | **A-** | **优先深挖**；验证 backlog 转化、预付款和客户集中 |
| **Eaton**（ETN US） | **生产+订单**：2026Q1 销售 75 亿美元、+17%；Electrical Americas 有机 +14%、订单滚动均值 +42%、backlog +44%；Electrical Global backlog +73%。[Q1](https://www.eaton.com/us/en-us/company/news-insights/news-releases/2026/eaton-reports-record-first-quarter-2026-results.html) | 电网到机架的认证、配电、开关设备、现场服务 | AI 收入未单列；并购 Boyd 后整合风险；电气设备仍有 Schneider/ABB/Siemens 等强竞争 | **A-** | **优先深挖**；较纯 AI 设备商更分散但收费点更耐久 |
| **Arista Networks**（ANET US） | **生产收入但 AI 未单列**：2026Q1 总收入 27.09 亿美元、+35.1%，GAAP 经营利润率 42.7%。XPO 和 1.6T 产品为新发布，不能据此认定收入。[Q1](https://investors.arista.com/Communications/Press-Releases-and-Events/Press-Release-Detail/2026/Arista-Networks-Inc--Reports-First-Quarter-2026-Financial-Results/default.aspx) | EOS/CloudVision、遥测、集群负载均衡与运维习惯 | 商用 silicon 依赖；大客户集中；白盒和 hyperscaler 自研；AI 收入不可归因 | **A-** | 候选；须取得 AI center 生产收入/客户扩张口径后再升档 |
| **CoreWeave**（CRWV US） | **生产+合同**：2026Q1 收入 20.78 亿美元、+112%；revenue backlog 994 亿美元；活跃电力超 1GW。[Q1 8-K](https://www.sec.gov/Archives/edgar/data/1769628/000176962826000220/coreweave1q26earningspress.htm) | GPU 集群调度、快速部署、融资和 AI 原生运维 | 同季经营亏损 1.44 亿、净亏损 7.40 亿；[10-Q](https://www.sec.gov/Archives/edgar/data/1769628/000176962826000222/crwv-20260331.htm)披露债务 251 亿美元、经营租赁负债 101 亿；backlog 需满足交付/可用性 | **A** | 高风险基础设施期权；不列确定性收费站 |

### 2.3 全球上市候选池（扩展扫描）

市值随时点波动且本子课题不作估值，故不以市值排序；“纯度”只表示本主题收入暴露，不表示股票优劣。

| 环节 | 上市候选（交易所/代码） | 主题纯度 | 信息充分度 | 快速处置/淘汰理由 |
|---|---|---:|---:|---|
| GPU/加速器 | NVIDIA (NASDAQ:NVDA)、AMD (NASDAQ:AMD) | 高 | A | Intel (NASDAQ:INTC) 暂不入前列：代工/CPU/重组混合，AI accelerator 生产收入缺乏同等级证明 |
| 定制 ASIC/互连芯片 | Broadcom (NASDAQ:AVGO)、Marvell (NASDAQ:MRVL)、Astera Labs (NASDAQ:ALAB)、Credo (NASDAQ:CRDO) | 中高 | A/B | Marvell FY26 数据中心收入逾 60 亿美元但 AI/非 AI 混合；Astera 新 Scorpio X 仅 initial shipments；小公司客户集中和路线切换风险高 |
| Foundry/封装 | TSMC (TWSE:2330/NYSE:TSM)、Samsung Electronics (KRX:005930)、ASE Technology (TWSE:3711/NYSE:ASX)、Amkor (NASDAQ:AMKR) | 中高/中 | A/B | Samsung 为手机、存储、foundry 混合体；ASE/Amkor 封测更分散，需验证先进封装利润而非只看数量 |
| HBM/存储 | SK hynix (KRX:000660)、Micron (NASDAQ:MU)、Samsung (KRX:005930) | 高/高/中 | A | 三家均已出现 HBM4 量产信号；但全组受内存周期约束，72%/80% 级阶段利润率不可外推为永续 |
| 半导体设备/测试 | ASML (NASDAQ:ASML)、Applied Materials (NASDAQ:AMAT)、Lam Research (NASDAQ:LRCX)、KLA (NASDAQ:KLAC)、Tokyo Electron (TSE:8035)、Advantest (TSE:6857)、DISCO (TSE:6146)、ASM International (AMS:ASM)、Besi (AMS:BESI) | 中 | A/B | AI 二阶受益；若无法拆出先进逻辑/DRAM/高性能测试增量，不列“纯 AI 收费站” |
| AI 网络 | Arista (NYSE:ANET)、Broadcom、Cisco (NASDAQ:CSCO)、Marvell、Credo、Astera、Coherent (NYSE:COHR)、Lumentum (NASDAQ:LITE)、Fabrinet (NYSE:FN) | 中高 | A/B | Cisco FY26Q3 累计 AI 基建订单 53 亿美元、全年订单目标 90 亿但收入目标约 40 亿，典型说明订单≠收入；光器件价格下降、CPO/铜互连切换和客户集中可能吞噬数量增长 |
| 电力/热管理 | Vertiv (NYSE:VRT)、Eaton (NYSE:ETN)、Schneider Electric (EPA:SU)、ABB (SWX:ABBN)、Delta Electronics (TWSE:2308)、Modine (NYSE:MOD)、Munters (STO:MTRS)、Legrand (EPA:LR)、nVent (NYSE:NVT)、Mitsubishi Electric (TSE:6503)、Fuji Electric (TSE:6504) | 中高 | A/B | 不淘汰；但多元化企业 AI 归因弱。Modine 的逾 40 亿美元 2027–29 capacity agreement 有 1.65 亿美元 upfront，仍是未来产能承诺而非当前收入 |
| 服务器/系统 | Dell (NYSE:DELL)、HPE (NYSE:HPE)、Super Micro (NASDAQ:SMCI)、Celestica (TSX/NYSE:CLS) | 中 | A/B | 组装/系统集成通常议价力弱；仅在液冷、机架设计、供应链速度形成差异时保留。HPE 2026Q2 AI backlog 63 亿美元，但 backlog 仍非收入（[IR slides](https://investors.hpe.com/~/media/Files/H/HP-Enterprise-IR/documents/q2-2026/q2-2026-earnings-presentation.pdf)） |
| 数据中心/AI 云 | CoreWeave (NASDAQ:CRWV)、Equinix (NASDAQ:EQIX)、Digital Realty (NYSE:DLR)、GDS (NASDAQ:GDS / HKEX:9698)、NEXTDC (ASX:NXT)、Keppel DC REIT (SGX:AJBU) | 中 | A/B | REIT/IDC 是电力与地产收费，不等于模型/Agent 收费；互联密度高的 EQIX 控制点强于纯批发容量；CoreWeave 因债务与客户风险只列期权 |

### 2.4 基础设施 ETF 穿透

| ETF | 穿透结果 | 主题纯度/重复持仓结论 | 处置 |
|---|---|---|---|
| **SMH** | [VanEck 2026-06-24 持仓](https://www.vaneck.com/us/en/investments/semiconductor-etf-smh?redirectVE=generic)：仅 26 只；NVDA 18.49%、TSM 9.08%、AVGO 5.66%、MU 5.46%、AMD 5.34%、INTC 5.14%，前六合计 **49.17%**（用项目 `financial_rigor.py calc` 精确求和） | 半导体纯度高，但不是“企业 Agent 收费站”纯度；与个股候选高度重复，且 Intel/TXN/ADI 等暴露并非纯 AI | 可作半导体篮子，不可替代数据/权限/工作流全链；与 NVDA/TSM/AVGO 个股同时持有会明显重复 |
| **SOXX** | [iShares 官方页](https://www.ishares.com/us/products/overview-v3-ishares-fund-data?portfolioId=239705&seoSlug=ishares-semiconductor-etf)说明追踪美国上市半导体指数，覆盖整个半导体价值链 | 同样是半导体周期篮子；不含电力散热、企业数据和治理层；与 SMH 高重叠 | 二选一即可；不应同时用 SMH、SOXX 再叠加相同头部个股 |
| **ARTY** | [iShares 官方页](https://www.ishares.com/us/products/297905/ishares-robotics-and-artificial-intelligence-etf-fund)为全球 AI 软件、基础设施与服务综合指数，50 只左右 | 名称“AI”但主题跨度大，混入软件/机器人/服务；对本研究六层的纯度低，需逐日持仓再判 | 在取得截止日完整 holdings 并计算层级权重前，不列优选替代 |

## 三、⑥基础模型和端侧模型：高风险期权

### 3.1 为什么只能称“高风险期权”

- **技术租值压缩已有公司级证据**：Alphabet 披露 2025 年 Gemini serving unit cost 下降 78%，意味着相同能力的推理成本快速下行；能力进步未必等比转成 API 毛利。
- **模型正被平台标准化和路由化**：Microsoft Foundry 提供逾 11,000 个模型；Apple 的 `LanguageModel` 协议让 Apple Foundation Model、Claude、Gemini、本地模型可在同一 API 下替换；AWS Bedrock 让采购、权限、治理、计费留在 AWS。
- **资本需求与收入同时爆发**：OpenAI/Anthropic 的自报 run-rate 很高，但也分别依赖 AWS/Azure/自建算力和巨额长期 compute commitments；未披露经审计毛利、自由现金流、客户留存或模型级 RPO。
- **“好模型”与“好股票”之间缺一座桥**：上市巨头可用广告、云、办公套件、设备生态交叉补贴模型；纯模型公司必须同时承担训练、推理、获客、部署工程和安全责任。

### 3.2 上市基础模型/端侧候选

| 公司 | 商业状态与可归因指标 | 商品化后可能保留的控制点 | 最强反面证据 | 充分度 | 研究处置 |
|---|---|---|---|---:|---|
| **Alphabet**（GOOGL/GOOG） | **生产/付费**：2025Q4 Cloud 收入 +48%至 177 亿美元、backlog 2,400 亿；生成式 AI 模型产品收入同比近 +400%，为“季度数十亿美元”级企业 AI 收入的一部分；Gemini Enterprise 800 万付费席位/2,800 家公司，12 万家企业使用 Gemini。[Q4 call](https://abc.xyz/investor/events/event-details/2026/2025-Q4-Earnings-Call-2026-Dr_C033hS6/default.aspx) | Search/Android/Chrome/Workspace/Cloud 分发，TPU，数据与全球服务规模 | 2026 CapEx 指引 1,750–1,850 亿美元；AI Mode 广告仍在早期测试；单位成本 -78%也说明模型层价格快速下压 | **A-** | 上市模型敞口首选深挖；价值更可能来自全栈而非 Gemini API 独占 |
| **Microsoft**（MSFT） | **生产/付费**：FY26Q3 AI business ARR 超 370 亿美元、+123%；M365 Copilot 逾 2,000 万付费席位；AI 业务包含多个产品，非纯模型收入。[Q3 call](https://www.microsoft.com/en-us/investor/events/fy-2026/earnings-fy-2026-q3)。FY26Q2 commercial RPO 6,250 亿美元，但约 45% 来自 OpenAI，不能全视作终端客户需求。[Q2 call](https://www.microsoft.com/en-us/investor/events/fy-2026/earnings-fy-2026-q2) | M365/Entra/Purview/GitHub/Azure 的身份、数据、权限、审计和分发 | OpenAI RPO 集中；AI 基建压低云毛利；客户可在 Foundry 多模型切换；微软自研模型尚未证明独立收入 | **A** | 更像平台收费站而非模型期权；基础模型敞口应折价看待 |
| **Amazon**（AMZN） | **生产**：Bedrock 被逾 10 万家公司使用，Trainium2 承载多数 Bedrock 推理；自研芯片 ARR 见上。[Q4 IR](https://ir.aboutamazon.com/news-release/news-release-details/2026/Amazon-com-Announces-Fourth-Quarter-Results/default.aspx) | AWS 的采购、权限、数据驻留、计费、芯片和模型市场 | Amazon 自有 Nova 模型没有独立收入披露；Anthropic/OpenAI 等模型可替代；资本开支巨大 | **B+** | 云/基础设施候选；不以“自有基础模型领先”作为核心论点 |
| **Alibaba**（BABA US / 9988 HK） | **生产/可归因**：FY26 March quarter Cloud 外部收入 +40%；AI-related products 连续 11 季三位数增长，占 Cloud 外部收入 30%，annualized AI-related revenue 358 亿元人民币；Model Studio 客户数同比 8 倍。[公司结果](https://www.alibabagroup.com/en-US/document-1991364841188622336) | Qwen 开源生态、阿里云、Model Studio、电商/支付/物流数据与中国市场分发 | “AI-related”含基础设施和应用，非 Qwen 模型收入；开源 Qwen 促进采用也可能削弱模型许可收费；中国竞争/监管/芯片限制 | **B+** | 中国全栈模型候选，需核对 IFRS 财报口径与外部客户留存 |
| **Baidu**（BIDU US / 9888 HK） | **生产收入**：2026Q1 AI Cloud Infra 收入 88 亿元人民币、+79%；GPU Cloud +184%。ERNIE 5.1 为 2026-05 发布，模型收入未单列。[Q1 results PDF](https://ir.baidu.com/node/14561/pdf) | 搜索入口、Apollo/地图、中文数据、云基础设施 | 口径是 AI Cloud Infra/GPU Cloud，不证明 ERNIE 模型租值；搜索份额与广告现金牛承压 | **B** | 观察；只有模型调用/续约/毛利拆分后才升档 |
| **Meta**（META） | **生产但间接变现**：2025 收入 2,009.66 亿美元、+22%，经营利润率 41%；无 Llama 独立收入。2025 CapEx 722.2 亿美元。[FY25](https://investor.atmeta.com/investor-news/press-release-details/2026/Meta-Reports-Fourth-Quarter-and-Full-Year-2025-Results/default.aspx) | 30 亿级社交分发、广告反馈数据、开源生态、眼镜入口 | 模型免费/开放削弱直接收费；AI 收入与 ROI 未拆；资本开支和人才成本先行 | **A-** | 作为广告/分发平台研究，不作为“模型 API 收费站”排名 |
| **Apple**（AAPL） | **现有生产+新一代预览**：2025 Foundation Models 已供开发者，Day One 等有具名应用；2026 新框架、Siri AI 和 PCC 大模型对应 2027 软件版，截止日仍有 Beta/未来发布成分。[2025 发布](https://www.apple.com/newsroom/2025/06/apple-supercharges-its-tools-and-technologies-for-developers/) / [2026 文档](https://developer.apple.com/documentation/FoundationModels/) | OS、Secure Enclave/Neural Engine、App Intents、设备分发、隐私与本地数据 | [2026 WWDC](https://developer.apple.com/videos/play/wwdc2026/339/)公开允许任意合规模型接入；小开发者 PCC 模型免费，模型不一定形成直接收入；新 Siri 尚未有生产 KPI | **B** | 端侧入口优先候选，但模型本身不作为独立收费站 |
| **Qualcomm**（QCOM） | **当前芯片收入混合；未来目标**：2026 Investor Day 将 FY29 非手机收入目标提至 400 亿美元，数据中心收入目标逾 150 亿；明确是 3–5 年目标，不是当前生产。[IR](https://investor.qualcomm.com/news-events/press-releases/news-details/2026/Qualcomm-Accelerates-Diversification-with-Comprehensive-Strategy-for-Data-Center-and-Sees-Multiple-Inflection-Points-Over-the-Next-3-to-5-Years/default.aspx) | 低功耗 NPU、modem/connectivity、OEM 关系、从边缘到云的编译软件 | 目标前瞻性强；手机周期与 Apple modem 替代；端侧模型跨芯片标准化；数据中心生态尚未验证 | **B-** | 高风险端侧/数据中心期权；等待实际设计量产收入 |
| **Arm**（ARM US） | **生产 royalty**：FY26Q4 royalty revenue 6.71 亿美元、+11%；云 AI 是最大增量，数据中心 royalty 超 2 倍，DPU/SmartNIC 接近 100% 份额（公司口径）；CSS 新授权已签，但首批 production chip sales 预计本财年 Q4。[call](https://investors.arm.com/static-files/78526857-5997-46eb-9b65-0d3249d83711) | ISA、软件兼容、CPU/CSS IP 与每设备 royalty | CSS production 收入仍未来；RISC-V；客户自研核；Arm 不拥有终端模型/工作流 | **A-** | 端侧与云 CPU 控制点候选，不是基础模型标的 |
| **MediaTek**（2454 TW） | Dimensity flagship SoC 已量产；但截至检索到的一手披露，未找到 2026 年可归因端侧 AI 收入/付费 KPI。2024 Dimensity 9400 ramp 推动季度收入 +6.5%（[IR](https://corp.mediatek.com/investor-relations/investor-relation-news/2024-q4-financial-results)） | Android OEM 规模、低功耗 SoC 集成、成本效率 | AI 功能可能只是换机规格而非新增收费；高端份额与 Qualcomm/Apple 竞争；缺乏 2026 归因数据 | **C+** | 保留观察；信息不足，不入前五深挖 |
| **SoftBank Group**（9984 JP） | 是 OpenAI/Arm/AI 基建组合敞口而非模型运营商。公司称截至 2026-03 已累计投资 OpenAI 346 亿美元，并另承诺 300 亿美元；[风险披露](https://group.softbank/en/ir/investors/management_policy/risk_factor) | 资本配置、Arm 与 OpenAI 的组合协同 | 少数股东影响力有限；以 400 亿美元 bridge facility 融资，OpenAI 盈利时点、诉讼、算力承诺均有风险 | **A** | 不列模型收费站；只作为高杠杆 NAV 期权研究 |

### 3.3 关键未上市公司：与上市股票严格分列

| 未上市公司 | 已验证商业信号 | 发布/试点/生产判定 | 最强反面证据 | 充分度/处置 |
|---|---|---|---|---|
| **OpenAI** | 公司称企业收入占总收入逾 40%，API 每分钟处理逾 150 亿 tokens；逾 100 万家企业采用产品/API。[企业更新](https://openai.com/index/next-phase-of-enterprise-ai/) / [部署公司公告](https://openai.com/index/openai-launches-the-deployment-company/)；LSEG 已组织级部署，产品发布周期由约 6 个月缩至约 2 周，客户请求到 production 约 4 周（[案例](https://openai.com/index/lseg/)） | LSEG 为**生产**；DeployCo 及收购 Tomoro 在 2026-05 仍属**宣布/待交割**；“100 万家采用”不能等同全部生产 | 未审计；未披露毛利/FCF/NRR/ACV；大量算力承诺；[AWS 上架](https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws/)虽拓宽分发，也把治理/计费留给 AWS | **B+**；未上市模型第一梯队，但必须以财务尽调而非宣传稿验证 |
| **Anthropic** | 公司称 2026-05 run-rate revenue 470 亿美元；PwC 列出 live production deployments，交付改善最高 70%，保险核保周期 10 周降至 10 天（[PwC 案例](https://www.anthropic.com/news/pwc-expanded-partnership)） | PwC 具名 **production**；新 enterprise AI services company 是**宣布/建设中**（[公告](https://www.anthropic.com/news/enterprise-ai-services-company)） | 收入/ROI 均公司自报、未审计；估值 9,650 亿美元、融资 650 亿美元显示高资本需求；依赖 AWS/Google/微软/NVIDIA 多方算力 | **B+**；与 OpenAI 并列单独跟踪，不与上市股票排序 |
| **xAI** | Grok 已进入部分云模型目录和 X/SpaceX 生态 | 多为产品发布/平台分发；本轮未找到截止日前经审计收入、ACV、RPO、NRR 或具名 ROI | 治理、关联交易、巨额算力、与 OpenAI/Anthropic/Google 快速竞赛；缺乏财务透明度 | **D**；高风险期权，不入深挖前五 |
| **Mistral AI** | 模型进入 Azure/AWS 等目录，具欧洲主权 AI 叙事 | 生产可用不等于公司商业规模已验证；本轮未找到一手可比收入/NRR | 开源策略和云分发压低模型租值；与大厂模型相比资本/分发弱 | **C-**；保留欧洲政策期权 |
| **Cohere** | CoreWeave 披露扩展 Cohere 关系，表明有持续算力消费（[CoreWeave Q1](https://www.sec.gov/Archives/edgar/data/1769628/000176962826000220/coreweave1q26earningspress.htm)） | 客户关系/工作负载存在，但没有可比财务与 ROI | 企业模型市场被 Microsoft/OpenAI/Anthropic/Google 夹击；分发依赖云伙伴 | **C-**；观察，不与上市公司排名 |
| **DeepSeek** | 开源模型被 Microsoft Foundry 等平台提供，技术扩散强 | 模型可用/下载不等于生产收入 | 开源和低价本身强化商品化；公司收入、治理、算力来源和客户续约不透明 | **D**；重要竞争反证，不是可投收费站 |
| **Moonshot AI / Zhipu AI / MiniMax** | 中国模型生态与企业/消费者采用候选 | 本轮没有取得同口径一手收入、ACV、RPO、续约/ROI | 竞争密集、价格战、监管与芯片供应；私有财务不透明 | **D**；留在未上市观察池 |

### 3.4 新闻、试点、生产环境的明确清单

| 事件 | 状态 | 为什么 |
|---|---|---|
| NVIDIA FY27Q1 数据中心收入、Broadcom FY26Q2 AI 收入 | **生产/已确认收入** | 财务结果已确认，而非客户意向 |
| TSMC N2 2025Q4 HVM、Micron 对 lead customer 的 HBM4 high-volume shipments | **量产** | 明确使用 HVM/high-volume shipments；Micron 对其他客户仍只是样品 |
| SK hynix 2025-09 “readies mass production” | **量产准备** | “准备好”不等同已交付；到 2026 公司更新才称 mass production |
| NVIDIA Rubin 首批云厂商、AMD/Meta 最多 6GW、OpenAI/Broadcom Jalapeño | **宣布/未来部署** | 使用 will/plan/expected，不能进入当前 AI 收入 |
| Vertiv/Eaton backlog/orders | **已签订单/需求验证，非收入** | 比发布会强，但仍有取消、延迟和执行风险 |
| OpenAI-LSEG、Anthropic-PwC live deployments | **生产案例** | 明确组织级部署/production，并有流程周期结果；但 ROI 是供应商案例 |
| OpenAI DeployCo、Anthropic enterprise services company | **公司成立/宣布** | 说明部署瓶颈真实，但不代表其规划收入已实现 |
| Apple 2026 Foundation Models/PCC/Siri AI | **开发者预览/Beta/未来系统发布** | 文档标 Beta，新系统对应后续软件版本，截止日无生产 KPI |
| Qualcomm FY29 150 亿美元数据中心收入目标 | **管理层目标** | 不是订单、backlog 或收入 |

## 四、淘汰理由与下一步深挖名单

### 4.1 本轮淘汰/降级

| 对象 | 淘汰或降级理由 |
|---|---|
| 把“所有 GPU 云/数据中心”视为收费站 | 资产重、融资重、客户集中；CoreWeave 的收入增长与巨额债务/租赁负债并存 |
| 服务器组装商作为核心收费站 | 机架组装和整合可有阶段性高需求，但长期议价权通常低于芯片、网络 NOS、供电和热管理；backlog 不能替代毛利/现金流验证 |
| Meta 作为“Llama 直接收费标的” | 无 Llama 独立收入、ACV、RPO 或续约；价值主要在广告与分发，而不是模型 API 收费 |
| Apple 作为“已完成端侧模型商业化” | 端侧入口强，但 2026 新功能多属预览/Beta，且统一协议主动支持第三方模型替换 |
| Qualcomm FY29 目标当作当前业绩 | 目标跨度 3–5 年；数据中心和 agent-driven edge upgrade 尚需量产收入证明 |
| xAI/Mistral/Cohere/DeepSeek 进入上市股票直接排名 | 私有财务、毛利、NRR、RPO 或审计信息不足；应单列期权 |
| SMH/SOXX/ARTY 作为“完整企业 AI 价值链”替代 | SMH/SOXX 几乎是半导体篮子；ARTY 跨软件、硬件、机器人，无法直接表达数据/权限/工作流收费站，且与个股重复 |

### 4.2 建议主报告下一步深挖的 5 家（仅研究优先级，不是买入结论）

1. **TSMC**：验证 CoWoS/SoIC 产能、定价、客户预付款、海外 fab 成本与台海尾部风险；核心问题是“技术与信任租值能否覆盖资本密集度”。
2. **Broadcom**：拆分 custom XPU 与 AI networking 收入/毛利，量化 Google/OpenAI 等客户集中和 290 亿美元 backstop 风险；核心问题是“共同设计锁定是否强于客户自研替代”。
3. **Vertiv**：按客户/产品拆 backlog、取消率、预付款、交付周期、液冷占比和售后服务；核心问题是“订单潮能否转成持续自由现金流”。
4. **Alphabet**：拆 Gemini/Vertex/TPU/Workspace 的 AI 可归因收入、付费席位扩张、Cloud backlog 转化及 serving cost 曲线；核心问题是“模型商品化后 Search+Cloud+Android 是否反而扩大控制点”。
5. **Arm**：拆云、手机、汽车 royalty，追踪 CSS production 芯片、每设备 royalty 与 RISC-V；核心问题是“端侧 AI 的租值最终归 ISA/CSS、芯片商、OS 还是模型”。

**备选第 6–8 名**：NVIDIA（软件生态与自研 ASIC 替代）、Eaton（配电 backlog 与 AI 归因）、Micron/SK hynix（HBM 供需和周期）。**OpenAI、Anthropic**另设未上市尽调轨道，不与上述 5 家上市公司排同一张榜。

## 五、研究空白与需主报告补证

- 多数公司不披露 AI 客户 ACV、净收入留存率或按模型划分的 RPO；“客户数/席位/token”不能替代 cohort expansion。
- Vertiv/Eaton/Arista/ASML 的 AI 收入归因仍不完整，需要管理层电话会或分部订单补充。
- OpenAI、Anthropic 的 revenue run-rate 与 ROI 来自公司材料，未取得审计报表；不能据此推算利润、现金流或估值安全边际。
- SK hynix、Samsung、MediaTek 等亚洲公司需再以交易所原始财报做一轮收入/利润桥交叉验证；本稿仅在有明确一手商业信号时引用。
- 本稿刻意不做 PE/PS/EV/EBITDA、目标价或买入结论。赛道逻辑成立不等于股票有安全边际，所有候选必须另过估值与资本回报审查。

> **免责声明**：本文件用于学习和研究，不构成投资建议。
