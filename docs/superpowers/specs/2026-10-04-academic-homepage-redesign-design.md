# Xinyu Shao Academic Homepage Redesign

## 目标

将现有主页重构为“学术主页”信息架构：首屏先建立 Xinyu Shao 作为 embodied AI / robot learning researcher 的身份，再依次呈现研究方向、动态、代表性论文、经历、教育和奖励/服务。英文页和中文页保持同一结构与视觉系统。

参考 `https://novaglow646.github.io/` 的信息层级和视觉节奏，但不复制其文字、个人品牌、代码或具体设计资产。

## 范围与约束

- 继续使用当前仓库的纯静态 HTML/CSS，不迁移到 Jekyll 或引入构建依赖。
- 保留当前已公开的所有个人介绍、经历、论文、教育信息和链接；本轮只改变组织方式和呈现方式，方便后续再删减。
- 不新增尚未正式公开的 LIP 条目；LIP 未来公开后再单独加入。
- 保留英文页 `index.html`、中文页 `zh.html` 和语言切换。
- 保留已经更新的 `profile.jpg`。

## 页面信息架构

### 1. 顶部导航

保留简洁的固定顶部导航，链接到页面内的 `About`、`News`、`Publications`、`Experience`、`Education` 和 `Awards / Service`，右侧提供 English / 中文切换。导航在移动端收缩为可用的紧凑布局。

### 2. About / 首屏

首屏采用参考主页的左右结构：左侧为姓名、身份和研究陈述，右侧为竖向圆角照片。

英文身份信息使用：

> Xinyu Shao / 邵新宇
>
> Ph.D. Student @ Tsinghua University
> Research Intern @ Huawei Noah's Ark Lab / 2012 Labs

研究陈述使用简洁版本：

> I work on robot learning and embodied intelligence, with a focus on VLA policies, generative world models, and data-efficient robot manipulation.

随后紧接 `Research Interests`，将现有研究内容归纳为：

- Vision-Language-Action Models
- World Models for Robot Learning
- Generative Policies / Diffusion Policies
- Spatial Grounding & Affordance
- Offline Reinforcement Learning and Sim-to-Real Transfer

中文页使用准确对应的中文表述，不改变事实边界。

底部保留 Email、Google Scholar、GitHub 等社交链接，并保持可访问性标签。

### 3. News

在 About 后直接放置 `🔥 News`，使用紧凑的日期—事件列表或表格。目前至少保留现有两条动态：

- 2026.09：`More than A Point` accepted at CoRL 2026。
- 2025.09：`Linear Differential Vision Transformer` accepted at NeurIPS 2025。

不编造尚未提供的 `2026.xx ICRA submission`；如用户后续确认该事件，再加入对应条目。

### 4. Selected Publications

标题使用 `Selected Publications`，旁边提供 `Full publication list → Google Scholar` 链接，不再使用“仅展示公开 arXiv 作品”等解释性说明。

当前论文全部搬入新列表，但顺序调整为：

1. `More than A Point: Capturing Uncertainty with Adaptive Affordance Heatmaps for Spatial Grounding in Robotic Tasks`（Xinyu Shao 一作，CoRL 2026 accepted）
2. `KAM-WM: Kinematic Affordance Maps from Latent World Models for Robot Manipulation`
3. `Generative Models in Decision Making: A Survey`
4. `Decoupling Semantics and Geometric Grounding: Spatial Visual Prompts for Language-Conditioned Imitation Learning`
5. `RASR: Range-Aware Scale Recovery for Metric UAV Navigation`
6. `Linear Differential Vision Transformer: Learning Visual Contrasts via Pairwise Differentials`

每篇论文使用参考主页式纵向条目：会议/状态 badge、论文标题、作者、会议或预印本状态、当前已有的简短贡献描述，以及 PDF/arXiv、Code、NeurIPS 等已有链接。论文标题和作者信息不做事实性改写。

### 5. Experience

将当前 Huawei 2012 Lab 具身智能算法研究实习内容放在论文之后，保留现有工作职责、数据规模、方法和结果数字，改为简洁的经历条目。

### 6. Education

保留清华大学博士和南京航空航天大学本科信息，包括时间、项目/专业、GPA 和现有奖学金信息。

### 7. Awards / Service

将当前教育部分中的清华大学综合奖学金信息迁移到 `Awards`，不凭空新增奖项或服务经历。若当前没有足够的 Service 内容，可保留 `Awards` 标题并在后续用户确认后扩展为 `Awards / Service`。

## 视觉系统

- 白色背景、约 930px 的窄内容栏、充足留白。
- 使用清晰的系统无衬线字体；姓名采用较大的高对比度标题。
- 正文使用深灰色，链接和会议 badge 使用低饱和蓝色。
- 各模块标题采用细底边线，取消现有大面积卡片化视觉。
- 头像使用竖向圆角矩形，不使用圆形裁切；桌面端位于 About 右侧，移动端置于介绍上方或下方。
- 论文条目采用两列结构：左侧状态/会议标签，右侧内容。
- 不加入复杂动画；只保留悬停、焦点和移动端导航等必要交互。
- 所有链接保持键盘可访问性和清晰的 hover/focus 状态。

## 实现文件与验证

主要修改：

- `index.html`
- `zh.html`
- `styles.css`

验证标准：

1. 英文页和中文页都能在本地静态服务器正常打开。
2. 当前所有论文、经历、教育信息、链接和头像仍然存在。
3. CoRL 一作位于 Selected Publications 第一项。
4. 页面在桌面和窄屏下均无横向溢出，照片和论文列表布局稳定。
5. `git diff --check` 通过，HTML 中的相对链接和锚点可用。
6. 用户确认预览后，再提交并推送到 `main`。
