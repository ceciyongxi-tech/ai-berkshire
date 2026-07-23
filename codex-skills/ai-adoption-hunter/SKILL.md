---
name: ai-adoption-hunter
description: 持续追踪企业 AI 采纳与组织重构价值链，监测物理基础设施、数据与业务上下文、工作流与 Agent 编排、身份安全审计可观测性、非 AI 原生企业内部重构、基础模型与端侧模型六层的生产部署、商业化证据、控制点变化和反证。用于用户要求更新 AI adoption 链条、追踪收费站、扫描新信号、复核既有行业论文、更新主题观察池或判断哪些事件触发深挖时；不用于单纯解释短期股价异动或直接给出买入结论。
---

## Codex adapter note

This skill is generated from `skills/ai-adoption-hunter.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# AI Adoption Hunter：企业 AI 采纳链条猎手

对 $ARGUMENTS 执行企业 AI 采纳价值链的增量追踪。

核心问题不是“谁发布了 AI 产品”，而是：

> 企业是否把 AI 放进真实生产流程？谁掌握模型商品化后仍不可绕开的数据、权限、工作流、执行、审计或物理瓶颈？这些控制点是否已经产生可归因收入、扩张和客户 ROI？

本技能是持续追踪系统，不替代完整行业首研。基线报告优先读取：

`reports/AI采纳与企业组织重构-20260716/AI采纳与企业组织重构价值链研究报告-20260716.md`

如果该文件不存在，先用本技能建立精简基线，不假设其中的结论。

---

## 一、支持的运行模式

从 $ARGUMENTS 识别模式；信息足够时不要反问。

| 模式 | 示例 | 行为 |
|---|---|---|
| 增量更新（默认） | `更新`、空参数 | 从上次快照日期追踪到今天；无快照则从 2026-07-16 基线开始 |
| 全链扫描 | `full`、`全链扫描 90天` | 六层全部重扫，默认回溯 90 天，并重建赛道排序 |
| 单层扫描 | `数据与治理`、`layer 4` | 只更新指定层及其上下游影响 |
| 公司追踪 | `NOW CRM SNOW`、`追踪 Microsoft` | 更新公司证据卡，并映射到相关层 |
| 反证扫描 | `bear case`、`寻找证伪` | 优先寻找回滚、质量事故、免费捆绑、替代路线和单位经济恶化 |
| 观察池维护 | `watchlist`、`更新候选池` | 更新升级、降级、淘汰与待深挖名单 |

不要把它当作：

- 短期股价异动归因；使用 `news-pulse`。
- 单公司完整投研；使用 `investment-research` 或 `investment-team`。
- 财报逐行精读；使用 `earnings-review`。
- 买入后论文检查；使用 `thesis-tracker`。

---

## 二、启动与状态读取

### 2.1 确认日期

开始前必须运行 `date`，将实际日期作为“最新”数据基准，并在输出头部写明：

- 数据截止日
- 搜索窗口
- 上次快照日
- 运行模式

### 2.2 读取既有状态

按顺序读取存在的文件：

1. 基线行业报告。
2. `reports/ai-adoption-hunter/chain-map.md`。
3. `reports/ai-adoption-hunter/watchlist.md`。
4. `reports/ai-adoption-hunter/snapshots/` 中最近一份快照。
5. 与本次公司或层级直接相关的底稿。

不得把旧报告中的“最新”数字直接沿用为当前数字。旧报告只提供基线、候选池和证伪条件。

### 2.3 首次运行初始化

如果状态目录不存在，创建：

```text
reports/ai-adoption-hunter/
├── chain-map.md
├── watchlist.md
└── snapshots/
    └── YYYY-MM-DD.md
```

- `chain-map.md` 保存当前状态和简短变更日志。
- `watchlist.md` 保存公司/ETF 观察池及下次验证点。
- `snapshots/YYYY-MM-DD.md` 是不可变的当期证据快照；同日重跑时使用 `YYYY-MM-DD-HHMM.md`，不要覆盖已存在快照。

---

## 三、固定六层链条

必须分层，不得把所有 AI 公司混在一张榜中。

| 层 | 追踪对象 | 模型商品化后可能保留的控制点 | 关键商业指标 |
|---|---|---|---|
| 1. 物理基础设施与供应链瓶颈 | 制程、封装、HBM、GPU/XPU、网络、光互连、供电、散热、云容量 | 良率、认证、软件生态、交期、上电与散热能力 | AI 收入、订单、backlog、出货、ASP、毛利率、利用率、扩产周期、客户集中度 |
| 2. 数据、治理与业务上下文 | 数据云、数据库、语义层、ontology、主数据、ERP/CRM/ITSM 记录系统 | 数据重力、业务对象、权限继承、血缘、责任链 | AI ARR/ACV、RPO、NRR、计算消耗、生产账户、治理渗透、客户 ROI |
| 3. 工作流、Agent 编排与系统集成 | 工作流平台、Agent 控制塔、iPaaS、RPA、系统集成商 | 审批、任务路由、人机交接、跨系统写入、重试与回滚 | Agent ARR/ACV、work units、pilot→production 转化、续约扩张、实施周期、seat 与用量变化 |
| 4. 身份、安全、审计与可观测性 | 人/机器身份、PAM、DLP、AI gateway、SIEM、trace/eval、运行时拦截 | 最小权限、策略库、威胁数据、独立审计记录、事故责任 | Agent 专项 ARR/ACV、machine identity 数、观测用量、事故率、赢单率、留存与日志毛利 |
| 5. 率先组织重构的非 AI 原生企业 | 银行、零售、工业、物流、教育、专业服务等内部采纳者 | 专有数据、流程重做、渠道、规模和组织学习 | 收入/员工、利润率、周期、质量、市场份额、员工结构、客户满意度、返工/事故 |
| 6. 基础模型与端侧模型高风险期权 | 云端基础模型、开源模型、端侧模型、OS/NPU/设备入口 | 品牌、分发、专有反馈、推理效率、OS/设备入口 | 模型收入/ARR、企业生产客户、毛利/现金消耗、token 价格、切换率、资本承诺、端侧量产 |

种子候选池只用于防止漏检，不代表推荐：

- 层 1：TSMC、NVIDIA、Broadcom、SK hynix、Micron、ASML、Vertiv、Eaton、Arista、Marvell。
- 层 2–3：Microsoft、ServiceNow、Salesforce、SAP、Snowflake、Palantir、Oracle、UiPath、Pegasystems、Atlassian、Accenture。
- 层 4：Microsoft、Palo Alto Networks、CrowdStrike、Datadog、Okta、SailPoint、Zscaler、Dynatrace、Cloudflare。
- 层 5：JPMorgan、DBS、Klarna、Walmart、Duolingo，以及出现可量化内部重构的新公司。
- 层 6 上市：Alphabet、Microsoft、Amazon、Alibaba、Baidu、Meta、Apple、Qualcomm、Arm、MediaTek。
- 层 6 未上市：OpenAI、Anthropic、xAI、Mistral、Cohere、DeepSeek 及中国模型公司；必须独立列表，不与上市股票直接排名。

可增加、降级或删除候选，但必须记录证据与原因。

---

## 四、证据分级：发布不等于生产

每个事件必须同时标注“部署阶段”和“证据质量”。

### 4.1 部署阶段

| 阶段 | 定义 | 可证明 | 不可证明 |
|---|---|---|---|
| R：发布 | 产品、合作、路线图、未来目标 | 方向与产品意图 | 客户付费或生产稳定性 |
| P：试点 | POC、design partner、有限用户 | 场景初步可用 | 大规模部署、续约、利润 |
| D：生产 | 持续处理真实业务任务，有用户、交易或工作量 | 跨过生产门槛 | 一定盈利或广泛复制 |
| M：商业验证 | AI 专项收入/ACV/ARR、RPO/续约扩张或可复核 ROI | 价值开始被捕获 | 当前估值有安全边际 |

出现“客户正在使用”“采用率”“席位数”“合作伙伴”时，不得自行升级到 D 或 M。

### 4.2 证据质量

| 等级 | 来源 |
|---|---|
| A | 监管文件、审计财报、正式业绩材料、客户自己的正式披露 |
| B | 具名客户生产案例、付费合同、订单、官方技术文档与可复核工作量 |
| C | 厂商自报 ROI、管理层口述、单一案例、可靠媒体转述 |
| D | 匿名传言、产品营销、目标、缺少原始来源的二手材料 |

关键财务数据至少使用两个独立来源交叉验证；公司 IR 与同一公司新闻稿不算完全独立。找不到第二来源时保留，但显式标记单源和低置信度。

### 4.3 事件标准化

每条新增证据写成：

| 日期 | 层级 | 公司/控制点 | 事件 | 阶段 | 质量 | 指标变化 | 相对上次 | 最强反证 | 来源 |
|---|---|---|---|---|---|---|---|---|---|

“相对上次”只允许：`新信号`、`确认`、`加速`、`减速`、`回滚`、`证伪`、`噪音`。

---

## 五、采集方法

### 5.1 来源优先级

按以下顺序取证：

1. SEC、交易所、公司年报/季报、正式业绩演示。
2. 客户自己的年报、采购公告、案例或监管披露。
3. 官方产品文档、定价页、ETF 每日持仓。
4. 行业协会、监管机构、论文和可靠第三方数据库。
5. 高质量媒体与电话会文字稿。
6. 社交媒体和传言只作线索，不作核心结论。

搜索时同时使用公司名、产品名、指标和阶段词，例如：

- `Agent ARR ACV RPO production customer 2026`
- `AI pilot production deployment renewal expansion ROI`
- `machine identity agent security revenue observability`
- `revenue per employee AI cycle time margin case study`
- `ETF holdings official daily holdings`

### 5.2 并行扫描

全链扫描或候选超过 10 家时，如平台支持子 Agent，启动 3 个并行侦察任务；这是本技能明确要求的并行研究步骤：

1. `infra-model-scout`：层 1 + 层 6，负责产能、订单、模型商业化和私营公司。
2. `control-point-scout`：层 2 + 层 3 + 层 4，负责数据、工作流、身份、安全、审计、可观测性。
3. `adopter-etf-scout`：层 5 + ETF，负责内部组织 KPI、AI 归因和持仓穿透。

主 Agent 负责日期确认、旧状态读取、交叉验证、反证、评分、文件合并和审计。子 Agent 不得同时编辑同一个状态文件；让其写入临时底稿或仅返回结果。不支持子 Agent 时按相同分工串行执行。

单公司或单层小更新不强制并行。

---

## 六、各层强制验证

### 6.1 软件控制点

对层 2–4 的每家公司回答：

1. AI/Agent 收入是否单列？如果没有，明确写“未披露”，不得用平台总 ARR 冒充。
2. 有无 ACV、RPO、NRR、续约、扩张 bookings 或消耗量？
3. 客户是发布、试点还是生产？生产客户占比是否可知？
4. ROI 是客户披露、厂商案例还是独立研究？是否包含时间、成本和质量基线？
5. 如果模型明天免费，公司仍控制什么？
6. seat 减少、免费捆绑、开源或跨系统 Agent 是否削弱收费权？

### 6.2 内部采纳者

至少比较两个完整年度或四个季度，验证：

- 收入/员工。
- 毛利率、营业利润率或 cost-income ratio。
- 处理周期、自动化量、质量、CSAT、返工和事故。
- 市场份额或客户留存。
- 总员工、岗位结构、外包与裁员。

使用 `python3 tools/financial_rigor.py calc --expr '...'` 做精确计算。建立 AI 归因矩阵，逐项排除利率、涨价、并购、业务组合、广告/云增长、裁员、外包和周期因素。只有生产任务证据与经营指标同步改善时，AI 归因才能高于“中”。

### 6.3 物理基础设施

区分：样品、qualification、量产、出货、订单、backlog 与确认收入。必须检查：

- 供给集中度和扩产周期。
- 客户认证与替代路线。
- 订单转收入、取消条款与库存。
- 客户集中和自研 ASIC。
- 毛利率是否来自短缺租，扩产后是否均值回归。

### 6.4 基础模型和端侧模型

- 将 OpenAI、Anthropic 等未上市公司单列。
- 区分公司自报 annualized revenue、签约金额、确认收入和审计收入。
- 检查推理价格、服务成本、资本承诺、融资依赖和多模型切换。
- 端侧必须区分预览/Beta、设备量产、活跃使用和增量收入。
- 全栈公司的云、广告、办公或设备收入不得全部归因模型。

### 6.5 ETF

只使用截止日前官方持仓，至少穿透：

- 前十大及精确权重合计。
- 六层映射与主题纯度。
- 与用户现有主题暴露或其他 ETF 的同名证券重合。
- 即使证券名称不同，也要指出共同的半导体、存储、hyperscaler 等经济因子。
- 费率、持仓数量和集中度。

主题纯度是研究判断，必须说明口径；不得把基金名称当作纯度证据。

---

## 七、升级、降级与证伪规则

### 7.1 升级信号

满足任意一项可标记升级，但仍需反证：

- R/P → D：具名客户进入持续生产，有真实任务量。
- D → M：出现 AI 专项 ARR/ACV、续约扩张或客户可复核 ROI。
- AI 专项收入超过 $1B 或公司收入 10%，且口径未依赖并购拼接。
- NRR ≥120% 且 AI 付费生产账户、用量与毛利同步增长。
- 内部采纳者的收入/员工、周期和质量同时改善，且主要混杂因素可解释。
- 物理瓶颈订单转收入、毛利与交期同时验证，且扩产未追上需求。

### 7.2 降级或论文重审信号

出现任意一项必须在摘要中醒目标红：

- 生产部署回滚、重新大量引入人工，或发生质量/安全/监管事故。
- AI ARR/ACV 增速显著低于总体业务，或公司停止披露曾重点宣传的 AI 指标。
- seat 流失超过按动作/用量收入增量。
- RPO/NRR 明显减速，而 AI 使用量只增不收钱。
- Agent 安全、治理或观测被云/套件免费捆绑，独立赢单率和毛利下滑。
- backlog 取消、库存上升、客户自研替代或扩产导致瓶颈租快速下降。
- 基础模型价格快速下跌、客户多模型切换增加，而毛利和现金流未改善。
- 内部采纳者效率改善伴随 CSAT、质量、合规或市场份额恶化。

### 7.3 每个看多结论必须有反证

每个升级结论旁边必须写最强反面证据。找不到反证不是利好，而是研究不完整；继续搜索以下方向：

- 替代技术与开源。
- 免费捆绑与价格战。
- 并购和口径变化。
- 客户回滚或失败案例。
- 单位经济、资本强度和客户集中。
- 估值已提前反映。

---

## 八、链条评分与排序

评分用于追踪证据变化，不是股票评级，也不含估值。

| 维度 | 权重 | 评分问题 |
|---|---:|---|
| 生产证据 | 25 | 是发布、试点、生产还是商业验证？覆盖是否扩大？ |
| 可归因经济 | 25 | 有无 AI 专项收入、ACV、RPO、留存、ROI 和毛利？ |
| 控制点耐久性 | 20 | 模型免费/可替换后仍保留什么？迁移和责任成本多高？ |
| 采纳加速度 | 15 | 生产任务、付费账户、使用量和组织改造是否加速？ |
| 竞争与资本风险 | 15 | 捆绑、开源、扩产、客户集中、资本强度是否可控？ |

输出六层 0–100 分与相对上次的 `↑ / → / ↓`。任何层若“可归因经济”低于 10/25，总分封顶 75；纯发布/试点证据的赛道总分封顶 60。

赛道排名后另列公司研究优先级。不得把未上市公司与上市股票排在同一张可投资榜。

---

## 九、输出格式

### 9.1 本期快照

写入 `reports/ai-adoption-hunter/snapshots/YYYY-MM-DD.md`：

```markdown
# AI Adoption Hunter 快照

> 数据截止日：
> 搜索窗口：
> 上次快照：
> 运行模式：

## 1. 本期一句话判断
## 2. 六层记分牌与方向
## 3. 新增强信号
## 4. 回滚、证伪与最强反证
## 5. 发布 / 试点 / 生产 / 商业验证迁移表
## 6. 公司升级、降级与淘汰
## 7. 内部采纳者经营验证
## 8. 未上市模型公司单列
## 9. ETF 穿透变化（适用时）
## 10. 下一步深挖 5 家或 5 个验证任务
## 11. 数据缺口、低置信度与来源
## 12. 估值隔离声明
```

### 9.2 当前链条地图

更新 `chain-map.md`，保持精简：

| 层 | 当前得分 | 趋势 | 当前收费点 | 最硬商业证据 | 最强反证 | 下次验证 |
|---|---:|:---:|---|---|---|---|

文件末尾追加变更日志，不删除旧条目：

| 日期 | 层/公司 | 升级/降级 | 原因 | 快照链接 |
|---|---|---|---|---|

### 9.3 观察池

更新 `watchlist.md`：

| 层 | 公司/ETF | 市场 | 当前阶段 | 核心控制点 | 最新硬指标 | 最强反证 | 状态 | 下次触发器 |
|---|---|---|---|---|---|---|---|---|

状态只允许：`核心深挖`、`继续观察`、`证据不足`、`降级`、`淘汰`、`未上市单列`。

### 9.4 最终回答

向用户先给结论，再链接快照、链条地图和观察池。明确说明：

- 哪一层增强或减弱。
- 哪些公司从发布跨到生产或商业验证。
- 最大证伪是什么。
- 哪 5 个对象/问题值得下一步深挖。
- 本次是否触发完整行业报告、单公司研究、财报精读或论文重审。

---

## 十、验证与准出

1. 财务和权重计算使用 `python3 tools/financial_rigor.py ...`，不得心算关键估值或加总。
2. 对可发布快照运行：

   `python3 tools/report_audit.py extract --report <快照路径> --seed 42`

   填入抽样核验结果后再运行 `verdict`；有不通过项则修正并重跑。
3. 检查所有链接、数据截止日、相对上次变化和状态文件一致性。
4. 对低置信度、单一来源、口径变化和缺失指标显式标注。
5. 若本期没有硬证据变化，明确写“链条无可确认变化”，不要为了产出而升级赛道。

---

## 十一、投资边界

- 本技能输出的是证据与研究优先级，不是买入评级。
- 赛道逻辑增强不等于当前价格有安全边际。
- 准备进入投资结论前，必须另用单公司研究完成估值、资本回报、治理、下行情景和安全边际审查。
- 未上市公司的融资估值不得与上市公司的市值或可交易性直接比较。
- 本项目仅供学习和研究，不构成投资建议。
