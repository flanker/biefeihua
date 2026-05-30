# 别废话 / biefeihua.cn — 设计规格

> 一个反对"AI 在职场聊天和文档里写废话"的单页宣言站。
> 灵感来自 [nohello.net](https://nohello.net) 与 [noslopgrenade.com](https://noslopgrenade.com)。

## 决策摘要

| 维度 | 决定 |
|------|------|
| 定位 | 宣言 + ❌/✅ 对比例子 + 可复制 Prompt 工具 |
| 场景 | IM 聊天 + 工作文档（立项书 / 方案书 / 结项报告） |
| 语气 | 犀利吐槽（文案有态度，版面克制） |
| 语言 | 中英双语，页内切换，默认中文 |
| 技术 | 单个 `index.html`，内联 CSS + 极少原生 JS，零依赖零构建 |
| 视觉 | 极简纸面风：浅米白底、大号黑字、克制红(❌)绿(✅)点缀，聊天气泡 / 文档片段卡片 |
| 检测器小玩意 | 不做（保持纯宣言，未来可加） |

## 技术架构

- **单文件 `index.html`**：所有 HTML / CSS / JS 内联，可直接丢任意静态托管（对象存储 / Pages / Nginx）。
- **无构建步骤、无外部依赖、无框架、无网络字体**（用系统字体栈，保证离线与首屏速度）。
- **响应式**：移动端单列、桌面端居中窄栏（阅读宽度 ~640px）。
- **双语实现**：两套文案都写进 DOM，分别带 `lang-zh` / `lang-en` class；JS 在 `<html>` 上切 `data-lang`，CSS 控制显隐。支持 URL hash（`#en` / `#zh`）直链与分享，并记忆到 `localStorage`。
- **可访问性**：语义化标签、足够对比度、`prefers-reduced-motion` 友好、复制按钮有 `aria-live` 反馈。

## 页面结构与最终文案

### ① Hero
- **ZH** 标题：**别废话。说人话。**
  副文：把 AI 生成的一大坨"正确的废话"甩进群里、塞进文档之前，先想清楚：你到底想说什么？
- **EN** 标题：**Cut the fluff. Talk like a human.**
  副文：Before you paste a wall of AI-generated "technically-correct nothing" into a chat or a doc — figure out what you're actually trying to say.

### ② 什么是"废话"（定义）
- **ZH**：废话 = 字数很多，信息很少。读起来像在说什么，其实什么都没说。AI 最擅长这个：四平八稳的排比、滴水不漏的"综上所述"、永远正确的"为了更好地推进工作"。
- **EN**：Fluff = lots of words, little information. It sounds like it's saying something, but it isn't. AI is great at exactly this: tidy parallel structures, airtight "in summary"s, the forever-true "in order to better drive the work forward."

### ③ ❌/✅ 对比 · IM 聊天（聊天气泡 mockup）
- ❌ **ZH**：一条 AI 生成的六段长消息，标题"关于是否采用方案 A 的综合分析与建议"，充斥"综合考虑各方面因素""为了更好地推进""具有重要意义"等套话。
  ❌ **EN**：A six-paragraph AI message titled "A Comprehensive Analysis and Recommendation on Whether to Adopt Option A," stuffed with "taking all factors into consideration," "in order to better drive," "is of great significance."
- ✅ **ZH**：建议用方案 A：成本低 30%，两周能上线。要看对比表吗？
  ✅ **EN**：Go with Option A: 30% cheaper, ships in two weeks. Want the comparison table?

### ④ ❌/✅ 对比 · 工作文档（文档片段 mockup）
- ❌ **ZH**：在当今数字化转型的大背景下，为了更好地响应公司战略、提升业务效能，经过综合研判，本项目应运而生……
  ❌ **EN**：Against the grand backdrop of today's digital transformation, in order to better respond to company strategy and improve operational efficiency, after comprehensive deliberation, this project came into being…
- ✅ **ZH**：这个项目解决一个问题：客服每天手动导报表要花 2 小时。我们做自动化，把这 2 小时还回去。
  ✅ **EN**：This project fixes one thing: support reps spend 2 hours a day exporting reports by hand. We automate it and give those 2 hours back.

### ⑤ 为什么这是个问题（金句区）
- **ZH**
  - 废话稀释信息——每多一句空话，真正重要的那句就更难被看见。
  - 你省下的那 5 分钟，是让 10 个读者各花 5 分钟替你解码。
  - AI 不会替你想清楚，它只会把你没想清楚的东西，包装得像想清楚了。
  - 引用："信息越来越多，意义越来越少。" —— 鲍德里亚
- **EN**
  - Fluff dilutes signal — every empty sentence makes the one that matters harder to find.
  - The 5 minutes you saved? You spent them for 10 readers, each decoding your mess for 5.
  - AI won't think it through for you. It just makes what you haven't thought through look like you have.
  - Quote: "We live in a world where there is more and more information, and less and less meaning." — Jean Baudrillard

### ⑥ 怎么办 · 防废话工具
- **三条原则 / Three rules**
  1. 先结论，后理由。/ Conclusion first, reasons after.
  2. 删到不能再删，意思还在。/ Cut until you can't cut more and the meaning's still there.
  3. 让 AI 帮你想，别让它帮你凑字数。/ Let AI help you think, not pad your word count.
- **可复制 Prompt（喂给 AI，带「复制」按钮，中英各一版）**
  - ZH：直接给结论，用最少的字。不要排比、不要"综上所述"、不要"为了更好地"这类套话。信息不够就直接问我，不要编。
  - EN：Give me the conclusion directly, in as few words as possible. No parallel structures, no "in summary," no "in order to better." If you don't have enough info, just ask — don't make it up.
- **发出去前的检查清单 / Checklist before you hit send**
  - □ 结论在第一句吗？ / Is the conclusion in the first line?
  - □ 删掉一半字，意思还在吗？ / Cut half the words — does it still mean the same?
  - □ 有没有"说了等于没说"的话？ / Any "says-nothing" sentences?
  - □ 收件人 5 秒内能 get 到重点吗？ / Can the reader get the point in 5 seconds?

### ⑦ CTA + Footer
- CTA **ZH**：看到有人往群里、文档里发废话？把这页甩给他。 **EN**：Caught someone lobbing AI slop into a chat or a doc? Send them this page.
- **复制链接 / Copy link** 按钮（`navigator.clipboard`，带复制成功反馈）。
- Footer：`中 / EN` 切换；"灵感来自 nohello.net 与 noslopgrenade.com"；域名 `biefeihua.cn`。

## 交互（原生 JS，极少）
1. **语言切换**：点击 `中 / EN` → 切 `data-lang`、更新 hash、写 `localStorage`；初始读 hash > localStorage > 默认中文。
2. **复制 Prompt**：复制当前语言对应的 Prompt 文本，按钮短暂显示"已复制 ✓"。
3. **复制链接**：复制带语言 hash 的当前 URL。

## 非目标（YAGNI）
- 不做废话检测器 / 评分玩具。
- 不做后端、不收集数据、不加分析埋点。
- 不做构建系统、不引框架、不引网络字体。
- 邮件/周报场景本期不单独成段（聊天与文档已覆盖核心）。

## 成功标准
- 单个 `index.html` 双击即可在浏览器打开，完整可用、无报错。
- 中英切换、两个复制按钮均工作正常。
- 移动端与桌面端排版都干净可读。
- 文案传达"犀利但克制"的态度，截图任意一屏都适合直接转发。
