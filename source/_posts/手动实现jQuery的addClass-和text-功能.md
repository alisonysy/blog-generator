---
title: 手动实现jQuery的addClass()和text()功能
date: 2019-01-26 22:14:41
tags: JavaScript jQuery
---
很多时候，通过DOM操作HTML会很麻烦，特别是像遇到返回回车Text的nodeList。此时，我们可以用一个函数包装一段需要经常执行的代码，并通过简单易记的名字每次调用同一个函数。jQuery的出现，避免了无谓的重复，以下是初学jQuery时，用于理解其作用的题目：
> 补全下面???部分的代码：
> window.jQuery = ???
> window.$ = jQuery

> var $div = $('div')
> $div.addClass('red') // 可将所有 div 的 class 添加一个 red
> $div.setText('hi') // 可将所有 div 的 textContent 变为 hi

```
window.jQuery = function (nodeOrSelector) {
    let nodes = {}
    if (typeof nodeOrSelect === 'String') { //先判断提供的参数是一个节点，还是CSS的选择器
        let temp = document.querySelectorAll(nodeOrSelector); //若是选择器，需要调用querySelectorAll获取所有节点，此处返回的是一个伪数组
        for (let i=0; i<temp.length; i++){
            nodes[i] = temp[i]
            }
        nodes.length = temp.length;
    }else if (nodeOrSelector instanceof node){ 
        nodes = { //此处为一致性，需要把nodes包装为一个伪数组
            0: nodeOrSelector,
            length: 1
        }
    }
    nodes.addClass = function(class){
        class.forEach( (value) => { //接收的参数是一个数组，用forEach历遍数组中需要添加的class
            for (let i=0; i<nodes.length; i++){
                nodes[i].classList.add(value); //用classList为nodes里每一个节点加上class
            }
        })
    }
    nodes.setText= function (textValue){
        for (let i=0;i<nodes.length; i++){
            nodes[i].textContent = textValue; //用textContent方法为节点添加文本
        }
        return textValue;
    }
    return nodes
}
window.$ = jQuery //此处用$符号代替jQuery，此后用$表示jQuery的调用
```
