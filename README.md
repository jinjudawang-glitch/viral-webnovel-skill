# viral-webnovel

`viral-webnovel` 是一个用于推进中文连载网文创作的 Codex Skill。

它不是“一次性让 AI 写完一本小说”的提示词，而是一套连载工作流：先判断题材能不能写，再搭故事骨架，再按 5 章一轮持续推进，写完还会压缩记忆、诊断爽点和修掉 AI 味。

默认方向是番茄/七猫式高追读爽文，尤其适合玄幻修仙、规则反转、废柴逆袭、宗门打脸、强钩子开局和中长篇连载。

## What It Produces

这个 skill 可以产出：

- 20 个爆款网文选题池
- 每个选题的点击潜力、新颖度、颠感上限、连载稳定性评分
- 书名、简介、一句话钩子
- 故事圣经
- 前 30 章卷纲
- 前 10 章试读计划
- 5 章一轮的正文续写
- 每轮后的活跃账本、冷库、伏笔和爽点复盘
- 读者弃读风险诊断
- 下一轮 3 条剧情分支
- 去 AI 味正文重写

## Why Not Just Prompt AI Directly?

普通提示词通常是：

```text
帮我写一本番茄风格玄幻爽文。
```

这能写出几章，但很容易出现：

- 前几章还行，后面开始重复
- 伏笔丢失
- 反派只会震惊
- 主角被剧情推着走
- 设定越写越散
- 正文有明显 AI 说明文味道

`viral-webnovel` 的区别是：它把网文创作拆成一套可控流程。

```text
选题池 -> 人工定选题 -> 故事圣经 -> 前30章卷纲 -> 前10章试读 -> 5章一轮正文 -> 滚动压缩 -> 诊断 -> 分支选择 -> 去AI味
```

它更像一个连载编辑助理，而不是单个写作提示词。

## Example Premise

测试时生成过一个题材：

```text
《我写差评，天道连夜整改》
```

设定是：修仙世界像一个巨大的服务系统。雷劫、灵根检测、宗门考核、秘境报名、飞升审核都有流程。

主角被宗门冤枉，要被引雷废根。他没有突然觉醒血脉，而是在识海里打开天道反馈面板，给雷劫写了一星差评：

```text
处罚依据未向用户公示。
证据链未完成复核。
雷劫服务态度恶劣，疑似配合执法堂暴力催收。
```

然后雷停了。

```text
投诉已受理。
涉事雷劫暂停执行。
```

这个 skill 会继续把这个设定拆成故事圣经、前 30 章卷纲、前 10 章试读计划和 5 章一轮正文。

## Install

使用 Codex 的 skill installer 从 GitHub 安装：

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo jinjudawang-glitch/viral-webnovel-skill \
  --path viral-webnovel \
  --name viral-webnovel
```

## Usage

安装后可以这样调用：

```text
用 $viral-webnovel 生成20个番茄/七猫式玄幻修仙爆款选题池，目标80-120章。
```

也可以指定任务：

```text
用 $viral-webnovel 给这个题材生成故事圣经。
```

```text
用 $viral-webnovel 按前10章试读计划写第1-5章，每章1000字以上。
```

```text
用 $viral-webnovel 诊断这5章哪里可能导致读者弃读，并给我3条后续分支。
```

## Skill Structure

```text
viral-webnovel/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── chapter-template.md
    ├── diagnose-loop.md
    ├── idea-scoring.md
    ├── memory-system.md
    ├── outline-structure.md
    ├── platform-patterns.md
    ├── rewrite-humanization.md
    └── story-bible-template.md
```

## Notes

- 默认输出中文。
- 默认写 80-120 章体量的短中篇连载。
- 正式正文默认每章 1000-1800 中文字符。
- 如果用户要求最新平台趋势，使用者需要联网检索并引用来源；否则使用 skill 内置平台模式库。
- 不建议让它一次性写完整本。推荐 5 章一轮推进。
