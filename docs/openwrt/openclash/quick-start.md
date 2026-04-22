# OpenClash — 快速开始

OpenClash 是 OpenWrt 平台上功能最完整的代理插件，提供可视化 Web 管理界面。

---

## 前提条件

- 路由器已安装 OpenWrt 系统
- 可访问路由器管理后台（通常为 `192.168.1.1`）

---

## 第一步：安装 OpenClash

1. 下载适合您路由器架构的 OpenClash 安装包：
   [OpenClash GitHub Releases](https://github.com/vernesong/OpenClash/releases)

2. 登录 OpenWrt 后台 → 「**系统**」→「**软件包**」

3. 点击「**上传软件包**」，选择下载的 `.ipk` 文件并安装

4. 安装完成后，在「**服务**」菜单下找到「**OpenClash**」

---

## 第二步：导入订阅配置

1. 进入 OpenClash 管理页面
2. 点击「**配置文件订阅**」→「**添加**」
3. 填写：
    - **配置文件名**：自定义（如 `myconfig`）
    - **订阅地址**：粘贴您的订阅链接
4. 点击「**保存配置**」
5. 点击「**一键生成配置**」或手动更新订阅

---

## 第三步：启动服务

1. 回到 OpenClash 主页
2. 点击「**启动 OpenClash**」
3. 等待核心文件下载完成（首次启动需要下载核心，可能需要几分钟）
4. 状态显示「**运行中**」即代理启用成功

!!! warning "核心文件下载失败"
    首次安装时核心文件需从 GitHub 下载，若下载失败可手动上传核心文件。详见 [OpenClash Wiki](https://github.com/vernesong/OpenClash/wiki)。
