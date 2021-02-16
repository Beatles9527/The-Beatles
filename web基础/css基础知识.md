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





# 美化网页

例：

span标签：重点要突出的字，使用span套起来

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        #title1{
            font-size: 50px;
            color: red;
        }
    </style>

</head>
<body>

你好,<span id="title1">李焕英</span>

</body>
</html>
```



## 字体样式

```html
<!--    font-family: 字体
        font-size:   字体大小
        font-weight: 字体粗细

-->

    <style>
        body{
            font-family: "Arial Black",华文行楷;
            color: red;
        }
        h1{
            font-size: 50px;
        }
        .p1{
            font-weight: bold;
        }
    </style>
```



## 文本样式

1. 颜色	color	rgb	rgba
2. **文本对齐方式   text-align = center**
3. **首行缩进  text-indent：2em**
4. **行高  line-height**  单行文字上下居中！line-height = height
5. 装饰  text-decoration
6. 文本图片水平对齐  vertical-align：middle；

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--    颜色:
        单词
        RGB  0~F
        RGBA  A: 0~1(透明度)

       text-align:排版，居中
       text-indent: 2em;    段落首行缩进
       /*行高，和 块的高度一致，就可以上下居中*/
       height: 100px;
       line-height: 100px;
-->

    <style>
        h1{
            /*color: rgb(0,255,255);*/
            color: rgba(0,255,255,0.9);
            text-align: center;
        }
        .p1{
            text-indent: 2em;
        }
        .p2{
            background: blue;
            /*行高，和 块的高度一致，就可以上下居中*/
            height: 100px;
            line-height: 100px;
            font-size: 10px;
        }
        /*下划线*/
        .p3{
            text-decoration: underline;
        }
        /*中划线*/
        .p4{
            text-decoration: line-through;
        }
        /*上划线*/
        .p5{
            text-decoration: overline;
        }
        /*超链接去下划线*/
        a{
            text-decoration: none;
        }
        /*水平对齐~ 参照物，  a，b*/
        img,span{
            vertical-align: middle;
        }
    </style>

</head>
<body>

<a href="https://google.com/">谷歌搜索</a>

<h1>火影忍者剧情介绍</h1>

<p class="p1">
    一只名为九尾妖狐的强大魔兽袭击了忍者五大国之一的火之国木叶忍者村。为了解决这场灾难，木叶忍者村的首领“第四代火影”将九尾妖狐封印在刚出生的儿子漩涡鸣人体内，让鸣人成为九尾妖狐的人柱力；鸣人的父亲在战斗中殉职身亡，而原本已经退休的第三代火影则再次成为木叶忍者村的领导者。鸣人从小就被木叶忍者村的村民们视为破坏村子夺走无数人命的九尾妖狐的化身而无视并排挤他。由于第三代火影禁止任何人提及这起事件，鸣人对于九尾妖狐一无所知，因此鸣人为了得到大家的认同而以成为历代最强的火影为目标。直到12年后，背叛村子的忍者水木向鸣人透露了真相。随后鸣人在战斗中击败了水木，得到他的老师伊鲁卡的认同。
</p>

<p class="p3">
    不久之后，鸣人终于成为一名忍者，与他视为竞争对手的宇智波佐助以及暗恋的春野樱一起组成了由上忍旗木卡卡西带领的第七班。佐助是宇智波一族的幸存者，在小时候，他的哥哥宇智波鼬将除了自己以外的族人全部杀死，自从那时候起佐助就以杀死哥哥为目标；小樱是喜欢佐助的少女；卡卡西是木叶忍者村第一的高手，人称“写轮眼的卡卡西”。鸣人在第七班开始忍者的生涯并执行各式各样的任务。
</p>

<p class="p4">
    第七班在经过数次任务，包括在波之国进行的重大任务之后，卡卡西认同第七班能参加可以晋升到中忍级别并执行困难任务的中忍考试。在考试期间，被通缉的逃亡忍者大蛇丸入侵了木叶忍者村并杀死了第三代火影。传说的三忍之一的自来也拒绝担任“第五代火影”的职位，并与鸣人一同寻找了他所推荐适合担任“第五代火影”的纲手。中间与寻求钢手治疗自己的大蛇丸发生冲突并得知大蛇丸之所以想得到佐助是因为佐助所拥有的写轮眼的力量。
</p>

<p class="p5">
    在寻找纲手的过程中，遇到目的是九尾妖狐的“晓”的成员宇智波鼬与干柿鬼鲛，而鼬是屠杀宇智波一族的凶手，佐助遇到鼬想要为一族复仇不成反被打成重伤。对此感到无力的佐助离开村子而前去找大蛇丸寻求能杀死鼬的力量。在佐助离开村子时小樱前去处阻止却被打晕，钢手从小樱得知事情经过后派出包含鸣人在内的五名忍者找回佐助，但是鸣人最后还是无法夺回佐助。从此第七班名存实亡，鸣人与小樱只能被迫与其他班合作完成任务。但鸣人与小樱还是不放弃佐助。为了能将佐助带回木叶忍者村，鸣人成为自来也的徒弟，而小樱则成为纲手的徒弟。
</p>

<p class="p2">  在经历一连串的任务后，自来也终于同意训练鸣人。最后鸣人与自来也一起离开木叶忍者村，踏上修行之路。</p>

<p>
    Immanuel Kant (UK: /kænt/,[18][19] US: /kɑːnt/;[20][21] German: [ɪˈmaːnu̯eːl ˈkant, -nu̯ɛl -];[22][23] 22 April 1724 – 12 February 1804) was a German philosopher and one of the central Enlightenment thinkers.[24][25] Kant's comprehensive and systematic works in epistemology, metaphysics, ethics, and aesthetics have made him one of the most influential figures in modern Western philosophy.[24][26]

    In his doctrine of transcendental idealism, Kant argued that space and time are mere "forms of intuition" which structure all experience, and therefore that while "things-in-themselves" exist and contribute to experience, they are nonetheless distinct from the objects of experience. From this it follows that the objects of experience are mere "appearances", and that the nature of things as they are in themselves is consequently unknowable to us.[27][28] In an attempt to counter the skepticism he found in the writings of philosopher David Hume, he wrote the Critique of Pure Reason (1781/1787),[29] one of his most well-known works. In it, he developed his theory of experience to answer the question of whether synthetic a priori knowledge is possible, which would in turn make it possible to determine the limits of metaphysical inquiry. Kant drew a parallel to the Copernican revolution in his proposal that the objects of the senses must conform to our spatial and temporal forms of intuition, and that we can consequently have a priori cognition of the objects of the senses.[b]
</p>

<p>
    <img src="images/123.jpg" alt="">
    <span>网络图片</span>
</p>

</body>
</html>
```



## 阴影

``` css
/*text-shadow: 阴影颜色 水平偏移 垂直偏移 阴影半径*/
        #price{
            text-shadow: #008000 10px 10px 2px;
        }
```



## 超链接伪类

**重要：a，a:hover**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /*默认颜色*/
        a{
            text-decoration: none;
            color: #ff0000;
        }
        /*鼠标悬浮的颜色*/
        a:hover{
            color: chartreuse;
        }
        /*鼠标按住未释放的状态*/
        a:active{
            color: blue;
        }
        /*text-shadow: 阴影颜色 水平偏移 垂直偏移 阴影半径*/
        #price{
            text-shadow: #008000 10px 10px 2px;
        }
    </style>

</head>
<body>

<a href="#">
    <img src="images/123.jpg" alt="">
</a>
<p>
    <a href="#">谨防网络诈骗</a>
</p>
<p>
    <a href="">公安部宣</a>
</p>
<p id="price">
    ￥99
</p>

</body>
</html>
```



## 列表

```css
/*ul li*/
/*
list-style:
        none:去掉圆点
        circle:空心圆
        decimal:数字
        square:正方形
 */

/*ul{*/
/*    background: #a0a0a0;*/
/*}*/

ul li{
    height: 30px;
    list-style: none;
    text-indent: 1em;
}
```

代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>列表样式</title>

    <link href="css/style.css" rel="stylesheet" type="text/css"/>

</head>
<body>

<div id="nav">
    <h2 class="title">全部商品分类</h2>
    <ul>
        <li><a href="#">图书</a>&nbsp;&nbsp;<a href="#">音像</a>&nbsp;&nbsp;<a href="#">数字商品</a></li>
        <li><a href="#">家用电器</a>&nbsp;&nbsp;<a href="#">手机</a>&nbsp;&nbsp;<a href="#">数码</a></li>
        <li><a href="#">电脑</a>&nbsp;&nbsp;<a href="#">办公</a></li>
        <li><a href="#">家居</a>&nbsp;&nbsp;<a href="#">家装</a>&nbsp;&nbsp;<a href="#">厨具</a></li>
        <li><a href="#">服饰鞋帽</a>&nbsp;&nbsp;<a href="#">个护彩妆</a></li>
        <li><a href="#">礼品箱包</a>&nbsp;&nbsp;<a href="#">钟表</a>&nbsp;&nbsp;<a href="#">珠宝</a></li>
        <li><a href="#">食品饮料</a>&nbsp;&nbsp;<a href="#">保健食品</a></li>
        <li><a href="#">彩票</a>&nbsp;&nbsp;<a href="#">旅行</a>&nbsp;&nbsp;<a href="#">充值</a>&nbsp;&nbsp;<a href="#">票务</a></li>
    </ul>
</div>

</body>
</html>
```

```css

#nav{
    width: 300px;
    background: #a0a0a0;
}

.title{
    font-size: 18px;
    font-weight: bold;
    text-indent: 1em;
    line-height: 35px;
    background: red;
}
/*ul li*/
/*
list-style:
        none:去掉圆点
        circle:空心圆
        decimal:数字
        square:正方形
 */

/*ul{*/
/*    background: #a0a0a0;*/
/*}*/

ul li{
    height: 30px;
    list-style: none;
    text-indent: 1em;
}

a{
    text-decoration: none;
    font-size: 14px;
    color: #000;
}
a:hover{
    color: orange;
    text-decoration: underline;
}

```



## 背景

背景颜色

背景图片

```css
<style>
        div{
            width: 1000px;
            height: 700px;
            border: 1px solid red;
            /*默认全部平铺*/
            background-image: url("images/123.jpg");
        }
        /*水平平铺*/
        .div1{
            background-repeat: repeat-x;
        }
        /*垂直平铺*/
        .div2{
            background-repeat: repeat-y;
        }
        /*不平铺*/
        .div3{
            background-repeat: no-repeat;
        }
    </style>
```



案例:

```css

#nav{
    width: 300px;
    background: #a0a0a0;
}

.title{
    font-size: 18px;
    font-weight: bold;
    text-indent: 1em;
    line-height: 35px;
    /*颜色，图片，图片位置，平铺方式*/
    background: red url("../images/Jerry.png") 250px 0px no-repeat;
}

ul li{
    height: 30px;
    list-style: none;
    text-indent: 1em;
    background-image: url("../images/Tom.png");
    background-repeat: no-repeat;
    background-position: 210px 0px;
}

a{
    text-decoration: none;
    font-size: 14px;
    color: #000;
}
a:hover{
    color: orange;
    text-decoration: underline;
}

```



## 渐变

相关网站参考：

[Grabient](https://www.grabient.com/)

```css
<style>
        body{
            background-color: #08AEEA;
            background-image: linear-gradient(237deg, #08AEEA 0%, #2AF598 100%);
        }
</style>
```



# 盒子模型

![](G:/images/盒子模型.png)



margin：外边距

padding：内边距

border：边框

## 边框

1. 边框的粗细
2. 边框的样式
3. 边框的颜色

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /*body总有一个默认的外边距 margin:0,常见操作*/
        /*h1,ul,li,a,body{*/
        /*    margin: 0;*/
        /*    padding: 0;*/
        /*    text-decoration: none;*/
        /*}*/
        #box{
            width: 300px;
            /*border: ;粗细，样式，颜色*/
            border: 1px solid red;
        }

        h2{
            font-size: 16px;
            background-color: #f106a3;
            line-height: 30px;
        }

        form{
            background: #2AF598;
        }
        div:nth-of-type(1) input{
            border: 3px solid black;
        }
        div:nth-of-type(2) input{
            border: 3px dashed #2cf524;
        }
        div:nth-of-type(2) input{
            border: 2px dashed #f32c2c;
        }

    </style>

</head>
<body>

<div id="box">
    <h2>会员登录</h2>
    <form action="#">
        <div>
            <span>用户名:</span>
            <input type="text">
        </div>
        <div>
            <span>密码:</span>
            <input type="text">
        </div>
        <div>
            <span>邮箱:</span>
            <input type="text">
        </div>
    </form>
</div>

</body>
</html>
```



## 内外边距

```css
<style>
        #box{
            width: 300px;
            /*border: ;粗细，样式，颜色*/
            border: 1px solid red;
            margin: 0 auto;
        }

        /*顺时针旋转
            margin:0
            margin:0 1px
            margin:0 1px 2px 3px
        */
        h2{
            font-size: 16px;
            background-color: #f106a3;
            line-height: 30px;
            margin: 0;
        }

        form{
            background: #2AF598;
        }
        input{
            border: 1px solid black;
        }

</style>
```



## 盒子的计算方式

**margin + border + padding + 内容宽度**



## 圆角边框

4个角

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--    左上  右上  右下  左下 （顺时针）-->
<!--    圆圈: 圆角 = 半径 -->
    <style>
        div{
            width: 100px;
            height: 100px;
            border: 10px solid red;
            border-radius: 100px;
        }
        img{
            border-radius: 25px;
        }
    </style>

</head>
<body>

<div></div>
<img src="images/Jerry.png" alt="">

</body>
</html>
```



## 盒子阴影

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--    margin: 0 auto; 居中
            要求: 在块元素里，块元素有固定的宽度
-->
    <style>
        div{
            border-radius: 50px;
            box-shadow: 10px 10px 100px yellow;
        }
    </style>

</head>
<body>

<div style="width: 500px;display: block;text-align: center">
    <img src="images/Tom.png" alt="">
</div>

</body>
</html>
```



# 浮动

## 标准文档流

标准文档流包括：块级元素和行内元素。

**(1). 块级元素**

  特点： 一个元素单独一行，不与其他元素并行，可以设置其宽度和高度，如果不设置宽度，宽度默认为其父元素的100%。

![1031302-20170111134754056-1871521214](E:/ChromeDownload/images/1031302-20170111134754056-1871521214.png)

 

**(2). 行内元素**

  特点：与其他元素并行，不能设置其宽度和高度，默认宽度为内容的宽度。

![1031302-20170111134822681-466004446](E:/ChromeDownload/images/1031302-20170111134822681-466004446.png)

**行内元素可以被包含在块级元素中，反之不可。**



## display

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--    block  块元素
        inline 行内元素
        inline-block 是块元素，但是可以内联在一行！
        none
-->

    <style>
        div{
            width: 100px;
            height: 100px;
            border: 1px solid red;
            display: inline;
        }
        span{
            width: 100px;
            height: 100px;
            border: 1px solid red;
            display: inline-block;
        }
    </style>

</head>
<body>

<div>div元素</div>
<span>span元素</span>

</body>
</html>
```



## float

html代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <link href="css/style.css" rel="stylesheet" type="text/css">

</head>
<body>

<div id="father">
    <div class="float1"><img src="images/123.jpg" alt=""></div>
    <div class="float2"><img src="images/456.jpg" alt=""></div>
    <div class="float3"><img src="images/Jerry.png" alt=""></div>
    <div class="float4"><img src="images/Tom.png" alt=""></div>
    <div class="float5">浮动是一种非常重要的布局属性</div>
</div>

</body>
</html>
```



左右浮动

```css
div{
    margin: 10px;
    padding: 5px;
}
#father{
    border: 1px #000 solid;
}
.float1{
    border: 1px #63f507 dashed;
    display: inline-block;
    float: right;
}
.float2{
    border: 1px #0000ff dashed;
    display: inline-block;
    float: right;
}
.float3{
    border: 1px #f106a3 dashed;
    display: inline-block;
    float: right;
}
.float4{
    border: 1px #5a93ee dashed;
    line-height: 23px;
    display: inline-block;
    float: right;
}
.float5{
    border: 1px #ff0000 dashed;
    font-size: 12px;
    line-height: 23px;
    display: inline-block;
    float: right;
}

```



## 父级边框塌陷的问题

~~html代码接上个标题！~~

clear

```css
/*
clear : right; 右侧不允许有浮动元素
clear : left; 左侧不允许有浮动元素
clear : both; 两侧不允许有浮动元素
clear : none;
*/
.float5{
    border: 1px #ff0000 dashed;
    font-size: 12px;
    line-height: 23px;
    display: inline-block;
    float: right;
    clear: both;
}
```

解决方案：

1. 增加父级元素的高度~

   ```css
   #father{
       border: 1px #000 solid;
       height: 800px;
   }
   ```

2. 增加一个空的div标签，清除浮动

   ```css
   <div class="clear"></div>
   
   .clear{
       clear: both;
       margin: 0;
       padding: 0;
   }
   ```

3. overflow

   ```css
   在父级元素增加一个  overflow: hidden;
   #father{
       border: 1px #000 solid;
       overflow: hidden;
   }
   ```

4. **父类添加一个伪类：after**

   ```css
   #father:after{
       content: '';
       display: block;
       clear: both;
   }
   ```

**小结：**

1. 浮动元素后面增加空div：简单，代码中尽量避免空div
2. 设置父元素的高度：简单，元素假设有了固定高度，就会被限制
3. overflow：简单，下拉的一些场景避免使用
4. 父类添加一个伪类：after（推荐）：写法稍微复杂，但无副作用！！！



**对比：**

- display：方向不可以控制
- float：浮动起来的话会脱离标准文档流，所以要解决父级边框塌陷的问题~



# 定位

## 相对定位

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!-- 相对定位
       相对于自己原来的位置进行偏移-->
    <style>
        body{
            padding: 20px;
        }
        div{
            margin: 10px;
            padding: 5px;
            font-size: 12px;
            line-height: 25px;
        }
        #father{
            border: 1px solid red;
            padding: 0;
        }
        #first{
            background-color: #995e5e;
            border: 1px dashed yellow;
            position: relative;
            top: -20px;
            left: 20px;
        }
        #second{
            background-color: #6d7d9e;
            border: 1px dashed #4bff00;
        }
        #third{
            background-color: #926baa;
            border: 1px dashed #0037ff;
            position: relative;
            bottom: -10px;
            right: 20px;
        }
    </style>

</head>
<body>

<div id="father">
    <div id="first">第一个盒子</div>
    <div id="second">第二个盒子</div>
    <div id="third">第三个盒子</div>
</div>

</body>
</html>
```

**相对定位:position: relative;**

相对于原来的位置，进行指定的偏移，相对定位的话，它仍在标准文档流中，原来的位置会被保留

```css
top: -20px;
left: 20px;
bottom: -10px;
right: 20px;
```

**案例练习：**

- 使用<div>和超链接<a> 布局页面
- 每个超链接宽度和高度都是100px，背景颜色是粉色，鼠标指针移上去时变为蓝色
- 使用相对定位改变每个超链接的位置

<img src="G:/images/相对定位练习.png" style="zoom:33%;" />

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        #box{
            width: 300px;
            height: 300px;
            border: 2px solid red;
            padding: 10px;
        }
        a{
            width: 100px;
            height: 100px;
            background-color: pink;
            text-decoration: none;
            line-height: 100px;
            text-align: center;
            color: white;
            display: block;
        }
        a:hover{
            background-color: blue;
        }
        .a2,.a4{
            position: relative;
            left: 200px;
            top: -100px;
        }
        .a5{
            position: relative;
            left: 100px;
            top: -300px;
        }
    </style>

</head>
<body>

<div id="box">
        <a class="a1" href="https://www.google.com/">链接1</a>

        <a class="a2" href="https://www.google.com/">链接2</a>

        <a class="a3" href="https://www.google.com/">链接3</a>

        <a class="a4" href="https://www.google.com/">链接4</a>

        <a class="a5" href="https://www.google.com/">链接5</a>
</div>

</body>
</html>
```



## 绝对定位

定位：基于xxx定位，上下左右~

1、没有父级元素定位的前提下，相对于浏览器定位

2、假设父级元素存在定位，我们通常会在相对于父级元素进行偏移

3、在父级元素范围内移动

相对于父级或浏览器的位置，进行指定的偏移，绝对定位的话，它不在标准流文档中，原来的位置不会被保留

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        body{
            padding: 20px;
        }
        div{
            margin: 10px;
            padding: 5px;
            font-size: 12px;
            line-height: 25px;
        }
        #father{
            border: 1px solid red;
            padding: 0;
            position: relative;
        }
        #first{
            background-color: #995e5e;
            border: 1px dashed yellow;
        }
        #second{
            background-color: #6d7d9e;
            border: 1px dashed #4bff00;
            position: absolute;
            left: 100px;
        }
        #third{
            background-color: #926baa;
            border: 1px dashed #0037ff;
        }
    </style>

</head>
<body>

<div id="father">
    <div id="first">第一个盒子</div>
    <div id="second">第二个盒子</div>
    <div id="third">第三个盒子</div>
</div>

</body>
</html>
```



## 固定定位 fixed

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        body{
           height: 1000px;
        }
        div:nth-of-type(1){ /* 绝对定位: 相对于浏览器 */
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
            right: 0;
            bottom: 0;
        }
        div:nth-of-type(2){ /* fixed,固定定位 */
            width: 50px;
            height: 50px;
            background-color: yellow;
            position: fixed;
            right: 0;
            bottom: 0;
        }
    </style>

</head>
<body>

<div>div1</div>
<div>div2</div>

</body>
</html>
```



## z-index

图层概率

z-index: 默认是0，最高无限~（一般999）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <link rel="stylesheet" href="css/style.css">

</head>
<body>

<div id="content">
    <ul>
        <li><img src="images/Tom.png"></li>
        <li class="tipText">猫和老鼠</li>
        <li class="tipBg"></li>
        <li>时间: 2021-02-16</li>
        <li>地点: China</li>
    </ul>
</div>

</body>
</html>
```

```css
#content{
    width: 236px;
    padding: 0px;
    margin: 0px;
    overflow: hidden;
    font-size: 12px;
    line-height: 25px;
    border: 1px #000 solid;
}
ul,li{
    padding: 0px;
    margin: 0px;
    list-style: none;
}
/*父级元素相对定位*/
#content ul{
    position: relative;
}
.tipText,.tipBg{
    position: absolute;
    width: 236px;
    height: 25px;
    top: 155px;
}
.tipText{
    color: yellow;
    /*z-index: 1;*/
}
.tipBg{
    background-color: #000;
    opacity: 0.5;/* 背景透明度 */
    /*filter: alpha(opacity=50); !* 存在版本兼容问题 *!*/
}

```

**透明度：opacity: 0.5;/* 背景透明度 */**

