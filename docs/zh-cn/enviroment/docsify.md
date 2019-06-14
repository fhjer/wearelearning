# Docsify

我们来了解一下docsify+markdown搭建的在线文档。

目前docsify环境只是我本地的环境，在线环境如何搭建后续学习后再慢慢总结。

## 官方文档

<https://docsify.js.org/#/zh-cn>

## 安装

推荐安装 `docsify-cli` 工具，可以方便创建及本地预览文档网站。

```bash
npm i docsify-cli -g
```

## 初始化项目

如果想在项目的 `./docs` 目录里写文档，直接通过 `init` 初始化项目。

```bash
docsify init ./docs
```

## 开始写文档

初始化成功后，可以看到 `./docs` 目录下创建的几个文件

- `index.html` 入口文件
- `README.md` 会做为主页内容渲染
- `.nojekyll` 用于阻止 GitHub Pages 会忽略掉下划线开头的文件

直接编辑 `docs/README.md` 就能更新网站内容，当然也可以[写多个页面](https://docsify.js.org/#/zh-cn/more-pages)。

## 本地预览

在`docs`目录下运行命令：

`docsify serve`

可以实时的预览，默认访问 [http://localhost:3000](http://localhost:3000/) 。

## index.HTML文件

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title> 文档中心 </title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Description">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <!-- <link rel="stylesheet" href="vender/themes/theme-defaults.css"> -->
  <link rel="stylesheet" href="vender/themes/theme-simple.css">
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      name: '在线文档系统',
	  loadSidebar: true,
	  subMaxLevel: 3,
	  loadNavbar: true,
	  relativePath: true,
	  auto2top: true,	    
	  alias: {
		'/':'/zh-cn/',
        '/_sidebar.md': '/zh-cn/_sidebar.md',
		'/.*/_navbar.md': '/_navbar.md'
	  },
      //主题组件
	  themeable: {
		readyTransition: true,
		responsiveTables: true
	  },
	//搜索---貌似跟配置的顺序有关系
	  search: {
		maxAge: 86400000, // 过期时间，单位毫秒，默认一天
		paths: 'auto',		
		// 支持本地化
		placeholder: {
			'/en-us/': 'Type to search',
			'/': '搜索'			
		},
		// 支持本地化
		noData: {
			'/en-us/': 'No Results',
			'/': '找不到结果'
		},
		// 搜索标题的最大程级, 1 - 6
		depth: 2
    },
	  // 翻页设置
	  pagination: {
		previousText: '上一章节',
		nextText: '下一章节',
		crossChapter: true
	 },	
	 	  //页签设置
	  tabs: {
		persist    : true,      // default
		sync       : true,      // default
		theme      : 'classic', // default
		tabComments: true,      // default
		tabHeadings: true       // default
	  },
	 	 // 代码拷贝
	  copyCode: {
		buttonText : {
		'/en-us/': 'Copy to clipboard',
		'/': '单击复制'
		},
		errorText  :  {
		'/en-us/': 'Error',
		'/': '复制失败'
		},
		successText:   {
		'/en-us/': 'Copied',
		'/': '复制成功'
		}
	  },
	  //说明、提示、警告、注意样式设置
	 'flexible-alerts': {
		style: 'flat',//或'callout'，'flat'
		note: {
			label: {
			'/en-us/': 'Note',
			'/': '说明'
			}
		},
		tip: {
			label: {
			'/en-us/': 'Tip',
			'/': '注意'
			}
		},
		warning: {
			label: {
			'/en-us/': 'Warning',
			'/': '警告'
			}
		},
		danger: {
			label: {
			'/en-us/': 'Attention',
			'/': '危险'
			}
		}
    }
  }
  </script>

  <script src="vender/docsify.js"></script>
  <script src="vender/plugins/docsify-themeable.js"></script>
  <script src="vender/plugins/zoom-image.min.js"></script>
    <!--搜索插件-->
  <script src="vender/plugins/search.js"></script>
    <!--翻页插件-->
  <script src="vender/plugins/docsify-pagination.min.js"></script>
    <!--页面页签插件-->
  <script src="vender/plugins/docsify-tabs.js"></script>
  <!--代码拷贝插件-->
  <script src="vender/plugins/docsify-copy-code.min.js"></script>
      <!-- Alerts样式插件 -->
  <script src="vender/plugins/docsify-plugin-flexible-alerts.min.js"></script>
  <!-- 插入PDF文件插件 PDFObject.js is a required dependency of this plugin -->
  <script src="vender/plugins/pdfobject.min.js"></script>
  <script src="vender/plugins/docsify-pdf-embed.js"></script>

</body>
</html>

```











