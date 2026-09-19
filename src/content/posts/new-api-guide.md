---
title: New API 使用手册（本机部署）
published: 2026-09-01
updated: 2026-09-01
description: 在 macOS 本机部署 New API，并配置 OpenAI 兼容客户端与免费渠道。
image: ./images/new-api-guide.avif
tags: [AI部署, New API, 自托管, API, 教程]
category: 技术实践
slug: new-api-guide
---

> 最后更新：2026-09-01 · 部署位置：`~/new-api` · 端口：3000

---

## 一、快速命令（最常用）

```bash
# 启动（后台运行，日志写入 new-api.log）
cd ~/new-api && (PORT=3000 TZ=Asia/Shanghai nohup ./new-api > new-api.log 2>&1 &)

# 查看是否在运行
pgrep -fl new-api

# 停止
pkill -f "./new-api"

# 看日志（实时滚动）
tail -f ~/new-api/new-api.log

# 确认端口被谁占用（3000 被占时先处理）
lsof -nP -i :3000
```

启动后浏览器访问 **http://localhost:3000**（局域网设备：http://192.168.31.83:3000，IP 变了就重新查 `ifconfig`）。

## 二、目录结构

| 文件 | 说明 | 能删吗 |
|---|---|---|
| `~/new-api/new-api` | 程序本体（macOS arm64 二进制，142M） | ❌ |
| `~/new-api/one-api.db` | **数据库（全部配置、渠道、令牌都在这里，SQLite）** | ❌ |
| `~/new-api/new-api.log` | 运行日志 | 可清空 |
| `~/new-api/logs/` | 日志目录 | 可清空 |

⚠️ **备份 = 备份 `one-api.db`**。要迁移/重装前先把整个 `~/new-api` 目录拷一份，渠道和令牌配置都在数据库里，丢了要重配。

## 三、客户端接入

- **Base URL**：`http://localhost:3000/v1`
- **API Key**：后台「令牌管理」里生成的令牌
- **模型名**：填渠道里的模型名（或渠道「模型映射」里映射后的短名）

例（Claude Code / Cline / Cherry Studio 等任意 OpenAI 兼容客户端）：

```yaml
base_url: http://localhost:3000/v1
api_key: sk-xxxx（你的令牌）
model: ds4 / minimax-m3 / hy3 ...
```

## 四、当前免费渠道池：示例

| 渠道 | Base URL | 状态 |
|---|---|---|
| Kilo | `https://api.kilo.ai/api/gateway` | 免费模型按 IP 限流 200 次/小时 |
| B.AI | `https://api.b.ai` | 8/27 起的免费 flash 活动，限时 |
| Groq | `https://api.groq.com/openai/v1` | 永久免费档 |
| Cerebras | `https://api.cerebras.ai` | 永久免费档 |
| Mistral | `https://api.mistral.ai/v1` | Experiment 免费档 |

**客户端锁定、不进池子的**（各走各的客户端）：

- AtomGit CodingPlan → 在 AtomCode 里用（推理接口有 AtomCode 签名校验，第三方网关进不去）
- Cline 免费档 → 在 Cline 插件/CLI 里用（官方明确 API 不提供免费模型）

## 五、常见操作

### 渠道不工作

1. 渠道列表点「测试」，看报错：
   - `401` → Key 错了或过期，重新生成
   - `404` → Base URL 问题，试加/去掉 `/v1`
   - `model is not enabled` → 该模型不在套餐/免费列表里
   - 返回 HTML → 被风控，换网络
2. 免费活动（B.AI/Kilo）会随时间失效，失效后直接**禁用渠道**即可，不影响其他渠道

### 换模型 / 切换供应商

- 客户端改 `model` 名即可
- 或后台把某渠道停用/启用
- failover 依赖：渠道「优先级」（高者先用）+「权重」（同优先级随机）+「自动禁用」（连续失败自动下线）

### 用量/日志在哪看

- 后台「日志」页：每次请求的渠道、模型、token、耗时
- 日志里「流」= stream 流式（边生成边返回，Claude Code 都是这种）；「非流」= 等全部生成完一次返回
- 「数据看板」页：token/请求量统计

## 六、升级 / 重装

```bash
# 停掉
pkill -f "./new-api"

# 下载最新版（arm64）
cd ~/new-api && curl -sL -o new-api "https://github.com/QuantumNous/new-api/releases/latest/download/new-api-macos-v1.0.0-rc.30" \
  && chmod +x new-api

# 重新启动（数据库 one-api.db 不动，配置全保留）
(PORT=3000 TZ=Asia/Shanghai nohup ./new-api > new-api.log 2>&1 &)
```

> 注意：升级前最好 `cp one-api.db one-api.db.bak-日期` 留个备份。

## 七、安全提醒

- 本机自用没问题，**不要**把 3000 端口暴露到公网
- 令牌等同访问凭证，别提交进 git / 发到群里
- 免费档普遍有「数据可能用于改进模型」条款（Kilo auto 路由、Cline、Mistral 等），**敏感代码**优先走明确不训练数据的渠道（Groq / Cerebras）
- 各免费源的 ToS 风险自己评估，B.AI/Kilo 这类“活动型”免费源随时可能失效
