CRM Demo AK版介绍 
===================================

本 Demo 通过访问密钥 (AccessKey) 调用接口的方式演示了软电话与用户自有系统的集成。

[CRM Demo AK版下载](https://cloudcallcenter-stage.oss-cn-hangzhou.aliyuncs.com/all-public/crm-demo/20210220/ccc-crm-demo-ak-java.zip)

背景信息 
----------------------

AccessKey包括AccessKey ID和AccessKey Secret。

* AccessKeyId：简称AK，用于标识用户。

  

* AccessKeySecret：简称SK，用于验证用户的密钥。 **AccessKeySecret必须保密！**

  




**警告** ：主账号Accesskey泄露会威胁您所有资源的安全。建议使用子账号（RAM用户）Accesskey进行操作，可以有效降低Accesskey泄露的风险。

时序图 
---------------------

![demoAK_seq_diagram](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6518800161/p190691.png)

使用说明 
----------------------

1. Demo下载后，根据项目中README文件内的说明进行配置并运行demo，可看到如下登录页面： {#h2-1-demo-readme-demo-1}
-----------------------------------------------------------------------------

![DemoIntro1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6518800161/p190692.png)

2. 首次进入需要录入管理员信息 {#h2-2-2}
--------------------------

![crm-demo-ak_home1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6518800161/p211322.png)

3. 管理员注册 
-----------------------------

![crm-demo-ak_adminRegister ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8958800161/p211323.png)

**注意** ：此处录入的 AccessKey ID 和 AccessKey Secret 对应的用户必须是所配置的云呼叫中心实例ID（instanceId）对应云呼实例的管理员，并且具有RAM管理权限。相关操作请参考：

1. [instanceId(呼叫中心实例ID)获取方式](https://help.aliyun.com/document_detail/85054.html#h2-instanceid-id-2 "instanceId(呼叫中心实例ID)获取方式")

   

2. [坐席管理](https://help.aliyun.com/document_detail/60419.html "坐席管理")

   

3. [为RAM用户创建访问密钥](https://help.aliyun.com/document_detail/116401.html "为RAM用户创建访问密钥")

   

4. [为RAM用户授权](https://help.aliyun.com/document_detail/116146.html "为RAM用户授权")

   

5. [访问密钥常见问题](https://help.aliyun.com/document_detail/134385.html "访问密钥常见问题")

   




其中参考4需要为RAM用户授予 "管理访问控制（RAM）的权限"。

4. 管理员注册后可以选择创建坐席，查看用户或是进入坐席工作台 
----------------------------------------------------

![crm-demo-ak_home2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0689800161/p211359.png)

其他说明 
----------------------

关于Demo中参数格式转换的说明 {#h2--demo-4}
------------------------------

参考：[实现来自客户端（浏览器端）的请求转发](https://help.aliyun.com/document_detail/65884.html?spm=a2c4g.11186623.2.30.3d997cf8m077QN#h2--66 "实现来自客户端（浏览器端）的请求转发")
