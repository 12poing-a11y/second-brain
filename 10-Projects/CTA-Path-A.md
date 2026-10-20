# Project · CTA Path A

**目标**：中国商品期货路径A纸面验证可复现、可回测。  
**状态**：进行中（L1）

## 链接

- 策略仓：https://github.com/12poing-a11y/cta-path-a
- 可视化：https://12poing-a11y.github.io/
- Notion 台账：中国期货CTA路径A验证台账

## 规则摘要

- 20D 与 60D 同向才开仓
- `lots = floor(3000 / (ATR14 × 乘数))`
- Equity 20万；路径A不下单

## 下次动作

- [ ] 仓库 Secrets 配齐 IFIND / NOTION
- [ ] Actions 手动跑通一次日报
- [ ] 周回测样本 ≥5 日后写第一份正式周报
