# English Less AI Tone

[English](README.md)

用于英文成稿的保守编辑 Skill。减少空泛、冗长或重复的表达，同时保留原意、事实、引用、限定词、语体和文章结构。

**只修改明确命中规则的部分，其余文字保持不变。**

## 安装

使用 Skills CLI：

```bash
npx skills add chows3539-droid/english-less-ai-tone
```

安装到 Codex 的全局技能环境：

```bash
npx skills add chows3539-droid/english-less-ai-tone --global --agent codex
```

也可以将本仓库克隆到你的智能体支持的 skills 目录。标准 Codex 环境可使用：

```bash
git clone https://github.com/chows3539-droid/english-less-ai-tone.git "${CODEX_HOME:-$HOME/.codex}/skills/english-less-ai-tone"
```

目标目录已存在时，不要重复执行克隆命令。受管理的 ChatGPT Work 环境可能需要通过其技能导入或持久化流程安装。未立即发现技能时，刷新技能列表或重新打开会话。

## 使用

```text
使用 $english-less-ai-tone 修改下面的英文。
保留原意、事实、引用、限定词和文章结构，保持原有正式程度。
只输出修改后的正文。

[粘贴英文]
```

想查看修改理由，可加：`逐项列出修改前后对照和规则编号。`

需要语法纠正，可加：`另外检查语法，并单独标明语法修改。` 默认只处理规则内的文风问题。

## 处理范围

前七类规则覆盖空泛开场、冗长短语、可简化的名词化动作、重复说明、可简化的递进表达、重复过渡词，以及机械重复的句式。每类规则都有适用条件和例外，完整内容见 [SKILL.md](SKILL.md)。

保留学术语气、有实际作用的被动语态、专业术语和必要的限定词。不会因为出现破折号、长句或某个单词，就认定文字存在问题。不会编造案例、数字、个人经历或引用。

## 融入反防御性写作

E8–E10 参考 [Kiterlin/anti-defensive-writing](https://github.com/Kiterlin/anti-defensive-writing)，处理不提供信息的自我辩解、以排除事项开头的范围说明，以及表达同一种不确定性的重复措辞。

例如：`The difference may perhaps reflect selection bias` 可以改为 `The difference may reflect selection bias`。但 `The study does not establish causality` 必须保留，因为它交代真实的研究边界。

保留真实道歉、必要对比、方法局限、不利结果和安全或法律限制。这里仅融入局部编辑规则，不默认重组段落或将局限移到其他章节，也不为了显得自信而加强结论。

## 示例

修改前：

> It is worth noting that the survey included 42 participants. The team met in order to review the responses.

修改后：

> The survey included 42 participants. The team met to review the responses.

下句保持原样，以保留不确定性和因果区别：

> The findings may indicate an association, not a causal effect.

示例仅演示编辑方式，不是作者身份判断或检测效果证明。

## 局限与来源

适用于英文论文草稿、雅思作文、邮件和报告等成稿。它不是翻译器、事实核查工具或自动改写脚本；英文规则是编辑启发式规则，尚无实证验证。使用效果取决于执行 Skill 的模型，结果仍需人工检查。不能判断文本由谁写作，也不保证降低 AI 检测率或提高雅思分数。

本项目参考 [larashero3-dotcom/lieflat-less-ai-tone](https://github.com/larashero3-dotcom/lieflat-less-ai-tone) 的白名单改写与信息保留方法，是独立英文改编版，并非官方英文版。原项目的中文语料统计不能作为这些英文规则的证据。

本项目借助 ChatGPT 创建，采用 [MIT License](LICENSE)，保留两个上游项目的版权声明。反防御性规则参考版本为 `f516147d017a3fe43ae99192cb89d8261b0c8679`；本项目并非其官方版本或完整替代。
