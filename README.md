# 我的私人小说库

用 [mdBook](https://github.com/rust-lang/mdBook) 搭建的静态小说 / 文档阅读站，部署在 GitHub Pages。

- 左侧章节目录，右侧正文
- 原生支持手机 / 电脑端适配
- 右上角一键切换**夜间模式**
- 全文搜索

## 本地预览

```bash
# 安装 mdBook：用 Rust 工具链
cargo install mdbook
# 或前往 https://github.com/rust-lang/mdBook/releases 下载对应系统的二进制

mdbook serve     # 默认 http://localhost:3000，带热重载
# 或仅构建
mdbook build     # 产物在 book/ 目录
```

## 目录结构

```
Myblack-books/
├── book.toml              # 站点配置（标题、语言、主题、site-url 等）
├── src/
│   ├── SUMMARY.md         # 左侧目录索引（小说章节在此增删）
│   ├── README.md          # 封面 / 站点首页
│   ├── 序章.md
│   └── chapter1.md ...    # 你的小说章节
├── theme/css/custom.css   # 中文阅读排版优化（自动加载）
└── .github/workflows/     # 推送到 main 分支即自动部署到 GitHub Pages
```

## 部署到 GitHub Pages

- 仓库：`mofablack5-wq/Myblack-books`
- 推送 `main` 分支后，GitHub Actions 自动构建并发布。
- 首次需在仓库 **Settings → Pages → Build and deployment → Source 选 "GitHub Actions"**。
- 站点地址：`https://mofablack5-wq.github.io/Myblack-books/`

> `book.toml` 里的 `site-url` 已设为 `/Myblack-books/`，必须与仓库名保持一致；若改仓库名需同步修改此处。

## 如何更新小说

1. 编辑 / 新增 `src/` 下的 `.md` 章节。
2. 在 `src/SUMMARY.md` 里增删目录项（格式：`- [标题](文件名.md)`）。
3. `git push` 到 `main`，GitHub Actions 自动重新部署。
