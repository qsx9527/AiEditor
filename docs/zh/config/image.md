# 图片配置

## 示例代码

```typescript
new AiEditor({
    element: "#aiEditor",
    image: {
        customMenuInvoke: (editor: Editor) => {
        },
        uploadUrl: "https://your-domain/image/upload",
        uploadHeaders: {
            "jwt":"xxxxx",
            "other":"xxxx",
        },
        uploader: (file, uploadUrl, headers, formName) => {
            //可自定义图片上传逻辑
        },
    },
})
```


- **customMenuInvoke**：自定义工具类的 “图片” 按钮的点击行为，比如点击不是选择本地文件，而是弹出一个对话框等自定义行为。
- **uploadUrl**：图片上传的 URL 地址。
- **uploadHeaders**：图片上传自定义 Http 头信息。
- **uploader**：自定义上传逻辑，默认是通过 `fetch` 进行上传。


## 服务器响应

图片上传成功后，要求服务器必须返回如下内容，其中 errorCode 必须为 0；

```json
{
  "errorCode": 0,
  "data": {
    "src": "http://your-domain.com/image.jpg",
    "alt": "图片 alt"
  }
}
```