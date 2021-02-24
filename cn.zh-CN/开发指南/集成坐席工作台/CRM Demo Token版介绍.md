CRM Demo Token版介绍 
======================================



CRMDemo下载链接：[java语言](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/ccc-crm-demo-java.zip)[php语言](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/crm-demo/ccc-crm-demo-php.zip)

CRMDemo 是一个集阿里云单点登录系统(基于Oauth2,以下简称Oauth2)和云呼叫中心坐席工作台(软电话)为一体的CRM示例，如果把Oauth2和软电话集成到用户自有系统中，使其能够在自有系统中通过Oauth2获取阿里云的AccessToken，从而使用云呼叫中心的资源，进而可以实现和自有系统的联动，比如来电弹屏，或者单击电话号码自动呼出等。

核心过程如下：

* 实现基于OAuth2的单点登录

  

* 软电话SDK和自有客户端的集成

  

* 实现来自客户端（浏览器端）的请求的转发

  




时序图![CRM_Demo_Seq_diagram](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241576.png)

1.CRMDemo的登录 
------------------------------

将CRMDemo下载下来后，根据项目中的README文件内的提示将demo运行起来，可看到如下登录页面：

![CRMDemo登录页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241577.png)

登录的uri:https://127.0.0.1:8443如果是通过公网登录端口号务必修改为HTTPS默认端口:443!CRM提供了自有的认证系统,该userName和passWord是CRM在初始化的时候写进数据库的,默认提供两组测试账号,User Name和Password分别是\<Edward,1234\>和\<sissi,5678\>。

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241578.png)

* 点击"Click here to see a customer list."获取用户列表;

  

* 点击"Retrieval Aliyun Token"会跳转至阿里云认证页面;请注意：云呼叫中心使用HTTPS协议，所以务必使用HTTPS协议。

  




2.Oauth2认证 
----------------------------

登录CRM之后，如需请求呼叫中心资源，请点击"Retrieval Aliyun Token"，跳转至阿里云系统认证页面，通过登录阿里云子账号完成认证授权（这里的子账号就是呼叫中心的坐席人员登录的账号，新建坐席时会收到邮件，邮件中包含了坐席登录呼叫中心的链接、账户名和密码）；这里除了输入账号密码手动登录外，我们还提供了一种 [服务端静默登录](~~63062~~) 的方式。![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241579.png)

在此之前，请确认您已经按照README中的提示替换了CRMDemo项目中的Client ID、Client Secret和instanceId！关于 Client ID、Client Secret和instanceId 的获取说明，请查看本文档底部。

第一步：获取授权码（authorization code） {#h2--authorization-code-11}
----------------------------------------------------------

获取访问令牌的第一步是要获取用户授权码。应用需要通过浏览器将用户重定向到阿里云OAuth 2.0服务,认证成功之后,阿里云服务端会携带授权码(code)和state重定向至注册的回调地址。 

请求样例：[https://signin.aliyun.com/oauth2/v1/auth?response_type=code\&response_mode=form_post\&redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback\&client_id=120171021\&state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5\&codeChallenge=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3](https://signin.aliyun.com/oauth2/v1/auth?response_type=code&response_mode=form_post&redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback&client_id=120171021&state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5&codeChallenge=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3)

    换行列出是为了更好的展示:
    https://signin.aliyun.com/oauth2/v1/auth?
    response_type=code&
    response_mode=form_post&
    redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback&
    client_id=120171021&state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5&
    codeChallenge=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3&access_type=offline
    
    其中state设置为任意字符串，AuthServer会将请求中的state参数及取值放到重定向的request中。应用通过state参数可以实现各种目的，比如状态保持，发送nonce从而减少CSRF威胁等。



返回样例:[https://127.0.0.1:8443/aliyun/auth/callback?code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3\&state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5](https://127.0.0.1:8443/aliyun/auth/callback?code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3&state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5)

    换行列出是为了更好的展示:
    GET  HTTP/1.1302Found
    https://127.0.0.1:8443/aliyun/auth/callback?
    code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3&
    state=75fb39a2-8b9f-49d6-9888-57a20ce8d7e5



第二步：用授权码换取访问令牌 {#h2--22}
------------------------

当Auth Server重定向至回调地址后,首先对返回的state参数做校验,然后获得授权码(code)以及初始请求中设置的redirect_uri参数值和nonce参数值(Auth Server用来判断是否是同一个站点的请求)，应用直接调用如下Endpoint(https://oauth.aliyun.com/v1/token)换取访问令牌 access_token,其包含了accessToken,refresh_token,credentials,idToken,userInfo等字段.

请求样例：[http://oauth.aliyun.com/v1/token?client_id=120171021\&grant_type=authorization_code\&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=\&code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3\&redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback\&code_verifier=yuhT7azLRG2ZVTp5BEFWtVV5WzXWGswH2ZW0VwWrfOMoV](http://oauth.aliyun.com/v1/token?client_id=120171021&grant_type=authorization_code&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3&redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback&code_verifier=yuhT7azLRG2ZVTp5BEFWtVV5WzXWGswH2ZW0VwWrfOMoV)

    换行列出是为了更好的展示:
    http://oauth.aliyun.com/v1/token?
    client_id=120171021&
    grant_type=authorization_code&
    client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&code=NTZ4wOaGVacs3oIk1sLfh8QWsF7CBfqTOEt3Sm1QJtzP3&
    redirect_uri=https://127.0.0.1:8443/aliyun/auth/callback&
    code_verifier=yuhT7azLRG2ZVTp5BEFWtVV5WzXWGswH2ZW0VwWrfOMoV



    返回样例:
    {
    "request_id":"231863ac-21eb-4927-9214-853eca0fa9b8",
    "access_token":"eyJBY2Nlc3NLZXlJZCI6IlNUUy5DVUR6ckpGa3UxZmNUM1IyNFF1U25kTjd4IiwiQWNjZXNzS2V5U2VjcmV0IjoiQmlXcHBqVE5BcllQQUtQZDJmU0hVMnhWZmdqZWF2eldIV3lKaTU3alFraXQiLCJTZWN1cml0eVRva2VuIjoiQ0FJU2l3SjFxNkZ0NUIyeWZTaklvcGJ4TWNqK3E3UlVocVNJVmhYajFqUUVlZHhDaTR1Y21qejNJWHhLZVhkc0Flc2VzZmswbEdwWTd2c2VpWU1TR3NVZEhCT2ROWkFwdGl6dVFvcFlKOWl2Z2RlOHlKQlpvcERIY0RIaEEzeVc5Y3ZXWlBxRFA3RzVVL3l4YWxmQ3V6WnV5TC9oRDF1TFZFQ2tOcHY3NHZ3T0xLNUZQRytDWUNGQkdjMWRLeVo3dGNZZUxnR3hEL3UyTlFQd2lXZWllaWdjc3dGbjIyaDA0dmI5a0pURXRVZU8xQUtua2JGUCtkdXFlTVgyTGVzVVpjOGdEb2Z0ZzdFdEtQQ2ZqM1VLdGlJbnJ2a20wUFoyZ1JiQ3B0eUhHRjVYNmdtTFA5ZlAvOGRuUkEwQ1BQUmtSdkFZOUtPa3lxQWo2cmFEejltcmxnd2dMT2hUVnluUGtWTW5HMVpoa0lrYWdBRSswZDlmRUYxMlJOKzVPY2U2bGx3bnVQRjYweTdadStMbU5oRENrL2U5Yi9UZFYwTkRQZ0hxamd4ald6cTZsSThheWhXOGYzWDZtcHRZcmlHaVpuczBFUWpmOHpDMTRybXZWR2NkK284enVNYk1SdUZRblM5NDVsVUZEVmRIRmlvSzFlelNpci91T1Q1Si90KzhZYjhmZS9PR0ZjUkxqRE50cW1BVkdaNGVVUT09In0",
    "token_type":"AliyunSTS",
    "refresh_token":"1vpn8NKWBK2lLvhf",
    "id_token":"eyJhbGciOiJSUzI1NiIsImtpZCI6IkpDOXd4enJocUowZ3RhQ0V0MlFMVWZldkVVSXdsdEZodWk0TzFiaDY3dFUifQ.eyJleHAiOjE1MTY1OTY4MTYsInN1YiI6IjI0NjU2NDAzMDc1MzgyODA1NDUiLCJuYW1lIjoieWFubGVAcHJlLm9uYWxpeXVuLmNvbSIsInVwbiI6InlhbmxlQHByZS5vbmFsaXl1bi5jb20iLCJhdWQiOiI5MjAxNzEwMzEiLCJpc3MiOiJodHRwczpcL1wvb2F1dGguYWxpeXVuLmNvbSIsImRpZCI6IiIsImFpZCI6IjEwNzU4MDc1MzYyNjczMjUiLCJiaWQiOiIyNjg0MiIsImlhdCI6MTUxNjU5MzIxNn0.eIQfAXswTrGD8db7VOO2XBS4g16aQRPQxhG2qC4cse3_Av6JmAeKjZWYGrJF7vSix8Pw7pPA6Je4tg53Xx2fhksaQXehsRnFDjAga1RkmL5v9fYJ1ksAQS3lZ6I_8WZ5grx186pc2hjwKlo8LRqLJMg76MjsHSnuCLyYKLTouR1f1Iv4QFfSrR5UzWQhG0jBWaGjGIGKSBv1ouxjeD8ouQxn-EsIRkrEa8wQclOQuYny-IdjEzeUrIrbvlRAxoZJRigc7_sdyB6dmYCM6aZgEp1n2lugIN_lWyfipW8VecczNyfc2bZeqtb6kzwitS7_23-mTCFUFlmwIMqTurDbPw",
    "additional_information":{"refresh_token_id":9718},
    "expires_in":"3599"
    }
    
    返回的参数中access_token是一个对象,其包含了accessToken,refresh_token,idToken等字段.
    * accessToken:有效时间最长为3小时,是一个base64-url encoded字符串,将其解析之后设置为credentials字段的值,也就是真正的访问令牌;
    * refresh_token:有效时间最长为2年,可以用来换取令牌;
    * userInfo：具体获取方式请查看该文档第四部分其他说明



第三步:刷新访问令牌 {#h2--33}
--------------------

由于access_token默认有效时间为一小时,所以每隔一小时需要点击从而刷新令牌,就是使用refresh_token换取了一个新的access_token.请求样例:[http://oauth.aliyun.com/v1/token?client_id=120171021\&grant_type=refresh_token\&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=\&refresh_token=1vpn8NKWBK2lLvhf\&redirect_uri=/aliyun/refresh](http://oauth.aliyun.com/v1/token?client_id=120171021&grant_type=refresh_token&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&refresh_token=1vpn8NKWBK2lLvhf&redirect_uri=/aliyun/refresh)

    换行列出是为了更好的展示:
    POST /v1/token HTTP/1.1
    Host: oauth.aliyun.com
    Content-Type: application/x-www-form-urlencoded
    
    http://oauth.aliyun.com/v1/token?
    client_id=120171021&
    grant_type=refresh_token&
    client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&
    refresh_token=1vpn8NKWBK2lLvhf&
    redirect_uri=/aliyun/refresh
    
    请求的返回值与用授权码换取访问令牌的返回值一致，但不包含refresh_token和id_token。所以获取newToken之后需要把oldToken中的refresh_token和id_token设置进newToken中,以便下次刷新访问令牌;



第四步:撤销令牌 {#h2--44}
------------------

如果您已经不打算再次调用呼叫中心的资源，点击"Revoke Aliyun Token"则会使您已经获取的阿里云AccessToken立即失效，如需再次请求呼叫中心资源只需要再次点击"Retrieval Aliyun Token"即可！请求实例:[https://oauth.aliyun.com/v1/revoke?client_id=120171021\&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=\&token=eyJBY2Nlc3NLZXlJZCI6IlNUUy5NTmpWbU1LVmNGajN6RGdXNjFGbmtXUUZaIiwiQWNjZXNzS2V5U2VjcmV0IjoiN0VFVEttb1pMWXZneGpaRUVHVGd2WFdUUFh4UG5hN1NTTFBuc3QyMkt6ZFMiLCJTZWN1cml0eVRva2VuIjoiQ0FJU2l3SjFxNkZ0NUIyeWZTaklySTNmSGRmNXBvbEM4YWpZZUdMV3N6WmtTdUZIdUpUdHVEejNJWHhLZVhkc0Flc2VzZmswbEdwWTd2c2VpWU1TR3NVZEhCT2ROWkFwdGk2ZWJZdFlKOWl2Z2RlOHlKQlpvcERIY0RIaEEzeVc5Y3ZXWlBxRFA3RzVVL3l4YWxmQ3V6WnV5TC9oRDF1TFZFQ2tOcHY3NHZ3T0xLNUZQRytDWUNGQkdjMWRLeVo3dGNZZUxnR3hEL3UyTlFQd2lXZWllaWdjc3dGbjIyaDA0dmI5a0pURXRVZU8xQUtua2JGUCtkdXFlTVgyTGVzVVpjOGdEb2Z0ZzdFdEtQQ2ZqM1VLdGlJbnJ2a20wUFoyZ1JiQ3B0eUhHRjVYNmdtTFA5ZlAvOGRuUkEwQ1BQUmtSdkFZOUtPa3lxQWo2cmFEejltcmxnd2dMT2hUVnluUGtWTW5HMVpoa0lrYWdBR1Y5bS9tR0FOcWgwTnhmWHJaeUxmSkxZSkVYRHkwQjhtYUlKV0hGY0htNHc2bTI0dFlLczlBV1VBbXpWQndFVlFyS1d5RFB4alFVSUR4SlJWSmthZ3JsRDRKbitrZjBVNEVWaFVITFRLVmRGTFBObWpCWWJhUjFzTDd5d1VhSE51bVNTdTA4OERmVkYzSldKVThHRnVtRDJzL2hTRjNpRHRPcENneXc5Sk1Vdz09In0\&redirect_uri=/aliyun/revoke](https://oauth.aliyun.com/v1/revoke?client_id=120171021&client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&token=eyJBY2Nlc3NLZXlJZCI6IlNUUy5NTmpWbU1LVmNGajN6RGdXNjFGbmtXUUZaIiwiQWNjZXNzS2V5U2VjcmV0IjoiN0VFVEttb1pMWXZneGpaRUVHVGd2WFdUUFh4UG5hN1NTTFBuc3QyMkt6ZFMiLCJTZWN1cml0eVRva2VuIjoiQ0FJU2l3SjFxNkZ0NUIyeWZTaklySTNmSGRmNXBvbEM4YWpZZUdMV3N6WmtTdUZIdUpUdHVEejNJWHhLZVhkc0Flc2VzZmswbEdwWTd2c2VpWU1TR3NVZEhCT2ROWkFwdGk2ZWJZdFlKOWl2Z2RlOHlKQlpvcERIY0RIaEEzeVc5Y3ZXWlBxRFA3RzVVL3l4YWxmQ3V6WnV5TC9oRDF1TFZFQ2tOcHY3NHZ3T0xLNUZQRytDWUNGQkdjMWRLeVo3dGNZZUxnR3hEL3UyTlFQd2lXZWllaWdjc3dGbjIyaDA0dmI5a0pURXRVZU8xQUtua2JGUCtkdXFlTVgyTGVzVVpjOGdEb2Z0ZzdFdEtQQ2ZqM1VLdGlJbnJ2a20wUFoyZ1JiQ3B0eUhHRjVYNmdtTFA5ZlAvOGRuUkEwQ1BQUmtSdkFZOUtPa3lxQWo2cmFEejltcmxnd2dMT2hUVnluUGtWTW5HMVpoa0lrYWdBR1Y5bS9tR0FOcWgwTnhmWHJaeUxmSkxZSkVYRHkwQjhtYUlKV0hGY0htNHc2bTI0dFlLczlBV1VBbXpWQndFVlFyS1d5RFB4alFVSUR4SlJWSmthZ3JsRDRKbitrZjBVNEVWaFVITFRLVmRGTFBObWpCWWJhUjFzTDd5d1VhSE51bVNTdTA4OERmVkYzSldKVThHRnVtRDJzL2hTRjNpRHRPcENneXc5Sk1Vdz09In0&redirect_uri=/aliyun/revoke)

    换行列出是为了更好的展示:
    https://oauth.aliyun.com/v1/revoke?
    client_id=120171021&
    client_secret=E1QGQUDMSqRNcOO/WTt83vQ25Bdtb0LJYSm0fFdF0eY=&
    token=eyJBY2Nlc3NLZXlJZCI6IlNUUy5NTmpWbU1LVmNGajN6RGdXNjFGbmtXUUZaIiwiQWNjZXNzS2V5U2VjcmV0IjoiN0VFVEttb1pMWXZneGpaRUVHVGd2WFdUUFh4UG5hN1NTTFBuc3QyMkt6ZFMiLCJTZWN1cml0eVRva2VuIjoiQ0FJU2l3SjFxNkZ0NUIyeWZTaklySTNmSGRmNXBvbEM4YWpZZUdMV3N6WmtTdUZIdUpUdHVEejNJWHhLZVhkc0Flc2VzZmswbEdwWTd2c2VpWU1TR3NVZEhCT2ROWkFwdGk2ZWJZdFlKOWl2Z2RlOHlKQlpvcERIY0RIaEEzeVc5Y3ZXWlBxRFA3RzVVL3l4YWxmQ3V6WnV5TC9oRDF1TFZFQ2tOcHY3NHZ3T0xLNUZQRytDWUNGQkdjMWRLeVo3dGNZZUxnR3hEL3UyTlFQd2lXZWllaWdjc3dGbjIyaDA0dmI5a0pURXRVZU8xQUtua2JGUCtkdXFlTVgyTGVzVVpjOGdEb2Z0ZzdFdEtQQ2ZqM1VLdGlJbnJ2a20wUFoyZ1JiQ3B0eUhHRjVYNmdtTFA5ZlAvOGRuUkEwQ1BQUmtSdkFZOUtPa3lxQWo2cmFEejltcmxnd2dMT2hUVnluUGtWTW5HMVpoa0lrYWdBR1Y5bS9tR0FOcWgwTnhmWHJaeUxmSkxZSkVYRHkwQjhtYUlKV0hGY0htNHc2bTI0dFlLczlBV1VBbXpWQndFVlFyS1d5RFB4alFVSUR4SlJWSmthZ3JsRDRKbitrZjBVNEVWaFVITFRLVmRGTFBObWpCWWJhUjFzTDd5d1VhSE51bVNTdTA4OERmVkYzSldKVThHRnVtRDJzL2hTRjNpRHRPcENneXc5Sk1Vdz09In0&
    redirect_uri=/aliyun/revoke



3.坐席工作台 
-------------------------

功能说明 {#h2-u529Fu80FDu8BF4u660E55}
---------------------------------

[软电话SDK](~~63063~~) 提供了所有和座席相关的功能，比如接打电话、转接、查看通话记录个人数据等，通过把软电话SDK集成到自有系统中，可以实现和自有系统的联动，比如来电弹屏或者单击电话号码自动呼出等。为了达成这一目标

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241580.png)

实现来自客户端（浏览器端）的请求转发 {#h2--66}
----------------------------

* 在CRM中对于坐席工作台的所有功能使用都是通过引入的 [软电话SDK](https://help.aliyun.com/document_detail/63063.html?spm=a2c4g.11186623.6.616.7G3WUC) 实现的，在软电话SDK的使用过程中，会发起多个请求到CccController（也就是自有业务系统的服务端），在CccController中调用OpenAPI来访问呼叫中心的资源。

  




**注意** ：Demo中此处采用了CommonAPI调用POP(阿里云网关) API的方式，请求参数做了格式转换。例如：1. 入参的key值需要大写；2. 不支持数组格式，只接收arryKey.1,arryKey.2这种格式；对应的响应参数为了前端软电话SDK的正确解析进行了逆处理。

参考：[软电话SDK前端接入useOpenApiSdk](https://help.aliyun.com/document_detail/63063.html#h2--config-3 "软电话SDK前端接入useOpenApiSdk")

* 请求示例:https://127.0.0.1:8443/aliyun/ccc/api?action=ListSkillGroupsOfUser

  

* 首先引入以下Jar包

  




    <dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-core</artifactId>
    <version>3.7.1</version>
    </dependency>



* CccController中的示例代码

  




    DefaultProfile profileBear =DefaultProfile.getProfile(REGION);
            profileBear.addEndpoint(ENDPOINT, REGION, PRODUCT, DOMAIN);
    
    BearerTokenCredentials bearerTokenCredentials =
    newBearerTokenCredentials(accessToken);
    DefaultAcsClient accessTokenClient =newDefaultAcsClient(profileBear, bearerTokenCredentials);
            accessTokenClient.setAutoRetry(false);
    
    /**
             * 使用CommonAPI调用POP API时，和使用传统产品SDK相比，请求和返回参数的格式都有所不同，因此需要进行一定的格式转换。
             */
    CommonRequest commonRequest =newCommonRequest();
            commonRequest.setDomain(DOMAIN);
            commonRequest.setVersion(VERSION);
            commonRequest.setAction(action);
    JSONObject jsonObject =JSONObject.parseObject(request);
    
    for(Entry<String,Object> entry : jsonObject.entrySet()){
    String key = entry.getKey().trim();
    if(key.length()>1){
                    key = key.substring(0,1).toUpperCase()+ key.substring(1);
    }elseif(key.length()==1){
                    key = key.toUpperCase();
    }else{
    continue;
    }
                commonRequest.putQueryParameter(key, entry.getValue().toString());
    }
    
            commonRequest.putQueryParameter("accessToken", accessToken);
    CommonResponse response =null;
    try{
                response = accessTokenClient.getCommonResponse(commonRequest);
    System.out.println(JSONObject.toJSONString(response.getData()));
    }catch(ClientException e){
                logger.error("Failed to invoke open API, request="+ JSON.toJSONString(commonRequest), e);
    thrownewCallCenterServiceException(e.getRequestId(), e.getErrCode(), e.getMessage());
    }
    JSONObject jsonResult =JSONObject.parseObject(response.getData());
    JSONObject newJsonResult =newJSONObject();
    /**
             * 此处对返回的参数进行格式转换，具体的格式转换效果参考CccController中的main方法。
             */
            copyObject(newJsonResult, jsonResult);
    returnJSONObject.toJSONString(newJsonResult);



4.其他说明 
------------------------

关于 Client ID、Client Secret和instanceId {#h2--client-id-client-secret-instanceid77}
---------------------------------------------------------------------------------

1. 在集成测之前请先参考 [Oauth2集成应用注册](~~70950~~), 以便获取Client ID 和 Client Secret（二者唯一的标示了您的应用，请注意保密）以及redirect_uri(请注意云呼叫中心使用WebRTC协议进行语音传输，因此redirect_uri必须使用HTTPS协议。)，在进行应用注册时，切记添加 https://127.0.0.1:8443/aliyun/auth/callback; 为回调地址，否则无法正常使用CRM Demo。

   

2. 当您获取到了Client ID 和 Client Secret那说明您的应用已经注册成功，接下来您需要用您自己的Client ID 和 Client Secret替换掉应用的属性文件中的对应值，并且获取到您呼叫中心的instanceId，替换掉home.html文件中的对应值!

   

3. 关于instanceId的获取，可以查看左侧文档目录中的 开发指南-简介 中的说明。

   




关于阿里云一年内免登陆策略的说明 {#h2-u5173u4E8Eu963Fu91CCu4E91u4E00u5E74u5185u514Du767Bu9646u7B56u7565u7684u8BF4u660E88}
---------------------------------------------------------------------------------------------------------

由于access_token默认有效时间为一小时,refreshToken有效期为一年,所以需要先获取refreshToken,然后将其保存,以后每次就可以不用去阿里云认证就可以用refreshToken换取AccessToken.那如何获取refreshToken呢?就是在上面的第二步,Auth Server重定向至回调地址的时候,其access_token字段中就包含了refreshToken.请注意云呼叫中心使用WebRTC协议进行语音传输，因此自有业务系统务必使用HTTPS协议。

根据access_token通过调用接口获取userInfo {#h2--access-token-userinfo}
-----------------------------------------------------------

接口地址：https://oauth.aliyun.com/v1/userinfo

可通过直接调用接口的形式，需要在请求头Header中增加一个参数Authorization，值为 Bearer ${access_token}，即 Bearer空格access_token，如下图所示：

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4590273161/p241581.png)
