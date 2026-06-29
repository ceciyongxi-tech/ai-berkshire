---
name: investment-research
description: "AI Berkshire skill: 投资研究：巴菲特-芒格-段永平-李录 四大师综合分析框架. Source: skills/investment-research.md."
---

## Codex adapter note

This skill is generated from `skills/investment-research.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Commands that reference `~/ai-berkshire/tools/...` assume the repo is checked out at `~/ai-berkshire`; if needed, prefer the current workspace path.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# 投资研究：巴菲特-芒格-段永平-李录 四大师综合分析框架

对 $ARGUMENTS 进行系统化投资研究分析。默认研究对象为美股上市公司，优先使用 SEC 原始披露、公司 IR、10-K/10-Q/8-K、earnings call、DEF 14A / Proxy Statement 和第三方财务数据库交叉验证。报告继续用中文输出。

## 研究框架

基于巴菲特、芒格、段永平、李录四位投资大师的方法论，按以下七个模块顺序执行研究：

### 前置步骤：AI研究偏见自觉（必须执行）

在开始研究前，先评估该公司的"AI可研究性"，识别潜在的数据偏见：

**信息丰富度评级**：
| 等级 | 特征 | AI研究陷阱 | 应对策略 |
|------|------|-----------|---------|
| A级（信息充裕） | 上市多年、券商覆盖多、媒体报道密集 | 共识过强，AI输出趋同于市场定价，alpha有限 | 重点做反面检验：聪明人为什么不买？被忽略的风险是什么？ |
| B级（信息适中） | 上市1-3年、覆盖有限、部分数据需推算 | AI可能用"合理推测"填补空白，看起来完整实则虚假确定性 | 每个推算数据标注置信度，区分"有据推算"和"凭空填充" |
| C级（信息稀缺） | 刚上市/冷门股/新兴市场、几乎无覆盖 | AI会因资料不足而过度保守，误判为"看不清=不好" | 用第一性原理提问（见下方），从有限信息中提取商业本质 |

**C级公司的第一性原理研究法**：
当公开资料不足时，不要试图拼凑出"看起来完整"的报告，而是聚焦以下底层问题：
1. 客户是谁？为什么付钱？有没有替代选择？
2. 复购靠什么驱动？是习惯、锁定、还是持续创造新价值？
3. 竞争对手拿100亿能复制这门生意吗？
4. 管理层做过什么关键决策？这些决策反映了什么判断力和价值观？

**偏见自查清单**（研究全程保持警惕）：
- [ ] 我的"确定性"感受是来自生意本质，还是来自资料数量？
- [ ] 如果把这家公司的资料量减少一半，我的结论会变吗？
- [ ] AI输出的分析是否与市场共识高度雷同？如果是，我的信息优势在哪？
- [ ] 是否存在"公开资料很少但生意本质极好"的可能性被低估了？

将信息丰富度评级结果写入报告开头，并在最终结论中注明"AI研究置信度"与"实际投资确定性"的区别。

### 前置步骤：美股公司类型与披露口径识别（必须执行）

在数据收集前，先识别公司类型，并据此选择财报和估值口径：

| 公司类型 | 必查披露 / 指标 | 特别注意 |
|---------|----------------|----------|
| US domestic issuer | 10-K / 10-Q / 8-K / earnings release / earnings call / DEF 14A | 标准美股主线 |
| ADR | 20-F / 6-K / ADS ratio / 本国披露 | EPS、股价、股数必须按 ADS ratio 对齐 |
| Foreign private issuer | 20-F / 6-K / IFRS 或本国 GAAP 调整 | 披露频率、会计准则、治理规则不同 |
| SPAC / de-SPAC | S-1、424B、8-K、PIPE、warrants、earnout、lock-up | 股本和潜在稀释通常最复杂 |
| REIT | FFO/AFFO、NOI、occupancy、cap rate、debt maturity | 不机械使用传统 PE |
| BDC | NAV、NII、credit quality、leverage、portfolio marks | 重点看信用周期和估值折溢价 |
| Bank / Insurance / Financial | NIM、CET1、ROE、loan loss provisions、combined ratio | 利率、信用、资本充足率优先 |
| SaaS / Cloud | ARR、NRR、RPO、deferred revenue、Rule of 40、SBC | GAAP 亏损公司重点看 FCF 和稀释 |
| Semiconductor | gross margin、inventory、customer concentration、capex cycle、export controls | 周期归一化利润比单年利润更重要 |
| Consumer / Retail | same-store sales、traffic、ticket、gross margin、inventory、store economics | 渠道、品牌、库存和定价权优先 |
| Biotech / Pharma | pipeline、cash runway、trial phase、FDA catalyst、LOE | 不用传统 PE 机械估值 |

**美股特有事项强制检查**：
- [ ] GAAP vs Non-GAAP reconciliation：调整项是否合理，是否连续扩大？
- [ ] SBC 是否真实侵蚀股东收益：金额、占收入、占 FCF、股本稀释。
- [ ] 回购是否抵消稀释：回购金额、均价、share count trend。
- [ ] 管理层是否用 adjusted metrics 美化业绩。
- [ ] 10-K Risk Factors 是否出现新的实质风险。
- [ ] DEF 14A 中管理层薪酬与股东利益是否一致。
- [ ] Insider transactions 仅作为辅助信号，不能替代基本面判断。
- [ ] 13F 持仓变化仅作为参考，不能替代基本面判断。

### 第一步：数据收集

> **数据源规范**：参见 `skills/financial-data.md`。美股研究必须 SEC/IR 原始披露优先，关键数据至少用一个独立第三方来源交叉验证，误差>1%须标记。
> - 原始一手：SEC EDGAR、10-K、10-Q、8-K、DEF 14A、S-1/F-1、公司 Investor Relations、earnings release、earnings call transcript
> - 第三方交叉验证：StockAnalysis、Macrotrends、CompaniesMarketCap、Yahoo Finance、Nasdaq / NYSE official quote pages
> - Koyfin / TIKR / Seeking Alpha 仅作辅助，不作为唯一来源

使用 Task 工具启动后台 Agent，从网络收集以下数据：

1. 收入结构：最近财年及近4季度分部收入、增速、毛利率
2. 财务指标：近5年收入、GAAP净利润、Non-GAAP净利润、毛利率、经营利润率、经营现金流、自由现金流、现金储备
3. 竞争格局：市场份额、主要竞争对手对比
4. 商业模式与护城河：核心竞争优势来源
5. 技术能力：核心技术栈、研发投入
6. 管理层：创始人/CEO履历、持股比例、关键决策记录
7. 行业前景：TAM（总可寻址市场）、增长预测
8. 风险因素：地缘政治、监管、供应链等
9. 当前估值：市值、PE、PS、PEG、EV/Revenue
10. 多空双方核心论点
11. 美股必查：segment revenue / operating income、GAAP vs Non-GAAP、SBC、dilution、buybacks、debt/cash、RPO/deferred revenue/ARR/NRR（SaaS/云/订阅公司）

#### 数据交叉验证（必须执行，使用金融严谨性工具）

数据收集完成后，**必须调用 `tools/financial_rigor.py` 对关键数据进行程序化验证**，杜绝LLM心算误差。

**必须验证的数据点**：
- 总股本（diluted weighted average shares 与 shares outstanding 分别说明，从 SEC/IR、交易所、Yahoo Finance、StockAnalysis 等至少2个源确认）
- 当前股价和市值（**手动计算 股价×总股本 并与报告市值对比，防止单位错误；必须注明使用 diluted shares 还是 shares outstanding**）
- 最近财年收入和净利润（从 10-K/10-Q + 至少1个第三方源确认；GAAP net income 与 Non-GAAP net income 分开）
- 现金储备和净现金（现金+短期投资-总债务，注意口径差异）
- 管理层持股比例（区分经济权益和投票权，注意AB股结构）
- EPS（basic EPS、diluted EPS、adjusted EPS 分开）
- FCF（Operating cash flow - CapEx，核对 CapEx 口径）
- SBC（金额、占收入、占 FCF 的比例）
- 回购与稀释（回购金额、回购价格、股本变化、可转债/期权/RSU）

**强制验证步骤（使用Bash调用工具）**：

Step 1 — 市值验算（精确十进制，非浮点）：
```bash
python3 ~/ai-berkshire/tools/financial_rigor.py verify-market-cap \
  --price {股价} --shares {总股本} --reported {报告市值} --currency {币种}
```

Step 2 — 关键数据多源交叉验证：
```bash
python3 ~/ai-berkshire/tools/financial_rigor.py cross-validate \
  --field {字段名} --values '{"10-K": 数值, "StockAnalysis": 数值}' --unit "USD million"
```
对收入、净利润、现金储备分别执行。

Step 3 — 估值指标精确验算（PE/PB/ROE/FCF Yield 等）：
```bash
python3 ~/ai-berkshire/tools/financial_rigor.py verify-valuation \
  --price {股价} --eps {EPS} --bvps {每股净资产} --fcf-per-share {每股FCF} --dividend {每股股息}
```

**验证规则**：
1. 每个关键数据点至少2个独立来源
2. 发现来源间有差异时，优先采用公司年报/交易所数据，并注明差异原因
3. **所有涉及计算的数据必须通过工具验算，禁止LLM心算**
4. 工具输出结果直接嵌入报告附录"关键数据交叉验证记录"
5. 如果工具报告 ❌ 偏差过大，必须排查原因后才能继续分析

**常见错误防范**：
- 市值单位：港币亿 vs 人民币亿 vs 美元亿，容易漏写/多写一个零
- 美股单位：USD / USD million / USD billion / USD trillion 混用，容易漏写/多写三个零
- 股本口径：diluted weighted average shares、basic shares、shares outstanding 不能混用
- GAAP vs Non-GAAP：adjusted EPS、adjusted net income 不能直接替代 GAAP
- SBC：Non-GAAP 常剔除 SBC，但股东实际承担稀释
- FCF口径：不同来源对资本支出的定义可能不同（是否含租赁、收购等）
- 债务口径：是否包含经营租赁负债
- 持股比例：AB股公司的经济权益 ≠ 投票权

### 第二步：生意本质分析 — 段永平"对的生意"

分析要点：
- 用一句话定义这门生意的本质
- 收入结构拆解（图表）
- 5年盈利能力趋势（图表）
- 商业模式画布：一次性销售 vs 订阅/复购？硬件 vs 软件 vs 平台？
- 生态粘性/客户锁定强度
- 毛利率水平与同行对比，解释为什么高/低
- 经营杠杆分析
- **段永平式追问**：这门生意好在哪？如果只能用一句话描述，是什么？

### 第三步：护城河评估 — 巴菲特"经济护城河"

逐一验证五类护城河：

| 护城河类型 | 验证方法 |
|-----------|---------|
| 品牌/定价权 | 是否能在不损失销量的情况下提价？ |
| 转换成本 | 客户迁移到竞品的成本有多高？ |
| 网络效应 | 用户越多产品越好吗？ |
| 规模效应 | 规模带来的成本优势有多大？ |
| 技术/专利壁垒 | 技术领先几年？能否被复制？ |

分析护城河趋势：过去5年变宽还是变窄？未来5年预判。

**巴菲特式追问**：10年后这条护城河还在吗？什么能摧毁它？

### 第四步：逆向思考与风险清单 — 芒格"反过来想"

- 列出"这家公司可能失败的所有路径"（表格：路径/概率/影响程度）
- 历史类比：找到历史上处于相似位置的公司，结局如何？
- 跨学科分析：用网络效应理论、技术采纳曲线、竞争博弈等模型交叉验证
- 偏误自查：叙事偏差、锚定效应、幸存者偏差
- 收集空方核心论点

**芒格式追问**：我最可能在哪里犯错？聪明人为什么会不买/做空这家公司？

### 第五步：管理层评估 — 段永平"对的人" + 巴菲特"管理层诚信"

- CEO/创始人关键决策复盘（表格：时间/决策/结果/评分）
- 资本配置能力：研发回报率、并购成功率、回购时机
- 股东利益一致性：管理层持股、薪酬结构、减持记录
- 组织能力：团队稳定性、关键人才风险
- 企业文化特征

**段永平式追问**：如果CEO退休，这家公司还能保持竞争力吗？

### 第六步：行业与文明趋势 — 李录"文明演进框架"

- 判断所在行业是否处于"文明级范式转移"
- 历史技术革命类比（蒸汽机/电力/互联网/AI）
- TAM增长曲线与天花板分析
- 公司在产业价值链中的位置
- 技术路线风险
- 客户/供应商集中度分析

**李录式追问**：站在20年后回看，这家公司是"这个时代的标准石油"还是"昙花一现的3Com"？

### 第七步：估值与安全边际 — 巴菲特"内在价值" + 段永平"对的价格"

- 当前市场定价（关键估值指标表格）—— **必须通过工具验算**
- 反向DCF：当前股价隐含了什么增长预期？
- 三情景估值 —— **必须通过工具精确计算，禁止心算**：
```bash
python3 ~/ai-berkshire/tools/financial_rigor.py three-scenario \
  --price {股价} --eps {EPS} --shares {总股本亿} \
  --growth {乐观增速} {中性增速} {悲观增速} \
  --pe {乐观PE} {中性PE} {悲观PE} --years 3 --currency {币种}
```
- 与自身历史估值对比
- 与同行估值对比

**按公司类型选择估值口径**：

| 类型 | 主要估值指标 |
|------|-------------|
| 成熟盈利公司 | P/E、EV/EBIT、EV/FCF、FCF yield、ROIC |
| 高增长软件 | EV/Sales、Rule of 40、FCF margin、RPO growth、SBC-adjusted FCF |
| 半导体 | cycle-normalized EPS、gross margin、inventory cycle、EV/EBIT |
| 金融 | P/B、ROE、CET1、NIM、credit loss cycle |
| REIT | P/AFFO、implied cap rate、NOI、debt maturity |
| 生物医药 | pipeline rNPV、cash runway、binary catalyst risk |

**段永平式追问**：如果股市明天关闭5年，你愿意以这个价格持有吗？

### 第八步：综合决策备忘录

汇总表格：

**美股披露与口径检查表（必须包含）**：

| 检查项 | 结论 | 来源 |
|--------|------|------|
| SEC filing checklist | 10-K / 10-Q / 8-K / DEF 14A / 20-F / 6-K 是否查阅 | |
| GAAP vs Non-GAAP table | 调整项、差额、是否合理 | |
| SBC and dilution table | SBC、占收入、占 FCF、股本变化 | |
| Buyback effectiveness table | 回购金额、均价、股本是否下降 | |
| Segment economics table | 分部收入、经营利润、margin | |
| Key shareholder questions | 股东最该追问的问题 | |
| Bull / bear debate | 多空论点和证据 | |

| 维度 | 结论 | 信心度 |
|------|------|--------|
| 生意质量（段永平） | | |
| 护城河（巴菲特） | | |
| 管理层（段永平+巴菲特） | | |
| 最大风险（芒格） | | |
| 文明趋势（李录） | | |
| 估值（巴菲特+段永平） | | |

最终决策表格：

| 策略 | 建议 |
|------|------|
| 空仓者 | |
| 持仓者 | |
| 卖出信号 | |
| 加仓信号 | |

四位大师的模拟点评（用引用格式）。

## 输出要求

1. 所有分析必须有数据支撑，附数据来源
2. 使用 Markdown 表格呈现关键数据
3. 每个模块末尾必须有对应大师的"追问"
4. 最终将完整报告写入 `~/[公司名]投资研究报告.md`
5. 结论要明确，不回避给出买入/观望/回避的建议
6. 估值部分必须给出具体的价格区间
7. **报告开头**必须包含"信息丰富度评级"（A/B/C）和"AI研究局限性声明"
8. **报告结尾**必须区分"AI分析置信度"与"投资确定性"——前者取决于资料量，后者取决于生意本质。明确告知读者：本报告的哪些结论基于充分数据，哪些基于有限信息的推理
9. 如果公司属于C级（信息稀缺），报告末尾必须列出"需要一手验证的问题清单"——建议读者通过田野调查、产品体验、供应链访谈等方式补充AI的盲区
10. 美股报告最终评级必须明确落到：买入 / 观察 / 回避 / 数据不足

## 数据抽检（准出流程）

报告写入文件后，**必须**执行数据抽检，通过后方可发布：

**Step 1 — 提取抽检清单（15%随机抽样）：**
```bash
python3 ~/ai-berkshire/tools/report_audit.py extract \
  --report <报告文件路径>
```
输出 JSON 模板，每项含 `fetched_value`（待填）。

**Step 2 — 取数核验：**
对清单中每个数据点，按 `skills/financial-data.md` 规范从可靠信源取数
（美股：SEC/IR 原始披露 + StockAnalysis / Macrotrends / CompaniesMarketCap 等第三方交叉验证），
填入 `fetched_value` / `fetched_source` / `fetched_value2` / `fetched_source2`。

**Step 3 — 输出判决：**
```bash
python3 ~/ai-berkshire/tools/report_audit.py verdict \
  --results '<填好的JSON>' \
  --report <报告文件名>
```

- **【准出】**：所有抽检点偏差 ≤ 1% → 报告可发布
- **【打回】**：任意点偏差 > 1% → 修正对应数据后重新抽检，直到准出
