# PriCube 单页作品集网站

一个受 [CREOVO](https://creovo.framer.website/) 风格启发的深色创意工作室落地页。项目结构简单：

```
PriCube/
├── index.html      # 页面结构
├── style.css       # 全部样式
├── script.js       # 交互动效
├── images/         # 图标等静态资源
└── README.md       # 本文件
```

## 本地预览

直接用浏览器打开 `index.html` 即可查看。

如果你想在本地起一个轻量服务器（推荐，用于确保资源路径正确）：

```bash
# 方案一：Node.js
npx serve .

# 方案二：Python 3
python -m http.server 8080
```

然后打开 http://localhost:8080 。

## 自定义内容

- **品牌名**：搜索替换 `index.html` 中的 `PriCube` 即可。
- **文案**：所有中文文案都在 `index.html` 中，直接编辑对应段落。
- **项目图**：当前使用纯 CSS 渐变/几何占位图（不依赖外部网络）。要替换为真实图片，找到 `.thumb-shapes` 相关样式，改成 `img` 标签或背景图片即可。
- **配色**：在 `style.css` 顶部 `:root` 里修改变量，如背景 `--bg`、强调色 `--accent`。

## 部署到 Cloudflare Pages

Cloudflare Pages 支持纯静态站点，本项目无需构建工具。

### 方案 A：Git 仓库 + 面板连接（推荐）

1. 在 GitHub 创建一个新仓库，例如 `pricube-site`。
2. 将本目录推送到仓库：

   ```bash
   git init
   git add .
   git commit -m "Initial PriCube site"
   git branch -M main
   git remote add origin https://github.com/你的用户名/pricube-site.git
   git push -u origin main
   ```

3. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/) → 进入 **Pages**。
4. 点击 **Create a project** → **Connect to Git**。
5. 选择 `pricube-site` 仓库，点击 **Begin setup**。
6. 构建设置：
   - **Build command**（构建命令）：留空
   - **Build output directory**（输出目录）：`/`（即根目录）
7. 点击 **Save and Deploy**，等待部署完成即可获得在线 URL。

### 方案 B：直接拖拽上传

1. 将 `PriCube` 文件夹压缩为 ZIP，或保持文件夹展开。
2. 登录 Cloudflare Dashboard → Pages → **Create a project** → **Upload assets**。
3. 上传本文件夹内容，部署完成后即可访问。

> 提示：如果你的 `index.html` 放在子文件夹里，Pages 默认入口仍是根目录的 `index.html`。本项目已将 `index.html` 放在根目录，直接上传即可。

## 后续扩展建议

- 添加项目详情页、独立联系页、404 页。
- 将项目/服务数据抽取为 JSON 或 Markdown，便于维护。
- 接入 Cloudflare Pages Functions 处理联系表单后端。
- 替换 CSS 占位图为真实作品集图片。
