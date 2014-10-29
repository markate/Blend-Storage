一、主动存储

主动存储主要考虑通过runtime为web提供存储大规模数据、文件的条件（每个轻应用创建一个私有的自己的文件存储路径

，以及数据存储文件），并且提供接口给用户进行调用。 其API列表如下：

组件名称：Blend.device.storage 

Native创建文件对数据进行存储、查询、删除。

1、getIDataItem(options)

options 是一个object对象如下：
<p>
```javascript
{
	paras:{
		appid:xxx,
		key:(string)
	},
	callback:{
		success:function(data){
			//这里data代表返回的数据
	},
	fail:function(){}
	}
}
```
</p>
功能：如存在则输出对应的JSON的字符串（下同）

2、setIDataItem(options)
options 是一个object对象如下：
<code>
{
paras:{
  appid:xxx,
	key:(string),
    value:{}
},
callback:{
  success:function(data){},
fail:function(){}
}
}
</code>
功能：设置存储的值。
<code>
3、removeDataItem(options)
options 是一个object对象如下：
{
paras:{
	appid:xxx,
	key:(string)
},
callback:{
  success:function(data){},
fail:function(){}
}
}
</code>
功能：删除一个数据对象
<code>
4、removeAllDataItems(options)
options 是一个object对象如下：
{
paras:{
	appid:xxx
},
callback:{
  success:function(data){},
fail:function(){}
}
}
</code>
功能：清除该域下所有的数据对象
<code>
5、getDataStorageSize(options)
options 是一个object对象如下：
{
paras:{
	appid:xxx
},
callback:{
  success:function(data){
    size: 1024 
},
fail:function(){}
}
}
</code>
功能：获取剩余的数据存储空间数据存储的剩余空间

6、getFileItem(options)
<code>
options 是一个object对象如下：
{
paras:{
	 appid:xxx,
   key:xxx，
 },
callback:{
    success:function(data){},
fail:function(){}
}
}
</code>
功能：获取文件的路径

规则说明：

存储文件实质上是存储数据+文件保存，即调用存储文件的api时，调用文件存储的api

后，再调用setIDatatem方法存储key以及对应的文件路径。所以所有data存储

中如果key 为 key  这种方式的则为文件存储。即getFileItem这个API也可以通过

getIDatatem实现。


7、setFileItem(options)

options 是一个object对象如下：
<code>
{
paras:{
   appid:xxx,
   key:xxx，
   value:”url”
},
callback:{
    success:function(data){},
fail:function(){}
}
}
</code>
功能：存储文件

存储文件实质上是存储数据+文件保存，即调用存储文件的api时，调用文件存

储的api后，再调用setIDatatem方法存储key以及对应的文件路径。所以所有data存

储中如果key 为  blend-file-damain-key  这种方式的则为文件存储。（domain即url的

域）

8、removeFileItem(options)
options 是一个object对象如下：
<code>
{
paras:{
	appid:xxx,
	key:(string)
},
callback:{
  success:function(data){},
fail:function(){}
}
}
</code>
功能：删除一个文件对象

说明：

（1）	删除文件

（2）	删除数据存储中对应的数据的key和value
<code>
9、removeAllFileItems(options)
options 是一个object对象如下：
{
paras:{
  appid:xxx
},
callback:{
  success:function(data){},
fail:function(){}
}
}
</code>
功能：清除本域的所有文件对象，并且将数据存储中相应的key和value删除

10、getFileStorageSize(options)
options 是一个object对象如下：
<code>
{
	appid:xxx,
paras:{},
callback:{
  success:function(data){
    size: 1024 
},
fail:function(){}
}
}
</code>
功能：获取文件存储空间剩余大小（只返回文件存储空间）
