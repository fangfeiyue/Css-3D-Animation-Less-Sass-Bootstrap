# 前端三剑客 — Css相关知识梳理
CSS是前端开发过程中必不可少的知识点，也是最难彻底掌握的部分。本项目系统梳理CSS中各方面的知识点，帮助前端工程师更清晰地了解实际工作中如何应用CSS技术的，更好地面对日常使用！

## 技术栈和主要框架
- Sass
- Less
- Bootstrap
- PostCss

## 下载项目
```
git clone https://github.com/fangfeiyue/Css-3D-Animation-Less-Sass-Bootstrap.git
```
## 运行项目
```
npm install
npm start
```
## 项目截图
## 文件结构
## 功能
- [√]
- [√]
- [√]
- [] 
## 一、Css基础-层叠样式表(Cascading Style Sheet)
### 1.选择器
- 选择器分类
    - 元素选择器，如a{}
    - 伪元素选择器，如::before{}
    - 类选择器，如.link{}
    - 属性选择器，如[type=radio]{}
    - 伪类选择器，如:hover{}
    - id选择器，如#id{}
    - 组合选择器，如[type=checkbox]+label{}
    - 否定选择器，如:not(.link){}
    - 通用选择器，如*{}
浏览器从右向左依次匹配选择器进行解析，这样可以加快浏览器对css解析速度

- 伪元素和伪类选择器的区别

伪元素是一种真实存在的元素，在页面上可以有样式可以有内容，伪类是一个元素的状态

- 选择器权重
我们刚从上面看过选择器的分类，感觉好蒙圈呀，怎么这么多的选择器？分这么多中干啥呢？就像英语一样，英语为啥分那么多音标呢，其实就是为了咱们好拼读。分这么多选择器也是为了咱们在不同的场景下可以方便的书写Css样式，其中最重要的是定义了选择器的权重，我们可以做个简单的计数，如下：
    - id选择器 +100
    - 类、属性、伪类 +10
    - 元素、伪元素 +1
    - 其他选择器 +0
    - !important优先级最高
    - 相同权重后写的生效
    - 元素属性优先级高

例子：
```
1.#id .link a[href]得到的计数结果为100 + 10 + 1 + 0 = 111；
2.#id .link.active得到的计数结果为100 + 10 + 10 = 120;
2会覆盖1的样式
```
但是要注意计数是一个不进位的数字，不如说我们有十一个类拼在一起，得到的计数结果为110，但它的
优先级并不会超过id选择器哦,权重的高的就是权重高哦。

### 2、非布局样式
### 字体
- 字体名称用引号包裹，字体组不能用引号包裹,如下sans-serif是字体组，所以不能用引号包裹
```
body{
    font-family: 'Gill Sans', sans-serif
}
```

- 阿里巴巴矢量图标库的使用
    - 登录[阿里巴巴矢量图标库](http://iconfont.cn/)
    - 搜索框输入想要的图标，如collect
    - 将鼠标放到要选中的图标上，加入购物车
    - 点击网页左上角的购物车,在左侧弹出的窗上新建项目，然后点击添加到项目
    - 然后点击到下载到本地，解压缩后打开demo_fontclass.html文件，按照这个文件介绍的操作即可

- 自定义字体
```
@font-face{
    font-family: 'FangFeiyue';
    src: url('');
}
.custom-font{
    font-family: 'FangFeiyue'
}
...
<div class="custom-font">自定义字体</div>
```
### 行高
- 问题：下面代码中图片距离div底部会产生一些间距
```
.div2{
    background-color: red;
}
....
<div class="div2">
    <span>我是一个粉刷匠</span>
    <img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=160554372,288864420&fm=27&gp=0.jpg" alt="">
</div>
```
原因：img为inline-block，会按照baseline的方式对齐，沿基线对齐就意味着到底线之间会有一空隙

解决办法：
- 解决办法一：display:block
- 解决办法二：vertial-align:bottom

### 背景
- linear-gradient背景渐变
```

...

div{
    height: 100px;
    
    /* background: linear-gradient(to right, red, green); */
    
    /* background: linear-gradient(180deg, red, green); */
    
    /* background: linear-gradient(135deg, red 0, green 10%, yellow 50%, blue 100%); */

    background: linear-gradient(135deg, transparent 0, transparent 49.5%, green 49.5%, green 50.5%, transparent 50.5%, transparent 100%),
        linear-gradient(45deg, transparent 0, transparent 49.5%, red 49.5%, red 50.5%, transparent 50.5%, transparent 100%);
    background-size: 30px 30px;
}

...

<div></div>
```
上述代码运行效果如下
![背景渐变](https://github.com/fangfeiyue/Css-3D-Animation-Less-Sass-Bootstrap/blob/master/img/Snip20180118_2.png)
- 背景图片和属性(雪碧图)
    - 雪碧图，使用基本步骤，以京东左侧悬浮窗京东会员为例
        - 下载这张雪碧图http://misc.360buyimg.com/mtd/pc/o2_toolbar/1.0.0/home/images/toolbars.png
        - 用ps打开这张雪碧图，分别用选框工具测量图片左边和顶部到小人左边和顶部的距离，注意：测量的单位为像素哦
        - 如果ps测量单位为厘米，可以按ctrl+k--》单位尺寸--》单位--》标尺，将厘米改为像素
        - 将这张图设置为背景图片background: url(http://misc.360buyimg.com/mtd/pc/o2_toolbar/1.0.0/home/images/toolbars.png); 
        - 设置background-position属性为刚测量的数据

        具体代码如下：
```
...
.div3{
    width: 100px;
    height: 100px;
    background: orange url(http://misc.360buyimg.com/mtd/pc/o2_toolbar/1.0.0/home/images/toolbars.png);
    background-position: -97px -212px;
}
...
<div class="div3"></div>
```
- base64和性能优化
    - 优点：
    使用base64的好处是可以节省http请求次数。
    - 缺点：
        - 会导致文件的体积增大，一方面图片本身的体积会变成之前的三分之四，另一方面本来图片是单独的文件，现在用base64将它放到的css样式中，从下面代码也能看出css里面增加了好多看不懂的代码。
        - 第二增加了浏览器解码的开销。
        - 第三不利于维护，因为很那从代码看出你这里到底放的是什么图片。

所以base64只适合非常小的图片。
```
...
.div2{
        height: 200px;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAEDWlDQ1BJQ0MgUHJvZmlsZQAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VVBg/m8AAAAfSURBVCgVY7RZ9eE/A4mAiUT1YOWjmqChNhoQlAQEAL0AAu98mKqkAAAAAElFTkSuQmCC)
}
...
<div class="div2"></div>
```
- 多分辨率适配

### 边框
- 边框的背景图
```
...
.div1{
    width: 400px;
    height: 200px;
    border: 30px solid transparent;
    border-image: url('./img/border.png') 30 round;
}
...
<div class="div1"></div>
```
- 边框实现三角形
```
...
 .div2{
    width: 0;
    height: 200;
    border-bottom: 30px solid red;
    border-right: 30px solid transparent;
    border-left: 30px solid transparent;
}
...
<div class="div2"></div>
```
### 滚动
- overflow
可能的值：
    - visible	默认值。内容不会被修剪，会呈现在元素框之外。
    - hidden	内容会被修剪，并且其余内容是不可见的。
    - scroll	内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。
    - auto	如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。
    - inherit	规定应该从父元素继承 overflow 属性的值。
### 文本折行
- overflow(word-wrap)通用换行控制
- word-break针对多字节文字
- white-space空白处是否断行
    - white-space: nowrap;文本不换行
```
...
.div1{
    border: 1px solid;
    width: 100px;
    word-wrap: normal;
    word-break: break-all;
    white-space: normal;
}
...
<div class="div1">
    asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfadfasdfadsf
</div>
```
## Bootstrap4
- 变化
    - 兼容IE10+
    - 使用flexbox布局
    - 抛弃nomalize.css
    - 提供布局和reboot版本
- Bootstrap的优缺点
    - 优点：css代码结构合理，现成的样式可以直接使用
    - 缺点：定制较为繁琐，体积大
- Bootstrap如何实现响应式布局
    - 原理：通过media query设置不同分辨率的class
    - 使用：为不同分辨率选择不同的网格class 
### bootstrap js组件

注意：bootstrap js依赖于jq和proper.js，使用的时候要把这个js文件引进来

- 使用方式
    - data-*属性
    - 基于js的api

如下demo，弹框使用的data-*属性来控制弹框的显示和隐藏，弹框2是用js api操作的
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js" integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q" crossorigin="anonymous"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js" integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl" crossorigin="anonymous"></script>
</head>
<body>
    <button id="showModal" data-toggle="modal" data-target="#exampleModal">弹窗1</button>
    <button id="showModal2">弹窗2</button>
    <div id="exampleModal" class="modal" tabindex="-1" role="dialog">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <p>Modal body text goes here.</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-primary">Save changes</button>
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            </div>
            </div>
        </div>
    </div> 
    <script>
        $('#showModal2').click(function(){
            $('#exampleModal').modal();
        });
    </script>             
</body>
</html>
```
### Bootstrap响应式布局

可以运用Bootstrap的栅格系统实现响应式布局,Bootstrap将屏幕分割成12分,我们可以使用Bootstrap定义的类来实现每个元素在不同的屏幕宽度下占屏幕几分，来实现响应式布局

![栅格系统](https://github.com/fangfeiyue/Css-3D-Animation-Less-Sass-Bootstrap/blob/master/img/Snip20180124_1.png)
我们可以根据上面的表格来设计不同屏幕尺寸下，元素的占屏比来实现响应式布局
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
    <title>Bootstrap</title>
    <style>
        .content > div{
            height: 100px;
            line-height: 100px;
            text-align: center;
            color: #333;
            background:#cccccc;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="row">
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
            <div class="content col-12 col-lg-3 col-md-4 col-sm-6"><div>内容</div></div>
        </div>
    </div>
</body>
</html>
```
Bootstrap提供了一套css样式，可以方便我们在没有设计的情况下尽快实现一些功能，但如果有设计的使用，仅仅靠Bootstrap自带的样式，很难完成相应的要求，这是我们就需要根据需求来定制Bootstrap的样式了。
### Bootstrap定制方法
- 使用css同名类进行覆盖
    - 优点：操作起来相对简单
    - 缺点：需要非常全面的去覆盖class不能有遗漏，工作量大，比较容易产生遗漏；
- 修改源码重新构建
    - 优点：主要了解bs的源码，就可以修改的非常彻底，不会留有死角
    - 缺点：门槛相对较高，需要去了解bs的源码
- 应用scss源文件修改变量，这种方式将BS当做预处理器的框架来使用，需要什么模块就引入什么模块， 同时可以对这些模块进行定制， 使用起来更灵活，但是这种方式对BS的结构要求更高，需要了解每一个模块是做什么的， 才能精准的去使用对应的模块。
## CSS工程化方案
## 勘误
由于本人的能力有限，项目难免有所瑕疵，欢迎您的批评、指正
## 感谢
如果对您有帮助，您可以点右上角 "Star" 支持一下 谢谢！ ^_^

或者您可以 "follow" 一下，我会不断开源更多的有趣的项目
## 个人简介
作者：房飞跃

博客地址：[前端网](http://www.qdfuns.com/house/31986/note) [GitHub](https://github.com/fangfeiyue)

职业：web前端开发工程师

爱好：探索新事物，学习新知识

座右铭：一个终身学习者

## 联系方式
坐标：北京

微信：

![XinShiJieDeHuHuan](http://note.youdao.com/yws/public/resource/c2361265179a03449f6d52397fd50033/xmlnote/100D55934BB446839482D3EA0CDC3E8D/17820)

QQ：294925572

邮箱：fangfeiyue918@163.com
## 赞赏
觉得有帮助可以微信扫码支持下哦，赞赏金额不限，一分也是您对作者的鼎力支持

![微信打赏](http://note.youdao.com/yws/public/resource/c2361265179a03449f6d52397fd50033/xmlnote/D77744C8EC944CF6AA232272CBC5CF6D/17828)
