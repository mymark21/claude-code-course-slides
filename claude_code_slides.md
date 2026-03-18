# Claude Code 课程 Slides

---

## 🟦 PART 1：基础

---

### Slide 1 — 封面/导言

- Claude Code 是什么
- Terminal-first AI 编程助手
- 不只是写代码 → 是一个 agent

---

### Slide 2 — 从文件夹开始

- ✅ 正确姿势：`cd 项目目录` → `claude`
- ❌ 错误姿势：根目录启动
- 为什么：上下文 = 项目范围
- 类比：给人讲任务，先说清楚"在哪个项目里"

---

### Slide 3 — 认识模型

- 当前可用模型一览（Sonnet / Opus / Haiku）
- 切换命令：`/model`
- 选择原则：复杂任务用 Opus，日常用 Sonnet，省钱用 Haiku

---

### Slide 4 — 两种模式

- **交互模式**：实时对话，适合探索
- **命令模式**：`claude -p "..."` 一次性执行，适合脚本/自动化
- 使用场景对比表

---

### Slide 5 — 打断 & 撤回

- 打断：`ESC` → 中断执行 → 立即补充新方向
- 撤回：`ESC ESC` → 回到上一条消息发送前的状态
- 区别：单击 = 转向，双击 = 时光倒流
- 类比：单击是"等等，换个思路"；双击是"这条路走错了，整个重来"

---

### Slide 6 — 处理上下文

- 原则：**一个对话 = 一个问题**
- 对话变长时：`/compact` 压缩上下文
- 回到旧对话：`/resume` + 对话 ID
- 为什么重要：上下文污染 → 输出质量下降

---

### Slide 7 — CLAUDE.md（项目记忆）

- 是什么：项目根目录的说明文件
- Claude 每次启动自动读取
- 写什么：技术栈、规范、禁止事项、常用路径
- 类比：新员工入职手册

---

### Slide 8 — 费用感知

- 查看用量：`/cost`
- Token 消耗来源：输入 / 输出 / 工具调用
- 节省技巧：压缩对话、精准 prompt、避免重复上传大文件

---

## 🟧 PART 2：工作流心法

---

### Slide 9 — 第一条 Prompt 怎么写

- 给背景 → 说目标 → 说约束
- 模板：`我在做 [X]，需要 [Y]，要求 [Z]`
- 不要：只说"帮我写个网站"

---

### Slide 10 — 什么时候新开对话

- ✅ 新开：换了任务目标 / 上下文超长 / 输出开始漂移
- ✅ 继续：同一问题的追问 / 小修改
- 判断标准：Claude 还记得"我们在做什么"吗？

---

### Slide 11 — 如何 Review 输出

- 不要盲目 Accept
- 检查清单：逻辑对吗？副作用？有没有删了不该删的？
- 养成习惯：`git diff` 看每一次变更

---

## 🟥 PART 3：进阶

---

### Slide 12 — 更好的终端：Ghostty

- 为什么换：性能、字体渲染、原生 macOS 体验
- 核心技巧：**拖动文件夹** → 自动 `cd` 到该目录
- 配置推荐：字体 / 透明度 / 快捷键

---

### Slide 13 — 自举：让 Claude 改自己

- 概念：用 Claude Code 修改 Claude Code 的配置和脚本
- 场景：自动生成 CLAUDE.md、优化自己的 workflow
- Wow moment：Claude 给自己写工具

---

### Slide 14 — 快捷键 & Permission 模式

- `cc` 别名 = 快速启动
- Permission pass 状态：跳过每次操作确认
- 适用场景：信任度高的任务 / 自动化流水线
- ⚠️ 注意：不建议在陌生代码库开启

---

### Slide 15 — Agent 蜂群模式

- 概念：一个主 agent → 派发多个 sub-agent 并行工作
- 场景举例：同时爬数据 + 写文章 + 生成图片描述
- 关键：任务拆解要清晰，子任务相互独立

---

### Slide 16 — Skill 体系

- 定义：可复用的 prompt 模板 + 上下文包
- **触发原则：做过 3 次 → 值得做成 skill**
- 结构：名称 / 触发词 / 模板内容 / 示例
- 存放位置：`.claude/skills/`

---

### Slide 17 — MCP：让 Claude 连接世界

- MCP = Model Context Protocol
- 类比：给 Claude 装插件
- 重点介绍 3 个：
  - `browser` → 操控浏览器
  - `filesystem` → 读写本地文件
  - `github` → 仓库操作
- 配置方式：`claude_desktop_config.json`

---

### Slide 18 — Agent 完备：渐进式披露

- 概念：Claude 自己配置自己的工具链
- 流程：需求 → Claude 分析 → 推荐 MCP → 自动写配置
- `cc` 配置其他工具的 demo 截图

---

## 🟩 PART 4：Demo

---

### Slide 19 — Demo 1：创建网站

- 输入：一句话描述
- 过程：Claude 选技术栈 → 生成文件结构 → 写代码 → 本地预览
- 重点展示：多文件协作能力

---

### Slide 20 — Demo 2：文章写作

- 场景：给定主题 → 调研 + 生成大纲 + 完整成文
- 配合 MCP browser：实时搜索资料
- 技巧：Skill 固定写作风格

---

### Slide 21 — Demo 3：网站 SEO 工作流

- 分析现有页面 → 生成 SEO 建议 → 自动修改 meta/结构
- 工具链：browser MCP + filesystem MCP
- 输出：改动报告 + diff

---

### Slide 22 — Demo 4：RPA 自动化浏览器

- 场景：批量表单填写 / 数据采集 / 定时操作
- 依赖：browser MCP（Playwright/Puppeteer）
- 展示：Claude 写脚本 → 自动执行 → 返回结果

---

### Slide 23 — 总结 & 资源

- 学习路径回顾（基础 → 心法 → 进阶 → 实战）
- 推荐资源：官方文档 / MCP 市场 / GitHub
- 下一步：挑一个 Demo，今天就跑起来
