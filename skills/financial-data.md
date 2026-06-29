# 财务数据获取与交叉验证规范

本规范适用于所有涉及企业财务数据的研究。**AI Berkshire 默认研究对象为美股上市公司**，关键数据必须优先回到 SEC 原始披露和公司 IR，并至少用一个独立第三方来源交叉验证。误差 > 1% 必须标记并解释口径差异。

---

## 默认数据源优先级：美股主线

### 1. 原始一手披露（最高优先级）

| 来源 | 用途 | 备注 |
|------|------|------|
| SEC EDGAR | 所有美国上市公司披露入口 | 优先查 accession filing 原文 |
| 10-K | 年报、业务、风险、分部、MD&A、审计财务 | 年度基准来源 |
| 10-Q | 季报、季度趋势、短期风险变化 | 季度基准来源 |
| 8-K | earnings release、重大事项、并购、融资、管理层变动 | 财报日和事件驱动必查 |
| DEF 14A / Proxy Statement | 管理层薪酬、董事会、股权激励、治理 | 管理层与股东利益一致性必查 |
| S-1 / F-1 | IPO 或 FPI 上市披露 | 新上市公司必查 |
| 公司 Investor Relations | earnings release、presentation、transcript、supplement | 与 SEC 文件互相核对 |
| Earnings Call Transcript | 管理层解释、analyst Q&A、guidance 变化 | 不替代财务报表 |

### 2. 第三方财务交叉验证源

| 来源 | 用途 | 限制 |
|------|------|------|
| StockAnalysis | 收入、利润、现金流、股本、分红、估值 | 与 SEC/IR 核对后使用 |
| Macrotrends | 长周期财务和估值序列 | 注意更新滞后和口径 |
| CompaniesMarketCap | 市值、EV、shares、同业排名 | 适合市值交叉验证 |
| Yahoo Finance | quote、market cap、financial summary | quote 可用，财务口径需复核 |
| Nasdaq / NYSE official quote pages | quote、market data、交易所信息 | 用于价格和上市状态确认 |
| Koyfin / TIKR / Seeking Alpha | 辅助数据、transcript、同业表 | 不能作为唯一来源 |

### 3. 行业与竞争数据

- 公司 filings 中的 market discussion、competition、risk factors。
- 竞争对手 10-K/10-Q/20-F/6-K 中的 segment disclosure、market share、客户集中度。
- Gartner / IDC / Canalys / Counterpoint / Synergy Research / Similarweb / SensorTower 等行业数据，按行业适用。
- Sector ETF holdings、thematic ETF holdings、industry lists 和 screeners 用于行业召回，不直接证明投资质量。

---

## 美股关键数据交叉验证规则

| 字段 | 必查口径 | 交叉验证要求 |
|------|----------|--------------|
| Revenue | GAAP revenue，必要时拆分 product/service/segment/geography | 10-K/10-Q 与 StockAnalysis 或 Macrotrends 交叉 |
| Net income | GAAP net income 与 Non-GAAP net income 分开列示 | 不得把 adjusted net income 当作 GAAP |
| EPS | basic EPS、diluted EPS、adjusted EPS 分开列示 | 估值默认用 diluted EPS；adjusted EPS 必须解释调整项 |
| Shares | diluted weighted average shares 与 shares outstanding 分别说明 | 回购、RSU、期权、可转债会导致口径差异 |
| Market cap | price × diluted shares 或 shares outstanding | 必须注明股价日期、股本口径和币种 |
| Free cash flow | Operating cash flow - CapEx | 核对 CapEx 是否含 PP&E、internal-use software、leases 或 acquisitions |
| SBC | Stock-based compensation | 披露金额、占收入比例、占 FCF 比例，并评估稀释 |
| Debt / cash | cash、cash equivalents、short-term investments、total debt | 列清净现金/净债务，不混淆 gross cash 与 net cash |
| Segment economics | segment revenue、operating income、margin | 美股公司必须优先分析分部，而不是只看合并数 |
| SaaS / Cloud metrics | RPO、deferred revenue、ARR、NRR、billings、Rule of 40 | 订阅型公司必须检查，缺失则标注 |
| Buybacks | repurchase amount、average price、ending share count | 检查回购是否真正降低股本 |
| Dilution | SBC、option/RSU、convertibles、warrants | 判断股权激励和可转债是否侵蚀股东收益 |

---

## 执行规范

### 第一步：回到原始文件

先确定公司类型和适用披露：

- US domestic issuer：10-K / 10-Q / 8-K / DEF 14A。
- ADR / Foreign private issuer：20-F / 6-K / ADS ratio，必要时查本国披露。
- SPAC / de-SPAC：S-1、424B、8-K、PIPE、earnout、warrant、lock-up。
- REIT / BDC / Bank / Insurance：使用行业专属口径，不机械套 PE。

### 第二步：第三方交叉验证

对每个关键财务指标，至少从原始披露和一个第三方来源取数。推荐格式：

```text
Revenue FY2025：$281.7B ✅
  - 10-K: $281.7B
  - StockAnalysis: $281.7B
  - 误差: 0.0%
  - 口径: GAAP revenue, USD
```

差异示例：

```text
Net income FY2025：$72.4B ⚠️ GAAP / Non-GAAP 差异
  - 10-K GAAP net income: $72.4B
  - Earnings release adjusted net income: $83.1B
  - 原因: adjusted 口径排除 SBC、restructuring、acquisition amortization
```

### 第三步：误差计算与处理

```text
误差率 = |来源1数值 - 来源2数值| / 来源1数值 × 100%
```

| 误差 | 处理方式 |
|------|---------|
| ≤ 1% | 一致，采用原始披露值，并标注两个来源 |
| 1% - 5% | 标记“数据存在差异”，说明 GAAP/Non-GAAP、股本、汇率、更新时间或 fiscal period 差异 |
| > 5% | 标记“数据存在重大差异”，必须回到 SEC/IR 原文核实，不得直接使用 |

---

## 常见差异原因

| 原因 | 说明 |
|------|------|
| GAAP vs Non-GAAP | 美股利润、EPS、margin 最常见差异来源 |
| Basic vs diluted shares | EPS、市值和 per-share 指标会受股本口径影响 |
| Weighted average shares vs shares outstanding | 财报 EPS 与当前市值计算不是同一股本口径 |
| Fiscal year vs calendar year | Apple、Microsoft、retailers 等财年不等于自然年 |
| TTM vs fiscal period | 第三方页面常把 TTM 与 FY 混排 |
| Segment reclassification | 公司重组分部后，历史数据可能被重述 |
| CapEx definition | PP&E、capitalized software、leases、acquisitions 口径可能不同 |
| SBC treatment | Non-GAAP 通常剔除 SBC，但股东实际承担稀释 |
| ADR ADS ratio | ADR 每股代表的普通股数量不同，EPS 和股价不可直接混用 |

---

## 非美股例外

本项目默认美股。只有当用户明确指定 A 股、港股或其他国际市场时，才使用当地披露体系：

- 港股：HKEX 披露易、公司年报、公告、IR；可用 Macrotrends ADR 或 Yahoo Finance 辅助。
- A 股：巨潮资讯、交易所公告、公司年报/季报；东方财富等仅作辅助。
- 其他市场：优先使用当地交易所/监管披露和公司 IR。

非美股研究必须在报告开头标注“非默认市场研究”，并说明使用了哪些非美股披露体系。

---

## 快速索引

| 场景 | 原始来源 | 交叉验证来源 |
|------|----------|--------------|
| Microsoft (MSFT) | SEC EDGAR 10-K/10-Q/8-K、Microsoft IR | StockAnalysis、Macrotrends、Yahoo Finance |
| NVIDIA (NVDA) | SEC EDGAR 10-K/10-Q/8-K、NVIDIA IR | StockAnalysis、CompaniesMarketCap、Nasdaq quote |
| Apple (AAPL) | SEC EDGAR 10-K/10-Q/8-K、Apple IR | StockAnalysis、Macrotrends、Yahoo Finance |
| Amazon (AMZN) | SEC EDGAR 10-K/10-Q/8-K、Amazon IR | StockAnalysis、Macrotrends、CompaniesMarketCap |
| ADR / FPI | 20-F、6-K、company IR、ADS ratio | Yahoo Finance、StockAnalysis、Nasdaq/NYSE quote |
