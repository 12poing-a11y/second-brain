# CTA 路径A · 核心规则

**schema_version:** wiki-claim-v1  
**Claim:** 中国商品期货路径A：仅当主力合约近20日与近60日收益同向才开仓；仓位为 `floor(风险预算 / (ATR14 × 乘数))`；当前为纸面记账不下单。  
**Source:** `raw/` 本地验证会话 + https://github.com/12poing-a11y/cta-path-a  
**Confirmed:** 2026-10-19  
**Status:** confirmed  

## Parameters

- Equity: ¥200,000  
- 单品种风险: 1.5% → ¥3,000  
- 品种: JD / JM / CF / SR / RU / MA  
- 自动化: GitHub Actions 工作日 15:30 / 周日周回测  

## Notes

- 路径A未达标前不升杠杆  
- 公开仓不含 API Key  
