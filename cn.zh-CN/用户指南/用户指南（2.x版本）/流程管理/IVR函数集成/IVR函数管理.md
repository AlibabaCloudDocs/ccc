IVR函数管理 
============================

IVR函数管理，可以将您在函数计算服务中增加的函数添加到呼叫中心实例中，然后在IVR流程中通过IVR函数模块去调用这些函数，在这些函数中，可以去访问您的自有系统，达到IVR与第三方系统集成交互的目的，从而实现例如订单查询，重置密码，身份验证等功能。

一、在函数计算控制台增加函数 
--------------------------------

1. 阿里云主账号登录到[函数计算控制台](https://fc.console.aliyun.com)；首次登录时，会提示您开通 **函数计算** ，点击 **立即开通** 。[函数计算价格说明](https://help.aliyun.com/document_detail/54301.html)； ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p261765.png)

   

2. 新建 **服务** ，然后在服务中新建 **函数** 。新建服务时，需要您选择区域，您直接选择距离您的服务器所在地最近的即可，这样可以提高函数计算调用速度。详细参考文档：https://help.aliyun.com/document_detail/60946.html#create-service![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p261766.png)

   

3. 如下图所示，在服务 **example-service** 中增加了一个名为 **checkUserIdentity** 的函数，所属区域为 **华南1(深圳)** ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p261767.png)

   




二、将函数计算中的函数添加到呼叫中心 
------------------------------------

* 打开[云呼叫中心控制台](https://ccc.console.aliyun.com/AccInstance)https://ccc.console.aliyun.com/AccInstance；进入需要访问的实例连接，在设置中的IVR集成中进行添加。

  




![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p264031.png)

在函数列表中，点击 **添加** ，然后在弹出窗中输入函数对应的信息，例如在第一步中最后添加的函数，然后点击 **确定** 保存，例如下图： 

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p264030.png)

* 新增的函数，我们建议使用 **测试** 功能，检测函数的连通性，点击对应函数的测试按钮，在弹框中输入该函数所需要的参数名称和值，然后点击下方的测试按钮，查看返回值是否符合预期。

  




![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p264029.png)

* 函数的编辑和删除。

  * 编辑：通常是由于您在函数计算控制台修改了对应的函数信息，记得及时同步到云呼叫中心。

    
  
  * 删除：如果函数计算控制台中的某个函数不再使用需要删除，删除前切记先修改IVR流程，保证正在使用的IVR流程中并没有使用该函数，然后再删除，删除后，需要到呼叫中心控制台删除该函数的引用。

    
  

  

  ![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9637978161/p264026.png)
  




三、重点说明： 
-------------------------

1. 如果在函数计算控制台修改了函数名称、函数所属的服务、区域，一定要到云呼叫中心控制台及时同步。 **如果函数所需要的参数发生变化，一定要记得同步修改IVR流程中使用该函数的函数模块里的入参，并且发布IVR，发布完成后记得打电话测试一下。**

   

2. 全流程操作示例，请参考本页面左侧导航中的 用户指南-IVR函数集成-使用示例。

   



