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

#### 安装

以管理员权限运行cmd.exe，执行安装命令：

`npm install --save-dev docsify-pdf-converter`

#### 配置



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