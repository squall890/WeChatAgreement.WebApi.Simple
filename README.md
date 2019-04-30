# 微信mac/ipad协议，webapi免IIS部署版本。
 请进入  http://www.wechattools.com/ 进行注册授权<br/><br/>
# 操作指南：
1.新机器首次需要进入cmd，关闭windows数据保护DEP（dep可能会导致不安全代码闪退）：bcdedit.exe/set {current} nx AlwaysOff，重启电脑<br/><br/>
2.找到mac/ipad目录<br/><br/>
3.打开WeChatServer.exe.config<br/><br/>
4.配置授权信息，api端口，和websocket端口，接收消息回调接口地址，管理员密码等参数<br/><br/>
```  
    <add key="AuthKey" value="" />
    <add key="WebApiHost" value="22221" />
    <add key="WebSocketHost" value="22222" />
    <add key="MsgCallBackUrl" value="" />
    <add key="AdminPassword" value="123456" />
```
其中IsReceiveMsg为是否接受websocket消息以及接口回调消息的开关。由于消息无法上线程锁。可能会因消息并发导致程序崩溃。如无需用到接收消息功能可以关闭该选项，会稳定很多。
<br/><br/>
5.右键管理员运行 WeChatServer.exe
看见  开启服务... 证明服务已经开启<br/><br/>
6.在浏览器运行http://localhost:22221/swagger/ 即可查看所有webapi文档。（请先仔细阅读test.html 代码 通过websocket创建连接 获取二维码登录后才可调用api）<br/><br/>
7.微信登录获取二维码需要参考Test.html 中websocket方式创建websocket链接来获取二维码登录。uuid为创建websocket时传入参数。<br/><br/>
8.提供两种登录方式 ：1、二维码登录  2、账号密码+62登录  （通过二维码登录以后 调用api获取到62数据 保存下来后即可通过账号密码+62进行登录）<br/><br/>
9.在微信成功登录以后，即可通过Http post的方式传入uuid来操作微信了<br/><br/>
10.有时微信多次非正常退出或者操作频繁时，会造成Api接口异常崩溃，可以运行进程保活工具<br/><br/>
11.消息回调通过websocket 异步回调的方式返回，如果websocket不在线则无法接受到消息回调，或者在config中配置MsgCallBackUrl，消息将会进行表单提交。如果有特殊需求可以联系群主索要代码自行修改消息回调逻辑，例如存入数据库或对其他应用api进行调用。<br/><br/>

# 声明:
仅供自己学习研究使用，引起任何法律纠纷概不负责

# 更多:
demo源码暂时不放github了。如需要研究源码学习，请加入我的知识星球。<br/>
demo源码使用c#进行开发，开发环境为VS2017 .net framework 4.6.1<br/>
![](https://github.com/changtuiqie/WeChatAgreement.WebApi.Simple/blob/master/zsxq.jpg) <br/>