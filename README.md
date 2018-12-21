# 微信mac/ipad协议，webapi免IIS部署版本。
 请进入  http://www.keduoduo.online/ 进行注册授权<br/>
1.找到mac/ipad目录<br/>
2.打开WeChatServer.exe.config<br/>
3.配置授权信息，api端口，和websocket端口，管理员密码等参数<br/>
```  
    <add key="AuthKey" value="" />
    <add key="WebApiHost" value="22221" />
    <add key="WebSocketHost" value="22222" />
    <add key="AdminPassword" value="123456" />
```
<br/>
4.右键管理员运行 WeChatServer.exe
看见  开启服务... 证明服务已经开启<br/>
5.在浏览器运行http://localhost:22221/swagger/ 即可查看所有webapi文档。（请先仔细阅读test.html 代码 通过websocket创建连接 获取二维码登录后才可调用api）<br/>
6.微信登录获取二维码需要参考Test.html 中websocket方式创建websocket链接来获取二维码登录。uuid为创建websocket时传入参数。<br/>
7.提供两种登录方式 ：1、二维码登录  2、账号密码+62登录  （通过二维码登录以后 调用api获取到62数据 保存下来后即可通过账号密码+62进行登录）
8.在微信成功登录以后，即可通过Http post的方式传入uuid来操作微信了<br/>
9.请<a target="_blank" href="https://jingyan.baidu.com/article/335530daab956419cb41c38a.html">关闭dep</a> ，dep可能会导致不安全代码闪退。
10.消息回调通过websocket 异步回调的方式返回，如果websocket不在线则无法接受到消息回调，如果有特殊需求可以联系群主索要代码自行修改消息回调逻辑，例如存入数据库或对其他应用api进行调用。

<a target="_blank" href="//shang.qq.com/wpa/qunwpa?idkey=3194af004cbc013eff0a61b99a46ae6f66c2c1f1fc62a9cdf58de1fd2b471058">获取更新信息请加入qq群：721314034</a>
<br/>
demo源码暂时不放github了。如需要研究源码学习，请进群联系群主。<br/>
demo源码使用c#进行开发，开发环境为VS 2017 框架.net framework 4.6.1<br/>

作者qq：286513187

