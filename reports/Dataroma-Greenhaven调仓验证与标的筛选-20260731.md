# Dataroma Greenhaven 调仓验证与标的筛选研究报告

> **研究日期**：2026-07-31（JST）  
> **数据截止**：13F 持仓截至 2026-06-30；价格截至 2026-07-30 美股收盘附近  
> **研究对象**：[Dataroma — Greenhaven Associates](https://www.dataroma.com/m/holdings.php?m=GA)  
> **一手核验**：[SEC 2026Q2 Form 13F-HR](https://www.sec.gov/Archives/edgar/data/846222/000121390026082192/0001213900-26-082192-index.html)  
> **一句话结论**：该页面确实显示 Greenhaven 大举转向医疗健康，并新建 IT 服务仓位；但它不支持“多家机构一致增配生物医药和云计算、规避能源与周期股”的完整叙事。

本文用于学习和研究，不构成投资建议。文中仓位均指“该主题内部仓位”，不是个人总资产配置。

---

## 第一步：先判断网站数据是否可靠

### 1. 页面身份与原始数据

链接中的 `m=GA` 对应 **Greenhaven Associates**，不是多家对冲基金的集合页面，也不是 Gardner Russo & Quinn（后者代码为 `GR`）。

| 项目 | Dataroma | SEC 原始 13F | 核验 |
|---|---:|---:|---|
| 报告期 | 2026Q2 | 2026Q2 | 一致 |
| 期末日期 | 2026-06-30 | 2026-06-30 | 一致 |
| 持仓条目 | 28 | 28 | 一致 |
| 组合市值 | $8,660,706,000 | $8,660,705,519 | 相差 $481，约 0.000006% |

结论：**Dataroma 对这份 13F 的转录准确度很高，可用于快速阅读；关键结论仍应回到 SEC 原始申报。**

### 2. 13F 能告诉我们什么，不能告诉我们什么

根据 [SEC Form 13F FAQ](https://www.sec.gov/rules-regulations/staff-guidance/division-investment-management-frequently-asked-questions/frequently-asked-questions-about-form-13f)：

- 它是季度末的部分美股多头持仓快照，不披露现金、完整外国市场持仓或大多数非 13F 证券。
- 空头不披露，也不会从同一证券的多头中扣除，因此不能据此还原净敞口。
- 法定申报期限可到季度结束后 45 天；Greenhaven 本次于 2026-07-28 提前申报，但其他机构未必同步。
- 市值权重会随股价变化。判断主动买卖应优先看**股数变化**，不能只看权重变化。

更重要的是，Dataroma 的 2026Q2 全站汇总页当时只覆盖 **4/83 家** SuperInvestor 申报。因此，在完整 13F 季结束前，用它证明“多家机构一致流向某行业”存在严重样本偏差。[Dataroma 首页](https://www.dataroma.com/m/home.php)

---

## 第二步：Greenhaven 实际做了什么

### 1. 关键买入与减持

| 股票 | 2026Q2 动作 | 股数变化 | Q2 期末权重 | 业务性质 |
|---|---:|---:|---:|---|
| BDX | 新建仓 | +5,681,708 | 9.93% | 医疗器械与耗材 |
| ICLR | 增持 | +54.84% | 6.22% | CRO 临床研发服务 |
| ACN | 新建仓 | +3,384,681 | 4.86% | IT 咨询、云与 AI 转型服务 |
| IQV | 新建仓 | +768,045 | 1.71% | 医疗数据、云软件、CRO |
| EPAM | 新建仓 | +587,300 | 0.54% | 软件工程、云与 AI 服务 |
| AVTR | 增持 | +9.04% | 2.82% | 生命科学实验耗材与工具 |
| DNOW | 增持 | +426.83% | 0.65% | 油气工业设备分销 |
| LEN | 增持 | +6.43% | 11.82% | 住宅建筑 |
| GM | 增持 | +2.77% | 11.46% | 汽车 |
| SLB | 减持 | -18.48% | 2.04% | 油田服务 |
| ARW | 减持 | -6.95% | 4.35% | 电子元器件分销 |
| AVT | 减持 | -3.77% | 3.87% | 电子元器件分销 |

资料来源：[Dataroma 持仓页](https://www.dataroma.com/m/holdings.php?m=GA)、[Dataroma 活动页](https://www.dataroma.com/m/m_activity.php?m=GA&typ=a)、SEC 13F 原始 XML。

### 2. 行业权重变化

| Dataroma 分类 | 2026Q1 | 2026Q2 | 环比变化 |
|---|---:|---:|---:|
| Consumer Discretionary | 66.62% | 52.73% | -13.89pct |
| Health Care | 7.61% | 21.38% | **+13.77pct** |
| Information Technology | 8.48% | 8.24% | -0.24pct |
| Services（主要为 ACN） | 0% | 4.86% | +4.86pct |
| Technology（主要为 EPAM） | 0% | 0.54% | +0.54pct |
| Energy | 5.73% | 3.24% | -2.49pct |

Q1 数据来源：[Dataroma 上一期持仓页](https://www.dataroma.com/m/holdings.php?L=2&m=GA)；Q2 数据来源同上。Dataroma 的行业标签较旧，例如把 ACN 单列为 Services，把 EPAM 单列为 Technology，因此不能机械相加后称为“云计算板块”。

### 3. 对原结论逐句判定

| 原结论 | 判定 | 证据 |
|---|---|---|
| 重点买入科技和医疗健康龙头 | **部分正确** | 医疗权重 +13.77pct；ACN、EPAM 为新仓，但只有 ACN 达到显著权重 |
| 提升生物医药占比 | **表述不准确** | 买入对象主要是医疗器械、CRO、医疗数据和生命科学工具；没有典型创新药/生物科技开发商 |
| 提升云计算相关股票占比 | **方向勉强成立，措辞过度** | ACN、EPAM 提供云与 AI 服务，IQV 有云软件；但没有 hyperscaler、纯 SaaS 或云基础设施平台 |
| 反映机构对科技创新和医疗增长乐观 | **只能说明 Greenhaven 的选择** | 单一管理人页面不能外推至“多家机构”；2026Q2 全站样本仍不完整 |
| 规避传统能源 | **部分错误** | 能源权重下降、SLB 被减持，但 DNOW 增持 426.83%，NOV 仍持有，能源并未退出 |
| 规避周期性行业 | **明显错误** | 汽车、住宅建筑、工业等周期股仍是组合主体；Consumer Discretionary 高达 52.73% |

**更准确的改写**：

> Greenhaven 在 2026Q2 明显降低了住宅建筑与汽车的相对集中度，把约 14 个百分点的组合权重转向医疗器械、CRO、医疗数据及企业 IT 服务；这是一种从单一深周期组合向医疗和数字化服务分散的再平衡，而不是全面押注生物医药与云计算，也不是退出能源和周期股。

---

## 第三步：候选标的漏斗

筛选池以本季度最有信息量的五个新建/大幅增持标的为主：ACN、EPAM、IQV、BDX、ICLR。数据以公司最新业绩、管理层指引及 StockAnalysis/S&P Global 快照交叉阅读。由于 GAAP 与调整后利润口径差异较大，估值采用调整后 EPS 时均明确标注。

| 公司 | 约价 | 前瞻 PE | ROE | 经营现金流/净利润 | 杠杆快照 | 漏斗结果 |
|---|---:|---:|---:|---:|---|---|
| ACN | $163.29 | 11.4x | 24.4% | 169% | 净现金；D/E 0.25x | **核心保留** |
| EPAM | 约 $103 | 7.7x | 10.9% | 154% | 净现金；D/E 0.08x | **期权型保留** |
| IQV | $237.79 | 17.4x | 22.8% | 204% | Debt/EBITDA 4.8x | **质量保留，价格等待** |
| BDX | 约 $165 | 12.8x | 6.7% | 336% | Debt/EBITDA 7.8x | 观察 |
| ICLR | 约 $180 | 16.7x | 1.8% | 现金流尚可但利润受重大调整影响 | 净债务约 $2.8B | 观察/暂缓 |

主要二级数据来源：[ACN statistics](https://stockanalysis.com/stocks/acn/statistics/)、[EPAM statistics](https://stockanalysis.com/stocks/epam/statistics/)、[IQV statistics](https://stockanalysis.com/stocks/iqv/statistics/)、[BDX statistics](https://stockanalysis.com/stocks/bdx/statistics/)、[ICLR statistics](https://stockanalysis.com/stocks/iclr/statistics/)。

### 为什么 BDX 和 ICLR 没有直接进入终选

**BDX** 是 Greenhaven 最大的新仓，但 2026 年刚完成 Biosciences & Diagnostic Solutions 与 Waters 的分拆合并，当前报表同时受终止经营、重组、债务清偿和法律事项影响。新 BD 的 FY2026 调整后 EPS 指引为 $12.52-$12.72，但 GAAP 回报率与杠杆仍不符合严格价值筛选标准。[BD FY2026 Q2 结果](https://investors.bd.com/news-events/press-releases/detail/958/bd-reports-second-quarter-fiscal-2026-financial-results)、[交易完成说明](https://investors.bd.com/news-events/press-releases/detail/937/bd-completes-combination-of-biosciences-diagnostic-solutions-business-with-waters-corporation)

**ICLR** 的订单恢复值得关注：2026Q1 book-to-bill 1.42、backlog $22.7B；但 2025 年财报调查确认曾存在不当收入调整，且 2026Q1 调整后 EBITDA 同比下降 20.2%。在会计可信度和利润率恢复至少再验证一个季度前，不宜因为 Greenhaven 连续加仓就照抄。[ICON 2026Q1 结果](https://investor.iconplc.com/news-releases/news-release-details/icon-reports-first-quarter-2026-results)、[ICON 2025 全年结果与调查说明](https://www.iconplc.com/news-events/press-releases/icon-reports-fourth-quarter-and-full-year-2025-results)

---

## 第四步：终选三家公司

## 1. Accenture（ACN）— 核心型

**生意本质**：企业为降低大型数字化、云迁移、网络安全和 AI 改造的失败风险，向 Accenture 购买全球交付能力、行业知识和长期托管服务。

2026 财年第三季度收入 $18.72B、同比 +6%；经营利润率 17.0%，自由现金流 $3.6B。管理层给出的 FY2026 调整后 EPS 指引为 $13.78-$13.90，自由现金流指引为 $10.8-$11.5B。[Accenture FY2026 Q3 原始业绩](https://newsroom.accenture.com/content/3qfy26-earnings/accenture-reports-third-quarter-fiscal-2026-results.pdf)

优点：

- ROE 约 24%，ROIC 约 27%，资产负债表为净现金。
- TTM 自由现金流约 $12.58B，现金转换质量高。
- 管理服务收入增速高于咨询，长期合同提高客户黏性。
- 约 11.8x FY2026 调整后 EPS 中值，且股息率接近 4%，估值已反映相当程度的 AI 替代担忧。

最强反方观点：

- 生成式 AI 会减少编码、测试和实施所需工时，传统“按人天收费”模式可能同时遭遇价格和工时压缩。
- Q3 新签订单同比下降，增长更多来自并购和汇率；若 AI 项目无法形成大规模托管收入，低估值可能是价值陷阱。

**行动区间**：以 $13.84 的 FY2026 调整后 EPS 中值为锚，10x/12x/14x 分别对应 $138/$166/$194。

- ≤$165：可分批建立核心仓。
- ≤$145：安全边际明显改善，可加仓。
- $190-$195 以上：若有机增长仍只有中个位数，应降低预期或部分兑现。

## 2. IQVIA（IQV）— 医疗数据与 CRO 卫星型

**生意本质**：药企同时购买 IQVIA 的临床研发执行、全球医疗数据和商业化分析，数据资产与服务网络相互强化。

2026Q2 业绩超过收入、调整后 EBITDA 和调整后 EPS 指引上限，公司把全年调整后 EPS 指引提高至 $12.80-$13.00。[IQVIA 2026Q2 结果](https://www.iqvia.com/newsroom/2026/07/iqvia-reports-second-quarter-2026-results)

优点：

- 医疗数据、云应用与 CRO 的组合比单一 CRO 更具交叉销售和转换成本。
- ROE 约 22.8%，TTM 经营现金流约 $2.82B，自由现金流约 $2.18B。
- 过去一年流通股数下降约 4.9%，资本回报积极。

主要风险：

- 总债务约 $16.3B、Debt/EBITDA 约 4.8x，利率或临床研发景气下行会放大权益波动。
- 6 月 30 日 Greenhaven 申报价为 $193.22；最新价约 $238，机构成本不能视作当前安全边际。
- 医药客户削减研发预算、订单取消率上升或数据隐私监管趋严，都可能压低估值。

**行动区间**：以 $12.90 的 2026 调整后 EPS 中值为锚，16x/18x/20x 分别对应 $206/$232/$258。

- 当前约 $238：业务可持有，但不建议追涨建重仓。
- $215-$225：开始分批。
- ≤$205：在基本面未恶化时具较好安全边际。
- 核心监测：book-to-bill、R&D Solutions 有机增长、净杠杆、自由现金流用于回购还是降债。

## 3. EPAM Systems（EPAM）— 高弹性期权型

**生意本质**：为大企业提供从产品工程、云迁移到 AI 落地的高技术交付团队，价值在复杂系统整合，而非单纯出售程序员工时。

2026Q1 收入 $1.40B、同比 +7.6%，有机固定汇率增长 +3.7%；FY2026 非 GAAP EPS 指引为 $12.98-$13.28。公司有约 $1.04B 现金、约 $0.29B 债务，资产负债表最干净。[EPAM 2026Q1 结果](https://investors.epam.com/news/news-details/2026/EPAM-Reports-Results-for-First-Quarter-2026/default.aspx)

优点：

- 约 7.9x 2026 非 GAAP EPS 中值，净现金约 $14/股，估值明显低于正常 IT 服务公司。
- TTM 自由现金流约 $544M，自由现金流收益率接近 10%。
- 股数同比下降约 3.7%，下行期仍在回购。

最强反方观点：

- AI 编码工具可能直接压缩 EPAM 的人员需求和收费单价；客户延迟项目时，高固定人力成本会快速侵蚀利润。
- ROE 仅约 11%，尚未达到硬性 15% 门槛。
- Greenhaven 只配了 0.54%，更像试仓而非高确定性判断；2026Q2 业绩将在 8 月 6 日公布。

**行动区间**：以 $13.13 的非 GAAP EPS 指引中值为锚，7x/8x/10x 对应 $92/$105/$131。

- 当前约 $103-$104：估值便宜，但不应在财报前建立大仓。
- 财报确认有机增长、利润率和现金流后，≤$100 可小仓分批。
- ≤$92：基本面未破坏时可提高期权仓。
- 任何“有机增长转负 + 利润率下修 + 回购停止”的组合，应视为论文失效信号。

---

## 第五步：组合与行动清单

### 1. 主题内部配置

| 公司 | 类型 | 推荐度 | 主题内建议权重 | 当前动作 |
|---|---|---:|---:|---|
| ACN | 核心 | ★★★★☆ | 50%-60% | $165 以下分批建立 |
| IQV | 卫星 | ★★★★☆ | 20%-30% | 等待 $215-$225，避免追涨 |
| EPAM | 期权 | ★★★☆☆ | 5%-10% | 等 8 月 6 日财报确认 |
| 现金 | 机会储备 | — | 10%-20% | 等待波动与财报验证 |

这不是按 Greenhaven 权重复制，而是按商业质量、资产负债表与估值重新排序。若只买一家公司，优先 ACN；若无法承受单股与财报风险，可用宽基医疗 ETF（如 VHT）和软件 ETF（如 IGV）替代，但 ETF 仍需单独核验当日估值与成分权重。

### 2. 暂不推荐直接买入的观察标的

- **BDX**：等待 FY2026 Q3、分拆后两至三个可比季度和债务下降路径清晰。
- **ICLR**：等待会计整改、审计可信度和 EBITDA 利润率恢复被连续验证。
- **AVTR**：生命科学工具景气可能触底，但杠杆与低回报率尚不足以成为优先标的。

### 3. 需要推翻本报告的证据

| 公司 | 关键失效信号 |
|---|---|
| ACN | 大额订单持续下降；并购剔除后收入不增长；AI 导致收入/员工和收费率同步恶化 |
| IQV | book-to-bill 长期低于 1；净杠杆不降反升；自由现金流大量用于高价回购 |
| EPAM | 有机固定汇率收入转负；利用率和价格同时下降；AI 原生业务无法抵消传统开发工时减少 |

---

## 第六步：信息充分度与最终判断

| 维度 | 等级 | 说明 |
|---|---|---|
| Greenhaven 13F 原始数据 | A | SEC 与 Dataroma 金额、股数、条目高度一致 |
| 单一管理人调仓解释 | A- | 股数变化明确；不知道季度内具体买入日期与成交价 |
| “多家机构”行业流向 | C | 2026Q2 当时仅少数 Dataroma 管理人完成申报，不能外推 |
| 候选公司财务数据 | B+ | 最新公司业绩已覆盖；BDX/ICLR 存在重组或会计口径扰动 |
| 估值时效性 | A- | 使用 2026-07-30 附近价格；股价会继续变化 |

**最终判断**：

1. Dataroma 网站本身对 Greenhaven 13F 的转录是可靠的。
2. “显著增配医疗健康”正确；“增配科技”需限定为企业 IT/AI 服务。
3. “生物医药和云计算”是主题包装，不是对实际持仓最准确的行业描述。
4. “规避传统能源和周期行业”不成立，尤其与 52.73% 的周期消费持仓及 DNOW 大幅增持相矛盾。
5. 基于质量与价格，而非跟单强度，优先顺序为 **ACN > IQV > EPAM**；BDX、ICLR 暂列观察。

---

## 主要资料来源

- [Dataroma Greenhaven 2026Q2 持仓](https://www.dataroma.com/m/holdings.php?m=GA)
- [Dataroma Greenhaven 调仓活动](https://www.dataroma.com/m/m_activity.php?m=GA&typ=a)
- [SEC Greenhaven 2026Q2 13F-HR](https://www.sec.gov/Archives/edgar/data/846222/000121390026082192/0001213900-26-082192-index.html)
- [SEC Form 13F FAQ](https://www.sec.gov/rules-regulations/staff-guidance/division-investment-management-frequently-asked-questions/frequently-asked-questions-about-form-13f)
- [Accenture FY2026 Q3 results](https://newsroom.accenture.com/content/3qfy26-earnings/accenture-reports-third-quarter-fiscal-2026-results.pdf)
- [IQVIA 2026Q2 results](https://www.iqvia.com/newsroom/2026/07/iqvia-reports-second-quarter-2026-results)
- [EPAM 2026Q1 results](https://investors.epam.com/news/news-details/2026/EPAM-Reports-Results-for-First-Quarter-2026/default.aspx)
- [BD FY2026 Q2 results](https://investors.bd.com/news-events/press-releases/detail/958/bd-reports-second-quarter-fiscal-2026-financial-results)
- [ICON 2026Q1 results](https://investor.iconplc.com/news-releases/news-release-details/icon-reports-first-quarter-2026-results)
- StockAnalysis/S&P Global company statistics pages linked in the funnel table

## 审计记录

- `financial_rigor.py` 核验 SEC 与 Dataroma 的 13F 总市值，偏差低于 0.001%。
- 估值区间以管理层调整后 EPS 指引中值乘以明确倍数计算，不把分析师目标价当作内在价值。
- `report_audit.py` 以 20% 比例抽检 17 个数据点：16 项通过、1 项口径警告、0 项失败；警告来自 ACN ROE 使用期末权益或平均权益时产生约 1.35% 的相对差异，不影响“ROE 显著高于 15%”的筛选结论。
- 待更新：Dataroma 2026Q2 全部 83 家管理人申报完成后的行业聚合结果；EPAM 2026Q2；BDX FY2026 Q3；ICON 2026Q2。
