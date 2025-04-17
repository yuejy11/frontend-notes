# JavaScript 基础 - 第1天

> 了解变量、数据类型、运算符等基础概念，能够实现数据类型的转换，结合四则运算体会如何编程。

* 体会现实世界的事物与计算机的关系
* 理解什么是数据并知道数据的分类
* 理解变量存储数据的“容器”
* 掌握常用运算符的使用，了解优先级关系
* 知道 JavaScript 数据类型隐式转换的特征

## 介绍

> 掌握 JavaScript 的引入方式，初步认识 JavaScript 的作用

### 引入方式

JavaScript 程序不能独立运行，它需要被嵌入 HTML 中，然后浏览器才能执行 JavaScript 代码。通过 `script` 标签将 JavaScript 代码引入到 HTML 中，有两种方式：

#### 内部方式

通过 `script` 标签包裹 JavaScript 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
  <!-- 内联形式：通过 script 标签包裹 JavaScript 代码 -->
  <script>
    alert('嗨，欢迎来传智播学习前端技术！')
  </script>
</body>
</html>
```

#### 外部方式

一般将 JavaScript 代码写在独立的以 .js 结尾的文件中，然后通过 `script` 标签的 `scr` 属性引入

```js
// demo.js
document.write('嗨，欢迎来传智播学习前端技术！')
```

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
  <!-- 外部形式：通过 script 的 src 属性引入独立的 .js 文件 -->
  <script src="demo.js"></script>
</body>
</html>
~~~

如果 script 标签使用 src 属性引入了某 .js 文件，那么标签的代码会被忽略！！！如下代码所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
  <!-- 外部形式：通过 script 的 src 属性引入独立的 .js 文件 -->
  <script src="demo.js">
    // 此处的代码会被忽略掉！！！！
  	alert(666);  
  </script>
</body>
</html>
```

### 注释和结束符

通过注释可以屏蔽代码被执行或者添加备注信息，JavaScript 支持两种行注释语法：

#### 单行注释

使用 `//` 注释单行代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 注释</title>
</head>
<body>
  
  <script>
    // 这种是单行注释的语法
    // 一次只能注释一行
    // 可以重复注释
    document.write('嗨，欢迎来传智播学习前端技术！');
  </script>
</body>
</html>
```

#### 多行注释

使用 `/* */` 注释多行代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 注释</title>
</head>
<body>
  
  <script>
    /* 这种的是多行注释的语法 */
    /*
    	更常见的多行注释是这种写法
    	在些可以任意换行
    	多少行都可以
      */
    document.write('嗨，欢迎来传智播学习前端技术！')
  </script>
</body>
</html>
```

**注：编辑器中单行注释的快捷键为 `ctrl + /`**



### 上角标和下角标

x^2^         y^3^

x~2~         y~3~

### 引用嵌套

> 引用嵌套
>
> > 引用嵌套
> >
> > > 引用嵌套

### 有序列表

1. 第一行内容
   1. 第1行
   2. 第2行
   3. 第3行
2. 第二行内容
3. 第三行内容

### 勾选框

- [ ] a
- [ ] b
- [ ] c


| 姓名 | 年龄 |      |
| ---- | ---- | ---- |
| 张三 |      |      |
| 李四 |      |      |
| 王五 |      |      |

### 字体

*斜体*

**粗体**

***斜粗体***

==高亮==

~~删除~~

<u>下划线</u>

### 脚注

想要购买的XXX请前往我们的官网[^1]

Here is some text with a footnote[^2].

[^1]: This is a small one!
[^2]: Helloworld and Hellopeople!

请大家多多三连[^3]支持

[^3]: 点赞、投币、转发

### 水平分割线

---



### 超链接

http://www.baidu.com

想了解更多知识请前往我们的[官网](https://itbaima.cn)

想了解更多知识请前往我们的[官网][def]

[def]: https://itbaima.cn

### 图片

> 可用 `<img> </img>` 配合 css 语言  控制图片大小

<img style="width: 600px; height:300px" src="https://oss.itbaima.cn/internal/markdown/2022/06/17/nzpG5CLfUg927Rr.jpg"></img>



![图片](https://oss.itbaima.cn/internal/markdown/2022/06/17/nzpG5CLfUg927Rr.jpg)



![图片][pic]

[pic]: https://oss.itbaima.cn/internal/markdown/2022/06/17/nzpG5CLfUg927Rr.jpg

> 若要将文档发送给其他人观看，要使用图床保存图片并进行插入

### 导出为PDF文件

+ 将文档用 vs code 打开

+ 在 vs code 中用浏览器进行预览

+ 在浏览器中导出PDF

  如，在微软浏览器中需要 右键 打印文件，在 打印 中导出PDF

























