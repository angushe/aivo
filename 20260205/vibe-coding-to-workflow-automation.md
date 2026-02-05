# AI编程实践：从Vibe Coding到工作流自动化

> 一场面向技术同行的AI编程实践分享工作坊

## 分享概览

| 项目 | 内容 |
|------|------|
| **时长** | 120分钟（2小时） |
| **形式** | 工作坊/Demo |
| **听众** | 开发人员，已在使用AI编程工具 |
| **目标** | 阶段跃迁 + 工作流自动化 + 思维转变 |

## 章节时间分配

| 章节 | 内容 | 时长 |
|------|------|------|
| — | 背景：Vibe Coding → Vibe Engineering | 2分钟 |
| 一 | 开场：8阶段模型 | 3分钟 |
| 二 | 逐阶段详解 + Superpowers | 30分钟 |
| 三 | MCP：连接外部系统 | 10分钟 |
| 四 | Skill：定义工作流程 | 15分钟 |
| 五 | Hooks：自动化触发 | 5分钟 |
| 六 | 现场挑战 | 25分钟 |
| 七 | 踩坑与技巧 | 10分钟 |
| 八 | Q&A | 10分钟 |
| 九 | 结语：超越工具 | 10分钟 |
| | **合计** | **120分钟** |

---

## 背景：从 Vibe Coding 到 Vibe Engineering（2分钟）

### 术语来源

Andrej Karpathy（特斯拉前 AI 总监、OpenAI 联创）在 2025 年 2 月的推文中首次提出：

> "There's a new kind of coding I call 'vibe coding', where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."

### 核心特征

| 特征 | 描述 |
|------|------|
| **自然语言驱动** | 用口语描述需求，AI 生成代码 |
| **忽略实现细节** | "forget that the code even exists" |
| **拥抱不确定性** | 不逐行审查，相信 AI 输出 |
| **快速迭代** | 出错就重来，不深究原因 |

### 适用场景 vs 局限

**适合**：
- 快速原型、验证想法
- 一次性脚本、小工具
- 学习新框架/语言

**不适合**：
- 生产环境代码
- 需要长期维护的项目
- 安全敏感场景

### Vibe Engineering：成熟版

Simon Willison 在 2025 年 10 月提出 **Vibe Engineering**——填补 Vibe Coding 和传统工程之间的术语空白：

> "从即兴演奏到指挥编排——你不是写每一行代码，而是设计写代码、检查代码、维护代码的系统。"

| | Vibe Coding | Vibe Engineering |
|---|-------------|------------------|
| **态度** | 放飞自我，不看代码 | 对产出负责 |
| **流程** | 即兴发挥 | 结构化编排 |
| **验证** | 能跑就行 | 测试驱动、自动化检查 |
| **适用** | 原型、hackathon | 生产环境 |

**核心原则**：
- **AI 作为一等公民**：不只是助手，而是有明确职责的协作者
- **验证驱动开发**：测试护栏 + 自动化反馈循环
- **Prompt 即架构**：prompt 是版本控制的架构产物，不是一次性 hack

### 与本次分享的关系

> **Vibe Coding 是起点，Vibe Engineering 是方向。**
>
> 本次分享的核心正是 Vibe Engineering 的实践：
> 如何从"随意 vibe"进化到"有纪律的 Agent 协作"——
> 既保持 AI 编程的高效，又确保输出的质量和可控性。

---

## 一、开场：8阶段模型（3分钟）

### 引用来源
Steve Yegge - [Welcome to Gas Town](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04)（2026年1月）

### 8阶段速览表

Yegge 原文将其比作程序员的"AI 进化阶段"（The 8 Stages of Dev Evolution To AI）：

| 阶段 | 描述 | Yegge 原文 |
|------|------|-----------|
| 1 | 零或接近零AI | "maybe code completions, sometimes ask Chat questions" |
| 2 | IDE内Agent，需确认权限 | "A narrow coding agent in a sidebar asks your permission to run tools" |
| 3 | IDE内Agent，YOLO模式 | "Trust goes up. You turn off permissions, agent gets wider" |
| 4 | Agent填满屏幕 | "Your agent gradually grows to fill the screen. Code is just for diffs" |
| 5 | CLI单Agent，YOLO | "Diffs scroll by. You may or may not look at them" |
| 6 | CLI多Agent并行 | "You regularly use 3 to 5 parallel instances. You are very fast" |
| 7 | 10+Agent，手动管理 | "You are starting to push the limits of hand-management" |
| 8 | 自建编排器 | "You are on the frontier, automating your workflow" |

**Yegge 的警告**：
> "If you're not at least Stage 7, or maybe Stage 6 and very brave, then you will not be able to use Gas Town."

（Gas Town 是 Yegge 构建的 Agent 编排系统，专为 Stage 7+ 用户设计）

### 开场话术

> "Steve Yegge今年初发了篇文章，把AI编程分成8个阶段。我先问大家——你现在在哪个阶段？（现场举手/投票）两个月前我在Stage 3，现在稳定在Stage 6-7之间。今天聊聊这个跃迁是怎么发生的。"

---

## 二、逐阶段详解（30分钟）

### Stage 1：零或接近零AI

**典型场景**：只用IDE自动补全，偶尔问ChatGPT

**瓶颈**：手动写所有代码，AI只是搜索引擎的替代品

**升级建议**：尝试让AI写一个完整函数，而不是只问问题

---

### Stage 2：IDE内Agent，需确认权限

**工具**：Cursor、Copilot Chat、Windsurf等

**工作模式**：每次操作都要点"允许"，AI改一行你确认一下

**瓶颈**：频繁打断，AI无法连续完成任务

**升级建议**：选一个低风险任务，尝试关闭逐步确认

---

### Stage 3：IDE内Agent，YOLO模式

**工具**：同上，但关闭权限确认

**工作模式**：给任务描述，让AI自己跑，最后review diff

**瓶颈**：IDE内Agent上下文有限，复杂任务容易迷路

**升级建议**：尝试CLI工具（如Claude Code），体验完整终端控制

---

### Stage 4：Agent填满屏幕，代码只看diff

**工具**：Cursor Composer、Claude Code

**工作模式**：Agent成为主角，你主要看diff和approve

**Yegge 原话**："Your agent gradually grows to fill the screen. Code is just for diffs."

> 关键转变：代码从"你写的东西"变成"你审的东西"

**瓶颈**：单Agent处理能力有上限，大任务仍需拆分

**升级建议**：学会写好prompt，任务拆分，开始考虑并行

---

### Stage 5：CLI单Agent，YOLO（重点）

**工具**：Claude Code、Codex、Copilot等CLI工具

**工作模式**：终端里跑Agent，diff滚动而过，你可能看可能不看

**Yegge 原话**："Diffs scroll by. You may or may not look at them."

> 关键转变：从 IDE 走向 CLI，获得更大的上下文和控制力

**关键能力**：
- 学会用 `/compact` 压缩上下文
- 善用 `CLAUDE.md` 给Agent项目背景
- 建立review习惯：跑完后统一看git diff

**瓶颈**：单线程，一个任务卡住整个流程

**升级建议**：开多个终端窗口，开始并行

---

### Stage 6：CLI多Agent并行（重点）

**工具**：多个Claude Code实例 + tmux/终端分屏

**工作模式**：
- 把大任务拆成独立子任务
- 每个终端窗口一个Agent处理一个子任务
- 你在窗口间切换，充当"调度员"

**Yegge 原话**："You regularly use 3 to 5 parallel instances. You are very fast."

> 关键转变：从单线程到并行，生产力质的飞跃

**关键能力**：
- 任务拆分：确保子任务之间低耦合
- Git分支管理：每个Agent一个分支，避免冲突
- 注意力管理：知道什么时候该介入，什么时候让它跑

**瓶颈**：手动调度累，超过5个实例容易乱

---

### Stage 6.5：Superpowers——半自动化工作流（重点介绍）

> 当你开始觉得手动管理多个Agent很累时，Superpowers 是一个值得尝试的"过渡方案"。

**项目地址**：[github.com/obra/superpowers](https://github.com/obra/superpowers)

**定位**：介于 Stage 6（手动多Agent）和 Stage 8（自建编排器）之间的**半自动编排方案**。它把 Stage 7 的很多"人肉操作"标准化成了自动触发的技能。

#### 核心理念

Superpowers 的核心思想是：**Agent 在动手写代码之前，先退一步问清楚你到底要做什么。**

它不是让 AI 更快地写代码，而是让 AI 用**正确的流程**写代码：
- 先设计，再动手
- 先计划，再执行
- 先测试，再实现
- 先审查，再合并

#### 7步工作流详解

```
┌─────────────────────────────────────────────────────────────────┐
│  1. brainstorming          想法 → 设计文档                      │
│         ↓                                                       │
│  2. using-git-worktrees    创建隔离工作空间                      │
│         ↓                                                       │
│  3. writing-plans          设计 → 2-5分钟的小任务                │
│         ↓                                                       │
│  4. subagent-driven-dev    子Agent逐个执行 + 两阶段审查          │
│         ↓                                                       │
│  5. test-driven-dev        红 → 绿 → 重构                       │
│         ↓                                                       │
│  6. requesting-code-review 代码审查                             │
│         ↓                                                       │
│  7. finishing-branch       合并/PR/清理                         │
└─────────────────────────────────────────────────────────────────┘
```

**Step 1: brainstorming（头脑风暴）**

触发时机：当你说"我想做一个xxx"时自动激活

工作方式：
- Agent **不会立刻写代码**，而是开始问问题
- 一次只问一个问题，优先用选择题
- 探索 2-3 种方案，给出推荐和理由
- 把设计拆成小段（200-300字）逐段确认
- 最后输出设计文档保存到 `docs/plans/`

价值：避免"方向错了写一堆废代码"

**Step 2: using-git-worktrees（Git Worktree 隔离）**

触发时机：设计确认后自动激活

工作方式：
- 为这个任务创建独立的 git worktree
- 切换到新分支
- 运行项目初始化（安装依赖等）
- 验证测试基线是绿的

价值：每个任务完全隔离，不怕互相踩踏

**Step 3: writing-plans（写计划）**

触发时机：有了设计文档后自动激活

工作方式：
- 把设计拆成**具体到可执行**的小任务
- 每个任务 2-5 分钟可完成
- 每个任务包含：精确文件路径、完整代码、验证步骤
- 写得足够清晰，让"没有上下文的初级工程师"也能执行

价值：任务粒度够细，Agent 不容易迷路

**Step 4: subagent-driven-development（子Agent驱动开发）**

触发时机：计划写好后自动激活

工作方式：
- 为每个任务启动一个**全新的子Agent**
- 子Agent 只专注于一个小任务
- 完成后进行**两阶段审查**：
  1. Spec 审查：是否符合设计要求？
  2. Quality 审查：代码质量是否达标？
- 两阶段都通过才继续下一个任务

价值：Agent 可以连续自主工作数小时不跑偏

**Step 5: test-driven-development（测试驱动开发）**

触发时机：实现代码时自动激活

工作方式：
- 严格的 RED-GREEN-REFACTOR 循环
- 先写失败的测试 → 看它失败 → 写最小实现 → 看它通过 → 提交
- **如果发现代码先于测试写出来，会删掉重来**

价值：强制 TDD 纪律，保证代码有测试覆盖

**Step 6: requesting-code-review（代码审查）**

触发时机：任务间隙自动激活

工作方式：
- 对照计划检查实现
- 按严重程度报告问题
- Critical 问题会阻止继续

价值：及早发现偏离计划的情况

**Step 7: finishing-a-development-branch（收尾）**

触发时机：所有任务完成后自动激活

工作方式：
- 验证所有测试通过
- 提供选项：合并到主分支 / 创建PR / 保留分支 / 丢弃
- 清理 worktree

价值：干净收尾，不留烂摊子

#### 为什么说是"半自动"？

| 特征 | Stage 6 手动 | Superpowers | Stage 8 编排器 |
|------|-------------|-------------|---------------|
| 任务拆分 | 人工拆 | 自动拆 | 自动拆 |
| Agent调度 | 人工开窗口 | 自动启动子Agent | 全自动调度 |
| 进度追踪 | 人工记录 | 自动检查点 | 全自动追踪 |
| 质量门禁 | 人工review | 两阶段自动审查 | 自动门禁 |
| 人类介入 | 频繁 | 关键节点确认 | 极少 |

Superpowers 自动化了大部分流程，但仍在关键节点保留人类确认——这是务实的选择，因为当前 AI 还不够可靠到完全放手。

#### 安装和使用

```bash
# Claude Code 中安装
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# 验证安装
/help
# 应该看到 brainstorming, write-plan 等命令
```

安装后不需要特别操作，技能会**自动触发**。当你开始描述一个任务，Agent 会自动进入 brainstorming 流程。

#### 适合谁用？

- ✅ 已经在 Stage 5-6，想要更结构化的工作流
- ✅ 经常发现 Agent 跑偏，想要更多约束
- ✅ 想尝试 TDD 但自己缺乏纪律
- ✅ 准备向 Stage 7-8 进化，想先体验自动化

- ❌ 刚接触 AI 编程，还在 Stage 1-3
- ❌ 只是简单任务，不需要这么重的流程
- ❌ 项目不用 Git

---

### Stage 7：10+ Agent，手动管理到极限

**工具**：Claude Code + git worktree + 脚本辅助

**工作模式**：
- 用git worktree为每个Agent创建独立工作目录
- 可能写简单脚本批量启动/监控
- 接近人肉编排器

**Yegge 原话**："You are starting to push the limits of hand-management."

> 关键挑战：你开始成为瓶颈——Agent 等你调度，而不是你等 Agent

**关键能力**：
- worktree隔离：避免Agent互相踩踏
- 状态追踪：用文档或简单工具记录谁在做什么
- 合并策略：处理多分支合并冲突

**瓶颈**：认知负荷爆炸，开始想要自动化

---

### Stage 8：自建编排器

**工具**：Gas Town、自研框架、或基于Claude API的定制方案

**工作模式**：
- Agent有层级：Manager Agent调度Worker Agent
- 自动化任务分配、进度追踪、结果合并
- 你只需定义目标，系统自动拆解执行

**Yegge 原话**："You are on the frontier, automating your workflow."

> 关键角色转变：从"调度员"变成"工厂设计师"——你设计自动化流程，而不是手动调度

**关于 Gas Town**：

Yegge 的 Gas Town 是 Stage 8 的代表作，他这样描述：

> "Gas Town helps you with the tedium of running lots of Claude Code instances. Stuff gets lost, it's hard to track who's doing what, etc. Gas Town helps with all that yak shaving, and lets you focus on what your Claude Codes are working on."
>
> "I've tamed them (Claude Code) to where you can use 20–30 at once, productively, on a sustained basis."

Gas Town 的核心组件包括：
- **Mayor**：主 Agent，你的首席执行官
- **Polecats**：按需启动的临时工作者
- **Refinery**：智能合并队列，处理多分支合并
- **Witness**：监工，确保 Polecats 不卡住
- **Crew**：你的长期助手团队

**现状**：前沿探索区，工具链尚不成熟，但 Gas Town 展示了方向

---

## 三、从写代码到自动化：MCP 打开的可能性（10分钟）

> 前面讲的都是"vibe coding"——用 AI 写代码。但 AI 的价值不止于此。

### Claude Code 扩展能力全景（三件套）

在深入 MCP 之前，先看全局——Claude Code 的三大扩展机制：

```
┌─────────────────────────────────────────────────────────────────┐
│                     Claude Code 扩展生态                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   MCP Server            Skill               Hooks               │
│   ──────────            ─────               ─────               │
│   连接外部系统           定义工作流程         事件触发脚本        │
│   (能力扩展)            (方法论封装)         (自动化钩子)        │
│                                                                 │
│   "能做什么"            "怎么做"            "做完后干什么"       │
│                                                                 │
│   例：连接 GitLab       例：TDD 流程         例：提交后自动跑测试 │
│   例：查询数据库         例：代码审查清单      例：保存后自动格式化 │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│   本章讲 MCP → 下一章讲 Skill → 再下一章讲 Hooks                 │
└─────────────────────────────────────────────────────────────────┘
```

接下来三章分别深入每一个。先从 MCP 开始。

---

### 开发者的"胶水工作"

写代码只占开发工作的一部分，大量时间花在**胶水工作**上：

- 看 Issue、理解需求
- 查日志、定位问题
- 跑 CI、等结果、看失败原因
- 发消息、同步进度
- 更新文档、写周报
- 处理 PR review 评论

这些工作重复、琐碎，但又不得不做。**如果 Agent 能帮你处理这些呢？**

---

### Agent 能力的两个层次

#### 层次一：内置能力（开箱即用）

Claude Code 本身就能做的自动化，不需要额外配置：

| 场景 | 示例 Prompt |
|------|-------------|
| 代码审查 | "审查这个 PR 的改动，找出潜在问题" |
| 重构辅助 | "把这个模块从 class 改成 hooks" |
| 文档生成 | "根据代码生成 API 文档" |
| 测试补全 | "给这个模块补充单元测试" |
| 日志分析 | "分析这段错误日志，找出根因" |
| 依赖升级 | "升级 React 到 18，处理 breaking changes" |

这些是"即插即用"的——给 Agent 足够的上下文，它就能做。

#### 层次二：MCP 扩展能力（连接外部系统）

当你需要 Agent 与**外部系统**交互时，MCP 就登场了。

---

### MCP 是什么？

> **Model Context Protocol** —— 让 AI 连接外部工具和数据的标准协议

```
┌─────────────┐      MCP 协议      ┌─────────────────┐
│ Claude Code │ ◄────────────────► │   MCP Server    │
└─────────────┘                    └────────┬────────┘
                                            │
                     ┌──────────────────────┼──────────────────────┐
                     ▼                      ▼                      ▼
               ┌──────────┐          ┌──────────┐          ┌──────────┐
               │ Database │          │   API    │          │ Services │
               │ Postgres │          │ Jira/Git │          │ Slack    │
               └──────────┘          └──────────┘          └──────────┘
```

**MCP Server 提供三种能力**：

| 类型 | 作用 | 示例 |
|------|------|------|
| **Tools** | 让 Agent 执行操作 | 创建 Issue、发消息、执行 SQL |
| **Resources** | 让 Agent 读取数据 | 文档、配置、数据库状态 |
| **Prompts** | 预定义的任务模板 | "分析这个 PR"、"总结这周的 Issue" |

**类比**：如果说 Claude Code 是大脑，MCP 就是让它长出手脚，能够触达外部世界。

---

### MCP 驱动的 Workflow 自动化示例

| 场景 | MCP Server | Agent 能做什么 |
|------|-----------|---------------|
| **Issue → 代码** | GitLab/GitHub | 读取 Issue → 分析需求 → 写代码 → 创建 PR |
| **数据库运维** | Postgres | 分析慢查询 → 生成优化建议 → 执行迁移 |
| **监控响应** | Prometheus | 读取告警 → 分析日志 → 定位问题 → 尝试修复 |
| **文档同步** | Notion/Confluence | 代码变更 → 自动更新对应文档 |
| **团队协作** | Slack | 任务完成 → 通知相关人 → 收集反馈 |
| **CI/CD 救火** | Jenkins/GitLab CI | 读取失败日志 → 分析原因 → 提交修复 |

---

### 实战案例：Issue 到 PR 的全自动化

```
┌─────────────────────────────────────────────────────────────────┐
│  1. 用户："解决 Issue #123"                                     │
│         ↓                                                       │
│  2. Agent（GitLab MCP）：读取 Issue 详情和评论                   │
│         ↓                                                       │
│  3. Agent：分析需求，定位相关代码文件                            │
│         ↓                                                       │
│  4. Agent：写代码、写测试、本地验证                              │
│         ↓                                                       │
│  5. Agent（GitLab MCP）：创建 MR，关联 Issue，填写描述           │
│         ↓                                                       │
│  6. Agent（Slack MCP）：通知 Reviewer："MR !456 ready for review"│
└─────────────────────────────────────────────────────────────────┘
```

**关键点**：整个流程中，你只说了一句话。Agent 自己完成了：
- 需求理解
- 代码实现
- PR 创建
- 团队通知

---

### 常用 MCP Server 推荐

| 类别 | MCP Server | 用途 |
|------|-----------|------|
| **代码托管** | GitLab MCP、GitHub MCP | Issue、PR、代码搜索 |
| **数据库** | Postgres MCP、MySQL MCP | 查询、迁移、优化 |
| **项目管理** | Jira MCP、Linear MCP | 任务管理、进度追踪 |
| **文档** | Notion MCP、Confluence MCP | 文档读写、知识库 |
| **通信** | Slack MCP、Discord MCP | 消息通知、团队协作 |
| **监控** | Prometheus MCP、Datadog MCP | 告警、日志、指标 |
| **通用** | Filesystem MCP、Web MCP | 文件操作、网页抓取 |

**查找更多**：[MCP Server 目录](https://github.com/modelcontextprotocol/servers)

---

### 如何开始？

**第一步：安装一个 MCP Server**

以 GitLab MCP 为例：
```bash
# 在 Claude Code 设置中添加 MCP Server 配置
# 详见各 MCP Server 的文档
```

**第二步：验证连接**
```
你：列出我最近的 5 个 Issue
Agent：（通过 GitLab MCP 获取数据）这是你最近的 Issue...
```

**第三步：尝试简单自动化**
```
你：读取 Issue #100，告诉我需要改哪些文件
你：解决 Issue #100，完成后创建 MR
```

---

### 展望：当 Agent 能连接一切

当 MCP 生态成熟，开发者的工作模式可能变成：

```
传统模式：                          Agent 模式：

看 Issue → 理解需求 → 写代码        "解决 Issue #123"
    ↓         ↓          ↓              ↓
看日志 → 定位问题 → 修复            Agent 自动完成全部
    ↓         ↓          ↓              ↓
写文档 → 发通知 → 等 Review         你：Review 结果，合并
```

**开发者的角色从"执行者"变成"决策者"**——你定义目标和标准，Agent 负责执行和汇报。

---

## 四、Skill——教 Agent 方法论（15分钟）

> MCP 解决"Agent 能连接什么"，Skill 解决"Agent 该怎么做"。

### Skill 是什么？

**一句话定义**：Skill 是一份 Markdown 文件，把你的经验/方法论写成 Agent 能理解和遵循的指令。

**最简示例**：

```markdown
# my-debug.md

name: my-debug
description: 我的调试方法论

## 触发条件
当用户说"帮我调试"或遇到报错时激活

## 执行步骤
1. 先复现问题，确认完整错误信息
2. 不要猜测，先读相关代码理解上下文
3. 形成假设，用最小改动验证
4. 修复后写测试防止回归
5. 解释根因，确保用户理解

## 禁止行为
- 不要一上来就改代码
- 不要同时尝试多个修复方案
```

**本质**：把"老司机的经验"变成"新手也能遵循的 SOP"。

---

### 为什么需要 Skill？

#### 没有 Skill 的问题

```
你：帮我调试这个 bug

Agent A（今天）：直接改代码，改错了，回滚，再试...
Agent A（明天）：先看日志，分析原因，精准修复

↑ 同一个 Agent，不同时间，不同表现
```

#### 有 Skill 的效果

```
你：帮我调试这个 bug

Agent（每次都）：
1. ✓ 复现问题
2. ✓ 读取相关代码
3. ✓ 形成假设
4. ✓ 最小改动验证
5. ✓ 补充测试

↑ 一致的、可预期的、高质量的流程
```

---

### Skill vs Prompt vs CLAUDE.md

| 维度 | 手动 Prompt | CLAUDE.md | Skill |
|------|------------|-----------|-------|
| **存储** | 每次手动输入 | 项目根目录文件 | 独立文件，可跨项目 |
| **作用域** | 当前对话 | 当前项目 | 可全局或项目级 |
| **触发** | 手动 | 自动加载 | 自动识别场景触发 |
| **复用** | 复制粘贴 | 项目内复用 | 跨项目、可分享 |
| **适合场景** | 一次性指令 | 项目背景信息 | 通用工作流程 |

**组合使用**：
- `CLAUDE.md`：告诉 Agent "这个项目是什么"
- `Skill`：告诉 Agent "遇到 X 情况该怎么做"
- `Prompt`：告诉 Agent "现在请做 Y"

---

### Skill 的三种使用方式

#### 方式一：使用现成的（即插即用）

```bash
# 安装 Superpowers，获得一整套成熟 Skills
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# 安装后自动生效，开始描述任务即可
你：我想给用户模块加一个导出功能
Agent：（自动进入 brainstorming 流程）让我先了解一下需求...
```

#### 方式二：写项目专属 Skill

```bash
# 在项目中创建 skills 目录
mkdir -p .claude/skills

# 创建你的 Skill
cat > .claude/skills/our-code-style.md << 'EOF'
name: our-code-style
description: 我们团队的代码规范

## 触发条件
写代码或代码审查时激活

## 规范要点
- 函数不超过 30 行
- 必须有错误处理
- 公开 API 必须有注释
- 使用 early return 减少嵌套
- 变量命名：camelCase，常量：UPPER_SNAKE_CASE

## 审查清单
- [ ] 是否符合单一职责
- [ ] 是否有适当的错误处理
- [ ] 是否有必要的测试
- [ ] 命名是否清晰表达意图
EOF
```

#### 方式三：写个人通用 Skill

```bash
# 放在用户级目录，所有项目都能用
mkdir -p ~/.claude/skills

# 例：你的 Git 提交规范
cat > ~/.claude/skills/my-commit-style.md << 'EOF'
name: my-commit-style
description: 我的 Git 提交规范

## 触发条件
当用户说"提交"或准备 git commit 时激活

## Commit Message 格式
<type>(<scope>): <subject>

<body>

## Type 类型
- feat: 新功能
- fix: 修复 bug
- refactor: 重构（不改变功能）
- docs: 文档
- test: 测试
- chore: 构建/工具

## 规则
- subject 不超过 50 字符
- body 每行不超过 72 字符
- 用中文写 body，英文写 type 和 subject
EOF
```

---

### 实用 Skill 示例

#### 示例 1：PR 描述生成器

```markdown
name: pr-description
description: 生成规范的 PR/MR 描述

## 触发条件
当用户说"写 PR 描述"或"准备提 MR"时激活

## 执行步骤

1. 运行 git log main..HEAD --oneline 查看提交历史
2. 运行 git diff main...HEAD --stat 查看改动文件
3. 分析改动的目的和影响
4. 按模板生成描述

## 输出模板

## Summary
[1-2 句话说明这个 PR 做了什么]

## Changes
- [文件/模块]: [改动说明]
- [文件/模块]: [改动说明]

## Why
[为什么需要这个改动，解决什么问题]

## Testing
- [ ] 单元测试通过
- [ ] 本地功能验证
- [ ] [其他相关测试]

## Screenshots (if applicable)
[UI 改动请附截图]
```

#### 示例 2：代码审查清单

```markdown
name: code-review
description: 系统化的代码审查流程

## 触发条件
当用户说"review 一下"或"帮我看看代码"时激活

## 审查维度

### 1. 正确性
- 逻辑是否正确？
- 边界条件是否处理？
- 错误处理是否完善？

### 2. 可读性
- 命名是否清晰？
- 是否需要注释？
- 结构是否合理？

### 3. 性能
- 有没有明显的性能问题？
- 是否有不必要的循环/查询？
- 大数据量下会怎样？

### 4. 安全性
- 有没有注入风险？
- 敏感数据是否保护？
- 权限检查是否到位？

### 5. 可测试性
- 是否容易测试？
- 是否有测试覆盖？

## 输出格式

### 🔴 必须修改
[严重问题]

### 🟡 建议修改
[改进建议]

### 🟢 做得好的地方
[值得肯定的点]
```

#### 示例 3：新项目初始化

```markdown
name: project-init
description: 新项目初始化检查清单

## 触发条件
当用户说"新建项目"或在空目录开始工作时激活

## 检查清单

### 基础配置
- [ ] .gitignore 是否完整
- [ ] README.md 是否有基本说明
- [ ] LICENSE 是否添加
- [ ] package.json / pyproject.toml 等配置是否正确

### 开发环境
- [ ] 代码格式化配置（prettier/black）
- [ ] Lint 配置（eslint/ruff）
- [ ] 编辑器配置（.editorconfig）
- [ ] Git hooks（husky/pre-commit）

### CI/CD
- [ ] 基础 CI 配置（GitHub Actions / GitLab CI）
- [ ] 测试自动运行
- [ ] Lint 检查

### Claude Code 配置
- [ ] CLAUDE.md 项目说明
- [ ] .claude/skills/ 团队 Skill（如有）
- [ ] .claude/settings.json（如有特殊配置）

## 执行步骤
根据项目类型（前端/后端/全栈）逐项检查并补充缺失项
```

---

### Skill 编写最佳实践

#### 结构清晰

```markdown
# 好的结构
name: skill-name
description: 一句话说明用途

## 触发条件        ← 什么时候激活
## 执行步骤        ← 具体怎么做（有序）
## 输出格式        ← 结果长什么样
## 禁止行为        ← 什么不能做
## 示例            ← 具体例子
```

#### 指令具体

```markdown
# ❌ 模糊
检查代码质量

# ✅ 具体
1. 检查函数是否超过 30 行
2. 检查是否有未处理的 Promise
3. 检查是否有 console.log 残留
```

#### 包含反例

```markdown
## 禁止行为
- 不要直接修改 node_modules
- 不要在没有测试的情况下重构
- 不要删除看起来没用的代码（先确认）
```

---

### 从 Skill 到团队标准化

```
个人 Skill                    团队 Skill                    组织 Skill
──────────                    ──────────                    ──────────
~/.claude/skills/             项目/.claude/skills/          内部 marketplace

你的个人习惯                   团队的代码规范                 公司的安全要求
你的提交风格                   项目的架构约定                 统一的审查标准
你的调试方法                   团队的 PR 模板                 合规检查清单
```

**Skill 是团队知识的沉淀**：
- 新人入职 → 安装团队 Skills → 立刻遵循团队规范
- 踩过的坑 → 写成 Skill → 所有人都不会再踩
- 最佳实践 → 固化为 Skill → 一致的高质量输出

---

## 五、Hooks——自动化的触发器（5分钟）

> 三件套的最后一个：Hooks 决定"什么时候自动做"。

### Hooks 是什么？

**一句话**：在特定事件发生时，自动执行的脚本。

```
┌─────────────────────────────────────────────────────────────┐
│                       Hooks 触发流程                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   事件发生           →       Hook 执行        →    结果      │
│                                                             │
│   Agent 写文件       →       格式化脚本        →    代码整齐  │
│   Agent 准备提交     →       lint + test      →    质量保障  │
│   Agent 完成任务     →       通知脚本          →    Slack 消息│
│   会话开始           →       环境初始化        →    加载配置  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

### 与 Git Hooks 的关系

| 维度 | Git Hooks | Claude Code Hooks |
|------|-----------|-------------------|
| **触发源** | Git 操作（commit/push） | Claude Code 事件 |
| **关注点** | 代码提交流程 | Agent 行为全过程 |
| **典型用法** | pre-commit 跑测试 | Agent 写完代码后自动 lint |
| **互补性** | 两者可以同时使用，覆盖不同场景 ||

---

### 常用 Hook 事件

| 事件 | 触发时机 | 用途示例 |
|------|---------|---------|
| `PreToolUse` | Agent 使用工具前 | 拦截危险操作、添加确认 |
| `PostToolUse` | Agent 使用工具后 | 自动格式化、记录日志 |
| `Notification` | Agent 发送通知时 | 转发到 Slack/邮件 |
| `Stop` | Agent 停止时 | 清理临时文件、发送报告 |

---

### 配置示例

Hooks 配置在 `~/.claude/settings.json` 或项目的 `.claude/settings.json` 中：

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "pattern": "\\.ts$",
        "command": "npx prettier --write $CLAUDE_FILE_PATH"
      }
    ],
    "Notification": [
      {
        "command": "notify-send 'Claude Code' '$CLAUDE_NOTIFICATION'"
      }
    ]
  }
}
```

**说明**：
- `matcher`：匹配工具类型（Write、Edit、Bash 等）
- `pattern`：匹配文件路径的正则表达式
- `command`：要执行的 shell 命令
- `$CLAUDE_*`：Claude Code 提供的环境变量

---

### 实用 Hooks 示例

#### 示例 1：TypeScript 文件自动格式化

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "pattern": "\\.(ts|tsx)$",
        "command": "npx prettier --write $CLAUDE_FILE_PATH && npx eslint --fix $CLAUDE_FILE_PATH"
      }
    ]
  }
}
```

#### 示例 2：任务完成桌面通知

```json
{
  "hooks": {
    "Stop": [
      {
        "command": "osascript -e 'display notification \"Task completed\" with title \"Claude Code\"'"
      }
    ]
  }
}
```

#### 示例 3：危险操作确认

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "pattern": "rm -rf|drop table|DELETE FROM",
        "command": "echo '⚠️ 危险操作检测' && read -p '确认执行? (y/n) ' confirm && [ \"$confirm\" = \"y\" ]"
      }
    ]
  }
}
```

---

### 三件套完整协作示例

```
┌─────────────────────────────────────────────────────────────────┐
│              场景：用户说"解决 Issue #123"                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ① Skill 激活：issue-to-pr 工作流启动                            │
│         ↓                                                       │
│  ② MCP 调用：GitLab MCP 读取 Issue #123 详情                     │
│         ↓                                                       │
│  ③ Skill 指导：按 TDD 流程写代码                                  │
│         ↓                                                       │
│  ④ Hook 触发：每次写文件后自动 prettier + eslint                  │
│         ↓                                                       │
│  ⑤ MCP 调用：GitLab MCP 创建 MR                                  │
│         ↓                                                       │
│  ⑥ Hook 触发：MR 创建成功，发送 Slack 通知                        │
│                                                                 │
│  结果：你只说了一句话，代码格式完美，团队已收到通知                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 三件套总结

| 组件 | 解决的问题 | 类比 |
|------|-----------|------|
| **MCP** | Agent 能连接什么系统 | 手（触达外部世界） |
| **Skill** | Agent 该遵循什么流程 | 脑（方法论和经验） |
| **Hook** | 什么时候自动执行动作 | 反射（自动响应） |

```
              ┌─────────────┐
              │   你的指令   │
              └──────┬──────┘
                     ▼
              ┌─────────────┐
              │    Skill    │ ← 定义流程
              └──────┬──────┘
                     ▼
         ┌───────────┴───────────┐
         ▼                       ▼
   ┌─────────────┐         ┌─────────────┐
   │     MCP     │         │    Hook     │
   │  (连接系统)  │         │  (自动触发)  │
   └─────────────┘         └─────────────┘
         ▼                       ▼
   ┌─────────────┐         ┌─────────────┐
   │ GitLab/Slack │         │ 格式化/通知  │
   └─────────────┘         └─────────────┘
```

**核心理念**：把重复的、机械的、容易忘记的事情，交给自动化。你只需要专注于**决策**。

---

## 六、现场挑战（25分钟）

### 流程

1. **收集挑战**（3分钟）：让听众提出想看的场景
2. **筛选执行**（2分钟）：选1-2个适合现场展示的
3. **现场演示**（15分钟）：用Claude Code解决
4. **复盘讨论**（5分钟）：这个过程展示了什么能力/局限

### 引导出题方向

- "有没有什么重复性工作想让AI自动化？"
- "有没有最近卡住的bug想现场试试？"
- "想看AI学一个新框架/语言的过程吗？"

### 保底方案

准备2-3个已跑通的案例备用：

| 案例 | 展示能力 |
|------|---------|
| 快速修复一个真实bug | 效率提升 |
| 给陌生代码加测试 | 理解+生成 |
| 用新框架写个小功能 | 快速学习 |

**切换时机**：
- 冷场没人出题
- 挑战太难/太偏
- 网络/工具出问题（可用录屏讲解）

---

## 七、踩坑与技巧（10分钟）

### 常见坑

| 坑 | 教训 |
|-----|------|
| 上下文爆炸 | 及时 `/compact`，任务完成后开新会话 |
| Agent改错文件 | 用 `CLAUDE.md` 明确项目结构和边界 |
| 过度信任不review | 跑完必看 `git diff`，尤其是删除操作 |
| 任务描述太模糊 | 给具体例子和验收标准，而非抽象需求 |
| 并行时互相踩踏 | 用分支或worktree隔离 |

### 实用技巧

| 技巧 | 效果 |
|------|------|
| 先让AI读代码再改 | 减少幻觉，提高准确率 |
| 小步提交 | 方便回滚，降低风险 |
| 让AI写测试验证自己 | 自动化质量保障 |
| 给失败案例让它学习 | 比描述需求更高效 |

---

## 八、Q&A（10分钟）

### 预判高频问题

**Q: Claude Code和Cursor/Copilot怎么选？**
> A: 不冲突。Cursor适合边写边改，Claude Code适合整块任务。我现在两个都用。

**Q: 付费值不值？**
> A: 如果你日常写代码，很快回本。关键是改变工作方式，而不只是用它补全。

**Q: 安全性/代码隐私怎么处理？**
> A: 敏感项目注意，可以用本地模型或企业版。一般项目风险可控。

**Q: 中文支持怎么样？**
> A: 完全没问题，Claude中文理解很好。

### 冷场备用话题

如果 Q&A 冷场，主动抛出争议性话题引发讨论：

1. **"AI 会让初级开发者失业吗？"**
   - 引导思考：AI 替代的是什么工作？创造的是什么机会？

2. **"代码质量是变好了还是变差了？"**
   - 引导思考：AI 生成的代码需要什么样的 review？

3. **"你敢让 AI 直接 push 到 production 吗？"**
   - 引导思考：信任边界在哪里？什么时候该人工介入？

4. **"AI 编程是'真正的编程'吗？"**
   - 引导思考：编程的本质是什么？

---

## 九、结语：超越工具（10分钟）

> 前面讲的是"术"——具体的工具、配置、技巧。最后聊聊"道"——更本质的思考。
>
> 这部分是整场分享的升华，从操作层面拉升到思维层面。

---

### Agent-Native Mindset

我们经历过几次"Native"思维的转变：

```
Web-Native       →    Mobile-Native    →    Cloud-Native    →    Agent-Native
─────────────────────────────────────────────────────────────────────────────
"为浏览器设计"        "为手机设计"          "为云设计"           "为 Agent 设计"

响应式布局            触摸优先              弹性伸缩             任务拆分优先
链接即入口            App 即入口            API 即入口           Prompt 即入口
```

**Agent-Native 意味着什么？**

| 传统思维 | Agent-Native 思维 |
|---------|-------------------|
| "我来写这段代码" | "我来定义目标，让 Agent 实现" |
| "这个任务怎么做" | "这个任务怎么拆，怎么验证" |
| "学会使用这个工具" | "学会指挥 Agent 使用工具" |
| "提高我的编码速度" | "提高我的决策质量" |
| "写出正确的代码" | "定义清楚什么是正确" |

**核心问题变了**：

> 不再是"我怎么写这段代码"
> 而是"我怎么描述清楚，让 Agent 写对；我怎么验证，确保它是对的"

---

### 什么会过时，什么不会

今天讲的这些——Claude Code、Superpowers、MCP、具体的命令和配置——坦白说，可能几个月后就变了。工具在快速迭代，今天的最佳实践明天可能就是过时的做法。

**但有些东西不会过时**：

#### 持久的能力

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   把模糊需求 ──→ 变成清晰任务      （需求分析能力）              │
│                                                                 │
│   判断代码 ──→ 好坏对错            （技术判断力）                │
│                                                                 │
│   知道何时介入 ──→ 何时放手        （管理 Agent 的智慧）         │
│                                                                 │
│   设计系统 ──→ 而非只写函数        （架构思维）                  │
│                                                                 │
│   为结果负责 ──→ 无论谁写的代码    （责任心）                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

#### 持久的原则

- **先理解，再动手** —— 无论是你写还是 Agent 写
- **小步验证，快速反馈** —— 别让 Agent 闷头跑太久
- **自动化重复劳动** —— 这正是 Agent 存在的意义
- **保持怀疑，保持验证** —— Trust, but verify

---

### Stay Hungry, Stay Foolish

Steve Jobs 的这句话，在 AI 时代有了新的含义：

#### Stay Hungry

> 现在你可能在 Stage 5-6，但 Stage 8 甚至 Stage 10 在等着我们。
>
> 永远有更高效的工作方式等待探索。
>
> 今天觉得"这已经很神奇了"，明天回头看可能只是起点。

#### Stay Foolish

> 敢于让 AI 做更多。
>
> 敢于放手，敢于承认自己不需要亲手写每一行代码。
>
> 不要被"这不是真正的编程"的声音困住。
>
> 真正的编程从来不是敲键盘——是解决问题。

---

### 一个开放问题

最后，留一个问题给大家思考：

> **"当 AI 能写出 90% 的代码时，程序员的价值在哪里？"**

我的思考：

```
                    ┌─────────────────────┐
                    │   定义"对的问题"    │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
     ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
     │ 设计好的系统 │   │ 做难的决策  │   │ 承担最终责任 │
     └─────────────┘   └─────────────┘   └─────────────┘
              │                │                │
              └────────────────┼────────────────┘
                               ▼
                    ┌─────────────────────┐
                    │   这些，AI 做不了    │
                    └─────────────────────┘
```

AI 写代码，你定义什么是"对的"。
AI 提方案，你决定走哪条路。
AI 执行快，你承担结果的责任。

**代码是手段，解决问题才是目的。**

---

### 结束语

> "我们正在见证软件开发方式的代际变革。
>
> 今天的不适应，是明天的新常态。
>
> 今天的前沿探索，是明天的基本技能。
>
> 保持好奇，保持开放，保持动手。
>
> 这是最好的时代。"

---

## 附录

### 带走清单（可打印分发）

分享结束后发给听众的一页纸：

```markdown
# AI 编程快速开始清单

## 今天就能做
- [ ] 安装 Claude Code：npm install -g @anthropic-ai/claude-code
- [ ] 在项目根目录创建 CLAUDE.md，写上项目简介
- [ ] 用 Claude Code 完成一个小任务

## 本周尝试
- [ ] 安装 Superpowers 插件
      /plugin marketplace add obra/superpowers-marketplace
      /plugin install superpowers@superpowers-marketplace
- [ ] 配置一个 MCP Server（推荐从 GitLab/GitHub MCP 开始）
- [ ] 写一个简单的 Hook（如自动格式化）

## 进阶探索
- [ ] 写一个团队专属 Skill
- [ ] 尝试多 Agent 并行（tmux + 多终端）
- [ ] 用 git worktree 隔离不同任务

## 资源链接
- Claude Code: https://docs.anthropic.com/claude-code
- Superpowers: https://github.com/obra/superpowers
- MCP 目录: https://github.com/modelcontextprotocol/servers
- 8阶段模型: https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04

## 记住
- 先理解，再动手
- 小步验证，快速反馈
- Trust, but verify
```

---

### 参考资料

**Vibe Coding / Vibe Engineering**
- Andrej Karpathy - [Vibe Coding 原始推文](https://x.com/karpathy/status/1886192184808149383)（2025年2月）
- Simon Willison - [Vibe Engineering](https://simonwillison.net/2025/Oct/7/vibe-engineering/)（2025年10月）
- [The Vibe Engineering Manifesto](https://www.vibeengineering.ai/p/the-vibe-engineering-manifesto)
- [Vibe Engineering (Manning 书籍)](https://www.manning.com/books/vibe-engineering) - Tomasz Lelek & Artur Skowroński

**8阶段模型**
- Steve Yegge - [Welcome to Gas Town](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04)
- [Yegge's Developer-Agent Evolution Model](https://justin.abrah.ms/blog/2026-01-08-yegge-s-developer-agent-evolution-model.html)

**Superpowers**
- [Superpowers](https://github.com/obra/superpowers) - 半自动化 AI 编程工作流
- Jesse Vincent - [Superpowers for Claude Code](https://blog.fsck.com/2025/10/09/superpowers/) - Superpowers 作者的介绍文章

**MCP (Model Context Protocol)**
- [MCP 官方文档](https://modelcontextprotocol.io/)
- [MCP Server 目录](https://github.com/modelcontextprotocol/servers) - 官方和社区 MCP Server 列表
- [Anthropic MCP 介绍](https://www.anthropic.com/news/model-context-protocol) - MCP 发布公告

**Skill**
- [Claude Code Skills 文档](https://docs.anthropic.com/en/docs/claude-code) - 官方文档
- [Superpowers Skills 源码](https://github.com/obra/superpowers/tree/main/skills) - 学习优秀 Skill 的写法

**Hooks**
- [Claude Code Hooks 文档](https://docs.anthropic.com/en/docs/claude-code/hooks) - 官方文档

### 演示前检查清单

- [ ] Claude Code 登录状态正常
- [ ] 网络稳定（备用热点）
- [ ] 保底案例准备就绪
- [ ] 保底录屏备份
- [ ] 终端字体大小调整（适合投屏）
- [ ] MCP Server 连接测试（如演示 MCP 功能）
- [ ] Superpowers 插件已安装（如演示 Superpowers）
