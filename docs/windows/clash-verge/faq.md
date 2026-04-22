# Clash Verge Rev — 常见问题

---

## 安装与启动问题

??? question "安装后无法启动，或提示文件损坏"
    **可能原因：** 旧版残留配置文件冲突，或安装路径含中文。

    **解决方案：**

    1. 卸载旧版本，手动删除残留配置目录：`C:\Users\<用户名>\.config\clash-verge`
    2. 从 [GitHub](https://github.com/clash-verge-rev/clash-verge-rev/releases) 重新下载最新版本
    3. 安装到**不含中文字符**的路径，例如 `C:\Program Files\ClashVerge`
    4. 右键以「管理员身份运行」

??? question "启动后界面空白或显示不全"
    **可能原因：** 缺少 WebView2 运行时。

    **解决方案：**

    1. 安装 [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)
    2. 确保 Windows 系统已更新到最新版本
    3. 尝试删除 `config.yml` 文件后重启（删除前请备份）

---

## 代理冲突问题

??? question "系统代理无法启用，与其他软件冲突"
    **场景：** 同时安装了旧版 Clash for Windows，导致系统代理被占用。

    **解决方案：**

    1. 打开 Clash for Windows → 设置 → 关闭 **System Proxy**
    2. 手动清理代理残留：按 `Win + R` 输入 `inetcpl.cpl` → 连接 → 局域网设置 → 取消勾选「为 LAN 使用代理服务器」
    3. 以管理员身份重新启动 Clash Verge

??? question "软件关闭后，整台电脑无法上网"
    **原因：** Clash Verge 未正常退出，系统代理设置残留。

    **解决方案：**

    1. 按 `Win + R` → 输入 `inetcpl.cpl`
    2. 连接 → 局域网设置 → 取消勾选「为 LAN 使用代理服务器」
    3. 重启 Clash Verge，重新开启系统代理

---

## 订阅与节点问题

??? question "导入订阅时报错 error sending request 或连接被强制关闭"
    **可能原因：** 订阅链接被当地网络屏蔽。

    **解决方案：**

    - 切换 Wi-Fi 或手机热点后重试
    - 联系服务提供商获取新的订阅链接
    - 使用在线订阅转换工具（如 subconverter）转换后导入

??? question "无法访问境外网站，但国内网络正常"
    **解决方案：**

    1. 在 Clash Verge 中点击「刷新订阅」获取最新节点
    2. 在节点列表中切换到延迟较低的其他节点
    3. 如所有节点均不可用，联系服务提供商排查线路问题

---

## 其他问题

??? question "如何切换软件语言？"
    打开「设置」→「Verge Setting」→「Language」，选择「中文」后保存。

??? question "如何查看连接日志？"
    点击左侧菜单「**日志**」，可查看详细连接记录。如需更详细信息，在设置中将日志级别调整为 `TRACE`。
