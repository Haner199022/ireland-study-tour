# Deployment

## 主线 · GitHub Pages（全球公开访问，中国大陆可达）

- **Live URL**: <https://haner199022.github.io/ireland-study-tour/>
- **GitHub repo**: <https://github.com/Haner199022/ireland-study-tour>
- **Account**: `Haner199022`
- **Branch**: `main` · serving from root (`/`)
- **Build**: 静态文件直供，无 Jekyll（含 `.nojekyll` 文件）

### 重新部署 / Redeploy

任何时候改了 `website/` 里的文件，推送即重发：

```bash
cd "/Users/erica/Library/Mobile Documents/iCloud~md~obsidian/Documents/Claude Code/Projects/CUC-ai-lab/Ireland-Study-Tour/website"
git add .
git commit -m "update: <你改了什么>"
git push
```

GitHub Pages 会在 **30–90 秒内**自动重建。无需手动触发。

### 首次推送（认证设置）

`gh` CLI 装在 `~/.local/bin/gh`，PATH 已写入 `~/.zshrc`。但要 push，git 需要拿到 token。两种方法：

**方法 A · 一次性环境变量（最简单）：**

```bash
export GH_TOKEN="ghp_你的token"
cd ".../website"
git push
```

**方法 B · 用 gh 重新登录（持久）：**

```bash
gh auth login -w   # 浏览器走 device-code 流程，需要 read:org scope
```

> 当前 token `ghp_xHn4...058JZd` 只有 `repo + workflow` scope，没有 `read:org`，
> 所以方法 B 不能用现有 token 走 `gh auth login`。
> 想用方法 B 需要在 <https://github.com/settings/tokens/new> 重新生成一个带 `repo, workflow, read:org` 的 token。

### 启用 GitHub Pages 设置

已经配好，不用重复操作。详情可在仓库 Settings → Pages 查看：
<https://github.com/Haner199022/ireland-study-tour/settings/pages>

### 绑定自定义域名（可选 · 未来用）

如果之后拿到 CUC 子域名（如 `ireland.cuc.edu.cn`）想换上去：

1. 在 CUC DNS 后台加一条 CNAME 记录指向 `haner199022.github.io`
2. 在仓库 Settings → Pages → Custom domain 填上你的域名
3. 勾选 **Enforce HTTPS**
4. 完事

GitHub Pages 自动处理 SSL 证书。

---

## 备份 · Vercel（已部署，需 VPN）

- **URL**: <https://cuc-ireland-tour.vercel.app>
- **Vercel project**: `ta-fs-projects/cuc-ireland-tour`

重新部署：

```bash
cd ".../website"
vercel deploy --prod
```

> 在中国大陆访问 vercel.app 域名需要 VPN。日常分享走 GitHub Pages 即可。

---

## 已废弃 · EdgeOne Pages

之前尝试过腾讯云 EdgeOne Pages（项目 ID `pages-8fcvqbbpsaef`），
但发现免费版必须自己绑域名才能公开访问，不适合本项目。
如不再使用可在腾讯云控制台手动删除项目。

---

## 部署内容 / What's deployed

```
website/
├── index.html              主页（含照片、动画、TOC）
├── opening-lecture.html    金院长 D2 开场幻灯片
├── opening-lecture.pdf     PDF 备用版
├── README.md               GitHub 仓库 README
├── .nojekyll               告诉 GitHub Pages 别用 Jekyll
├── .gitignore              忽略 .vercel / .edgeone / .DS_Store
└── vercel.json             Vercel 配置（GH Pages 用不到，无害）
```
