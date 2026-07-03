# Cursor + Claude + Codex：内容站自动写作流程怎么搭

> 更新时间：2026/07/02 · 账号C · 工作流向

用 AI 写内容站文章，不是打开 ChatGPT 问一句就完事。要跑通"选题 → 写稿 → 审校 → 发布"的完整链路，需要把几个工具串起来。这篇讲我自己在用的流程。

- [2026-07-03｜不是程序员，怎么用 Codex 帮你干活（法务招聘都在用）](posts/20260703-codex-non-programmer-workflow.md)

> 🌟 **流程中用到的第三方服务（非 OpenAI 官方）：**
> • [ZEOGPT](https://www.zeogpt.com/register?ref=Ac3KbS3F) — 写稿主力，多模型切换（GPT-5.5 / Claude / Gemini 等）
> • [GPTBuy](https://gptbuys.com/?ref=LIJUN) — 需要官方 ChatGPT Plus/Pro 时，协助充值
> • [ZeoAPI](https://www.zeoapi.com/register?aff=FM4J) — API 中转，Cursor 里批量调用走这个

---

## 整体流程

四步走，每步用不同工具：

| 步骤 | 干什么 | 用什么工具 | 为什么用它 |
| --- | --- | --- | --- |
| 1. 选题 | 找关键词、定方向 | GPT-5.5 对话 | 头脑风暴快，能批量出选题 |
| 2. 写稿 | 生成初稿 | Cursor + Claude/GPT API | 在编辑器里直接写，上下文完整 |
| 3. 审校 | 降 AI 味、查事实 | 人工 + GPT 辅助 | AI 查格式问题，人查味道 |
| 4. 发布 | 格式化 + 推送 | Codex / 脚本 | 批量处理 HTML、推 Git |

---

## 第一步：选题

打开 [ZEOGPT](https://www.zeogpt.com/register?ref=Ac3KbS3F)，选 GPT-5.5 Thinking 或 Deep Research 模式，给它一个 prompt：

> 我在做一个 AI 工具教程站。目标读者是国内想用 ChatGPT 但不会翻墙的人。给我 10 个选题方向，每个用一句话描述角度，不要太宽泛。

出来的选题再筛一轮：有没有搜索量、我能不能写出干货、跟已有内容有没有重复。

---

## 第二步：在 Cursor 里写稿

为什么不直接在 ChatGPT 网页版写？因为：

- Cursor 里可以把大纲、素材、参考文档都放在上下文里
- 可以切模型——写正文用 Claude Opus 4.8，查数据用 GPT-5.5 Thinking

API 走 [ZeoAPI](https://www.zeoapi.com/register?aff=FM4J) 中转，国内访问更方便，按 token 计费。通常兼容 OpenAI API 调用格式，具体以平台文档为准。支持多模型切换。

### 实际操作

1. 新建 .md 文件，先写大纲（手动）
2. 每个章节用 AI 扩写，一节一节来
3. 写完一节回头读，不对的地方马上改
4. 全文写完后整体通读一遍

---

## 第三步：审校降 AI 味

AI 写的文章最大的问题不是错，是"AI 腔"。读起来像在读产品说明书。

我的审校清单：

- 删掉"综上所述""值得注意的是""在当今时代"
- 句子超过 30 字就拆
- 有没有我自己的态度（不是中立描述）
- 有没有具体数字或个人经历
- 大声读一遍，卡顿的地方改掉

---

## 第四步：格式化发布

文章写好是 Markdown，发布需要转成 HTML 或推到 CMS。

这步可以用 Codex 或脚本自动化：

- Markdown → HTML 转换
- 自动插入推广链接块
- Git commit + push
- 触发部署

Codex 的具体可用方式以 OpenAI 官方说明及各平台实际接入为准。如果你用 ChatGPT Pro 里的 Codex，可以直接描述任务让它跑。ZEOGPT 也提供 Codex 类体验入口。没有这些的话，写个 Python 脚本也能搞定。

---

## 成本

| 工具 | 月费 | 用途 |
| --- | --- | --- |
| ZEOGPT | ¥30-60 | 选题 + 快速对话 |
| ZeoAPI | 按量（约 ¥50-100） | Cursor 里的 API 调用 |
| Cursor | $20 | 编辑器 |
| 合计 | 约 ¥200-300/月 | 日产 2-3 篇的量 |

比雇一个写手便宜，但你得花时间审校和把控质量。AI 负责量，你负责味道。

> 💡 关键心得：不要让 AI 一口气写完整篇。分段写、分段审，质量比"生成全文再改"好得多。

------

## 长期更新版

这篇内容后续会继续整理到网站教程中，方便统一查看：

- ChatGPT 中文教程站：https://www.chinachatgpt.com/
- 相关主题：ChatGPT 中文版、Codex、API 中转、AI 工具教程


**按需求选入口：**普通使用（选题/写稿/对话）→ [ZEOGPT](https://www.zeogpt.com/register?ref=Ac3KbS3F) · 官方订阅协助 → [GPTBuy](https://gptbuys.com/?ref=LIJUN) · 开发者 API 调用 → [ZeoAPI](https://www.zeoapi.com/register?aff=FM4J)
以上均为第三方服务，与 OpenAI 无官方授权关系。
