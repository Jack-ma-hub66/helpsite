# Clash Verge Rev — 快速开始（macOS）

Clash Verge Rev 是跨平台的图形化代理客户端，macOS 版本原生支持 Intel 和 Apple Silicon 芯片。

---

## 第一步：下载与安装

前往 [Clash Verge Rev GitHub Releases](https://github.com/clash-verge-rev/clash-verge-rev/releases)，下载对应版本：

```
Clash.Verge_x.x.x_aarch64.dmg    ← Apple Silicon（M 系列芯片）
Clash.Verge_x.x.x_x64.dmg        ← Intel 芯片
```

安装步骤：

1. 双击 `.dmg` 文件，将 Clash Verge 拖入 **Applications（应用程序）** 文件夹
2. 首次运行时系统会提示「无法验证开发者」，前往「系统设置」→「隐私与安全性」→ 点击「仍要打开」
3. 如弹出权限请求，请允许网络访问和系统代理权限

---

## 第二步：导入订阅配置

=== "方法一：订阅链接（推荐）"

    1. 从服务提供商处复制**订阅链接**
    2. 打开 Clash Verge，点击左侧「**配置**」
    3. 点击「**订阅链接**」→「**添加订阅**」
    4. 粘贴链接后点击「**保存**」

=== "方法二：本地文件"

    1. 在订阅链接末尾加入 `&app=clashmeta`，用浏览器打开下载
    2. 将文件重命名为 `.yaml` 后缀
    3. 在 Clash Verge 中点击「**导入文件**」

---

## 第三步：启用代理

1. 点击「**设置**」→ 开启「**系统代理**」
2. 在节点列表中选择代理模式（推荐「**规则模式**」）
3. 选择延迟较低的节点

---

## 第四步：测试连接

打开浏览器访问测试网站，确认连接正常。节点延迟应低于 200ms。

!!! tip "macOS 独有问题"
    如遇到「增强模式」需要输入密码，这是正常的系统权限请求，输入 Mac 登录密码即可。
