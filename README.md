# 🥟 laomian-mantou — 老面馒头技能治理（Sourdough Skill Governance）

> 把技能（SKILL.md）当作活的面团，而不是一次性写完的静态文件。
> 灵感来自老面馒头（sourdough steamed bun）的制作原理：留老面、自然发酵、兑碱防酸、留种传代。

**English tagline**: Treat skills as living dough — progressive fermentation, distillation, anti-bloat gates, and seed preservation for AI agent skills (SKILL.md format, works with Claude Code / Codex / Cursor / OpenClaw / Hermes / OpenCode and any skills-compatible runtime).

## 核心思想

| 老面馒头 | 技能治理 |
|---|---|
| **老面（面起子）**：上锅留一小块发面作下批菌种 | `starter.md` 留种：<30 行最小可传承内核，技能腐化后可从种子恢复 |
| **发酵**：经验在池子里攒着，急不来 | `ferment.md` 追加式经验池，单次踩坑不直接改 SKILL.md |
| **蒸馏**：攒够同类才合并 | 同类经验 ≥3 条 → 蒸馏成 1 条通用规则进 SKILL.md |
| **兑碱**：发过头会酸 | 兑碱门：>300 行 / description 过宽 / 软化措辞 → 强制修剪 |
| **醒面**：成型后静置再蒸 | 改完跑真实任务验证才定稿 |
| **留种**：每锅蒸熟后留种 | 每次蒸馏后同步重写 starter.md，防止恢复点过时 |

## 仓库结构

```
skill/
├── SKILL.md      # 技能本体：五步循环 + 失败模式 + 反例黑名单
├── starter.md    # 种子模板（<30 行，蒸馏后必更新）
└── ferment.md    # 发酵日志模板（只追加，不覆盖）
```

将 `skill/` 目录复制进你的 agent 技能目录（如 `~/.claude/skills/laomian-mantou/`、`~/.hermes/skills/laomian-mantou/` 等）即可使用。

## 使用方式（触发词）

| 你说 | 它做 |
|---|---|
| 喂老面 / 记个经验 | 追加一条经验到目标技能的 ferment.md |
| 蒸馒头 / 蒸馏 | 同类 3 条合并成 1 条规则进 SKILL.md（CHECKPOINT 确认后） |
| 留种 | 重写 starter.md |
| 技能酸了 / 膨胀了 | 跑兑碱门检查并修剪 |
| 技能坏了 / 恢复 | 从 starter.md 恢复重写 SKILL.md |

English triggers also work: `feed the starter`, `distill`, `save seed`, `skill is bloated`, `restore skill from seed`.

## 五步循环

1. **喂养（喂老面）**：使用技能中踩坑/被纠正 → 追加一行进 ferment.md，不立即改 SKILL.md
2. **蒸馏（蒸馒头）**：同类经验 ≥3 条 → 合并成 1 条规则 patch 进 SKILL.md，原条目标记 `[已蒸馏→SKILL.md]`
3. **兑碱门**：SKILL.md >300 行 / description >500 字符 / 软化措辞 ≥2 处 → 修剪
4. **醒面**：改完跑真实任务或用你喜欢的评估器（如 darwin-skill）复评，不降才保留
5. **留种**：重写 starter.md（<30 行），对照技能原始目标

## 反哲学（为什么不用别的方式）

- ❌ 单次经验直接写进 SKILL.md → 规则打架、技能膨胀（面酸了）
- ❌ 覆盖/删除经验日志 → 丢审计证据
- ❌ 种子多代复制不回炉 → 传代退化
- ❌ 范围外经验喂进来 → 杂菌污染

## 兼容性

纯 Markdown 协议，无脚本依赖、无平台绑定。任何支持 SKILL.md 约定（name + description frontmatter）的 agent runtime 均可加载。

## License

MIT
