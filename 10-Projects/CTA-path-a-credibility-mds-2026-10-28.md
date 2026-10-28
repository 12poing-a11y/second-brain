# CTA Path-A · 可信度门禁 + MDS 情绪纸面袖套

- **date**: 2026-10-28
- **status**: paper-only / no live
- **claim**: 正式日/回测产物受 ATR·日历门禁；ChatGPT 情绪策略落地为 MDS+EHI 纸面对照，不改 Path-A 手数。
- **source**: `cta-path-a` (`research_quality.py`, `sentiment_mds.py`); pytest 8 passed; ChatGPT share t_6ae1fabe…
- **evidence**: confirmed (code + local tests)

## Snapshot

- Paper book asof 2026-10-27: V long / EB long / MA long / FG short
- Observe sleeve: AU / CU / AL / NI / I / JM / SS
- GitHub: https://github.com/12poing-a11y/cta-path-a/tree/cursor/streamlit-research-desk
- PR: https://github.com/12poing-a11y/cta-path-a/pull/3
- Notion card: https://app.notion.com/p/407ca62ab5a78194bc06de45f1540c2a

## Next

1. Next weekday `daily_update` refreshes `ret_1d` sentiment snapshot
2. Merge PR#3 → main so Actions run pytest + quality gate
3. Full signals/trades DB sync via CI `NOTION_TOKEN` (local token not set)
