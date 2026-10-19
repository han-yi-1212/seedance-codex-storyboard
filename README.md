# 🎬 seedance-codex-storyboard

> **专为 Seedance 视听创成平台与 Codex 自动化管线深度打造的 AI 电影级商业短剧视听导演系统（v6.0）**  
> 全面直通 **Seedance** 视频生成/神经音频渲染管线，深度适配 **Codex** 智能体工作流编排与代码级批量分发。全面兼容任意海外短剧题材（都市豪门、虐恋情仇、悬疑动作、狼人奇幻、女性复仇、职场商战等），以输入剧本为主干底料，实现从文学叙事到机器物理指令的“零返工级工业编译”。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Dedicated for](https://img.shields.io/badge/Dedicated-Seedance%20%26%20Codex-blue.svg)]()
[![Version](https://img.shields.io/badge/Version-6.0.0-green.svg)]()

---

## 🚀 一、双核心架构：为 Seedance 与 Codex 量身定制

### 1. 面向 Seedance（视听创成与渲染落地点）
- **镜头级物理约束与防肢体融化（Anti-Morphing）**：单镜头严格控制在 ≤ 2.0 秒（黄金 0.8s ~ 1.8s），契合扩散模型最佳稳定渲染区间。
- **声画错位（J/L-Cut）与防假人口型（Anti-Bleeding Lipsync）**：杜绝听者特写误套口型的“腹语术”翻车，精确标注“画内同步口型”与“听者闭口听”。
- **180° 轴线与视线几何锁死**：正反打强制标注机位视线同侧与左右朝向，杜绝切镜颠倒与视线乱飞。
- **母带级三层纯净分轨**：剥离未授权 BGM 污染，只保留【对白 + 微拟音 Foley + 环境底噪 Ambience】。

### 2. 面向 Codex（自动化管线与 Agent 编排中枢）
- **机用高可解析性**：采用标准的“大镜头组（Master Shot Group）+ 十维标准化工程字段”，Codex Agent 可无损切片、参数提取与批量接口分发。
- **自动化生成质检清单（Redline Checklist）**：内置轴线、视线、口型、道具守恒、时长等自动化质检红线，支持 Codex 进行全闭环自动测试与校验。

---

## 🌟 二、全球海外商业短剧爆款五大法则

本系统全面继承并升维了商业短剧的视听工业密码，确保生成的剧本具备最高级别的用户留存与商业转化：

### 1. 全题材自适应：黄金 3 秒视觉首因法则（Visual Hook First）
- **破除小说慢热流水账**：海外短剧前 3 秒划走率高达 70%，杜绝平铺直叙的背景介绍、端坐喝茶或长篇内心独白。
- **题材自适应匹配开局强钩子**：
  - *动作/危机题材*：危机前置、极限倒计时或高能悬念误导；
  - *情感/虐恋题材*：高压对峙爆发点前置、身份差撕裂对撞、或尊严被践踏的关键时刻；
  - *悬疑/反转题材*：反常视觉奇观、关键证物特写、或失控现场。

### 2. 身份与情境的多维反差（Dynamic Contrast）
- 深挖输入剧本中角色身上的内在戏剧张力，将其转化为可见的画面对比：
  - *角色双重身份反差*（如：高高在上的权势外壳 vs 私下深情脆弱的裂纹）；
  - *空间与阶级反差*（如：奢靡顶层的权力中枢 vs 冰冷残酷的现实生存困境）；
  - *情绪反差*（如：表面礼貌克制的心如止水 vs 皮肤之下暗流涌动的狂暴欲望）。

### 3. 人物张力与情感的身体物理外化（Physicality & Chemistry）
- 拒绝平淡站桩对话，将关系具象为“物理空间与肉体动作”：
  - 空间距离的侵略、逼近与退守；
  - 有力量感与阻尼感的肢体接触、受力失衡、衣料摩擦压痕；
  - 生理层级的微反应：呼吸频率骤变、咬肌紧绷、喉结吞咽、瞳孔骤缩。

### 4. 高密度戏剧推进与全剧 20 多集精炼重构（High-Density Episodic Pacing）
- **严禁单一事件注水**：每集 1:30 拒绝拖沓慢热，必须包含 2~3 个完整的戏剧反转与实质性推进。
- **全剧 20 多集精品体量**：将原本 40~50 集碎片化长篇网络剧本，以 2:1 或 2.5:1 的高密度压缩法，重构成 20~24 集的美剧级强情节精品短剧。

### 5. 严苛的好莱坞工业视听规范
- **置顶《全片统一视觉规范》**：角色统一、摄影风格、光影逻辑（冷暖色温分割）、表演规范（红线禁令）。
- **十维标准化分镜字段**：场景、景别、机位、拍摄角度、运镜、画面动作表演、【对白/口型】、【语气/发声】、光影、音效。
- **双语战略**：纯英文对白/画外音（每秒 ≤ 3.5 词精确口型契合） + 专业中文导演视听提示词。

---

## 📂 三、项目结构与七大知识库导航

```
seedance-codex-storyboard/
├── README.md                                # 项目总览与工业规范说明
├── examples/
│   └── ai_call_showcase.md                  # 商业级实战示范案例
└── skills/
    └── ai-video-storyboard/                 # 核心 Skill 模块
        ├── SKILL.md                         # v6.0 System Prompt（Seedance & Codex 专属）
        └── references/
            ├── ai_production_execution_guide.md # 1. Seedance & Codex 视听工程落地执行指南
            ├── short_drama_hook_matrix.md       # 2. 短剧开局强钩子与黄金三秒法则
            ├── cinematic_language_guide.md      # 3. 影视视听语言与景别运镜速查
            ├── director_visual_engines.md       # 4. 对话场景6大视觉引擎与20位大师导演风格
            ├── prompt_engineering_guide.md      # 5. 现代 AI 视频提示词工程与 I2V 管线手册
            ├── validation_checklist.md          # 6. 自动化七项深度规则自检与 13 项验收标准
            └── storyboard_schema.json           # 7. 工业级单镜头数据结构 JSON Schema 规范
```

---

## 📄 四、开源许可

本项目基于 [MIT License](LICENSE) 许可开源。
