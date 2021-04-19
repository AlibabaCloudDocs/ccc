IVR基本操作 
============================

开始模块和结束模块不可以删除。

IVR发布 
--------------------------

IVR流程搭建完毕，需进行发布。只有状态为 **未发布** 、 **有更新，未发布** 、 **发布失败** 这三种状态可以进行发布，发布的方式有以下两种。

* 第一种方式为在IVR搭建完成后，在IVR保存并发布 按钮，即可将IVR进行发布。

  




![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8627978161/p263939.png)

* 第二种方式为在IVR列表中，点击操作区域的 **发布** ，即可进行发布。

  




![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8627978161/p263940.png)

当IVR流程的状态为 **发布成功** 时，需要将电话号码与IVR流程进行绑定，IVR流程才能最终生效。

* 点击页面左侧导航中的 **号码管理** 编辑 按钮。

  




![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8627978161/p263941.png)

* 在右侧的弹层中，进行绑定。 **用途** 请根据您的需要进行选择，IVR流程列表中仅显示状态为 **发布成功** 的IVR流程。

  




![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8627978161/p263942.png)

电话号码绑定成功后，该号码的呼入电话将进入该IVR流程。

IVR编辑 
--------------------------

除了状态为 **发布中** 的IVR流程不可编辑外，其他状态的IVR流程均可进行编辑。点击IVR列表中相应IVR流程的 **编辑** ，即可进入IVR画布，进行编辑。

基础信息可编辑，但IVR名称不可重复。

模块的添加和删除

* 编辑时，您可以添加新的模块，也可以删除画布中已有的模块，点击模块右侧的 **删除**

  




<!-- -->

* 删除前

  




![11](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9627978161/p263943.png)

* 删除后

  




![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9627978161/p263944.png)

**说明 ：** 开始模块和结束模块不可以删除。

**模块的编辑** 

* 可以点击模块上的 **设置** 图标，在右侧的弹窗中进行相应的编辑，编辑后点击确定提交即可。

  




![13](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9627978161/p263945.png)

* 编辑时记得经常点击 **保存** 按钮进行保存。

  

* 编辑完成后，状态将变为 **有更新，未发布** ，需要再次 **发布** ，方可进行更新，否则来电进线仍为上一次发布的IVR流程。

  




IVR克隆 
--------------------------

通过IVR克隆，可以将已有的IVR流程进行复制，填写上流程名称后，即可进行保存，从而生成一个新的IVR流程；这对于需要创建多个比较相似的流程时操作起来很方便。

IVR删除 
--------------------------

在IVR列表页面，点击对应IVR的 **删除** 按钮，二次确认后，方可删除。

**说明 ：** 对于已发布，并且已绑定电话号码的IVR流程，需要先对电话号码进行解绑后才可以删除。解绑电话参考IVR发布中的电话绑定，选择不绑定即可。
