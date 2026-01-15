# DOM

## 1. DOM介绍

DOM全称为 “Document Object Model”，文档对象模型，提供操作HTML文档的方法。（注：每个html文件在浏览器中都视为一篇文档,操作文档实际就是操作页面元素。）

当网页加载时，浏览器就会自动创建当前页面的文档对象模型（DOM）。在DOM中，文档的所有部分（例如元素、属性、文本等）都会被组织成一个树结构（类似于族谱），树中每一个分支的终点称为一个节点，每个节点都是一个对象。



## 2. 获取节点

DOM为我们提供了一个全局内置对象`document`，要操作HTML标签，我们可以调用`document`对象中的各种方法来获取页面中的标签（在js中我们可以称之为 **元素** 或者 **节点**）：

**根据CSS选择器来获取DOM元素**

```javascript
// 选择匹配的第一个元素
// 返回值：CSS选择器匹配的第一个元素。如果没有匹配到，则返回null。
document.querySelector('css选择器')
```

```javascript
// 选择匹配的多个元素
// 返回值：CSS选择器匹配的NodeList对象集合  是一个伪数组
document.querySelectorAll('css选择器')
```

**通过ID获取：**`document.getElementById()`

**通过class名获取：**`document.getElementsByClassName()`

**通过标签名获取：**`document.getElementsByTagName()`



## 3. 操作HTML内容

`节点.innerHTML` : 读取或设置元素文本内容,可识别标签语法
`节点.innerText` : 读取或设置元素文本内容,不能识别标签语法



## 4. 监听事件

事件是达到某个事先设定的条件，自动触发的动作。例如点击了某个按钮、在文本框中输入文本、按下键盘上的某个按键、移动鼠标等等。我们可以使用 JavaScript中的监听事件来检测事件是否发生并执行某些特定的程序。

**事件种类**

|    事件     |                 描述                 |
| :---------: | :----------------------------------: |
|   onclick   |       点击鼠标左键时触发此事件       |
| onmouseover | 当鼠标移动到某个元素上方时触发此事件 |
| onmouseout  |  当鼠标离开某个元素范围时触发此事件  |
|   onblur    |     当前元素失去焦点时触发此事件     |
|   onfocus   |    当某个元素获得焦点时触发此事件    |
|  onscroll   |   当滚动浏览器的滚动条时触发此事件   |

**代码书写步骤**

- 获取事件源：`document.getElementById(“box”);`
- 绑定事件： 事件源box.事件onclick = function(){ 事件驱动程序 };



## 5. 操作节点的标签属性

直接使用 `节点.属性` 的方式。eg：`console.log(节点.id);` `节点.title = "新的title"`。class名字不能 `.class` ，而是使用 `.className` 代替。



## 6. 操作样式

访问元素节点的style属性，获取样式对象；样式对象中包含CSS属性，使用点语法操作。

```js
p.style.color = "white";
p.style.width = "300px";
p.style.fontSize = "20px";
```

> 如果css属性名包含连接符，使用JS访问时，一律去掉连接符,改为驼峰， font-size -> fontSize

使用 `.className` 可以来操作标签的类名，但是需要新加一个类名，或者去掉某个类名时，使用`.className`较为麻烦。所以推荐使用.classList` 来操作类名。

添加：`节点.classList.add("类名")`

移除：`节点.classList.remove("类名")`

切换（有则删，无则加）：`节点.classList.toggle("类名")`



## 7. 创建、添加、删除节点

- 创建节点：createElement 创建一个元素节点；
- 添加节点：
  - appendChild 元素最后添加一个子节点；
  - insertBefore 在元素某个子节点之前添加新子节点，第一个参数为新节点，第二个参数为已存在的子节点。
- 替换节点：replaceChild 用新节点替换某个子节点，第一个参数为新节点，第二个参数为已存在的某个子节点。
- 删除节点：removeChild 删除元素的某个子节点。

