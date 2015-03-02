/*
Title: actionButton
Description: actionButton
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

actionButton 是一个仿照新浪微博快捷菜单而定制的一个模块，使用该模块可弹出一个由多个按钮组成的菜单，点击按钮，菜单消失。此模块最大的特点是弹出和消失都有相应的动画，开发者可自定义按钮的样式和个数（超过单屏显示的可以左右拖动）。效果炫酷，调用方便快捷

![图片说明](/img/docImage/actionButton.jpg)

#**open**<div id="1"></div>

打开弹动按钮菜单

open({params}, callback(ret, err))

##params

items：

- 类型：数组
- 默认值：无
- 描述：弹出的子菜单按钮的信息，该数组有多少个元素，则有多少个菜单按钮。不可为空

内部字段：

```js
[{
    bgColor:            //背景色值
    image：		//图片路径
    title：		//标题
}]
```

pageControl：

- 类型：JSON
- 默认值：无
- 描述：配置页面控制器的显示，可为空，若为空，则不显示页面控制器

内部字段：

```js
{
    activeColor:0,          //当前页颜色值，可为空，默认为红色
    inactiveColor:0,        //非当前页颜色值，可为空，默认为灰色
}
```

topHeight：

- 类型：数字
- 默认值：屏幕的一半
- 描述：上边一排按钮距离屏幕顶部的高度，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

clickDisappear：

- 类型：布尔
- 默认值：true
- 描述：点击子菜单按钮后是否关闭菜单，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	index:       //点击子菜单返回其下标
}
```

##示例代码

```js
var obj = api.require('actionButton');
obj.open({
 	items:[{bgColor:'#00CED1',title:'子标题',image:'widget://res/actionSheet_icon1.png'},
		{bgColor:'#FFC0CB',title:'子标题',image:'widget://res/actionSheet_icon2.png'},
		{bgColor:'#DB7093',title:'子标题',image:'widget://res/actionSheet_icon3.png'},
		{bgColor:'#FF00FF',title:'子标题',image:'widget://res/actionSheet_icon4.png'},
		{bgColor:'#A52A2A',title:'子标题',image:'widget://res/actionSheet_icon5.png'},
		{bgColor:'#A0522D',title:'子标题',image:'widget://res/actionSheet_icon6.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'},
		{bgColor:'#7FFF00',title:'子标题',image:'widget://res/actionSheet_icon7.png'}],
	topHeight:200,
	pageControl:{activeColor:'#778899',inactiveColor:'#DDA0DD'}
},function(ret,err){
	api.alert({msg:ret.index});
});
```

##补充说明

打开弹动菜单按钮

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭菜单

close()

##示例代码

    var obj = api.require('actionButton');
    obj.close();

##补充说明

关闭菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏菜单

hide()

##示例代码

    var obj = api.require('actionButton');
    obj.hide();

##补充说明

隐藏菜单，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="3"></div>

显示已隐藏的菜单

show()

##示例代码

    var obj = api.require('actionButton');
    obj.show();

##补充说明

显示已隐藏的菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

