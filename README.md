# lody-baka-dev-team

编排者团队的 6 个角色提示词。

## 团队与角色

### 编排者团队

| 角色 | 描述 | 版本 | 文件 |
|---|---|---|---|
| 编排者 | 开发流水线的调度者：意图卡→六段任务书→派发→收结果→门禁→汇报。不写代码、不判 PASS。 | rev 25 | [`orchestrator.md`](roles/orchestrator.md) |
| 调查员 | 只读取证：产出带文件行号和来源的证据包，未知项标 UNKNOWN。不写文件、不提方案、不派活。 | rev 6 | [`investigator.md`](roles/investigator.md) |
| 建造者 | 唯一写者：按六段任务书和路径白名单做最小实现，提交分支，给出 diff、SHA、自测证据。不合并、不发布。 | rev 11 | [`builder.md`](roles/builder.md) |
| 审查者 | 只读审查：两轴看 diff，输出 P0/P1/P2 加证据，只能 BLOCK 不能放行。不写代码、不跑验收。 | rev 12 | [`gate-reviewer.md`](roles/gate-reviewer.md) |
| 放行者 | 唯一放行者：在干净提交上原样跑冻结验收命令，输出 PASS/FAIL/INCONCLUSIVE 加命令、输出、环境。不改代码。 | rev 16 | [`verifier.md`](roles/verifier.md) |
| 运维执行者 | 按需运维：只在发布、回滚、服务器变更或事故时启用。无备份、无回滚方案不动手。不参与日常写代码。 | rev 9 | [`operator.md`](roles/operator.md) |

## 目录结构

```text
README.md
manifest.json        机器可读清单（含每个角色的版本与文件名）
roles/               每个角色一份 Markdown，正文是完整提示词
teams/               团队清单
```

## 更新方式

角色定义保存在 Lody 的 Agent Role 里。修改后用 `lody agent-role get <id> --json`
重新导出，再运行生成脚本覆盖本仓库。不要直接改 `roles/*.md`，会被下次导出覆盖。
