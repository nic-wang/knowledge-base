# 🛠️ 知识库日常维护指南

> 给牛牛自己看的 SOP · 给糯米鸡下次接手时看的 context

---

## 📍 关键坐标

| 项目 | 地址 |
|---|---|
| 仓库 | https://github.com/nic-wang/knowledge-base |
| Pages 首页 | https://nic-wang.github.io/knowledge-base/ |
| 本地路径 | `/Users/nic/WorkBuddy/20260429233105` |
| 默认分支 | `main` |
| Git 身份 | `Nic Wang <157982458+nic-wang@users.noreply.github.com>` |

## 📂 目录约定

```
knowledge-base/
├── README.md              ← GitHub 仓库首页（Markdown 导航）
├── index.html             ← Pages 首页（GitHub 风格卡片导航）
├── _config.yml            ← Jekyll 配置
├── .gitignore             ← 忽略 .workbuddy/ 等敏感目录
├── docs/
│   ├── ai-agents/         ← AI Agent 主题
│   ├── sales-tips/        ← 腾讯广告/法律行业销售
│   ├── tech/              ← 技术探索
│   └── life/              ← 个人/家庭/嘻嘻相关
└── assets/                ← 共享资源（CSS/图片/字体）
```

---

## 🚀 新增一篇文档的标准流程

### 1. 本地写好 HTML
放进对应主题目录：
```bash
# 举例：写好了新的 AI Agent 笔记
mv ~/Desktop/new-article.html /Users/nic/WorkBuddy/20260429233105/docs/ai-agents/
```

### 2. 更新导航（两处）

**a) `README.md`** —— 在对应分区下新增一条：
```markdown
- [新文章标题](./docs/ai-agents/new-article.html) · YYYY-MM-DD
  一句话简介
```

**b) `index.html`** —— 找到对应 `<div class="card">`，在 `<ul>` 里插入：
```html
<li>
  <a href="./docs/ai-agents/new-article.html">新文章标题</a>
  <span class="date">· YYYY-MM-DD</span>
</li>
```
同时把 `card-count` 的数字加 1。

**c) 更新记录**
在 `README.md` 和 `index.html` 的"更新记录"表格最上方新增一行。

### 3. 提交并推送

```bash
cd /Users/nic/WorkBuddy/20260429233105
git add .
git commit -m "add: 新文章标题"
git push
```

> 首次 push 会提示输入 GitHub 账号 + PAT。输入后 osxkeychain 会记住，以后直接 push。

### 4. 等 1-2 分钟
Pages 自动重新部署，刷新 https://nic-wang.github.io/knowledge-base/ 就看到了。

---

## 🔐 认证方式（已配置）

- **credential.helper** = `osxkeychain`（macOS 钥匙串）
- **首次 push** 会弹窗要账号密码：
  - username: `nic-wang`
  - password: **你的 PAT**（不是 GitHub 登录密码）
- 之后 osxkeychain 会自动记住，无需再输

## 🚨 PAT 管理

- **当前用的是经典 PAT**（30 天过期）
- **到期后**：去 https://github.com/settings/tokens 生成新 PAT，首次 push 时替换即可
- **本次使用后建议立即吊销**：https://github.com/settings/tokens → 找到 token → Revoke

---

## ⚠️ 内容合规红线

| 绝对禁止 push | 原因 |
|---|---|
| 腾讯内部代码 / 项目文件 | 公司红线 |
| 内部 TAPD 需求 / 内部文档 | 信安合规 |
| 客户真实名字 / 合同金额 | 客户隐私 |
| `.workbuddy/` 目录内容 | 我的本地记忆，含你个人信息 |
| PAT / API Key / 密码 | 任何时候都不能 push |

> `.gitignore` 已帮你挡掉 `.workbuddy/`，但**每次 commit 前先 `git status` 看一眼**是好习惯。

---

## 🎨 文档风格统一约定

所有新加的 HTML 都遵循 **GitHub 风格**：

- 白底：`background: #ffffff`
- 边框：`border: 1px solid #d1d9e0`
- 主色：`#0969da`（蓝链接）、`#1a7f37`（绿/成功）、`#cf222e`（红/警告）
- 字体：`-apple-system, PingFang SC, Microsoft YaHei`
- **不要**渐变、阴影、圆角卡片
- label 标签：圆角 10px，浅底深字

可以直接复用 `docs/ai-agents/tencent-agents-comparison.html` 的 `<style>` 块作为起点。

---

## 🐛 常见问题

### Pages 迟迟没更新？
- 正常需要 30 秒到 2 分钟
- 去 Settings → Pages 看 "Your site is live at..." 的状态
- 或者 https://github.com/nic-wang/knowledge-base/deployments 看部署历史

### push 被拒 (rejected)？
```bash
git pull --rebase origin main
git push
```

### 想删除一篇文档？
```bash
git rm docs/ai-agents/old-article.html
git commit -m "remove: 旧文章"
git push
```
同时更新 README.md 和 index.html 的导航。

---

## 🦜 糯米鸡提示

> 这个知识库的长期价值在于**持续沉淀**，不在于一次性完美。
> 先把东西放进来，链接稳定可访问，以后每次修改都是增量改进。
> 结论前置，证据后置 —— 是这个知识库的灵魂。

_Last updated: 2026-04-30_
