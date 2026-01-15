# Ajax

Ajax即"Asynchronous Javascript And XML"（异步 JavaScript 和 XML），  通过JS异步的向服务器发送请求并接收响应数据。

```javascript
// XMLHttpRequest简称为xhr，称为 "异步对象"，代替浏览器向服务器发送异步的请求并接收响应。
let xhr = new XMLHttpRequest()
```

```javascript
// 创建请求 xhr.open(method,url)
// method:请求方式，取值'GET' 或 'POST' 
// url:请求地址，字符串。
xhr.open('请求方式，取值"GET" 或 "POST"', '请求地址，字符串')
```

```javascript
// 通知xhr向服务器端发送请求xhr.send()
xhr.send()
```

```javascript
// 拿数据  xhr.response 
xhr.onload = function(){
    if(xhr.status === 200){
        let data = JSON.parse(xhr.response)
    }
}
```

**jQuery的ajax**

```javascript
$.ajax({
    method : "POST" //请求方式
    ,url : "/url" //请求地址
    ,data : {} //需要发送的数据
    ,dataType : "json" //对请求返回的数据预处理
    ,success : function(data){} //请求成功的回调函数
    ,error : function(err){} //请求失败的回调函数
});
```



## JSON

JSON全称"JavaScript Object Notation"，译为"JavaScript 对象简谱"或"JavaScript 对象表示法"，是一种轻量级的、基于文本的、开放的数据交换格式，通常用于在 Web 客户端（浏览器）与 Web 服务器端之间传递数据。