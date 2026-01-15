# JavaScript对象

JavaScript中`object`类型包含的数据有很多，数组、普通对象、DOM节点、内置对象等等都属于`obejct`类型。

## 1. JavaScript创建对象

JavaScript中使用花括号`{ }`来创建对象，`{ }`中用来定义对象中的属性。属性是一个个`键:值`对的组合，其中键（属性名称）始终是字符串类型的，而值（属性值）则可以是任意类型，例如字符串、数组、函数或其它对象等。不同的属性之间使用逗号进行分隔。

```javascript
let person = {
    name: "吴彦祖",
    age: 28,
    gender: "Male",
    displayName: function() {
        document.write(this.name);
    }
};
```

> 在定义对象时，属性名称虽然是字符串类型，但通常不需要使用引号来定义
>
> 函数的this指向,指向调用函数的对象

要访问或获取属性的值，您可以使用`对象名.属性名`或者`对象名["属性名"]`的形式

```javascript
console.log(person.name)
console.log(person["age"])
```

使用`对象名.属性名`或者`对象名["属性名"]`的形式除了可以获取对象的属性值外，也可以用来设置或修改对象的属性值

```javascript
person.phone = "150*******8";
person.age = 20;
person["name"] = "湖南吴彦祖";
```

使用delete语句来删除对象中的属性

```javascript
delete person.gender;
delete person["phone"];
```

for-in循环是一种特殊循环，可用于循环对象或数组

```javascript
// 将对象内的所有键值对循环输出, 此时可以使用for-in
for (let key in o) {
  let text = `当前属性名：${key}, 值：${o[key]}`
}
```



## 2. 内置对象

内置对象是JavaScript预先提供的一些特殊对象，能实现不同的功能

### 2.1 Array（数组）对象

数组是值的有序集合，数组中的每个值称为一个元素，每个元素在数组中都有一个数字位置，称为下标，下标从0开始，依次递增。

```javascript
let arr = [10, 50, true];
```

- 数组用于存储若干数据,自动为每位数据分配下标,从0开始
- 数组中的元素不限数据类型,长度可以动态调整
- 动态操作数组元素 ：根据元素下标读取或修改数组元素，arr[index]

**属性和方法**

- length：获取数组长度

- push(data)：在数组的末尾添加一个或多个元素,多个元素之间使用逗号隔开，返回添加之后的数组长度。

- pop()：移除末尾元素，返回被移除的元素。

- shift()：移除数组的第一个元素，返回被移除的元素。

- unshift(data)：在数组的头部添加一个或多个元素，返回添加之后的数组长度。

- splice(index,num)：从数组中添加/删除项目，返回被删除的项目。

- slice(startNum,endNum) 截取数组：startNum 参数为起始位置(包含), endNum 参数结束位置(不包含)。

- toString()：将数组转换成字符串类型，返回字符串结果。

- join(param)：将数组转换成字符串,可以指定元素之间的连接符,如果参数省略,默认按照逗号连接，返回字符串。

- reverse()：反转数组,倒序重排，返回重排的数组,注意该方法直接修改原数组的结构

- sort()：对数组中元素排序,默认按照Unicode编码升序排列，返回重排后的数组,直接修改原有数组

    参数 : 可选,自定义排序算法

    ```javascript
    // 自定义升序
    function sortASC(a,b){
        return a-b;
    }
    ```

    > 作用：作为参数传递到sort()中,会自动传入两个元素进行比较,如果a-b>0,交换元素的值,自定义升序排列

    ```javascript
    // 自定义降序
    function sortDESC(a,b){
        return b-a;
    }
    // 如果返回值>0,交换元素的值,b-a表示降序排列
    ```

### 2.2 String（字符串）对象

- 转换字母大小写：
    - toUpperCase() 转大写字母
    - toLowerCase() 转小写字母
    - 返回转换后的字符串,不影响原始字符串
- 获取字符或字符编码
    - charAt(index)： 获取指定下标的字符
    - charCodeAt(index)  获取指定下标的字符编码
    - 参数为指定的下标,可以省略,默认为0
- indexOf(str,fromIndex)：获取指定字符的下标,从前向后查询,找到即返回
    - str 表示要查找的字符串,必填
    - fromIndex 表示起始下标,默认为0
    - 返回指定字符的下标,查找失败返回-1
- 截取字符串
    - substring(startIndex,endIndex)：根据指定的下标范围截取字符串,startIndex ~ endIndex-1，startIndex：表示起始下标 ，endIndex：表示结束下标,可以省略,省略表示截止末尾
    - substr(startIndex,len)：从指定索引位置截取指定长度的字符串
- split(param)：将字符串按照指定的字符进行分割,以数组形式返回分割结果。参数 : 指定分隔符,必须是字符串中存在的字符,如果字符串中不存在,分割失败,仍然返回数组
- match(regExp/subStr)：查找字符串中满足正则格式或满足指定字符串的内容。返回 : 数组,存放查找结果
- replace(regExp/subStr,newStr)：根据正则表达式或字符串查找相关内容并进行替换，替换后的字符串,不影响原始字符串。



### 2.3 Math对象

Math对象主要提供一些列数学运算的方法

属性：圆周率 :  Math.PI

我们主要用的就是他里面的随机数方法

- Math.random() 随机生成0到1之间的数 包括0不包括1
- Math.ceil() 向上取整(天花板值) 遇到小数向上取整
- Math.floor() 向下取整(地板值) 遇到小数向下取整
- Math.round() 四舍五入



### 2.4 日期对象

**创建日期对象**

```javascript
let date1 = new Date("2022/11/11");
let date2 = new Date("2011/11/11 11:11:11");
```

**日期对象方法**

1. getTime() 返回一个毫秒值 到时间零点的距离
2. getFullYear() 返回年
3. getMonth() 返回月 注意:得到的月份是从0开始 要返回当前月需要加1
4. getDate() 返回日期
5. getHours() 返回小时
6. getMinutes() 返回分钟
7. getSeconds() 返回秒
8. getDay() 返回星期