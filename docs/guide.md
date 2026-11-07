# 使用指南

这页简单记一下平时在本地改文档、预览效果，再到推上 GitHub 自动发布的常规步骤吧。命令基本都是我在 macOS 终端下实际跑过的。

## 日常更新流程

1. 在本地修改 `docs/` 目录下的 Markdown 文件（如果新增了页面，记得顺手去 `mkdocs.yml` 的 `nav` 里登记一下）。
2. 启动本地预览服务，在浏览器里点一遍改过的页面、表格和跳转链接。
3. 跑一次严格模式构建，确认没有死链或者配置警告。
4. 用 Git 提交改动并推送到远端 `main` 分支。
5. 去仓库的 Actions 页面瞄一眼 `build` 和 `deploy` 变绿没有，最后打开线上地址确认内容已经刷新。

## 本地环境与常用命令

第一次拉下仓库后，建议先在项目根目录建个独立的虚拟环境把依赖装好，免得跟系统里别的 Python 包打架：

```bash
# 创建并激活虚拟环境（macOS / Linux）
python3 -m venv .venv
source .venv/bin/activate

# 安装 MkDocs 与 Material 主题
python -m pip install -r requirements.txt
```

平时写文档最常用的其实就是下面这两条命令：

```bash
# 启动本地热重载预览，默认监听 http://127.0.0.1:8000/
python -m mkdocs serve

# 严格模式构建静态产物（把警告当成错误处理）
python -m mkdocs build --strict
```

## 几个容易忽略的细节

- **关于 `--strict` 参数**：顺带一提，推送之前最好先在本地跑一遍 `mkdocs build --strict`。因为工作流里也是加了 `--strict` 的，万一文档里手滑把相对链接写错了（比如把 `about.md` 写成 `docs/about.md`），本地几秒钟就能报出来拦住，总比推上去等一两分钟看 Actions 飘红要强就是了。
- **关于 `site/` 目录**：本地跑完 `build` 之后根目录会多出一个 `site/` 文件夹，里面全是编译好的 HTML/CSS/JS。这玩意已经在 `.gitignore` 里排除了，千万别手动去改里面的文件，也别塞进 Git 提交。
- **关于触发路径**：目前工作流只监听了 `docs/**`、`mkdocs.yml`、`requirements.txt` 和工作流文件本身。如果只是改外面的 `README.md` 或者 `report/` 目录下的实验报告，push 上去是不会触发重新部署的，属于正常现象。

需要看代码块和表格混合排版效果的话，可以接着看下一页的 [API 参考](api.md)。
