---
title: 初识HTML——常用标签介绍.md
date: 2019-01-12 22:09:53
tags: HTML
---

  HTML的标签有很多，每个HTML文档都有的是< html >、< head >、< body >，最常用的包括< div >、< span >、< a >、< ul >/< ol >和< li >、< table >等。其中< div >和< span >是没有任何默认样式的，当HTML里只有< div >< /div >或< span >< /span >是没有任何显示的。这篇文章着重介绍< a >、< ul >/< ol >和< li >、< table >。

## < a > 超链接
  a标签是anchor锚点的意思，它会创建一个连接到其他网页、文件、邮箱地址，甚至同一页面的其他地方的超链接。一个简单的< a >标签写法：
  > < a href="跳转的内容" > 链接文本 < /a > 

  *注意：*在< a >标签里不能内嵌另一个< a >标签。

  ### < a >标签常见属性：
  #### 1. href="跳转的内容"
  href后面可接：

  **1)URL**：包括网页地址、ftp地址、邮箱等，当内容没有指定协议类型时，如
  > href="//baidu.com"

  href会根据HTML文档的协议类型补全路径。若在本地直接打开编写的HTML文档，则为file:协议，无法找到baidu.com。
  
  **2)javascript伪协议**：可用于实现点击< a >标签后不跳转到别的地方，或在当前页面执行一段代码的效果。如
  > href="javascript:;"

  这样点击< a >标签时，页面不会有任何反应。

  **3)#/#id**：
  > href="#"

  此时点击< a >标签会返回当前页面顶部。

  > href="#id"

  此时点击< a >标签会返回当前页面指定的id的部分。

  **4)直接空的""**：此时点击< a >会刷新页面

  #### 2. target="呈现跳转内容的方式"
  target后面可接：

  **1)_blank**：表示打开一个新的标签页或窗口展示链接的内容

  **2)_self**：表示在当前的页面打开链接的内容

  **3)_parent**：表示在当前页面的父框架中打开链接的内容，若没有父框架元素，则在当前窗口打开

  **3)_top**：表示在当前页面的顶层窗口打开链接的内容，若只有父框架，则用父框架打开；若没有顶层窗口或父框架，则在当前页面打开

  #### 3. download
  在< a >标签中加入download会指示浏览器下载URL而不是导航到URL。

---

## < ul >/< ol >和< li > 列表
  当我们需要*列表*时，我们会选择：
  <ul><li>无序的列表，用< ul >和< li >表示</li></ul>    或是
  <ol><li>有序的列表，用< ol >和< li >表示</li></ol>

  ### 无序列表的用法：
  > < ul >
      < li > 文本 < /li >
      < li > 文本 < /li >
      ..
    < /ul >

  ### 有序列表的用法：
  > < ol >
      < li > 文本 < /li >
      < li > 文本 < /li >
      ..
    < /ol >

---

## < table > 表格
  要在HTML里呈现表格，首先要写
  > < table >
  > 表格内容
  > < /table >
  
  其中“表格内容”包含的元素有：
  1. < caption > 标题，可有可无
  2. < colgroup > ，可有0或多个
  3. < thead > 表头，可有可无
  4. 以下2个元素其中1个：
        < tbody > 0或多个；
        < tr > 1或多个
  5. < tfoot > ，可有可无
  用< tr >元素表示1行，< td >元素表示1个单元格内的数据。表格里的列数由任意一个< tr >元素里的< td >或< th >元素的**最大数量**决定。

  这是个栗子：
  <table border=3px align="center">
  <caption>这是表格标题</caption>
  <colgroup>
    <col width="100">
    <col width="50">
  </colgroup>
  <thead>
    <tr>
      <th>项目1(宽度为100px)</th>
      <th>项目2(宽度为50px)</th>
      <th>项目3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>数据1</td>
      <td>数据2</td>
      <td>数据3(没有设置宽度)</td>
      <td>数据4(我是多了出来的)</td>
    </tr>
    <tr>
      <td>数据5</td>
      <td>数据6</td>
      <td>数据7</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>总数1</td>
      <td>总数2</td>
      <td>总数3</td>
    </tr>
  </tfoot>
  </table>

### < caption >
  > < caption > 标题文本 < /caption >

### < colgroup >
  < colgroup >元素内可设置每个列的宽度，和指定列的背景颜色（不推荐用HTML指定背景颜色）。
  设置指定列的宽度：
  > < colgroup >
  >     < col width="100" > 第一列宽度为100px
  >     < col width="50" > 第二列宽度为50px
  >     当没有第三个/第n个< col width >时，会默认宽度为能容纳文本的宽度
  >  < /colgroup >

### < thead >
  用< thead >元素表示这是表头。里面可包含< tr >、< th >或< td >。< th >元素会加粗文本，表示项目。
  > < thead >
  >   < tr >
  >     < th > 项目1 < /th >
  >     < th > 项目2 < /th >
  >     < th > 项目3 < /th >
  >   < /tr >
  > < /thead >

### < tbody >
  > < tbody >
  >   < tr >
  >     < td > 数据1 < /td >
  >     < td > 数据2 < /td >
  >     < td > 数据3 < /td >
  >     < td > 数据4 < /td >
  >   < /tr >
  >   < tr >
  >     < td > 数据5 < /td >
  >     < td > 数据6 < /td >
  >     < td > 数据7 < /td >
  >   < /tr >
  > < /tbody >

  此处例子的< tbody > 部分有2行，其中第一行因为有4个单元格，导致整个表格多了1列。

### < tfoot >
  < tfoot >可用作为总计的行。
  > < tfoot >
  >   < tr >
  >     < td > 总数1 < /td >
  >     < td > 总数2 < /td >
  >     < td > 总数3 < /td >
  >   < /tr >
  > < /tfoot >

### < thead >, < tbody > 和< tfoot >的作用
  这3个元素在HTML表格里其实是可有可无，他们的作用是*按顺序*标记表格的内容，即无论编程时三个元素的顺序如何，在前端展示< thead >的内容总在< tbody >前，< tbody >的内容总在< tfoot >前。