/*
Title: baiduNavigation
Description: baiduNavigation
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">

</div>

#**概述**

baiduNavigation模块封装了百度导航的sdk，使用此模块只需输入起点终点经纬度即可轻松集成百度导航功能：

在集成此模块之前需先配置config文件。在config里添加如下字段：

```js
名称：baiduNavigation
参数：android_api_key、ios_api_key
描述：百度开放平台的安全码获取需要区分移动平台，意味着如果你的同一个App需要同时支持IOS和Android平台，那么，您必须为这两个平台单独申请apiKey，即同一个App申请两个apiKey，并将这两个apiKey同时配置在config文件中。	
```

配置示例：

```js
<feature name="baiduNavigation">
					<param name="android_api_key " value=" 2kyNa3maO5mXcASnUe5EwVoM " />
					<param name="ios_api_key " value=" IvbnWLuuTnbmjOOg17zpbe0O " />
</feature>
```

字段描述：

```js
1、android_api_key：android版本的apiKey
2、ios_api_key：Ios版本的apiKey
```

详情参考OpenApiGuid_Baidu.doc文档，与baiduMap配置相似。


#**start**<div id="a1"></div>

开始导航

start({params}, callback(ret, err))

##params

start：

- 类型：json对象
- 默认值：无
- 描述：起点信息，不能为空

内部字段：

```js
{
    position: //起点经纬度，与address配合可为空，josn对象类型
      内部字段：{
	lon：  //起点经度，数字类型，不可为空
	lat：  //起点纬度，数字类型，不可为空
				}
    title：//起点描述信息，字符串类型，可为空
    address://起点地址信息，字符串类型，与position配合为空
}
```

goBy：

- 类型：数组对象
- 默认值：无
- 描述：途经点位置信息，可为空，可输入1-3个途经点

内部字段：

```js
[{
	position: //起点经纬度，与address配合可为空，josn对象类型
	内部字段：{
	lon：  //起点经度，数字类型，不可为空
	lat：  //起点纬度，数字类型，不可为空
			}
    title：//起点描述信息，字符串类型，可为空
    address://起点地址信息，字符串类型，与position配合为空
}]
```

end：

- 类型：json对象
- 默认值：无
- 描述：终点信息，不能为空

内部字段：

```
{
	position: //起点经纬度，与address配合可为空，josn对象类型
      内部字段：{
		lon：  //起点经度，数字类型，不可为空
		lat：  //起点纬度，数字类型，不可为空
			}
    title：//起点描述信息，字符串类型，可为空
    address://起点地址信息，字符串类型，与position配合为空
}
```

routMode：

- 类型：字符串
- 默认值：recommend
- 描述：导航路线类型，取值范围见[路线类型](!Constant)，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
{
	status: //导航成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg: //错误描述
	code：//错误码，参见导航错误码
}
```

##示例代码

```js
var baiduNavigation = api.require('baiduNavigation');
baiduNavigation.start({
    start: { // 起点信息.
        position: { // 经纬度，与address配合可为空
			lon: 112.47723797622677, // 经度.
			lat: 34.556480000000015 // 纬度.
        },
        title: "中国四大石窟之一", // 描述信息
        address: "龙门石窟" // 地址信息，与position配合为空
    },
	goBy: [{ // 途经点位置信息.
        position: { // 经纬度，与address配合可为空
		lon: 109.77539000000002, // 经度
		lat: 33.43144 // 纬度.
        },
        title: "释源", // 描述信息
        address: "白马寺" // 地址信息，与position配合为空
    }],
    end: { // 终点信息.
        position: { // 经纬度，与address配合可为空
		lon: 111.57062599999995, // 经度
		lat: 33.784214 // 纬度
        },
        title: "龙蛇之窟", // 描述信息
        address: "鸡冠洞" // 地址信息，与position配合为空
    }
}, function(ret, err){
	if(ret.status){
		api.alert({
            title: "提示",
			msg:'导航成功'
        });
}else{
	varmsg = "未知错误";
	if(1 == err.code){
		msg = "获取地理位置失败";
	        }
	if(2 == err.code){
		msg = "定位服务未开启";
	        }
	if(3 == err.code){
		msg = "线路取消";
	        }
	if(4 == err.code){
		msg = "退出导航";
	        }
if(5 == err.code){
	msg = "退出导航声明页面";
        }
		api.alert({
            title: "导航出错",
			msg: msg
        });
    }
});
```

##补充说明

开始导航指定线路

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>

<div id="const-content">
<div class="outline">
[导航失败错误码](#a100)

[路线类型](#a101)
</div>

#**导航失败错误码**<div id="a100"></div>

导航失败码。数字类型

##取值范围：

- 1		//获取地理位置失败
- 2		//定位服务未开启
- 3		//线路取消
- 4		//退出导航
- 5		//退出导航声明页面

#**路线类型**<div id="a101"></div>

所要导航路线的类型。字符串类型

##取值范围：

- recommend            //推荐
- android专用类型（对ios无效）
- min_time		//最短时间
- min_dist		//最短距离
- min_toll		//最少收费
- avoid_trafficJam		//躲避拥堵
