---
name: bobo-research-evidence
description: Offline evidence assembler and report gates for horizontal/vertical research. Use after a research plan and verified sources exist, when the user needs claim ledgers, timelines, cross-sectional matrices, gap disclosure, or a formal deep-research report. Does not search the network itself.
---

# Bobo 横纵证据整理

离线证据整理器：在已有研究计划与核验来源后，过结构闸门再写正式报告。本技能**不联网**；搜索与打开原文须事先完成。

## 何时使用

- 已有 `plan_id` 绑定的计划与候选 envelope，需要主张账本、时间线、横截面矩阵、横纵交汇、三情景或缺口披露。
- 用户要求正式深度研究报告，而不是搜索摘要。

计划阶段请先用配套技能 `bobo-research-plan`。

## 流程

1. 完整阅读 [references/hengzong-research.md](references/hengzong-research.md)。
2. 搜索结果只是候选；只有打开原文并逐主张核对后才标 verified。
3. 写作前组装 bundle（canonical plan、envelopes、annotations、claims、retained gaps），运行：

   ```bash
   python3 scripts/assemble_hengzong_evidence.py --bundle -
   ```

4. 仅当 `scope_complete`、逐 workstream 基础 claim、非空 timeline、非空 cross-sectional matrix、覆盖与矛盾处理、横纵交汇与三情景等结构门全部满足时，才写正式报告。
5. `supports` / `contradicts` 链接必须含 `locator`、`event_date`、`scope`。普通缺口为 `blocking`；仅在同一缺口完成至少两条不同补搜并给出 `impact` / `disclosure` / `bounded_conclusion` 时，才可 `ready_with_disclosure`。

执行摘要见 [references/hengzong-execution-contract.md](references/hengzong-execution-contract.md)。

## 输出

正式报告至少含：范围与方法、纵向时间线、横向结构矩阵、横纵交汇、三情景（horizon / triggers / invalidators）、证据缺口披露。行业研究且 goal 含未来或机会时，须含非空 `opportunity_map`。

## 安全

- 脚本纯离线、无密钥、不发网。
- 不打印或保存 Cookie、Token、API Key、登录凭证。
- 只读；不发帖、不改账号状态；不绕过登录墙或付费墙。

## 归属

横纵协议受 `hv-analysis`（作者：数字生命卡兹克）启发并扩展；参考提交 `7a5c4934be4106ac740ffdb95280bb81b3f4b83c`。详见 `THIRD_PARTY_NOTICES.md`。本技能由 bobo 维护。
