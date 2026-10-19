# 🎬 seedance-codex-storyboard

> **专为 Seedance 视听创成平台与 Codex 自动化管线深度打造的 AI 电影级商业短剧视听导演系统（v6.0）**  
> 全面直通 **Seedance** 视频生成/神经音频渲染管线，深度适配 **Codex** 智能体工作流编排与代码级批量分发。核心实现从文学剧本到机器渲染指令的“零返工级工业编译”。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Dedicated for](https://img.shields.io/badge/Dedicated-Seedance%20%26%20Codex-blue.svg)]()
[![Version](https://img.shields.io/badge/Version-6.0.0-green.svg)]()

---

## 🚀 双核心架构：为 Seedance 与 Codex 量身定制

### 1. 面向 Seedance（视听创成与渲染落地点）
- **镜头级物理约束与防肢体融化（Anti-Morphing）**：单镜头严格控制在 ≤ 2.0 秒（黄金 0.8s ~ 1.8s），契合扩散模型最佳稳定渲染区间。
- **声画错位（J/L-Cut）与防假人口型（Anti-Bleeding Lipsync）**：杜绝听者特写误套口型的“腹语术”翻车，精确标注“画内同步口型”与“听者闭口听”。
- **180° 轴线与视线几何锁死**：正反打强制标注机位视线同侧与左右朝向，杜绝切镜颠倒与视线乱飞。
- **母带级三层纯净分轨**：剥离未授权 BGM 污染，只保留【对白 + 微拟音 Foley + 环境底噪 Ambience】。

### 2. 面向 Codex（自动化管线与 Agent 编排中枢）
- **机用高可解析性**：采用标准的“大镜头组（Master Shot Group）+ 十维标准化工程字段”，Codex Agent 可无损切片、参数提取与批量接口分发。
- **自动化生成质检清单（Redline Checklist）**：内置轴线、视线、口型、道具守恒、时长等自动化质检红线，支持 Codex 进行全闭环自动测试与校验。

---

## 📂 项目结构

```
seedance-codex-storyboard/
├── README.md                                # 项目总览与工业规范说明
├── examples/
│   └── ai_call_showcase.md                  # 商业级实战示范案例
└── skills/
    └── ai-video-storyboard/                 # 核心 Skill 模块
        ├── SKILL.md                         # v6.0 System Prompt（Seedance & Codex 专属）
        └── references/
            ├── ai_production_execution_guide.md # 视听工程落地执行指南
            ├── cinematic_language_guide.md      # 视听语言与景别速查
            └── short_drama_hook_matrix.md       # 短剧钩子与黄金三秒法则
```

---

## 📄 开源许可

本项目基于 [MIT License](LICENSE) 许可开源。
