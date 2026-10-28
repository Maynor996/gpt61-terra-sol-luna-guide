> 在线阅读（GitHub Pages）：https://maynor996.github.io/gpt61-terra-sol-luna-guide/

# GPT-6.1 Terra / Sol / Luna / Astra 中文指南

公开整理的三篇中文 SEO / 选型笔记：ChatGPT Work、Codex、API 上手与家族分流。

## 文章一：GPT-6.1 Terra 上手

# GPT-6.1 Terra 是什么？ChatGPT Work / Codex / API 怎么用上

最近搜索里常出现 **gpt 6.1 terra**、**gpt 6 terra** 这类关键词。简单说：**GPT-6.1 Terra** 是 OpenAI 面向「会干活」场景（看屏、跨应用操作、日常公文与轻量工程）推的一档偏性价比模型；在 API 里模型 ID 为 **`gpt-6.1-terra`**。本文按教程口吻，只讲它是什么、在 ChatGPT Work / Codex / API 里怎么用上，以及怎么自己验手感。

功能、开放范围、价格一律**以 OpenAI 官方当日说明为准**；文中公开口径仅作上手对照。

![OpenAI 官宣 GPT-6.1 Terra](docs/01-terra/01-openai.jpg)

---

## 1. GPT-6.1 Terra 定位一句话

| 维度 | 公开口径（摘要） |
| --- | --- |
| 产品定位 | 更快、更省的 computer use / 视觉推理 + 更自然写作 |
| 相对上一代 | 相对 **GPT-5.6 Terra** 有明显提升（官方在 Agents’ Last Exam 等评测上给出对比） |
| 相对旗舰 | 官方称在部分 Agent 任务上可与 **GPT-6 Astra** 中等努力档接近，且 **token 单价约为 Astra 的约 1/10**（公开口径，以官网价目为准） |
| 入口 | ChatGPT **Work**、**Codex**；API：`gpt-6.1-terra` |

适合先试的人：已经在用 Work / Codex 跑多步任务、或自建 Agent 看截图/点界面的开发者。不适合把它当成「最强一切」——复杂编码、极致推理仍可能要上 Sol / Astra。

---

## 2. Agents’ Last Exam：怎么理解官方说法

公开材料里，OpenAI 用 **Agents’ Last Exam**（面向专业电脑工作流的 Agent 评测）介绍 Terra，例如把建筑图纸做成 3D、逐镜头审片并写时间码日志这类任务。

需要**小心表述**的几点：

1. 分数与成本是 **OpenAI 自己跑出来的公开主张**，不是第三方独立复现结论。  
2. 「与 Astra 持平」类表述通常对应**某一努力档、某一套评测**，不要外推成「全面持平」。  
3. 「更快 / 更省」指该评测语境下的任务完成效率与估算费用，不等于任意场景的 tokens/秒。

上手建议：把官方图表当**选型线索**，用你自己的 3～5 个真实任务做 A/B，再决定默认档。

---

## 3. ChatGPT Work：怎么切到 Terra

1. 使用已开通 Plus / Pro / Enterprise / Edu 等相应权益的账号（以你订阅页当日为准）。  
2. 打开 **ChatGPT Work**（偏多步交付、可调用工具的工作流，而不是普通闲聊 Chat）。  
3. 在模型选择器里找到 **GPT-6.1 Terra**（界面文案可能写作 GPT-6.1 Terra / Terra，以客户端为准）。  
4. **新开一轮**再测，避免旧线程上下文干扰对比。

第一次验收用「真实任务」，例如：

- 给一张界面/产品参考图，让它在可用工具里完成填表、改文件、导出步骤；  
- 或：读一份短文档 → 提取字段 → 按模板输出可直接粘贴的结果。

![社区演示：Terra 看屏完成持续操作类任务](docs/01-terra/02-tibo.jpg)

上图这类「对着参考持续操作」的流程，比空问「你是谁」更能看出 gpt 6 terra 与上一代的差别。

---

## 4. Codex：工程向怎么用上

Codex（桌面 / Cloud 等入口以你当前客户端为准）面向写代码、改仓库、命令行任务：

1. 更新到支持新模型的 Codex / ChatGPT Desktop 版本。  
2. 在任务或会话的模型列表中选择 **GPT-6.1 Terra**。  
3. 用同一仓库任务对比：定位 bug → 改代码 → 说明改动文件；记录是否一次做完、是否乱改范围。

官方也提到：对**最复杂**的编码任务，**GPT-6.1 Sol** 与 **GPT-6 Astra** 往往仍更合适。Terra 更适合当成「日常工程吞吐默认档」来试，而不是唯一答案。

---

## 5. API：模型 ID 与调用注意

开发者在 OpenAI API 中：

- **model**：`gpt-6.1-terra`  
- 权限：控制台 / 文档当日模型列表为准  
- 对比测试：固定 system、tools、reasoning effort，只换 model  

示意（伪代码）：

```text
POST /v1/responses   # 或你当前使用的 Responses / Chat Completions 入口
{
  "model": "gpt-6.1-terra",
  "input": "……你的任务……"
}
```

跑 computer-use / Agent 时，优先用**能看截图、能调工具**的链路测；纯文本补全很难反映 Terra 主打能力。`reasoning.effort` 公开文档支持从 `none` 到 `max` 等档位（以文档当日为准），验收时至少对比 medium 与更高档各一次。

标准 API 公开价目示例（**以官网当日为准**）：约 **$1 / 1M input**、**$5 / 1M output**（另有 cached input 等细则）。

---

## 6. 五分钟验收清单

- [ ] Work / Codex 模型列表能选到 GPT-6.1 Terra  
- [ ] API 用 `gpt-6.1-terra` 能正常返回  
- [ ] 至少完成 1 个「看屏 / 跨步骤」真实任务  
- [ ] 与当前默认模型（如 Sol 或 5.6 Terra）同任务对比耗时与费用  
- [ ] 记下失败样例：拒操作、看错控件、中途停，便于改 prompt / 工具描述  

---

## 7. 小结

**GPT-6.1 Terra（`gpt-6.1-terra`）** 更适合当作 Agent / computer-use / Codex 日常干活的默认候选：网页端走 ChatGPT Work 与 Codex，开发者走 API。先用同一任务对比完成率、耗时、账单，再决定是否替换现有默认档。

Agents’ Last Exam 等数字请按「公开主张、场景相关」理解；一切以 OpenAI 官方当日页面为准。本文只做上手整理，不构成对任何第三方服务的背书。

---

## 附：本地对照环境（可选）
直连不稳或只想先摸手感时，可自行复制下列入口做对照（纯文本）：
网页对话对照：https://trygpt.asia/list/#/home
包月额度对照：https://momoai.asia/home
多模型 API 对照：https://tryallapi.com/
订阅路径对照：https://chongzhi.trygpt.asia/
与官方无关；价格以各页当日为准。

---

## 文章二：Sol vs Terra

# GPT-6.1 Sol vs GPT-5.6 Terra：差在哪、谁更适合跑 Agent

选型时最容易搜到的两句是：**sol vs 5.6 terra**，以及「现在跑 Agent 该上 Sol 还是 Terra」。本文做对照笔记：一边是 **GPT-6.1 Sol**（新一代偏强档），一边是仍常见的 **GPT-5.6 Terra**（上一代性价比档）；文末顺带说明何时该选同代的 **GPT-6.1 Terra**。

价格与能力数字均标为**公开口径 / 以官网为准**，不编造站外榜单分数。

![GPT 家族价目示意（公开材料截图，以官网当日为准）](docs/02-sol-vs-terra/01-pricing.jpg)

---

## 1. 先分清在比什么

| 名称 | 代际 | 大致定位（公开口径） |
| --- | --- | --- |
| **GPT-6.1 Sol** | 6.1 | 接近旗舰体验的复杂工作 / 编码 / Agent，单价显著低于 Astra |
| **GPT-5.6 Terra** | 5.6 | 上一代「干活平衡档」，偏 computer use 与日常吞吐 |
| （对照）**GPT-6.1 Terra** | 6.1 | 新一代平衡档；官方称相对 Astra 约 **1/10** token 成本量级 |
| （对照）**GPT-6 Astra** | 6 | 旗舰；Sol 公开口径为 **near-Astra、约 1/5 价** |

很多人把「Sol vs Terra」混在一起比：其实要先问——你是拿 **6.1 Sol 换掉 5.6 Terra**，还是在 **6.1 Sol 与 6.1 Terra** 之间选默认 Agent？下文两段都写清楚。

---

## 2. 公开口径：成本阶梯（务必以官网为准）

标准 API 价目（每 1M tokens，**公开页摘要，可能调整**）：

| 模型 | Input（约） | Output（约） | 相对关系（公开口径） |
| --- | --- | --- | --- |
| GPT-6 Astra | $10 | $50 | 旗舰参照 |
| GPT-6.1 Sol | $2 | $10 | **近 Astra 能力、约 1/5 价**（公开口径） |
| GPT-6.1 Terra | $1 | $5 | 相对 Astra 约 **1/10** token 单价量级（公开口径） |
| GPT-5.6 Terra | $2 | $12 | 上一代 Terra；输入侧常与 6.1 Sol 同量级、输出往往更贵 |

读表方式：

- **6.1 Sol vs 5.6 Terra**：输入标价接近时，Sol 通常代表「同价位附近换更强一代」；是否划算看你任务失败率与返工成本。  
- **6.1 Terra**：若公开价目仍成立，往往是「比 Sol 再省一档、比 5.6 Terra 更新一代」的默认候选。  
- ChatGPT Work / Codex 套餐额度消耗也按模型不同；同一额度下 Terra 往往能多跑一些任务（官方宣传口径），**以你账单为准**。

---

## 3. 能力侧：短列表对比（不堆未经标注的分数）

下面只列**可核对的公开主张方向**，不发明第三方榜数字：

| 维度 | GPT-6.1 Sol | GPT-5.6 Terra |
| --- | --- | --- |
| 代际 | 6.x 对齐 / 编码 / 协作风格升级后的强档 | 5.6 代平衡档 |
| Agent / 专业工作流 | 官方在 Agents’ Last Exam 等评测上给出较高档表现 | 可用，但官方用 6.1 Terra 对比时强调相对 5.6 Terra 有明显跃升 |
| 复杂编码 | 公开材料倾向：难题更站 Sol / Astra | 日常改仓可以，难题易触顶 |
| 速度与费用 | 比 Astra 明显更省；未必是最快最便宜 | 上一代性价比；相对 6.1 系列可能「又慢一点又贵一点」 |
| 入口 | Work / Codex / API（`gpt-6.1-sol`）；Chat 侧是否可见以当日开放为准 | 视账号与产品线是否仍保留 5.6 档 |

**Agents’ Last Exam** 等图表请当作厂商公开主张：同一努力档、同一评测设定下的对比线索，不是跨厂商、跨场景的总排名。

---

## 4. 什么时候选 Sol？什么时候留 / 上 Terra？

### 更偏向 GPT-6.1 Sol 的情况

- Agent 失败一次代价高（线上变更、客户交付、长链路工具调用）。  
- Codex 任务偏「大重构、跨模块、要接近可合并质量」。  
- 你已经觉得 5.6 Terra「差不多能做但经常返工」，想用同预算附近换一代。  
- 需要更接近 Astra 的表现，但暂时不想付 Astra 全价 → 公开口径下 Sol 常是「近旗舰、约 1/5 价」的折中。

### 更偏向 Terra（优先考虑 6.1 Terra；若仍停在 5.6 则计划升级）的情况

- 高并发、高吞吐：发票录入、看图填表、批处理看屏任务。  
- 失败可重试，更在意单次成本与速度。  
- 想把 Astra / Sol 留给难题，Terra 做默认工人。  
- 仍在用 **GPT-5.6 Terra**：若账号已开放 **GPT-6.1 Terra**，多数「日常 Agent」场景更建议先试 6.1，而不是长期停在 5.6。

### 一张决策小表

| 你的约束 | 更建议 |
| --- | --- |
| 预算紧、任务可重试、量大 | 6.1 Terra（或 Luna 分流简单请求） |
| 要稳、偏难、编码深 | 6.1 Sol |
| 极致质量、不计成本 | Astra |
| 还在 5.6 Terra，且已开放 6.1 | 先同任务 A/B 升到 6.1 Terra，再决定要不要上 Sol |

---

## 5. 十分钟 A/B 怎么跑

1. 准备 **同一任务脚本**（同一仓库 / 同一套工具 / 同一截图）。  
2. 分别跑：`gpt-5.6-terra`（若仍可用）、`gpt-6.1-terra`、`gpt-6.1-sol`。  
3. 只记三件事：**是否完成、耗时、token/费用**。  
4. 难题加一轮更高 `reasoning.effort`，避免「默认档没跑满」造成误判。  
5. 以你自己的日志为准，不要只背宣传句。

---

## 6. 小结

- **sol vs 5.6 terra**：多数是「新一代强档 vs 上一代平衡档」——若任务偏难、返工贵，优先试 **GPT-6.1 Sol**；若只是日常吞吐，优先看是否已能用上 **GPT-6.1 Terra**。  
- 公开口径提醒：**Terra ≈ Astra 的约 1/10 token 成本量级；Sol ≈ 近 Astra、约 1/5 价**——均须标注为公开口径，并以官网当日价目与产品页为准。  
- 跑 Agent 没有唯一正确答案：用同一任务量费用与完成率，比纠结型号名字更有效。

---

## 附：本地对照环境（可选）
直连不稳或只想先摸手感时，可自行复制下列入口做对照（纯文本）：
网页对话对照：https://trygpt.asia/list/#/home
包月额度对照：https://momoai.asia/home
多模型 API 对照：https://tryallapi.com/
订阅路径对照：https://chongzhi.trygpt.asia/
与官方无关；价格以各页当日为准。

---

## 文章三：Luna / Terra / Sol / Astra 选型

# Luna / Terra / Sol / Astra 怎么选？GPT-6.1 家族定位一次看清

搜 **luna terra sol**、**sol vs astra**、**sol release** 时，信息往往散落在多篇官宣里。本文把 **GPT-6 / GPT-6.1** 家族四档——**Luna、Terra、Sol、Astra**——按定位、价位、适用场景串成一份选型笔记，方便做默认模型与分流策略。

开放范围、价目、是否出现在 Chat / Work / Codex / API，一律 **以 ChatGPT / API 当日开放为准**；不确定具体日历日时不编造上线日期。

![OpenAI 模型家族相关官宣示意](docs/03-family/02-openai.jpg)

---

## 1. 家族地图（从轻到强）

| 档位 | 常见型号示例 | 一句话定位 | API 名示例（以文档为准） |
| --- | --- | --- | --- |
| **Luna** | GPT-6 Luna | 最轻量、最便宜的日常与高吞吐 | `gpt-6-luna` |
| **Terra** | GPT-6.1 Terra | 看屏 / computer use / 日常 Agent 的性价比默认档 | `gpt-6.1-terra` |
| **Sol** | GPT-6.1 Sol（及 GPT-6 Sol） | 近旗舰的复杂工作与编码，价格明显低于 Astra | `gpt-6.1-sol` / `gpt-6-sol` |
| **Astra** | GPT-6 Astra | 旗舰：最强深度与对齐取向的兜底 | `gpt-6-astra` |

记忆口诀：**Luna 跑量 → Terra 干活 → Sol 攻坚 → Astra 封顶。**

---

## 2. 价目阶梯（公开口径）

![家族价目示意（截图仅供对照，以官网当日为准）](docs/03-family/01-pricing.jpg)

标准 API 公开价摘要（每 1M tokens，**可能调整，以官网为准**）：

| 模型 | Input | Output | 选型含义 |
| --- | --- | --- | --- |
| GPT-6 Astra | ~$10 | ~$50 | 最贵；难题与高风险交付 |
| GPT-6.1 Sol | ~$2 | ~$10 | 公开口径：**near-Astra，约 1/5 价** |
| GPT-6.1 Terra | ~$1 | ~$5 | 公开口径：相对 Astra 约 **1/10** token 单价量级 |
| GPT-6 Luna | ~$0.10 | ~$0.50 | 海量简单请求、预过滤、草稿 |

Work / Codex 若按额度计量：同一套餐下，选更轻的档通常能多跑任务——具体仍看官方说明与你的用量报告。

---

## 3. 各档展开：什么时候用

### Luna：跑量与分流

- 分类、抽取、短回复、简单改写、高 QPS 网关前置。  
- 作为「贵模型之前的过滤器」：Luna 做完再决定是否升级到 Terra / Sol。  
- 不指望它稳定完成长链路 computer use 或大重构。

### Terra（重点关注 GPT-6.1 Terra）：默认工人

- 视觉理解 + 精确一点的电脑操作 + 更自然写作，是官方给 6.1 Terra 的主打组合。  
- 适合：填表、对图操作、日常 Codex、多数业务 Agent。  
- 相对 **GPT-5.6 Terra**：官方在 Agents’ Last Exam 等评测上给出明显提升主张——仍请按「公开主张」理解，并用自有任务验收。  
- 复杂编码封顶时，官方也提示可改走 Sol / Astra。

### Sol：近旗舰攻坚（含 sol release / 可用性说明）

- 公开定位接近 Astra 的专业工作、编码、computer use，但成本低一截。  
- **可用性**：Sol / 6.1 Sol 出现在 Chat、Work、Codex、API 的哪些表面，**以 ChatGPT / API 当日开放为准**；历史上存在「先在 Work / Codex / API，Chat 侧逐步放开」的情况，**请勿把不确定的具体日历日写进生产配置假设**。  
- API 侧常见 ID：`gpt-6.1-sol`（以文档列表为准）。  
- 当你已经用 Terra「能做但不稳」时，Sol 往往是下一档，而不是直接跳 Astra。

### Astra：封顶与兜底

- 最难推理、最高风险交付、需要旗舰对齐与深度的任务。  
- 适合作为「升级路径的最后一跳」或关键路径强制指定，而不是全部流量的默认模型。

---

## 4. 三组高频对比

### luna terra sol（怎么叠起来用）

```text
请求进入
  ├─ 简单 / 可缓存 → Luna
  ├─ 常规 Agent / 看屏 / 日常编码 → Terra
  └─ 失败重试或标记为 hard → Sol（仍失败 → Astra）
```

### sol vs astra

| 问题 | 更稳妥的答案 |
| --- | --- |
| 能不能用 Sol 代替 Astra？ | 多数非极端任务可以先试；公开口径称 Sol 近 Astra、约 1/5 价 |
| 什么时候必须 Astra？ | 失败成本极高、内部规范要求旗舰、Sol 多次触顶 |
| 价格直觉 | Astra 最贵；Sol 是「性价比旗舰感」常见选择 |

### sol release（上线与看到与否）

不要写死「某月某日一定全量可见」。实操核对清单：

1. ChatGPT 模型选择器（Chat / Work 分开看）  
2. Codex 桌面或 Cloud 的模型列表  
3. API 控制台模型列表与文档定价页  
4. 客户端是否已更新到支持该模型的版本  

任一项当日不可见，都先当「未对你的账号/区域开放」，而不是配置写错唯一可能。

---

## 5. 场景速查表

| 场景 | 优先 | 备选 |
| --- | --- | --- |
| 客服草稿 / 字段抽取 / 高 QPS | Luna | Terra |
| 看屏填表、多步业务 Agent | Terra | Sol |
| 大重构、难 bug、长 Codex 任务 | Sol | Astra |
| 关键交付、最终质检 | Astra | Sol 人工复核 |
| 还在用 5.6 Terra | 先试 6.1 Terra | 不够再上 Sol |

---

## 6. 小结

- **Luna / Terra / Sol / Astra** 是一条清晰的成本—能力阶梯，而不是四个互斥「信仰」。  
- 搜 **luna terra sol** 时，先定默认档（多数团队会落在 Terra），再用 Sol / Astra 做升级路径。  
- **sol vs astra**：公开口径下 Sol 提供近旗舰体验与约 1/5 价；是否替下 Astra 用你的失败成本说话。  
- **sol release / 可见性**：以 ChatGPT 与 API **当日开放**为准，不编造具体日历日。  

价目与评测主张均可能更新；上线前再核对官方文档与价目页。本文仅供选型整理。

---

## 附：本地对照环境（可选）
直连不稳或只想先摸手感时，可自行复制下列入口做对照（纯文本）：
网页对话对照：https://trygpt.asia/list/#/home
包月额度对照：https://momoai.asia/home
多模型 API 对照：https://tryallapi.com/
订阅路径对照：https://chongzhi.trygpt.asia/
与官方无关；价格以各页当日为准。
