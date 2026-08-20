# Low-Level Design Skill

一个面向 AI 编码助手（Claude Code / Codex）的 skill，用于在**修改 / 新增 / 重构代码**时，参考 low-level design 思维——SOLID 原则与常用设计模式——写出干净、易维护的代码。

核心立场：**按需应用、优先简单，绝不生搬硬套设计模式。** 设计模式是识别问题的词汇表，不是待办清单。

## 目录结构

- `SKILL.md` —— 主指令：触发条件、四步判断工作流、反模式警告
- `references/solid-principles.md` —— SOLID 五大原则速查（定义 / 识别信号 / 反例 / 何时该用）
- `references/design-patterns.md` —— 18 个设计模式目录（意图 / 识别信号 / 常见误用）
- `references/examples/` —— bad / good 示例代码
  - `oops/` —— OOP 基础与 UML（abstraction、encapsulation、inheritance、association、aggregation、composition、dependency）
  - `solid/` —— 五大原则的 bad / good 对照
  - `patterns/` —— behavioral / creational / structural 三类 18 个模式
  - `ride-sharing/` —— 综合项目（bad 版 vs good 版）

## 安装

> 两种工具共用同一份 `SKILL.md`（YAML frontmatter + Markdown），只需分别软链到各自的 skills 目录即可。目录名建议用 `low-level-design`（与 `name` 字段一致）。

### Claude Code

```bash
# 用户级（所有项目可用）
mkdir -p ~/.claude/skills
ln -s "$PWD" ~/.claude/skills/low-level-design

# 或项目级（仅当前项目）
mkdir -p .claude/skills
ln -s "$PWD" .claude/skills/low-level-design
```

### Codex

```bash
mkdir -p ~/.codex/skills
ln -s "$PWD" ~/.codex/skills/low-level-design
```

启用 skills 功能（一次性）：

```bash
codex --enable skills
# 或写入 ~/.codex/config.toml：
# [features]
# skills = true
```

> 提示：也可用 `cp -r` 代替软链 `ln -s`；软链能保持后续更新同步。

## 使用

- **Claude Code**：skill 会依据 `SKILL.md` 的 description 在相关任务中自动触发，也可手动引用。
- **Codex**：用 `/skills` 查看、`$low-level-design` 手动调用；description 同样用于自动触发。
- 当你让 AI 修改代码、加功能、重构或 review 时，skill 会引导它走判断框架：**识别坏味道 → 定位真实痛点 → 选择最小解法 → 验证是否更简单**。只有出现明确的模式信号时才参考对应模式，不会为了套模式而套模式。
