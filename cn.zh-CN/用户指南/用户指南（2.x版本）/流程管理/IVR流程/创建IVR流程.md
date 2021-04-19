创建IVR流程 
============================

点击IVR流程列表右上角的 添加按钮，可进入到新建IVR的画布：

![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263888.png)



**接下来，以阿里云客户服务中心为例，创建一个简单的IVR流程来讲解各项功能的基本使用。** 

一. 填写基础信息 
------------------------------

请输入IVR流程名称、当前版本的描述信息并选择版本类型。在此先选择主流程进行演示。

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263894.png)

**状态说明** 

* **主流程** 主流程属于IVR流程的主干流程，可以直接引用已发布的子流程进行操作。

  

* **子流程** 子流程相对主流程会缺少"子流程"和"智能导航"模块的使用，子流程完成发布后可以在主流程中的"子流程"模块中实现复用。

  

* **满意度流程** 满意度流程相对主流程会缺少"转人工"、"转外线"、"函数"、"子流程"和"智能导航"模块的使用，满意度流程发布后配合设置-\>满意度调研-\>语音满意度进行使用。

  




二. 流程搭建 
----------------------------

在主流程中有七个模块以供使用，各模块详情可参见 **[IVR模块介绍]()** [。]()

* **开始和挂机模块需作为默认模块，将自动出现在画布中，并且不可删除。**

  




![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263896.png)

* **添加放音模块,用作播放欢迎语**

  




选中左侧基础模块栏中的 放音按钮，拖动到画布区域合适的位置释放。

![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263899.png)

**说明 ：** 右侧红框范围为有效的画布区域。

选中放音模块并点击模块上的设置图标，在右侧弹出窗口进行编辑，将模块命名为"欢迎语"，此处以文字转语音作为示例，也可以自行录音，然后到"音频"中进行上传。编辑完成后，点击底部的确定按钮。

![4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263904.png)

接下来将开始模块和"欢迎语"连接起来，选中开始模块点击模块右侧的圆心，不要松开鼠标按键，移动鼠标，此时会有一个浅色线的方块跟随鼠标，将方块拖动到放音模块的左侧，松开鼠标，连线即可完成。

![5](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263905.png)

如连线错误，可将鼠标放在连线上，将出现 **删除** 图标，点击可删除连线。

![7](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263908.png)

三. 添加收号模块 
------------------------------

重复上一步中的步骤操作 **收号** 模块，此处仍然以文字转语音作为示例。编辑时模块命名为"主菜单"，选择接收数字的类型为固定位数1位，编辑完成后点击确认即可。

![7](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263912.png)

重复上一步操作将 **放音** 模块和 **收号** 模块进行连线。

![8](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263913.png)

接下来我们先给"主菜单"中 **收号失败** 的情况添加一个 **放音** 模块，并进行编辑，编辑时模块命名为"主菜单收号失败"。

![9](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3527978161/p263914.png)

编辑完成后将"主菜单"中的 **收号失败** 与新的"主菜单收号失败"相连，"主菜单收号失败"的结束与"主菜单"相连。

![20](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263916.png)

四. 添加分支模块 
------------------------------

然后我们给"主菜单"的 **收号成功** 的情况添加一个 **分支** 模块，并对分支模块进行编辑，编辑时命名为"主菜单分支"。

注意：在"主菜单分支"中选择参数时需要选择"主菜单"的变量。

![11](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263921.png)

接下来为"主菜单"对应的参数进行配置，配置完成后将"主菜单"的 **收号成功** 与"主菜单分支"相连；重听的\*号分支与"欢迎语"相连；其他分支与"主菜单收号失败"相连。

![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263924.png)

五. 添加转人工模块和放音模块，作为分支模块的出口 
----------------------------------------------

接下来我们给"主菜单分支"的转人工情况添加新的 **转人工** 模块，首先将基础模块栏中的 **转人工** 模块拖动到画布中，并进行配置，命名为"主菜单转人工"。

![14](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263927.png)

然后我们将"主菜单转人工"与"主菜单分支"中的转人工分支进行连接；

![16](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263928.png)

然后为"主菜单转人工"的转人工失败和转人工超时创建新的收号模块，编辑时命名为"转人工失败/超时收号"并连线。

![17](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263930.png)

再给"转人工失败/超时收号"创建一个新的分支模块用来处理收号，命名为"转人工失败/超时分支"，编辑时参数需要选择"转人工失败/超时收号"的变量。

![19](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263931.png)接下来：

* 将"转人工失败/超时收号"的收号失败与"主菜单转人工"相连。

  

* 将"转人工失败/超时分支"的等待情况与"主菜单转人工"相连。

  

* 将"转人工失败/超时分支"的返回主菜单与"主菜单"相连。

  

* 将"转人工失败/超时分支"的其他分支单与"主菜单转人工"相连。

  




![21](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263934.png)

六. 添加新的收号模块和分支模块 
-------------------------------------

接下来完善"主菜单分支"的 **ECS规格升级** ，这里我们假定ECS规格升级有两种，分别为ECS大规格升级和ECS小规格升级，大小规格的区分依据用户的账号，账号为0-4开头的为小规格，5-9开头的为大规格。所以需要用户来输入账号，并且依据账号判断规格，所以我们添加收号模块和分支模块。

首先添加一个新的 **收号** 模块，用作 **输入账号** 使用，命名为ECS规格升级收号，接收数字的采用长度区间。

![22](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263935.png)

然后添加 **分支** 模块，对规格进行判断，编辑时命名为"ECS规格升级分支"，选择参数需要选择"ECS规格升级收号"的变量。

![23](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263936.png)

接下来为"ECS规格升级收号"的收号失败创建一个 **放音** 模块，命名为"ECS规格升级输入失败放音"

![24](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4527978161/p263937.png)

最后完成连线：

* 将"主菜单分支"的ECS规则升级情况与"ECS规格升级收号"相连；

  

* "ECS规格升级收号"的收号失败情况与"ECS规格升级输入失败放音"相连；

  

* "ECS规格升级输入失败放音"的结束再与"ECS规格升级收号"相连；

  

* "ECS规格升级收号"的收号成功情况与"ECS规格升级分支"相连；

  

* "ECS规格升级分支"的大规格和小规格情况与"主菜单转人工"相连；

  

* "ECS规格升级分支"的其他分支与"ECS规格升级输入失败放音"相连；

  




七. 流程搭建完成 
------------------------------

恭喜你，已经完成了一个功能完整的IVR流程，最后 **记得点击画布右上角"仅保存"或"保存并发布按钮"按钮进行保存或发布。** 

各个模块的使用方式，不仅限于上述使用方式，具体参见IVR模块结束。这是一个高度可定制化的IVR流程编辑器，可以根据实际的业务场景，自行编辑搭建。

