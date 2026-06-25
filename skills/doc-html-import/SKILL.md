---
name: doc-html-import
description: 文档/网页内容导入知识库系统，解析标题正文图片，下载上传图片替换URL，生成标准HTML。
version: 1.0.0
tags: [文档, HTML, 内容导入, 图片处理]
---

# Doc HTML Import Skill

## 触发场景

- Word 转 HTML
- 网页文章抓取
- 图片下载与替换
- 富文本内容导入
- 知识库内容录入

## 执行流程

1. **解析内容**
   - 解析标题（h1-h6）
   - 解析正文段落
   - 解析图片（`<img src="...">`）
   - 解析列表、表格、引用

2. **下载图片**
   ```javascript
   // 下载图片到本地临时目录
   const images = document.querySelectorAll('img')
   for (const img of images) {
     const url = img.src
     const filename = `image_${Date.now()}.png`
     await downloadImage(url, `./temp/${filename}`)
     img.setAttribute('data-local-path', `./temp/${filename}`)
   }
   ```

3. **上传图片**
   - 调用系统上传接口
   - 获取系统返回的 URL
   - 记录上传失败的图片

4. **替换图片地址**
   ```javascript
   // 替换本地路径为系统 URL
   for (const img of images) {
     const localPath = img.getAttribute('data-local-path')
     const systemUrl = await uploadImage(localPath)
     img.src = systemUrl
     img.removeAttribute('data-local-path')
   }
   ```

5. **生成标准 HTML**
   ```html
   <!DOCTYPE html>
   <html lang="zh-CN">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>${title}</title>
   </head>
   <body>
     <h1>${title}</h1>
     ${content}
   </body>
   </html>
   ```

6. **输出报告**
   - 成功导入的图片数量
   - 失败图片清单（URL + 失败原因）
   - 生成的 HTML 文件路径
   - 需要手动处理的图片

## 错误处理

- 图片下载失败：记录 URL 和错误，继续处理其他图片
- 上传接口超时：重试 3 次，仍失败则记录
- HTML 格式异常：尝试清理后重新解析
- 编码问题：统一转换为 UTF-8

## 禁止行为

- 不要跳过图片下载直接使用外链
- 不要在 HTML 中保留临时本地路径
- 不要忽略上传失败的图片
- 不要修改原文的标题和正文内容
