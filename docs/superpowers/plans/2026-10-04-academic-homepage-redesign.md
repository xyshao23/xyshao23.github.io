# Academic Homepage Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将 Xinyu Shao 的英文和中文个人主页重构为参考学术主页的单列学术信息架构，同时保留当前全部公开内容，便于后续筛选。

**Architecture:** 继续使用仓库现有的纯静态 `index.html`、`zh.html` 和 `styles.css`。两份 HTML 保持相同的 section 顺序和语义结构，文案分别使用英文和中文；CSS 负责窄栏、首屏左右布局、论文两列列表、响应式移动布局和无卡片视觉。

**Tech Stack:** HTML5, CSS3, 原生静态文件；不引入 Jekyll、JavaScript 框架或外部构建依赖。

**Spec:** `docs/superpowers/specs/2026-10-04-academic-homepage-redesign-design.md`

## Global Constraints

- 保留当前已公开的所有个人介绍、经历、论文、教育信息和链接；本轮只改变组织方式和呈现方式。
- 不新增尚未正式公开的 LIP 条目；LIP 未来公开后再单独加入。
- News 按 `2025.09 → 2026.09` 的实际时间顺序排列。
- 有 arXiv 链接的 News 标题才添加链接；没有链接的 workshop 条目只显示标题和会议信息。
- 参考 `novaglow646.github.io` 的信息层级和视觉节奏，但不复制其文字、个人品牌、代码或具体设计资产。
- 继续使用已经更新的 `profile.jpg`，照片在桌面端为右侧竖向圆角矩形，移动端自适应。
- 用户确认本地预览后，才提交并推送页面改动到 `main`。

## Review Focus

- 两个语言页面的 section 顺序、锚点和导航是否完全对应；由 Task 2 的链接/锚点检查覆盖。
- News 中四条事件是否按时间顺序、标题和 workshop 全称准确呈现；由 Task 1/2 的文本断言覆盖。
- 论文标题、作者、状态和已有链接是否被完整保留；由 Task 1/2 的现有内容清单检查覆盖。
- 长论文标题、长 workshop 名称和窄屏布局是否溢出；由 Task 3 的本地渲染和尺寸检查覆盖。
- 头像、Email、Scholar、GitHub 和论文外链是否仍可访问；由 Task 4 的 URL/资源检查覆盖。

### Task 1: 重构英文主页内容与信息架构

**Files:**
- Modify: `index.html`

**Interfaces:**
- Produces the English semantic structure and content consumed by `styles.css` and the browser checks in Task 4.

- [ ] **Step 1: Rewrite the page skeleton and navigation**

保留现有 head 中的 charset、viewport、description、canonical 和 hreflang；将 body 重排为 `about`、`news`、`publications`、`experience`、`education`、`awards` 六个可导航 section。导航文本使用 `About`、`News`、`Publications`、`Experience`、`Education`、`Awards` 和 `中文`。

- [ ] **Step 2: Implement the new About section**

将首屏姓名改为 `Xinyu Shao` 与中文名并列，身份行使用 `Ph.D. Student @ Tsinghua University` 和 `Research Intern @ Huawei Noah's Ark Lab / 2012 Labs`；加入用户确认的 research statement 和 `Research Interests` 列表。保留 Email、Google Scholar、GitHub 链接和 `profile.jpg`。

- [ ] **Step 3: Implement chronological News**

按以下顺序写入四条事件：

1. 2025.09：`Linear Differential Vision Transformer: Learning Visual Contrasts via Pairwise Differentials`，链接到 `https://arxiv.org/abs/2511.00833`，accepted to NeurIPS 2025。
2. 2026.09：`More than A Point` 的现有论文标题，链接到 `https://arxiv.org/abs/2510.10912`，accepted at CoRL 2026。
3. 2026.09：`Beyond Video Generation: Exploring Latent Interaction Priors from Frozen Video World Models for Robot Learning`，不添加不存在的链接，说明被 NeurIPS 2026 Workshop: Robot Learning with World Models: Capabilities, Frontiers, and Challenges 接收。
4. 2026.09：`RASR: Range-Aware Scale Recovery for Metric UAV Navigation`，链接到 `https://arxiv.org/abs/2607.09815`，accepted at ACM MM 2026 Workshop UAVM。

采用参考主页的自然语言句式，例如 `One paper, [Title], was accepted ...`，不添加用户尚未确认的 ICRA submission。

- [ ] **Step 4: Reorder and restyle Selected Publications content**

标题改为 `Selected Publications`，加入 `Full publication list → Google Scholar`。保留当前六篇论文的标题、作者、状态、简介和已有链接，顺序固定为 CoRL 一作、KAM-WM、Survey、Spatial Visual Prompts、RASR、Linear Differential Vision Transformer。每篇使用会议/状态 badge、标题、作者、venue/status、highlights 和 links 的语义结构。

- [ ] **Step 5: Move remaining current information below publications**

将 Huawei 2012 Lab 研究实习保留为 Experience 条目，将清华博士和南航本科保留为 Education 条目，将现有清华综合奖学金放到 Awards 条目；不新增 PDF 中尚未确认要展示的专利、LIP、MATS 或 ResCue 内容。

### Task 2: 同步重构中文主页内容

**Files:**
- Modify: `zh.html`

**Interfaces:**
- Produces the Chinese equivalent of Task 1 with identical section IDs, ordering, links, and content coverage.

- [ ] **Step 1: Mirror the English skeleton and navigation**

保持与 `index.html` 相同的 `about`、`news`、`publications`、`experience`、`education`、`awards` section IDs，导航使用中文标签并保留 `English` 切换。

- [ ] **Step 2: Translate and preserve the About content**

将身份、research statement 和 research interests 翻译为自然中文，保留英文论文标题、作者名、会议名和链接；照片 alt 文本、Email、Scholar、GitHub 链接继续可用。

- [ ] **Step 3: Mirror the four chronological News entries**

News 使用与英文页相同的四个日期、论文标题和 workshop 全称；可用 arXiv 链接保持一致，无链接的 workshop 条目不新增超链接。

- [ ] **Step 4: Mirror Selected Publications, Experience, Education and Awards**

将英文页的论文顺序、所有现有链接、经历数字、教育信息和奖学金信息逐项对应到中文页，避免只翻译标题而遗漏正文内容。

### Task 3: 重写静态视觉系统

**Files:**
- Modify: `styles.css`

**Interfaces:**
- Consumes the shared class names and section structure from Tasks 1–2.
- Produces the desktop and mobile visual behavior for both language pages.

- [ ] **Step 1: Replace the current card-oriented variables and base layout**

设置白色背景、约 930px 内容宽度、深灰正文、低饱和蓝色链接/标签和细分割线；保留可读的系统无衬线字体与 focus 状态。

- [ ] **Step 2: Style fixed navigation and About two-column layout**

实现窄高固定导航、首屏左文右图、竖向圆角照片、研究兴趣嵌套列表和底部社交链接；照片使用 `object-fit: cover`，不再使用圆形头像。

- [ ] **Step 3: Style News and publication list**

News 使用紧凑的日期—事件行；论文使用左侧 badge、右侧文本的两列结构；长标题、作者和 workshop 名称允许自然换行，不使用横向滚动。

- [ ] **Step 4: Add responsive and accessibility behavior**

在窄屏下导航收缩、About 变为单列、头像居中、论文条目堆叠；保留键盘可见 focus、语义标题层级和图片 alt 文本。

### Task 4: 本地验证、预览和发布

**Files:**
- Test: `index.html`, `zh.html`, `styles.css`, `profile.jpg`

**Interfaces:**
- Consumes all changed files from Tasks 1–3.
- Produces a verified static site ready for the user-facing preview and GitHub Pages deployment.

- [ ] **Step 1: Run static integrity checks**

运行 `git diff --check`；用 `rg` 断言两个页面都包含六个 section、四条 News 标题、六篇 Selected Publications 标题、`profile.jpg`、Email 和 Google Scholar 链接。

- [ ] **Step 2: Run a local HTTP preview**

使用 `python3 -m http.server` 提供仓库根目录，分别请求 `/`、`/zh.html`、`/styles.css` 和 `/profile.jpg`，预期全部返回 200，且 HTML 中没有引用不存在的本地资源。

- [ ] **Step 3: Inspect desktop and narrow-screen rendering**

在浏览器中打开英文页和中文页，检查首屏照片裁切、News 顺序、论文第一项是否为 CoRL、长标题换行、导航锚点和移动端无横向溢出。

- [ ] **Step 4: Commit the implementation**

```bash
git add index.html zh.html styles.css
git commit -m "Redesign academic homepage layout"
```

- [ ] **Step 5: Push and verify GitHub Pages**

用户确认预览后运行 `git push origin main`；随后请求线上 `/`、`/zh.html` 和 `/profile.jpg`，确认页面返回 200，线上头像可下载，并检查远程 `main` 指向刚刚的 commit。
