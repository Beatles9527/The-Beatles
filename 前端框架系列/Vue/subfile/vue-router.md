# 什么是路由？

> 路由是一个网络工程里面的术语。
> 路由（routing）就是通过互联的网络把信息从源地址传输到目的地址的活动. --- 维基百科

路由器提供了两种机制: **路由**和**转送**.

- 路由是决定数据包从来源到目的地的路径.
- 转送将输入端的数据转移到合适的输出端.

路由中有一个非常重要的概念叫**路由表**.
路由表本质上就是一个映射表, 决定了数据包的指向.



# 路由的发展

## 后端路由阶段

​	早期的网站开发整个HTML页面是由服务器来渲染的,服务器直接生产渲染好对应的HTML页面, 返回给客户端进行展示.但是, 

一个网站, *这么多页面服务器如何处理呢?*
一个页面有自己对应的网址, 也就是URL,URL会发送到服务器, 服务器会通过正则对该URL进行匹配, 并且最后交给一个Controller进行处理,Controller进行各种处理, 最终生成HTML或者数据, 返回给前端,这就完成了一个**IO操作**.
上面的这种操作, 就是**后端路由**.

---

​	当我们页面中需要请求不同的路径内容时, 交给服务器来进行处理, 服务器渲染好整个页面, 并且将页面返回给客户端.这种情况下渲染好的页面, 不需要单独加载任何的js和css, 可以直接交给浏览器展示, 这样也有利于SEO的优化.
后端路由的**缺点**:
一种情况是整个页面的模块由后端人员来编写和维护的.
另一种情况是前端开发人员如果要开发页面, 需要通过PHP和Java等语言来编写页面代码.
而且通常情况下HTML代码和数据以及对应的逻辑会混在一起, 编写和维护都是非常糟糕的事情.

![image](../images/01-后端路由阶段.png)



## 前端路由阶段

### 前后端分离阶段

**前后端分离阶段：**
随着*Ajax*的出现, 有了前后端分离的开发模式.
后端只提供API来返回数据, 前端通过Ajax获取数据, 并且可以通过JavaScript将数据渲染到页面中.
这样做最大的优点就是前后端责任的清晰, 后端专注于数据上, 前端专注于交互和可视化上.
并且当移动端(iOS/Android)出现后, 后端不需要进行任何处理, 依然使用之前的一套API即可.
目前很多的网站依然采用这种模式开发.

![image](../images/02-前端后端分离阶段.png)



### 单页面富应用阶段

**单页面富应用阶段:**
其实SPA最主要的特点就是在前后端分离的基础上加了一层前端路由.
也就是前端来维护一套路由规则.

![image](../images/03-SPA页面页面的阶段.png)

<img src="../images/04-前端路由中url和组件的关系.jpg" alt="image" style="zoom:100%;" />



**前端路由的核心是什么呢？**

改变URL，但是页面不进行整体的刷新。
*如何实现呢？*

**URL的hash:**
URL的hash也就是锚点(#), 本质上是改变window.location的href属性，我们可以通过直接赋值location.hash来改变href, 但是页面不发生刷新.

![image](../images/24.png)

**HTML5的history模式：pushState()**

history接口是HTML5新增的, 它有五种模式改变URL而不刷新页面,history.pushState().

![image](../images/25.png)

**HTML5的history模式：replaceState()**

![image](../images/26.png)

**HTML5的history模式：go**

![image](../images/27.png)

**说明:**

上面只演示了三个方法,因为 history.back() 等价于 history.go(-1),history.forward() 则等价于 history.go(1),这三个接口等同于浏览器界面的前进后退。



# vue-router简介

> 目前前端流行的三大框架, 都有自己的路由实现:
> Angular的ngRouter
> React的ReactRouter
> Vue的vue-router

==vue-router==是Vue.js官方的路由插件，它和vue.js是深度集成的，适合用于构建单页面应用。
我们可以访问其官方网站对其进行学习: https://router.vuejs.org/zh/

vue-router是基于**路由和组件**的，
**路由**用于设定访问路径, 将路径和组件映射起来。
在vue-router的单页面应用中, 页面的路径的改变就是**组件的切换**。

---

**安装和使用vue-router**

*使用npm来安装路由:*

步骤一: 安装vue-router

```sh
npm install vue-router --save
```

步骤二: 在模块化工程中使用它(因为是一个插件, 所以可以通过Vue.use()来安装路由功能)

![image](../images/Snipaste_2021-05-23_20-40-51.png)

第一步：导入路由对象，并且调用 Vue.use(VueRouter)
第二步：创建路由实例，并且传入路由映射配置
第三步：在Vue实例中挂载创建的路由实例.

![image](../images/Snipaste_2021-05-23_20-41-42.png)

```js
import Vue from 'vue' 
import VueRouter from 'vue-router' 

Vue.use(VueRouter)
```

*使用vue-router的步骤:*
第一步: 创建路由组件
第二步: 配置路由映射: 组件和路径映射关系
第三步: 使用路由: 通过<router-link>和<router-view>



# vue-router基本使用

## 初始步骤

- 创建router实例

![image](../images/28.png)

- 挂载到Vue实例中

![image](../images/29.png)

- 步骤一：创建路由组件

![image](../images/30.png)

- 步骤二：配置组件和路径的映射关系

![image](../images/31.png)

- 步骤三：使用路由.

![image](../images/32.png)

<!--<router-link>: 该标签是一个vue-router中已经内置的组件, 它会被渲染成一个<a>标签.
<router-view>: 该标签会根据当前的路径, 动态渲染出不同的组件.
网页的其他内容, 比如顶部的标题/导航, 或者底部的一些版权信息等会和<router-view>处于同一个等级.
在路由切换时, 切换的是<router-view>挂载的组件, 其他内容不会发生改变.-->

![image](../images/33.png)

---

## 相关配置

- 路由的默认路径

我们这里还有一个不太好的实现: 默认情况下, 进入网站的首页, 我们希望<router-view>渲染首页的内容.但是我们的实现中, 默认没有显示首页组件, 必须让用户点击才可以.如何可以让路径默认跳转到首页, 并且<router-view>渲染首页组件呢?
非常简单, 我们只需要配置多配置一个映射就可以了！

![image](../images/34.png)

**配置解析:**
我们在routes中又配置了一个映射. 
path配置的是根路径: /	（也可以不填写/）
redirect是重定向, 也就是我们将根路径重定向到/home的路径下, 这样就可以得到我们想要的结果了.

- HTML5的History模式

我们前面说过改变路径的方式有两种:
**URL的hash**
**HTML5的history**
默认情况下, 路径的改变使用的URL的hash.
如果希望使用HTML5的history模式, 非常简单, 进行如下配置即可:

![image](../images/35.png)

如下：

![image](../images/36.png)



## router-link补充

在前面的<router-link>中, 我们只是使用了一个属性: **to**, 用于指定跳转的路径.
<router-link>还有一些其他属性:
**tag**: tag可以指定<router-link>之后渲染成什么组件, 比如上面的代码会被渲染成一个<li>元素, 而不是<a>
**replace**: replace不会留下history记录, 所以指定replace的情况下, 后退键返回不能返回到上一个页面中
**active-class**: 当<router-link>对应的路由匹配成功时, 会自动给当前元素设置一个router-link-active的class, 设置active-class可以修改默认的名称.
在进行高亮显示的导航菜单或者底部tabbar时, 会使用到该类.
但是通常不会修改类的属性, 会直接使用默认的router-link-active即可. 

![image](../images/37.png)

---

修改**linkActiveClass**

该class具体的名称也可以通过router实例的属性进行修改 

![image](../images/38.png)

![image](../images/39.png)

**exact-active-class：**
类似于active-class, 只是在精准匹配下才会出现的class.
后面看到嵌套路由时, 我们再看下这个属性.



## 路由代码跳转

有时候, 页面的跳转可能需要执行对应的JavaScript代码, 这个时候, 就可以使用第二种跳转方式了
比如, 我们将代码修改如下: 

![image](../images/40.png)



# vue-router详解

## 动态路由

在某些情况下，一个页面的path路径可能是不确定的，比如我们进入用户界面时，希望是如下的路径：
/user/aaaa或/user/bbbb
除了有前面的/user之外，后面还跟上了用户的ID
这种path和Component的匹配关系，我们称之为**动态路由**(也是路由传递数据的一种方式)。

![image](../images/41.png)

![image](../images/42.png)

![image](../images/43.png)

![image](../images/44.png)







