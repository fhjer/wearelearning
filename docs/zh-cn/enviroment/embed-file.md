# 文件嵌入

docsify 4.6 开始支持嵌入任何类型的文件到文档里。你可以将文件当成 `iframe`、`video`、`audio` 或者 `code block`，如果是 Markdown 文件，甚至可以直接插入到当前文档里。

详细介绍请参见https://docsify.js.org/#/zh-cn/embed-files

## 案例尝试

### md文档

链接形式：[嵌入md](/zh-cn/产品知识学习/FAQ模板.md)

内容显示(经验证，并未按官方文档中显示成当前文档的一部分)：[嵌入md](/zh-cn/产品知识学习/FAQ模板.md                                           ':include')

### 嵌入EXCEL

[excel](/zh-cn/enviroment/test.xlsx)

### 嵌入PDF

> [!Tip]
>
> 嵌入PDF插件加入后，影响docsify发布结果:
>
> 问题现象：侧边栏新加入的md无法访问。
>
> 解决办法：注释掉html中引入该脚本的代码后，可以访问了

需要在html入口文件中增加插件引入链接（实际上不加也可以用）：

```HTML
<!-- PDFObject.js is a required dependency of this plugin -->
<script src="//cdnjs.cloudflare.com/ajax/libs/pdfobject/2.1.1/pdfobject.min.js"></script> 
<!-- 下面这两个选择一个使用即可，如果把插件下载到了本地，需将路径改为本地路径。-->
<!-- This is the source code of the pdf embed plugin -->
<script src="path-to-file/docsify-pdf-embed.js"></script>
<!-- or use this if you are not hosting the file yourself -->
<script src="//unpkg.com/docsify-pdf-embed-plugin/src/docsify-pdf-embed.js"></script>

```

markdown用法：

```html
​```pdf
PDF文件的引用路径
​```
```



示例：

```pdf
/zh-cn/pdfEmbed.pdf
```

[PDF嵌入](/zh-cn/pdfEmbed.pdf)