---
title: 初识CSS——布局小贴士
date: 2019-01-14 22:38:18
tags: CSS
---

刚开始学HTML和CSS，看着貌似为数不多的元素和属性，以为很简单，但在真正要实现某种理想的效果时，却让人脑袋疼。特别是在如何利用不同的属性的元素（内联元素和块级元素）参与CSS z字形的文档流的规则，做出一版好看的布局。本文给大家几个布局的小技巧：
#### 1. 左右布局
#### 2. 左中右布局
#### 3. 水平居中
#### 4. 垂直居中

---

## 左右布局
  在HTML里，块级元素（block-level element）是另起一行，并占据它父元素（或页面）整个宽度的，此为“块”状。
  ![块元素占据整个页面宽度](http://imglf5.nosdn0.126.net/img/RW5xeGhweHowWDdmYXY4dVdNZTFZSGovcEhIdDNOTnZrOGRQRjM4VlM1aE1BR0NYanNTOXdnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0 "块元素占据页面宽度")
  因此，假设有2个块级元素：
  **< div id="block1" > < /div >** 和 **< div id="block2" > < /div >** 
  若要使2个块级元素成左右布局，可以：
  ### 利用float属性
  HTML:
  ![HTML代码-利用float把2个div设置成左右结构](http://imglf6.nosdn0.126.net/img/RW5xeGhweHowWDdzRkVMOTQrUTczeWtVMnYrcE13Yng1dE1DYkRXdUVXUVNLbVNrMENlNERRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

  CSS:
  ![CSS代码-利用float把2个div设置成左右结构](http://imglf4.nosdn0.126.net/img/RW5xeGhweHowWDdzRkVMOTQrUTczeDNlR3d1TVlERERQZ2J6RG5FTjRENFlzNzVJODN5MjZnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)
  在写CSS的时候，在把第一个block设置成float:left之后，block1里面的p会自动增加margin，此时可以把block2的display设置成inline-block，再把宽度调整就可以显示左右布局：
  ![float: left的左右布局](http://imglf4.nosdn0.126.net/img/RW5xeGhweHowWDVrbGJ1Uk8zUFVDanBZSERlODVoTjR1TDIvbUJIdEx0NmNwdDZLZXk2M25RPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

  *注意*：在使用float的时候，需要与clearfix结合，因为float会使div脱离文档流，需要clearfix把后面正常参与文档流的内容后挪，不然会造成div中的内容与后面的内容视觉上重合。

## 左中右布局
  要实现左中右的布局，这里可以使用CSS里position的属性。
  假设有1个大的块级元素，3个小的块级元素：
  **< div id="biggest" > < /div >**
  **< div id="block1" > < /div >** 
  **< div id="block2" > < /div >** 
  **< div id="block3" > < /div >**
  此时
  ### 利用position: relative和 position: absolute
  HTML:
  ![HTML代码-利用position属性](http://imglf6.nosdn0.126.net/img/RW5xeGhweHowWDZPSFdURHo2cWdUMGV5UmtQdGV2eEJvUDZIMzZoWDlxQzkyUEY3UWFJZWNnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

  CSS:
  ![CSS代码-利用position属性](http://imglf4.nosdn0.126.net/img/RW5xeGhweHowWDZPSFdURHo2cWdUM3FsRk5BWFRDTDgyak12MlhQSGwyUDg1c0hyeldmZkJ3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)
  ![CSS代码续上-利用position属性](http://imglf5.nosdn0.126.net/img/RW5xeGhweHowWDZPSFdURHo2cWdUOFZrMVFUR0E0SEY3cFVTV0h5ejFISGhLVnVVdjJ6T2VRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

  此处利用每个block里面的width属性，可让3个block把整个div分割成3块。
  成果：
  ![position的左中右布局](http://imglf5.nosdn0.126.net/img/RW5xeGhweHowWDZPSFdURHo2cWdUNVVrTHpKTVR2Zjk5ZXQ2MEh0QTlmamR2NUJ6TVg0ejl3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

## 水平居中
  ### 内联元素水平居中
  内联元素的水平居中可只直接利用text-align的属性,
  在CSS里使该内联元素：
  >   text-align: center;

  ### 块级元素水平居中
  当一个有固定宽度（通常小于浏览器页面宽度）的块级元素需水平居中时，利用margin的属性使块级元素的左右margin设置为auto：
  >   margin: 0 auto;

## 垂直居中
### 内联元素垂直居中
#### 单行垂直居中
假设有1个div，里面包含文本，要使div里的文本在div内垂直居中，可以在元素的上下添加相同像素的padding，也可以把div里的line-height和height设置成一样。
HTML:
![HTML代码——内联单行垂直居中](http://imglf6.nosdn0.126.net/img/RW5xeGhweHowWDcwUE9VUStPdUxvOGVscVpNL0ZsN2d3bU9hY3VjYTlXSGVmSmRBSThHTXdnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

CSS:
![CSS代码——内联单行垂直居中](http://imglf4.nosdn0.126.net/img/RW5xeGhweHowWDcwUE9VUStPdUxvL3pCbFJVTzZUeXU2WmdCeXpMRGsxV1pwNzdLZlVSYWR3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

成果：
![内联单行垂直居中](http://imglf6.nosdn0.126.net/img/RW5xeGhweHowWDcwUE9VUStPdUxvNlpXcDBDRnN2bmZLbDhQakNBNnBuMnpFc3NmZUp1NGNBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

### 块级元素垂直居中
假如已知块级元素的高度height，要使1个id为block1的块级元素在另一个id为block0的块级元素里垂直居中，同样可以使用position的属性：
HTML:
![HTML——块级元素垂直居中](http://imglf4.nosdn0.126.net/img/RW5xeGhweHowWDRuclc0K0NqM29KeGM4eUhNdUR3K3l1TEloVXpVc0ZDVGtiSVFZRlhPV0NRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

CSS:
![CSS——块级元素垂直居中](http://imglf3.nosdn0.126.net/img/RW5xeGhweHowWDRuclc0K0NqM29KNFVVK045SExZYzdEdHA5d29VRzZickIrakJwTXN6aG5RPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

成果：
![块级元素垂直居中](http://imglf3.nosdn0.126.net/img/RW5xeGhweHowWDRuclc0K0NqM29KeFlnS01WR1l6UkRqemVVQ3FTZ1VnUXFocFFNaGFLeWNBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)