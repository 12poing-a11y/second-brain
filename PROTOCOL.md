# 三角色协议（Argona / Karpathy Second Brain）

来源启发：https://x.com/Argona0x/status/2111837226006921640  

核心：**第二大脑会自信地记错东西** → 必须分职，且每条知识可追溯。

## 三个角色（不要混在一个 agent 里乱改）

| 角色 | 做什么 | 绝不能做 |
|------|--------|----------|
| **Reader** | 把链接/PDF/语音/对话结论放入 `raw/`，只增不改 | 改 wiki、下结论覆盖旧页 |
| **Librarian** | 根据新 raw 更新相关 `wiki/` 页（常一次动 若干页） | 删改 raw；无来源就写断言 |
| **Checker** | 夜间/周日查：矛盾、过期、孤儿页；矛盾时**提问**而不是静默覆盖 | 自行“修好”有争议的事实 |

## 每页 wiki 必须露出三字段

```text
Claim:     （一句话断言）
Source:    （raw/ 路径或 Notion/URL）
Confirmed: （YYYY-MM-DD，最后一次被新来源确认）
Status:    confirmed | unconfirmed | disputed
```

- 超过 **30 天**无新来源触及 → `unconfirmed`
- 新来源与旧页冲突 → `disputed`，@你确认，禁止静默覆盖
- 你问出一个好答案 → Librarian **回写**成 wiki 页（大脑因使用而增长）

## 角色怎么落到你现有栈

| 角色 | 谁跑 | 写哪里 |
|------|------|--------|
| Reader | 你 / Cursor / Grokbot 投喂 | `raw/` + Notion Inbox |
| Librarian | Cursor（整理会话）或 Grokbot | `wiki/` + Notion 卡片备注 |
| Checker | 周日例行（与 CTA 周回测同日） | 产出 `wiki/_checks/` 报告 |

## 范围纪律（帖子原话：先做一个主题）

当前唯一深耕主题：**中国商品期货 · CTA 路径A**  

其它主题只进 Inbox/raw，不建完整 wiki，直到 CTA 闭环稳定。

## 补充（2026-10-20）：Planner 与团队映射

| 角色 | 团队成员 | 职责 / 写哪里 |
|------|----------|---------------|
| Planner | 首席幕僚 | 编排派单，不直接写 wiki |
| Reader | 小秘 | 来源 → `raw/` + Inbox |
| Librarian | 小G | `wiki/` 断言页 |
| Checker | 小N | `wiki/_checks/`，冲突标 disputed |
| 周日 Checker 审计 | 复盘官 | 每周 `wiki/_checks/YYYY-MM-DD-check.md` |

### 回复开头（强制）

```text
角色: Reader|Librarian|Checker|Planner
拟改文件: …
需要你确认: 是/否 + 问题
```

### schema_version

`desk-note-v1`（raw/desk，默认 tradable=false）· `wiki-claim-v1` · `cta-signal-v1` · `cta-backtest-v1`。路径与合并规则见 [`wiki/_index/merge-map.md`](./wiki/_index/merge-map.md)。

### 安全边界

未经磊确认：不删文件、不 force-push、不改 Secrets、不联系外部人或发帖、不下单。改 cta-path-a 代码或 Actions 前先征得同意。
