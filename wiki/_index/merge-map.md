# 合并映射 · 统一数据契约

Claim:     second-brain、cta-path-a、Cursor、GrokBot、Notion、OBS 共用同一套路径与 schema_version，合并按本页契约执行。
Source:    90-Templates/GrokBot-Bootstrap-Prompt.md；磊 2026-10-20 指令
Confirmed: 2026-10-20
Status:    confirmed
schema_version: wiki-claim-v1

## 权威与路径

| 数据 | 权威位置 | schema_version |
|------|----------|----------------|
| 数字（信号/持仓/风险） | `cta-path-a/archive/l1_report_YYYYMMDD.json` | cta-signal-v1 |
| 人读摘要 | `second-brain/wiki/CTA/signal-YYYY-MM-DD.md` | wiki-claim-v1 |
| 盘前叙事 | `second-brain/raw/desk/…`（默认 `tradable: false`） | desk-note-v1 |
| 断言页 | `second-brain/wiki/**` | wiki-claim-v1 |
| 回测 | cta-path-a 周回测输出 | cta-backtest-v1 |

## 品种代码

只用大写：`JD JM CF SR RU MA`。

## 冲突优先级

1. 以 `raw/` 与 cta-path-a archive 为准。
2. 冲突页标 `Status: disputed` 并问磊，禁止静默覆盖。

## 协作方

- Cursor 与 GrokBot 用同一套 schema_version 与路径，不各写各的。
- OBS vault 镜像 second-brain，不另建平行目录。
- 云电脑共享研究台 `/workspace/desk/project-log/` 作为来源，按 desk-note-v1 映射进 `raw/desk/`（只增不改）。
- 无 Notion API 时，待同步项记在 `wiki/_index/notion-sync-pending.md`。
