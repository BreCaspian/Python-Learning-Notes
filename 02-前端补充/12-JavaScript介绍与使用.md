# JavaScript介绍与使用

## 1. JavaScript介绍

简称JS，是一种浏览器解释型语言,嵌套在HTML文件中交给浏览器解释执行。主要用来实现网页的动态效果，用户交互及前后端的数据传输等。

JS组成

- 核心语法-ECMAScript：规范了JS的基本语法
- 文档对象模型-DOM：Document Object Model ，提供了一系列操作的文档的方法
- 浏览器对象模型-BOM：Browser Object Model，提供了一系列操作浏览器的方法



## 2. JavaScript书写位置

- **内部JavaScript：**直接写在html文件里，用script标签包住。

    > 注意 ：<script></script>标签可以书写在文档的任意位置，书写多次，一旦加载到script标签就会立即执行内部的JS代码

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>title</title>
    </head>
    <body>
      <!-- 内部JavaScript：通过script标签包裹JavaScript代码 -->
      <script>
        alert('hello world');
      </script>
    </body>
    </html>
    ```

- **外部JavaScript**：JavaScript代码写在以.js结尾的文件里通过script标签，引入到html页面中。

    - 如果 script 标签使用 src 属性引入了某 .js 文件，那么 标签的代码会被忽略

        ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8">
          <title>title</title>
        </head>
        <body>
          <!-- 
            外部JavaScript：通过 script 的 src 属性引入独立的 .js 文件 
            -->
          <script src="demo.js">
            // 此处的代码会被忽略掉！！！！
          	alert(666);  
          </script>
        </body>
    </html>
        ```
    
        
    
    