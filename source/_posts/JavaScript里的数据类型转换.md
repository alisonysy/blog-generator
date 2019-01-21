---
title: JavaScript里的数据类型转换
date: 2019-01-21 09:32:35
tags: JavaScript
---
我们知道JS里有7种数据类型，那么7种类型之间怎样进行转换呢？哪些API可以使用？

## 其他类型转换为string字符串
### .toString()属性
Number、boolean可以直接使用.toString()转换为字符串：
```
(3).toString() // '3'
//第一个()里为要转换的number
true.toString() //'true'
```
Null和undefined用.toString()时会有报错，而object的.toString()只会得到<kbd>[object Object]<kbd>的结果。
### ""/''空字符串+要转换的类型
一种更为方便也更万能的方法是用空字符串''加上要转换的类型：
```
1 + '' // "1"
true + '' // "true"

var a = {}; 
a + '';
//"[object Object]"

null + ''// "null"
undefined + ''// "undefined"
```

## 其他类型转换为boolean布尔值
### Boolean()
在Boolean()里加上要转换的类型，可以返回出对应的布尔值：
```
Boolean(2) // true
Boolean('string') // true
Boolean(NaN) // false
Boolean({name:'may'}) // true
```
### !!+要转换的类型
由于!在JS里表示“非”，!!得到的即数据类型用Boolean()转换时的值：
```
!! 2 // true
!! null // false
!! [] // true
```
我们可以观察到有些值转换为布尔值的时候，返回的是true，有些返回的是false，怎么区分呢？事实上，除了以下6个值返回的是false，其他返回的都是true：
> 0
> NaN
> null
> undefined
> false
> ''或""

## 其他类型转换为number数字
### Number()方法
```
Number('234') // 123
```
### parseInt()和parseFloat()方法
parseInt()和parseFloat()都能使一个字符串转换为数字。字符串也可以是以二进制(0b开头)、八进制(0o开头)、十六进制(0x开头)的。其中，使用parseInt()时默认把字符串转为十进制的数字，但可通过增加第二个参数来标明目标的进制：
```
parseInt('234') // 234
parseFloat('1.23') // 1.23
parseInt('234',8) // 156，这里的第二个参数告诉浏览器要把'234'转换为八进制的数字
parseInt('0x3401') // 13313，这里以'0x'开头表明字符串是以十六进制来转译的
```
### 字符串 - 0
另一个简单直接的方法就是用字符串减去一个0：
```
'0x3401' - 0 // 13313
true - 0 // 1

var phoneNum = '010234567'; 
phoneNum - 0;
// 10234567，注意浏览器会自动忽略数字前的0
```
### +/- 字符串
通过加号+或减号-再跟一个字符串的方式也可实现转换为数值的目标：
```
+ '0x3401' // 13313
- '-1' // 1
```

## 其他类型转换为object对象
7种数据类型中，原始类型的数据是直接用stack堆内存储存的，object是复杂类型，用stack堆内存储存object的值的地址，而heap堆内存储存object里的key-value。Object的地址可更改，object与值关系称为object的引用。
**数据的储存：**
![JS数据的储存：c和d指向的是两个不同的对象](https://i.loli.net/2019/01/21/5c4551d7cb2ef.jpg)

由于对象的属性可以动态创建，若创建对象后，要往对象添加属性，使用栈内存直接储存对象时，会占用大量内存，使速度变慢，所以一般使用栈内存储存对象地址，而堆内存储存对象里的键值对。若一开始创建了2个对象，假设是o1和o2，之后把o1的值赋予o2时，并没有创建新的对象，而是把o1对象储存的地址复制到了o2，即o2对象现在的地址与o1一样指向同一个键值对：
```
var o1 = {name:'xxx'}
var o2 = {name:'yyy'}

o2 = o1;
o2.name;
// "xxx"，因为现在o2的地址指向了{name:'xxx'}
```
此时，若通过属性object.property的方法修改o2的name，实际是修改原来的存在堆内存里的键值对：
```
var o1 = {name:'xxx'}
var o2 = {name:'yyy'}

o2 = o1;
o2.name = 'zzz';
o1.name;
// "zzz"，因为修改的是原来{name:'xxx'}的数据，由于o1和o2指向同一个地址，所以o1的name属性的值也会随之改变
```
但若是把另一个对象再次赋值给o2，那么o2的地址就会改变，现在o2的地址与o1的地址指向不同的键值对：
```
var o1 = {name:'xxx'}
var o2 = {name:'yyy'}

o2 = o1;
o2 = {name:'zzz'};
o1.name;
// "xxx"，因为把{name:'zzz'}赋值给o2时，实际上是在堆内存创建了另一个{name:'zzz'}的键值对，而o2的地址从原来的{name:'xxx'}指向了新的数据，因此原来的{name:'xxx'}没有被修改
```
同理，把另一个值赋予o2时，只是会更改原来o2在stack栈内存内储存的地址：
```
var o1 = {name:'xxx'}
var o2 = {name:'yyy'}

o2 = o1;
o2.name; // "xxx"

o2 = null;
o2.name; // 此时会报错，因为这是o2的值是null，并没有name这个属性
```

还有一个要注意的点：
```
var o1 = {name:'xxx'}
var o2 = {name:'yyy'}

o2 = o1;
o1.p = o1 = {name:'zzz'};

o1.p; // undefined，因为浏览器在读o1.p = o1 = {name:'zzz'}时，是从左往右先定下o1的地址，此时o1的地址还是指向{name:'xxx'}，所以新建的p属性是在原来o1的{name:'xxx'}上添加，现在即为
{name:'xxx';p:{name:'zzz'}}

o2.p; // {name:'zzz'}，在浏览器定下o1的地址后，把{name:'zzz'}赋值给o1，此时o1有一个新的地址，指向{name:'zzz'}；但o2此时指向的仍是旧的地址，旧的地址添加了p属性后，p指向的是o1的新地址，即{name:'zzz'}
```
