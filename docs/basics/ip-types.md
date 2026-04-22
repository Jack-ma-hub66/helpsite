# 机房 IP vs 住宅 IP

为什么有些节点看 Netflix 显示"不可用"，有些却可以？IP 类型是关键原因之一。

---

## 两种 IP 类型

### 机房 IP（Datacenter IP）

这类 IP 来自云服务器提供商，如 AWS、GCP、Azure、Vultr、Hetzner 等。

**特点：**
- 速度快、带宽大、价格便宜
- IP 归属显示为"数据中心"或具体云服务商名称
- **几乎所有主要流媒体都能识别并屏蔽**
- Google 频繁弹出验证码
- 注册账号时常被拒绝

**适合：**普通翻墙浏览、访问不限制 IP 类型的服务

---

### 住宅 IP（Residential IP）

这类 IP 来自真实的家庭宽带用户，由 ISP（互联网服务提供商）分配给普通家庭。

**特点：**
- 在各大数据库中被识别为"真实用户"
- 流媒体解锁能力强（Netflix、Disney+、Hulu 等）
- 几乎不触发验证码
- 价格较贵，带宽相对较小
- IP 归属显示为 ISP 名称（如 Comcast、AT&T、BT 等）

**适合：**流媒体解锁、需要绕过 IP 限制的服务、注册境外账号

---

### 原生 IP vs 广播 IP

除了机房/住宅的区别，还有"原生 IP"的概念：

| 类型 | 说明 |
|------|------|
| 原生 IP | IP 归属地与服务器实际所在地一致，如服务器在美国，IP 也显示美国 |
| 广播 IP | IP 归属地与服务器实际所在地不一致，如服务器在香港但 IP 显示美国 |

Netflix、Disney+ 等流媒体对**原生 IP**的识别更严格——广播美国 IP 但实际在香港的服务器，可能无法解锁美区内容。

---

## 如何识别节点的 IP 类型

连上节点后，访问以下网站查看 IP 信息：

### 方法一：ipinfo.io

访问 [ipinfo.io](https://ipinfo.io)，查看 `org` 字段：

```
"org": "AS14061 DigitalOcean, LLC"   → 机房 IP（DigitalOcean 是云服务商）
"org": "AS7922 Comcast Cable"        → 住宅 IP（Comcast 是美国家庭宽带运营商）
"org": "AS2914 NTT"                  → 可能是机房也可能是企业网络
```

### 方法二：ip.sb 或 ipapi.is

访问 [ip.sb](https://ip.sb) 或 [ipapi.is](https://ipapi.is)，查看：
- `type` 字段：`hosting`（机房）或 `isp`（住宅/ISP）
- `is_datacenter`：`true` 表示机房 IP

### 方法三：Scamalytics

访问 [scamalytics.com/ip/你的IP](https://scamalytics.com)，查看：
- `ISP fraud score`：住宅 IP 通常评分低
- `Datacenter`：`Yes/No`

---

## 机房 IP 和住宅 IP 的流媒体解锁对比

| 服务 | 机房 IP | 住宅 IP |
|------|---------|---------|
| Netflix 自制剧 | ✅ 通常可以 | ✅ 可以 |
| Netflix 授权内容（地区限定） | ❌ 大概率被拒 | ✅ 通常可以 |
| Disney+ | ❌ 大概率被拒 | ✅ 通常可以 |
| Hulu | ❌ 基本不行 | ✅ 通常可以 |
| YouTube Premium | ✅ 可以 | ✅ 可以 |
| ChatGPT/OpenAI | ⚠️ 部分可以 | ✅ 通常可以 |
| Spotify | ✅ 通常可以 | ✅ 可以 |

!!! note "结论"
    如果你的主要需求是看 Netflix、Disney+ 等流媒体，要专门找**住宅 IP 节点**或**原生 IP 节点**。普通翻墙浏览用机房 IP 就够了。

---

## 为什么住宅 IP 贵那么多？

住宅 IP 的获取方式有限：
1. 真实用户安装特定软件，将自己的家庭网络带宽出租（P2P 住宅代理）
2. 合法购买 ISP 分配的 IP 段（成本极高）

无论哪种方式，成本都远高于租用云服务器，所以住宅 IP 节点通常价格是机房 IP 的 5-10 倍甚至更多。
