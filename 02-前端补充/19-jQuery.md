# jQuery

## 1. jQuery介绍 

jQuery是JavaScript的工具库，对原生JavaScript中的DOM操作、事件处理、包括数据处理和Ajax技术等进行封装,提供更完善，更便捷的方法。



## 2. 工厂函数 - $()

"$()"函数用于获取元素节点，创建元素节点或将原生JavaScript对象转换为jquery对象,返回 jQuery 对象。jQuery 对象实际是一个类数组对象，包含了一系列jQuery 操作的方法。

原生JavaScript对象与jQuery对象的属性和方法不能混用。可以根据需要，互相转换 :

1. 原生JavaScript转换jQuery对象
   $(原生对象)，返回 jQuery 对象
2. jQuery对象转换原生JavaScript对象
   - 方法一 : 根据下标取元素,取出即为原生对象
     var div = $("div")[0];
   - 方法二 : 使用jQuery的get(index)取原生对象
     var div2 = $("div").get(0);

## 3. jQuery获取元素

jQuery通过选择器获取元素，$("选择器")

```javascript
标签选择器：$("div")
ID 选择器：$("#d1")
类选择器：$(".c1")
群组选择器：$("body,p,h1")
后代选择器： $("div .c1")
子代选择器： $("div>span")
相邻兄弟选择器： $("h1+p")  匹配选择器1后的第一个兄弟元素,同时要求兄弟元素满足选择器2
通用兄弟选择器： $("h1~h2") 匹配选择器1后所有满足选择器2的兄弟元素
```

过滤选择器，需要结合其他选择器使用。

```javascript
:first
  匹配第一个元素 例:$("p:first")
:last
  匹配最后一个元素 例:$("p:last")
:odd
  匹配奇数下标对应的元素
:even
  匹配偶数下标对应的元素
:eq(index)
  匹配指定下标的元素
:lt(index)
  匹配下标小于index的元素
:gt(index)
  匹配下标大于index的元素
:not(选择器)
  否定筛选,除()中选择器外,其他元素
```



## 4. 操作元素内容

```javascript
// 设置或读取标签内容,等价于原生innerHTML,可识别标签语法
html() 
// 设置或读取标签内容,等价于innerText,不能识别标签
text() 
// 设置或读取表单元素的值,等价于原生value属性
val()  
```



## 5. 操作标签属性

1. attr("attrName","value")
   设置或读取标签属性
2. prop("attrName","value")
   设置或读取标签属性
   注意 :在设置或读取元素属性时,attr()和prop()基本没有区别;但是在读取或设置表单元素(按钮)的选中状态时,必须用prop()方法,attr()不会监听按钮选中状态的改变,只看标签属性checked是否书写
3. removeAttr("attrName")
   移除指定属性



## 6. 操作标签样式

1. 针对类选择器,提供操作class属性值的方法

```javascript
// 添加指定的类名
addClass("className")	
// 移除指定的类型,如果参数省略,表示清空class属性值
removeClass("className")
// 如果当前元素存在指定类名,则移除;不存在则添加
toggleClass("className")
```

2. 操作行内样式

```javascript
// 设置行内样式
css("属性名","属性值")  
// 设置一组CSS样式
css(对象)			 
```



## 7. 元素的创建,添加,删除

1. 创建：使用$("标签语法")，返回创建好的元素

```javascript
// 创建元素
let div = $("<div></div>");	
// 设置内容和属性
div.html("动态创建").attr("id","d1").css("color","red"); 
let h1 = $("<h1 id='d1'>一级标题</h1>")
```

2. 作为子元素添加

```javascript
// 在$obj的末尾添加子元素newObj
$obj.append(newObj);
// 作为第一个子元素添加至$obj中
$obj.prepend(newObj);	
```

3. 作为兄弟元素添加

```javascript
// 在$obj的后面添加兄弟元素
$obj.after(newObj);	
// 在$obj的前面添加兄弟元素
$obj.before(newObj);	
```

4. 移除元素 

```javascript
// 移除$obj
$obj.remove();	
```



## 8. 动画效果

1. 显示和隐藏

   ```javascript
    show(speed,callback)/hide(speed,callback)
   ```

   - speed	  可选。规定元素从隐藏到完全可见的速度。默认为 "0"。
   - callback   可选。show 函数执行完之后，要执行的函数

2. 通过使用滑动下拉和上推效果，显示隐藏的被选元素（ **只针对块元素** ）

   ```javascript
    slideDown(speed,callback)/slideUp(speed,callback)
   ```

3. 通过使用淡隐淡现方式显示效果，显示隐藏的被选元素

   ```javascript
    fadeOut(speed,callback)/fadeIn(speed,callback)
   ```



## 9. 数据与对象遍历

1. $(selector).each() 方法规定为每个匹配元素规定运行的函数

   ```javascript
   $(selector).each(function(index,element){})
   ```

   必需。为每个匹配元素规定运行的函数。

   - *index* - 选择器的 index 位置
   - element - 当前的元素

2. $.each()函数是框架提供的一个工具类函数，通过它，你可以遍历对象、数组的属性值并进行处理

   ```javascript
   $.each(Object, function(index, data){});
   ```

   必需。为每个匹配元素规定运行的函数。

   - *index* - 选择器的 index 位置
   - data- 当前的数据



## 10. jQuery事件处理

文档加载完毕原生JavaScript 方法：window.onload
jQuery:

```javascript
$(function(){
  // 文档加载完毕后执行
})
```

区别：原生onload事件不能重复书写，会产生覆盖问题；jquery中对事件做了优化,可以重复书写ready方法,依次执行

事件绑定方式

```javascript
$("div").on("click",function(){});
$("div").click(function(){});  
```

