SIP话机接入 
============================



1. 第一步：IP电话必须获取到IP地址，并且此IP地址需要和电话系统的IP地址互联互通，亿联话机默认DHCP获取地址，按一下话机的OK键如图，可以查看话机的IP地址，其他品牌IP话机可通过其他方式查看IP。![SIP话机接入-1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0433617161/p259220.png)

   

2. 第二步：打开浏览器，在地址栏输入IP地址，如下图所示，回车。![SIP话机接入-2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0433617161/p259223.png)

   

3. 第三步：亿联IP话机的默认账户和密码都是admin，其他品牌默认密码可能不一样。![SIP话机接入-3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0433617161/p259224.png)

   

4. 第四步：按照下图填写注册信息，状态激活，分机号、密码和服务器地址不能填错。![](https://intranetproxy.alipay.com/skylark/lark/0/2021/png/149813/1617021148084-4bf6d0dc-060b-46ff-91c6-b3a1156c0d46.png?x-oss-process=image%2Fresize%2Cw_720)

   

5. 第五步：按照下图配置安全策略，配置完成后点击提交即可。![](https://intranetproxy.alipay.com/skylark/lark/0/2021/png/149813/1617021334516-60857dbd-bf1c-40d0-9b89-091ff859d831.png?x-oss-process=image%2Fresize%2Cw_746)

   






6. 第六步：调用接口[RegisterDevice](/cn.zh-CN/开发指南/开发指南（2.x版本）/API参考/话务/RegisterDevice.md)传入云呼实例ID、话机设备ID以及第四部注册账号的密码。

   

7. 第七步：查看此电话注册状态，"已注册"表示电话已经注册成功，此时您就可以正常使用了。![SIP话机接入 - 7](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0433617161/p259225.png)

   



