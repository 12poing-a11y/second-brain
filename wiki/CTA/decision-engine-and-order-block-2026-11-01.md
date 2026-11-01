# CTA 决策引擎升级 + 订单块(OB)增量模块

**schema_version:** wiki-claim-v1  
**Claim:** 保留 Path-A 基准；研究台升级为决策引擎；OB 为信号附加分/位置止损工具，须 BOS+最后反向K+回踩定义、防前视、ablation 晋级，本阶段仅影子研究不进 formal。  
**Source:** `raw/chatgpt-shares/2026-11-01/`（`INDEX.md`、`01-四维框架.md`、`02-订单块.md`、`03-后续实现方向.md`）；https://chatgpt.com/s/t_6ae5e47157748191b3ab13ce0e7850c8 ；https://chatgpt.com/s/t_6ae703ed42e4819186f39d9d978686b6 ；https://chatgpt.com/s/t_6ae704d7b55c8191ab0c3ec382adadb6 ；desk handoff `/workspace/desk/project-log/2026-11-01-四维决策引擎与OB模块-框架方向.md`  
**Confirmed:** 2026-11-01  
**Status:** unconfirmed  

## Notes

- **P0 统一成本口径。** 先审计各回测入口对成交时点、费用、持仓与换月是否同一口径，再修。P0 不能跳过；否则后续优化可能只是在优化回测假象。研究台上的评分不能直接变成交易指令。
- **P1 `fair_value` 须样本外 A/B/C。** A 组冻结现有 Path-A；B 组只附加估值偏离、不改交易；C 组才在偏离达到预设条件时调整决策。估值可能有解释力却没有短周期预测力，须证明样本外独立价值后才能参与交易决策。没有可靠估值时不输出精确公允价值。
- **HMM 无一票否决。** HMM 继续作为市场状态研究工具，与简单趋势和波动率基准对照。现有记录表明，HMM 与趋势联合门控不一定优于单独趋势，因此不授予自动否决权。
- **不要单一冲突分数。** 信号先归入趋势、定价、资金、事件与基本面、风险状态五组，组内去冗余后再综合。输出综合方向、证据一致程度、各组贡献、主要冲突来源、持有周期和失效条件，而不是一个加权总分。
- **正式稿仍停在 1.2 / 1.5。** 决策引擎升级与 OB 本阶段不写入 formal。Path-A 基准保持不动；不同时改趋势信号、仓位、止损、估值和对冲。允许交易只是研究系统的决策输出，不代表下单。
- **OB 为独立影子轨，与 1.0 / 1.8 / sentiment / IV / CWFT / VT 平行。** 本阶段仅影子研究，不进 formal，不改 Path-A 手数。定义采用市场结构突破（BOS）+ 最后一根反向 K + 回踩；摆动点须在确认后才可用，禁止用未来 K 线提前生成信号。OB 用作信号附加分和位置止损参考，不是已验证的独立盈利策略。须经消融（ablation）证明增量，并通过无前视、成本与样本外晋级后，才考虑升级为正式信号。

## Links

- Related: [`wiki/CTA/path-a-rules.md`](./path-a-rules.md)
- Raw: [`raw/chatgpt-shares/2026-11-01/`](../../raw/chatgpt-shares/2026-11-01/INDEX.md)
- Desk handoff（本仓未收录正文，仅作路径注记）: `/workspace/desk/project-log/2026-11-01-四维决策引擎与OB模块-框架方向.md`
