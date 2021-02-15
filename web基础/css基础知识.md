# CSS基础入门

## CSS快速入门

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <!--    规范，<style> 可以编写css代码，每一个声明最好用分号结尾
            语法:
                选择器{
                    声明1；
                    声明2；
                    声明3；
                }
    -->

    <!--    <style>-->
    <!--        h1{-->
    <!--            color: red;-->
    <!--        }-->
    <!--    </style>-->

    <!--    外部引用-->
    <link rel="stylesheet" href="css/style.css">
</head>
<body>

<h1>CSS练习</h1>

</body>
</html>
```

```css
h1{
    color: red;
}
```



## 导入方式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--    内部样式-->
    <style>
        h1{
            color: green;
        }
    </style>

<!--    外部样式-->
    <link rel="stylesheet" href="css/style.css">
    
    <!--    导入式-->
    <style>
        @import url("css/style.css");
    </style>

</head>
<body>

<!--优先级: 就近原则-->
<h1>CSS导入方式练习</h1>

<!--行内样式:在标签元素中，编写一个style属性，编写样式即可-->
<h2 style="color: black">CSS导入方式练习</h2>

</body>
</html>
```

```css
/*外部样式*/
h1{
    color: red;
}
```



**外部样式两种写法：**

- 链接式：

  html

```html
<!--    外部样式-->
    <link rel="stylesheet" href="css/style.css">
```

- 导入式：

  @import 是CSS 2.1 特有的！

```html
<!--    导入式-->
    <style>
        @import url("css/style.css");
    </style>
```



## 选择器

选择页面上的某一个元素或者某一类元素

### 基本选择器

1. **标签选择器**：选择一类标签 	标签{}

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
   
       <style>
           /*标签选择器，会选择页面上所有该标签的元素*/
           h1{
               color: #a13d30;
               background: #ff0000;
               border-radius: 24px;
           }
           p{
               font-size: 80px;
               color: #008000;
           }
       </style>
   
   </head>
   <body>
   
   <h1>刘德华</h1>
   <h1>张学友</h1>
   <p>张国荣</p>
   
   </body>
   </html>
   ```

2. **类 选择器 （class）**：选择所有class属性一致的标签，跨标签。  .class{}

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
   
       <style>
           /*类选择器的格式   .class的名称{}
                好处：可以多个标签归类，是同一个class，可以复用
           */
   
           .class1{
               color: red;
           }
           .class2{
               color: green;
           }
           .class3{
               color: #0000ff;
           }
       </style>
   
   </head>
   <body>
   
   <h1 class="class1">刘德华</h1>
   <h1 class="class2">张学友</h1>
   <p class="class3">张国荣</p>
   
   </body>
   </html>
   ```

   

3. **id选择器**：全局唯一！   #id{}

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
   
       <style>
           /*id选择器   : id必须保证全局唯一！
               #id名称{}
               优先级:
               不遵循就近原则，固定！！！
               id选择器 > class 选择器 > 标签选择器
           */
           #class1{
               color: red;
           }
           #class2{
               color: #0000ff;
           }
           .class01{
               color: chartreuse;
           }
           h1{
               color: aqua;
           }
       </style>
   
   </head>
   <body>
   
   <h1 class="class01" id="class1">刘德华</h1>
   <h1 id="class2">张学友</h1>
   <h1 class="class01">黄家驹</h1>
   <h1>周星驰</h1>
   <p>张国荣</p>
   
   </body>
   </html>
   ```

   *优先级：id>class>标签*

   ---

   

### 层次选择器

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /*p{*/
        /*    background: aqua;*/
        /*}*/

        /*后代选择器*/
        body p{
            background: red;
        }

        /*子选择器*/
        body>p{
            background: green;
        }

        /*相邻兄弟选择器: 只有一个，向下选择*/
        .active + p{
            background: blue;
        }

        /*通用兄弟选择器，当前选中元素的向下的所有兄弟元素*/
        .active1~p{
            background: yellow;
        }

    </style>

</head>
<body>

<p>p0</p>
<p class="active">p1</p>
<p>p2</p>
<p class="active1">p3</p>
<ul>
    <li>
        <p>p4</p>
    </li>
    <li>
        <p>p5</p>
    </li>
    <li>
        <p>p6</p>
    </li>
</ul>
<p>p7</p>
<p>p8</p>

</body>
</html>
```



1. 后代选择器：在某个元素的后面	（爷爷、爸爸、你自己）

   ```css
   /*后代选择器*/
           body p{
               background: red;
           }
   ```

2. 子选择器，（上面是三代人，这里是一代人）

   ```css
   /*子选择器*/
           body>p{
               background: green;
           }
   ```

3. 相邻兄弟选择器   相邻的下一个元素

   ```css
   /*相邻兄弟选择器: 只有一个，向下选择*/
           .active + p{
               background: blue;
           }
   ```

4. 通用选择器

   ```css
   /*通用兄弟选择器，当前选中元素的向下的所有兄弟元素*/
           .active1~p{
               background: yellow;
           }
   ```

   

### 结构伪类选择器

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /*选择ul的第一个元素，即:<li>li1</li>*/
        ul li:first-child{
            background: red;
        }
        /*选择ul的最后一个元素，即:<li>li3</li>*/
        ul li:last-child{
            background: green;
        }
        /*选择 p1 元素:定位到父元素，选择当前的第一个元素
            选择当前p元素的父级元素，选中父级元素的第一个，并且是当前元素才生效！
        */
        p:nth-child(1){
            background: blue;
        }
        /*选中父元素，下的p元素的第二个，类型*/
        p:nth-of-type(2){
            background: yellow;
        }

        a:hover{
            background: cyan;
        }

    </style>

</head>
<body>

<!--<hi>h1</hi>-->
<!--<a>1234567890</a>-->
<p>p1</p>
<p>p2</p>
<p>p3</p>
<ul>
    <li>li1</li>
    <li>li2</li>
    <li>li3</li>
<!--    <li>-->
<!--        <p>p4</p>-->
<!--    </li>-->
<!--    <li>-->
<!--        <p>p5</p>-->
<!--    </li>-->
<!--    <li>-->
<!--        <p>p6</p>-->
    </li>
</ul>
<p>p7</p>
<p>p8</p>

</body>
</html>
```



### 属性选择器（常用）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        .demo a{
            float: left;
            display: block;
            height: 50px;
            width: 50px;
            border-radius: 10px;
            background: chartreuse;
            text-align: center;
            color: gainsboro;
            text-decoration: none;
            margin-right: 5px;
            font: bold 20px/50px Arial;
        }

        /*属性名，    属性名 = 属性值（正则）
            = 绝对等于（完全匹配）
            *= 包含这个元素
            ^= 以这个开头
            $= 以这个结尾

        */
        /*存在id属性的元素   a[]{}*/
        /*a[id]{*/
        /*    background: yellow;*/
        /*}*/

        /*选中id=first的元素*/
        /*a[id=first]{*/
        /*    background: yellow;*/
        /*}*/

        /*class   中有links的元素*/
        /*a[class*="links"]{*/
        /*    background: cyan;*/
        /*}*/

        /*选中href中以http开头的元素*/
        /*a[href^=http]{*/
        /*    background: red;*/
        /*}*/

        /*选中href中以jpg结尾的元素*/
        a[href$=jpg]{
            background: red;
        }

    </style>

</head>
<body>

<p class="demo">
    <a href="https://www.baidu.com" class="links item first" id="first">1</a>
    <a href="" class="links item active" target="_blank" title="test">2</a>
    <a href="images/123.html" class="links item">3</a>
    <a href="images/123.png" class="links item">4</a>
    <a href="images/123.jpg" class="links item">5</a>
    <a href="abc" class="links item">6</a>
    <a href="/a.pdf" class="links item">7</a>
    <a href="/abc.pdf" class="links item">8</a>
    <a href="abc.doc" class="links item">9</a>
    <a href="a.doc" class="links item">10</a>
</p>

</body>
</html>
```





