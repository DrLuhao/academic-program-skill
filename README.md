# 科研项目管理 Skill

academic-program 用于维护科研工作区、当前研究状态、实验记录和论文证据链。按任务加载信息，避免每次工作都重新初始化或读取全部研究历史。

## 文档策略

| 项目情况 | 默认入口 |
| --- | --- |
| 一次性咨询或分析 | 不强制创建文档 |
| 小型持续项目 | AGENTS.md：稳定约定，可附简短当前工作 |
| 持续科研项目 | AGENTS.md：稳定约定；PROJECT.md：当前研究状态 |
| 已有项目 | 复用现有入口，兼容旧三文档，不自动迁移 |

AGENTS.md 只列关键目录、运行/验证入口和项目特有约束。PROJECT.md 保存目标、阶段、近期任务、阻塞及证据链接。详细实验和历史计划独立保存，按需读取。

已有 AGENTS.md 保留原指令；迁移时检查内容与链接，不擅自搬动数据或删除旧文件。

## 工作区与上下文

- 沿用已有目录；新项目按需使用 code/、data/、work/、docs/experiments/、outputs/runs/、paper/、references/。
- 临时文件放 work/；实验使用唯一 run-id，不覆盖重跑。
- 每个实验维护一份全过程文档，覆盖重跑、失败修正和结论；收尾清理已核实无后续用途的冗余中间文件，保留原始数据、最终成果和必要证据。
- 原始数据只读，共享大数据不复制；源码和计划采用稳定文件名。
- 先定位再读取；不默认扫描全部日志、数据和历史；只更新实际变化的文档。
- 普通代码解释、单次润色、一般科研问答不自动触发。

## 科研质量与绘图

保留输入校验、防泄漏、真值来源、失败记录和论文主张边界。区分程序完成、验证通过与科学结论成立。复用已有记录工具，不强制新建台账。

科研图默认简洁英文、Times New Roman、放大字体并检查不重叠或裁切；图像只输出 PNG，不额外输出 PDF 等格式。保留复现所需代码、配置和数据。用户明确要求优先。

## 安装或更新

在仓库根目录执行以下 PowerShell，将文件同步到目标目录（保留目标其他文件）：

~~~powershell
$skillTarget = Join-Path $env:USERPROFILE '.codex\skills\academic-program'
New-Item -ItemType Directory -Force -Path $skillTarget | Out-Null
Copy-Item -Path '.\academic-program\*' -Destination $skillTarget -Recurse -Force
~~~

## 使用示例

- 使用 academic-program 整理这个科研项目，复用已有入口，不搬动原始数据。
- 使用 academic-program 规划这个假设的实验，先不运行代码。
- 使用 academic-program 总结这次实验，更新当前状态和证据链接。
- 使用 academic-program 将旧三文档整理为 AGENTS.md 和 PROJECT.md，保留全部约束和证据。

## 仓库结构

~~~text
academic-program/
  SKILL.md
  agents/openai.yaml
  references/project-doc-templates.md
  references/experiment-evidence.md
~~~

正文负责任务分流与硬约束，模板和实验细则按需加载。文档数量和长度是手段，实际 token 收益需通过真实任务对比验证，不承诺固定节省比例。
