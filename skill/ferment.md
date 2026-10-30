# ferment.md — 发酵日志（laomian-mantou 自治理）

> 只追加，不覆盖。格式：`[YYYY-MM-DD] 场景 | 教训一句话`
> 蒸馏后在条目末尾标记 `[已蒸馏→SKILL.md]`。

[2026-10-30] claude 侧索引插行后消失 | claude 索引由 ~/.claude/skills/ 目录自动重生，手工插行会被刷掉；正确做法是先补技能软链再插行
[2026-10-30] write_file 覆盖已有 starter.md 被拒 | write_file 要求先读全文才能覆盖（防 stale 覆盖）；流程写明"留种前先 read_file 再 write_file"
[2026-10-30] hermes cron show 报不是子命令 | cron 验证用 hermes cron list（show 不存在）；建 job 用 cron create，改 prompt 用 cron edit --prompt
[2026-10-30] MCP 计划工具多轮持续不可用 | 长任务依赖单点工具（ekko update_plan）会整轮卡住；协议流程不应硬依赖任一可选工具，降级为文字汇报即可

