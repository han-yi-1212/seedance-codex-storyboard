# 现代 AI 视频提示词工程与多模态资产控制手册
*(Modern AI Video Prompt Engineering & Asset Control Manual V1.2.1)*

本文档详细说明当前主流 AI 图像与视频生成平台在工业分镜制作中的**真实官方语法、多模态一致性控制参数与 I2V（Image-to-Video）管线规范**。

---

## 一、工业级核心工作流：I2V（首帧生视频）标准管线

在现代工业化 AI 视频生产中，**Text-to-Video (T2V) 直接纯文本生视频已不是首选**，因为纯文字描述无法保证角色五官细节、特定服装和复杂空间在多镜头间的跨镜头守恒。

当前行业的主流解法为 **I2V (Image-to-Video) 工业流水线**：
```
[剧作分镜] ──► [Midjourney / Flux 渲染起始帧关键帧]
                     │ (绑定 --cref / --oref 角色参考与 --sref 风格参考)
                     ▼
             [获得高一致性 Keyframe 起始帧图片]
                     │
                     ▼
             [输入 Runway / Kling / MiniMax 进行 I2V 运镜与微动态驱动]
                     │ (应用官方 Camera Control 与首尾帧技术)
                     ▼
             [最大化抑制面容漂移与背景畸变，获得稳定分镜视频]
```

---

## 二、图像端：多模态角色与风格一致性规范

### 1. Midjourney 官方一致性参数演进

| 参数 | 适用版本 | 官方定义与工业用法 |
|---|---|---|
| `--cref [URL]` | **v6 主力** | **Character Reference (角色参考)**：传入角色的白底标准立绘或三视图 URL，锁定面部五官与骨骼轮廓。配合 `--cw [0-100]`（`--cw 100` 全包面容发型服装，`--cw 0` 仅锁定五官）。 |
| `--oref [URL]` | **v7 / 全能参考** | **Omni Reference (全能主体/对象参考)**：用于复杂主体、关键道具（如特定枪械、特定U盘）或全身角色的高保真锚定。 |
| `--sref [URL]` | **v6 / v7 通用** | **Style Reference (风格参考)**：传入目标影片的调色/光影参考图 URL，全剧镜头保持统一影调（配合 `--sw 0~1000`，推荐 `--sw 800`）。 |
| `--ar [比例]` | 通用 | **Aspect Ratio (画幅比例)**：横屏短剧统一 `--ar 16:9`；竖屏微短剧统一 `--ar 9:16`。 |
| `--style raw` | 通用 | **Raw Mode (原始摄影质感)**：消除 Midjourney 默认的过度平滑插画感，增强真实皮肤毛孔与胶片颗粒。 |

#### 标准生图 Prompt 结构示例：
```
Close-up portrait of East Asian man 25yo, messy black hair, pale skin with dark circles, worn dark hoodie, cold blue chiaroscuro lighting, cinematic film still, 35mm lens --ar 9:16 --style raw --cref https://asset.film/lin_chuan.png --cw 100 --sref https://asset.film/cyber_noir.png --sw 800
```

### 2. Flux 1.0 / SD 生态
- **PuLID / IP-Adapter FaceID**：通过人脸特征向量提取保持五官一致性（权重推荐 0.75~0.85）。
- **LoRA**：为定制主角训练专属 Character LoRA，在提示词中显式调用 `<lora:character_model:0.8>`。
- **ControlNet OpenPose / Depth**：用于精确控制特定分镜中角色的复杂构图与机位透视。

---

## 三、视频端：主流平台官方运动控制与运镜规范

### 1. Runway (Gen-3 Alpha / Gen-4)

Runway 官方提供了**控制面板运镜参数**与**文本 Prompt 自然语言控制**两种协同方式：
- **Camera Control 轴向参数**：
  - `Pan (水平平移)`：Left / Right
  - `Tilt (垂直俯仰)`：Up / Down
  - `Zoom (变焦推拉)`：In / Out
  - `Roll (轴向旋转)`：Clockwise / Counter-clockwise
  - `Camera Speed`：运镜运动幅度与速度调节
- **Prompt 运动描述工业规范**：
  在文本中明确写出摄影机动作与主体微动作，避免复合动作。
  *范例*：`Camera: Slow Zoom In (Speed 1), locked on subject. Subject: minimal breathing movement, eyes staring straight.`

### 2. 可灵 Kling (Kling 1.5 / 1.6 / 2.0)

可灵拥有最强大的三维运镜控制与首尾帧技术：
- **6 轴运镜模式**：
  - `水平平移 (X)`：[-10 到 +10]
  - `垂直平移 (Y)`：[-10 到 +10]
  - `前后变焦 (Z)`：[-10 到 +10]（推进取正，拉远取负）
  - `水平旋转 (Yaw)`：[-10 到 +10]
  - `垂直俯仰 (Pitch)`：[-10 到 +10]
  - `滚动旋转 (Roll)`：[-10 到 +10]
- **首尾帧过渡 (First & Last Frame)**：
  提供第一帧（起始姿态）与最后一帧（终止姿态），AI 在两帧之间生成严格受约束的物理运动插值（适合精准开门、拔卡、倒地等关键动作）。
- **元素控制 (Elements)**：在官方库中上传角色模型，保证生视频时最大程度抑制换脸。

### 3. 海螺 MiniMax (Hailuo 01/02) 与其他主流模型

海螺模型对**自然语言的动作动词**理解极深，忌讳机械堆砌参数词，必须采用精炼的**电影指令级动词**：
- **原则**：只描述可见物理动作与摄影机真实轨迹，严禁复合动作。
- *范例*：`Static camera. The man's eyes dart sharply to the right in sudden panic, breath freezing in his throat. Cold cyan lighting.`

---

## 四、镜头时长与台词配对工程准则

| 场景类型 | 默认时长区间 | 对应单镜台词字数上限 | 典型景别与运镜 |
|---|---|---|---|
| **悬念建立 / 环境交代** | 2.0s ~ 3.0s | ≤ 9 ~ 12 字（或无台词） | WS / ELS，缓慢推进 (Slow Push In) |
| **人物心理与微反应** | 1.5s ~ 2.0s | ≤ 6 ~ 8 字 | MCU / CU，固定 (Locked Static) |
| **突发危机与动作戏** | **1.0s ~ 1.5s (快切)** | ≤ 4 ~ 6 字（甚至无台词） | ECU / CU，极快动作或微距定格 |
| **结局余味 / 悬念留白** | 2.0s ~ 3.0s | ≤ 8 ~ 11 字（空灵留白） | MS / WS，缓慢拉远 (Dolly Out) 或定格 |

> [!IMPORTANT]
> **台词配对物理铁律**：中文正常口语语速上限为 `4.0 ~ 4.5 字/秒`。单镜头内台词字数绝不能超过 `时长 × 4.5 字`。超出字数必须拆分镜头或采用跨镜头声音延续（L-Cut / J-Cut）。
