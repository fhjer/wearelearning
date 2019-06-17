# 主题&插件

## 主题说明

除去docsify本身自带的集中主题外，还有一种主题：`docsify-themeable`。

它本身具有三种主题，可对其主题进行定制修改。

<https://jhildenbiddle.github.io/docsify-themeable/#/>

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

#### 导出参数配置

创建配置文件`.docsifytopdfrc.<js|json|yaml>`，或在当前项目的 `package.json`文件中增加`"docsifytopdf"`配置。

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

#### FAQs

**问题描述1**：

执行转换命令后，系统报错：

```bash
internal/modules/cjs/loader.js:584
    throw err;
    ^

Error: Cannot find module 'C:\Program Files\nodejs\node_global\node_modules\docsify-pdf-converter\.bin\cli.js'
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:582:15)
    at Function.Module._load (internal/modules/cjs/loader.js:508:25)
    at Function.Module.runMain (internal/modules/cjs/loader.js:754:12)
    at startup (internal/bootstrap/node.js:283:19)
    at bootstrapNodeJSCore (internal/bootstrap/node.js:622:3)
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! docsify-pdf-converter@2.1.0-beta.0 convert: `docsify-pdf-converter`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the docsify-pdf-converter@2.1.0-beta.0 convert script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
npm WARN Local package.json exists, but node_modules missing, did you mean to install?

```

**解决办法**：

1. 下载插件源文件：<https://github.com/meff34/docsify-to-pdf-converter>。
2. 解压缩后将`.bin`文件夹拷贝至`C:\Program Files\nodejs\node_global\node_modules\docsify-pdf-converter\`。

**问题描述2**：

执行转换命令后，系统报错：

```bash
internal/modules/cjs/loader.js:584
    throw err;
    ^

Error: Cannot find module 'rcfile'
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:582:15)
    at Function.Module._load (internal/modules/cjs/loader.js:508:25)
    at Module.require (internal/modules/cjs/loader.js:637:17)
    at require (internal/modules/cjs/helpers.js:22:18)
    at Object.<anonymous> (C:\Program Files\nodejs\node_global\node_modules\docsify-pdf-converter\.bin\cli.js:3:16)
    at Module._compile (internal/modules/cjs/loader.js:701:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:712:10)
    at Module.load (internal/modules/cjs/loader.js:600:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:539:12)
    at Function.Module._load (internal/modules/cjs/loader.js:531:3)
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! docsify-pdf-converter@2.1.0-beta.0 convert: `docsify-pdf-converter`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the docsify-pdf-converter@2.1.0-beta.0 convert script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
npm WARN Local package.json exists, but node_modules missing, did you mean to install?

```

**解决办法**：

执行命令，安装rcfile：

cnpm install --save rcfile

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

你好!

### **English**

Hello there!

<!-- tabs:end -->