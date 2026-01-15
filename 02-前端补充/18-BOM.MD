# BOM

浏览器对象模型（Browser Object Model，简称 BOM）是 JavaScript 的组成部分之一，BOM 赋予了JavaScript程序与浏览器交互的能力。

window对象是BOM 的核心，用来表示当前浏览器窗口，其中提供了一系列用来操作或访问浏览器的方法和属性。另外，JavaScript中的所有全局对象、函数以及变量也都属于window对象。

- alert()：在浏览器窗口中弹出一个提示框，提示框中有一个确认按钮

- open()：打开一个新的浏览器窗口

- scrollTo()：将窗口的内容滚动到指定的坐标

- setInterval()：周期性定时器每隔一段时间就执行一次代码

  ```javascript
  // 开启定时器:
  let timerID = setInterval(function, interval);
  /*
  参数 :
       function : 需要执行的代码,可以传入函数名;或匿名函数
       interval : 时间间隔,默认以毫秒为单位 1s = 1000ms
  返回值 : 返回定时器的ID,用于关闭定时器
  */
  ```

  ```javascript
  // 关闭指定id对应的定时器
  clearInterval(timerID);
  ```

- setTimeout()：一次性定时器等待多久之后执行一次代码

  ```javascript
  // 开启超时调用:
  let timerId = setTimeout(function,timeout);
  // 关闭超时调用:
  clearTimeout(timerId);
  ```

window的大部分属性又是对象类型：

- history：保存当前窗口所访问过的URL

  ```javascript
  back() 对应浏览器窗口的后退按钮，访问前一个记录
  forward() 对应前进按钮，访问记录中的下一个URL
  ```

  location：保存当前窗口的地址栏信息(URL) 

  - 属性：href 设置或读取当前窗口的地址栏信息


- navigator：获取浏览器相关的信息。