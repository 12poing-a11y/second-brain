# CF2701 机构席位与资金结构跟踪

> 研究窗口：最近 3–5 个郑棉交易日；10 个交易日作为背景。  
> 原则：事实、推断、假设、反证分开；缺数据就标缺失，不填造。

## 1. 目标

联合跟踪郑棉 CF2701 的前 20 名多空席位、重点会员席位、价格、成交量、总持仓、现货基差、新棉供应、纺企需求和 ICE 棉花，判断：

1. 空头回补是否持续，是否接近衰竭；
2. 是否有新增多头接棒；
3. 回踩是缩量整理还是反弹失效；
4. 席位信号是否获得现货与基本面支持。

## 2. 每日字段

- 交易日期、合约、收盘价/结算价、涨跌、成交量、全市场持仓及增减。
- 前 20 名多头持仓/增减、前 20 名空头持仓/增减、净持仓或净空变化。
- 重点会员席位（按数据覆盖及排名动态调整）：永安、中信、中粮、东证、国泰君安、华泰等；分别记录多单、空单、净持仓及其变化。
- 现货基差、籽棉收购价、新棉上市/加工进度、纺企采购与库存、ICE 价格与量仓（可核实才填）。

每项数字必须附来源、发布日期、统计日期、合约、单位及口径。不同统计日期的数据不得拼成连续序列。缺失时写“暂无可靠最新数据”；统计日期不明时写“统计日期未确认”。

## 3. 持仓变化的解释边界

会员席位代表多个客户汇总，不等于单一机构或单一方向资金。仅凭每日持仓差分，通常不能直接识别真实开仓和平仓，使用“可能”“与……特征相符”等表述。

| 价格 | 总持仓 | 席位证据 | 初步解释（非事实认定） |
|---|---|---|---|
| 上涨 | 下降 | 空单减少 | 与空头回补相符，但不能证明所有买盘来自平空 |
| 上涨 | 增加 | 多单增加、净空收窄 | 更支持新增多头参与，仍需排除套保/套利 |
| 下跌 | 增加 | 空单增加、净空扩大 | 空头主动性增强的可能性上升 |
| 下跌 | 下降 | 多空均减 | 更像去杠杆/仓位退出，方向看多空减幅 |
| 价格与席位分化 | 任意 | 重点会员方向相反 | 标记分歧，不强行归纳成一致方向 |

## 4. 3–5 日结构化判断

每日分别输出：

1. **已核实事实**：逐日价量仓、前 20 名及会员席位变化。
2. **合理推断**：空头回补、新增多头、空头加仓或去杠杆的证据强弱。
3. **反证与缺口**：统计日期、来源冲突、未取得字段。
4. **趋势判断**：偏多/中性/偏空及证据强度。
5. **回踩支撑、反弹压力、失效条件**：必须基于最新可核实价格结构；旧价位只能标为历史观察区。
6. **下一交易日待验证的 3 项指标**。
7. 计算最近 3 日、5 日累计变化，并保留 10 日背景序列。

## 5. 交叉验证与失效条件

- 上涨、持仓下降、空单减少：可能是回补行情；若回补动能衰减、价格滞涨，回踩风险上升。
- 上涨、持仓增加、多单增加、净空收窄：更支持新增多头参与，但仍需检查席位是否分化。
- 下跌、持仓增加、空单增加：反弹失效风险上升。
- 回踩缩量、席位净空不再扩大、支撑有效，随后上涨增仓：更支持反弹延续。
- 若跌破最新确认的回踩低点，同时跌价增仓、重点席位空单增加、现货基差走弱，则提高反弹失效判断等级。

## 6. 研究评分（待验证参数，不是已回测策略）

- 前 20 名净持仓变化：30 分
- 重点会员席位：25 分
- 价格、成交量、总持仓：25 分
- 现货与基本面：20 分

关键数据缺失时输出“无法评分”。评分阈值需经历史样本验证，未验证前不得作为独立下单信号。

## 7. 证据与知识管理协议

遵循第二大脑的 Reader / Librarian / Checker 模式：

- 每条核心结论记录 `Claim / Source / Confirmed`。
- 来源冲突标记 `disputed`，不得静默覆盖。
- 30 天没有新来源，状态降为 `unconfirmed`。
- 逐日数据、推断、反证和后续验证均需可追溯。
- 优先郑商所、中国棉花信息网和可核验的行情/持仓来源。

## 8. 当前历史基线（待持续复核）

公开历史表曾显示永安期货 CF2701 净空：

| 日期 | 净空持仓（手） |
|---|---:|
| 2026-10-12 | 33,035 |
| 2026-10-13 | 31,409 |
| 2026-10-14 | 32,916 |
| 2026-10-15 | 35,489 |
| 2026-10-16 | 38,568 |
| 2026-10-19 | 42,351 |

该序列显示 10 月 12–19 日永安席位净空总体扩大；它不能证明 10 月 20 日之后仍在加空，也不能证明随后已平空。每次使用前必须重新核对原始来源和统计口径。

## 9. GitHub 镜像

- 仓库：<https://github.com/12poing-a11y/second-brain>
- 文件路径：`markets/cotton/CF2701-seat-flow.md`
- 本文是跟踪规范与历史基线，不代表已取得最新交易日席位数据；每次分析必须重新核验来源与统计日期。


## 2026-11-19 Daily Evidence (archived 2026-11-20)

**Claim:** CF2701 Top20 long/short totals and price/OI on 2026-11-19 show net-long improvement largely driven by short reduction, not strong evidence of fresh long accumulation.  
**Source:** Cotway 2026-11-19 archive (direct Zhengzhou member-position file parsing claimed; row-level validation reported): https://cotway.net/archive/2026-11-19.html ; independent cross-check: https://data.bywl.top/members-positions/ ; independent cross-check: https://data.bywl.top/members-positions/  
**Confirmed:** 2026-11-20. **Status:** disputed on Top20 net-change arithmetic; core totals are source-reported, not independently downloaded from the official XLSX in this run.

| Date | CF2701 day close / settle | Day volume | Day OI / change | Top20 long / change | Top20 short / change | Net long / change |
|---|---:|---:|---:|---:|---:|---:|
| 2026-11-19 | 15,525 / 15,455 | 411,000 | 613,774 / -11,046 | 457,172 / -1,456 | 424,464 / -9,899 | 32,708 / +8,443* |

\* A second source reports net-long change +8,069. Preserve as disputed; do not silently replace. 11/18 reported net long 24,265 under the first source's basis.

Night session (trade date 11/20): CF2701 15,570 (+115 vs 11/19 settlement 15,455), volume 159,400, OI 620,307 (+6,533 vs day-session close). No night-session member differential available.

Key member evidence (11/19):
- CITIC: long 67,235 (+1,864), short 57,230 (-3,217), reported net long 10,005 (+5,081).
- Guotai Junan: long 52,769 (+2,792), short 42,640 (-66), reported net long 10,129 (+2,858).
- Galaxy: long 34,894 (+56), short 44,179 (+917), net short remains; member's long/short changes diverge.
- COFCO: long 34,756 (+1,475); net-short rank entry 4,384 (-1,315), source tables differ by ranking type; do not net without matching scope.
- Top net-short ranks: YongAn 26,087 (-81), Nanhua 15,162 (+224), Changjiang 10,765 (+529), Guangfa 10,661 (-650), RuiDa 9,780 (+203), Galaxy 9,285 (+861), Guoxin 8,938 (-529), China International 8,896 (+780), COFCO 4,384 (-1,315).

**Inference:** day-session OI contracted while Top20 short holdings fell substantially more than long holdings, consistent with short covering/position reduction. Night-session price and OI rose, implying new exposure entered but direction cannot be identified without night member data. Do not equate seats with industry hedging.

**3–5 day assessment:** 11/17, 11/18, 11/19 day-session OI changes approximately -7,874, -8,307, -11,046 (aggregate -27,227); 11/19 night +6,533 partially reversed the contraction. Top20 complete 3/5-day series is missing; seat-flow score remains **not scored**.

**Next validation:** official Zhengzhou XLSX; daily Top20 long/short net-change consistency; 11/20 old-warrant cancellation and new-crop registration; whether rebound holds 15,625–15,635 with OI and spot-basis confirmation.
