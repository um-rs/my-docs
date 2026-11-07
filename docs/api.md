# API 参考

> 说明：本站是纯静态托管在 GitHub Pages 上的，下面这两个接口只是拿来测试技术文档里写接口说明、参数表格和 JSON 代码块的排版效果，并没有挂真实的后端服务就是了。

## 1. 查询文档列表

按分页或关键词拉取当前站点收录的文档条目摘要。

- **请求方法**：`GET`
- **请求路径**：`/api/docs`

### 请求参数（Query）

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| `page` | integer | 否 | 页码，默认从 `1` 开始 |
| `keyword` | string | 否 | 按标题模糊检索，比如传 `指南` |

### 返回示例（200 OK）

```json
{
  "total": 4,
  "page": 1,
  "items": [
    {
      "id": 1,
      "slug": "index",
      "title": "vita 的技术文档",
      "updated_at": "2026-11-07"
    },
    {
      "id": 2,
      "slug": "guide",
      "title": "使用指南",
      "updated_at": "2026-11-07"
    }
  ]
}
```

---

## 2. 获取单篇文档详情

根据文档 `id` 查询对应的正文摘要和元信息。

- **请求方法**：`GET`
- **请求路径**：`/api/docs/{id}`

### 返回示例（200 OK）

```json
{
  "id": 2,
  "slug": "guide",
  "title": "使用指南",
  "author": "um-rs",
  "summary": "本地虚拟环境配置、预览命令以及自动部署触发规则说明。",
  "url": "https://um-rs.github.io/my-docs/guide/"
}
```

### 异常返回示例（404 Not Found）

当传入的 `id` 不存在时，接口返回对应的错误提示：

```json
{
  "error": "DOC_NOT_FOUND",
  "message": "未找到对应 ID 的文档条目"
}
```

---

看完接口排版示例后，可以点击返回 [使用指南](guide.md) 或回到 [首页](index.md)。
