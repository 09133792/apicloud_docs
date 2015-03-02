/*
Title: bookReader
Description: bookReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setValue](#2)

[show](#3)

[hide](#4)

[close](#5)

[getProgress](#6)

[setBrightness](#7)

[getBrightness](#8)

[brightness](#9)
</div>

#**概述**

本模块是原生实现的一个文本阅读器，开发者只要传进来一个text文本文件，配置相应的参数，模块底层即可实现一个翻页效果的图书阅读器

![图片说明](/img/docImage/bookReader.jpg)

#**open**<div id="1"></div>

打开阅读器

open({params}, callback(ret, err))

##params

x：

- 类型：数字	
- 默认值： 0
- 描述：模块视图左上角点的坐标，可为空

y：

- 类型：数字	
- 默认值：0
- 描述：模块视图左上角点的坐标，可为空

w：

- 类型：数字	
- 默认值：当前设备屏幕的宽
- 描述：模块视图左上角点的宽，可为空

h：

- 类型：数字	
- 默认值：当前设备屏幕的高
- 描述：模块视图左上角点的高，可为空

bg：

- 类型：字符串	
- 默认值：#FFFFF0
- 描述：阅读器的背景色，支持rgb，rgba，img，#，可为空

animType：

- 类型：字符串
- 默认值：curl
- 描述：翻页动画效果，可为空。（保留使用）

progress：

- 类型：数字
- 默认值：0
- 描述：阅读器打开时的进度，取值范围0-100，可为空

textStyle：

- 类型：json对象
- 默认值：见内部字段
- 描述：阅读文本字体样式设置，可为空

内部字段：

```js
{
	size：         //字体大小，数字，默认12，可为空
    color:         //字体颜色，字符串，支持rgb，rgba，#，可为空。默认#424242
}
```

filePath：

- 类型：字符串
- 默认值：无
- 描述：阅读器数据源文件地址，支持widget等本地路径协议，不可为空

codingType：

- 类型：字符串
- 默认值：gbk
- 描述：所要阅读的文本的编码格式，取值范围:gbk、utf8，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将模块视图添加到指定窗口的名字，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	eventType://事件类型，字符串，取值范围见事件类型
	progress：//阅读当前进度（翻页时）
}
```

##示例代码

```js
var obj = api.require('bookReader');
obj.open({
   filePath : "widget://res/test.txt"
},function(ret, err){
   if(ret){
        api.alert({msg:ret.eventType+ret.progress});
    }
});
```

##补充说明

打开阅读器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setValue**<div id="2"></div>

设置阅读器的参数

setValue({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：阅读器的背景色，支持rgb，rgba，img，#，可为空

animType：

- 类型：字符串
- 默认值：curl
- 描述：翻页动画效果，可为空。（保留使用）

progress：

- 类型：数字
- 默认值：0
- 描述：阅读器打开时的进度，取值范围0-100，可为空

textStyle：

- 类型：json对象
- 默认值：见内部字段
- 描述：阅读文本字体样式设置，可为空

内部字段：

```js
{ 
	size：         //字体大小，数字，默认12，可为空
    color:         //字体颜色，字符串，支持rgb，rgba，#，可为空
}
```

filePath：

- 类型：字符串
- 默认值：无
- 描述：阅读器数据源文件地址，支持widget等本地路径协议，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""//错误描述，字符串
}
```

##示例代码

```js
var obj= api.require('bookReader');
obj.setValue({
	bg:"#000000",
	textStyle:{
		color:"#FFFFFF",
		size:20
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**show**<div id="3"></div>

显示阅读器

show(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""//错误描述，字符串
}
```

##示例代码

	var obj= api.require('bookReader');
	obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**hide**<div id="4"></div>

隐藏阅读器

hide(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""//错误描述，字符串
}
```

##示例代码

	var obj= api.require('bookReader');
	obj.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭阅读器

close(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""//错误描述,字符串
}
```

##示例代码

	var obj= api.require('bookReader');
	obj.close();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getProgress**<div id="6"></div>

关获取指定文件的阅读进度

getProgress(params,callBack(ret,err))

##params

filePath：

- 类型：字符串
- 默认值：无
- 描述：所要获取当前阅读进度的文件地址，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:             //状态值，布尔值
	progress:           //进度，数字
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg: ""//错误描述,字符串
}
```

##示例代码

	var obj = api.require('bookReader');
	obj.getProgress({filePath:"widget://res/test.txt"});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**setBrightness**<div id="7"></div>

设置屏幕亮度

setBrightness(params,callBack(ret,err))

##params

brightness：

- 类型：数字
- 默认值：80
- 描述：设置的屏幕的亮度，取值范围0-100，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //是否设置成功，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg: ""//错误描述,字符串
}
```

##示例代码

	var obj = api.require('bookReader');
	obj.setBrightness();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**getBrightness**<div id="8"></div>

获取屏幕亮度

getBrightness(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //是否设置成功，布尔值
	brightness:           //返回的当前屏幕亮度，数字类型
}
```

err：

- 类型：JSON对象

内部字段：

```
{
	msg: “”		//错误描述,字符串
}
```

##示例代码

	var obj = api.require('bookReader');
	obj.getBrightness();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**brightness**<div id="9"></div>

获取、设置屏幕亮度

brightness(params,callBack(ret,err))

##params

brightness：

- 类型：数字
- 默认值：无
- 描述：设置的屏幕的亮度，取值范围0-100，可为空，若为空则返回当前屏幕亮度

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           	//是否设置成功，布尔值
	brightness:         //params为空时返回当前屏幕亮度，数字类型
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
	msg: “”//错误描述,字符串
}
```

##示例代码

```js
var obj = api.require('bookReader');
obj.brightness(function(ret,err){
	if(ret.status){
		api.alert({msg:ret.brightness});
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


</div>


<div id="const-content">
#**事件类型**

callBack事件的类型。字符串

##取值范围：

- click				//点击
- page_up			//向上翻页
- page_down        	//向下翻页
- page_over         //在最后一页时的下翻页事件
- page_begin        //在第一页时的上翻页事件
