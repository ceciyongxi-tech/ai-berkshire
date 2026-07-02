# 投研团队：美股四角色并行分析框架

对 $ARGUMENTS 进行团队化美股投资研究分析。使用 Team 工具创建真正的多Agent并行研究团队。默认数据源为 SEC/IR 优先，StockAnalysis、Macrotrends、CompaniesMarketCap、Yahoo Finance、Nasdaq/NYSE quote pages 用于交叉验证；禁止只用新闻或二手摘要。

## 执行流程

### 第一步：展示团队框架

向用户展示以下团队结构，确认后启动：

| 角色 | 职责 | 分析框架 |
|------|------|----------|
| **team-lead**（你自己） | 统筹协调、汇总研判、输出最终报告 | 四大师综合框架 |
| **business-analyst** | 商业模式、客户、定价权、产品替代性、网络效应、生态锁定 | 段永平视角 |
| **financial-analyst** | 10-K/10-Q 财务拆解、GAAP vs Non-GAAP、SBC、回购、稀释、FCF质量、ROIC/FCF yield | 巴菲特视角 |
| **industry-researcher** | 美股行业格局、竞争对手 filings、ETF holdings、市场规模、份额、增长、周期位置 | 芒格视角 |
| **risk-assessor** | 10-K risk factors、监管、诉讼、DEF 14A薪酬、insider transactions、capital allocation、失败路径 | 李录视角 |

### 第一步半：AI研究偏见评估

在创建团队前，先向用户展示该公司的"AI可研究性"评估：

**信息丰富度评级**（决定研究策略）：
| 等级 | 特征 | 研究策略调整 |
|------|------|------------|
| A级（信息充裕） | 上市多年、券商覆盖广 | 团队重点放在**反面检验**和**非共识视角**，避免输出与市场一致的"正确的废话" |
| B级（信息适中） | 上市不久、覆盖有限 | 每个Agent的推算数据必须标注置信度，team-lead汇总时标注"数据充分度" |
| C级（信息稀缺） | 冷门/新上市/新兴市场 | 团队转为"第一性原理模式"：不追求报告完整性，聚焦商业本质的几个核心问题 |

**关键提醒**：资料多≠确定性高，资料少≠确定性低。AI能输出的置信度 ≠ 投资的真实确定性。确定性来自商业模式本身，不来自资料数量。

将评级结果告知每个Agent，影响其研究方式。

同时识别美股公司类型并告知每个 Agent：US domestic issuer / ADR / Foreign private issuer / SPAC or de-SPAC / REIT / BDC / Bank / Insurance / Financial / SaaS / Cloud / Semiconductor / Consumer / Retail / Biotech / Pharma。不同类型必须采用对应财报口径和估值指标，例如 ADR/FPI 查 20-F/6-K/ADS ratio，金融看 NIM/CET1/ROE/loan loss provisions，REIT 看 FFO/AFFO/NOI/cap rate/debt maturity，SaaS 看 ARR/NRR/RPO/deferred revenue/Rule of 40/SBC，半导体看 gross margin/inventory/customer concentration/capex cycle/export controls，生物医药看 pipeline/cash runway/trial phase/FDA catalyst。

### 第二步：创建团队

使用 TeamCreate 创建团队：
- team_name: `{公司名}-research`（英文小写，如 `meituan-research`）
- agent_type: `team-lead`

同时确定本次研究的统一输出目录：
- `reports/{公司名}/`
- 所有分报告和最终报告都必须写入该目录，禁止只写入 `~/` 根目录的单文件报告
- 如果目录不存在，先创建目录

### 第三步：创建4个任务

使用 TaskCreate 创建以下4个任务（每个都要有 subject、description、activeForm）：

#### 任务1：商业模式分析
- subject: `分析{公司名}商业模式、护城河与用户价值`
- description 包含：
  1. 商业模式本质：基于 10-K business section 定义核心生意、客户、产品和收入结构
  2. 平台/产品飞轮效应如何运转
  3. 护城河分析：品牌/转换成本/网络效应/规模效应/技术壁垒，逐一验证
  4. 用户/客户价值：为各方创造了什么独特价值，客户集中度是否过高
  5. 业务矩阵与协同效应
  6. 段永平"好生意"标准评估：差异化、定价权、可持续竞争优势
  7. 必须基于 10-K business section、segment disclosure、customer concentration、竞争对手 filings；行业报告只能辅助

#### 任务2：财务与估值分析
- subject: `分析{公司名}10-K/10-Q财务质量、GAAP/Non-GAAP、SBC、回购、稀释与估值`
- description 包含：
  1. 近3-5年营收、净利润、经营利润趋势
  2. 盈利能力指标：ROE、ROA、毛利率、经营利润率
  3. 现金流分析：经营性现金流、自由现金流、资本开支
  4. 资产负债表健康度：现金储备、负债率、流动性
  5. 估值分析：PE/PS/PB/EV等，与历史及同业对比
  6. 安全边际评估：内在价值 vs 当前股价
  7. **金融严谨性验证（必须使用Bash调用工具，禁止心算）**：
     - 市值验算：`python3 ~/ai-berkshire/tools/financial_rigor.py verify-market-cap --price {价格} --shares {股本} --reported {报告市值} --currency {币种}`
     - 估值验算：`python3 ~/ai-berkshire/tools/financial_rigor.py verify-valuation --price {价格} --eps {EPS} --bvps {每股净资产}`
     - 关键数据交叉验证：`python3 ~/ai-berkshire/tools/financial_rigor.py cross-validate --field {字段} --values '{JSON}' --unit {单位}`
     - 三情景估值：`python3 ~/ai-berkshire/tools/financial_rigor.py three-scenario --price {价格} --eps {EPS} --shares {股本亿} --growth {乐观} {中性} {悲观} --pe {乐观PE} {中性PE} {悲观PE}`
     - 将工具输出结果直接嵌入报告中作为验证记录

#### 任务3：行业与竞争分析
- subject: `分析{行业}行业格局与{公司名}竞争态势`
- description 包含：
  1. 行业规模与增长：市场规模、增速、渗透率
  2. 竞争格局：基于竞争对手 10-K/20-F/6-K、ETF holdings、industry lists 召回并交叉验证主要对手市场份额、竞争策略对比
  3. 核心竞争者威胁评估：逐个分析主要竞争对手
  4. 各细分赛道格局
  5. 行业趋势：技术变革、政策影响、新进入者
  6. 产业链分析：上中下游价值分配
  7. 要求搜索最新行业数据和竞争动态；SaaS 检查 Rule of 40，硬件/半导体检查 inventory cycle，消费/零售检查库存和同店销售，金融/REIT 使用行业专属指标

#### 任务4：风险与管理层评估
- subject: `评估{公司名}投资风险与管理层质量`
- description 包含：
  1. 管理层评估：CEO能力圈、诚信度、战略眼光、资本配置能力、历史决策质量
  2. 监管风险：当前及潜在监管影响
  3. 竞争风险：各竞争对手威胁程度评估
  4. 业务风险：新业务亏损、扩张不确定性
  5. 宏观风险：经济周期、行业周期影响
  6. 治理结构：股权结构、关联交易、股东回报政策
  7. 长期确定性：10年后公司会怎样？什么可能颠覆其商业模式？
  8. 要求搜索最新监管动态、管理层言论等

### 第四步：启动4个并行Agent

使用 Task 工具同时启动4个Agent（**必须在同一条消息中并行调用**）：

每个Agent的配置：
- `subagent_type`: `general-purpose`
- `run_in_background`: `true`
- `team_name`: 对应团队名
- `name`: 对应角色名（business-analyst / financial-analyst / industry-researcher / risk-assessor）

每个Agent的prompt模板：

```
你是{公司名}投研团队中的"{角色中文名}"，负责从{大师名}投资视角分析{公司名}。

请完成任务 #{任务编号}：{任务subject}

具体要求：
{任务description的内容}

**研究方法**：
- 使用 WebSearch 搜索最新公开信息（财报、行业报告、新闻）
- **财务数据必须来自两个独立来源**，按 `skills/financial-data.md` 规范执行（美股：macrotrends+stockanalysis；港股：aastocks+macrotrends；A股：东方财富+巨潮资讯），两源误差>1%须标记
- 确保数据准确，关键数据标注来源
- 分析要深入，不流于表面

**输出要求**：
- 报告要详尽，使用Markdown表格呈现关键数据
- 每个分析维度要有明确结论和评分
- 报告末尾要有该维度的总体结论
- 除发送给 team-lead 外，必须将完整分报告写入统一输出目录：
  - business-analyst: `reports/{公司名}/01-商业模式分析-段永平视角.md`
  - financial-analyst: `reports/{公司名}/02-财务估值分析-巴菲特视角.md`
  - industry-researcher: `reports/{公司名}/03-行业竞争分析-芒格视角.md`
  - risk-assessor: `reports/{公司名}/04-风险管理层评估-李录视角.md`

**完成后**：
1. 使用 TaskUpdate 将任务 #{任务编号} 标记为 completed
2. 确认对应 Markdown 分报告已写入 `reports/{公司名}/`
3. 通过 SendMessage 把完整分析报告发送给 team-lead（type: "message", recipient: "team-lead"）
```

### 第五步：接收报告并跟踪进度

- 向用户实时展示进度表（哪些Agent已完成、哪些仍在研究中）
- 每收到一份报告，更新进度并展示该报告的核心要点（3-5条）
- 等待全部4份报告到齐

### 第六步：关闭团队成员

全部报告收到后，向4个Agent发送 shutdown_request（使用 SendMessage，type: "shutdown_request"）。

### 第七步：汇总最终报告

综合4份分析报告，输出以下结构的最终报告：

---

#### 1. 一句话结论
> 用一段话（50-100字）概括是否值得投资及核心逻辑

#### 2. 四维评分总表
| 维度 | 框架 | 评分(1-5星) | 核心判断 |
|------|------|------------|----------|

综合评分：X / 5

#### 3. 核心数据速览
关键财务和经营指标表格（近2年对比）

必须额外包含美股口径表：SEC filing checklist、GAAP vs Non-GAAP table、SBC and dilution table、buyback effectiveness table、segment economics table。

#### 4. 各维度分析摘要
每个维度摘取3-5条最重要的发现

#### 5. 投资论点（Bull vs Bear）
- 🟢 看多逻辑（5-7条）
- 🔴 看空逻辑（5-7条）

#### 6. 巴菲特买入前Checklist
| # | 检查项 | 通过? | 说明 |
10个核心检查项，逐一评估

#### 7. 最终投资建议
- 定性判断表（生意质量/管理层/估值/时机）
- 分层操作建议表（激进型/稳健型/保守型 → 建议+价格区间）
- 关键催化剂（加仓信号/减仓信号各3-5条）
- 最终评级必须落到：买入 / 观察 / 回避 / 数据不足

#### 8. 总结段落
100-200字的最终总结

---

### 第八步：保存报告

将完整最终报告写入 `reports/{公司名}/最终报告.md`。

如需要保留带日期的归档副本，可额外写入 `reports/{公司名}/{公司名}投资研究报告_{日期}.md`（日期格式 YYYYMMDD），但不得替代上述五文件结构。

最终输出目录必须包含：
- `01-商业模式分析-段永平视角.md`
- `02-财务估值分析-巴菲特视角.md`
- `03-行业竞争分析-芒格视角.md`
- `04-风险管理层评估-李录视角.md`
- `最终报告.md`

### 第九步：数据抽检（准出流程）

```bash
# Step 1 — 提取抽检清单（15%随机抽样）
python3 ~/ai-berkshire/tools/report_audit.py extract \
  --report <报告文件路径>

# Step 2 — 对清单每项从 SEC/IR 原始披露和可靠第三方源取数（参见 skills/financial-data.md）

# Step 3 — 输出准出/打回判决
python3 ~/ai-berkshire/tools/report_audit.py verdict \
  --results '<填好的JSON>' \
  --report <报告文件名>
```

**【准出】** 全部通过 → 报告可发布；**【打回】** 有不通过 → 修正后重审。

### 第十步：清理团队

使用 TeamDelete 清理团队资源。

## 重要注意事项

1. **4个Agent必须并行启动**——在同一条消息中调用4次Task工具
2. **Agent通过SendMessage汇报**——不是文件协作，是消息通信
3. **数据准确性**——要求Agent使用WebSearch搜索最新数据，关键数据交叉验证
4. **结论要明确**——不回避给出买入/观望/回避建议和具体价格区间
5. **所有分析必须有数据支撑**——附数据来源
6. **耐心等待**——4个Agent研究需要几分钟，实时向用户更新进度
7. **反偏见意识**——team-lead在汇总时必须评估：各Agent的分析是否受限于资料充裕度？是否与市场共识过度趋同？最终报告需包含"信息丰富度评级"和"AI研究局限性声明"
8. **信息稀缺时的诚实原则**——宁可在报告中留白标注"数据不足"，也不要用推测填满框架伪装确定性
