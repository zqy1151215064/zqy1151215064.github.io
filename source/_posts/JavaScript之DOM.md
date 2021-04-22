---
title: JavaScript之DOM
date: 2021-04-22 10:30:39
tags: 
type: javascript
---

# Document对象

`Document`接口表示任何在浏览器中载入的网页，并作为网页内容的入口，也就是[DOM 树](www.developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_W3C_DOM_Level_1_Core)。DOM树包含了像 `<body>`、 `<table>`这样的元素，以及大量其他元素。它向网页文档本身提供了全局操作功能，能解决如何获取页面的URL，如何在文档中创建一个新的元素这样的问题。



## 使用Document元数据

| 属性           | 说明                                                         | 返回值                |
| -------------- | ------------------------------------------------------------ | --------------------- |
| characterSet   | 只读属性，返回当前文档的字符编码，该字符编码是用于渲染此文档的字符集，可能与该页面指定的编码不同 | 字符串                |
| charset        | Document.characterSet的别名。请改用此属性                    | 字符串                |
| compatMode     | 表明当前文档的渲染模式是怪异模式/混杂模式还是标准模式        | 字符串                |
| cookie         | 获取并设置与当前文档相关联的cookie。可以把它当成一个 `getter and setter` | 字符串                |
| defaultView    | 返回当前 `document`对象所关联的 `window`对象，如果没有，会返回 `null` | Window对象            |
| dir            | 获取或设置文档的文字方向（rtl或ltr）                         | 字符串                |
| domain         | 获取或设置当前文档的域名                                     | 字符串                |
| implementation | 返回当前文档中所包含的图片的列表                             | DOMImplementation对象 |
| lastModified   | 返回文档最后修改的时间                                       | 字符串                |
| location       | 返回当前文档的URI                                            | Location对象          |
| readyState     | 返回当前文档的加载状态。当该属性值发生变化时，会在 document 对象上触发 readystatechange 事件 | 字符串                |
| referrer       | 返回来源页面的URI                                            | 字符串                |
| title          | 获取或设置当前的文档的标题                                   | 字符串                |

# Location对象

`Location`接口表示其链接到的对象的位置（URL）。所做的修改反映在与之相关的对象上。Document和Window接口都有这样一个链接的Location，分别通过 `Document.location`和 `Window.location`访问。

## 属性

`Location`接口不继承任何属性，但是实现了那些来自 URLUtils 的属性。

| 属性     | 说明                                                         | 返回值 |
| -------- | ------------------------------------------------------------ | ------ |
| href     | 包含整个URL的一个DOMString                                   | 字符串 |
| protocol | 包含URL对应协议的一个DOMString，最后有一个":"                | 字符串 |
| host     | 包含了域名的一个DOMString，可能在该串最后带有一个":"并跟上URL的端口号 | 字符串 |
| hostname | 包含了URL域名的一个DOMString                                 | 字符串 |
| port     | 包含端口号的一个DOMString                                    | 字符串 |
| pathname | 包含URL中路径部分的一个DOMString，开头有一个 `/`             | 字符串 |
| search   | 包含URL参数的一个DOMString，开头有一个 `?`                   | 字符串 |
| hash     | 包含块标识符的DOMString，开头有一个 `#`                      | 字符串 |
| username | 包含URL中域名前的用户名的一个DOMString                       | 字符串 |
| password | 包含URL域名前的密码的一个DOMString                           | 字符串 |
| origin   | 包含页面来源的域名的标准形式DOMString，只读属性              | 字符串 |

### 方法

`Location`没有继承任何方法，但实现了来自 URLUtils的方法。

| 方法       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| assign()   | 加载给定URL的内容资源到这个Location对象所关联的对象上        |
| reload()   | 重新加载来自当前URL的资源。他有一个特殊的可选参数，类型为Boolean，该参数为true时会导致该方法引发的刷新一定会从服务器上加载数据。如果是 `false`或没有制定这个参数，浏览器可能从缓存当中加载页面 |
| replace()  | 用给定的URL替换掉当前的资源。与 `assign()`方法不同的是用 `replace()`替换的新页面不会被保存在会话的历史History中，这意味着用户将不能用后退按钮转到该页面 |
| toString() | 返回一个DOMString，包含整个URL。它和读取URLUtils.href的效果相同。但是用它是不能够修改Location的值得 |

