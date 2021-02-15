# HTML基础应用

## 基本标签

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>基本标签</title>
</head>
<body>

<!-- 标题标签 -->
<h1>一级标签</h1>
<h2>二级标签</h2>
<h3>三级标签</h3>

<!--段落标签-->

<p>白日依山尽</p>
<p>黄河入海流</p>
<p>欲穷千里目</p>
<p>更上一层楼</p>

<!--水平线标签-->
<hr>


<!--换行标签-->
白日依山尽<br/>
<br/>黄河入海流
欲穷千里目<br/>
更上一层楼<br/>

<!--粗体、斜体-->
<h1>字体样式标签</h1>

粗体:<strong>刘德华</strong><br>
斜体:<em>刘德华</em><br>

<strong><em>刘德华</em></strong><br>


<!--特殊符号-->

空格：
空&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;格
<br>
大于号：&gt;
<br>
小于号：&lt;
<br>
&copy;版权船长所有


</body>
</html>
```





## 图像标签、超链接

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>图像标签</title>
</head>
<body>

<a name="top">起点</a>

<!--src:图片地址，alt:图片名字，      ../  上一级目录 -->

<!--图片标签-->
<img src="../resources/自来也.jpg" alt="自来也" title="悬停文字(自来也)" width=300 height="300">

<!--链接标签-->
<!--a标签
href:必填，表示要跳转到哪个页面
target:表示窗口在哪里打开
    _blank  在新标签中打开
    _self   在自己的网页打开

-->
<a href="图像标签.html" title="_blank">点击我跳转到页面</a>
<a href="https://www.google.com/" target="_self">谷歌一下</a>

<br>

<a href="https://www.google.com/" title="_blank">
    <img src="../resources/自来也.jpg" alt="自来也" title="悬停文字(自来也)" width=300 height="300">
</a>

<p>白日依山尽</p>
<p>黄河入海流</p>
<p>欲穷千里目</p>
<p>更上一层楼</p>

<!--锚链接-->
<a href="#top">回到起点</a>

<a name="down">down</a>

<!--功能性链接-->
<!--邮件链接 : mailto-->
<a href="mailto:838890974@qq.com">船长邮箱</a>
<!--QQ链接-->
<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=&site=qq&menu=yes">
    <img border="0" src="http://wpa.qq.com/pa?p=2::52" alt="船长的QQ号" title="船长的QQ号"/></a>
<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=&site=qq&menu=yes">
    <img border="0" src="http://wpa.qq.com/pa?p=2::53" alt="船长的QQ号" title="船长的QQ号"/></a>

</body>
</html>
```



1. 块元素：无论内容多少，该元素独占一行（p、h1-h6）
2. 行内元素：内容撑开宽度，左右都是行内元素的可以排在一行（a、strong、em...)



## 列表标签

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>列表学习</title>
</head>
<body>

<!--有序列表-->
<ol>
    <li>Java</li>
    <li>Java</li>
    <li>Java</li>
    <li>Java</li>
    <li>Java</li>
</ol>
<hr/>

<!--无序列表-->
<ul>
    <li>C++</li>
    <li>C++</li>
    <li>C++</li>
    <li>C++</li>
    <li>C++</li>
</ul>


<!--自定义列表-->
<!--一般常见在网页底部-->
<dl>
    <dt>HTML</dt>

    <dd>html</dd>
    <dd>html</dd>
    <dd>html</dd>
    <dt>HTML</dt>

    <dd>html</dd>
    <dd>html</dd>
</dl>

</body>
</html>
```



## 表格标签



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格学习</title>
</head>
<body>

<!--表格table
行   tr
列   td
边框  border
-->

<table border="1px">
    <tr>
        <td>1-1</td>
        <td>1-2</td>
        <td>1-3</td>
        <td>1-4</td>
    </tr>
    <tr>
        <td>2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
    </tr>
    <tr>
        <td>3-1</td>
        <td>3-2</td>
    </tr>
    <tr>
<!--  colspan 跨列-->
        <td colspan="4">1-1</td>
    </tr>
    <tr>
<!--  rowspan 跨行-->
        <td rowspan="2">2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
    </tr>
    <tr>
        <td>3-1</td>
        <td>3-2</td>
    </tr>
</table>
</body>
</html>
```





## 视频、音频

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>媒体元素</title>
</head>
<body>

<!--音频和视频
src:    资源路径
controls:   控制条
autoplay:   自动播放
-->
<!--<video src="../resources/video/296049054-1-208.mp4" controls autoplay></video>-->

<audio src="../resources/audio/07 - Hey Jude.flac" controls></audio>
<br>
<audio src="../resources/audio/14 - Golden Slumbers.flac" controls></audio>
</body>
</html>
```





# 页面结构分析

| 元素名  | 描述                                               |
| ------- | -------------------------------------------------- |
| header  | 标题头部区域的内容（用于页面或页面中的一块区域）   |
| footer  | 标记脚部区域的内容（用于整个页面或页面的一块区域） |
| section | Web页面中的一块独立区域                            |
| article | 独立的文章内容                                     |
| aside   | 相关内容或应用（常用于侧边栏）                     |
| nav     | 导航类辅助内容                                     |



# 内嵌框架

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内嵌框架</title>
</head>
<body>

<!--iframe 内联框架
src:    地址
w-h:    宽度高度
name:   框架标识名
-->

<!--<iframe src="//player.bilibili.com/player.html?aid=886699788&bvid=BV1yK4y1n7y2&cid=296049054&page=1" -->
<!--        scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> -->
<!--</iframe>-->

<!--<iframe src="https://www.baidu.com/" frameborder="0" width="1000px" height="800px"></iframe>-->

<iframe src="" name="baidu" frameborder="0" width="800px" height="800px"></iframe>
<a href="https://www.baidu.com/" target="baidu">跳转百度一下</a>
</body>
</html>
```





# 表单

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录注册</title>
</head>
<body>

<h1>get注册</h1>

<!--表单form

action: 表单提交的位置，可以是网站，也可以是一个请求处理地址
method: post,get 提交方式
-->

<form action="index.html" method="get">
<!--    文本输入框: input type="text"
        value=""    默认初始值
        maxlength=""    最大字符数量
        size=""     文本框长度
        placeholder     默认提示
        required     非空判断
-->
    <p>名字:<input type="text" name="username" placeholder="请输入内容" required></p>
<!--    密码框: input type="password"-->
    <p>密码:<input type="password" name="pwd"></p>

<!--    单选框标签
        input type="radio"
        value:  单选框的值
        name:   表示组（下面name属性设置为一样，就是限定了只能单选一个性别）
-->
    <p>性别:
        <input type="radio" value="boy" name="sex"/>男
        <input type="radio" value="girl" name="sex"/>女
    </p>

<!--    多选框
        input type="checkbox"
        checked 默认选中
-->
    <p>爱好:
        <input type="checkbox" value="sleep" name="hobby">睡觉
        <input type="checkbox" value="code" name="hobby" checked>敲代码
        <input type="checkbox" value="chat" name="hobby">聊天
        <input type="checkbox" value="game" name="hobby">游戏
    </p>

<!--    按钮
        input type="button" 普通按钮
        input type="image"  图像按钮
        input type="submit" 提交按钮
        input type="reset"  重置按钮
-->
    <p>按钮:
        <input type="button" name="button" value="点击变长">
        <input type="image" src="../resources/自来也.jpg">
    </p>

    <p>
        <input type="submit">
        <input type="reset">
    </p>

<!--    下拉框，列表框
        selected    默认选中
-->
    <p>下拉框:
        <select name="列表名称">
            <option value="China" selected>中国</option>
            <option value="US">美国</option>
            <option value="Japan">日本</option>
        </select>
    </p>

<!--    文本域
        cols="50" rows="10"
-->
    <p>反馈:
        <textarea name="textarea" cols="50" rows="10">文本内容</textarea>
    </p>

<!--    文件域
        input type="file" name="files"
-->
    <p>
        <input type="file" name="files">
        <input type="button" value="上传" name="upload">
    </p>

<!--    邮箱验证-->
    <p>邮箱:
        <input type="email" name="email">
    </p>

<!--    正则表达式-->
    <p>自定义邮箱:
        <input type="text" name="DIYemail" pattern="\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*">
    </p>

    <!--    url验证-->
    <p>url:
        <input type="url" name="url">
    </p>

    <!--    数字验证-->
    <p>数字:
        <input type="number" name="number" max="100" min="0" step="1">
    </p>

    <!--    滑块-->
    <p>音量:
        <input type="range" name="voice" min="0" max="100" step="2">
    </p>

    <!--    搜索框-->
    <p>搜索:
        <input type="search" name="search">
    </p>

    <p>
<!--        增强鼠标可用性-->
        <label for="mark">点击我就可以锁定在输入框哦！</label>
        <input type="text" id="mark">
    </p>
</form>
<hr>
<h1>post注册</h1>
<form action="index.html" method="post">
    <!--    文本输入框: input type="text"
            readonly    只读
    -->
    <p>名字:<input type="text" name="username" value="admin" readonly></p>
    <!--    密码框: input type="password"
            hidden      隐藏
            value       默认值
    -->
    <p>密码:<input type="password" name="pwd" hidden value="123456"></p>
<!--            disable  禁用-->
    <p>
        <input type="submit" disabled>
        <input type="reset">
    </p>
</form>

</body>
</html>
```





