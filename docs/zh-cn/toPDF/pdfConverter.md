# docsify-pdf-converter

`docsify-pdf-converter`插件将docsify文档导出为PDF格式的文档。

## 安装环境

win10系统

### 在线安装

1. 以管理员身份运行`cmd.exe`，执行安装命令：

   `npm install --save-dev docsify-pdf-converter@2.1.0-beta.0 -g`或`npm i docsify-pdf-converter -g`

   其中，参数`--save-dev`的含义是代表把安装包信息写入package.json文件的`devDependencies`字段中，包安装在指定项目的node_modules文件夹下；若在安装插件后加上`@版本号`可以指定安装的版本，否则默认安装最新正式版本。
   
   > [!Note]
   >
   > windows环境下使用上述安装命令时，会报错或安装依赖不全。
   >
   
2. 若直接执行以上安装命令，安装失败或者依赖包安装不全，则可依次执行以下命令，以解决上一步骤中出现的问题。

   ```bash
   npm install -g cnpm --registry=https://registry.npm.taobao.org
   cnpm i puppeteer
   `cnpm i docsify-pdf-converter -g`或`cnpm install --save-dev docsify-pdf-converter -g`（全局安装）
   ```
   
3. [配置参数](#参数配置)。

4. 安装后，发现配置完参数，执行时若报错：No docs found, please run docsify init first。

   1. 在github上下载修正版的[源码文件](https://github.com/FabianGosebrink/docsify-to-pdf-converter/tree/fabiangosebrink/fixing-path-pf-served-concatenated-md)。

   2. 用其替换`C:\Program Files\nodejs\node_global\node_modules\docsify-pdf-converter`下的内容即可。

### 离线(尚未尝试)

将在联网环境下全局安装的docsify-pdf-converter文件夹，连同`converter`、`converter.cmd`、`docsify-pdf-converter`和`docsify-pdf-converter.cmd`，拷贝到内网对应的全局安装路径下。

```bash
`docsify-pdf-converter`和`docsify-pdf-converter.cmd`等文件所在路径：
C:\Program Files\nodejs\node_global

`docsify-pdf-converter文件夹`所在路径:
C:\Program Files\nodejs\node_global\node_modules
```



## 参数配置

1. 创建文件：`.docsifytopdfrc.<js|json|yaml>`。

   1)  若在文档根目录（即`docs`）下创建该文件，则以`json`文件为例，其内容应为：

   

   ```json
   
   {
     "pathToStatic":"static"      //合并生成的md文件的存放路径及文件夹名称
     "mainMdFilename": "TEST-documentation.md",   //合并生成的md文件，在static文件夹下
     "removeTemp": true,
     "contents": "zh-cn/_sidebar.md",   //文档目录获取，按_sidebar.md文件中列出的文件生成
     "pathToPublic": "pdf/TEST-documentation.pdf", //生成的pdf文件存放路径及文件名
     "pdfOptions": {
       "format": "A4", //纸张大小
       "margin": {   //页边距设置
   		"top": "2cm",
   		"right": "1.8cm",
   		"bottom": "2cm",
   		"left": "1.8cm"
    	 },
   	"displayHeaderFooter" : true    //页眉页脚显示，缺省关闭，开启后，页眉缺省展示为文档标题和日期，页脚展示URL和页码，有headerTemplate和footerTemplate，但是没找到正确的设置方法。
     },
     "emulateMedia": "screen",
     "pathToDocsifyEntryPoint": "."
   }
   ```

   > [!Tip]
   >
   > 在`docs`文件夹下创建该文件，能够直接成功生成PDF，但是页面排版比较紧凑。

   

   2) 若在`docs`外部创建，则应配置为：

   ```json
   {
     "pathToStatic":"static"      //合并生成的md文件的存放路径及文件夹名称
     "mainMdFilename": "TEST-documentation.md",   //合并生成的md文件，在static文件夹下
     "removeTemp": true,
     "contents": "docs/zh-cn/_sidebar.md",   //文档目录获取，按_sidebar.md文件中列出的文件生成
     "pathToPublic": "pdf/TEST-documentation.pdf", //生成的pdf文件存放路径及文件名
     "pdfOptions": {
       "format": "A4"
     },
     "emulateMedia": "screen",
     "pathToDocsifyEntryPoint": "./docs"
   }
   ```

   

   > [!Tip]
   >
   > 此时可生成合并后的md，但不能直接成功生成正确的PDF，因为生成的PDF中无内容。这是由于'docsify-pdf-converter\src\render.js'中获取的发布路径如下：
   > const docsifyUrl = `http://localhost:${docsifyRendererPort}/#/${pathToStatic}/${mainMdFilenameWithoutExt}`;
   > 解读后个人认为需要将生成的md文件放在docs文件夹下，但是此配置生成不知为何是在docs外部生成的，如果将 "pathToStatic":"static" "pathToStatic":"docs/static"，按代码解析的路径并不正确。
   > 目前不知道怎么修改代码使得获取该路径与配置解耦合。
   > 之前总是报错时，按照此配置生成的static文件夹却是在docs目录下，现在不知怎滴又不成了。

   

2. 创建`package.json`文件或将安装时生成的`package.json`拷贝到`docs`目录下，并增加以下内容。

   ```json
   在`package.json`文件中增加以下内容：
   {
     "scripts": {
       "convert": "node_modules/.bin/docsify-pdf-converter"
     }
   }
   此文件位置跟`.docsifytopdfrc.<js|json|yaml>`一致即可。
   ```

   

3. 在`docs`目录下执行命令`npm run convert`，生成PDF。

> [!Tip]
>
> _sidebar及各index文件中需修改为相对路径，绝对路径时会报错。
>
> 如果是在docs外配置的参数文件，那么建议手动转换成PDF：由于使用了docsify-tabs、alerts等插件，建议修改掉tabs后，本地发布以下，然后通过浏览器打印生成PDF，这样就能转化插件引入的风格，否则会有代码。
>
> 另外：导出PDF时，不会生成目录；另存为PDF时，内部的一些链接会失效。表格无法调整，表格过大时，没办法复用标题行，禁止跨页断行等等。
>
> 如果直接用Typora导出PDF可以生成目录，但目录级别是错乱的。



## 卸载

以管理员身份运行`cmd.exe`，执行全局卸载命令：`npm uninstall -g docsify-pdf-converter`