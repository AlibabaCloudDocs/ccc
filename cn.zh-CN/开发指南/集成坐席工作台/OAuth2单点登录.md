OAuth2单点登录 
===============================



**本文将为您说明如何获取访问令牌（access_token）以及 刷新令牌（refresh_token）** 

必读文档 {#h2-u5FC5u8BFBu6587u68631}
--------------------------------

* [OAuth应用开发概述](https://help.aliyun.com/document_detail/93693.html)

  

* [应用注册](https://help.aliyun.com/document_detail/70950.html)

  

* [获取访问令牌及刷新令牌的步骤](https://help.aliyun.com/document_detail/93696.html)

  




静默登录的方式获取授权码 {#h2-u9759u9ED8u767Bu5F55u7684u65B9u5F0Fu83B7u53D6u6388u6743u78012}
--------------------------------------------------------------------------------

在上面必读文档中的 **获取访问令牌及刷新令牌的步骤** 中的第一步，正常来说需要用户手动输入阿里云子用户账号密码来登陆进行认证获取授权码，很多用户并不希望让客服手动来登陆，希望通过服务端来静默登录，所以我们提供了一种服务端静默登录的方式，目前只有java版的demo可供参考：[BatchTokenRetrieval](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/oauth2-demo/BatchTokenRetrieval.zip)。

在呼叫中心新建的坐席，首次登录时会强制重置密码，所以需要您手动关闭 **下次登录必须重置密码** 的开关，参考文档：[坐席或管理员忘记登录密码时怎么办?](~~60675~~)。后期我们会在 **文件导入坐席** 功能页面增加一个是否需要坐席首次登录时重置密码的选项来控制这个操作。现阶段麻烦您手动关闭一下。

**强调说明：如果您使用了静默登录，切记不可每次调用API都进行一次静默登录获取access_token，因为频繁的静默登录会导致登录过于频繁被阿里云流控，进而导致静默登录失败，一定要按照 整体流程说明 中第一小节所属，保存refresh_token，使用refresh_token获取access_token。** 

温馨提示： {#h2--3}
--------------

1. 访问令牌（access_token）的有效期由创建应用时指定，默认为1小时，最长可设置为3小时；

   

2. 刷新令牌（refresh_token）的有效期由创建应用时指定，默认为30天（2592000秒），最长可设置为1年；

   

3. 访问令牌和刷新令牌的有效期都可以在企业控制台中通过管理应用来修改：[Oauth应用管理](https://ram.console.aliyun.com/applications)；

   

4. 建议将refresh_token的有效期设置的长一些，然后将refresh_token保存下来，每次直接用refresh_token来获取有效的access_token；这样可以避免经常性的需要登录阿里云账户，就失去了单点登录的意义；

   

5. 调用demo测试时配置文件的用户密码格式为：数字和字母，不能包含特殊字符；同时注意创建的OAuth应用是否分配了访问云呼的权限。

   



