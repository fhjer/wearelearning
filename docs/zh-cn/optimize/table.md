# 表格
> MarkDown+Docsify除去自身的语法、排版和渲染风格外，我们有时还需要进行文档中进行一些格式微调，这些调整则需要借助HTML+CSS。以下介绍一些微调小窍门。后续学习下HTML+CSS，巩固下基础。

## 单元格合并

MarkDown的表格语法无法实现单元格合并，可使用HTML的`<table></table>`标记对来实现。

<p><ul>无序列表：
    <li>使用跨行或者跨列时，使用th标签</li>
    <li>跨行： rowspan的的参数就是要跨的行数</li>
    <li>跨列： colspan的参数就是要跨的列数</li>
</ul>
</p>
<table frame="border" border="1">
    <thead>
        <tr>
        	<th rowspan="2"  valign="middle"  align="center">真实情况</th>
        	<th colspan="2" align="center">预测结果</th>
    	</tr>
        <tr>
       	 	<td>正例</td>
        	<td>反例</td>
    	</tr>
    </thead>
	<tbody>	<tr>
    	<td>正例</td>
    	<td>TP(真正例)</td>
    	<td>FN(假反例)</td>
	</tr>
	<tr>
    	<td>反例</td>
    	<td>FP(假正例)</td>
    	<td>TN(真反例)</td>
	</tr>
</tbody></table>


## 单元格宽度调整

> 两种方式：
>
> - 第1种，将在目标单元格中填充空格，或在句子较长的列中适当换行，以调整列宽；此方法比较笨拙。
>
> - 第2种，`<table>` 中表格的宽度由标题的 `<th>` 决定，我们只需要利用上 CSS 操作一番即可达到目的。
>
>   原作地址请参考：<https://blog.csdn.net/maxsky/article/details/54666998?utm_source=blogxgwz6>

通过CSS代码来对表格宽度进行调整：

```css
将表格第一列和第二列的列宽设置为100px。
<style>
table th:first-of-type {
	width: 100px;
}
table th:nth-of-type(2) {
    width: 100px;
}
</style>

<!-- 下方是表格的 Markdown 语法 --!>
名称|值|备注
---|---|---

说明：
首先，<th> 存在于 <table> 中；
其次，th:first-of-type 的意思是每个 <th> 为其父级的第一个元素，这里指的就是围绕着【名称】的 <th>。
同理，第二、三个使用 th:nth-of-type(2)、th:nth-of-type(3) 就可以了，以此类推。
上述的 th:first-of-type 等于 th:nth-of-type(1)。
```

> [!NOTE]
>
> - 若md中表格列数都一致，那么不管将`<style>`标签放置在何处，都会将当前md文件中所有的表格对应的该列列宽进行统一调整为设置的值。---`最适用的场景`
>
> - 若列数不一致，那么就近放置`<style>`标签，会将当前表格的某列宽设置为定义值。
>
>   其他不同列数表格的该列列宽不受本标签定义控制，会根据自身的单元格内部内容自行调整。

## 单元格内部样式

markdown自身的表格内部不支持有序或无序列表，我们可以使用HTML的标记对。

```html
<ol><li>有序标记对</li></ol>
<ul><li>无序标记对</li></ul>
如若需要展示列表下的信息，则直接在<li></li>标记对中使用换行标记<br>即可，使用<p></p>也能换行，但是前后会有空行，不美观，不建议使用。
```



