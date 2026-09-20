---
title: 解决 Token 焦虑：我的 AI 工具与额度清单
published: 2026-09-20
updated: 2026-09-20
description: 个人整理的九款 AI 编程与办公工具，记录免费额度、低价套餐、试用经验，以及平时关注的资源入口。
image: ./images/token-anxiety.avif
tags: [AI工具, Token, AI编程, 免费额度, 个人整理]
category: 技术实践
slug: token-anxiety
draft: false
---

最近攒了一些 AI 工具的免费额度和低价套餐信息，散在收藏夹和聊天记录里，找起来挺麻烦，干脆整理成一篇。

下面一共九款，免费、试用、付费的都有，顺手附上领取方式和一些使用笔记。活动不一定一直有，碰到能用的就试试。绑卡试用的记得取消续费，这个最容易忘。

## 一、先看这张表

| 工具 | 值得关注的地方 | 入口 |
| --- | --- | --- |
| Cline | 免费额度约 1500 万 Token；另有低价 Cline Pass | [Cline](https://app.cline.bot/) |
| Zed / Delta | Zed Pro 试用 14 天，含 5 美元试用额度，两款产品共享 | [Zed](https://zed.dev/) · [Delta](https://delta.dev/) |
| Kiro | 首次升级付费套餐可获 20 美元抵扣；Pro 每月 1000 积分 | [Kiro](https://kiro.dev/) |
| Antigravity | 使用谷歌 Gemini，个人整理中的低成本方案 | [Antigravity](https://antigravity.google/) |
| AtomCode | 每周有免费 Token Plan 可领取 | [AtomCode](https://atomcode.atomgit.com/) |
| WorkBuddy | 国际版绑卡可试用 7 天 Pro | [WorkBuddy 邀请链接](https://workbuddy.ai/invite?code=ZVA8L3WT) |
| 智谱 AutoClaw | 下载登录送额度，周末额度较多 | [AutoClaw](https://autoclaw.z.ai/) |
| Command Code | 面向开源模型的终端智能体，1 美元起 | [Command Code](https://commandcode.ai/) |
| OpenCode | 开源智能体；可选 Go 套餐 10 美元/月 | [OpenCode](https://opencode.ai/) |

## 二、工具与使用笔记

### 1. Cline：免费额度与低价套餐

Cline 的桌面端和 VS Code 插件都能使用免费额度，约 **1500 万 Token**。整理时留意到的免费模型有：

- `z-ai/glm-5.3-flash`
- `cline-free/deepseek-v4.1-flash`
- `cline-free/muse-spark-1.3-contributor`

如果免费额度不够，也可以看看 **Cline Pass**。通过优惠链接订阅约 **14 元/月**，模型可通过 API 调用。这里的优惠套餐和前面的免费额度分开看，具体操作可参考下面的帖子。

- [Cline 控制台](https://app.cline.bot/)
- [Cline Pass 优惠参考](https://linux.sb/topic/22191?p=1&floor=29)

### 2. Zed / Delta：先用试用额度感受工作流

Zed 提供 **14 天 Pro 免费试用**，包含 **5 美元的 GPT-5.6 Luna 使用额度**，无需绑卡。额度用完或满 14 天，试用即结束；这笔额度由 Zed 和同门产品 Delta **共享**，并非各领一份。具体规则见 [Zed 定价页](https://zed.dev/pricing)。

对我来说，试用的价值是先看看工具是否顺手：代码编辑、与 Agent 协作、审阅改动，这些环节能不能融入自己的习惯，比单纯追求额度更有意义。

**网络方面的个人经验：** 尽量使用稳定、干净的节点，最好是美国节点。桌面端如果提示访问被拒，可以尝试切换节点后重试。

- [Zed](https://zed.dev/)
- [Delta](https://delta.dev/)

### 3. Kiro：首次升级抵扣，留意账单周期

Kiro 的 **Pro 套餐为 20 美元/月，包含 1000 积分**。通过社交账号或 AWS Builder ID 首次升级付费套餐，可获得 **20 美元订阅抵扣**，需要有效信用卡。抵扣会结合当月剩余天数分配，不能简单理解为“开通后完整一个月免费”。具体以 [Kiro 定价与抵扣说明](https://kiro.dev/pricing/) 为准。

如果只是体验，开通时就把续费日期记下来，试完再决定是否保留订阅，免得过了账单日才想起取消。

- [Kiro 官网](https://kiro.dev/)

### 4. Antigravity：我的低成本使用笔记

Antigravity 使用谷歌 Gemini 模型。下面保留的是我收集的低成本使用路径，涉及账号、地区和验证方式，实际体验可能因人而异。

1. 在闲鱼购买约 **5 元的 Jio 套餐**，激活到自己的谷歌账号下，建议使用小号。
2. 查看账号地址；如果显示中国，可参考 [这篇地区修改帖子](https://www.nodeseek.com/post-519034-1) 调整为美国。
3. 下载 Antigravity 并登录。如果验证环节要求扫码发短信，可以尝试下面的方法。

**验证方法一：** 手机同时安装 **Google App（不是 Chrome）** 和 **YouTube**，并登录对应账号。用 Google App 扫码，可能会跳转到 YouTube 完成验证，无需发送验证码。

**验证方法二：** 如果上述方式无效，可参考 [另一篇验证经验帖](https://www.nodeseek.com/post-911507-1)。

如果还需要反向代理，可看看 [Antigravity-Manager](https://github.com/lbjlaq/Antigravity-Manager)。

- [Antigravity 官网](https://antigravity.google/)

### 5. AtomCode：留意每周的免费额度

AtomCode 是一个 Agent 项目，个人使用体验还不错。**每周都有免费 Token Plan 可领取**，适合放进常用入口里，需要时看看当期活动。

免费额度拿来处理日常小任务、体验不同模型，往往已经够用。遇到更复杂的工作，再决定是否切换到其他工具。

- [AtomCode 官网](https://atomcode.atomgit.com/)

### 6. WorkBuddy：国际版有 7 天 Pro 试用

WorkBuddy 分国内版和国际版。**国际版绑卡后可试用 7 天 Pro**，可以趁这段时间集中体验自己常用的任务。

如果没有长期订阅的打算，记得及时取消。试用期短，最好在开通当天就记下到期时间。

- [WorkBuddy 国际版邀请链接](https://workbuddy.ai/invite?code=ZVA8L3WT)

### 7. 智谱 AutoClaw：登录赠送额度，周末可以多试试

AutoClaw **下载并登录后就有赠送额度**，周末的额度比较大，使用思路与 WorkBuddy 类似。

如果手上正好有一批文档整理、资料归纳之类的任务，可以集中试一试，看看它能替自己完成多少实际工作。

- [AutoClaw 官网](https://autoclaw.z.ai/)

### 8. Command Code：1 美元起的终端智能体

Command Code 面向开源模型，主要在终端里使用。整理时的订阅门槛为 **1 美元**，适合喜欢 CLI 工作流的人尝试。

有用户反馈，订阅几天后会收到邮件，可以加少量费用升级套餐。这个信息作为参考保留，后续优惠能持续多久还不确定。

- [Command Code 官网](https://commandcode.ai/)

### 9. OpenCode：工具开源，Go 套餐按需选择

OpenCode 是开源 AI 编程智能体，支持终端、IDE 和桌面端。**使用工具本身不要求订阅 Go**，可以接入自己的模型服务。

如果想使用它提供的低价订阅，**OpenCode Go 为 10 美元/月**。这是可选的模型服务套餐，具体额度和支持模型见 [OpenCode Go 说明](https://opencode.ai/v2/docs/console/go)。

- [OpenCode 官网](https://opencode.ai/)

## 三、补充资源

### 平时关注的社区

下面这些社区时常会有工具体验、额度活动和试用 API 的分享，适合有空时翻一翻：

- [LINUX DO](https://linux.do/)
- [LINUX SB](https://linux.sb/)
- [NodeSeek](https://www.nodeseek.com/)
- [V2EX](https://www.v2ex.com/)
- [SB.SB](https://sb.sb/)

其中也会出现中转站的试用信息。稳定的中转站不多，我个人几乎不怎么使用，这部分更适合作为线索，是否采用还是要自己甄别。

### 卡网与价格聚合

卡网上偶尔能看到价格很低的成品号。**我个人没有购买过，情况不详**，这里只保留入口，作为备用资料。

- [PriceAI 渠道列表](https://priceai.cc/channels)
- [OpenPrice 卡券产品](https://www.openprice.cc/card-products/all)
- [CardNav 店铺导航](https://cardnav.xyz/shops/gpt-plus)

## 四、让额度服务于自己的工作

收集这些入口，是为了需要时有得选。真到日常使用，我更倾向于留下一个顺手的主力工具，再备一个低成本选项；临时活动刚好能用上，就用一用。

免费额度值得留意，自己的时间也一样。少花一点精力反复注册、切换和配置，把已经拿到的额度用在手头的问题上，这份清单才算派上了用场。
