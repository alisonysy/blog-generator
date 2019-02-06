---
title: DOM文档对象模型初探
date: 2019-01-23 17:31:24
tags: JavaScript
---
DOM，即Document Object Model，中文翻译是文档对象模型。它把文档映射成对象，是连接网页的一种接口，？不太懂？
我们看到的每一个网页(web page)，是一个文档(document)。文档上面有很多不同的元素、内容、样式等等，那我们往文档上面添加JS时候，应该怎么找到对应的东西呢？这时DOM就派上用场，它把HTML文档组织成一个由节点(node)连接成的树形结构，每一个节点包含对象，当我们需要拿到、添加、更改、删除文档中的某些东西时，我们可以通过DOM来做到。
![What DOM is?](https://i.loli.net/2019/01/26/5c4bbe45837a9.png)
那么，操作DOM的API主要有哪些类型？

### Document
Document类型的接口代表浏览器中的页面，< html >的实例是由Document构造出来的，相当于DOM树形结构的大门，通过Document API我们可以对HTML文档做进一步操作。
```
var webAddr = document.documentURI;
console.log(webAddr);

//这会打印出当前页面的网址
```

### Element
Element是文档对象继承的最广泛的基本类型。其中HTMLElement接口是HTML里元素的基本接口。

常见的Element属性：
**Element.attributes** 以NamedNodeMap对象的形式返回对应的HTML里元素的属性
**Element.classList** 以DOMTokenList返回元素的类，后面可以添加.add或.remove来增加或删除类。与className不同的是，classList返回的是一个伪数组，可以通过*Element*.classList[ x ]来获得其中一个类的值，而className返回的是包含所有值的字符串。
**Element.clientHeight** 对于有CSS样式或内联布局盒子的元素来说，它返回一个元素的内部高度的数值(不包含margin、border、横向滚动条的高度)
**Element.clientTop** 是元素的顶部边框的像素宽度。clientTop是offsetTop和client area top中间的部分。
**Element.id** 可以查找某个元素的id，也可设置某个元素的id，还可通过getElementById()来获取一个HTML里的元素。
```
var idString = element.id; // 查询某个元素的id
element.id = idString; //对某个元素设置id
```
**Element.tagName** 在HTML文档中会返回对应元素的标签名。

常见的Element方法：
**Element.getAttribute()** 返回一个指定元素的属性的值。
**Element.getBoundingClientRect()** 返回一个元素的大小及其相对于视窗的位置。返回的值包括left, top, right, bottom, x, y ,width和height。
**Element.getElementsByClassName()** 提供一个类的名称，然后返回指定类的元素。
**Element.querySelectorAll()** 可以提供以CSS形式写的选择器，浏览器以NodeList的形式返回所有符合这个选择器的元素。与**Element.querySelector()**不同的是，querySelectorAll()会返回所有符合的元素，但querySelector()只返回符合的第一个元素。
**Element.scrollTo(x-coord, y-coord)** 用于在一个元素内滚动到对应的位置。常使用window.scrollTo()使当前视窗滚动到指定地方。
**Element.toggleAttribute()** 用于为指定元素设置一个添加/删除属性的开关，若该元素有相关属性，则删除它；若无，则添加。

### NodeList
一个NodeList是由通过诸如Node.childNodes属性或document.getElementByTagName()方法得到的所有节点组成的集合，注意，返回的集合不是数组，但可以使用数组的forEach()方法，而且可使用Array.from()将其转换成真正的数组。

NodeList的属性：
**NodeList.length** 是唯一的属性，当这个NodeList是动态的时候，当有新的节点加入NodeList时，NodeList.length会动态变化，否则，length在第一次获取后若没有重新获取，则保持第一次获取时的值。

NodeList的方法：
**NodeList.item() / NodeList[ item ]** 返回列表中的节点元素。
**NodeList.entries() / NodeList.keys() / NodeList.values()** 均返回节点迭代器。
**NodeList.forEach()** 对节点列表中每一个元素执行一个指定函数。
---
EventTarget是由对象执行的、可以接收和监听事件的DOM接口。Element, Document, 和Window是最常见的事件对象。

---
TBC