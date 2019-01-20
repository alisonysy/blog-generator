---
title: JS的数据类型
date: 2019-01-20 19:36:41
tags: JavaScript
---

JavaScript里有**7**种数据类型，分别是string(字符串)、number(数字)、boolean(布尔值)、undefined、null、symbol和object(对象)。Symbol是ES 6引入的，此处不论述，具体可以参考方应杭老师的[知乎链接](https://zhuanlan.zhihu.com/p/22652486)。

## string 字符串
字符串是0或多个排在一起的字符，通常放在''或“”之中。
字符串默认只能写1行，若需要写多行，可以使用‘+’连接运算符来连接多个单行字符串，但连接后的字符串输出仍然是1行。若需要输出多行字符，可以使用 **`** 反引号包括多行的内容。如：
> ` 第一行
> 第二行
> 第三行
> `

这时将输出：
> " 第一行
> 第二行
> 第三行
> "

反斜杠 **\\**在字符串里可以用来表示其他的特殊字符，例如：
+ \\0: null
+ \\b: 后退键
+ \\f: 换页符
+ \\n: 换行符
+ \\r: 回车键
+ \\t: 制表符
+ \\': 单引号
+ \\\: 反斜杠

## number 数字
数字在JavaScript内是以64位浮点数的形式储存的，这导致包含小数的运算时，结果可能不准确，如：
(```)
(0.4 - 0.2) === (0.5 - 0.3) //false
(```)

JavaScript里允许的数值范围可以通过
> Number.MAX_VALUE //1.7976931348623157e+308
> Number.MIN_VALUE //5e-324

来确定。

当一个数值小数点前的数字多于21位(不包含21位)的时候，JS里会自动将数值转为科学计数法：用*exx*或是*e+xx*来表示(xx为小数点从科学计数法转换为普通字面形式时应后退的位数)
当一个数值小数点后的0多于5个时，JS会自动将数值转为科学计数法：用*e-xx*来表示
(```)
0.00000008 // 8e-8
(```)

当需要检测一个事物是否为number时，可使用typeof：
(```)
var s = 123;
var d = '123';

typeof s // number
typeof d // string
(```)

## boolean 布尔值
Boolean的值只有**true**(真)和**false**(假)两个。通过*前置逻辑运算符 !(Not)*、*相等运算符 ===、!==、==、!=*，和比较运算符*>、>=、<、<=* ，可在运算的地方返回布尔值。同时以下的值会返回false：
+ undefined
+ null
+ false 
+ 0
+ NaN
+ ''或"" (空字符串)

## null和undefined
null在JS中表示“没有”，undefined在JS中表示未定义，两者之间十分相似。通过<kbd>==<kbd>来查询，两者是相等的。
(```)
undefined == null //true
(```)

当一个变量被声明但未赋值时，该变量是undefined；而创建1个对象，但先不赋值时，惯例把该对象设为null。

## object 对象
对象是一组“键值对”(key-value)的无序的复合数据集合。里面的键名key是对象的属性property，若键名是数字，则会自动转换成字符串。
我们可以通过Object.keys()的方法查询一个对象的所有属性。
(```)
var a = {
  p1: 'xxx',
  p2: 'yyy'
};

Object.keys(a) //['p1','p2']
(```)

我们还可以通过历遍属性的方法for..in..循环来get到一个对象的键值对：
(```)
var a = {
  p1:'xxx',
  p2:'yyy',
  p3:'zzz'
}

for (var key in a){
  console.log(key + ':' + a[key]);
}
//p1:xxx
//p2:yyy
//p3:zzz
(```)