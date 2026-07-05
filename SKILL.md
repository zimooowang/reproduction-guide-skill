---
name: reproduction-guide
description: Create, audit, or tailor evidence-driven reproduction guides for machine learning papers, models, benchmarks, datasets, and open-source research projects. Use when the user asks for a reproducibility guide, reproduction plan, paper/code reproduction roadmap, implementation checklist, experiment reconstruction, audit of a reproduction guide, or a personalized executable plan under specific compute/time constraints.
---

# Reproduction Guide

## Core Rule

Build an engineering evidence chain, not a generic paper summary:

`reproduction guide = reproducible boundary + method abstraction + evidence chain + component mapping + implementation route + validation protocol + risk register + first executable step`

Do not assume the project contains reinforcement learning, agents, SFT, rewards, rollouts, verifiers, distributed training, or any other mechanism. First classify the project from evidence, then include only the modules that apply.

## Workflow

Use the A/B/C sequence unless the user asks for only one stage:

1. **A - Full map**: Generate the complete evidence-driven reproduction guide.
2. **B - Audit**: Remove unsupported claims, over-specific assumptions, and missing validation.
3. **C - Tailor**: Convert the guide into the user's executable plan under their hardware, time, code, and skill constraints.

If the user only supplies a paper title or project name, gather or request enough inputs to avoid inventing details. Prefer current primary sources: paper, appendix, official repository, model/data cards, project docs, author issues, release notes, and official benchmark pages.

## Stage A: Full Reproduction Guide

### 1. Collect Inputs

Capture these fields when available:

- Project or paper name
- Paper, homepage, official repository, model, dataset, or benchmark links
- Target reproduction scope: run model, reproduce evaluation, minimal method reproduction, full training reproduction, migration or extension
- User's base model, framework, codebase, hardware, time budget, skill level, current progress, and special concerns

When fields are missing, proceed with explicit assumptions only if low risk. Otherwise ask a concise question.

### 2. Classify Project Type

Identify what kind of work this is before designing the guide. Common categories include:

- LLM or multimodal model
- Vision, language, speech, video, generative, diffusion, or flow model
- RL, post-training, alignment, agent, tool-use, or code-intelligence system
- World model, VLA, robotics, detection, segmentation, tracking, or 3D vision
- Compression, distillation, quantization, pruning
- Dataset, benchmark, training system, inference system, or evaluation framework

State which modules are applicable and which are not.

### 3. Define Reproducible Boundary

Start with the reproduction conclusion rather than background. Separate:

- What is officially released
- What is described but not released
- What can be reconstructed from related work
- What cannot be reproduced reliably from public evidence
- Which reproduction level is realistic for the user

Mark unknowns clearly. Do not turn guesses into facts.

### 4. Explain Method Mechanism

Compress the method into a short computational flow:

- Input and output
- Core model or system components
- Training, inference, data, retrieval, planning, control, or evaluation loop, only when applicable
- Key losses, objectives, rewards, prompts, policies, metrics, or protocols, only when applicable
- What is new relative to prior work

Explain formulas and objectives in implementable language. If an equation or design detail is not public, say so and propose a measurement or reconstruction strategy.

### 5. Build Evidence Chain

Organize sources by trust level:

1. Official paper, appendix, technical report
2. Official GitHub, model repository, dataset card, documentation, configs, scripts, issues
3. Author talks, blogs, demos, release notes
4. Closely related papers and upstream methods
5. Third-party reproductions or implementations

For each important claim, attach source evidence or label it as an inference. For each external implementation, explain what component it helps reproduce and what gap remains.

### 6. Map System Components

Break the system by function, not by project popularity. Depending on applicability, map:

- Data format and preprocessing
- Model architecture
- Training objective
- Inference or decoding path
- Agent/tool-use loop
- Reward, verifier, rollout, simulator, or environment
- Evaluation benchmark and metric computation
- Distributed training, serving, or infrastructure

For each component, state: role, required inputs/outputs, official availability, substitute implementation, and validation method.

### 7. Define Reproduction Levels

Use levels that make partial success meaningful:

- **Level 1: Run reproduction** - load released artifacts and run an example.
- **Level 2: Evaluation reproduction** - reproduce reported metrics or benchmark protocol.
- **Level 3: Minimal method reproduction** - implement the core idea with controlled simplifications.
- **Level 4: Full training or research-grade reproduction** - recreate training pipeline, data, objective, and evaluation as far as public evidence permits.
- **Level 5: Migration or extension** - adapt the method to the user's task, data, or codebase.

For every level, give goal, prerequisite, implementation actions, success signal, and likely failure mode.

### 8. Design Implementation Route

Write a dependency-ordered plan. Each step must include:

- Theory target
- Engineering action
- Files or modules to create or inspect
- Command or pseudocode when useful
- Expected intermediate artifact
- Verification criterion
- Fallback if the step fails

Start from a minimal runnable path before scaling to full training.

### 9. Provide Minimal Engineering Design

When useful, include:

- Minimal repository layout
- Core configuration fields
- Dataset schema or sample record
- Model input/output interface
- Training batch format
- Evaluation result format
- Minimal runnable script or command

Keep this concrete enough that the user can begin coding immediately.

### 10. Define Validation

Include:

- Benchmark or metric protocol
- Sanity checks for data, model, objective, and outputs
- Baselines: released model, simple baseline, no-core-component baseline, and core-component version
- Ablations that prove the component matters
- Acceptance criteria for running, correctness, learning signal, component effect, and interpretable benchmark results

### 11. Estimate Resources

Estimate GPU memory, disk, data volume, batch size, sequence length, training steps, wall time, and bottlenecks only when evidence supports it. Otherwise give a measurement procedure and scaling heuristic.

### 12. Register Risks

List:

- Missing artifacts
- Ambiguous algorithm details
- Data licensing or access limits
- Evaluation mismatch
- Compute bottlenecks
- Implementation traps
- Claims that depend on inference rather than direct evidence

Explain how to reduce each risk.

## Stage B: Audit A Reproduction Guide

When auditing a generated guide, produce:

- Overall credibility rating: high, medium, low, or not reproducible from public evidence
- Unsupported claims, with why they are unsupported
- Confused facts versus recommendations
- Over-assumptions such as unnecessary RL, Agent, reward, rollout, verifier, SFT, distributed training, or architecture-specific modules
- Missing modules: data, interfaces, baseline, ablation, resource budget, validation, failure modes
- The five most dangerous misunderstandings
- A corrected reproduction route

Only check reward, rollout, verifier, simulator, or agent-specific items when the project actually uses them.

## Stage C: Tailor To The User

Convert the full guide into the user's executable version:

- Choose the highest realistic reproduction level.
- List components to keep, remove, simplify, or replace.
- Provide a minimal system architecture.
- Give milestones with deliverables and success criteria.
- Recommend a code directory layout.
- Define core interfaces and data structures.
- Select minimal baselines and ablations.
- Estimate resources or define how to measure them.
- End with exactly one first action: file, command, expected output, and success flag.

Do not tell the user to start with full training unless the prerequisites are already satisfied.

## Output Standard

Write in a direct engineering style. Prefer tables for component maps, reproduction levels, source evidence, risks, and milestones. Use source links or file references when available. Keep uncertainty visible.

Avoid:

- Pure literature review without implementation path
- Uncited factual claims about unreleased code, data, or hyperparameters
- Structure for its own sake
- Treating one project category as the default for all ML work
- Ending with a vague recommendation instead of a concrete next step
