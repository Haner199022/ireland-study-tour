# Deployment · Vercel

## 当前部署 / Current Deployment
- **Production URL**: <https://cuc-ireland-tour.vercel.app>
- **Vercel project**: `ta-fs-projects/cuc-ireland-tour`
- **Account**: `haner199022`
- **Inspect dashboard**: <https://vercel.com/ta-fs-projects/cuc-ireland-tour>

## 重新部署 / Redeploy

任何时候改了 `website/` 里的文件，重新部署一行命令：

```bash
cd "/Users/erica/Library/Mobile Documents/iCloud~md~obsidian/Documents/Claude Code/Projects/CUC-ai-lab/Ireland-Study-Tour/website"
vercel deploy --prod
```

> Node + Vercel CLI 已装在 `~/.node/`，PATH 已写入 `~/.zshrc` —— 新开终端直接可用。

## 添加自定义域名 / Custom Domain（可选）

如果之后想用 `study.cuc.edu.cn` 之类的自有域名：

```bash
vercel domains add study.cuc.edu.cn cuc-ireland-tour
```

然后按 Vercel 提示在域名 DNS 后台加 CNAME 记录指向 `cname.vercel-dns.com`。

## 删除部署 / Remove

```bash
vercel project rm cuc-ireland-tour
```

## 部署内容 / What's deployed

```
website/
├── index.html              主页（含照片、动画、TOC）
├── opening-lecture.html    金院长 D2 开场幻灯片
├── opening-lecture.pdf     PDF 备用版
└── vercel.json             部署配置（cleanUrls + 安全头 + 缓存策略）
```

`.vercel/` 目录是 Vercel 生成的项目链接元数据，**不要 删除**。
