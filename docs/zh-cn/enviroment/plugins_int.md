# 主题&插件

## 主题说明

除去docsify本身自带的集中主题外，还有一种主题：`docsify-themeable`。

它本身具有三种主题，可对其主题进行定制修改。

<https://jhildenbiddle.github.io/docsify-themeable/#/>

###CSS定制
图片居中设置
```bash
.markdown-section img{
	max-width: 100%;
	//垂直居中
	vertical-align: middle;
	//水平居中
	margin: 0 auto;
	display: block
	/*block 块元素，前后换行，设置为此值事，水平居中才会生效；inline 行内元素，前后不换行，默认值*/
	
}
```

## 插件说明

此处介绍的插件，详细介绍可参考[docsify官方文档](<https://docsify.js.org/#/zh-cn/awesome?id=plugins>)。

### 嵌入PDF

> [!Tip]
>
> 嵌入PDF插件加入后，影响docsify发布结果:
>
> 问题现象：侧边栏新加入的md无法访问。
>
> 解决办法：注释掉html中引入该脚本的代码后，可以访问了

markdown用法：


```pdf
	PDF文件引用路径
```

示例：

```pdf
/zh-cn/pdfEmbed.pdf
```

### 导出PDF

`docsify-pdf-converter`插件将docsify文档导出为PDF格式的文档。

#### 安装插件

以管理员权限运行cmd.exe，执行安装命令：

`npm install --save-dev docsify-pdf-converter`

若直接执行以上安装命令，安装失败，则可依次执行以下命令：

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm i puppeteer
cnpm install --save-dev docsify-pdf-converter
```

若安装后发现`C:\Program Files\nodejs\node_global\node_modules\docsify-pdf-converter`下无`.bin`文件夹，则下载插件源文件，进行离线安装：

```bash
在解压的离线包文件夹下执行命令：
cnmp intall 
```



#### 导出参数配置

在当前项目下创建配置文件`.docsifytopdfrc.<js|json|yaml>`，并在`package.json`文件中增加`"docsifytopdf"`配置。

配置文件 `.docsifytopdfrc.js` 内容如下：

```js
module.exports = {
  contents: [ "docs/_sidebar.md" ], // array of "table of contents" files path
  pathToPublic: "pdf/readme.pdf", // path where pdf will stored
  pdfOptions: "<options for puppeteer.pdf()>", // reference: https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pagepdfoptions
  removeTemp: true, // remove generated .md and .html or not
  emulateMedia: "screen", // mediaType, emulating by puppeteer for rendering pdf, 'print' by default (reference: https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pageemulatemediamediatype)
}
```

若为`.docsifytopdfrc.json`，则文件内容如下：

```json
{
  "mainMdFilename": "TEST-documentation.md",
  "removeTemp": true,
  "contents": "_sidebar.md",
  "pathToPublic": "./TEST-documentation.pdf",
  "pdfOptions": {
    "format": "A4"
  },
  "emulateMedia": "screen",
  "pathToDocsifyEntryPoint": "."
}

```

在`package.json`中增加脚本：

```json
{
  "scripts": {
    "convert": "node_modules/.bin/docsify-pdf-converter"
  }
}
```

执行命令：

```sh
npm run convert
```

> [!Tip]
>
> 转换成功的前提：
>
> 1. 不能嵌套文件夹
> 2. siderbar中不能是多级列表
> 3. 不能再siderbar中套用index这种指向其他md文件的md
>
> 生成PDF的缺点：
>
> - 不能生成目录
>
> - 不能显示图片



### Alerts样式

`docsify-plugin-flexible-alerts.min.js`提供多种告警样式。

> [!Tip]
>
> Alert样式有好几个参数，各参数的使用说明请参见[Alert插件介绍](<https://github.com/zanfab/docsify-plugin-flexible-alerts>)。

markdown用法：

```html
> [!NOTE]
> An alert of type 'note' using global style 'callout'.
> [!NOTE|style:flat]
> An alert of type 'note' using alert specific style 'flat' which overrides global style 'callout'.

```

> [!NOTE]
> flat样式的说明。

> [!NOTE|style:callout]
>
> callout样式的说明，覆盖了flat样式的说明。

> [!Tip|label:自定义标题|iconVisibility:hidden]
>
> 自定义标题的注意，隐藏图标。

### 页签插件docsify-tabs

#### 参考文档

MD文件中页签插件，使用说明路径：

<https://jhildenbiddle.github.io/docsify-tabs/#/>

脚本路径：

<!-- docsify (latest v4.x.x)-->

<script src="https://cdn.jsdelivr.net/npm/docsify@4"></script>

<!-- docsify-tabs (latest v1.x.x) -->

<script src="https://cdn.jsdelivr.net/npm/docsify-tabs@1"></script>

#### 使用说明

> [!Note]
>
> 标题尝试+Tab嵌套：不可以！
>
> 页签名字格式应为`标题（1-6识别出来都一样）+加粗`格式，才会识别为标签。
>
> 标签区域要以`<!-- tabs:start -->`开始，以`<!-- tabs:end -->`结束。

#### 示例

<!-- tabs:start -->

### **中文**

#### 内部标题1

> 这是引言

你好!

| head1 | head2 |
| ----- | ----- |
| note  | note  |

列表

- list 1
- list 2
- 。。。

#### 内部标题2

### **English**

#### Heading1

Hello there!

#### Heading2

> this is a test.

we can try.

<!-- tabs:end -->