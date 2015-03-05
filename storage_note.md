##Clouda离线存储介绍

**概念介绍**

Clouda离线存储一套可编程的离线缓存方案。其主要通过对本地数据库操作、文件存储操作、http请求拦截而实现的。

***常态离线缓存***：资源被缓存以后，如果没有删除缓存，以后每次访问都会使用缓存资源

***非常态离线缓存***：资源被缓存以后，只有在网络离线的情况下使用缓存资源，网络在线时不使用缓存资源

**Clouda离线存储的简单使用**

通过meta标签启动离线存储功能
	
	1、在head中间加入：

	<script name="baidu-tc-cerfication" type="text/javascript" charset="utf-8" src="http://apps.bdimg.com/cloudaapi/lightapp.js"></script>
	<meta name="Cache-Type" content="text/css;text/js;image/gif"> 

	该meta标签代表需要缓存该页面的所有的css文件、js文件、gif图片文件。

	2、在初始化Blend时加入cache组件，在加入组件后做下cache的初始化

	Blend.lightInit({
		ak:'xxx', /*ak是用户在百度开发者平台申请的appKey*/
		module:['cache']
	},function(){
		Blend.device.cache.init();
	});

在页面中加入这段代码即表示离线缓存本地css、js、gif资源，当然如果需要缓存如：png\jpg 等图片，也可以在content中加入 "image/png;image/jpg"（注意：使用该缓存会自动将本页面缓存为非常态离线缓存）。

**Clouda离线存储的自主编程操作**

在一些情况可能我们仅仅想缓存一些

 