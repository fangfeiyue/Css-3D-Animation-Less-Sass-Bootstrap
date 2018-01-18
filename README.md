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
