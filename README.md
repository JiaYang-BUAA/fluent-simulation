# Fluent 仿真与验证 · fluent-simulation

A Chinese-language Codex skill for planning, running and checking Ansys Fluent simulations.

适合三种请求：只有几何时拟定计算方案；已有 Fluent 算例时执行、诊断与续算；已有结果时判断某项工程结论是否成立。

| 从哪里开始 | 能得到什么 |
|---|---|
| [开算方案与估时](references/preflight.md) | 确认初始条件和边界，选择物理模型，给出三档网格、资源与墙钟耗时的估算依据。 |
| [运行、调度与恢复](references/execution.md) | 区分可并行的工况和必须串行的步骤；核对检查点，按需监控长作业，验收结束后停用监控。 |
| [传热专项验收](references/thermal-validation.md) | 分开判断换热量、两侧压降和壁温；瞬态还要核查储能、时间步与周期。 |

## 安装与使用

把本仓库放到 Codex 的个人技能目录，文件布局应为 `skills/fluent-simulation/SKILL.md`。例如在 PowerShell 中：

```powershell
$root = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME '.codex' }
git clone https://github.com/JiaYang-BUAA/fluent-simulation.git (Join-Path $root 'skills/fluent-simulation')
```

若同名技能已存在，请先比较内容。安装后在新任务中使用：

> 用 $fluent-simulation 检查这个换热芯的 STEP 和工况表，先别开算。推荐模型，比较三档网格、资源和预计时间。

> 用 $fluent-simulation 审阅已有粗细网格结果，分别判断换热量、热侧压降和最高壁温的变化能否分辨。

仅做规划和审阅无需启动 Fluent。真实求解需要单独提供 Fluent、许可证和兼容的 PyFluent、MCP 或 Journal 执行途径。仓库包含技能说明和教学示例，不包含生产算例或经实验验证的基准。

技能入口：[SKILL.md](SKILL.md)。工作流组织参考 [cavoiie/fluent-cfd-skill](https://github.com/cavoiie/fluent-cfd-skill)，执行接口参考 [Ansys 官方 PyFluent MCP](https://github.com/ansys/pyfluent-mcp)。本项目为独立社区技能。
