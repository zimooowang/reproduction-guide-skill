# Reproduction Guide Skill

English | [中文](#复现指南-skill)

`reproduction-guide` is a Codex skill for creating evidence-driven reproduction guides for machine learning papers, models, benchmarks, datasets, and open-source research projects.

It is designed for cases where a user wants more than a paper summary: the output should define what is actually reproducible, map public evidence to implementation components, expose unknowns, and end with a concrete first action.

## What It Does

- Builds a reproducibility boundary from public evidence.
- Classifies the project type before choosing modules to analyze.
- Avoids assuming RL, agents, rollouts, rewards, verifiers, SFT, or distributed training unless the project actually uses them.
- Maps official artifacts, related papers, and third-party code into an engineering plan.
- Splits reproduction into levels from "run released artifacts" to "research-grade training reproduction".
- Audits generated guides for unsupported claims and over-specific assumptions.
- Tailors a full guide to the user's compute, time, codebase, and skill constraints.

## Workflow

The skill follows an A/B/C workflow:

1. **Full map**: generate a complete evidence-driven reproduction guide.
2. **Audit**: remove unsupported claims, missing validation, and category assumptions.
3. **Tailor**: convert the full guide into an executable plan for the user's actual constraints.

The final tailored output should end with exactly one first action: a file, command, expected output, and success flag.

## Installation

Copy this folder into your Codex skills directory:

```bash
cp -R reproduction-guide ~/.codex/skills/
```

Then invoke it explicitly:

```text
Use $reproduction-guide to create an evidence-driven reproduction guide for this paper or open-source ML project.
```

## Repository Layout

```text
reproduction-guide/
├── SKILL.md
├── README.md
└── agents/
    └── openai.yaml
```

## Example Prompts

```text
Use $reproduction-guide to build a reproduction guide for this paper. Focus on what can be reproduced with one 24GB GPU.
```

```text
Use $reproduction-guide to audit this reproduction plan and remove unsupported assumptions.
```

```text
Use $reproduction-guide to tailor the full reproduction plan to my current repo and hardware.
```

## License

Add an open-source license before publishing if you want others to reuse, modify, or redistribute this skill.

---

# 复现指南 Skill

[English](#reproduction-guide-skill) | 中文

`reproduction-guide` 是一个用于生成机器学习论文、模型、benchmark、数据集和开源研究项目复现指南的 Codex skill。

它适合用户需要的不只是论文总结，而是一份可执行的工程复现方案：明确哪些内容真的可复现，把公开证据映射到实现组件，暴露未知项，并给出一个可以立即开始的具体动作。

## 它能做什么

- 基于公开证据界定可复现边界。
- 先判断项目类型，再决定需要分析哪些模块。
- 不默认假设项目一定包含 RL、Agent、rollout、reward、verifier、SFT 或分布式训练，除非证据表明项目确实使用了这些机制。
- 将官方产物、相关论文和第三方代码映射成工程实施计划。
- 将复现目标拆分为多个层级，从“运行已发布产物”到“研究级训练复现”。
- 审计生成的复现指南，找出缺少证据的断言和过度具体的假设。
- 根据用户的算力、时间、代码基础和技术水平裁剪出可执行版本。

## 工作流

这个 skill 使用 A/B/C 三阶段流程：

1. **完整地图**：生成一份证据驱动、结构完整的复现指南。
2. **审计修正**：移除无证据断言、缺失验证和项目类型误判。
3. **个人裁剪**：根据用户的真实约束，把完整指南变成可执行计划。

最终裁剪后的输出应当只以一个第一步动作结尾：对应文件、命令、预期输出和成功标志。

## 安装

把这个目录复制到你的 Codex skills 目录：

```bash
cp -R reproduction-guide ~/.codex/skills/
```

然后显式调用：

```text
Use $reproduction-guide to create an evidence-driven reproduction guide for this paper or open-source ML project.
```

也可以用中文调用：

```text
使用 $reproduction-guide 为这篇论文生成一份证据驱动的复现指南。
```

## 仓库结构

```text
reproduction-guide/
├── SKILL.md
├── README.md
└── agents/
    └── openai.yaml
```

## 示例提示词

```text
使用 $reproduction-guide 为这篇论文生成复现指南，重点说明单张 24GB GPU 能复现到什么程度。
```

```text
使用 $reproduction-guide 审计这份复现计划，删除缺少证据支持的假设。
```

```text
使用 $reproduction-guide 根据我当前的仓库和硬件条件裁剪完整复现方案。
```

## 许可证

如果希望他人复用、修改或再发布这个 skill，请在正式开源前添加 LICENSE 文件。
