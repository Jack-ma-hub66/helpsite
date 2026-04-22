# 隐私与泄漏防护

开着代理不等于完全匿名。有几种常见的"泄漏"问题，可能在你不知情的情况下暴露你的真实 IP。

---

## DNS 泄漏

### 什么是 DNS 泄漏？

开着代理，但 DNS 查询却绕过了代理，直接发给了你本地运营商的 DNS 服务器。

结果：你访问的网站知道了你的真实 IP（通过 DNS 查询的来源 IP）。

**示意图：**

```
正常情况（无泄漏）：
你的设备 → 代理服务器 → DNS 查询 → google.com 的 IP
                 （DNS 查询从代理服务器发出，对方看到代理 IP）

DNS 泄漏时：
你的设备 → DNS 查询直接发给运营商 DNS ← 暴露真实 IP！
你的设备 → 代理服务器 → 访问网站（但 DNS 已经泄漏了）
```

### 如何检测 DNS 泄漏？

连上节点后，访问 [dnsleaktest.com](https://www.dnsleaktest.com) 或 [browserleaks.com/dns](https://browserleaks.com/dns)。

- 如果显示的 DNS 服务器位于**代理节点所在国家**：无泄漏 ✅
- 如果显示的是**你的运营商 DNS**（如中国电信、联通）：存在 DNS 泄漏 ❌

### 如何修复 DNS 泄漏？

在代理客户端设置中：

- **Clash Verge**：设置 → DNS → 开启"代理 DNS"或将 DNS 模式改为 `fake-ip`
- **v2rayN**：设置 → 路由设置 → DNS → 配置国外 DNS 走代理
- 通用方案：使用加密 DNS（DoH），并确保 DNS 请求走代理通道

---

## WebRTC 泄漏

### 什么是 WebRTC 泄漏？

WebRTC 是浏览器的一个功能，用于视频通话、实时通信（如 Google Meet、Discord 网页版）。

WebRTC 会绕过代理，直接获取并暴露你的**真实本地 IP 和公网 IP**——即使你开着代理。

### 如何检测 WebRTC 泄漏？

访问 [browserleaks.com/webrtc](https://browserleaks.com/webrtc)，查看显示的 IP 是否与你的代理 IP 一致。

如果页面显示了你的真实 IP（与代理 IP 不同），则存在 WebRTC 泄漏。

### 如何修复 WebRTC 泄漏？

**方法一：浏览器扩展（推荐）**

安装 `WebRTC Leak Prevent` 或 `uBlock Origin`（在设置中开启 WebRTC 保护）。

**方法二：浏览器设置（Firefox）**

1. 地址栏输入 `about:config`
2. 搜索 `media.peerconnection.enabled`
3. 将其设为 `false`

**方法三：使用 TUN 模式**

在 Clash Verge 中开启 TUN 模式（虚拟网卡），所有流量包括 WebRTC 都会经过代理。

---

## TLS 指纹

### 什么是 TLS 指纹？

当你的浏览器或代理客户端发起 HTTPS 连接时，TLS 握手包含大量信息（支持的加密算法、扩展列表等），这些信息的组合形成独特的"指纹"。

GFW 和部分网站可以通过 TLS 指纹判断：
- 你使用的是哪个代理客户端（如 Clash、v2rayN）
- 这是否是代理流量而非普通浏览器流量

### 如何应对 TLS 指纹检测？

现代代理客户端（如 Clash Verge 使用的 Mihomo 核心、Xray）已内置 TLS 指纹伪装功能，会将自己的指纹伪装成 Chrome 或 Firefox 浏览器。

在 Clash Verge 中，这通常是默认开启的，无需手动配置。

---

## IP 地址泄漏综合检测

连上代理后，访问以下网站做全面检查：

| 工具 | 地址 | 检测内容 |
|------|------|---------|
| BrowserLeaks | [browserleaks.com](https://browserleaks.com) | WebRTC、Canvas 指纹、DNS、IP 等综合检测 |
| DNS Leak Test | [dnsleaktest.com](https://www.dnsleaktest.com) | DNS 泄漏专项检测 |
| IPLeak | [ipleak.net](https://ipleak.net) | IP 和 DNS 综合检测 |
| Whoer | [whoer.net](https://whoer.net) | 匿名度综合评分 |

---

## 隐私保护最佳实践

**基础级：**
- ✅ 开启代理客户端的 DNS 保护
- ✅ 安装 WebRTC 保护扩展
- ✅ 定期检测 dnsleaktest.com

**进阶级：**
- ✅ 使用 TUN 模式（全局代理，更彻底）
- ✅ 使用 Clash Verge 的 Fake-IP DNS 模式
- ✅ 避免在代理和非代理状态下使用同一浏览器 Profile

**高级需求：**
- ✅ 使用独立的浏览器 Profile 区分代理和非代理环境
- ✅ 配合 Tor 使用（极端匿名需求）

---

!!! info "关于完全匿名"
    没有任何技术手段可以做到 100% 匿名。代理工具的主要目的是**绕过地理限制**，不是实现完全匿名。如有极高的隐私需求，需要更专业的解决方案。
