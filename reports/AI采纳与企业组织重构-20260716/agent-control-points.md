# AI 采纳与企业组织重构：数据、工作流与安全控制点

> 研究范围：②数据、治理与业务上下文；③工作流、Agent 编排与系统集成；④身份、安全、审计与可观测性  
> 数据截止日：**2026-07-16**（已以系统 `date` 命令确认）  
> 定位：产业链与商业验证，**不构成买入结论**；任何公司都需另行通过估值与安全边际检验。

## 一、先说结论

### 1.1 三层赛道排序（仅按控制点质量，不含估值）

| 排名 | 层级 | 结论 | 生产验证 | 收费权来源 | 最强反面证据 |
|---|---|---|---|---|---|
| 1 | ③ 工作流、Agent 编排与系统集成 | **最接近当期收费站** | 强：ServiceNow、Salesforce、UiPath 已有 ACV/ARR、付费合同或生产客户 | 任务路由、人机交接、异常升级、跨系统写操作和消耗计费 | 巨头可把 Agent 编排换成套件功能；一般编排框架开源化，单独中间层容易被压价 |
| 2 | ② 数据、治理与业务上下文 | **最宽、最持久的控制点** | 中强：总体续约与 RPO 强，但 Snowflake/SAP/Palantir 多未拆 AI 单品收入 | 语义层、权限继承、数据血缘、主数据、业务对象和实时上下文 | 开放表格/目录格式、云厂商据库和客户多云策略削弱锁定；高增长可能仍来自传统数据仓库迁移 |
| 3 | ④ 身份、安全、审计与可观测性 | **必选但 AI 增量尚难分离** | 中：核心安全/可观测已生产，Agent 专属收入大多未披露 | 非人身份、最小权限、运行时拦截、全链路追踪、合规证据和故障闭环 | 可能由 Microsoft/Palo Alto/CrowdStrike 套件化并吞；开源 OpenTelemetry/开源 evals 压低单点可观测价值 |

**核心判断**：模型商品化之后，真正不容易被替换的不是“能调用哪个模型”，而是四件事：**谁可以看什么、数据在业务中意味什么、谁允许 Agent 做什么、出问题后谁能重放与追责**。

### 1.2 验证标签口径

- **[发布]**：产品发布、预览、GA 或合作公告；不代表客户已上生产。
- **[试点]**：POC、有限范围试用、“导入开始”或软目标；不视为经验证的收费站。
- **[生产]**：明确已在生产环境、有持续实际使用、付费合同/用量或已量化业务结果。
- “GA”只标为 **[发布]**，除非同一证据又显示客户生产使用。

## 二、逻辑链与幸存控制点

```text
模型能力上升、价格下降、多模型并存
  → 企业稀缺品从“智能”变成“可用的业务上下文”
    → 需要统一语义、数据血缘、权限和业务对象（②）
      → Agent 从回答问题进入跨系统执行
        → 需要确定性工作流、补偿交易、人工审批和写入接口（③）
          → 非人身份与高频机器操作激增
            → 需要最小权限、运行时防护、追踪、evals、成本/质量可观测（④）
```

| 模型商品化后仍存的控制点 | 为什么能收费 | 主要代表 |
|---|---|---|
| 业务对象/语义层 | 模型可换，但客户、订单、库存、风险之间的组织定义不能轻易重建 | Palantir Ontology、Salesforce Customer 360/Data 360、SAP Business Data Cloud、Microsoft Work IQ |
| 权限继承与主数据 | Agent 的答案和行动必须继承原系统权限 | Snowflake Horizon、Databricks Unity Catalog、Salesforce/Informatica、Microsoft Purview/Entra |
| 工作流与执行闭环 | “会说”不等于“可靠地完成工作”；需审批、重试、回滚与记录 | ServiceNow、Salesforce Agentforce、UiPath Maestro/robots、Microsoft Copilot Studio |
| 无代理接入老系统 | API 不全、主机/桌面/专有系统仍需执行层 | UiPath、ServiceNow IntegrationHub、大型系统集成商 |
| 身份和最小权限 | Agent 数量可远超员工，凭据生命周期和动态授权成为刚需 | Microsoft Entra/Agent 365、Okta、Palo Alto/CyberArk、CrowdStrike/SGNL |
| 独立观测、审计与运行时拦截 | 企业不能只信任 Agent 自报成功；需交叉模型/工具的独立记录 | Datadog、Dynatrace、Palo Alto/Chronosphere、CrowdStrike、Cloudflare |

## 三、商业证据：从发布到生产

### 3.1 ② 数据、治理与业务上下文

| 公司 | 验证标签与当期商业证据 | AI 可归因收入 / ACV / RPO / 扩张 | 客户 ROI/生产结果 | 看多逻辑 | 最强反面证据 | 信息 |
|---|---|---|---|---|---|---|
| **Palantir** (NASDAQ: PLTR) | **[生产]** Q1 2026 收入 16 亿美元，+85%；美国商业收入 5.95 亿美元，+133%；美国商业 TCV 11.8 亿美元 [S1][S2] | AIP 与 Foundry 捆绑，**AI 单品收入未披露**；总 RPO 44.5 亿美元，NDR 150% [S2] | **[生产]** Fortune 100 消费品客户统一至少 7 个 ERP，估算年节省最高 1 亿美元 [S3] | Ontology 将数据、逻辑、动作和权限映射成业务运营系统，且支持 BYOM，模型可换 [S4] | 政府收入仍占 53%；美国占收入 79%，地理/大客户集中；AIP 捆绑使 AI 真实价格和毛续约不透明 [S1] | **A** |
| **Salesforce** (NYSE: CRM) | **[生产]** Q1 FY27 Agentforce ARR 12 亿美元，+205%；Agentforce + Data 360 ARR 近 34 亿美元（含 11 亿美元 Informatica Cloud ARR）；已交付 38 亿个 Agentic Work Units [S5] | 这是样本中最清晰的 AI/Agent ARR 之一；>50% Agentforce + Data 360 bookings 来自既有客户，证明扩张；**AI 专项 RPO/ACV 未披露** [S5] | **[生产]** FY26 已披露生产账户数环比增长；官方客服场景曾显示案例量下降 7% [S6] | Customer 360 + Data 360 + Informatica 使 Agent 直接站在客户、销售、服务和元数据上；已有消耗计费单位 | 34 亿美元组合 ARR 含收购的 Informatica，不可把全部视为内生 AI；成交数不等于大规模生产，且数据层与应用层容易捕获套件锁定 | **A** |
| **Snowflake** (NYSE: SNOW) | **[生产/活跃使用]** Q1 FY27 产品收入 13.34 亿美元，+34%；Snowflake Intelligence 3 个月内被近 2,500 个账户使用 [S7] | 产品 NRR 126%，RPO 92.1 亿美元，+38%；**Cortex/Intelligence AI 收入、ACV 未单列** [S7][S8] | 未见同期可与 AI 单品价格匹配的公开 ROI；账户使用不等于付费生产 | 企业数据、跨云共享、权限与计算消耗是天然 Agent 上下文层；支持多模型降低模型绑定 | 高增长无法拆解为“AI 新增”和传统迁仓；开放格式、Databricks 和云厂商原生数据库同时压价 | **A** |
| **Databricks** (未上市) | **[生产]** 官方客户数超 20,000，超 60% Fortune 500；Unity Catalog/MLflow/Agent Framework 覆盖从数据到生产监控 [S9][S10] | **公司当期 ARR、AI 可归因收入、RPO、NDR 未按上市公司口径披露** | **[生产]** Snappt 一周建成客户分析，官方称留存提高 30% [S11] | 开源 Delta/MLflow + 统一目录贯通数据、模型、Agent 和评测，是强中立控制点 | 未上市且财务口径不对称；对云算力供应商存在成本依赖；客户 ROI 多为厂商案例 | **B** |
| **SAP** (Xetra/NYSE: SAP) | **[生产主张，数据不足]** Q1 2026 当期云 backlog 219 亿欧元，按固定汇率 +25%；云 ERP 收入 +30% [S12] | **Business AI/Joule 收入、ACV、RPO 增量未单列** | 管理层称 Business AI 已产生客户结果，但本期公开结果未提供可复核的统一 ROI | ERP 交易记录、业务语义和角色权限是极强上下文，模型很难绕过 | AI 货币化几乎不透明；客户的核心数据可通过 Snowflake/Databricks/云平台零拷贝旁路化 | **B** |
| **金蝶国际** (HKEX: 0268) | **[发布+生产核心 SaaS]** 2025 年订阅 ARR 约 40.9 亿元人民币，+19.2%；已发布近 20 个企业 AI Agent [S13] | **AI Agent 独立收入/ACV/RPO/NDR 未披露** | 未见可归因到 Agent 的统一客户 ROI | 中国本土财务、HR、供应链上下文和合规适配有区域壁垒 | 核心 ARR 可能主要是云 ERP，Agent 收入不明；国际化和产品平台生态弱于全球龙头 | **B** |

### 3.2 ③ 工作流、Agent 编排与系统集成

| 公司 | 验证标签与当期商业证据 | AI 可归因收入 / ACV / RPO / 扩张 | 客户 ROI/生产结果 | 看多逻辑 | 最强反面证据 | 信息 |
|---|---|---|---|---|---|---|
| **ServiceNow** (NYSE: NOW) | **[生产]** 2025 年末 Now Assist ACV 超 6 亿美元；Q1 2026 超 100 万美元 ACV 的 Now Assist 客户数 +130% [S14][S15] | 这是最清晰的 Agent ACV 证据之一；总 cRPO 126.4 亿美元，+22.5%，总 RPO 277 亿美元，+25%；**Now Assist RPO/NDR 未单列** [S15] | **[生产]** Kainos 知识文章 600 篇、平均解决时间下降 71%、客户满意度 99% [S16]；ServiceNow 内部 120 天实现 1,000 万美元年化效益、14% 自助分流提升 [S17] | 掌握 IT/HR/客服工单、审批、SLA 和跨部门交接；AI 改进可直接挂到 ACV | 流程越稳定，越可被 Microsoft/Salesforce/SAP 套件内 Agent 处理；内部 ROI 为自家案例，需独立客户复核 | **A** |
| **Salesforce** | **[生产]** Agentforce ARR 12 亿美元；38 亿 Agentic Work Units；几千万付费/成交指标见 3.1 [S5] | >50% 组合 bookings 来自扩张；Agentforce One/Apps 高级 SKU bookings +60% [S5] | **[生产]** 美国劳工部已将 Agentforce 部署到全国联络中心，但尚无量化 ROI [S18] | CRM 是销售/服务 Agent 的事件与写入层，Data 360 与 Slack 增加上下文 | 客户可用 Microsoft/ServiceNow/自建 Agent 调用 Salesforce API；消耗计费或造成预算不可预测 | **A** |
| **UiPath** (NYSE: PATH) | **[生产]** Q1 FY27 管理层明确称 agentic products 正从试点转入生产；总 ARR 19.01 亿美元，+12% [S19] | 总 NDR 109%，净新 ARR 4,900 万美元；**Agentic 收入/ACV/RPO 未单列** [S19] | **[生产]** Tetra Pak 客户引入与供应链从数天降到数小时，财税文档精度近 99%；保留 human-in-the-loop [S20] | RPA 机器人能进入没有良好 API 的桌面/旧系统，Maestro 可编排人、机器人和 Agent | NDR 109% 仍远低于高增长平台水平；浏览器使用、API 标准化和 OS 原生 Agent 可蚀食传统 RPA | **A** |
| **Microsoft** (NASDAQ: MSFT) | **[生产]** Q3 FY26 Microsoft 365 Copilot 付费席位超 2,000 万，+250%；近 90% Fortune 500 用低代码工具建有活跃 Agent [S21] | Copilot Credits 消耗环比近翻倍；**Copilot Studio/Agent 365 收入、ACV 和 RPO 未单列** [S21] | **[生产]** HSBC 用 Dynamics 365 预制 Agent 使问题解决时间下降 >30%；Accenture 超 74 万席 [S21] | Work IQ + M365/Dynamics/Power Platform 接入邮件、文档、会议、角色和业务应用，是最广泛的企业上下文 | 与 Azure/M365 捆绑使归因不清；高资本开支、推理成本和内部食用会压制经济性；不是纯度标的 | **A** |
| **Palantir** | **[生产]** AIP/Foundry/Apollo 支持生产 Agent、工作流、evals 与边缘部署 [S4][S22] | 见 3.1；AI 收入未分拆 | 见 3.1；生产 ROI 强，但不能全部归因于生成式 AI | Ontology 上的动作与权限是模型无法自己生成的运营层 | 实施服务重、价格不透明，客户也可用 Snowflake/Databricks + 云工作流自建 | **A** |
| **Celonis** (未上市，德国) | **[生产核心平台/发布 Agent]** 进程挖掘可为 Agent 提供真实流程图和瓶颈；官方引用客户 6 个月回本、383% ROI，但为厂商综合调查 [S23] | **ARR、ACV、RPO、NDR 未披露** | 有总体 ROI，但 Agent 单品的生产贡献未分离 | Process Intelligence 提供“工作实际如何发生”的上下文，对跨 ERP Agent 很有价值 | 未上市、财务透明度低；SAP Signavio、ServiceNow、Microsoft 与顾问公司都可竞争 | **C** |

### 3.3 ④ 身份、安全、审计与可观测性

| 公司 | 验证标签与当期商业证据 | AI 可归因收入 / ACV / RPO / 扩张 | 客户 ROI/生产结果 | 看多逻辑 | 最强反面证据 | 信息 |
|---|---|---|---|---|---|---|
| **Palo Alto Networks** (NASDAQ: PANW) | **[生产核心安全/发布 AI 安全]** Q3 FY26 NGS ARR 81 亿美元，+60%，其中收购的 CyberArk + Chronosphere 贡献 16 亿美元；RPO 184 亿美元 [S24] | **AI 安全/Agent 安全收入未分拆**；剔除并购后的有机 NGS ARR 约 65 亿美元，+28% [S25] | 未见当期 Agent 安全独立 ROI；核心安全已生产不等于新产品已规模生产 | 网络+云+SOC+身份+可观测+最新 Portkey AI gateway 构成跨层控制面 | 60% 增长被并购显著放大；收购整合、高额商誉和套件重叠是实质风险 | **A** |
| **CrowdStrike** (NASDAQ: CRWD) | **[生产核心安全/发布 AI 安全]** Q1 FY27 ARR 55.1 亿美元，+24%；净新 ARR 2.56 亿美元，+32%；多模组渗透继续上升 [S26] | **AI Detection & Response/Agentic MDR/AI agent security 收入、ACV、RPO 未单列** | 官方引用第三方 TEI：替换旧端点安全 ROI 273%，但非 Agent 安全独立 ROI [S27] | 端点是 Agent 实际执行、凭据使用和数据泄漏的一线执法点；收购 SGNL 扩展动态身份 | 2024 全球事故是最强反例：单一安全控制面也能成为系统性故障源；AI 增量无法从平台增长中分离 | **A** |
| **Datadog** (NASDAQ: DDOG) | **[生产]** Q1 2026 收入 10.06 亿美元，+32%；超 10 万美元 ARR 客户 4,550，+21% [S28] | 总体 NRR 为 low-120s；**Agent/LLM Observability 收入、ACV、RPO 未披露** [S29] | **[生产]** Baz 每日处理约 100 万次 LLM 操作，上线 <2 天，根因洞察提速约 80% [S30] | 已有 APM/logs/infra 数据，能把 Agent trace 与真实运行时故障、成本和安全相关联 | OpenTelemetry 与 Langfuse/Arize/Phoenix 等开源/专用系统降低迁移成本；大客户费用可出现优化/压缩 | **A** |
| **Okta** (NASDAQ: OKTA) | **[发布；核心 IAM 生产]** Okta for AI Agents 于 2026-04-30 GA；Q1 FY27 RPO 47.19 亿美元，+16%，cRPO 24.99 亿美元，+12% [S31][S32] | **AI Agent 身份收入、ACV、客户数和 NDR 未披露** | 尚无可复核的 Agent 身份生产 ROI；不应把 GA 当成生产验证 | 中立身份层可跨云/跨应用管理人、服务账户与 Agent，理论上是关键税口 | Microsoft Entra 捆绑优势强；公司增长仅约 11%，AI Agent 产品仍在商业化起点 | **A** |
| **Dynatrace** (NYSE: DT) | **[生产核心可观测/发布 Agent]** FY26 ARR 20.54 亿美元，按固定汇率 +16% [S33] | **Agentic observability 收入/ACV/RPO/NDR 未单列** | 未见当期 Agent 单品可归因 ROI | Davis 因果图与全栈上下文适合作为确定性运营引擎 | 增长低于 Datadog；产品转向消耗模式与旧 APM 客户迁移存在执行风险 | **A** |
| **Cloudflare** (NYSE: NET) | **[生产核心边缘/发布 Agent]** Q1 2026 收入 6.398 亿美元，+34%，cRPO +34% [S34] | **Workers AI/Agents/AI security 收入、ACV、NDR 未分拆** | 未见当期 Agent 安全单品 ROI | 边缘网络可观察和限制 Agent 的 API/网络访问，也可运行 Agent 工作负载 | 公司将 AI 贡献与核心 CDN/安全混在一起；Q1 宣布减员约 1,100 人，组织重构效果尚需续验 [S34] | **A** |
| **HENNGE** (TSE Growth: 4475) | **[生产核心 IAM/发布 AI 接口]** HENNGE One 签约用户超 300 万、客户 3,731 家，覆盖约 20% 东证上市公司；2026-07-15 首个原生 MCP 接口才发布 [S35][S36] | 公司有核心 ARR 目标，但**Agent 可归因 ARR/ACV 未披露** | 日本企业 IAM/DLP 为生产，Agent 仍只能标记为发布 | 日本本地渠道、邮件安全与合规支持有区域壁垒 | AI 相关商业证据几乎为零，且与 Microsoft/Okta 直接竞争 | **B** |

## 四、全球候选池与主题纯度

> 纯度不等于质量：Microsoft 纯度低但控制面强；小型纯 Agent 公司纯度高，但可能没有分发、数据或续约壁垒。

| 地区 | 候选（代码/状态） | 所属层 | 主题纯度 | 信息 | 当前处置 |
|---|---|---|---|---|---|
| 美国 | Palantir (PLTR) | ②③④ | 高 | A | 核心深挖；需分离 AIP 与旧 Foundry/政府增长 |
| 美国 | Salesforce (CRM) | ②③④ | 中高 | A | 核心深挖；需剔除 Informatica 并购对 ARR 的影响 |
| 美国 | ServiceNow (NOW) | ③④ | 高 | A | 核心深挖；需复核外部客户的真实年化 ROI |
| 美国 | Snowflake (SNOW) | ②④ | 高 | A | 核心深挖；需追踪 AI 功能付费渗透和单位经济 |
| 美国 | Microsoft (MSFT) | ②③④ | 低（高度多元） | A | 战略对照组，非纯度标的 |
| 美国 | UiPath (PATH) | ③ | 高 | A | 保留；需观察 NDR 能否随 Agent 上生产明显上行 |
| 美国 | Datadog (DDOG) | ④ | 高 | A | 核心深挖；需拿到 LLM/Agent Observability 付费贡献 |
| 美国 | CrowdStrike (CRWD) | ④ | 高 | A | 保留；需分离 AI 安全与平台整合增长 |
| 美国 | Palo Alto Networks (PANW) | ④ | 高 | A | 保留；并购后口径需重建，不可直接用 60% ARR 增长 |
| 美国 | Okta (OKTA) | ④ | 高 | A | 观察；AI Agent 身份尚未通过生产/收入门槛 |
| 美国 | Cloudflare (NET) | ③④ | 中 | A | 观察；需分拆 Workers/AI Gateway/AI Security 商业指标 |
| 美国 | Dynatrace (DT)、Elastic (ESTC)、Confluent (CFLT)、MongoDB (MDB) | ②/④ | 中高 | B | 二线保留；AI 单品收入不透明，控制点面临开源/云厂商竞争 |
| 欧洲 | SAP (SAP)、UiPath (PATH，美国上市/罗马尼亚起源) | ②③ | 中/高 | A | 保留 |
| 欧洲 | Celonis、Collibra、Dataiku、Mistral AI（均未上市） | ②③④ | 高 | C | 单列未上市候选，不与上市股票排名 |
| 日本 | HENNGE (4475)、Trend Micro (4704) | ④ | 高 | B | 区域观察；Agent 收入未验证 |
| 日本 | PKSHA (3993)、Cybozu (4776) | ③ | 中高 | B/C | PKSHA 称超 7,000 个 Agent 运行，但 AI Agent ARR/ACV 未披露 [S37]；仅观察 |
| 日本 | NTT DATA Group (9613)、Fujitsu (6702)、NEC (6701)、SCSK (9719) | ②③④ | 低（系统集成/多元） | B | Tier 4；可受益于实施需求，但不是可扩展软件税口的纯度标的 |
| 中国/香港 | 金蝶国际 (0268.HK)、用友网络 (600588.SH) | ②③ | 高 | B | 金蝶保留；用友已发布 BIP 5 多 Agent，但 2025 年报尚无 AI 收入分拆 [S38] |
| 中国/香港 | 阿里巴巴 (9988.HK/BABA)、腾讯 (0700.HK) | ②③④ | 低（高度多元） | A | 作为云+协作平台对照；不作为主题纯度标的 |
| 中国 | 奇安信 (688561.SH)、深信服 (300454.SZ)、启明星辰 (002439.SZ) | ④ | 中高 | C | 信息不足；未找到截止日可复核的 Agent 安全收入/扩张数据，暂不进入深挖组 |

## 五、未上市公司单列

| 公司 | 价值链位置 | 已验证 | 未验证/不可与上市股直接排名的原因 |
|---|---|---|---|
| Databricks | 数据、目录、ML/Agent 生命周期 | 超 20,000 客户，多个生产案例 [S9] | 无公开公司等级 RPO/NDR/AI 收入披露，估值和股权结构口径不对称 |
| Celonis | 进程语义与工作流改进 | 核心进程挖掘为生产，有综合 ROI 调查 [S23] | Agent 收入和续约未披露，官方案例存在选择性披露 |
| Collibra / Alation | 数据目录、血缘和治理 | 已有成熟企业客户 | 无同口径财务数据；目录功能正被 Snowflake/Databricks/云套件捆绑 |
| Workato / Glean | 集成编排 / 企业搜索与上下文 | 客户需求成立 | ARR、RPO、NDR 与 Agent 生产占比不足；面临 Microsoft/ServiceNow/Salesforce 分发层捆绑 |
| Anthropic / OpenAI | 基础模型和 Agent SDK | 产品使用与企业合作强 | 属用户要求的“基础模型高风险期权”，本文不与数据/权限/工作流上市控制点混排 |

## 六、明确淘汰与降级理由

| 标的/类别 | 处置 | 原因 |
|---|---|---|
| 把“已发布 Agent”当成“已大规模生产” | **淘汰该论证** | Okta for AI Agents、HENNGE MCP、部分 SAP/Joule 和中日 Agent 发布缺少付费、生产用量与 ROI |
| 把安全/数据平台总 ARR 当作 AI ARR | **淘汰该论证** | CrowdStrike、PANW、Datadog、Okta、Snowflake 都未提供足够的 AI 收入拆分 |
| Informatica (INFA) | **移出独立候选** | 已并入 Salesforce；其 11 亿美元 Cloud ARR 只可作为 Salesforce 组合指标，不可作为独立股票 |
| CyberArk / Chronosphere | **移出独立候选** | 截止日已并入 Palo Alto Networks，已无独立上市经济暴露 [S24] |
| Splunk | **移出独立候选** | 已并入 Cisco；可作为产品竞争者，不是独立股票 |
| Darktrace | **移出上市候选** | 被 Thoma Bravo 私有化；归入未上市安全竞争集 |
| 通用 Agent 编排初创 | **暂不深挖** | LangGraph/AutoGen/云平台 SDK 将“编排图”快速商品化；若没有业务系统写权、分发和合规记录，难成收费站 |
| NTT DATA/Fujitsu/NEC/SCSK 等 SI | **Tier 4** | 项目收入可受益，但人力密集实施很难获得软件级边际毛利和网络效应 |
| 用友、PKSHA、HENNGE、金蝶的 Agent 叙事 | **保留地区候选，不进入全球 Top 5** | 核心 SaaS/安全收入可验证，但 Agent 可归因 ARR、ACV、RPO、NDR 和外部 ROI 不足 |

## 七、本组三层最值得下一步深挖的 5 家

> 这是研究优先级，不是股票推荐或买入排名。

| 顺序 | 公司 | 为什么值得深挖 | 下一步必须拿到的证据 | 否决条件 |
|---|---|---|---|---|
| 1 | **ServiceNow** | Now Assist 已有 >6 亿美元 ACV、大 ACV 客户高增长、外部生产 ROI；工作流是 Agent 产生经济价值的直接层 | Now Assist 毛续约、净扩张、用量计费毛利；前 20 大客户从试点到全企业的时间 | Now Assist ACV 增长明显降速，或超过一半生产客户不能在 12–18 个月证明 ROI |
| 2 | **Salesforce** | 已披露 Agentforce 12 亿美元 ARR、扩张 bookings 和真实 Agentic Work Units，数据+工作流+消耗计费闭环最完整 | 剔除 Informatica 后的内生 Agentforce/Data 360 增长；每 AWU 价格、推理成本和毛利；付费到生产转化率 | ARR 高增长主要由捆绑/并购造成，而生产账户、AWU/账户或续约不同步 |
| 3 | **Palantir** | Ontology + AIP + Apollo 是最完整的“数据到行动”操作系统候选，商业收入、TCV、RPO、NDR 均强 | AIP 新客户和旧 Foundry 扩容的分拆；bootcamp → 付费生产的 cohort；客户集中和实施成本 | 美国商业高增长主要来自少数大合同，或 NDR 随高基数快速回落 |
| 4 | **Snowflake** | 中立数据、治理、跨云与多模型位置强；RPO +38%、NRR 126% 证明客户扩张 | Cortex/Intelligence 付费账户、收入和推理毛利；AI workload 对核心计算消耗的净增量 | 2,500 账户使用不能转化为增量消耗，或多模型/开放格式使客户绕过高价原生 AI |
| 5 | **Datadog** | Agent 上生产后，跨模型、跨工具、跨基础设施的独立可观测层是稀缺品；已有大量生产 telemetry 和可量化客户案例 | Agent Observability ARR/ACV、付费渗透、每百万 trace 毛利；与开源栈的胜率 | LLM/Agent 观测长期只是 APM 附加功能，或客户因成本将高频 trace 采样/自建 |

**安全层备选**：CrowdStrike 和 Palo Alto Networks 均值得专题深挖，但前者的 AI 安全增量未分拆，后者的当期 ARR 又被 CyberArk/Chronosphere 并购显著扭曲，因此本轮未挤入前 5。

## 八、关键来源（全部为原始/公司官方来源）

- **[S1] Palantir Q1 2026 Form 10-Q**: https://www.sec.gov/Archives/edgar/data/1321655/000132165526000028/pltr-20260331.htm
- **[S2] Palantir Q1 2026 Business Update**: https://investors.palantir.com/files/Palantir%20-%20Q1%202026%20Business%20Update.pdf
- **[S3] Palantir customer use case, Fortune 100 consumer goods**: https://www.palantir.com/docs/foundry/use-case-examples/optimizing-production-with-erp-data-across-the-supply-chain
- **[S4] Palantir AIP overview / BYOM**: https://www.palantir.com/docs/foundry/aip ; https://www.palantir.com/docs/foundry/aip/bring-your-own-model
- **[S5] Salesforce Q1 FY27 results**: https://investor.salesforce.com/news/news-details/2026/Salesforce-Delivers-Record-First-Quarter-Fiscal-2027-Results/default.aspx
- **[S6] Salesforce Q1 FY26 results / internal production result**: https://investor.salesforce.com/news/news-details/2025/Salesforce-Reports-Record-First-Quarter-Fiscal-2026-Results/default.aspx
- **[S7] Snowflake Q1 FY27 results**: https://investors.snowflake.com/financials/quarterly-results/default.aspx
- **[S8] Snowflake Q1 FY27 Form 10-Q**: https://www.sec.gov/Archives/edgar/data/1640147/000164014726000030/snow-20260430.htm
- **[S9] Databricks official platform/customer count**: https://www.databricks.com/
- **[S10] Databricks production ML documentation**: https://docs.databricks.com/en/machine-learning/index.html
- **[S11] Databricks/Snappt production customer story**: https://community.databricks.com/t5/announcements/customer-story-how-databricks-powered-snappt-s-real-time-fraud/td-p/144747
- **[S12] SAP Q1 2026 results**: https://news.sap.com/2026/04/sap-announces-q1-2026-results/
- **[S13] Kingdee FY2025 results**: https://www.kingdee.com/global/2026/03/23/kingdee-international-announces-fy2025-annual-results-cloud-subscription-revenue-increased-by-20-9-adjusted-net-profit-reached-rmb232-million/
- **[S14] ServiceNow 2025 annual-report filing (Now Assist ACV)**: https://www.sec.gov/Archives/edgar/data/1373715/000137371526000039/now-20260406.htm
- **[S15] ServiceNow Q1 2026 results**: https://investor.servicenow.com/news/news-details/2026/ServiceNow-Reports-First-Quarter-2026-Financial-Results/default.aspx
- **[S16] ServiceNow/Kainos customer story**: https://www.servicenow.com/customers/kainos-now-assist.html
- **[S17] ServiceNow internal production story**: https://www.servicenow.com/customers/now-on-now-now-assist.html
- **[S18] Salesforce/U.S. Department of Labor production deployment**: https://investor.salesforce.com/news/news-details/2026/U-S--Department-of-Labor-Taps-Agentforce-to-Enhance-Citizen-Support/default.aspx
- **[S19] UiPath Q1 FY27 results / Form 8-K exhibit**: https://ir.uipath.com/financials/sec-filings/content/0001734722-26-000037/path-2026430xex991.htm
- **[S20] UiPath/Tetra Pak production customer story**: https://www.uipath.com/resources/automation-case-studies/tetra-pak-cuts-process-time-with-agentic-ai
- **[S21] Microsoft FY26 Q3 earnings call**: https://www.microsoft.com/en-us/investor/events/fy-2026/earnings-fy-2026-q3
- **[S22] Palantir integrated AIP/Foundry/Apollo architecture**: https://www.palantir.com/docs/foundry/architecture-center/platforms
- **[S23] Celonis official newsroom / customer ROI item**: https://www.celonis.com/news
- **[S24] Palo Alto Networks Q3 FY26 results**: https://investors.paloaltonetworks.com/news-releases/news-release-details/palo-alto-networks-reports-fiscal-third-quarter-2026-financial
- **[S25] Palo Alto Networks Q3 FY26 earnings transcript**: https://investors.paloaltonetworks.com/static-files/ea18c9ae-cbe6-4b5d-aa7c-65a6b9aeb2e2
- **[S26] CrowdStrike Q1 FY27 results**: https://ir.crowdstrike.com/news-releases/news-release-details/crowdstrike-reports-first-quarter-fiscal-year-2027-financial
- **[S27] CrowdStrike FY26 results / TEI reference**: https://ir.crowdstrike.com/news-releases/news-release-details/crowdstrike-reports-fourth-quarter-and-fiscal-year-2026
- **[S28] Datadog Q1 2026 results**: https://investors.datadoghq.com/news-releases/news-release-details/datadog-announces-first-quarter-2026-financial-results/
- **[S29] Datadog May 2026 investor presentation**: https://investors.datadoghq.com/static-files/986ca4cd-9507-4c9d-b56f-4bae59d3dd47
- **[S30] Datadog/Baz production case study**: https://www.datadoghq.com/case-studies/baz/
- **[S31] Okta for AI Agents release**: https://investor.okta.com/news-and-events/news-releases/news-details/2026/Okta-Announces-New-Blueprint-for-the-Secure-Agentic-Enterprise/default.aspx
- **[S32] Okta Q1 FY27 results**: https://investor.okta.com/financials/quarterly-results/default.aspx
- **[S33] Dynatrace FY26 results**: https://ir.dynatrace.com/news-events/press-releases/detail/425/dynatrace-reports-fourth-quarter-and-full-year-fiscal-2026-financial-results
- **[S34] Cloudflare Q1 2026 results**: https://www.cloudflare.net/news/news-details/2026/Cloudflare-Announces-First-Quarter-2026-Financial-Results/default.aspx
- **[S35] HENNGE 3 million contracted users**: https://hennge.com/global/info/press/20260528_user3m/
- **[S36] HENNGE news page (first native MCP integration, 2026-07-15)**: https://hennge.com/global/info/
- **[S37] PKSHA AI Agents launch / operating-agent count**: https://www.pkshatech.com/news/20250407/
- **[S38] Yonyou 2025 annual report**: https://pdf.dfcfw.com/pdf/H2_AN202604171821302988_1.pdf

## 九、研究边界与可信度

1. **A 级**：有 SEC/审计财报/官方 IR 及可复核的定量续约或生产证据。**B 级**：核心业务财务可验，但 AI/Agent 分拆不足。**C 级**：私营公司、只有产品公告，或缺少可复核商业指标。
2. 未将“账户使用”、“已成交”、“GA”自动当作大规模生产；表中已主动降级。
3. 客户 ROI 多来自厂商官方案例，存在幸存者偏差；下一轮应优先向客户财报、采购文件、独立调研和管理层电话会反向求证。
4. 本文刻意不提供价格目标、仓位或买入结论。高质量收费站不等于高质量投资；尚需单独审查估值、股权激励稀释、并购商誉、推理毛利和安全边际。

---

*For learning and research only; not investment advice.*
