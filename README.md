# 帮助中心 — 部署说明

基于 MkDocs + Material 主题构建的静态帮助文档网站。

---

## 本地预览

```bash
# 安装依赖
pip install -r requirements.txt

# 启动本地预览（热重载）
mkdocs serve

# 浏览器访问
# http://127.0.0.1:8000
```

---

## 构建静态文件

```bash
mkdocs build
```

生成的静态文件在 `site/` 目录，可直接部署到任何静态托管服务。

---

## 部署方式

### 方式一：GitHub Pages（推荐，免费）

1. 将项目推送到 GitHub 仓库
2. 在仓库根目录创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy MkDocs
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      - run: pip install -r requirements.txt
      - run: mkdocs gh-deploy --force
```

3. 推送后自动部署到 `https://<用户名>.github.io/<仓库名>/`

### 方式二：Cloudflare Pages（推荐，国内访问更快）

1. 登录 Cloudflare Pages，连接 GitHub 仓库
2. 构建设置：
    - **构建命令**：`pip install mkdocs-material && mkdocs build`
    - **输出目录**：`site`
3. 保存后自动部署

### 方式三：Vercel

1. 在 Vercel 导入 GitHub 仓库
2. 框架选择「Other」
3. 构建命令：`pip install mkdocs-material && mkdocs build`
4. 输出目录：`site`

---

## 文件结构

```
helpsite/
├── mkdocs.yml          # 网站配置（导航、主题、插件）
├── requirements.txt    # Python 依赖
├── docs/
│   ├── index.md        # 首页
│   ├── windows/        # Windows 平台教程
│   │   ├── index.md
│   │   ├── clash-verge/
│   │   └── v2rayn/
│   ├── macos/          # macOS 平台教程
│   ├── android/        # Android 平台教程
│   ├── ios/            # iOS/iPadOS 平台教程
│   ├── openwrt/        # OpenWrt 平台教程
│   ├── glossary/       # 词汇表
│   └── faq/            # 全局常见问题
└── site/               # 构建输出（自动生成，不要手动编辑）
```

---

## 添加新内容

每个页面都是一个 `.md` 文件。新增教程步骤：

1. 在对应平台目录创建新 `.md` 文件
2. 在 `mkdocs.yml` 的 `nav:` 部分添加对应条目
3. 运行 `mkdocs serve` 预览效果

---

## 常用 Markdown 组件

```markdown
# 提示框
!!! tip "标题"
    内容

!!! warning "警告"
    内容

!!! note "注意"
    内容

# 折叠式 FAQ
??? question "问题"
    答案

# 多标签页
=== "标签一"
    内容一

=== "标签二"
    内容二

# 表格
| 列一 | 列二 |
|------|------|
| 内容 | 内容 |
```
