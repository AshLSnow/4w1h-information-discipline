# 4W1H 信息纪律

一个 [Claude Code](https://claude.com/claude-code) Skill：用 **4W1H**（Who / When / Why / What / How）评估新闻链接、文章、公告与传闻的信息价值；当你关注自身决策时，帮助深入审视信息如何影响你的判断。

## 它解决什么问题

大多数“这条信息值不值得信”的回答，要么止于复述原文，要么止于搜了一下标题。这个 skill 要求 agent 真正做核验：追溯原始信源、交叉核对独立证据、主动搜索反证，并把「文章声称」「原始材料记录」「独立证据支持」「agent 推断」分开陈述。

它同时拒绝两种偷懒：不因为来源有利益关系就判定为假，也不因为没找到反证就判定为真。

## 两种模式

| 模式 | 典型输入 | agent 的工作 | 交付 |
|---|---|---|---|
| **快速评估** | 链接、粘贴文章、“这条新闻信息价值如何”“值得看吗” | 自主读取、多轮询证、评估文章价值 | 简短价值卡，关键证据和局限可追溯 |
| **个人深思** | “这让我焦虑”“我该如何判断 / 决定”“带我深入思考” | 将事实核验与个人目标、预期、情绪、行动选择结合 | 判断地图、行动条件，必要时少量提问 |

“快速”指低交互成本和精简交付，**不代表降低核验标准**——agent 仍需做真实核验。

## 安装

克隆到 Claude Code 的 skills 目录：

```bash
# macOS / Linux
git clone https://github.com/AshLSnow/4w1h-information-discipline.git \
  ~/.claude/skills/4w1h-information-discipline
```

```powershell
# Windows PowerShell
git clone https://github.com/AshLSnow/4w1h-information-discipline.git `
  "$env:USERPROFILE\.claude\skills\4w1h-information-discipline"
```

也可以只放进某个项目（`.claude/skills/`），仅在该项目内生效。

## 使用

安装后直接给材料即可，不需要先声明“请使用某个 skill”：

```
https://example.com/some-article   这条值得看吗
```

```
这让我很焦虑，我该怎么判断要不要跟进
```

## 目录结构

```
.
├── SKILL.md                      # 入口：模式路由、4W1H 定义、证据与行为约束
├── references.md                 # 方法来源与设计边界
└── references/
    ├── quick-assessment.md       # 快速评估：三轮询证流程、核验预算与停止条件、价值卡模板
    ├── value-rubric.md           # 信息价值判据：分维度判断与高 / 中 / 低 / 待定校准
    └── personal-reflection.md    # 个人深思：从接收信息到自主判断的流程
```

参考文件按需加载，不需要一次读完。

## 设计边界

- 本 skill 的价值判据是为具体使用场景设计的**实践规则**，不是经过统计验证的量表，也不代表任何机构的官方标准。
- 4W1H 的五问结构沿用自 `references.md` 中所列文章的提法；SIFT 等外部方法仅作为核验流程参考，不为其价值评级背书。
- 分析不授权任何外部行动（转发、联系作者、交易等），也不自动创建持续监控。
- 输出分开给出**主张可信度**、**文章信息价值**、**个人行动适用性**，禁止用一个总分把三者混为一谈。

## 许可

本仓库尚未附带开源许可证文件。若你希望他人可以自由使用、修改与分发，建议补充一份（如 MIT）。
