# 内部组织重构与 ETF 穿透底稿

> 数据截止日：2026-07-16（JST）  
> 定位：总报告第五层“非 AI 原生企业内部重构”与 ETF 穿透的证据底稿。公司自报的 economic value、节省工时与客户案例均不视作独立审计结果。

## 一、先给结论

1. 截止日没有足够证据证明任何大型非 AI 原生企业已经“完成”组织重构；DBS 最接近形成显式方法论，Klarna 的人员/客服变化最激进，JPMorgan 的生产规模最强。
2. 收入/员工改善不能直接归因 AI。利率、业务组合、价格、自然减员、外包、广告、云业务与裁员都可能是更大驱动。
3. 真正可信的内部采纳证据要同时出现：生产任务量、处理周期/质量、资源投入变化、公司级利润或份额，并有对照期。
4. AIQ、WTAI、BOTZ 都不能纯粹表达“数据、权限、工作流与 Agent 执行收费站”；其前十大分别明显偏向半导体、大平台和工业自动化。
5. ETF 重复持仓意味着同时持有三只并不等于获得三套独立主题暴露。

## 二、内部采纳者证据矩阵

| 公司 | 生产证据 | 经营变化 | AI 归因 | 最强反面证据 |
|---|---|---|---|---|
| JPMorgan | CIB 175+ AI 用例生产；65,000+ CIB 用户使用 LLM Suite；交易筛查量 >2x、人工检查减半 | 2023→2025 收入/员工约 $510k→$573k，+12.3%；KYC 单位成本近 -40% | 中 | 集团收益受利率、交易活跃度、Visa 收益和规模增长显著影响；总员工仍增加 |
| DBS | 2,000+ 模型、430+ 用例；DBS-GPT 覆盖核心市场员工；启动 Operating Model Transformations | 公司自报 AI/ML economic value 约 S$1B；2025 cost-income 40%、ROE 16.2%；识别 11,000+ 员工深度再培训 | 中高 | economic value 非独立审计；利率与财富管理是重要收益驱动；员工口径不适合强行跨年精算 |
| Klarna | AI 助手处理 80% 客服对话、约 31M 次对话；内部 CSAT 未下降 | 2022→2025 收入/员工约 $344k→$1.24M；员工 -49%；2025 调整后经营利润率 1.9% | 中高 | 2025 IFRS 经营仍亏损约 $229M；后续重提人工服务质量；自然减员、供应商削减和收入增长共同作用 |
| Walmart | 150 万美国员工获得 AI 工具；排班规划 90→30 分钟；供应链工具多市场生产 | FY2024→FY2026 收入/员工约 $309k→$340k，+10.0%；经营利润率均 4.2% | 低到中 | 电商、广告、会员费、价格与客流是更主要财务驱动；没有 AI 单独收益口径 |
| Duolingo | Video Call 等 AI 功能收费并生产；内部推行后又校正 AI-first 政策 | 2024→2025 收入/员工约 $901k→$1.153M，+27.9%；经营利润率 8.4%→13.1% | 中 | 毛利率 72.8%→72.2%，AI 成本是压力之一；员工仍增加约 8%；收入主要由订阅增长驱动 |
| Amazon | 代码迁移、客服、物流与机器人均有生产用例；同时是 AI 供应商 | 2023→2025 收入/员工约 $377k→$455k，+20.7%；经营利润率约 6.4%→11.2% | 低 | AWS、广告、业务组合与成本削减足以解释大部分改善，无法从公开数据分离内部 AI 贡献 |

## 三、精确计算口径

- JPMorgan：2023 收入 $158.104B / 309,926 人 = $510,135/人；2025 收入 $182.447B / 318,512 人 = $572,810/人，增幅 12.286%。
- Walmart：FY2024 收入 $648.125B / 2.1M 人 = $308,631/人；FY2026 收入 $713.163B / 2.1M 人 = $339,601/人，增幅 10.035%。
- Duolingo：2024 收入 $748.024M / 约 830 人 = 约 $901k/人；2025 收入 $1.037589B / 超过 900 人 = 约 $1.153M/人，增幅约 27.9%。因员工数是年报约数，只保留近似值。
- Amazon：2023 收入 $574.785B / 1.525M 人 = $376,908/人；2025 收入 $716.924B / 1.576M 人 = $454,901/人，增幅 20.693%。
- Klarna 的收入/员工指标采用公司 2025 年报披露口径，不自行用期末员工数重构平均员工口径。

## 四、ETF 前十大穿透

权重来自截止日前基金官方持仓页；求和使用 `tools/financial_rigor.py calc`。主题纯度是研究判断，不是基金公司的分类。

| ETF | 前十大及权重 | 前十合计 | 穿透判断 |
|---|---|---:|---|
| AIQ | SK hynix 6.44%、Micron 6.38%、AMD 5.57%、Samsung 4.39%、Intel 4.29%、Cisco 4.06%、TSMC 3.32%、Apple 3.27%、Broadcom 3.08%、NVIDIA 2.96% | **43.76%** | 几乎是半导体/硬件与大平台篮子，对数据、权限、工作流覆盖弱 |
| WTAI | Micron 4.56%、NVIDIA 4.44%、Samsung 4.24%、Amazon 3.97%、Meta 3.80%、Kioxia 3.66%、Alphabet 3.62%、PANW 3.30%、SK Square 3.22%、SanDisk 3.17% | **37.98%** | 比 AIQ 分散，但仍偏硬件和超大平台，纯工作流/身份权重很低 |
| BOTZ | ABB 9.95%、Keyence 9.58%、NVIDIA 9.24%、Fanuc 8.52%、Intuitive Surgical 6.11%、SMC 4.62%、汇川 3.92%、Daifuku 3.47%、Cognex 2.42%、Alphabet 2.39% | **60.22%** | 工业自动化/机器人基金，不是企业 Agent 治理基金 |

### 前十大重合

- AIQ × WTAI：Micron、Samsung、NVIDIA。
- AIQ × BOTZ：NVIDIA。
- WTAI × BOTZ：NVIDIA、Alphabet。
- 全持仓口径的半导体、存储与 hyperscaler 因同一经济驱动，实际因子重合高于“同名证券”重合。

## 五、可证伪跟踪框架

| 研究对象 | 下一步必须拿到 | 降级条件 |
|---|---|---|
| JPMorgan / DBS | AI 项目年度收益的定义、成本基线、质量/风险指标、员工结构变化 | 规模扩大但返工、事故或监管成本上升 |
| Klarna | 人工回补后的 CSAT、处理成本、信用损失和人均收入持续性 | 服务质量恶化，或人员回升后效率优势消失 |
| Walmart | 门店/供应链工具覆盖率、节省工时转为利润或份额的桥接 | 流程节时但利润率与客户体验没有改善 |
| Duolingo | AI SKU 收入、推理毛利、留存与员工结构 | AI 收入增长低于推理成本，或政策回撤损伤执行 |
| 主题 ETF | 全持仓六层映射、重复因子、估值与费率 | “AI”标签无法带来目标控制点敞口，且重复现有持仓 |

## 六、主要一手来源

- [JPMorgan 2025 Annual Report](https://www.jpmorganchase.com/ir/annual-report/2025)、[2024 CIB letter](https://www.jpmorganchase.com/ir/annual-report/2024/ar-ceo-letter-petno-rohrbaugh)
- [DBS 2025 CEO reflections](https://www.dbs.com/annualreports/2025/ceo-reflections.html)、[DBS 2025 CFO statement](https://www.dbs.com/annualreports/2025/cfo-statement.html)
- [Klarna 2025 SEC annual report](https://www.sec.gov/Archives/edgar/data/2003292/000162828026038366/annualreport2025.htm)
- [Walmart FY2026 10-K](https://www.sec.gov/Archives/edgar/data/104169/000010416926000055/wmt-20260131.htm)、[Walmart associate AI tools](https://corporate.walmart.com/news/2025/06/24/walmart-unveils-new-ai-powered-tools-to-empower-1-5-million-associates)
- [Duolingo 2025 10-K](https://www.sec.gov/Archives/edgar/data/1562088/000162828026012494/duol-20251231.htm)
- [Amazon 2025 10-K](https://www.sec.gov/Archives/edgar/data/1018724/000101872426000004/amzn-20251231.htm)
- [AIQ official holdings](https://www.globalxetfs.com/funds/AIQ)、[WTAI official holdings](https://www.wisdomtree.com/us/products/megatrends/wtai)、[BOTZ official holdings](https://www.globalxetfs.com/funds/botz)

本底稿只验证生产与经营证据，不给出买入结论。任何公司或 ETF 必须另过估值与安全边际。
