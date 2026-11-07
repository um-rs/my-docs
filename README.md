# my-docs｜个人静态文档自动部署实践

基于 **MkDocs Material** 搭建的四页个人技术文档站，通过 **GitHub Actions** 实现推送 `main` 分支后自动构建并部署到 **GitHub Pages**。

## 相关链接

- **在线文档网站**：[https://um-rs.github.io/my-docs/](https://um-rs.github.io/my-docs/)
- **个人实验报告**：[个人实验报告](report/README.md)
- **个人主站博客**：[https://vita.do](https://vita.do)

## 目录说明

- `docs/`：存放网站 4 个页面的 Markdown 源码（`index.md`、`about.md`、`guide.md`、`api.md`）
- `mkdocs.yml`：站点基础信息、Material 主题及导航栏配置
- `.github/workflows/deploy.yml`：GitHub Pages 自动构建与部署工作流
- `report/`：实践过程记录、思考题解答与关键步骤截图

## 本地构建与预览

在项目根目录下创建虚拟环境并安装依赖后，即可在本地启动预览：

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt

# 严格模式构建检查
python -m mkdocs build --strict

# 启动本地预览（默认地址 http://127.0.0.1:8000/）
python -m mkdocs serve
```
